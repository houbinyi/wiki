A类地址的第一组数字为1～126。
B类地址的第一组数字为128～191。
C类地址的第一组数字为192～223。
10.0.0.0～10.255.255.255
172.16.0.0～172.131.255.255
192.168.0.0～192.168.255.255

net.ipv4.tcp_tw_reuse = 1
net.ipv4.tcp_tw_recycle = 1
net.ipv4.tcp_fin_timeout = 30
net.ipv4.tcp_keepalive_time = 1200   
net.ipv4.ip_local_port_range = 1024    65000   ## 端口分配范围
net.ipv4.tcp_max_tw_buckets = 5000   ## 设置"time_wait"的桶最多容纳5000个

添加完毕以后

sysctl -p 让以上配置生效

nslookup



