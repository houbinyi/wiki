Content-Type: text/x-zim-wiki
Wiki-Format: zim 0.4
Creation-Date: 2016-07-05T11:26:36+08:00

====== Kafka ======

=== Deploy ===
**Install**
tar -xzf kafka_2.11-0.10.0.0.tgz
cd kafka_2.11-0.10.0.0

=== Lunch ===
**Start Server**
bin/zookeeper-server-start.sh config/zookeeper.properties
bin/kafka-server-start.sh config/server.properties

**Create a topic**
bin/kafka-topics.sh --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic test
bin/kafka-topics.sh --list --zookeeper localhost:2181

**Send some messages**
bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test

**Start a consumer**
bin/kafka-console-consumer.sh --zookeeper localhost:2181 --topic test --from-beginning

**Setting up a multi-broker cluster**
cp config/server.properties config/server-1.properties
cp config/server.properties config/server-2.properties

=== Core Concept ===
partion
replication
consummer group



