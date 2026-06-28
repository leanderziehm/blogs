# ISO Model vs TCP/IP Model



tcp splits by mtu



## IP&#x20;

Source IP\
Destination IP\
TTL\
Protocol



```
Ethernet
  src MAC = aa:bb:cc
  dst MAC = dd:ee:ff

IP
  src = 192.168.1.100
  dst = 93.184.216.34

TCP
  sport = 52341
  dport = 80

HTTP
  GET / HTTP/1.1
```

ip protocol

6 = TCP\
17 = UDP\
1 = ICMP





| OSI Layer       | Examples                  | Uses Ports?                                 |
| --------------- | ------------------------- | ------------------------------------------- |
| 7. Application  | HTTP, HTTPS, DNS, SMTP    | No (but services are associated with ports) |
| 6. Presentation | TLS, encryption, encoding | No                                          |
| 5. Session      | Session management        | No                                          |
| 4. Transport    | TCP, UDP                  | **Yes**                                     |
| 3. Network      | IP, ICMP                  | No                                          |
| 2. Data Link    | Ethernet, Wi-Fi           | No                                          |
| 1. Physical     | Cables, radio waves       | No                                          |

## ISO Model

| Layer | Name              |   |
| ----- | ----------------- | - |
| 7     | Application Layer |   |
| 6     |                   |   |
| 5     |                   |   |
| 4     |                   |   |
| 3     |                   |   |
| 2     |                   |   |
| 1     | Physical Layer    |   |

## TCP IP Model

| TCP/IP Layer | Examples                    |
| ------------ | --------------------------- |
| Application  | HTTP, HTTPS, DNS, SMTP, SSH |
| Transport    | TCP, UDP                    |
| Internet     | IP, ICMP                    |
| Link         | Ethernet, Wi-Fi, ARP        |



### Ethernet (Layer 2)

An Ethernet frame is usually:

```
+------------------+
| Ethernet Header  |
+------------------+
| IP Packet        |
+------------------+
```

Common fields:

| Field           | Purpose                      |
| --------------- | ---------------------------- |
| Destination MAC | Who should receive the frame |
| Source MAC      | Who sent the frame           |
| EtherType       | What protocol is inside      |

Example:

```
Dst MAC: ff:ff:ff:ff:ff:ffSrc MAC: 00:11:22:33:44:55Type: 0x0800 (IPv4)
```

Common EtherTypes:

| Value  | Meaning           |
| ------ | ----------------- |
| 0x0800 | IPv4              |
| 0x86DD | IPv6              |
| 0x0806 | <p></p><p>ARP</p> |





When you're looking at packet crafting (Scapy, Wireshark, networking), it's useful to know the fields that appear most often and what they do.

### Ethernet (Layer 2)

An Ethernet frame is usually:

```
+------------------+
| Ethernet Header  |
+------------------+
| IP Packet        |
+------------------+
```

Common fields:

| Field           | Purpose                      |
| --------------- | ---------------------------- |
| Destination MAC | Who should receive the frame |
| Source MAC      | Who sent the frame           |
| EtherType       | What protocol is inside      |

Example:

```
Dst MAC: ff:ff:ff:ff:ff:ff
Src MAC: 00:11:22:33:44:55
Type: 0x0800 (IPv4)
```

Common EtherTypes:

| Value  | Meaning |
| ------ | ------- |
| 0x0800 | IPv4    |
| 0x86DD | IPv6    |
| 0x0806 | ARP     |

Scapy:

```python
Ether(dst="ff:ff:ff:ff:ff:ff")
```

***

### IP (Layer 3)

The IP header tells the network where the packet should go.

Common fields:

| Field | Purpose                  |
| ----- | ------------------------ |
| src   | Source IP                |
| dst   | Destination IP           |
| ttl   | Hop limit                |
| proto | TCP, UDP, ICMP, etc.     |
| id    | Fragmentation identifier |
| flags | Fragmentation control    |
| len   | Packet length            |

Example:

```python
IP(
    src="192.168.1.10",
    dst="8.8.8.8",
    ttl=64
)
```

Typical values:

| Field | Common Value                                     |
| ----- | ------------------------------------------------ |
| ttl   | 64 (Linux), 128 (Windows), 255 (network devices) |
| proto | 6=TCP, 17=UDP, 1=ICMP                            |

#### Most commonly used IP protocol numbers

These are the ones you’ll encounter constantly on the internet and in most networks:

