# RabbitMQ

## Overview

RabbitMQ is a message broker which rests on top of some message protocol such as AMQP or MQTT.
AMQP and MQTT define binary representation of a message that is being sent.

A message is binary blob of data.
A size of a queue is determined by the memory and the disk space of a machine which hosts this queue.
You cannot publish a message directly to a queue, you first need to pass it to an exchange.

RabbitMQ team suggests using `pika` Python library.
This library is has a synchronous interface and callback-based flow.

## Messages and Queues

When you produce messages to a queue and you have multiple consumers,
RabbitMQ users Round-Robin algorithm to distribute the messages.

`auto_ack` parameter determines whether a message is acknowledged automatically,
If it is, then if a consumer dies, the message is lost - it is not distributed among other workers.
Essentially, this works great for non-important messages.
If you have an important message, use `channel.basic_ack` after you've processed the message.
You must acknowledge a message on the same channel that has delivered this message.

If RabbitMQ dies or quits, all queues and messages are lost.
To prevent this, mark a queue as durable and a message as persistent.
!!! **Once you've created a queue as non-durable, you cannot redefine durability! It remains non-durable.**
!!! **If you mark a message as persistent,**
!!! **it may still be lost since RabbitMQ may not flush it to the disk or die while receiving this message.**
!!! To prevent this, use **publisher confirms** strategy.

Use `channel#qos` parameter to specify a maximum number of messages that a worker can process at a time.

## Exchanges

Exchanges receive messages from publishers and route them to queues. They can also discard messages.
There are four types of exchanges.
The process of associating an exchange and a queue is called binding.
So, producers pass messages to some exchange and this exchanges further routes this message to queues.

### Fanout Exchange Type

Fanout Exchange ignores routing key and sends a message to all queues which are bound to it.

### Direct Exchange Type

Direct Exchange Type allow you to route messages based on their routing key.
You publish a message with some routing key.
Direct exchange then routes this message to a queue which has been bound to this exchange with the same routing key.
You can assign multiple routing keys to the same queue.

## RabbitMQ Message Delivery Patters

* Work Queue (Task Queue): a message is delivered to only one worker to be processed.
* Pub/Sub: a message is delivered to multiple consumers.
