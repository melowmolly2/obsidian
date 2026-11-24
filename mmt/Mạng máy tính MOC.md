---
tags:
  - mmt/moc
---

# 🌐 Mạng máy tính – Map of Content

Giáo trình: *Computer Networking: A Top-Down Approach* – Kurose & Ross, 8th ed.
Môn: COMPSCI 453

---

## Chương 1 – Computer Networks & the Internet

| # | Note | Nội dung chính |
|---|---|---|
| 1.1 | [[C1. Computer networks and the internet/1.1 Internet là gì, giao thức là gì]] | Internet: nuts & bolts / services; giao thức; RFC, IETF |
| 1.2 | [[C1. Computer networks and the internet/1.2 The Network Edge]] | Host, access networks (DSL, HFC, FTTH), physical media |
| 1.3 | [[C1. Computer networks and the internet/1.3 The Network Core]] | Packet switching, circuit switching, routing vs forwarding |
| 1.4 | [[C1. Computer networks and the internet/1.4 Performance]] | Delay ($d_\text{proc}, d_\text{queue}, d_\text{trans}, d_\text{prop}$), loss, throughput |
| 1.5 | [[C1. Computer networks and the internet/1.5 Protocol layers and Their Service Models]] | Internet stack 5 tầng, encapsulation |
| 1.6 | [[C1. Computer networks and the internet/1.6 Network Security]] | Sniffing, IP spoofing, DoS/DDoS |
| 1.7 | [[C1. Computer networks and the internet/1.7 Lịch sử Internet]] | ARPAnet → TCP/IP → Web → hiện đại |
| 1.8 | [[C1. Computer networks and the internet/1.8 Bổ sung]] | Digital divide, quản trị Internet |

---

## Chương 2 – Application Layer

| # | Note | Nội dung chính |
|---|---|---|
| 2.1 | [[C2. Application layer/2.1 Principles of Network Applications]] | Client-server, P2P, socket, transport services |
| 2.2 | [[C2. Application layer/2.2 The Web and HTTP]] | HTTP, persistent/non-persistent, cookies, HTTP/2, Web cache |
| 2.3 | [[C2. Application layer/2.3 Email]] | SMTP, IMAP, user agent, mail server |
| 2.4 | [[C2. Application layer/2.4 DNS]] | Phân cấp DNS, iterative/recursive query, caching, RR |
| 2.5 | [[C2. Application layer/2.5 Video Streaming + CDNS]] | DASH, CDN (enter deep / bring home) |
| 2.6 | [[C2. Application layer/2.6 Socket Programming]] | UDP socket, TCP socket, Python code |
| 2.7 | [[C2. Application layer/2.7 Bổ sung]] | Third-party cookie, web tracking, GDPR |

---

## Chương 3 – Transport Layer

| # | Note | Nội dung chính |
|---|---|---|
| 3.1 | [[C3. Transport Layer/3.1 Giới thiệu về Transport Layer]] | Dịch vụ tầng giao vận, multiplexing vs demultiplexing, so sánh TCP vs UDP |
| 3.2 | [[C3. Transport Layer/3.2 Multiplexing, Demultiplexing]] | Connectionless (UDP) vs connection-oriented (TCP 4-tuple) demux |
| 3.3 | [[C3. Transport Layer/3.3 UDP]] | UDP segment, checksum 16-bit, best-effort service |
| 3.4 | [[C3. Transport Layer/3.4 RDT]] | Nguyên lý truyền tin cậy: rdt1.0 đến rdt3.0, Go-Back-N, Selective Repeat |
| 3.5 | [[C3. Transport Layer/3.5 TCP]] | TCP segment, Seq/ACK number, RTT/Timeout, Flow control (rwnd) |
| 3.6 | [[C3. Transport Layer/3.6 Congestion Control]] | Nguyên nhân và chi phí tắc nghẽn, kiểm soát tắc nghẽn đầu cuối vs mạng hỗ trợ |
| 3.7 | [[C3. Transport Layer/3.7 TCP Congestion Control]] | AIMD, Slow Start, ssthresh, TCP Tahoe/Reno, CUBIC, BBR |
| 3.8 | [[C3. Transport Layer/3.8 Sự tiến hóa của tầng giao vận]] | Thách thức của TCP hiện đại, giao thức QUIC (HTTP/3) over UDP |

---

## Chương 4 – Network Layer: Data Plane

| # | Note | Nội dung chính |
|---|---|---|
| 4.1 | [[C4. Network Layer - Data Plane/4.1 Overview of Network Layer]] | Data plane vs Control plane, Forwarding vs Routing, Best-effort service model |
| 4.2 | [[C4. Network Layer - Data Plane/4.2 What's Inside a Router]] | Cổng vào, Longest prefix match, TCAM, Switching fabric, HOL blocking, Buffering, Lập lịch (FIFO, Priority, RR, WFQ), Net neutrality |
| 4.3 | [[C4. Network Layer - Data Plane/4.3 The Internet Protocol (IPv4, DHCP, NAT, IPv6)]] | IPv4 datagram, Phân mảnh (MTU), Địa chỉ IP, Subnets, CIDR, DHCP 4 bước, NAT, IPv6, Tunneling |
| 4.4 | [[C4. Network Layer - Data Plane/4.4 Generalized Forwarding and SDN]] | Match-plus-action, Bảng luồng (Flow table), OpenFlow 1.0, Thống nhất Router/Switch/Firewall/NAT, P4 |
| 4.5 | [[C4. Network Layer - Data Plane/4.5 Middleboxes]] | Định nghĩa Middlebox (RFC 3234), NFV & Whitebox, IP Hourglass, Nguyên lý End-to-End, Trí thông minh mạng |

---

## Câu hỏi ôn tập

[[Câu hỏi ôn tập]]
[[Bộ câu hỏi ôn tập 3 chương]]

### Bộ câu hỏi theo chương (có đáp án ẩn)

| Chương | Link |
|---|---|
| Index | [[Câu hỏi ôn tập/Index]] |
| Chương 1 | [[Câu hỏi ôn tập/C1 – Câu hỏi ôn tập]] |
| Chương 2 | [[Câu hỏi ôn tập/C2 – Câu hỏi ôn tập]] |
| Chương 3 | [[Câu hỏi ôn tập/C3 – Câu hỏi ôn tập]] |
