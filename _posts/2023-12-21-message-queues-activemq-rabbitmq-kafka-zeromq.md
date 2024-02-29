---
layout:     post
title:      Message Queues - 
subtitle:   ActiveMQ, RabbitMQ, Kafka, ZeroMQ
author:     NDA
header-img: img/posts/bg15.png
header-mask: 0.5
catalog:    true
tags:
    - System Design
---

Message queues are a form of asynchronous service-to-service communication. They are important in enhancing a system's scalability, reliability, and maintainability.

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-g7w358m.jpeg)

The list of key features:

1. **Asynchronous Communication**: Allows different parts of a system to communicate without needing to respond immediately, leading to more efficient use of resources.
2. **Decoupling of Services**: Enables services to operate independently, reducing the system's complexity and enhancing maintainability and scalability.
3. **Load Balancing**: Distributes messages evenly across different services or workers, helping to manage workload and improve system performance.
4. **Order Preservation**: Some message queues can ensure that messages are processed in the order they are sent, which is crucial for specific applications.
5. **Scalability**: Facilitates easy scaling of applications by adding more consumers or resources to handle increased message flow.
6. **Rate Limiting and Throttling**: Controls the rate at which messages are processed, which is important for managing resources and preventing system overloads.
7. **Fan-out Capability**: Message queues often include a fan-out mechanism, which allows a single message to be delivered to multiple consumers or services simultaneously.
8. **Data Persistence**: Offers the ability to store messages on disk or in memory until they are successfully processed, ensuring data is not lost in case of system failures.
9. **Message Filtering and Routing**: Allows messages to be routed or filtered based on specific criteria or content, enabling more targeted and efficient processing.

# Components

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-1s8357g.jpeg)

In the context of message queues, the concepts of producers, consumers, and messages form the core of how these systems operate.

1. **Producer** is an application or service responsible for creating and sending messages to the message queue. It does not need to be aware of who will process the message or when it will be processed.
2. **Consumer** is an application or service that retrieves and processes messages from the queue. It acts on the data sent by producers.
3. **Messages** are the data packets sent from producers to consumers. They can vary in size and format, ranging from simple text strings to complex data structures like JSON or XML.
4. **Message Broker** is a middleware tool that facilitates communication between different applications or services by receiving messages from a sender and routing them to the appropriate receiver. It typically provides features like message queuing, routing, transformation, and delivery assurance.

# Messaging Models

Globally, there are two types of messaging: Point-to-Point and Publish-Subscribe.

## Point-to-Point

<div style="float: left; margin: 2em 2em 2em 2em;width:40%">
<img src="https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-mta35lh.jpeg" alt="">
</div>
<p class="line-space" ><br></p>
<p>Messages sent by a producer are placed in a queue and are consumed by a single consumer. It ensures that each message is processed only once by one receiver.</p>
<div style="clear:both;"></div>

## Publish-Subscribe

<div style="float: left; margin: 2em 2em 2em 2em;width:40%">
<img src="https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-h4b35t0.jpeg" alt="">
</div>
<p class="line-space" ><br></p>
<p>Messages are published to a specific topic rather than a queue.
Multiple consumers can subscribe to a topic and receive messages broadcast to that topic.</p>
<div style="clear:both;"></div>

However, some messaging protocols and the brokers that support them use an additional Exchange component for routing. In that case, messages are published to an exchange in the broker first. The Exchange, acting as the routing agent, forwards these messages to the appropriate queue using its routing rules.

The following exchange operating modes are distinguished:

## Direct exchange

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-kkc354q.jpeg)

The message is routed to the queues whose binding key matches the message's routing key.

## Topic exchange

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-lwd35ma.jpeg)

The topic exchange will perform a wildcard match between the routing key and the routing pattern specified in the binding to publish messages to the queue.

## Fanout exchange

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-7ae35p5.jpeg)

A message sent to a fan-out exchange is copied and forwarded to all the queues bound to the exchange.

## Header exchange

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-vhf353s.jpeg)

Header exchanges will use the message header attributes for routing.

## Dead letter

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-u6g35el.jpeg)

Dead letter queues collect messages that couldn’t be processed successfully for various reasons like processing errors, message expiration, or delivery issues.

# Protocols

Message brokers are responsible for delivering messages from producers to consumers. They use specific protocols that define the rules and formats for messaging.

The most popular protocols in this domain are:

## AMQP (Advanced Message Queuing Protocol)

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-a7h35o1.jpeg)

A binary protocol designed for message-oriented middleware with robustness, security, and interoperability. Ideal for complex and reliable enterprise messaging systems.


