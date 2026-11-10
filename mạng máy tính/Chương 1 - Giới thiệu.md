# Chương 1: Giới thiệu (Introduction)

> Nguồn: *Computer Networking: A Top-Down Approach, 9th ed.* - Chapter 1

---

## 1.1 Internet là gì?

### Nuts-and-bolts view
- **Internet** = tập hợp **thiết bị cuối** (hosts/end systems) kết nối bởi **liên kết truyền thông** (communication links) và **bộ định tuyến** (packet switches/routers).

### Thành phần
| Loại | Ví dụ |
|------|-------|
| **End systems** | Máy tính, điện thoại, IoT (tivi, tủ lạnh, xe hơi, cảm biến) |
| **Communication links** | Cáp đôi xoắn (twisted pair), cáp quang (fiber), vô tuyến (WiFi, 4G/5G), vệ tinh |
| **Packet switches** | Router, Link-layer switch |

### Giao thức (Protocol)
> **Định nghĩa**: Quy định *định dạng*, *thứ tự* các thông điệp trao đổi giữa các thực thể, và *hành động* khi gửi/nhận.

**Ví dụ**: HTTP, TCP, IP, WiFi, 4G/5G, DNS, TLS, BGP, OSPF...

---

## 1.2 Cạnh mạng (Network Edge)

### Hosts (End Systems)
- Chạy **ứng dụng mạng** (client/server: Web, Email, Video, P2P...)
- Được gọi là **end systems** vì nằm ở "cạnh" của mạng.

### Access Network (Mạng truy cập)
Kết nối end system đến **router đầu tiên** (edge router).

| Loại | Băng thông đặc trưng | Đặc điểm |
|------|---------------------|----------|
| **DSL** | ~24 Mbps down / 2.5 Mbps up | Dùng cáp điện thoại, dedicated line |
| **Cable (HFC)** | ~100+ Mbps down / 10+ Mbps up | Shared broadcast medium |
| **FTTH** | 100 Mbps - 10 Gbps | Fiber đến nhà, dedicated |
| **4G LTE** | ~10-50 Mbps | Di động, shared |
| **5G NR** | ~100 Mbps - 1+ Gbps | Di động, low latency, network slicing |
| **WiFi (802.11ax/be)** | ~100 Mbps - 1+ Gbps | Wireless LAN, unlicensed spectrum |
| **Ethernet** | 100 Mbps - 100 Gbps | Enterprise/campus, wired |

### Physical Media (Phương tiện vật lý)
- **Guided**: Twisted pair (Cat5e/6/6a/7), Coaxial, Fiber (single-mode/multi-mode)
- **Unguided**: Radio waves (WiFi, Cellular), Microwave, Satellite

---

## 1.3 Lõi mạng (Network Core)

### Chuyển mạch gói (Packet Switching) - Kiến trúc Internet
- Dữ liệu chia thành **packets (gói tin)**
- **Store-and-forward**: Router nhận toàn bộ gói → kiểm tra → chuyển tiếp
- **Transmission delay** = $L/R$ (độ dài gói / băng thông link)
- **Queueing delay + Loss**: Khi arrival rate > link rate → hàng đợi đầy → drop packet

### Chuyển mạch mạch (Circuit Switching) - Mạng điện thoại truyền thống
- **Reservation**: Cấp phát tài nguyên chuyên dụng (bandwidth, time slot)
- **FDMA / TDMA**: Frequency/Time Division Multiplexing
- **Guaranteed performance**, nhưng kém hiệu quả cho bursty data traffic

### Cấu trúc Internet: "Network of Networks"
```
Tier 1 ISP (Global backbone) ←→ Tier 1 ISP (peering)
      ↓                                    ↓
Tier 2 ISP (Regional) ←→ Tier 2 ISP (peering)
      ↓
Tier 3 ISP / Access ISP (Last mile) → End users
      ↓
IXP (Internet Exchange Point) - Peering vật lý
CDN (Content Delivery Network) - Cache content gần user
```

---

## 1.4 Hiệu suất mạng (Performance Metrics)

| Chỉ số | Công thức / Mô tả | Nguyên nhân |
|--------|-------------------|-------------|
| **Loss (Mất gói)** | Gói bị drop khi queue đầy | Buffer overflow, congestion |
| **Delay (Độ trễ)** | $d_{total} = d_{proc} + d_{queue} + d_{trans} + d_{prop}$ | Processing, queueing, transmission, propagation |
| **Throughput (Thông lượng)** | Tốc độ truyền thực tế = min(bottleneck link rates) | Bottleneck link, congestion, protocol overhead |

