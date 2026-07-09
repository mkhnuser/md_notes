# RabbitMQ

## Overview

RabbitMQ is a message broker which rests on top of message delivery protocols such as:

* AMQP;
* MQTT;
* Or others.

## Message Delivery Patters

* Work Queue (Task Queue, Competing Consumer Pattern):

      A message is delivered to only one worker to be processed.

* Publish / Subscribe:

      A message is delivered to multiple consumers.

### Work Queue (Task Queue, Competing Consumer Pattern)

A message is delivered to precisely one worker.
Round Robin algorithm is used to distribute messages among workers by default.

### Publish / Subscribe

A message is delivered to multiple consumers using exchanges, queues and the binding process.

### Default Exchange

The exchange which routes a message to a queue with the name equal to the routing key.

### Fanout Exchange

Fanout Exchange ignores routing key and sends a message to all queues which are bound to it.

### Direct Exchange

Direct Exchange allows you to route messages based on their routing key.
You can assign multiple routing keys to the same queue.

### Topic Exchange

Topic Exchange allows you to use a composite routing key: `quick.brown.fox`.

### Headers Exchange

It is possible to route messages based on headers mapping.

### Exchange-to-Exchange Binding

It it possible to bind an exchange to another exchange.

### Consistent Hashing Strategy

Consistent hashing is possible as well.

### Alternative Exchanges

You can bind an alternative exchange to a main exchange so that
when a message with a bad routing key arrives,
you redirect this message this exchange.

### Deadletter Exchanges

You might want to route messages which have expired to a particular exchange.

## Data Safety in RabbitMQ 

Understand that data safety is a mutual responsibility of a Publisher, RabbitMQ, and Consumer.
Conceptually, your data flow looks like this: Publisher <-> RabbitMQ <-> Consumer.

1. Publisher <-> RabbitMQ: Publisher Confirms Strategy.

        RabbitMQ can signify to a publisher that a message has been received.

2. RabbitMQ Death Data Safety.

        Consider the persistence of messages on a disk.

3. RabbitMQ <-> Consumer: Consumer Acknowledgement Strategy.

        Consumer can send ACK to signify that a message has been processed successfully.

## Data Deduplication

You should be ready to handle data duplicates.
