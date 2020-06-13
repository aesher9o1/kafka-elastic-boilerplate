# Docker compose explained

## Confluent Zookeeper

> Zookeeper keeps track of status of the Kafka cluster nodes and it also keeps track of Kafka topics, partitions etc.

| Environment Variable                           | Objective                                                                 | Set                                                      |
| ---------------------------------------------- | ------------------------------------------------------------------------- | -------------------------------------------------------- |
| KAFKA_BROKER_ID                                | -                                                                         | 1                                                        |
| KAFKA_ZOOKEEPER_CONNECT                        | Instructs Kafka how to get in touch with ZooKeeper.                       | zookeeper:2181                                           |
| KAFKA_LISTENER_SECURITY_PROTOCOL_MAP           | security protocol to use, per listener name.                              | PLAINTEXT:PLAINTEXT,PLAINTEXT_HOST:PLAINTEXT             |
| KAFKA_INTER_BROKER_LISTENER_NAME               | Defines which listener to use for inter-broker communication              | PLAINTEXT                                                |
| KAFKA_ADVERTISED_LISTENERS                     | external address (host/IP) so that clients can correctly connect to it    | PLAINTEXT://broker:29092,PLAINTEXT_HOST://localhost:9092 |
| KAFKA_AUTO_CREATE_TOPICS_ENABLE                | Create topics automatically when you send messages to non-existing topics | true                                                     |
| KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR         | -                                                                         | 1                                                        |
| KAFKA_TRANSACTION_STATE_LOG_MIN_ISR            | In-Sync Replica set acknowledgments for successful commit                 | 1                                                        |
| KAFKA_TRANSACTION_STATE_LOG_REPLICATION_FACTOR | -                                                                         | 1                                                        |
| KAFKA_GROUP_INITIAL_REBALANCE_DELAY_MS         | GroupCoordinator will delay the initial consumer rebalance.               | 100                                                      |
