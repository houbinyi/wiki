Content-Type: text/x-zim-wiki
Wiki-Format: zim 0.4
Creation-Date: 2016-04-25T16:39:05+08:00

====== deamon ======

=== daemon ===
**start-stop-daemon**
/sbin/start-stop-daemon --start --quiet --oknodo --make-pidfile --pidfile /opt/nginx.pid --exec /home/chenshu/nginx/bin/nginx  -- -c /home/chenshu/nginx/etc_nginx/nginx.conf

/sbin/start-stop-daemon --stop --oknodo --pidfile /opt/nginx.pid

=== keep alive ===
**supervisord**
sudo apt-get install supervisor
sudo /etc/init.d/supervisor stop
sudo /etc/init.d/supervisor start

sudo vim /etc/supervisord/conf.d/*.conf

sudo supervisorctl status
sudo supervisorctl reread
sudo supervisorctl update
sudo supervisorctl reload

**monit**
**daemontools**
**runit**

=== cron ===



=== init & service ===

1) /etc/init.d/*
2) /etc/rc[0-6].d/*

**init**
sudo initctl list

**chkconfig**
chkconfig --list

**sysv-rc-conf** 
sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf 

**rcconf**
sudo apt-get install rcconf
sudo rcconf

**bum**
sudo apt-get install bum
sudo bum

**service**
sudo service --status-all
sudo service serviceName start
sudo service serviceName stop

**Fedora:(systemd)**
# systemctl enable docker
# systemctl start docker

**Ubuntu:(upstart)**
# vim /etc/init.d/serviceName
# chmod 755 /etc/init.d/serviceName
# update-rc.d serviceName defaults 99
# update-rc.d -f serviceName remove
# service serviceName start

**RedHat6:(init.d)**
$ chkconfig dcoker on
$ service docker start
or $ /etc/init.d/docker start




