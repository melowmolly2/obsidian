# Chương 4: Lớp Mạng (Network Layer)

> Nguồn: *Computer Networking: A Top-Down Approach, 9th ed.* - Chapter 4

---

## 4.1 Tổng quan: Data Plane vs Control Plane

| Plane | Chức năng | Time scale | Ví dụ |
|-------|-----------|------------|-------|
| **Data Plane (Forwarding)** | Chuyển gói tin từ input port → output port | Per-packet (ns-μs) | Longest prefix match, switching fabric |
| **Control Plane (Routing)** | Tính toán bảng định tuyến, trao đổi thông tin topology | Per-event (ms-s) | OSPF, BGP, RIP, SDN Controller |

### Router Architecture
```
Input Ports → Switching Fabric → Output Ports
     ↓              ↓                ↓
  Lookup        Crossbar/       Queueing/
  Forwarding    Shared Mem/     Scheduling
  Table                        (AQM)
```

---

## 4.2 Chuyển tiếp (Forwarding) & Định tuyến (Routing)

### Forwarding Table
- Entry: `(Prefix/Length, Next Hop, Output Interface, Metric)`
- **Longest Prefix Match (LPM)**: Khớp tiền tố dài nhất
- **TCAM** (Ternary Content-Addressable Memory): Hardware LPM ở line rate

### Switching Fabric
| Loại | Đặc điểm | HOL Blocking |
|------|----------|--------------|
| **Memory** | CPU copy packet | Không (nếu đủ nhanh) |
| **Bus** | Shared bus, contention | Có |
| **Crossbar** | Non-blocking (N×N), scheduler | Có tại input queue (VOQ giải quyết) |

### Virtual Output Queuing (VOQ)
- Hàng đợi riêng cho **mỗi output port** tại **input port** → loại bỏ HOL blocking
- Scheduler (iSLIP, maximal matching) cấp phát crossbar

---

## 4.3 Giao thức IP (Internet Protocol)

### 4.3.1 IPv4 - RFC 791

#### IPv4 Header (20 bytes cơ bản)
```
 0                   1                   2                   3
 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|Version|  IHL  |DSCP/ECN|          Total Length                |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|         Identification        |Flags|      Fragment Offset   |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|  TTL  | Protocol | Header Checksum |        Source IP        |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                    Destination IP                             |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                    Options (Variable)                         |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```
