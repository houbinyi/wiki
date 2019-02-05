Content-Type: text/x-zim-wiki
Wiki-Format: zim 0.4
Creation-Date: 2016-08-22T17:06:11+08:00

====== Storm ======

=== Deploy ===
vim storm.yaml

storm.zookeeper.servers:
	 - "192.168.187.16"
	 - "192.168.180.101"
nimbus.host: "192.168.187.16"
storm.local.dir: "/data/storm/data"


bin/storm nimbus
bin/storm supervisor
bin/storm ui
