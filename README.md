# kafka

## Run with Docker Compose
Start Containers
```
docker-compose up
```
Access the Kafka Tools container
```
docker exec -ti kafka bash
```

### Topics

Create a Topic
```
kafka-topics --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic MY_TOPIC_NAME
```

List Topics
```
kafka-topics --list --bootstrap-server localhost:9092
```

Describe a Topic
```
kafka-topics --describe --bootstrap-server localhost:9092 --topic MY_TOPIC_NAME
```

Increase Partitions
```
kafka-topics --bootstrap-server localhost:9092 --alter --topic MY_TOPIC_NAME  --partitions 10 
```

### Create Producer
```
kafka-console-producer --broker-list localhost:9092 --topic MY_TOPIC_NAME --property "parse.key=true" --property "key.separator=:"
>1:First Message
>2:Second Message
>3:Third Message
```

### Create Consumer
Only new messages
```
kafka-console-consumer --bootstrap-server localhost:9092 --topic MY_TOPIC_NAME --property "print.key=true" --group MY_GROUP_NAME
```
All messages
```
kafka-console-consumer --bootstrap-server localhost:9092 --topic MY_TOPIC_NAME --from-beginning --property "print.key=true"  --group MY_GROUP_NAME
```

### Consumers Groups
Show all
```
kafka-consumer-groups --bootstrap-server localhost:9092 --all-groups --describe
```

## Manually run

Init Zookeeper
```
bin/zookeeper-server-start.sh config/zookeeper.properties
```

Init Kafka
```
bin/kafka-server-start.sh config/server.properties
```
