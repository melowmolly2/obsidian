# Chương 3: Lớp Vận chuyển (Transport Layer)

> Nguồn: *Computer Networking: A Top-Down Approach, 9th ed.* - Chapter 3

---

## 3.1 Giới thiệu & Dịch vụ lớp vận chuyển

### Chức năng chính
- **Process-to-process communication** (dùng port number)
- **Multiplexing/Demultiplexing**: Gom/bóc tách dữ liệu từ nhiều socket
- **Error detection**: Checksum
- **Reliable delivery** (TCP): ACK, retransmission, sequencing
- **Flow control** (TCP): Receiver buffer management
- **Congestion control** (TCP): Network capacity management

### Multiplexing/Demultiplexing
| Giao thức | Demultiplexing key |
|-----------|-------------------|
| **UDP** | Destination port |
| **TCP** | 4-tuple: (src IP, src port, dst IP, dst port) |

---

## 3.2 UDP (User Datagram Protocol) - RFC 768

### Đặc điểm
- **Connectionless**: Không handshake
- **Unreliable**: Không ACK, không retransmit, không sequencing
- **No flow/congestion control**: Gửi nhanh bao nhiêu tùy ứng dụng
- **Low overhead**: Header 8 bytes
- **Message-oriented**: Giữ ranh giới message (không phải byte-stream)

### UDP Header (8 bytes)
```
 0      7 8     15 16    23 24    31
+--------+--------+--------+--------+
| Source | Destination | Length | Checksum |
|  Port  |    Port     |        |          |
+--------+--------+--------+--------+
```
- **Length**: UDP header + data (bytes)
- **Checksum**: Pseudo-header + UDP header + data (IPv4: optional, IPv6: mandatory)

### Ứng dụng dùng UDP
| Ứng dụng | Lý do |
|----------|-------|
| **DNS** | Nhỏ, nhanh, retry ở application layer |
| **DHCP** | Broadcast, client chưa có IP |
| **Streaming (RTP)** | Độ trễ thấp, mất gói chấp nhận được |
| **Gaming (Real-time)** | Latency critical, UDP + custom reliability |
| **QUIC / HTTP/3** | UDP + TLS 1.3 built-in, 0-RTT, multiplexing |
| **SNMP, NTP, TFTP** | Đơn giản, nhẹ |

---

## 3.3 TCP (Transmission Control Protocol) - RFC 793, 9293

### Đặc điểm chính
- **Connection-oriented**: 3-way handshake thiết lập kết nối
- **Reliable**: Sequence number, ACK, retransmission
- **Byte-stream**: Không ranh giới message (application tự framing)
- **Full-duplex**: Hai chiều đồng thời
- **Flow control**: Sliding window (rwnd)
- **Congestion control**: AIMD, Slow Start, Fast Recovery
- **In-order delivery**: Sắp xếp lại tại receiver

### TCP Header (20 bytes cơ bản, có options)
```
 0                   1                   2                   3
 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|          Source Port          |       Destination Port        |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                        Sequence Number                        |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                    Acknowledgment Number                      |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|  Data |       |U|A|P|R|S|F|                               |
| Offset| Res.  |R|C|S|S|Y|I|            Window Size         |
|       |       |G|K|H|T|N|N|                               |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|           Checksum            |         Urgent Pointer      |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|                    Options (Variable)                         |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```
**Flags**: URG, ACK, PSH, RST, SYN, FIN (+ ECE, CWR, NS cho ECN)

### 3.3.1 Thiết lập kết nối: 3-Way Handshake
```
Client                           Server
  |                               |
  |----- SYN (seq=x) ------------>|  SYN_RCVD
  |                               |
  |<---- SYN-ACK (seq=y, ack=x+1)-|  ESTABLISHED
  |                               |
  |----- ACK (ack=y+1) ---------->|  ESTABLISHED
  |                               |
```
- **ISN (Initial Sequence Number)**: Randomized (tránh old duplicate segments)
- **SYN cookie**: Chống SYN flood (server không lưu state cho SYN_RCVD)

