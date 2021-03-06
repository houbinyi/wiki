=== Create/Remove virtual interface by command ===
sudo ifconfig eth0:0 192.168.10.10 up
sudo ifconfig eth0:0 down

=== Create virtual interface by config ===
sudo vim /etc/network/interfaces

auto eth0:0
iface eth0:0 inet static
address 192.168.10.10
netmask 255.255.255.0
#network 192.168.10.1
#broadcast 192.168.1.255

sudo /etc/init.d/networking restart


ifconfig
ifconfig -a 
ifconfig 网络端口 IP地址 hw <HW> MAC地址 netmask 掩码地址 broadcast 广播地址 [up/down]
[root@localhost ~]# ifconfig eth0 down
ifdown eth0
[root@localhost ~]# ifconfig eth0 192.168.1.99 broadcast 192.168.1.255 netmask 255.255.255.0
ifconfig eth0 192.168.1.99 broadcast 192.168.1.255 netmask 255.255.255.0 up
[root@localhost ~]# ifconfig eth0 up
ifup eth0
[root@localhost ~]# ifconfig eth0
 ifconfig eth1 192.168.1.252 hw ether 00:11:00:00:11:11 netmask 255.255.255.0 broadcast 192.168.1.255 up
ifconfig eth1 hw ether 00:11:00:00:11:22
 ifconfig eth1 192.168.1.252 netmask 255.255.255.0 broadcast 192.168.1.255 up

虚拟网络接口指的是为一个网络接口指定多个IP地址，虚拟接口是这样的 eth0:0 、 eth0:1、eth0:2 ... .. eth1N。
[root@localhost ~]# ifconfig eth1:0 192.168.1.251 hw ether 00:11:00:00:11:33 netmask 255.255.255.0 broadcast 192.168.1.255 up
或
[root@localhost ~]# ifconfig eth1 hw ether 00:11:00:00:11:33
[root@localhost ~]# ifconfig eth1 192.168.1.251 netmask 255.255.255.0 broadcast 192.168.1.255 up

注意：指定时，要为每个虚拟网卡指定不同的物理地址；



https://help.ubuntu.com/community/Kerberos

**/usr/share/doc/ifupdown/examples/network-interfaces**

=== /etc/network/interfaces ===
sudo vim /etc/network/interfaces

auto eth0
iface eth0 inet static
	address 192.168.1.5
	network 192.168.0.0
	netmask 255.255.255.0
	broadcast 192.168.0.255
	gateway 192.168.1.254
	up route add -net 192.168.1.128 netmask 255.255.255.128 gw 192.168.1.2
	up route add default gw 192.168.1.200
	down route del default gw 192.168.1.200
	dns-search ***
	dns-nameservers ***
	dns-domain ***
	down route del -net 192.168.1.128 netmask 255.255.255.128 gw 192.168.1.2


sudo ifconfig eth0 down
sudo ifdown eth0 
sudo ifconfig eth0 up
sudo ifup eth0 

sudo service networking restart

=== /etc/resov.conf ===
nameserver x.x.x.x
search x.x.x
domain x.x.x
