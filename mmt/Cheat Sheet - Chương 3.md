# ⚡ Cheat Sheet: Chương 3 – Tầng giao vận (Transport Layer)

up:: [[Mạng máy tính MOC]]

## 1. Multiplexing & Demultiplexing
- **Multiplexing (Sender):** Gom dữ liệu từ nhiều socket, gắn header (port).
- **Demultiplexing (Receiver):** Dựa vào header (source/dest port, IP) để chuyển segment đúng socket.
  - **UDP socket:** Xác định bởi `(dest IP, dest port)`.
  - **TCP socket:** Xác định 4-tuple: `(source IP, source port, dest IP, dest port)`.

## 2. UDP (User Datagram Protocol)
- **Đặc điểm:** Unreliable, connectionless, best-effort.
- **Ưu điểm:** Nhanh, không overhead handshake, header nhỏ (8 bytes). Dùng cho DNS, streaming, gaming.

## 3. Reliable Data Transfer (RDT)
- **Rdt 1.0 $\to$ 2.0/2.1/2.2:** Dùng ACK, NAK, Sequence number (0, 1) chống lỗi bit.
- **Rdt 3.0 (Stop-and-Wait):** Thêm timer xử lý mất gói (loss). Hiệu suất thấp ($U_{sender}$ rất nhỏ).
- **Pipelined protocols:**
  - **Go-Back-N (GBN):** Window size $N$. Cumulative ACK. Khi timeout, gửi lại tất cả từ base.
  - **Selective Repeat (SR):** ACK riêng từng gói. Bộ đệm ở receiver. Gói lỗi/mất nào gửi lại gói đó.

## 4. TCP (Transmission Control Protocol)
- **Đặc điểm:** Connection-oriented, reliable, byte-stream, full-duplex, flow-controlled.
- **Handshake 3 bước (3-way handshake):**
  1. SYN ($seq = x$)
  2. SYN+ACK ($seq = y, ack = x+1$)
  3. ACK ($ack = y+1$)
- **Flow Control:** Receiver dùng `rwnd` (Receive Window) báo cho sender tránh tràn bộ đệm.
- **TCP Timeout/RTT:** EstimatedRTT = $(1-\alpha)\text{EstimatedRTT} + \alpha\text{SampleRTT}$. Timeout = EstimatedRTT + $4 \times \text{DevRTT}$.

## 5. TCP Congestion Control
- **AIMD (Additive Increase Multiplicative Decrease):** Tăng tuyến tính CWND, giảm một nửa khi mất gói.
- **Slow Start:** CWND bắt đầu từ 1 MSS, tăng theo cấp số nhân ($\times 2$ mỗi RTT) cho đến khi đạt `ssthresh`.
- **Congestion Avoidance:** Tăng tuyến tính (+1 MSS mỗi RTT) sau khi vượt `ssthresh`.
- **Fast Recovery / Fast Retransmit:** Phát hiện mất gói qua 3 duplicate ACKs $\to$ giảm CWND một nửa, không về Slow Start.
