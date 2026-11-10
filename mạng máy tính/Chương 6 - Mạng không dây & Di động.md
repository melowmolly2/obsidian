# Chương 6: Mạng Không dây & Di động (Wireless & Mobile Networks)

> Nguồn: *Computer Networking: A Top-Down Approach, 9th ed.* - Chapter 6 (slide Chapter 7 trong PPTX)

---

## 6.1 Đặc thách của truyền không dây (Wireless Challenges)

| Thách thức | Mô tả | Hệ quả |
|------------|-------|--------|
| **Path Loss** | Suy giảm tín hiệu theo khoảng cách (~dⁿ, n=2-4) | Cần power control, rate adaptation |
| **Shadowing** | Cản trở vật lý (tường, tòa nhà) | Log-normal fading, coverage holes |
| **Multipath Fading** | Nhiều path đến receiver → constructive/destructive interference | Frequency-selective fading, ISI |
| **Doppler Shift** | Chuyển động → frequency shift | Channel coherence time giảm |
| **Interference** | Co-channel, adjacent-channel, non-WiFi (microwave, Bluetooth) | SNR giảm, throughput giảm |
| **Hidden Terminal** | A nghe không thấy C, nhưng cả hai đến B | Collision tại B, cần RTS/CTS |
| **Exposed Terminal** | B nghe A, defer truyền cho C (dù C không bị ảnh hưởng) | Throughput thừa, cần spatial reuse |

### SNR & Rate Adaptation
- **SNR (Signal-to-Noise Ratio)** = Signal Power / Noise Power
- **Modulation & Coding Scheme (MCS)**: Chọn theo SNR (QPSK 1/2 → 256-QAM 5/6)
- **Rate Adaptation Algorithms**: Minstrel, SampleRate, AMRR, RCPI-based

---

## 6.2 WiFi (IEEE 802.11) - Chi tiết

### 6.2.1 Kiến trúc & Terminology
| Term | Mô tả |
|------|-------|
| **STA (Station)** | Thiết bị client (laptop, phone, IoT) |
| **AP (Access Point)** | Infrastructure mode: Bridge wireless ↔ wired |
| **BSS (Basic Service Set)** | 1 AP + associated STAs (Infrastructure BSS) |
| **IBSS** | Independent BSS (Ad-hoc, không AP) |
| **ESS (Extended Service Set)** | Nhiều BSS nối qua Distribution System (DS), cùng SSID |
| **SSID** | Service Set Identifier (tên mạng, 0-32 bytes) |
| **BSSID** | MAC address của AP (trong BSS) |

### 6.2.2 MAC Layer - DCF (Distributed Coordination Function)

#### Interframe Spaces (IFS)
| IFS | Giá trị (802.11g) | Ưu tiên | Dùng cho |
|-----|------------------|---------|----------|
| **SIFS** | 16 μs | Cao nhất | ACK, CTS, BlockAck, MPDU trong TXOP |
| **PIFS** | 25 μs | Cao | PCF (Point Coordination Function) |
| **DIFS** | 34 μs | Thấp | Data, Management frames (DCF) |
| **EIFS** | DIFS + ACK time | Thấp nhất | Sau frame lỗi (không decode được) |

#### Backoff Procedure
```
1. Sense medium idle for DIFS
2. Choose random backoff counter: k ∈ [0, CW-1]
   CW = Contention Window, khởi tạo CWmin, max CWmax
   CWmin = 15 (802.11b), 15/31/63/127 (802.11a/g/n/ac/ax)
3. Decrement counter each idle slot time (σ = 9/20/50 μs)
4. Counter = 0 → Transmit
5. Collision/No ACK → CW = min(2×CW, CWmax), retry
6. Success → CW = CWmin
```

#### Frame Exchange Sequences
**Basic Access (Data + ACK)**:
```
DIFS → Backoff → DATA → SIFS → ACK
```

