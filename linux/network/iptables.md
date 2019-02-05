=== Usefull command ===
$ iptables -t nat -L # list nat rules
$ iptables -t nat -F # flush nat rules


/etc/init.d/iptables.up.rules

=== Command ===
tableName := nat|mangle|filter
chainName := INPUT|OUTPUT|FORWARD|PREFOUTING|POSTROUTING
action := ACCEPT|DROP|REDIRECT|REJECT|SNAT|DNAT|MASQUERADE|LOG
state := NEW|ESTABLISTED|RELATED|INVALID

**Default policy**
iptables [-t tableName] <-P> <chainName> <action>

**View iptables rule**
iptables [-t tableName] <-L> [chainName]

iptables -nv -L (default -t filter)

**AIDR iptables rule**
iptables -<A|I|D|R> 
-t <tableName> <chainName> [ruleNumber] 
[-i|o networkCardName] [-p protocalName] 
[-s srcIp|srcSubNet] [--sport srcPort] 
[-d destIp|destSubNet] [--dport destPort] 
<-j action>

**Clare rule and counter**
iptables [-t tableName] <-F|Z>
F:flush all rules
Z:reset counter to zero
X:delete user defined chain

=== NAT ===
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -s 192.168.56.0/24  -j SNAT --to-source 10.0.0.1
iptables -t nat -A POSTROUTING -s 192.168.56.0/24 -j MASQUERADE

**1) Edit /etc/network/interfaces to make your LAN connection static instead of dynamic. Your WAN connection, of course, should remain dynamic.**

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
auto eth1
iface eth1 inet static
	 address 192.168.3.1
	 network 192.168.3.0
	 netmask 255.255.255.0

**2) Next, install the 'dnsmasq' package and configure by editing /etc/dnsmasq.conf to hand out IPs in the appropriate range.**

**3) Change the kernel settings to permit IP Forwarding. Edit /etc/sysctrl.conf:**

net.ipv4.ip_forward=1

**4) Create a set of IPTables rules to permit NAT. Save this script as /etc/network/if-up.d/00-firewall. That way, it will run every time an interface is brought up, superseding any other rules you have laying around.**

#!/bin/sh
PATH=/usr/sbin:/sbin:/bin:/usr/bin

# Delete all previously existing rules
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

# Always accept loopback traffic
iptables -A INPUT -i lo -j ACCEPT

# Allow established connections
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i ppp0 -o br0 -m state --state ESTABLISHED,RELATED -j ACCEPT

# ALLOW INCOMING OPEN PORTS TO THE SERVER FROM OUTSIDE HERE
#
# Allow outgoing connections from the LAN side
iptables -A FORWARD -i br0 -o ppp0 -j ACCEPT
#
#

# Masquerade
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

# Reject any non-established connections from the WAN
iptables -A INPUT -m state --state NEW -i ppp0 -j REJECT
iptables -A FORWARD -i ppp0 -o br0 -j REJECT

**5) Make it work. It should start automatically upon reboot. But to test it without rebooting (good idea), here's how to make it work:**

sudo sysctl -p                            # Apply the kernel changes
sudo service dnsmasq restart       # Reload the changed dnsmaq.conf
sudo ifdown eth0
sudo ifdown eth1                        # Reload changed interface and IPTables
sudo ifup eth0
sudo ifup eth1                            # Reload changed interface and IPTables


=== Save and Load ===
$ sudo iptables-save >/etc/iptables-rules
$ sudo vi  /etc/network/interfaces
pre-up iptables-restore </etc/iptables-rules


