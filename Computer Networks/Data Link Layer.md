# Data Link Layer

## Devices

### Switches

#### Overview

Switches operate on a Data Link Layer.

#### Properties

Switches maintain a CAM table to associate a given switch port with a MAC address.
That said, switches operate on data frames.

#### Objectives

Switches allow one to:

1. Physically connect devices within a LAN.
2. Efficiently route frames within a LAN.

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

## VLAN - Virtual Local Area Network

### Overview

VLANs allow one to groups hosts in a logical network.

## STP - Spanning Tree Protocol

### Overview

To avoid cycles while data frames are routed,
STP constructs a spanning tree for switches in your local network,
which breaks cycles.