**RTS/CTS (Hidden Terminal Mitigation)**:
```
DIFS → Backoff → RTS → SIFS → CTS → SIFS → DATA → SIFS → ACK
```
- **RTS**: Request to Send (duration field → NAV)
- **CTS**: Clear to Send (duration field → NAV)
- **NAV (Network Allocation Vector)**: Virtual carrier sense, các STA khác defer

#### Frame Types (802.11)
| Category | Subtypes | Mô tả |
|----------|----------|-------|
| **Management** | Beacon, Probe Req/Resp, Auth, Assoc/Reassoc, Disassoc, Deauth | Quản lý BSS |
| **Control** | RTS, CTS, ACK, BlockAck, PS-Poll | Hỗ trợ truyền data |
| **Data** | Data, Data+CF-Ack, Data+CF-Poll, QoS Data | Payload người dùng |

### 6.2.3 Physical Layer (PHY) Standards Evolution

| Standard | Brand | Year | Band | Max PHY Rate | Key Features |
|----------|-------|------|------|--------------|--------------|
| **802.11b** | WiFi 1 | 1999 | 2.4 GHz | 11 Mbps | DSSS, CCK |
| **802.11a** | WiFi 2 | 1999 | 5 GHz | 54 Mbps | OFDM (64 subcarriers) |
| **802.11g** | WiFi 3 | 2003 | 2.4 GHz | 54 Mbps | OFDM, backward compatible with b |
| **802.11n** | **WiFi 4** | 2009 | 2.4/5 GHz | 600 Mbps | MIMO (4×4), 40 MHz, Frame Aggregation (A-MPDU, A-MSDU), BlockAck |
| **802.11ac** | **WiFi 5** | 2013 | 5 GHz | 6.93 Gbps | MU-MIMO (DL, 4×4), 80/160 MHz, 256-QAM, Beamforming (explicit) |
| **802.11ax** | **WiFi 6/6E** | 2019/2020 | 2.4/5/6 GHz | 9.6 Gbps | **OFDMA**, MU-MIMO (UL+DL, 8×8), 1024-QAM, BSS Coloring, TWT, OFDMA RU |
| **802.11be** | **WiFi 7** | 2024 | 2.4/5/6 GHz | 46 Gbps | 320 MHz, 4096-QAM, **MLO** (Multi-Link Operation), 16 streams, Preamble Puncturing, MLO |

### 6.2.4 Key Technologies Deep Dive

#### OFDM / OFDMA
- **OFDM**: Chia channel thành nhiều **orthogonal subcarriers** (64/256/512/1024/2048)
- **Cyclic Prefix (CP)**: Chống ISI (0.8/1.6/3.2 μs)
- **OFDMA (802.11ax/be)**: Chia subcarriers thành **Resource Units (RU)** (26/52/106/242/484/996/1992-tone) → multiple users đồng thời

#### MIMO (Multiple Input Multiple Output)
| Mode | Mô tả |
|------|-------|
| **Spatial Multiplexing** | Truyền **khác nhau** data streams song song → tăng throughput (rank = min(Tx, Rx antennas)) |
| **Spatial Diversity** | Truyền **cùng** data qua nhiều antenna → tăng reliability (STBC, CDD) |
| **Beamforming** | Tiền mã hóa (precoding) tập trung năng lượng về receiver → tăng SNR |
| **MU-MIMO** | AP truyền đến **nhiều STA** cùng lúc trên cùng resource (DL MU-MIMO từ ac, UL+DL từ ax) |

#### BSS Coloring (802.11ax/be) - Spatial Reuse
- **Color** (6-bit) trong PHY header → phân biệt BSS overlapping
- **OBSS PD (Overlapping BSS Preamble Detection)**: Nếu color khác và RSSI < threshold → **transmit cùng lúc** (spatial reuse)
- **SR (Spatial Reuse) TXOP**: Giảm power, giảm NAV

