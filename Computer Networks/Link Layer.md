# Link Layer

## Addressing

### MAC address - Media Access Control

MAC address uniquely identifies a device in a network.

## ARP - Address Resolution Protocol

### Overview

ARP maps IP addresses to MAC addresses.

### Protocol

Given an IP address,
ARP answers a question of which MAC is given to a machine with this IP address;
an ARP request contains information about a sender IP, a desired IP, a sender MAC;
an ARP reply will have information about a desired IP's MAC.

ARP acts within a local network.

### ARP Spoofing

An attacker might reply to an ARP request with its own IP address.

## STP - Spanning Tree Protocol

### Overview

To avoid cycles, STP constructs a spanning tree for switches in your local network.
