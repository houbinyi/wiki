Content-Type: text/x-zim-wiki
Wiki-Format: zim 0.4
Creation-Date: 2016-12-30T14:14:22+08:00

====== ZooKeeper ======

=== Deploy ===
cp conf/zoo_sample.cfg conf/zoo.cfg

vim conf/zoo.cfg
tickTime=2000
initLimit=10
syncLimit=5
dataDir=/data/zookeeper
clientPort=2181
server.1=10.0.30.138:2555:3555
server.2=10.0.30.139:2555:3555

vim conf/myid
1

=== Lunch ===
bin/zkServer.sh start
bin/zkServer.sh start-foreground


