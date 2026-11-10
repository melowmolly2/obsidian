# Chương 5: Lớp Liên kết & LAN (Link Layer & LANs)

> Nguồn: *Computer Networking: A Top-Down Approach, 9th ed.* - Chapter 5 (slide Chapter 6 trong PPTX)

---

## 5.1 Dịch vụ lớp liên kết (Link Layer Services)

| Dịch vụ | Mô tả |
|---------|-------|
| **Framing** | Đóng gói datagram L3 thành frame: Header + Payload + Trailer |
| **Link Access (MAC)** | Điều phối truy cập shared medium (CSMA/CD, CSMA/CA, TDMA...) |
| **Addressing** | MAC address (48-bit) cho hop-to-hop delivery |
| **Error Detection** | Parity, Checksum, CRC (Cyclic Redundancy Check) |
| **Error Correction** | FEC (Forward Error Correction), Hamming code (ít dùng trên wired) |
| **Flow Control** | Hop-by-hop (PAUSE frame, PFC) |

### Frame Structure (Generic)
```
[Preamble/SFD] [Dst MAC] [Src MAC] [Type/Length] [Payload] [CRC/FCS] [Inter-frame Gap]
```

---

## 5.2 Error Detection & Correction

### Parity Bit
- **Even parity**: Tổng bit 1 là chẵn
- **Odd parity**: Tổng bit 1 là lẻ
- Phát hiện **1-bit error**, không sửa được

### Checksum (Internet Checksum)
- 1's complement sum của 16-bit words
- Dùng ở IP, TCP, UDP header

### CRC (Cyclic Redundancy Check) - Phổ biến nhất tại L2
- **Polynomial division** trong Galois Field GF(2)
- **Generator polynomial** G(x) (ví dụ: CRC-32 Ethernet: `0x04C11DB7`)
- **Frame check sequence (FCS)** = Remainder của `M(x) × x^k / G(x)`
- **Phát hiện**: All 1-bit, all 2-bit, all odd-bit, all burst ≤ k bits, 99.99% burst > k bits
- **Hardware-friendly**: Shift register (LFSR)

### Forward Error Correction (FEC)
- **Hamming Code**: (7,4) → 4 data bits + 3 parity bits → sửa 1-bit, phát hiện 2-bit
- **Reed-Solomon**: Block code, dùng trong storage, QR, DVB, WiFi (LDPC), 5G (LDPC/Polar)
- **LDPC (Low-Density Parity-Check)**: Capacity-approaching, WiFi 6/7, 5G NR, 100G Ethernet
- **Polar Codes**: 5G control channel

---

## 5.3 Multiple Access Protocols (Giao thức truy cập đa phương tiện)

### Phân loại
| Loại | Giao thức | Đặc điểm |
|------|-----------|----------|
| **Channel Partitioning** | TDMA, FDMA, CDMA | Chia kênh cố định, không tranh chấp |
| **Random Access** | ALOHA, Slotted ALOHA, CSMA, CSMA/CD, CSMA/CA | Tranh chấp, backoff, throughput < 100% |
| **Taking Turns** | Polling, Token Passing | Không tranhchap, độ trễ xác định, phức tạp |

### ALOHA & Slotted ALOHA
| Protocol | Throughput max | Nguyên lý |
|----------|----------------|-----------|
| **Pure ALOHA** | 18.4% | Gửi bất cứ lúc, collision → retransmit sau random time |
| **Slotted ALOHA** | 36.8% | Time slot đồng bộ, gửi đầu slot |

### CSMA (Carrier Sense Multiple Access)
- **1-persistent**: Sense busy → wait, idle → transmit immediately (collision cao)
- **Non-persistent**: Sense busy → wait random, idle → transmit
- **p-persistent**: Slotted, idle → transmit with prob p, defer (1-p) to next slot

### CSMA/CD (Collision Detection) - Ethernet Hữu tuyến (802.3)
```
1. Carrier Sense: Nghe medium
2. Transmit nếu idle
3. Collision Detection: Phát hiện collision khi transmit (voltage level)
4. Jam Signal: Gửi 32-48 bit jam để tất cả station biết collision
5. Binary Exponential Backoff: Wait k × 512 bit times, k ∈ [0, 2^min(n,10)-1]
   n = số collision liên tiếp (max 16 attempts)
```
- **Slot time** = 512 bit times = 51.2 μs (10 Mbps) → **Minimum frame size 64 bytes** (để detect collision trước khi frame kết thúc)
- **Hiệu suất**: ~50-60% tại load cao

### CSMA/CA (Collision Avoidance) - WiFi (802.11)
- **Không detect collision được** (half-duplex radio, hidden terminal)
- **DCF (Distributed Coordination Function)**:
  ```
  DIFS → Backoff (random slots) → Transmit → SIFS → ACK
  ```