#### TWT (Target Wake Time) - 802.11ax/be
- AP và STA **đồng bộ lịch ngủ/thức** → tiết kiệm pin IoT/mobile
- STA chỉ thức dậy tại negotiated TWT → giảm contention

#### MLO (Multi-Link Operation) - 802.11be (WiFi 7)
- **Simultaneous** sử dụng nhiều band/link (2.4+5+6 GHz)
- **Straddling**: Tx trên link 1, Rx trên link 2
- **Aggregated MSDU**: Load balancing, redundancy, ultra-low latency

#### Preamble Puncturing (802.11be)
- **Puncture** (tắt) các subchannel bị interference/radar trong channel rộng (320 MHz) → vẫn dùng phần còn lại

### 6.2.5 WiFi Security

| Standard | Year | Authentication | Encryption | Key Derivation |
|----------|------|----------------|------------|----------------|
| **WEP** | 1997 | Shared Key (Open/Shared) | RC4 (40/104-bit) | Static key (YẾU) |
| **WPA** | 2003 | PSK / 802.1X (EAP) | TKIP (RC4 + MIC) | PMK → PTK (4-way handshake) |
| **WPA2** | 2004 | PSK / 802.1X | **AES-CCMP** (Counter+CBC-MAC) | PMK → PTK (4-way handshake) |
| **WPA3** | 2018 | **SAE** (PSK) / 802.1X (EAP-TLS) | AES-GCMP (128/192/256) | **SAE** (Dragonfly) / Suite B |

#### WPA2-Personal (PSK) - 4-Way Handshake
```
AP (Authenticator)                    STA (Supplicant)
    |                                       |
    |------- ANonce ----------------------->|  (Commit)
    |                                       |
    |<------ SNonce, MIC -------------------|  (Confirm)
    |                                       |
    |------- GTK (encrypted), MIC --------->|  (Confirm)
    |                                       |
    |<------ ACK ---------------------------|  (Complete)
```
- **PMK** = PBKDF2(SSID, PSK, 4096 iterations)
- **PTK** = PRF-512(PMK, "Pairwise key expansion", ANonce || SNonce || AMAC || SMAC)
- **GTK**: Group Temporal Key (broadcast/multicast)

#### WPA3-Personal: SAE (Simultaneous Authentication of Equals) - RFC 7664
- **Dragonfly Key Exchange** (PAKE - Password Authenticated Key Exchange)
- **Chống offline dictionary attack**: Không capture handshake để brute-force
- **Forward Secrecy**: Mỗi session key độc lập
- **Anti-clogging token**: Chống DoS (commit message có token)

#### Enterprise (802.1X / EAP)
```
STA (Supplicant) ←→ AP (Authenticator) ←→ RADIUS Server (Authentication Server)
       EAPOL (EAP over LAN)                RADIUS (EAP over RADIUS)
```
- **EAP Methods**: EAP-TLS (certs), PEAP (TLS tunnel + MSCHAPv2), EAP-TTLS, EAP-PWD, EAP-AKA' (5G)
- **RADIUS**: AAA (Authentication, Authorization, Accounting)
- **Key Hierarchy**: MSK (Master Session Key) → PMK → PTK/GTK

---

## 6.3 Mạng Di động (Cellular Networks) - 4G LTE & 5G NR

### 6.3.1 4G LTE (Long Term Evolution) - 3GPP Release 8+

#### Kiến trúc EPS (Evolved Packet System)
```
UE (User Equipment) ←→ eNodeB (Evolved Node B) ←→ EPC (Evolved Packet Core)
                                                          ↓
                              ┌───────────────────────────┼───────────────────────────┐
                              MME                    SGW                      PGW
                          (Control)            (User Plane)            (Gateway to Internet)
                              ↓                    ↓                        ↓
                          HSS (Subscr)       PCRF (Policy)            PCRF (Charging)
```

