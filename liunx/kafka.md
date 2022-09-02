# kafka 常用命令
```
kafka-topics.sh --list --bootstrap-server slave100:9092,slave101:9092,slave102:9092

kafka-topics.sh --create --topic test1 --replication-factor 1 --partitions 1 --bootstrap-server slave100:9092,slave101:9092,slave102:9092

kafka-console-consumer.sh --topic test1 --from-beginning --bootstrap-server slave100:9092,slave101:9092,slave102:9092

kafka-console-producer.sh --topic test1 --bootstrap-server slave100:9092,slave101:9092,slave102:9092

kafka-topics.sh --describe --topic test1 --bootstrap-server slave100:9092,slave101:9092,slave102:9092

kafka-topics.sh --delete --topic test1 --bootstrap-server slave100:9092,slave101:9092,slave102:9092```