| Field | Kích thước | Mô tả |
|-------|------------|-------|
| **Version** | 4 bits | 4 |
| **IHL** | 4 bits | Header length (32-bit words), min=5 (20B) |
| **DSCP** | 6 bits | DiffServ Code Point (QoS) |
| **ECN** | 2 bits | Explicit Congestion Notification |
| **Total Length** | 16 bits | Header + Data (max 65,535 bytes) |
| **Identification** | 16 bits | ID cho fragment reassembly |
| **Flags** | 3 bits | DF (Don't Fragment), MF (More Fragments) |
| **Fragment Offset** | 13 bits | Offset 8-byte blocks |
| **TTL** | 8 bits | Hop limit, giảm 1 mỗi router |
| **Protocol** | 8 bits | Upper layer: TCP=6, UDP=17, ICMP=1... |
| **Header Checksum** | 16 bits | Chỉ checksum header (IPv6 bỏ) |

#### Phân mảnh (Fragmentation)
- **MTU** khác nhau giữa các link → router phân mảnh nếu `DF=0`
- **Reassembly**: Chỉ tại **destination host**
- **IPv6**: **Không phân mảnh tại router** (chỉ source fragmentation via Path MTU Discovery)

#### Địa chỉ IPv4 & CIDR
- **32-bit**, dotted-decimal: `192.168.1.1`
- **CIDR** (Classless Inter-Domain Routing): `a.b.c.d/x` (prefix length)
- **Private Address** (RFC 1918):
  | Range | Prefix | Hosts |
  |-------|--------|-------|
  | 10.0.0.0 - 10.255.255.255 | 10.0.0.0/8 | ~16.7M |
  | 172.16.0.0 - 172.31.255.255 | 172.16.0.0/12 | ~1M |
  | 192.168.0.0 - 192.168.255.255 | 192.168.0.0/16 | ~65K |
- **Loopback**: 127.0.0.0/8 (127.0.0.1)
- **Link-local**: 169.254.0.0/16 (APIPA)
- **Multicast**: 224.0.0.0/4
- **Broadcast**: 255.255.255.255 (limited), subnet-directed

#### NAT (Network Address Translation) - RFC 3022
| Loại | Đặc điểm |
|------|----------|
| **Static NAT** | 1 private ↔ 1 public (1-1) |
| **Dynamic NAT** | Pool public IP, assign khi cần |
| **NAPT / PAT** (Port Address Translation) | Nhiều private → 1 public, dùng **port** phân biệt (phổ biến nhất) |

**NAT Traversal**: STUN, TURN, ICE (cho P2P, VoIP)

---

### 4.3.2 IPv6 - RFC 8200

#### Đặc điểm chính
- **128-bit address** (3.4×10³⁸ addresses)
- **Header cố định 40 bytes** (no options in main header)
- **Không checksum header** (layer 2/4 đã có)
- **Không phân mảnh tại router** (ICMPv6 Packet Too Big → PMTUD)
- **Flow Label** (20 bits): Per-flow QoS/ECMP hashing
- **Extension Headers**: Hop-by-Hop, Routing, Fragment, ESP, AH, Destination Options

#### IPv6 Header (40 bytes)
```
 0                   1                   2                   3
 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|Version| Traffic Class |           Flow Label (20 bits)       |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|         Payload Length        |  Next Header  |   Hop Limit  |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                                                               |
|                    Source Address (128 bits)                  |
|                                                               |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                                                               |
|                   Destination Address (128 bits)              |
|                                                               |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```
| Field | Kích thước | Mô tả |
|-------|------------|-------|
| **Version** | 4 bits | 6 |
| **Traffic Class** | 8 bits | DSCP (6) + ECN (2) |
| **Flow Label** | 20 bits | Flow identification |
| **Payload Length** | 16 bits | Extension headers + payload |
| **Next Header** | 8 bits | Extension header type hoặc upper layer protocol |
| **Hop Limit** | 8 bits | TTL equivalent |

#### Địa chỉ IPv6
- **Notation**: 8 groups hex 16-bit, `::` nén zeros: `2001:0db8:85a3::8a2e:0370:7334`
- **Prefix**: `/64` chuẩn cho subnet (SLAAC)
- **Loại địa chỉ**:
  | Loại | Prefix | Mô tả |
  |------|--------|-------|
  | **Global Unicast** | 2000::/3 | Routable Internet |
  | **Unique Local (ULA)** | fc00::/7 | Private (thay site-local) |
  | **Link-Local** | fe80::/10 | Chỉ trên link, auto-config |
  | **Loopback** | ::1/128 | Localhost |
  | **Unspecified** | ::/128 | Chưa có địa chỉ |
  | **Multicast** | ff00::/8 | Group communication |
  | **Embedded IPv4** | ::ffff:0:0/96 | IPv4-mapped IPv6 |

#### ICMPv6 - RFC 4443 (Thay thế ICMPv4 + ARP + IGMP)
| Message Type | Chức năng |
|--------------|-----------|
| **Router Solicitation (RS)** | Host yêu cầu RA |
| **Router Advertisement (RA)** | Router broadcast prefix, flags, lifetime |
| **Neighbor Solicitation (NS)** | ARP replacement: hỏi MAC từ IP |
| **Neighbor Advertisement (NA)** | Trả lời NS, DAD (Duplicate Address Detection) |
| **Redirect** | Better next hop |
| **Packet Too Big** | PMTUD (ICMPv6 Type 2) |
| **Time Exceeded / Parameter Problem** | Error reporting |

#### Transition IPv4 → IPv6
| Kỹ thuật | Mô tả |
|----------|-------|
| **Dual Stack** | Host/router chạy cả IPv4 và IPv6 |
| **Tunneling** | 6to4, 6in4, ISATAP, GRE, DS-Lite |
| **Translation** | NAT64/DNS64 (IPv6-only client → IPv4 server), 464XLAT |

---

## 4.4 Thuật toán định tuyến (Routing Algorithms)

### Phân loại
| Loại | Thuật toán | Ví dụ giao thức |
|------|------------|-----------------|
| **Link-State (LS)** | Dijkstra (SPF) | OSPF, IS-IS |
| **Distance-Vector (DV)** | Bellman-Ford | RIP, EIGRP (hybrid) |
| **Path-Vector** | DV + AS-PATH | BGP |

### Link-State (OSPF/IS-IS)
- Mỗi router có **toàn bộ topology** (LSDB)
- **Dijkstra** tính shortest-path tree từ router đó
- **Flooding** LSA/LSP → all routers
- **Hierarchy**: Area 0 (backbone) → Area non-backbone → Virtual link

### Distance-Vector (RIP)
- Chỉ biết **distance** (hop count) đến destination qua **neighbor**
- **Count-to-infinity** problem → Split horizon, Poison reverse
- Max 15 hops (16 = infinity)

### BGP (Border Gateway Protocol) - RFC 4271
- **Inter-AS routing** (Path Vector)
- **Policy-based**: Không chỉ shortest path, mà business relationship
- **Attributes**: AS-PATH, NEXT-HOP, LOCAL_PREF, MED, ORIGIN, COMMUNITY
- **Decision Process**: LOCAL_PREF → AS-PATH length → ORIGIN → MED → eBGP > iBGP → IGP cost → Router ID
- **iBGP**: Full mesh hoặc Route Reflector / Confederation
- **eBGP**: Directly connected (TTL=1 default)

---

## 4.5 Router Internals chi tiết

### Input Port Processing
1. **Line Termination**: Physical/Layer 2 termination
2. **Decapsulation**: Strip L2 header
3. **Lookup/Forwarding**: LPM → Output port, Next hop
4. **Queueing**: Input queue (VOQ) nếu fabric busy

### Output Port Processing
1. **Queueing**: Output queue (congestion point chính)
2. **Scheduling**: FIFO, Priority, WFQ, DRR, PIFO
3. **AQM**: RED, CoDel, PIE, FQ-CoDel
4. **Encapsulation**: Add L2 header cho next hop

### Scheduling Algorithms
| Algorithm | Đặc điểm |
|-----------|----------|
| **FIFO / Tail Drop** | Đơn giản, không phân biệt flow |
| **Priority Queueing (PQ)** | Strict priority, starvation thấp |
| **Round Robin (RR)** | Fair giữa các class/queue |
| **Weighted Fair Queueing (WFQ)** | Weight-based fair share, per-flow state |
| **Deficit Round Robin (DRR)** | O(1), byte-based fair, no per-flow state |
| **FQ-CoDel / CAKE** | Flow isolation + AQM (CoDel), best practice hiện nay |

### Active Queue Management (AQM)
| Algorithm | Nguyên lý |
|-----------|-----------|
| **RED (Random Early Detection)** | Drop/mark xác suất tăng khi avg queue > min_th |
| **CoDel (Controlled Delay)** | Kiểm soát **sojourn time** (delay trong queue), target ~5ms |
| **PIE (Proportional Integral Enhanced)** | PID controller trên drop probability |
| **FQ-CoDel** | Per-flow queue + CoDel → fairness + low latency |

---

## 4.6 SDN (Software-Defined Networking) & OpenFlow

### Kiến trúc SDN
```
Application Layer (Northbound API)
         ↓
Control Layer (SDN Controller: ONOS, ODL, Ryu, OpenDaylight)
         ↓ OpenFlow / NETCONF / gNMI
Infrastructure Layer (Switches, Routers - OpenFlow enabled)
```

### OpenFlow - Match + Action
- **Flow Table**: Entries `(Match fields, Priority, Counters, Instructions, Timeouts)`
- **Match fields**: L2 (MAC, VLAN), L3 (IP src/dst, protocol, DSCP), L4 (port src/dst), Tunnel ID...
- **Actions**: Forward, Drop, Modify (VLAN push/pop, TTL decrement), Group, Meter, Send to Controller
- **Pipeline**: Table 0 → Table 1 → ... (Table Miss → Controller hoặc Default Drop)

### Group Table
- **All** (multicast/flood), **Select** (load balance), **Indirect** (single next hop), **Fast Failover** (backup ports)

### Meter Table
- Rate limiting (bandwidth policing), packet/byte counters, color marking (green/yellow/red)

---

## 4.7 Middlebox & NFV (Network Function Virtualization)

### Middlebox (L4-L7 devices)
| Thiết bị | Chức năng |
|----------|-----------|
| **Firewall** | L3/L4 ACL, Stateful inspection, L7 DPI |
| **NAT** | Address/port translation |
| **Load Balancer** | L4 (IP/port), L7 (HTTP header, cookie) |
| **IDS/IPS** | Signature/Anomaly detection |
| **WAN Optimizer** | Deduplication, compression, caching |
| **Proxy** | Forward/Reverse, SSL termination |

### NFV (ETSI NFV MANO)
- **VNF (Virtual Network Function)**: Network function chạy trên VM/Container
- **NFVI**: Compute/Storage/Network infrastructure (OpenStack, Kubernetes)
- **MANO**: Orchestrator (NFVO), VNF Manager (VNFM), VIM
- **Benefits**: Agility, cost (COTS hardware), scale, automation

---

## 4.8 So sánh IPv4 vs IPv6 tóm tắt

| Đặc điểm | IPv4 | IPv6 |
|----------|------|------|
| **Address size** | 32-bit | 128-bit |
| **Header size** | 20-60 bytes (variable) | 40 bytes (fixed) + extension headers |
| **Checksum** | Header checksum | Không (L2/L4 đảm bảo) |
| **Fragmentation** | Router + Host | Chỉ Host (PMTUD) |
| **Options** | Trong header | Extension headers |
| **ARP** | ARP (broadcast) | NDP (NS/NA, multicast) |
| **DHCP** | DHCPv4 | DHCPv6 + SLAAC (stateless) |
| **Broadcast** | Có (255.255.255.255) | Không (dùng multicast ff02::1) |
| **QoS** | DSCP/ECN (ToS byte) | Traffic Class + Flow Label |
| **Security** | IPsec (optional) | IPsec (mandatory support) |

---

## Tóm tắt chương 4

| Chủ đề | Key Points |
|--------|------------|
| **Data vs Control Plane** | Forwarding (per-packet) vs Routing (per-event) |
| **IPv4** | Header, Fragmentation, CIDR, Private IP, NAT/NAPT |
| **IPv6** | 128-bit, fixed header, no fragmentation at router, NDP/ICMPv6, SLAAC |
| **Routing Algorithms** | Link-State (Dijkstra/OSPF/IS-IS), Distance-Vector (Bellman-Ford/RIP), Path-Vector (BGP) |
| **Router Internals** | Input/Output processing, Switching fabric (Crossbar), VOQ, Scheduling (DRR, FQ-CoDel), AQM (CoDel, PIE) |
| **SDN/OpenFlow** | Control-data separation, Match+Action, Flow/Group/Meter tables |
| **Middlebox/NFV** | L4-L7 functions, VNF on COTS, MANO orchestration |

---

## Liên kết
- [[MỤC LỤC - Lý thuyết Mạng máy tính]]
- [[Chương 3 - Lớp Vận chuyển]]
- [[Chương 5 - Lớp Liên kết & LAN]]