### 3.3.2 Ngắt kết nối
```
Active Close (Client)          Passive Close (Server)
      |                            |
      |----- FIN (seq=u) -------->|  CLOSE_WAIT
      |                            |  (ACK sent)
      |<---- ACK (ack=u+1) -------|  FIN_WAIT_2
      |                            |
      |                            |  (App closes)
      |<---- FIN (seq=v) --------|  LAST_ACK
      |                            |
      |----- ACK (ack=v+1) ------>|  CLOSED
      |       TIME_WAIT (2*MSL)   |
      |                            |
```
- **TIME_WAIT**: 2×MSL (Maximum Segment Lifetime, thường 60s) → đảm bảo ACK cuối cùng đến được
- **RST**: Abort connection (error, port closed)

### 3.3.3 Truyền dữ liệu tin cậy

#### Sequence Number & ACK
- **Sequence number**: Byte number của **byte đầu tiên** trong segment
- **ACK number**: Sequence number của **byte tiếp theo mong đợi** (cumulative ACK)
- **Window**: Số byte có thể gửi mà chưa cần ACK = `min(cwnd, rwnd)`

#### Retransmission Mechanisms
| Cơ chế | Trigger | Hành động |
|--------|---------|-----------|
| **Timeout (RTO)** | Timer hết hạn | Retransmit segment, `cwnd = 1 MSS`, `ssthresh = cwnd/2`, Slow Start |
| **Fast Retransmit** | 3 Duplicate ACKs | Retransmit ngay (không chờ timeout), Fast Recovery |
| **SACK (Selective ACK)** | Option négociated | Receiver báo chính xác block nào nhận được → sender retransmit chính xác |

#### RTO (Retransmission Timeout) Calculation
```
SampleRTT = measured RTT cho segment (ignore retransmissions)
EstimatedRTT = (1-α) × EstimatedRTT + α × SampleRTT    (α = 0.125)
DevRTT = (1-β) × DevRTT + β × |SampleRTT - EstimatedRTT|   (β = 0.25)
RTO = EstimatedRTT + 4 × DevRTT
```
- **Karn's Algorithm**: Không sample RTT cho retransmitted segments
- **Exponential backoff**: RTO × 2 sau mỗi timeout liên tiếp

---

## 3.4 Flow Control (Kiểm soát luồng)

### Receiver Window (rwnd)
- **rwnd** = `RcvBuffer - (LastByteRcvd - LastByteRead)`
- Sender không được gửi quá `min(cwnd, rwnd)` byte chưa ACK
- **Zero window**: Receiver advertise rwnd=0 → Sender gửi **Zero Window Probe** (1 byte) định kỳ để kiểm tra

---

## 3.5 Congestion Control (Kiểm soát tắc nghẽn) - TCP Reno/CUBIC/BBR

### Biến số chính
- **cwnd (Congestion Window)**: Giới hạn sender-side dựa trên network condition
- **ssthresh (Slow Start Threshold)**: Ngưỡng chuyển từ Slow Start → Congestion Avoidance
- **MSS (Maximum Segment Size)**: Kích thước segment tối đa (thường 1460 bytes cho Ethernet)

### Các giai đoạn (TCP Reno)

| Giai đoạn | Điều kiện | Cập nhật cwnd |
|-----------|-----------|---------------|
| **Slow Start** | `cwnd < ssthresh` | `cwnd += 1 MSS` mỗi ACK nhận được (tăng cấp số: ~2× mỗi RTT) |
| **Congestion Avoidance** | `cwnd ≥ ssthresh` | `cwnd += 1 MSS` mỗi RTT (tăng tuyến tính: +1 MSS/RTT) |
| **Fast Recovery** | 3 DupACKs | `ssthresh = cwnd/2`, `cwnd = ssthresh + 3 MSS`, sau đó CA |
| **Timeout** | RTO expires | `ssthresh = cwnd/2`, `cwnd = 1 MSS`, Slow Start |

