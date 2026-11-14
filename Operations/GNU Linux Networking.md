# GNU Linux Networking

## Network Isolation

`ip netns` - create a network namespace to which network interfaces can be attached.

## Copying files over a network

### scp & rsync

`scp` command has the following disadvantages:

1. No preservation of files metadata.
2. No computation of transmission deltas.
3. No preservation of symbolic links.

See "The Linux Bible", 11th edition, discussion on this in Chapter 13.

## DNS

### DNS commands

There are two main commands to get IP addresses:

1. dig;
2. host;

### dig

* Get IP addresses for a domain name using the default DNS server:

      dig google.com

* Get IP addresses for a domain name using a specific DNS server:

      dig google.com @8.8.8.8

* Get a domain name of an IP address with a short output:

      dig -x 142.251.1.139 +short

### /etc/hosts

`/etc/hosts` file is used before any DNS queries.
