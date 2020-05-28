# Clean Kafka Topic Data
## by toptic retention time
```console
topic=xxxxx
kafka-topics.sh --zookeeper localhost:2181 --alter --topic $topic --config retention.ms=1000
kafka-topics.sh --zookeeper localhost:2181 --alter --topic $topic --config retention.hours=168
```

## by purge log files
```console
# shutdown kafka
cd ~/service/kafka && sudo bin/zookeeper-server-stop.sh

# shutdown zookeeper
cd ~/service/kafka && sudo bin/kafka-server-stop.sh

# locate log.dir of server.properties and delete it
sudo rm -rf /tmp/kafka-logs/*

# locate zookeeper data files and delete it
sudo rm -rf ~/data/zookeeper/*

# start zookeeper
cd ~/service/kafka && sudo nohup bin/zookeeper-server-start.sh config/zookeeper.properties > ~/service/logs/zk.log 2>&1 &

# start kafka
cd ~/service/kafka && sudo nohup bin/kafka-server-start.sh config/server.properties > ~/service/logs/kafka-server.log 2>&1 &

# check result
cd ~/service/kafka && bin/zookeeper-shell.sh 10.13.12.36:2181 ls /brokers/ids

```