* **Use Cases**: Enterprise applications, financial systems, and business processes
* **Messaging Model**: point-to-point, publish-subscribe
* **Security**: TLS/SSL, SASL, PLAIN
* **Addressing**: Uses exchange and queue-based addressing with routing capabilities
* **Architecture**: Broker-based

## MQTT (Message Queuing Telemetry Transport)

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-q2i35p7.jpeg)

A lightweight, publish-subscribe network protocol optimized for high-latency or unreliable networks, ideal for IoT scenarios.

* **Use Cases**: IoT devices, home automation, mobile messaging applications
* **Messaging Model**: publish-subscribe
* **Security**: TLS/SSL, SASL, PLAIN
* **Addressing**: It uses topic-based addressing where messages are published to topics
* **Architecture**: Broker-based

## JMS (Java Message Service)

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-fij352s.jpeg)

A Java-based messaging standard offers interfaces for point-to-point and publish-subscribe messaging patterns in Java applications.

* **se Cases**: Enterprise Java applications, integration of multiple Java-based systems
* **Messaging Model**: point-to-point, publish-subscribe
* **Security**: Relies on the underlying Java EE security model
* **Addressing**: Uses JNDI for locating queues and topics
* **Architecture**: It is often implemented on top of enterprise service buses or application servers.

## STOMP (Simple Text Oriented Messaging Protocol)

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-iuk35o3.jpeg)

A simple, text-based protocol that is easy to implement, suitable for scenarios where advanced messaging features are not a priority.

* **Use Cases**: Rapid development environments and simple messaging applications
* **Messaging Model**: point-to-point, publish-subscribe
* **Security**: PLAIN; relies on the underlying transport protocol for encryption
* **Addressing**: Frame-based with headers for destination, content type, etc.
* **Architecture**: Broker-based

## Kafka Protocol

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-f7l35mf.jpeg)

Associated with Apache Kafka, a distributed streaming platform capable of handling high-throughput data streams.

* **Use Cases**: Real-time analytics, data pipelines, stream processing applications
* **Messaging Model**: publish-subscribe
* **Security**: SSL/TLS, SASL
* **Addressing**: Topic-based with partitioning for scalability.
* **Architecture**: Distributed system architecture with brokers and coordination.

## ZMTP (ZeroMQ Message Transport Protocol)

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-7qm35xs.jpeg)

The underlying protocol for ZeroMQ is a high-performance asynchronous messaging library for building scalable, distributed applications.

* **Use Cases**: High-throughput, low-latency applications, microservices architecture.
* **Messaging Model**: request-reply, publish-subscribe, pipeline, exclusive pair, etc.
* **Security**: PLAIN, CurveZMQ, and ZAP
* **Addressing**: Flexible addressing using sockets
* **Architecture**: Library-based, enabling a brokerless design or various brokered configurations

# Brokers

|  | **ActiveMQ** | **RabbitMQ** | **Kafka** | **ZeroMQ**
|-|-|-|-|-|
| Written in | Java | Erlang | Scala | C++
| Cross-platform | yes | yes | yes | yes
| Opensource | yes | yes | yes | yes
| Multiple languages | yes | yes | yes | yes
| Protocols | AMQP, AUTO, MQTT, OpenWire, REST, RSS and Atom, Stomp, WSIF, WS Notification, XMPP, WebSocket | AMQP, STOMP, MQTT, HTTP | Binary over TCP | TCP, UDP, inproc, PGM, IPC, TIPC, NORM, SOCKS5
| QoS | at-least-once at-most-once | at-least-once at-most-once | at-least-once at-most-once exactly-once | at-least-once at-most-once
| Message patterns | Queue, Pub-Sub | Queue, Pub-Sub, RPC | Pub-Sub | Request-Reply, Pub-Sub, Push-Pull, Dealer and Router, Pair, Exclusive Pair, etc
| Persistence | Disk, DB | Mem, Disk | Disk | - 

## ActiveMQ

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-5uo35tx.jpeg)

Apache **ActiveMQ** is an open-source, multi-protocol, Java-based message broker designed by Apache. It's known for its robustness and flexibility, supporting various messaging protocols and clients, making it a versatile choice for integrating disparate systems.

Architecture Features:

* **Multi-Protocol Support**: ActiveMQ supports a wide range of messaging protocols, including AMQP, MQTT, OpenWire, STOMP, and JMS (Java Message Service), making it highly adaptable to different client requirements.
* **JMS Provider**: As a JMS provider, ActiveMQ complies with the JMS API, which allows loose coupling, asynchronous communication, and reliability for Java applications.
* **Broker-Based Architecture**: ActiveMQ uses a broker architecture, where a central broker handles message routing, delivery, and queuing.
* **Pluggable Persistence and Storage**: Offers options for message persistence, including database storage (for durability) and file-system storage, supporting both high-performance and high-durability scenarios.
* **Clustering and Load Balancing**: Supports clustering and load balancing, enabling high availability and scalability.
* **Client-Side Acknowledgements**: Provides different options for message acknowledgments, enhancing message reliability.

