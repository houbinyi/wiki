netstat -nat //Display current active Internet connections (servers and established connection)
sudo netstat -tulp //Display open ports
sudo netstat -tulpn //Display open ports

netstat -i //Display network interfaces stats (RX/TX etc)    

-t : TCP connections
-u : UDP connections
-e : Established

netstat -lu

使用netstat检查网络状态

　　接下来介绍一个很有用的命令——netstat，使用netstat命令可以监控TCP/IP网络配置和工作状况。它可以显示内核路由表、 活动的网络状态以及每个网络接口的有用的统计数字。欲得详情请阅man page。

　　-a 显示所有Internet连接的有关信息，包括那些正在监听的信息
　　-i 显示所有网络设备的统计数字
　　-c 不断显示网络的更新状态。这个参数使用netstat每秒一次的输出网络状态列表，直到该程序被中断
　　-n 以数字/原始形式显示远程地址、本地地址和端口信息，而不是解析主机名和服务器
　　-o 显示计数器的终止时间和每个网络连接的回退（back off）情况
　　-r 显示内核路由表
　　-t 只显示TCP socket信息，包括正在监听的信息
　　-u 只显示UDP socket信息
　　-v 显示netstat版本信息
　　-w 显示原始（raw）socket信息
　　-x 显示UNIX域socket信息 
