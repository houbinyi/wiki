Content-Type: text/x-zim-wiki
Wiki-Format: zim 0.4
Creation-Date: 2016-09-08T15:59:23+08:00

====== inetd ======

=== inetd ===
sudo apt-get install inetutils-inetd 

sudo vim /etc/inetd.conf
?tftp dgram udp wait root /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot


