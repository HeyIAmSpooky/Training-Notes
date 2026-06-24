## What is Wireshark?

**Wireshark** is the world's foremost and most widely-used network protocol analyzer. It lets you capture and interactively browse network traffic on a computer network. It's used for network troubleshooting, analysis, software and protocol development, and security auditing.

Download from [wireshark.org](https://www.wireshark.org/download.html). Pre-installed on Kali Linux. Command-line version: `tshark`.

## 🔍 Filter Types

### Capture Filters (BPF)

Applied BEFORE capturing. Uses Berkeley Packet Filter syntax. Reduces capture file size.

### Display Filters

Applied AFTER capturing. More powerful syntax. Filters what you see, not what's captured.

## 🔣 Display Filter Operators

|Operator|Description|Example|
|---|---|---|
|==|Equal|ip.addr == 192.168.1.1|
|!=|Not equal|ip.addr != 10.0.0.1|
|>|Greater than|tcp.port > 1024|
|<|Less than|frame.len < 100|
|>=|Greater than or equal|tcp.window_size >= 65535|
|<=|Less than or equal|ip.ttl <= 64|
|contains|Contains string|http contains "password"|
|matches|Regex match|http.host matches ".*\.com"|
|&&|Logical AND|ip.src == 10.0.0.1 && tcp.port == 80|
|\||Logical OR|tcp.port == 80 \| tcp.port == 443|
|!|Logical NOT|!arp|

## 🌐 IP Address Filters

|Filter|Description|
|---|---|
|ip.addr == 192.168.1.1|Source or destination IP|
|ip.src == 192.168.1.1|Source IP only|
|ip.dst == 192.168.1.1|Destination IP only|
|ip.addr == 192.168.1.0/24|Subnet (CIDR notation)|
|!(ip.addr == 192.168.1.1)|Exclude specific IP|
|ip.ttl == 64|TTL value|
|ip.version == 4|IPv4 only|
|ipv6.addr == ::1|IPv6 address|

## 🔌 TCP Filters

|Filter|Description|
|---|---|
|tcp|All TCP traffic|
|tcp.port == 80|Source or destination port|
|tcp.srcport == 443|Source port|
|tcp.dstport == 22|Destination port|
|tcp.flags.syn == 1|SYN flag set|
|tcp.flags.ack == 1|ACK flag set|
|tcp.flags.fin == 1|FIN flag set|
|tcp.flags.reset == 1|RST flag set|
|tcp.analysis.retransmission|TCP retransmissions|
|tcp.stream eq 5|Follow TCP stream #5|

## 📡 UDP Filters

|   |   |
|---|---|
|udp|All UDP traffic|
|udp.port == 53|DNS port|
|udp.srcport == 67|DHCP server port|
|udp.length > 1000|Large UDP packets|

## 🌐 HTTP Filters

|Filter|Description|
|---|---|
|http|All HTTP traffic|
|http.request|HTTP requests only|
|http.response|HTTP responses only|
|http.request.method == "GET"|GET requests|
|http.request.method == "POST"|POST requests|
|http.response.code == 200|OK responses|
|http.response.code == 404|Not found responses|
|http.response.code >= 400|Error responses|
|http.host contains "example"|Host contains string|
|http.request.uri contains "login"|URI contains string|
|http.user_agent contains "Mozilla"|User agent filter|
|http.cookie|Packets with cookies|
|http.content_type contains "image"|Image content|

## 🔤 DNS Filters

|   |   |
|---|---|
|dns|All DNS traffic|
|dns.qry.name contains "example"|Query name contains string|
|dns.qry.type == 1|A records|
|dns.qry.type == 28|AAAA records|
|dns.flags.response == 0|DNS queries only|
|dns.flags.response == 1|DNS responses only|

## 📦 Other Protocol Filters

|Filter|Description|
|---|---|
|icmp|ICMP traffic (ping)|
|arp|ARP traffic|
|dhcp|DHCP traffic|
|tls|TLS/SSL traffic|
|ssh|SSH traffic|
|ftp|FTP traffic|
|smb \| smb2|SMB traffic|
|rdp|RDP traffic|
|kerberos|Kerberos traffic|

## 📹 Capture Filters (BPF Syntax)

Applied before capture in Capture → Options. Uses different syntax than display filters.

|Filter|Description|
|---|---|
|host 192.168.1.1|Traffic to/from IP|
|src host 192.168.1.1|Traffic from IP|
|dst host 192.168.1.1|Traffic to IP|
|net 192.168.1.0/24|Traffic to/from subnet|
|port 80|Traffic on port 80|
|tcp port 443|TCP port 443|
|udp port 53|UDP port 53|
|portrange 1-1024|Port range|
|not arp|Exclude ARP|
|tcp and port 80|TCP on port 80|

## ⌨️ Useful Shortcuts & Features

|Action|Shortcut/Method|
|---|---|
|Follow TCP Stream|Right-click → Follow → TCP Stream|
|Follow HTTP Stream|Right-click → Follow → HTTP Stream|
|Export Objects (files)|File → Export Objects → HTTP/SMB/etc.|
|Protocol Hierarchy|Statistics → Protocol Hierarchy|
|Conversations|Statistics → Conversations|
|Endpoints|Statistics → Endpoints|
|IO Graph|Statistics → IO Graph|
|Start Capture|Ctrl+E|
|Stop Capture|Ctrl+E|
|Find Packet|Ctrl+F|
|Next Packet|Ctrl+N|

## 🖥️ TShark (Command-Line)

```
# Capture on interface
```

## 📚 Additional Resources

- [Official Wireshark Documentation](https://www.wireshark.org/docs/)
- [Display Filter Reference](https://wiki.wireshark.org/DisplayFilters)
- [Capture Filter Reference](https://wiki.wireshark.org/CaptureFilters)
- [Download Wireshark](https://www.wireshark.org/download.html)