- **RTS/CTS** (tùy chọn): Giải quyết Hidden Terminal
  ```
  RTS → CTS → DATA → ACK
  ```
- **NAV (Network Allocation Vector)**: Virtual carrier sense (duration field)

---

## 5.4 LAN (Local Area Network) & Ethernet

### Ethernet Evolution
| Standard | Speed | Medium | Topology | Note |
|----------|-------|--------|----------|------|
| 802.3 (10BASE5) | 10 Mbps | Thick coax | Bus | Vampire tap |
| 802.3u (100BASE-TX) | 100 Mbps | UTP Cat5 | Star (Switch) | Fast Ethernet |
| 802.3ab (1000BASE-T) | 1 Gbps | UTP Cat5e | Star | Gigabit, 4 pairs |
| 802.3ae (10GBASE) | 10 Gbps | Fiber/UTP Cat6a | Star | 10G |
| 802.3bs (400GBASE) | 400 Gbps | Fiber | Star | Data center |

### Ethernet Frame (802.3)
```
[Preamble 7B] [SFD 1B] [Dst MAC 6B] [Src MAC 6B] [Type/Length 2B] [Payload 46-1500B] [FCS 4B]
```
- **Preamble (7B)**: `10101010` × 7 - đồng bộ clock
- **SFD (1B)**: `10101011` - Start Frame Delimiter
- **Type/Length**: ≥ 1536 (0x0600) = EtherType (IPv4=0x0800, IPv6=0x86DD, ARP=0x0806); < 1536 = Length (802.2 LLC)
- **Payload**: Min 46B (padding nếu ít hơn) → đảm bảo collision detection
- **FCS**: CRC-32

### MAC Address (EUI-48)
- **48-bit**: `OUI (24-bit) + Vendor Assigned (24-bit)`
- **Notation**: `aa:bb:cc:dd:ee:ff` hoặc `aa-bb-cc-dd-ee-ff`
- **Bit 0 (LSB first byte)**: I/G (Individual/Group) - 0=Unicast, 1=Multicast/Broadcast
- **Bit 1**: U/L (Universal/Local) - 0=OUI (global), 1=Locally administered
- **Broadcast**: `ff:ff:ff:ff:ff:ff`
- **IPv6 Multicast MAC**: `33:33:xx:xx:xx:xx` (low 32-bit của IPv6 multicast)

### Switch (Layer 2 Switch / Bridge)
| Chức năng | Mô tả |
|-----------|-------|
| **Learning** | Học `Src MAC → Port` từ frame đến (self-learning, aging timer ~300s) |
| **Forwarding** | Tra bảng MAC: Unicast → port cụ thể; Unknown/Multicast/Broadcast → flood tất cả port trừ port đến |
| **Filtering** | Không forward frame nếu Src và Dst cùng port |
| **STP/RSTP** | Tránh loop (802.1D/802.1w) |

#### Spanning Tree Protocol (STP - 802.1D) & RSTP (802.1w)
- **Root Bridge**: Bridge ID nhỏ nhất (Priority + MAC)
- **Root Port**: Port có cost thấp nhất đến Root
- **Designated Port**: Port có cost thấp nhất trên mỗi segment
- **Port States**: Blocking → Listening → Learning → Forwarding (STP); Discarding → Learning → Forwarding (RSTP)
- **RSTP**: Convergence ~1 giây (vs 30-50s STP), Proposal/Agreement handshake

### VLAN (Virtual LAN) - IEEE 802.1Q
- **Phân tách Broadcast Domain** logic trên cùng infrastructure vật lý
- **Tag 4-byte** chèn sau Src MAC:
  ```
  [TPID=0x8100] [PCP 3b] [DEI 1b] [VID 12b]  → 4096 VLAN (0, 4095 reserved)
  ```
- **Access Port**: Untagged, gán 1 VLAN (end device)
- **Trunk Port**: Tagged, truyền nhiều VLAN (switch-switch, switch-router)
- **Native VLAN**: Untagged trên trunk (mặc định VLAN 1)
- **Inter-VLAN Routing**: Router-on-a-stick (subinterface) hoặc Layer 3 Switch (SVI)

### Link Aggregation (LACP - 802.3ad/802.1AX)
- **Gộp nhiều link vật lý** thành 1 logical link
- **LACP**: Negotiate aggregation, detect link failure
- **Load Balancing**: Hash (Src/Dst MAC, IP, Port) → phân phối flow
- **Lợi ích**: Tăng bandwidth, redundancy, load balancing

---

## 5.5 WiFi (IEEE 802.11) - Overview (Chi tiết ở Chương 6)

