route -n
route add default gw 172.16.236.0

route [-nee]
route add [-net|-host] [网域或主机] netmask [mask] [gw|dev]
route del [-net|-host] [网域或主机] netmask [mask] [gw|dev]

添加iptables -t nat -A POSTROUTING -o eth1 -j SNAT --to 192.168.2.173 


参数：
   -n  ：不要使用通讯协定或主机名称，直接使用 IP 或 port number；
   -ee ：使用更详细的资讯来显示
增加 (add) 与删除 (del) 路由的相关参数：
   -net    ：表示后面接的路由为一个网域；
   -host   ：表示后面接的为连接到单部主机的路由；
   netmask ：与网域有关，可以设定 netmask 决定网域的大小；
   gw      ：gateway 的简写，后续接的是 IP 的数值喔，与 dev 不同；
   dev     ：如果只是要指定由那一块网路卡连线出去，则使用这个设定，后面接 eth0 等