| Network Element | Chức năng |
|-----------------|-----------|
| **MME** | Mobility Management Entity: Auth, security, bearer mgmt, idle mode tracking |
| **HSS** | Home Subscriber Server: User profile, authentication vectors (AV) |
| **SGW** | Serving Gateway: Anchor user plane during handover, lawful intercept |
| **PGW** | PDN Gateway: IP address allocation, policy enforcement, charging, external IP connectivity |
| **PCRF** | Policy and Charging Rules Function: QoS, charging rules |
| **eNodeB** | Radio access: Scheduling, HARQ, RRC, measurements, handover execution |

#### Radio Interface (E-UTRA)
- **Downlink**: **OFDMA** (Orthogonal FDMA) - 12 subcarriers = 1 RB (Resource Block) = 180 kHz
- **Uplink**: **SC-FDMA** (Single Carrier FDMA) - DFT-spread OFDM, PAPR thấp hơn
- **Frame**: 10 ms = 10 subframes (1 ms) = 20 slots (0.5 ms)
- **Subcarrier spacing**: 15 kHz (normal CP), 7.5 kHz (extended CP)
- **MIMO**: Up to 4×4 (DL), 2×2 (UL)
- **Carrier Aggregation (CA)**: Gộp tối đa 5 CCs (Component Carriers) → 100 MHz total

#### Bearer & QoS
- **EPS Bearer**: Default Bearer (always on) + Dedicated Bearers (QoS-specific)
- **QCI (QoS Class Identifier)**: 1-9 (GBR: 1-4, Non-GBR: 5-9)
  | QCI | Type | Priority | Delay | Loss | Example |
  |-----|------|----------|-------|------|---------|
  | 1 | GBR | 2 | 100ms | 10⁻² | VoLTE |
  | 5 | Non-GBR | 1 | 100ms | 10⁻⁶ | IMS Signaling |
  | 6 | Non-GBR | 6 | 300ms | 10⁻⁶ | Video (buffered) |
  | 7 | Non-GBR | 7 | 100ms | 10⁻³ | Voice/Video (live) |
  | 9 | Non-GBR | 9 | 300ms | 10⁻⁶ | Best effort (default) |

---

### 6.3.2 5G NR (New Radio) - 3GPP Release 15/16/17/18

#### Kiến trúc 5GC (5G Core) - Service Based Architecture (SBA)
```
UE ←→ gNB (Next Gen NodeB) ←→ 5GC (Network Functions)
                                              ↓
    ┌─────────────┬─────────────┬─────────────┼─────────────┬─────────────┐
    AMF         SMF           UPF           AUSF        UDM           PCF
 (Access &    (Session      (User Plane    (Auth       (Unified      (Policy
  Mobility)    Management)   Function)     Server)      Data Mgmt)     Control)
                                              ↓
                                          NEF (Network
                                           Exposure)
                                           NRF (NF Repository)
```
| NF | Chức năng |
|----|-----------|
| **AMF** | Access & Mobility Management: Registration, connection mgmt, handover, NAS signaling |
| **SMF** | Session Management: PDU session establishment, IP allocation, UPF selection |
| **UPF** | User Plane Function: Packet routing, forwarding, inspection, QoS enforcement |
| **AUSF** | Authentication Server Function: 5G-AKA, EAP-AKA', SUCI protection |
| **UDM** | Unified Data Management: Subscription data, authentication credentials |
| **PCF** | Policy Control Function: QoS policies, charging rules |
| **NEF** | Network Exposure Function: Northbound API cho 3rd party apps |
| **NRF** | NF Repository Function: Service discovery, registration |
| **NSSF** | Network Slice Selection Function: Slice selection/assistance |