### Độ trễ end-to-end (ví dụ)
- $d_{trans} = L/R$ (ví dụ: 1500 bytes / 1 Gbps = 12 μs)
- $d_{prop} = \text{distance} / \text{speed of light}$ (ví dụ: 5000 km / $2 \times 10^8$ m/s = 25 ms)
- **RTT** (Round Trip Time) ≈ 2 × propagation + queueing + processing

---

## 1.5 Mô hình lớp (Protocol Layers)

### 5 lớp (Internet Model) vs 7 lớp (OSI)
| # | Internet (5 lớp) | OSI (7 lớp) | Chức năng chính |
|---|------------------|-------------|-----------------|
| 5 | **Application** | Application | Ứng dụng người dùng (HTTP, DNS, SMTP...) |
| 4 | **Transport** | Transport | Process-to-process (TCP, UDP) |
| 3 | **Network** | Network | Host-to-host routing (IP, OSPF, BGP) |
| 2 | **Link** | Data Link | Hop-to-hop (Ethernet, WiFi, MAC) |
| 1 | **Physical** | Physical | Bit transmission trên medium |

### Encapsulation (Đóng gói)
```
Application Data
    ↓ + Transport Header (TCP/UDP)
Segment
    ↓ + Network Header (IP)
Datagram
    ↓ + Link Header/Trailer (Ethernet)
Frame
    ↓ Physical Layer
Bits on wire
```
Mỗi lớp thêm **header** (và đôi khi **trailer**) → gọi chung là **PDU** (Protocol Data Unit).

### Service Models
- **Connectionless** (IP, UDP): Best-effort, no state
- **Connection-oriented** (TCP): Handshake, state, reliable
- **Reliable vs Unreliable**: TCP (ACK, retransmit) vs UDP/IP (no guarantee)
- **Flow/Congestion Control**: TCP có, UDP không

---

## 1.6 An ninh mạng (Security Overview)

### Các mối đe dọa chính
| Tấn công | Mô tả | Ví dụ |
|----------|-------|-------|
| **Eavesdropping (Nghe lén)** | Passive sniffing | Wireshark trên WiFi open |
| **Spoofing (Giả mạo)** | Fake source IP/MAC/Email | IP spoofing, ARP poisoning |
| **Man-in-the-Middle** | Can thiệp, sửa đổi traffic | SSL stripping, DNS hijack |
| **DoS/DDoS** | Làm đầy tài nguyên | SYN flood, amplification |
| **Malware** | Virus, worm, ransomware, botnet | Mirai, WannaCry |

### Các lớp bảo vệ
- **Application**: PGP, S/MIME, HTTPS
- **Transport**: TLS/SSL
- **Network**: IPsec
- **Link**: WPA2/WPA3, MACsec
- **Physical**: Physical security, TEMPEST

---

## 1.7 Lịch sử tóm tắt

| Năm | Sự kiện |
|-----|---------|
| 1961 | Kleinrock: Packet switching theory |
| 1969 | ARPANET: 4 node đầu tiên |
| 1972 | Email (Ray Tomlinson), @ symbol |
| 1973 | Ethernet (Metcalfe), TCP idée (Cerf/Kahn) |
| 1983 | TCP/IP trở thành chuẩn ARPANET (Flag day) |
| 1989 | WWW (Berners-Lee), HTTP/HTML |
| 1993 | Mosaic browser → Web bùng nổ |
| 1998 | Google founded |
| 2000s | Web 2.0, Social media, Streaming, Cloud |
| 2010s | Mobile Internet, IoT, SDN/NFV, HTTPS everywhere |
| 2020s | 5G, WiFi 6/7, QUIC/HTTP3, Zero Trust, AI/ML in networking |

---

## Tóm tắt chương 1

| Khái niệm chính | Mô tả |
|-----------------|-------|
| **Internet** | Network of networks, packet-switched |
| **Protocol** | Quy tắc giao tiếp (format, order, actions) |
| **Edge vs Core** | End systems + access net vs Router backbone |
| **Packet vs Circuit Switching** | Store-forward shared vs Reserved dedicated |
| **Performance** | Loss, Delay (4 components), Throughput |
| **Layering** | 5 lớp Internet, encapsulation, service models |
| **Security** | CIA triad + threats at each layer |

---

## Liên kết
- [[MỤC LỤC - Lý thuyết Mạng máy tính]]
- [[Chương 2 - Lớp Ứng dụng]]