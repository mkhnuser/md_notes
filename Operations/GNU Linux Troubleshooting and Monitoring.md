# GNU Linux Troubleshooting and Monitoring

## Troubleshooting

### vmstat

`vmstat` lets you see a general information about how your system performs.

### top / htop

`top` or `htop` allows one to examine the running processes interactively.

### free

`free` displays the amount of free and used RAM.

### df

`df` - disk free; displays the amount of space available on your non-volatile storage.

### du

`du` - disk usage; displays how much space is taken by a file.

### ip route show

`ip route show` displays basic networking info.

### ss

`ss` stands for Socket Statistics.

    ss -tulpn
    ss -s

### tcpdump

`tcpdump` allows one to capture and examine the network traffic.

## Monitoring

### Zabbix

Zabbix is an agent-based software which allows one to monitor an infrastructure.
One has to install a Zabbix Agent on a host which is to be monitored.
After it, the agent sends information to a Zabbix Server directly or through a Zabbix Proxy entity.

Zabbix can be configured as a push system or as a pull system.
A Zabbix Agent might send data to the Zabbix server (push model).
Or, it can wait till a server pulls data from it (pull model).

Zabbix is usually used to monitor your IT infrastructure as a whole.

### Prometheus

Prometheus uses a time-series database to store metrics of your applications.
One can use PromQL to compose queries to this database.

In Prometheus, every metric has a set of key:value pairs which server as metadata for a metric.
This is important for analytics.

Prometheus is a pull system: a Prometheus Server pulls metrics from hosts.

Prometheus for created to monitor containerized environments,
so usually one uses Prometheus to monitor containerized applications.

### Grafana

Grafana is a metric visualization and alerting tool.
