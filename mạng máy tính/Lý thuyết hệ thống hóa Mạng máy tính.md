# Lý thuyết hệ thống hóa môn Mạng máy tính
*Dựa trên: Computer Networking: A Top-Down Approach, 9th edition - Kurose & Ross*

---

## MỤC LỤC

1. [Chương 1: Giới thiệu](#chương-1-giới-thiệu)
2. [Chương 2: Lớp Ứng dụng](#chương-2-lớp-ứng-dụng)
3. [Chương 3: Lớp Vận chuyển](#chương-3-lớp-vận-chuyển)
4. [Chương 4: Lớp Mạng](#chương-4-lớp-mạng)
5. [Chương 5: Lớp Liên kết & LAN](#chương-5-lớp-liên-kết--lan)
6. [Chương 6: Mạng không dây & Di động](#chương-6-mạng-không-dây--di-động)
7. [Chương 7: An ninh mạng](#chương-7-an-ninh-mạng)

---

## CHƯƠNG 1: GIỚI THIỆU

### 1.1 Internet là gì?
- **Nuts-and-bolts view**: Internet = tập hợp các thiết bị cuối (hosts/end systems) kết nối bởi các liên kết truyền thông (communication links) và bộ định tuyến (packet switches/routers).
- **Thiết bị cuối**: máy tính, điện thoại, IoT (tivi, tủ lạnh, xe hơi...).
- **Liên kết vật lý**: cáp đồng, cáp quang, vô tuyến, vệ tinh.
- **Bộ định tuyến**: router, switch chuyển mạch gói.

### 1.2 Giao thức (Protocol)
> **Định nghĩa**: Giao thức quy định *định dạng*, *thứ tự* các thông điệp trao đổi giữa các thực thể giao tiếp, và *hành động* khi gửi/nhận thông điệp.

**Ví dụ**: HTTP, TCP, IP, WiFi, 4G/5G, DNS, TLS.

### 1.3 Cạnh mạng (Network Edge)
- **Hosts (End systems)**: Chạy ứng dụng mạng (client/server).
- **Access network (Mạng truy cập)**: Kết nối host tới router đầu tiên (edge router).
  - DSL, Cable, FTTH (Fiber to the Home), 4G/5G, WiFi, Ethernet.
- **Physical media (Phương tiện vật lý)**: Cáp đôi xoắn, cáp quang, vô tuyến.

### 1.4 Lõi mạng (Network Core)
- **Chuyển mạch gói (Packet Switching)**:
  - Gói tin được chia nhỏ, lưu trữ chuyển tiếp (store-and-forward).
  - Thời gian truyền gói: $L/R$ (độ dài gói / băng thông liên kết).
  - Hàng đợi (queue) tại router → độ trễ, mất gói khi đầy.
- **Chuyển mạch mạch (Circuit Switching)**: Cấp phát tài nguyên chuyên dụng (TDMA/FDMA).
- **Cấu trúc Internet**: Network of networks (ISP tier 1, tier 2, tier 3, IXP, CDN).

### 1.5 Hiệu suất mạng
| Chỉ số | Mô tả |
|--------|-------|
| **Mất gói (Loss)** | Gói bị drop khi hàng đợi đầy |
| **Độ trễ (Delay)** | Tổng: nodal processing + queueing + transmission + propagation |
| **Thông lượng (Throughput)** | Tốc độ truyền dữ liệu thực tế (bottleneck link) |

### 1.6 Mô hình lớp (Protocol Layers)
| Mô hình | 5 lớp (Internet) | 7 lớp (OSI) |
|---------|------------------|-------------|
| Lớp 5 | Ứng dụng (Application) | Ứng dụng |
| Lớp 4 | Vận chuyển (Transport) | Vận chuyển |
| Lớp 3 | Mạng (Network) | Mạng |
| Lớp 2 | Liên kết (Link) | Liên kết |
| Lớp 1 | Vật lý (Physical) | Vật lý |

**Encapsulation**: Mỗi lớp thêm header (và đôi khi trailer) → gói tin lớp dưới.

### 1.7 An ninh & Lịch sử
- **Các mối đe dọa**: nghe lén, giả mạo, DoS, malware.
- **Lịch sử**: ARPANET (1969) → TCP/IP (1983) → WWW (1990) → Web 2.0, Streaming, Cloud, IoT, 5G...

---

## CHƯƠNG 2: LỚP ỨNG DỤNG (APPLICATION LAYER)

### 2.1 Kiến trúc ứng dụng
| Kiến trúc | Đặc điểm |
|-----------|----------|
| **Client-Server** | Server luôn bật, IP cố định, farm server cho khả năng mở rộng |
| **P2P (Peer-to-Peer)** | Không server chuyên dụng, peer vừa client vừa server, tự mở rộng |

### 2.2 Giao dịch tiến trình (Process Communication)
- **Socket**: API giữa ứng dụng và tầng vận chuyển.
- **Địa chỉ tiến trình**: IP address + Port number.
  - Well-known ports: HTTP(80), HTTPS(443), FTP(21), DNS(53), SMTP(25), SSH(22).

### 2.3 Dịch vụ vận chuyển mà ứng dụng cần
| Yêu cầu | Giao thức phù hợp |
|---------|-------------------|
| Tin cậy, thứ tự, kiểm soát luồng | **TCP** |
| Không tin cậy, độ trễ thấp, multicast | **UDP** |
| An ninh (mã hóa, xác thực) | **TLS/SSL** (trên TCP) |

### 2.4 Web & HTTP
- **HTTP**: Giao thức yêu cầu-đáp ứng (request-response), stateless.
- **Phiên bản**: HTTP/1.0 (non-persistent), HTTP/1.1 (persistent, pipelining), HTTP/2 (multiplexing, header compression, server push), HTTP/3 (QUIC trên UDP).
- **Message format**:
  - Request: Method, URL, Version, Headers, Body
  - Response: Version, Status code, Headers, Body
- **Mã trạng thái**: 200 OK, 301/302 Redirect, 400 Bad Request, 404 Not Found, 500 Server Error.

**Cookie**: Giữ trạng thái (stateful) trên HTTP stateless → Set-Cookie header.

**Web Cache (Proxy)**: Giảm độ trễ, giảm băng thông truy cập origin server.
- **Conditional GET**: `If-Modified-Since` → 304 Not Modified.

### 2.5 Email (Electronic Mail)
- **SMTP (port 25)**: Gửi mail (push), TCP tin cậy, 7-bit ASCII.
- **POP3 (port 110)**: Kéo mail về, xóa trên server (thường).
- **IMAP (port 143)**: Đồng bộ thư mục, giữ mail trên server.
- **MIME**: Mở rộng cho non-ASCII (attachment, UTF-8).

### 2.6 DNS (Domain Name System)
- **Chức năng**: Phân giải tên miền → IP address.
- **Kiến trúc**: Phân cấp, phân tán.
  - Root servers → TLD (.com, .vn) → Authoritative servers.
- **Truy vấn**: Recursive (client yêu cầu server giải quyết) vs Iterative (server trả referral).
- **Cache**: TTL (Time To Live) giảm tải root/TLD.
- **Bản ghi (Resource Records)**: A, AAAA, CNAME, MX, NS, TXT.
- **Bảo mật**: DNSSEC (ký số), DNS over HTTPS (DoH), DNS over TLS (DoT).

### 2.7 P2P File Distribution (BitTorrent)
- **Chia file thành pieces** → peers trao đổi pieces.
- **Tracker**: Điều phối peer list.
- **Tit-for-tat**: Ưu tiên peer upload cho mình → công bằng.
- **DHT**: Tracker-less (phi tập trung).

### 2.8 Video Streaming & CDN
- **DASH (Dynamic Adaptive Streaming over HTTP)**: Manifest (MPD) + nhiều bitrate chunks.
- **CDN**: Cache nội dung tại edge servers gần user → giảm độ trễ, giảm tải origin.

### 2.9 Socket Programming
- **TCP Socket**: `socket()`, `bind()`, `listen()`, `accept()`, `send()`, `recv()`, `close()`.
- **UDP Socket**: `socket()`, `bind()`, `sendto()`, `recvfrom()`, `close()`.

---

## CHƯƠNG 3: LỚP VẬN CHUYỂN (TRANSPORT LAYER)

### 3.1 Giới thiệu & Dịch vụ
- **Multiplexing/Demultiplexing**: Port number phân biệt tiến trình.
  - UDP: destination port.
  - TCP: (src IP, src port, dst IP, dst port) = 4-tuple.
- **Kiểm tra lỗi**: Checksum (IPv4: header+data; IPv6: pseudo-header+data).

### 3.2 UDP (User Datagram Protocol)
- **Đặc điểm**: Không kết nối, không tin cậy, không thứ tự, không kiểm soát luồng/輻輳.
- **Header**: Src port, Dst port, Length, Checksum (8 bytes).
- **Ứng dụng**: DNS, DHCP, streaming, gaming, QUIC.

### 3.3 TCP (Transmission Control Protocol)
- **Đặc điểm**: Kết nối (connection-oriented), tin cậy, thứ tự, full-duplex, byte-stream.
- **Kết nối 3-way handshake**: SYN → SYN-ACK → ACK.
- **Ngắt kết nối**: FIN → ACK → FIN → ACK (hoặc RST).

#### 3.3.1 Truyền dữ liệu tin cậy
- **Sequence number**: Số thứ tự byte đầu tiên trong segment.
- **ACK**: Cumulative ACK (số byte tiếp theo mong đợi).
- **Retransmission**:
  - Timeout (RTO): EstimatedRTT + 4×DevRTT.
  - Fast Retransmit: 3 Duplicate ACKs.
- **Sliding Window**: Flow control (rwnd) + Congestion control (cwnd).

#### 3.3.2 Kiểm soát luồng (Flow Control)
- **Receiver window (rwnd)**: Không gian buffer còn lại tại receiver.
- Sender không gửi quá `min(cwnd, rwnd)`.

#### 3.3.3 Kiểm soát tắc nghẽn (Congestion Control)
| Giai đoạn | Mô tả |
|-----------|-------|
| **Slow Start** | cwnd += 1 MSS mỗi ACK (tăng cấp số) |
| **Congestion Avoidance** | cwnd += 1 MSS mỗi RTT (tăng tuyến tính) |
| **Fast Recovery** | Khi 3 DupACKs: ssthresh = cwnd/2, cwnd = ssthresh + 3 MSS |
| **Timeout** | ssthresh = cwnd/2, cwnd = 1 MSS (Slow Start) |

**TCP Tahoe / Reno / NewReno / CUBIC / BBR**: Các biến thể cải tiến.

### 3.4 Kiểm soát tắc nghẽn dựa trên độ trễ (Delay-based) & ECN
- **ECN (Explicit Congestion Notification)**: Router đánh dấu gói (CE bit) thay vì drop → receiver báo sender qua ECE bit.

---

## CHƯƠNG 4: LỚP MẠNG (NETWORK LAYER)

### 4.1 Tổng quan
- **Data Plane (Forwarding)**: Chuyển gói tin từ input → output port (per-packet).
- **Control Plane (Routing)**: Tính toán bảng định tuyến (routing algorithms, protocols).

### 4.2 Chuyển tiếp (Forwarding) & Định tuyến (Routing)
- **Forwarding Table**: (Prefix, Next Hop, Output Interface).
- **Longest Prefix Match**: Khớp tiền tố dài nhất.
- **Switching Fabric**: Memory, Bus, Crossbar.

### 4.3 Giao thức IP (Internet Protocol)
#### IPv4
- **Header**: Version, IHL, DSCP/ECN, Total Length, Identification, Flags, Fragment Offset, TTL, Protocol, Header Checksum, Src/Dst IP, Options.
- **Phân mảnh (Fragmentation)**: MTU khác nhau → DF bit, MF bit, Fragment Offset.
- **Địa chỉ**: 32-bit, dotted-decimal (192.168.1.1).
- **CIDR**: Classless Inter-Domain Routing (a.b.c.d/x).
- **Private IP**: 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16.
- **NAT (Network Address Translation)**: Private ↔ Public, NAPT (Port-based).

#### IPv6
- **Địa chỉ**: 128-bit, hex (2001:0db8::/32).
- **Header cố định 40 bytes**: Version, Traffic Class, Flow Label, Payload Length, Next Header, Hop Limit, Src/Dst.
- **Không phân mảnh tại router**: Chỉ source fragmentation.
- **Không checksum header**.
- **ICMPv6**: NDP (Neighbor Discovery), Router Solicitation/Advertisement.

### 4.4 Thuật toán định tuyến
| Loại | Thuật toán | Ví dụ |
|------|------------|-------|
| **Link-State** | Dijkstra (SPF) | OSPF, IS-IS |
| **Distance-Vector** | Bellman-Ford | RIP, BGP (path vector) |

- **OSPF**: Intra-AS, hierarchy (Area 0 backbone), cost = reference bandwidth / interface bandwidth.
- **BGP**: Inter-AS, Path Vector, Policy-based (AS-PATH, LOCAL_PREF, MED).

### 4.5 Router Architecture
- **Input Port**: Line termination, link layer, lookup/forwarding, queueing.
- **Switching Fabric**: Crossbar, shared memory, bus.
- **Output Port**: Queueing, link layer, line termination.
- **HOL Blocking**: Head-of-line blocking tại input queue.
- **Scheduling**: FIFO, Priority, Round Robin, Weighted Fair Queueing (WFQ), Deficit Round Robin (DRR).
- **AQM (Active Queue Management)**: RED, CoDel, PIE.

### 4.6 SDN & OpenFlow
- **Control Plane tách biệt**: Controller tập trung lập trình forwarding table.
- **OpenFlow**: Match+Action (header fields → forward/drop/modify/controller).
- **Flow Table**: Priority, Counters, Instructions.

### 4.7 Middlebox & Network Function Virtualization (NFV)
- **Middlebox**: Firewall, NAT, Load Balancer, IDS, WAN Optimizer.
- **NFV**: Chạy network function trên VM/Container (VNF) thay vì phần cứng chuyên dụng.

---

## CHƯƠNG 5: LỚP LIÊN KẾT & LAN (LINK LAYER & LANS)

### 5.1 Dịch vụ lớp liên kết
- **Framing**: Đóng gói datagram thành frame (header + payload + trailer).
- **Truy cập phương tiện (Media Access Control - MAC)**: Ai được truyền trên shared medium?
- **Địa chỉ MAC**: 48-bit (OUI + vendor assigned), unicast/multicast/broadcast.
- **Phát hiện lỗi (Error Detection)**: Parity, Checksum, CRC (Cyclic Redundancy Check).
- **Sửa lỗi (Error Correction)**: FEC (Forward Error Correction), Hamming code.

### 5.2 Giao thức truy cập đa phương tiện (Multiple Access Protocols)
| Loại | Giao thức | Đặc điểm |
|------|-----------|----------|
| **Channel Partitioning** | TDMA, FDMA, CDMA | Chia kênh cố định |
| **Random Access** | ALOHA, Slotted ALOHA, CSMA, CSMA/CD, CSMA/CA | Tranh chấp, backoff |
| **Taking Turns** | Polling, Token Passing | Không tranh chấp, độ trễ xác định |

- **CSMA/CD (Ethernet hữu tuyến)**: Carrier Sense, Collision Detection → Binary Exponential Backoff.
- **CSMA/CA (WiFi)**: Carrier Sense, Collision Avoidance → RTS/CTS, ACK.

### 5.3 LAN (Local Area Network) & Ethernet
- **Ethernet (IEEE 802.3)**: Bus → Star (Switch).
- **Frame**: Preamble, Dst MAC, Src MAC, Type/Length, Payload (46-1500B), CRC.
- **Switch**: Học MAC (self-learning), Forwarding/Filtering, Spanning Tree Protocol (STP/RSTP) tránh loop.
- **VLAN (802.1Q)**: Virtual LAN, tag 4-byte trong frame → phân tách broadcast domain.
- **Link Aggregation (802.3ad/LACP)**: Gộp nhiều link vật lý thành logic link.

### 5.4 MPLS (Multi-Protocol Label Switching)
- **Label**: 20-bit, gán tại ingress router → swap tại transit → pop tại egress.
- **LSP (Label Switched Path)**: Đường đi xác định trước.
- **Ứng dụng**: VPN, Traffic Engineering, Fast Reroute.

### 5.5 Mạng trung tâm dữ liệu (Data Center Networks)
- **Topology**: Fat-tree, Clos, Leaf-Spine.
- **Đặc điểm**: High bisection bandwidth, low latency, ECMP routing.
- **Công nghệ**: VXLAN, NVGRE, Geneve (overlay), RoCE, PFC, ECN.

---

## CHƯƠNG 6: MẠNG KHÔNG DÂY & DI ĐỘNG (WIRELESS & MOBILE NETWORKS)

### 6.1 Đặc thách của truyền không dây
- **Signal attenuation**: Path loss, shadowing, multipath fading.
- **Interference**: Co-channel, adjacent channel.
- **SNR (Signal-to-Noise Ratio)**: Quyết định modulation/coding rate.
- **Hidden/Exposed Terminal Problem**: RTS/CTS giải quyết.

### 6.2 WiFi (IEEE 802.11)
#### Kiến trúc
- **BSS (Basic Service Set)**: AP + Stations.
- **ESS (Extended Service Set)**: Nhiều BSS cùng SSID, kết nối qua Distribution System.
- **Ad-hoc (IBSS)**: Không AP.

#### MAC Layer (DCF - Distributed Coordination Function)
- **CSMA/CA**: DIFS, Backoff, RTS/CTS (optional), DATA, SIFS, ACK.
- **Frame types**: Management (Beacon, Probe, Auth, Assoc), Control (RTS, CTS, ACK), Data.

#### Phân tầng vật lý (PHY) - Tiêu chuẩn
| Tiêu chuẩn | Band | Băng thông tối đa | Đặc điểm chính |
|------------|------|-------------------|----------------|
| 802.11b | 2.4 GHz | 11 Mbps | DSSS |
| 802.11a | 5 GHz | 54 Mbps | OFDM |
| 802.11g | 2.4 GHz | 54 Mbps | OFDM |
| 802.11n (WiFi 4) | 2.4/5 GHz | 600 Mbps | MIMO, 40 MHz |
| 802.11ac (WiFi 5) | 5 GHz | 6.9 Gbps | MU-MIMO, 160 MHz, 256-QAM |
| 802.11ax (WiFi 6/6E) | 2.4/5/6 GHz | 9.6 Gbps | OFDMA, MU-MIMO UL/DL, BSS Coloring, TWT |
| 802.11be (WiFi 7) | 2.4/5/6 GHz | 46 Gbps | 320 MHz, 4096-QAM, MLO, 16 spatial streams |

#### MIMO & Beamforming
- **Spatial Multiplexing**: Truyền song song nhiều stream (rank).
- **Spatial Diversity**: Truyền cùng data qua nhiều antenna → độ tin cậy.
- **Beamforming**: Tập trung năng lượng về phía receiver.

#### Bảo mật WiFi
| Chuẩn | Năm | Xác thực | Mã hóa |
|-------|-----|----------|--------|
| WEP | 1997 | Shared key | RC4 (yếu) |
| WPA | 2003 | PSK/802.1X | TKIP |
| **WPA2** | 2004 | PSK/802.1X | **AES-CCMP** |
| **WPA3** | 2018 | SAE (PSK), 802.1X | AES-GCMP, 192-bit (Enterprise) |

- **WPA2-PSK**: 4-way handshake (EAPOL) → PTK (Pairwise Transient Key).
- **WPA3-Personal**: SAE (Simultaneous Authentication of Equals) → chống offline dictionary attack.
- **802.1X / EAP**: Enterprise (RADIUS), EAP-TLS, EAP-TTLS, PEAP.

### 6.3 Mạng di động (Cellular) - 4G LTE & 5G
#### 4G LTE (Long Term Evolution)
- **Kiến trúc**: UE ↔ eNodeB ↔ EPC (MME, SGW, PGW, HSS, PCRF).
- **Radio**: OFDMA (downlink), SC-FDMA (uplink).
- **Bearer**: Default + Dedicated (QCI - QoS Class Identifier).

#### 5G NR (New Radio)
- **Kiến trúc**: UE ↔ gNB ↔ 5GC (AMF, SMF, UPF, AUSF, UDM, PCF, NEF, NRF).
- **Service-based Architecture (SBA)**: HTTP/2, JSON, NF registry.
- **Network Slicing**: eMBB, URLLC, mMTC.
- **Spectrum**: Sub-6 GHz (FR1), mmWave (FR2: 24-52 GHz).
- **Key Tech**: Massive MIMO, Beamforming, NOMA, Flexible Numerology, Mini-slot.
- **Xác thực 5G**: 5G-AKA, EAP-AKA', SUCI (Subscription Concealed Identifier), AUSF (Authentication Server Function).

### 6.4 Quản lý di động (Mobility Management)
- **Home Network / Visited Network**: Home Agent, Foreign Agent (Mobile IP).
- **Handover**: Hard handover (break-before-make) vs Soft/Softer handover.
- **5G**: Xn handover (gNB-gNB), N2 handover (AMF involvement).

---

## CHƯƠNG 7: AN NINH MẠNG (NETWORK SECURITY)

### 7.1 Mục tiêu an ninh
| Mục tiêu | Mô tả |
|----------|-------|
| **Confidentiality (Bảo mật)** | Chỉ bên được phép mới đọc được dữ liệu |
| **Integrity (Toàn vẹn)** | Dữ liệu không bị sửa đổi không được phép |
| **Authentication (Xác thực)** | Xác minh danh tính thực thể |
| **Non-repudiation (Phủ nhận)** | Không thể chối cối hành động đã thực hiện |
| **Availability (Khả dụng)** | Dịch vụ luôn sẵn sàng |

### 7.2 Mật mã học (Cryptography)

#### 7.2.1 Mật mã đối xứng (Symmetric Key)
- **Cùng khóa** encrypt/decrypt: AES (128/192/256), ChaCha20, 3DES (deprecated).
- **Mode**: ECB (không an toàn), CBC, CTR, GCM (AEAD), CCM.
- **Key Distribution Problem**: Cần kênh an toàn để chia sẻ khóa.

#### 7.2.2 Mật mã khóa công khai (Public Key / Asymmetric)
- **Key pair**: Public key (công khai), Private key (bí mật).
- **RSA**: Kích thước khóa ≥ 2048-bit, encrypt/sign.
- **ECC (Elliptic Curve)**: Khóa nhỏ hơn, nhanh hơn (P-256, P-384, Curve25519).
- **Diffie-Hellman (DH)**: Trao đổi khóa trên kênh công khai.
  - **Ephemeral (DHE/ECDHE)**: Forward Secrecy.

#### 7.2.3 Hàm băm (Hash Function)
- **Đặc tính**: One-way, collision-resistant, fixed output.
- **Thuật toán**: SHA-256, SHA-384, SHA-3, BLAKE2.
- **HMAC**: Keyed-hash cho message integrity + authentication.

#### 7.2.4 Chữ ký số (Digital Signature)
- **Quy trình**: Sign = Encrypt(Hash(m), Private_Key), Verify = Decrypt(Sign, Public_Key) == Hash(m).
- **Ứng dụng**: PKI, Certificate, Code signing, Document signing.

#### 7.2.5 Chứng chỉ công khai (PKI - Public Key Infrastructure)
- **CA (Certificate Authority)**: Ký chứng chỉ bind Identity ↔ Public Key.
- **X.509 Certificate**: Subject, Issuer, Validity, Public Key, Signature, Extensions (SAN, Key Usage, EKU).
- **Chain of Trust**: Root CA → Intermediate CA → Leaf Certificate.
- **Revocation**: CRL (Certificate Revocation List), OCSP (Online Certificate Status Protocol).

### 7.3 Bảo mật Email
- **PGP/GPG**: Web of Trust, sign + encrypt.
- **S/MIME**: X.509 certificate, sign + encrypt.
- **Kỹ thuật**: Hybrid encryption (Session key + Public key).

### 7.4 TLS (Transport Layer Security)
- **Phiên bản**: SSL 3.0 (deprecated) → TLS 1.0/1.1 (deprecated) → **TLS 1.2** → **TLS 1.3** (RFC 8446, 2018).
- **Cung cấp**: Confidentiality (AES-GCM, ChaCha20-Poly1305), Integrity (AEAD), Authentication (X.509, PSK).
- **Handshake TLS 1.3 (1-RTT)**:
  1. ClientHello (key_share, supported_groups, cipher_suites)
  2. ServerHello (key_share, certificate, CertificateVerify, Finished)
  3. Client (Finished) → Application Data
- **0-RTT (Resumption)**: PSK từ phiên trước, dễ bị replay attack.
- **Cipher Suites TLS 1.3**: Chỉ 5 suites (AES-GCM, ChaCha20-Poly1305), bắt buộc (EC)DHE.

### 7.5 IPsec (Network Layer Security)
- **Hai chế độ**:
  - **Transport Mode**: Chỉ encrypt payload, giữ IP header gốc.
  - **Tunnel Mode**: Encrypt toàn bộ IP datagram, đóng gói trong IP header mới.
- **Hai giao thức**:
  - **AH (Authentication Header - RFC 4302)**: Integrity + Auth, KHÔNG encrypt.
  - **ESP (Encapsulating Security Payload - RFC 4303)**: Integrity + Auth + Encryption (phổ biến hơn).
- **Security Association (SA)**:.Single direction, stateful (SPI, keys, algorithms, seq#).
- **SPD/SAD**: Security Policy Database (what to do), Security Association Database (how to do).
- **IKE (Internet Key Exchange)**: IKEv2 (RFC 7296).
  - Phase 1: IKE SA (ISAKMP) -.auth (PSK/PKI), Diffie-Hellman.
  - Phase 2: Child SA (IPsec SAs) - quick mode.

### 7.6 An ninh mạng không dây & Di động
- **WiFi**: WPA2/WPA3, 4-way handshake, 802.1X/EAP, RADIUS, Eduroam.
- **5G**: 5G-AKA, SUCI, AUSF/SEAF/AMF, TLS tunnel giữa visited/home network.

### 7.7 An ninh vận hành (Operational Security)

#### Firewall (Tường lửa)
| Loại | Đặc điểm |
|------|----------|
| **Stateless Packet Filter** | Kiểm tra từng gói: IP src/dst, port src/dst, protocol, TCP flags. Không theo dõi trạng thái kết nối. |
| **Stateful Packet Filter** | Theo dõi connection state table (SYN, ESTABLISHED, FIN). Chỉ cho phép gói "has sense". |
| **Application Gateway (Proxy)** | Hiểu giao thức ứng dụng (HTTP, FTP, SMTP). Filter ở lớp 7. |

- **ACL (Access Control List)**: Rules (action, condition) áp dụng top-down.
- **DMZ (Demilitarized Zone)**: VLAN cho public servers (Web, DNS, Mail), cách biệt internal network.

#### IDS/IPS (Intrusion Detection/Prevention Systems)
- **Signature-based**: So khớp pattern tấn công đã biết (Snort rules).
- **Anomaly-based**: Học baseline normal behavior → phát hiện lệch.
- **Deployment**: Network-based (NIDS), Host-based (HIDS).
- **Địa điểm**: Internet → Firewall → DMZ (IDS) → Internal Network (IDS).

---

## TỔNG KẾT & SƠ ĐỒ TƯ DUY

```
┌─────────────────────────────────────────────────────────────┐
│                    MẠNG MÁY TÍNH (TOP-DOWN)                  │
├─────────────────────────────────────────────────────────────┤
│  LỚP 5: ỨNG DỤNG (Application)                              │
│  HTTP, DNS, SMTP, POP3, IMAP, P2P, Video Streaming, Socket  │
├─────────────────────────────────────────────────────────────┤
│  LỚP 4: VẬN CHUYỂN (Transport)                              │
│  UDP (nhanh, không tin cậy)  │  TCP (tin cậy, kiểm soát    │
│                              │  luồng, tắc nghẽn)            │
├─────────────────────────────────────────────────────────────┤
│  LỚP 3: MẠNG (Network)                                      │
│  IP (v4/v6), Định tuyến (OSPF, BGP), Router, SDN, NAT       │
├─────────────────────────────────────────────────────────────┤
│  LỚP 2: LIÊN KẾT (Link)                                     │
│  Ethernet, Switch, VLAN, WiFi (802.11), MPLS, Data Center   │
├─────────────────────────────────────────────────────────────┤
│  LỚP 1: VẬT LÝ (Physical)                                   │
│  Cáp, Vô tuyến, Băng thông, Độ trễ, Mất gói                 │
└─────────────────────────────────────────────────────────────┘
                        ▲
                        │ CẮT NGANG (CROSS-CUTTING)
                        ▼
            ┌───────────────────────┐
            │     AN NINH MẠNG      │
            │  Crypto, TLS, IPsec,  │
            │  Firewall, IDS, WiFi/ │
            │  5G Security          │
            └───────────────────────┘
```

---

## TÀI LIỆU THAM KHẢO
1. **Computer Networking: A Top-Down Approach, 9th Edition** - Kurose & Ross (Pearson, 2025)
2. RFCs: 791 (IPv4), 8200 (IPv6), 793 (TCP), 768 (UDP), 8446 (TLS 1.3), 4301/4303 (IPsec), 5246 (TLS 1.2)
3. IEEE 802.3 (Ethernet), 802.11 (WiFi), 802.1Q (VLAN)
4. 3GPP TS 38.xxx (5G NR)

---

*Tài liệu được hệ thống hóa từ slide giảng dạy Computer Networking: A Top-Down Approach 9th edition. Dùng cho mục đích học tập, ôn tập.*