### Biến thể TCP hiện đại
| Variant | Năm | Đặc điểm nổi bật |
|---------|-----|------------------|
| **Tahoe** | 1988 | Chỉ Slow Start + CA, timeout → cwnd=1 |
| **Reno** | 1990 | + Fast Retransmit + Fast Recovery |
| **NewReno** | 1995 | Cải tiến Fast Recovery cho multiple losses |
| **SACK** | 1996 | Selective ACK option |
| **CUBIC** | 2006 | **Default Linux**, cubic function of time since last loss, RTT-fair |
| **BBR** | 2016 | **Google**, Model-based (BtlBw, RTprop), không dựa trên loss, pacing rate |
| **Vegas** | 1994 | Delay-based, phát hiện congestion trước khi loss |

### ECN (Explicit Congestion Notification) - RFC 3168
- Router **đánh dấu** gói (IP header: ECT(0)/ECT(1) → CE) thay vì drop
- Receiver phản hồi qua **ECE flag** trong TCP ACK
- Sender giảm cwnd như thể loss → **giảm latency, tăng throughput**
- Yêu cầu: Sender + Receiver + Router đều hỗ trợ

---

## 3.6 Kiểm soát tắc nghẽn dựa trên độ trễ (Delay-based)

| Thuật toán | Nguyên lý |
|------------|-----------|
| **TCP Vegas** | So sánh `Expected = cwnd/RTT_min` vs `Actual = cwnd/RTT_current`, tăng/giảm cwnd để giữ queue nhỏ |
| **TCP BBR** | Mô hình đường ống: 추정 `BtlBw` (bottleneck bandwidth) và `RTprop` (min RTT), pacing tại `BtlBw`, giữ `in-flight = BDP + margin` |
| **Copa / PCC** | Online learning / utility maximization |

---

## 3.7 Tóm tắt so sánh TCP vs UDP

| Đặc điểm | TCP | UDP |
|----------|-----|-----|
| **Kết nối** | Có (3-way handshake) | Không |
| **Tin cậy** | Có (ACK, retransmit, sequencing) | Không |
| **Thứ tự** | Có (in-order delivery) | Không |
| **Flow control** | Có (sliding window, rwnd) | Không |
| **Congestion control** | Có (AIMD, Slow Start, BBR...) | Không |
| **Header size** | 20-60 bytes | 8 bytes |
| **Hiện thực** | Kernel (complex state machine) | Kernel (simple) |
| **Phù hợp** | Web, Email, File transfer, SSH | DNS, DHCP, Streaming, Gaming, QUIC |

---

## 3.8 TCP Performance Issues & Optimizations

| Vấn đề | Giải pháp |
|--------|-----------|
| **Head-of-Line Blocking** | HTTP/2 multiplexing, HTTP/3 (QUIC streams) |
| **Bufferbloat** | AQM (CoDel, PIE, FQ_CoDel), BBR |
| **High latency (Long Fat Networks)** | Window scaling (RFC 1323), BBR |
| **Mobile handover** | MPTCP (Multipath TCP), QUIC connection migration |
| **Short flows (Web)** | TCP Fast Open (TFO), TLS 1.3 0-RTT, QUIC 0-RTT |

---

## Tóm tắt chương 3

| Chủ đề | Key Points |
|--------|------------|
| **UDP** | Không kết nối, không tin cậy, header 8B, DNS/Streaming/QUIC |
| **TCP** | Kết nối, tin cậy, byte-stream, flow+congestion control |
| **Handshake** | 3-way (SYN, SYN-ACK, ACK), ISN randomized |
| **Reliability** | Seq#, cumulative ACK, timeout (RTO), Fast Retransmit (3 DupACK), SACK |
| **Flow Control** | rwnd (receiver buffer), Zero Window Probe |
| **Congestion Control** | Slow Start (exp), CA (linear), Fast Recovery, CUBIC (default), BBR (model-based) |
| **ECN** | Router mark CE, receiver ECE, sender giảm cwnd không drop |
| **Optimizations** | Window scaling, TFO, MPTCP, QUIC |

---

## Liên kết
- [[MỤC LỤC - Lý thuyết Mạng máy tính]]
- [[Chương 2 - Lớp Ứng dụng]]
- [[Chương 4 - Lớp Mạng]]