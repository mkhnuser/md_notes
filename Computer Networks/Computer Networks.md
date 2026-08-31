# Computer Networks

## Addressing

### MAC address - Media Access Control

MAC address uniquely identifies a device in a network.

## IP protocol

### Overview

IP protocol uniquely identifies a host in a network.
IP protocol is responsible for data fragmentation into packets.
IP protocol does not guarantee the reliability of transmission.

### Packet Fragmentation

If the total length of a packet exceeds MTU, then a fragmentation happens.

## ARP - Address Resolution Protocol

### Overview

ARP maps IP addresses to MAC addresses.

Given an IP address,
ARP answers a question of which MAC is given to a machine with this IP address;
an ARP request contains information about a sender IP, a desired IP, a sender MAC;
an ARP reply will have information about a desired IP's MAC.

ARP acts within a local network.

### ARP Spoofing

An attacker might reply to an ARP request with its own IP address.

## TCP and UDP

### Overview

The usage of TCP allows:

1. Reliability of transmission;
2. Bitrate negotiation with a receiver through a `Window size` option.
3. In-order transmission of data segments.

However, UDP is faster.