### Kiến trúc
- **BSS (Basic Service Set)**: 1 AP + Stations
- **ESS (Extended Service Set)**: Nhiều BSS cùng SSID, cùng Distribution System
- **IBSS (Ad-hoc)**: Không AP, peer-to-peer

### MAC (DCF - CSMA/CA)
- **DIFS** (DCF Interframe Space) = 34 μs (802.11g), **SIFS** = 16 μs
- **Backoff**: Random [0, CW-1] slots, CW = Contention Window (min CWmin, max CWmax)
- **ACK**: Bắt buộc cho unicast data frame
- **Retry Limit**: Short retry (7), Long retry (4)

---

## 5.6 MPLS (Multi-Protocol Label Switching)

### Khái niệm
- **Label** (20-bit) gán tại **Ingress LER** (Label Edge Router)
- **LSR (Label Switch Router)**: Swap label (Label Swapping)
- **Egress LER**: Pop label → forward IP packet
- **LSP (Label Switched Path)**: Đường đi xác định trước

### MPLS Header (Shim Header - 4 bytes)
```
 0                   1                   2                   3
 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                Label (20 bits)          |Exp|S|   TTL (8)    |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```
- **Label**: 20 bits (0-15 reserved: IPv4 Explicit Null=0, Router Alert=1, IPv6 Explicit Null=2, Implicit Null=3)
- **Exp (TC)**: 3 bits Traffic Class (QoS)
- **S (Bottom of Stack)**: 1 bit (MPLS label stacking)
- **TTL**: 8 bits (TTL propagation từ IP)

### Ứng dụng MPLS
| Ứng dụng | Mô tả |
|----------|-------|
| **L3VPN (RFC 4364)** | VRF, RD, RT, MP-BGP cho VPN routing |
| **L2VPN (VPWS/VPLS)** | Pseudowire (LDP/T-LDP), VPLS (BGP/LDP signaling) |
| **Traffic Engineering (MPLS-TE)** | RSVP-TE / SR-TE, explicit path, bandwidth reservation |
| **Fast Reroute (FRR)** | Link/Node protection < 50ms (detour/bypass LSP) |
| **Segment Routing (SR-MPLS)** | Source routing, SID list, không cần LDP/RSVP |

---

## 5.7 Data Center Networks (Mạng trung tâm dữ liệu)

### Topology
| Topology | Đặc điểm |
|----------|----------|
| **Fat-Tree / Clos** | Multi-stage, non-blocking, equal-cost multipath (ECMP) |
| **Leaf-Spine** | 2-tier: Leaf (ToR) ↔ Spine (Core), tất cả Leaf kết nối tất cả Spine |
| **DCell / BCube** | Server-centric, server có multiple NICs |

### Công nghệ DCN
| Công nghệ | Mục đích |
|-----------|----------|
| **VXLAN (RFC 7348)** | L2 over L3 (UDP 4789), VNI 24-bit (16M segments), VTEP encapsulation |
| **NVGRE / Geneve** | Tương tự VXLAN, khác header |
| **EVPN (RFC 7432)** | BGP control plane cho VXLAN, MAC learning qua BGP |
| **RoCE (RDMA over Converged Ethernet)** | Zero-copy, kernel-bypass, PFC (Priority Flow Control) + ECN |
| **PFC (802.1Qbb)** | Per-priority pause (no-drop cho RoCE/iSCSI) |
| **ECN (3168/8311)** | Congestion marking thay pause |
| **DCB (Data Center Bridging)** | PFC + ETS (Enhanced Transmission Selection) + DCBX |
| **CONGA / DRB / HULA** | Adaptive load balancing trên ECMP |

---

## Tóm tắt chương 5

| Chủ đề | Key Points |
|--------|------------|
| **Framing** | Header + Payload + Trailer (CRC) |
| **Error Detection** | CRC (polynomial), Checksum, Parity |
| **Error Correction** | FEC: Hamming, Reed-Solomon, LDPC, Polar |
| **Multiple Access** | Partition (TDMA/FDMA/CDMA), Random (CSMA/CD, CSMA/CA), Turns (Token) |
| **Ethernet** | Frame, MAC address, Switch (learning, flooding, STP/RSTP) |
| **VLAN** | 802.1Q tag (VID 12-bit), Access/Trunk, Native VLAN, Inter-VLAN routing |
| **Link Aggregation** | LACP, hash-based load balancing |
| **MPLS** | Label (20-bit), LSP, LER/LSR, VPN/TE/FRR/SR applications |
| **Data Center** | Leaf-Spine, VXLAN/EVPN, RoCE/PFC/ECN, Adaptive LB |

---

## Liên kết
- [[MỤC LỤC - Lý thuyết Mạng máy tính]]
- [[Chương 4 - Lớp Mạng]]
- [[Chương 6 - Mạng không dây & Di động]]