#### 5G New Radio (NR) - Air Interface
| Đặc điểm | 4G LTE | 5G NR |
|----------|--------|-------|
| **Spectrum** | Sub-6 GHz (FR1) | FR1 (450 MHz - 7.125 GHz) + **FR2 mmWave (24.25 - 52.6 GHz)** |
| **Numerology** | Fixed 15 kHz SCS | **Flexible SCS**: 15, 30, 60, 120, 240, 480 kHz (×2ⁿ) |
| **Slot Duration** | 1 ms (14 symbols) | **Variable**: 1 ms @ 15 kHz, 0.5 ms @ 30 kHz, 0.25 ms @ 60 kHz... |
| **Mini-slot** | Không | **2/4/7 symbols** (URLLC) |
| **CP Type** | Normal/Extended | Normal, **Extended** (large cell) |
| **Waveform** | OFDMA (DL), SC-FDMA (UL) | **CP-OFDM** (DL+UL), **DFT-s-OFDM** (UL optional) |
| **MIMO** | Up to 4×4 | **Massive MIMO** (64/128/256 antennas), **Multi-user MIMO**, **Beamforming** |
| **Duplex** | FDD / TDD | **TDD** (dominant), FDD, **Dynamic TDD**, **SUL** (Supplementary UL) |
| **Bandwidth** | Max 20 MHz/CC, 5 CCs = 100 MHz | **Max 100 MHz (FR1), 400 MHz (FR2)**, CA up to 16 CCs = 800 MHz/1.6 GHz |
| **Modulation** | 256-QAM | **1024-QAM** (FR1), 256/64-QAM (FR2) |

#### 5G Use Cases (Triangle)
| Use Case | KPI Targets | Slice Type |
|----------|-------------|------------|
| **eMBB** (Enhanced Mobile Broadband) | Peak DL 20 Gbps, UL 10 Gbps; User experienced 100 Mbps DL / 50 Mbps UL | Slice 1 (High throughput) |
| **URLLC** (Ultra-Reliable Low Latency) | Latency 1 ms (user plane), 0.5 ms (control); Reliability 99.9999% | Slice 2 (Low latency, high reliability) |
| **mMTC** (Massive Machine Type Comms) | 1M devices/km²; 10 yr battery; Low cost | Slice 3 (High connection density) |

#### Network Slicing
- **NSSAI (Network Slice Selection Assistance Information)**: S-NSSAI = SST (Slice/Service Type) + SD (Slice Differentiator)
- **SST values**: 1=eMBB, 2=URLLC, 3=mMTC, 128-255=Operator specific
- **Network Slice Instance**: Dedicated/Shared NF resources, isolation (resource, security, management)

#### 5G Authentication & Security
- **5G-AKA**: Improved AKA (vs 4G) - home network control, key separation
- **SUCI (Subscription Concealed Identifier)**: Encrypt SUPI (IMSI) bằng public key của home network → **privacy** (no IMSI catcher)
- **EAP-AKA'**: Extensible Authentication Protocol for 5G (RFC 5448 + RFC 9048)
- **AUSF/SEAF/AMF**: Authentication distributed
- **Key Hierarchy**: K_SEAF → K_AMF → K_NASenc/K_NASint/K_gNB → K_UPenc/K_UPint

---

## 6.4 Mobility Management (Quản lý di động)

### Mobile IP (IPv4 - RFC 5944, IPv6 - RFC 6275)
| Concept | Mô tả |
|---------|-------|
| **Home Network** | Mạng gốc của Mobile Node (MN) |
| **Home Address** | IP cố định tại Home Network |
| **Foreign Network** | Mạng đang truy cập (Visited) |
| **Care-of Address (CoA)** | IP tạm tại Foreign Network |
| **Home Agent (HA)** | Router tại Home Network, tunnel traffic đến MN |
| **Foreign Agent (FA)** | Router tại Foreign Network (IPv4) |
| **Binding Update** | MN báo HA CoA mới |
| **Triangle Routing** | CN → HA → MN (suboptimal) → Route Optimization (Binding Update to CN) |