* **6 — TCP (Transmission Control Protocol)**\
  Used for most reliable internet communication: web browsing (HTTPS), email, file transfers, APIs, etc.
* **17 — UDP (User Datagram Protocol)**\
  Used for fast, lightweight communication: streaming, DNS, VoIP, online gaming.
* **1 — ICMP (Internet Control Message Protocol)**\
  Used for diagnostics and network control (e.g., `ping`, `traceroute`).
* **41 — IPv6 encapsulation (IPv6-in-IPv4 tunneling)**\
  Used in transition mechanisms between IPv4 and IPv6.
* **47 — GRE (Generic Routing Encapsulation)**\
  Common in VPNs and tunneling setups.
* **50 — ESP (Encapsulating Security Payload)** and **51 — AH (Authentication Header)**\
  Used in IPsec VPNs for encryption and authentication.
* **89 — OSPF (Open Shortest Path First)**\
  A major routing protocol used inside enterprise networks.

#### Also common in specific environments

* **132 — SCTP (Stream Control Transmission Protocol)** → telecom and signaling systems
* **88 — EIGRP** → Cisco-heavy enterprise networks
* **115 — L2TP** → VPN tunnels
* **112 — VRRP** → router redundancy setups

A packet often looks like:

```
IP
  src=192.168.1.10
  dst=8.8.8.8
  ttl=64
  proto=6
```

***

### TCP (Layer 4)

TCP has the most important fields for connection-oriented networking.

Common fields:

| Field   | Purpose                 |
| ------- | ----------------------- |
| sport   | Source port             |
| dport   | Destination port        |
| seq     | Sequence number         |
| ack     | Acknowledgment number   |
| flags   | SYN, ACK, FIN, etc.     |
| window  | Receive window size     |
| options | MSS, Window Scale, SACK |

Example:

```python
TCP(
    sport=50000,
    dport=80,
    flags="S"
)
```

#### Most common flags

| Flag | Meaning |
| ---- | ------- |
| S    | SYN     |
| A    | ACK     |
| F    | FIN     |
| R    | RST     |
| P    | PSH     |

Common combinations:

| Flags | Meaning                    |
| ----- | -------------------------- |
| S     | Connection request         |
| SA    | SYN+ACK                    |
| A     | Normal established traffic |
| FA    | Connection close           |
| RA    | Connection reset           |

***

#### Common TCP options

Modern SYN packets usually contain:

| Option         | Purpose              |
| -------------- | -------------------- |
| MSS            | Maximum Segment Size |
| Window Scale   | Larger windows       |
| SACK Permitted | Selective ACK        |
| Timestamp      | RTT measurement      |

Example Wireshark output:

```
MSS=1460
SACK Permitted
Window Scale=7
Timestamp
```

***

### HTTP (Layer 7)

HTTP is text-based.

A typical request:

```http
GET /index.html HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0
Accept: */*
Connection: keep-alive
```

#### Most common request headers

| Header         | Purpose                |
| -------------- | ---------------------- |
| Host           | Target website         |
| User-Agent     | Client identity        |
| Accept         | Content types accepted |
| Cookie         | Session data           |
| Authorization  | Authentication         |
| Content-Type   | Type of body data      |
| Content-Length | Body size              |
| Referer        | Previous page          |
| Connection     | keep-alive / close     |

Example:

```http
POST /login HTTP/1.1
Host: example.com
Content-Type: application/json
Content-Length: 42
```

***

#### Common response headers

Server response:

```http
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 1024
Server: nginx
Set-Cookie: session=abc123
```

Common response headers:

| Header         | Purpose         |
| -------------- | --------------- |
| Content-Type   | MIME type       |
| Content-Length | Size            |
| Server         | Server software |
| Set-Cookie     | Session cookie  |
| Cache-Control  | Caching rules   |
| Location       | Redirect target |

***

#### Ethernet

```
dst MAC
src MAC
type
```

#### IP

```
src IP
dst IP
ttl
protocol
```

#### TCP

```
sport
dport
seq
ack
flags
window
```

#### HTTP

```
method (GET/POST)
Host
User-Agent
Content-Type
Cookie
Status Code
```

A real web request stack might look like:

```
Ethernet
  src=00:11:22:33:44:55
  dst=aa:bb:cc:dd:ee:ff

IP
  src=192.168.1.10
  dst=93.184.216.34
  ttl=64

TCP
  sport=53124
  dport=443
  seq=12345
  ack=67890
  flags=ACK

HTTP
  GET /
  Host: example.com
```
