# Computer Networks

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

## IP protocol

### Overview

IP protocol uniquely identifies a host in a network.

### Packet Fragmentation

IP protocol is responsible for data fragmentation into packets.
If the total length of a packet exceeds MTU, then a fragmentation happens.

## TCP and UDP

### Overview

The TCP ensures:

1. Reliability of transmission;
2. Bitrate negotiation with a receiver through a `Window size` option.
3. In-order transmission of data segments.

Whereas UDP is faster.

## DHCP - Dynamic Host Configuration Protocol

### Overview

A DHCP server assigns IP addresses to hosts.
A DHCP server can as well provide a host with a DNS server or a default gateway.

### Protocol

1. A host sends a `DHCPDISCOVER` broadcast request.
2. A DHCP server responds with a `DHCPOFFER` response which contains an available IP address.
3. A host responds with `DHCPREQUEST` to claim the IP address.
4. A DHCP server responds with `DHCPACK` to grant the IP address.

## DNS - Domain Name System

### Overview

Before DNS came into existence, users had to manually download `hosts` file,
which is still present on most machines.

### Domain Hierarchy

1. .com, .org, etc. - are all examples of top level domains.
2. company.com, example.com - are all examples of second level domains.
3. blog.company.com, wiki.example.com - are all examples of subdomains.
4. www.blog.company.com - www is an example of a host.

### DNS records types

There are multiple types of DNS records:

* A record = represents an IPv4 address of a host.
* AAAA record = represents IPv6 address of a host.
* NS record = represents a name server which is responsible for a given domain name.
* etc.

### Example of a DNS lookup


    user:~$ dig google.com

    ; <<>> DiG 9.18.39-0ubuntu0.22.04.5-Ubuntu <<>> google.com
    ;; global options: +cmd
    ;; Got answer:
    ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 11346
    ;; flags: qr rd ra; QUERY: 1, ANSWER: 6, AUTHORITY: 0, ADDITIONAL: 1

    ;; OPT PSEUDOSECTION:
    ; EDNS: version: 0, flags:; udp: 65494
    ;; QUESTION SECTION:
    ;google.com.                    IN      A

    ;; ANSWER SECTION:
    google.com.             79      IN      A       64.233.161.100
    google.com.             79      IN      A       64.233.161.102
    google.com.             79      IN      A       64.233.161.101
    google.com.             79      IN      A       64.233.161.113
    google.com.             79      IN      A       64.233.161.139
    google.com.             79      IN      A       64.233.161.138

    ;; Query time: 4 msec
    ;; SERVER: 127.0.0.53#53(127.0.0.53) (UDP)
    ;; WHEN: Mon Aug 31 14:50:13 UTC 2026
    ;; MSG SIZE  rcvd: 135

    user:~$

## STP - Spanning Tree Protocol

### Overview

To avoid cycles, STP constructs a spanning tree for switches in your local network.
