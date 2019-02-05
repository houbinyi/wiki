=== inetd ===
sudo apt-get install inetutils-inetd 

sudo vim /etc/inetd.conf
?tftp dgram udp wait root /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot


