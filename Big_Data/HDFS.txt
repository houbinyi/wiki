Content-Type: text/x-zim-wiki
Wiki-Format: zim 0.4
Creation-Date: 2016-04-29T15:30:59+08:00

====== HDFS ======

hadoop fs -ls /user
hadoop fs -lsr /user   (递归的)

hadoop fs -mkdir /user/trunk

hadoop fs -put test.txt /user/trunk
hadoop fs -put test.txt .  (复制到hdfs当前目录下，首先要创建当前目录)

hadoop fs -get /user/trunk/test.txt . (复制到本地当前目录下)

hadoop fs -cat /user/trunk/test.txt
hadoop fs -tail /user/trunk/test.txt  (查看最后1000字节)

hadoop fs -rm /user/trunk/test.txt

hadoop fs -help ls (查看ls命令的帮助文档)

