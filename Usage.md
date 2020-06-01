# Kafka Usage

### set partition
```
cd /vagrant-share/software/kafka/
bin/kafka-topics.sh --bootstrap-server localhost:9092 --alter --partitions $2 --topic $1
```
