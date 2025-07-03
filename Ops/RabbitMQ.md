# RabbitMQ

## Overview

RabbitMQ is a message broker which rests on top of message delivery protocols such as AMQP, MQTT, or others.

## Messages and Queues

A message can be anything.
A size of a queue is determined by the memory and the disk space of a machine which hosts this queue.
You cannot publish a message directly to a queue, you first need to pass it to an exchange.

## RabbitMQ Message Delivery Patters

* Work Queue (Task Queue, Competing Consumer Pattern): a message is delivered to only one worker to be processed.
* Publish / Subscribe: a message is delivered to multiple consumers.

### Work Queue (Task Queue, Competing Consumer Pattern)

A message is delivered to precisely one worker.
Round Robin algorithm is used to distribute messages among workers.

### Publish / Subscribe

A message is delivered to multiple consumers using exchanges, queues and binding process.

## Exchanges

Exchanges receive messages from publishers and route them to queues.
The process of associating an exchange and a queue is called binding.
So, producers pass messages to some exchange and this exchanges further routes this message to queues based on binding.
You use routing key for routing.

### Fanout Exchange Type

Fanout Exchange ignores routing key and sends a message to all queues which are bound to it.

### Direct Exchange Type

Direct Exchange Type allow you to route messages based on their routing key.
You publish a message with some routing key.
Direct exchange then routes this message to a queue which has been bound to this exchange with the same routing key.
You can assign multiple routing keys to the same queue.

### Topic Exchange

Topic Exchange allows you to use a composite routing key: *quick.brown.fox*.
You can bind a queue to a Topic Exchange with *quick.#*;
in this case the queue will receive messages with the following routing keys:
*quick.rabbit*, *quick.another.animal*, etc.

### Other Exchanges

There are some other exchanges which are less popular.

## Data Safety in RabbitMQ 

Understand that data safety is a mutual responsibility of a Publisher, RabbitMQ, and Consumer.
Conceptually, your data flow looks like this: Publisher <-> RabbitMQ <-> Consumer.

Suppose you want to send your messages reliably;
you want to ensure that once you've sent a message to RabbitMQ, it does not get lost.
Then you need to implement the strategies below.

Here are the three things which can go wrong:

1. Once a Publisher sends a message, it may not be delivered to RabbitMQ.
2. RabbitMQ as such dies / reloads.
3. Consumer dies while processing the message.

1. Publisher <-> RabbitMQ Data Safety: Publisher Confirms Strategy.

      Publisher Confirms mechanism ensures that RabbitMQ has absolutely received a message from a Publisher.
      Essentially, once RabbitMQ has successfully received a message from a Publisher,
      it sends a confirmation message.

2. RabbitMQ Death Data Safety.

      If RabbitMQ dies or quits, all queues and messages are lost by default.
      To prevent this, mark a queue as durable and a message as persistent.
      This ensures that queues and messages will survive RabbitMQ death.
      RabbitMQ archives persistence and durability by writing data to a disk.

      Once you've created a queue as non-durable, you cannot redefine its durability.
      If you mark a message as persistent,
      it may still be lost since RabbitMQ may not flush it to the disk or die while receiving this message.
      To prevent this, use **Publisher confirms** Strategy.

3. RabbitMQ <-> Consumer Data Safety: Consumer Acknowledgement Strategy.

      Consumer Acknowledgement Mechanism ensures that if a worker (consumer) dies, or
      its channel is closed, or connection is closed, or TCP connection is lost
      the message will still be requeued and redelivered to a worker.

      A default ack timeout of 30 minutes is set.
      Be careful of a message duplication: a message may be received more than once by your worker...