### Handover (Handoff)
| Loại | Đặc điểm |
|------|----------|
| **Hard Handover** | Break-before-make (LTE: X2-based, N2-based) |
| **Soft/Softer Handover** | Make-before-break (CDMA, WCDMA) - multiple cells đồng thời |
| **Horizontal Handover** | Cùng technology (LTE ↔ LTE, 5G ↔ 5G) |
| **Vertical Handover** | Khác technology (WiFi ↔ LTE, LTE ↔ 5G) |

#### 5G Handover
| Handover Type | Path | Latency |
|---------------|------|---------|
| **Xn Handover** | gNB1 ↔ gNB2 (direct) | ~10-20 ms |
| **N2 Handover** | gNB1 → AMF → gNB2 | ~50-100 ms |
| **Dual Connectivity (EN-DC / NR-DC)** | MN kết nối 2 gNB/eNodeB đồng thời | Seamless (no break) |

---

## 6.5 Spectrum Management

| Spectrum Type | Đặc điểm | Ví dụ |
|---------------|----------|-------|
| **Licensed** | Độc quyền, auction, carrier (Viettel, VNPT, MobiFone) | 700/900/1800/2100/2600 MHz, 3.5 GHz, 26/28 GHz |
| **Shared** | Dynamic sharing, incumbent priority (CBSD, SAS) | **CBRS** 3.5 GHz (US), LSA (Europe) |
| **Unlicensed** | Free, power limits, listen-before-talk | **2.4 GHz**, **5 GHz** (WiFi), **6 GHz** (WiFi 6E/7), **60 GHz** (802.11ad/ay) |

### CBRS (Citizens Broadband Radio Service) - 3.5 GHz US
- **Tier 1**: Incumbent (Navy radar, satellite) - Protected
- **Tier 2**: **PAL** (Priority Access License) - Auctioned, 10 MHz, 3 years
- **Tier 3**: **GAA** (General Authorized Access) - Free, opportunistic
- **SAS** (Spectrum Access System): Cloud-based dynamic coordinator

---

## Tóm tắt chương 6

| Chủ đề | Key Points |
|--------|------------|
| **Wireless Challenges** | Path loss, shadowing, multipath, Doppler, interference, hidden/exposed terminal |
| **WiFi Architecture** | BSS/ESS/IBSS, SSID/BSSID, AP/STA |
| **802.11 MAC** | CSMA/CA, DCF, DIFS/SIFS, Backoff, RTS/CTS, NAV, Frame types |
| **PHY Evolution** | 802.11b/a/g → n (WiFi 4) → ac (WiFi 5) → ax (WiFi 6/6E) → be (WiFi 7) |
| **Key PHY Techs** | OFDM/OFDMA, MIMO (SU/MU, Spatial Mux/Diversity), Beamforming, BSS Coloring, TWT, MLO, Preamble Puncturing |
| **WiFi Security** | WEP→WPA→WPA2 (AES-CCMP, 4-way handshake)→WPA3 (SAE, GCMP, 192-bit), 802.1X/EAP |
| **4G LTE** | EPS (MME/SGW/PGW/HSS/PCRF), eNodeB, OFDMA/SC-FDMA, CA, QCI Bearers |
| **5G NR** | 5GC (SBA: AMF/SMF/UPF/AUSF/UDM/PCF/NEF/NRF), FR1+FR2, Flexible Numerology, Mini-slot, Massive MIMO, Beamforming, Network Slicing (eMBB/URLLC/mMTC) |
| **5G Security** | 5G-AKA, SUCI (encrypted IMSI), EAP-AKA', AUSF/SEAF/AMF, Key hierarchy |
| **Mobility** | Mobile IP (HA/FA/CoA), Handover (Hard/Soft, Xn/N2), Dual Connectivity |
| **Spectrum** | Licensed/Shared (CBRS/SAS)/Unlicensed (2.4/5/6/60 GHz) |

---

## Liên kết
- [[MỤC LỤC - Lý thuyết Mạng máy tính]]
- [[Chương 5 - Lớp Liên kết & LAN]]
- [[Chương 7 - An ninh mạng]]