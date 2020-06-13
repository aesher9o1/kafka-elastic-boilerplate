# Docker compose explained

> Docker images used from [Confluentinc](https://github.com/confluentinc/cp-docker-images/)

#### [cp-base-new](https://github.com/confluentinc/common-docker/tree/master/base)

1. Extents and Open JDK image
2. Installs Python and python tools
3. Install [confluent docker utils](https://github.com/confluentinc/confluent-docker-utils) used for testing docker images
4. Removes PIP and git
5. Remove cached shit from image
6. Remove requirement.txt file
7. Extract artifacts downloaded to `/etc/confluent/docker`

## [Confluent Zookeeper](https://github.com/confluentinc/kafka-images/blob/master/zookeeper/Dockerfile.deb8)

> Zookeeper keeps track of status of the Kafka cluster nodes and it also keeps track of Kafka topics, partitions etc. Extends cp-base and installs repos

`VOLUME ["/var/lib/${COMPONENT}/data", "/var/lib/${COMPONENT}/log", "/etc/${COMPONENT}/secrets"]`

## Confluent Broker

> Each Kafka Broker has a unique ID (number). Kafka Brokers contain topic log partitions. Connecting to one broker bootstraps a client to the entire Kafka cluster.

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

## Confluent Schema Registry

> Confluent Schema Registry provides a serving layer for your metadata. It provides a RESTful interface for storing and retrieving your Avro®, JSON Schema, and Protobuf schemas. It stores a versioned history of all schemas based on a specified subject name strategy, provides multiple compatibility settings and allows evolution of schemas according to the configured compatibility settings and expanded support for these schema types. It provides serializers that plug into Apache Kafka® clients that handle schema storage and retrieval for Kafka messages that are sent in any of the supported formats.