Scenarios for Use:

* **Enterprise Integration**: Ideal for integrating different systems within an enterprise, mainly where Java-based or multiple protocols are used.
* **Asynchronous Communication**: Useful in scenarios where decoupling system components is essential, like in microservices architecture.
* **Distributed Computing**: Facilitates message communication in distributed systems, ensuring data consistency and reliability.
* **IoT Communication**: Can be used in IoT setups, especially where MQTT is preferred.

Pros:

* **Versatility in Protocol Support**: One of the key strengths of ActiveMQ is its support for multiple protocols, offering flexibility in various environments.
* **Reliability and Durability**: Provides reliable message delivery and durable storage.
* **Clustering and High Availability**: Supports clustering for load balancing and high availability.
* **JMS Support**: Comprehensive support for the JMS API makes it a strong candidate for Java-based systems.

Cons:

* **Performance**: While robust, ActiveMQ may not match the performance of some newer message brokers, especially in scenarios with extremely high throughput requirements.
* **Complex Configuration**: Can be difficult to configure and manage, especially in clustered setups.
* **Resource Usage**: Might require significant resources, particularly under heavy load, for optimal performance.
* **Management and Monitoring**: While it offers management tools, they might be less comprehensive and user-friendly than those of some newer brokers.

## RabbitMQ

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-l8p35ir.jpeg)

**RabbitMQ** is an open-source message broker software known as a message-oriented middleware. It's written in Erlang and is built on the Open Telecom Platform framework for clustering and failover. RabbitMQ is widely used for handling asynchronous processing, enabling communication between distributed systems through various messaging protocols, primarily AMQP (Advanced Message Queuing Protocol).

Architecture Features:

* **Support for Multiple Messaging Protocols**: While RabbitMQ is primarily known for AMQP, it also supports MQTT, STOMP, and other protocols through plugins.
* **Producer-Consumer Model**: It follows the standard producer-consumer pattern, where producers send messages and consumers receive them, with RabbitMQ acting as the broker.
* **Exchange-Queue Binding**: Messages in RabbitMQ are published to exchanges, which are then routed to bound queues based on routing keys and patterns.
* **Durable and Transient Messaging**: Supports durable (persistent on disk) and transient (in-memory) messages.
* **Clustering and High Availability**: RabbitMQ can be clustered for high availability and scalability, distributing queues among multiple nodes.
* **Flexible Routing**: Offers several exchange types (like direct, topic, fanout, and headers) for diverse routing logic.
Pluggable Authentication and Authorization: Supports pluggable authentication modules, including LDAP.

Scenarios for Use:

* **Asynchronous Processing**: Ideal for decoupling heavy processing tasks in web applications, ensuring responsive user interfaces.
* **Inter-Service Communication**: Used in a microservices architecture for communicating between services.
* **Task Queues**: Well-suited for handling background tasks like sending emails or processing images.
* **Distributed Systems**: Facilitates message communication in distributed systems, maintaining consistency and reliability.

Pros:

* **Reliability**: RabbitMQ is known for its reliability and ability to ensure message delivery.
* **Flexible Routing Capabilities**: Its routing capabilities are more advanced than those of many message brokers.
* **Scalability and High Availability**: Supports scalable clustering, which is crucial for large-scale applications.
* **Wide Protocol Support**: The ability to support multiple messaging protocols increases adaptability.
* **Management Interface**: Comes with a user-friendly management interface, which simplifies monitoring and managing message flows.

Cons:

* **Learning Curve**: Understanding RabbitMQ's routing and setup can be complex for beginners.
* **Memory Usage**: It can be memory-intensive, especially under heavy load, requiring proper monitoring and tuning.
* **Erlang Dependency**: Being built on Erlang, it introduces an additional technology stack that teams might need to familiarize themselves with.
* **Performance Under High Load**: While generally performant, performance tuning might be necessary under extremely high loads or in complex routing scenarios.

## Kafka

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-l3s35u1.jpeg)

Apache **Kafka** is an open-source stream-processing software platform developed by LinkedIn and later donated to the Apache Software Foundation. It's designed to handle high volumes of data and enable real-time data processing. Kafka is a distributed, partitioned, and replicated commit log service.

Architecture Features:

* **Producer-Consumer Model**: Kafka operates on a producer-consumer model. Producers publish messages to Kafka topics, and consumers subscribe to those topics to read the messages.
* **Topics and Partitions**: Data in Kafka is categorized into topics. Each topic can be split into partitions, allowing for parallel data processing. Partitions also enable Kafka to scale horizontally.
* **Distributed System**: Kafka runs as a cluster on one or more servers, and the Kafka cluster stores streams of records in categories called topics.
* **Replication**: Kafka replicates data across multiple nodes (brokers) to ensure fault tolerance. If a node fails, data can be retrieved from other nodes.
* **Zookeeper Coordination**: Kafka uses ZooKeeper for cluster management and coordination, ensuring consistency across the cluster.
* **Commit Log Storage**: Kafka stores all data as a sequence of records (or a commit log), providing durable message storage.

Scenarios for Use:

* **Real-Time Data Processing**: Ideal for real-time analytics and monitoring systems where quick data processing is crucial.
* **Event Sourcing**: Suitable for recording the sequence of events in applications.
* **Log Aggregation**: Effective for collecting and processing logs from multiple services.
* **Stream Processing**: Can be used for complex stream processing tasks like aggregating data streams or real-time filtering.
* **Integration with Big Data Technologies**: Often used with big data tools for data processing and analysis.

Pros:

* **High Throughput**: Can handle high volumes of data and many simultaneous transactions.
* **Scalability**: Easily scalable both horizontally and vertically.
* **Durability and Reliability**: Provides durable storage of messages.
* **Fault Tolerance**: High fault tolerance due to data replication.
* **Flexibility**: Can be used for a wide range of use cases, from messaging systems to activity tracking and log aggregation.

Cons:

* **Complexity**: Setup and management can be complex, especially for large clusters.
* **Resource Intensive**: Can be resource-intensive, requiring a good amount of memory and CPU.
* **Dependency on ZooKeeper**: Relies on ZooKeeper for coordination, adding an extra component to manage.
* **Latency**: While fast, it may not be suitable for use cases requiring extremely low latency.

# ZeroMQ

![](https://hackernoon.imgix.net/images/iOvSeC4bWUctj2q3XImABGDqXVO2-gav3536.jpeg)

**ZeroMQ** (ØMQ, 0MQ, or ZMQ) is a high-performance asynchronous messaging library for distributed or concurrent applications. It's not a message broker but a library that abstracts socket communication into a message-oriented middleware, making it easier to implement complex communication patterns in a scalable way. Developed in C++, ZeroMQ can be used in various programming languages through bindings.

Architecture Features:

* **Socket-Based Communication**: ZeroMQ uses sockets that abstract away the complexity of low-level network programming. These sockets can be used in patterns like publish-subscribe, request-reply, and fan-out.
* **Brokerless Design**: Unlike traditional message brokers, ZeroMQ is brokerless, allowing direct communication between endpoints without requiring a central message broker.
* **Scalable Multithreading**: Provides a way to manage multiple threads with socket-based communication, facilitating scalable I/O bound operations.
* **Asynchronous I/O**: Supports non-blocking, asynchronous I/O operations, which is critical for building responsive, high-performance applications.
* **Language Agnostic**: Offers bindings for multiple programming languages, making it accessible from different technology stacks.

Scenarios for Use:

* **Microservices**: Ideal for inter-service communication in a microservices architecture.
* **High-Performance Computing**: Used in parallel processing systems where performance is critical.
* **Distributed Systems**: Suitable for scenarios requiring complex, distributed messaging patterns without the overhead of a broker.
* **Real-time Communication**: Effective in systems needing low-latency, real-time data exchange.

Pros:

* **High Performance**: ZeroMQ is designed for high throughput and low latency, making it suitable for performance-critical applications.
* **Flexibility in Messaging Patterns**: Supports various messaging patterns, providing flexibility for different communication scenarios.
* **Reduced Complexity**: The brokerless architecture simplifies deployment and reduces system complexity.
* **Scalability**: Facilitates easy scaling of applications with its efficient handling of multiple connections.
* **Lightweight**: Less resource-intensive compared to traditional messaging brokers.

Cons:

* **No Built-in Durability or Message Persistence**: Lacks built-in message durability or persistence support, which must be handled externally.
* **Requires Explicit Management of Connections**: Developers need to manage connections, retries, and error handling, which can add complexity to application logic.
* **Learning Curve**: Understanding and effectively using ZeroMQ's patterns can require a steep learning curve.
* **Lack of a Central Broker**: While this can be an advantage, it also means needing more centralized management, monitoring, and control over the messaging system.
