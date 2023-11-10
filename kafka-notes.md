# kafka important topics
<img src = https://github.com/Kamaljit12/Data-engineering-interview-notes/blob/main/jpg/kafka.jpg>

# What is Kafka?
Apache Kafka is a fast, scalable, fault-tolerant messaging system which enables communication between producers
and consumers using message-based topics. In simple words, it designs a platform for high-end new generation 
distributed applications. Before moving forward in Kafka Tutorial, let’s understand the Messaging System in Kafka.
# Messaging Systems in Kafka
- The main task of managing system is to transfer data from one application to another so that the applications can mainly 
work on data without worrying about sharing it.
- Distributed messaging is based on the reliable message queuing process. Messages are queued non-synchronously 
between the messaging system and client applications.
## There are two types of messaging patterns available:
- Point to point messaging system
- Publish-subscribe messaging system
- ### Point to Point Messaging System:
  - In this messaging system, messages continue to remain in a queue. More 
than one consumer can consume the messages in the queue but only one consumer can consume a particular 
message. After the consumer reads the message in the queue, the message disappears from that queue.
- ### Publish-Subscribe Messaging System :
  - In this messaging system, messages continue to remain in a Topic. 
Contrary to Point to point messaging system, consumers can take more than one topic and consume every 
message in that topic. Message <b>producers</b> are known as <b>publishers</b> and Kafka consumers are known as 
<b>subscribers</b>.

<img src = https://github.com/Kamaljit12/Data-engineering-interview-notes/blob/main/jpg/kafka_1.jpg>

# Before and After Kafka

<img src = https://github.com/Kamaljit12/Data-engineering-interview-notes/blob/main/jpg/kafka_2.jpg>

# Architecture of Kafka

<img src = https://github.com/Kamaljit12/Data-engineering-interview-notes/blob/main/jpg/kafka_3.jpg>

# Components of Kafka
## Kafka Cluster
  - A Kafka cluster is a system of multiple interconnected Kafka brokers (servers). These 
brokers cooperatively handle data distribution and ensure fault tolerance, thereby enabling efficient data 
processing and reliable storage.
## Kafka Broker
  - A Kafka broker is a server in the Apache Kafka distributed system that stores and 
manages the data (messages). It handles requests from producers to write data, and from consumers to 
read data. Multiple brokers together form a Kafka cluster.
## Kafka Zookeeper
  - Apache ZooKeeper is a service used by Kafka for cluster coordination, failover 
handling, and metadata management. It keeps Kafka brokers in sync, manages topic and partition 
information, and aids in broker failure recovery and leader election.
## Kafka Producer
  - In Apache Kafka, a producer is an application that sends messages to Kafka topics. It 
handles message partitioning based on specified keys, serializes data into bytes for storage, and can 
receive acknowledgments upon successful message delivery. Producers also feature automatic retry 
mechanisms and error handling capabilities for robust data transmission.
# Components of Kafka
## Kafka Consumer
  - A Kafka consumer is an application that reads (or consumes) messages from Kafka 
topics. It can subscribe to one or more topics, deserializes the received byte data into a usable format, 
and has the capability to track its offset (the messages it has read) to manage the reading position within 
each partition. It can also be part of a consumer group to share the workload of reading messages.
# What does ZooKeeper do in Kafka Cluster?
- Broker Management:
  - It helps manage and coordinate the Kafka brokers, and keeps a list of them.
- Topic Configuration Management:
  - ZooKeeper maintains a list of topics, number of partitions for each 
topic, location of each partition and the list of consumer groups.
- Leader Election:
  - If a leader (the node managing write and read operations for a partition) fails, 
ZooKeeper can trigger leader election and choose a new leader.
- Cluster Membership:
  - It keeps track of all nodes in the cluster, and notifies if any of these nodes fail.
- Synchronization:
  - ZooKeeper helps in coordinating and synchronizing between different nodes in a Kafka 
cluster.
# Topics in Kafka
- ### Topic:
  - A Kafka Topic is a category or stream name to which messages are published by the Producers and 
retrieved by the Consumers.
- ### Partitions:
  - Each Kafka topic is divided into one or more partitions. Partitions allow for data to be parallelized, 
meaning data can be written to or read from multiple partitions at once, increasing overall throughput.
- ### Producer Data Writing:
  - Producers write data to topics, and they typically choose which partition to write to within 
the topic either in a round-robin style or using a semantic partition function.
- ### Consumer Data Reading:
  - Consumers read data from topics. They read from each partition in the order the data 
was written, maintaining what's known as an offset to track their progress.
- ### Retention Policy:
  - Kafka topics retain all messages for a set amount of time, regardless of whether they have 
been consumed. This time period is configurable per topic.
- ### Immutable Records:
  - Once a message is written to a Kafka topic partition, it can't be changed (it's immutable). It's 
available to consumers to read until.

# Topics in Kafka

<img src = https://github.com/Kamaljit12/Data-engineering-interview-notes/blob/main/jpg/kafka_4.jpg>

# Partitions in Kafka
In Apache Kafka, a partition is a division of a Kafka topic. Partitions play a crucial role in Kafka's functionality and 
scalability. Here's how:
- ### Parallelism:
  - Partitions enable parallelism. Since each partition can be placed on a separate machine (broker), a 
topic can handle an amount of data that exceeds a single server's capacity. This allows producers and consumers 
to read and write data to a topic concurrently, thus increasing throughput.
- ### Ordering:
  - Kafka guarantees that messages within a single partition will be kept in the exact order they were 
produced. However, if order is important across partitions, additional design considerations are needed.
- Replication:
  - ### Partitions of a topic can be replicated across multiple brokers based on the topic's replication factor. 
This increases data reliability and availability.
- Failover:
  - ### In case of a broker failure, the leadership of the partitions owned by that broker will be automatically 
taken over by another broker, which has the replica of these partitions.
- Consumer Groups:
  - ### Each partition can be consumed by one consumer within a consumer group at a time. If 
more than one consumer is needed to read data from a topic simultaneously, the topic needs to have more than 
one partition.
- Offset:
  - ### Every message in a partition is assigned a unique (per partition) and sequential ID called an offset. 
Consumers use this offset to keep track of their position in the partition.

# Partitions in Kafka

<img src = https://github.com/Kamaljit12/Data-engineering-interview-notes/blob/main/jpg/kafka_5.jpg>










