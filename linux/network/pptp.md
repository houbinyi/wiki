https://linux.cn/article-3376-1.html
http://blog.csdn.net/b_h_l/article/details/10002787

=== Server: ===
$ sudo apt-get install pptpd

$ sudo vi /etc/pptpd.conf
localip 172.16.0.1 #你的主机IP
remoteip 172.16.0.247-253 #分配给接入的client的IP

$ sudo vi /etc/ppp/pptpd-options
ms-dns 8.8.8.8
ms-dns 8.8.4.4

$ sudo vi /etc/ppp/chap-secrets
//#用户名，服务，密码，限制ip//
"user" pptpd "user" *

$ sudo /etc/init.d/pptpd restart

Server IP forwarding 
$ sudo vi /etc/sysctl.conf
net.ipv4.ip_forward=1
sudo sysctl -p

$ sudo apt-get install iptables

//# all target subnet ip out to ech0(intranet net card)// 
sudo iptables -t nat -A POSTROUTING -s 172.16.0.0/16 -d 10.0.0.0/8 -o eth0 -j MASQUERADE
//# all other ip out to eth1(public net card)//
$ sudo iptables -t nat -A POSTROUTING -s 172.16.0.0/16 -o eth1 -j MASQUERADE

$ sudo iptables-save >/etc/iptables-rules

$ sudo vi  /etc/network/interfaces
$ pre-up iptables-restore </etc/iptables-rules

$ sudo iptables -A FORWARD -s 172.16.0.0/16-p tcp -m tcp --tcp-flags SYN,RST SYN -j TCPMSS --set-mss 1200
$ sudo iptables-save >/etc/iptables-rules

=== Client: ===
GUI:
$ sudo apt-get install pptp-linux network-manager-pptp
1. Advanced
	a. authentication methods: MSCHAP, MSCHAPv2;
	b. MPPE; 
	c. All Available; 
	d. Allow stateful encryption
	e. Allow BSD data compression
	f. Allow Deflate data compression
	g. Use TCP header compression
	h. Send PPP echo packets)

CLI:
$ sudo pptpsetup --create beta --server 101.200.84.236 --username houbinyi --password houbinyi --encrypt --start
$ sudo pon beta
$ sudo poff -a
