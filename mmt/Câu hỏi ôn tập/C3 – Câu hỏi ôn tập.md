---
tags:
  - mmt/ôn-tập
  - mmt/câu-hỏi
  - mmt/chương-3
---

up:: [[Mạng máy tính MOC]]
prev:: [[C2 – Câu hỏi ôn tập]]

# 📝 Chương 3 – Transport Layer

> Dựa trên giáo trình *Computer Networking: A Top-Down Approach* – Kurose & Ross, 8th ed.
> Nguồn ghi chú: [[3.1 Giới thiệu về Transport Layer]] · [[3.2 Multiplexing, Demultiplexing]] · [[3.3 UDP]] · [[3.4 RDT]] · [[3.5 TCP]] · [[3.7 TCP Congestion Control]]

---

## 🔵 Phần A – Lý thuyết (tự luận)

> [!question] C3-1. Transport Layer vs. Network Layer
> Phân biệt **transport layer** và **network layer** về phạm vi cung cấp dịch vụ. Dùng ví dụ Ann–Bill để minh họa.

> [!success]- 📌 Đáp án & Giải thích
> 
> | | Transport Layer | Network Layer |
> |---|---|---|
> | **Phạm vi** | Giao tiếp logic giữa **các process** | Giao tiếp logic giữa **các host** |
> | **End point** | Process (định danh bởi port) | Host (định danh bởi IP) |
> | **Ví dụ giao thức** | TCP, UDP | IP |
> 
> **Ví dụ Ann–Bill (từ slide):**
> ```
> Nhà Ann: 12 đứa trẻ gửi thư → Nhà Bill: 12 đứa trẻ nhận thư
> 
> • Nhà = host
> • Trẻ em = process
> • Thư = app message
> • Ann & Bill (phân loại thư đến đúng tay người) = transport protocol
> • Bưu điện (chuyển thư giữa hai nhà) = network-layer protocol (IP)
> ```
> 
> **Transport layer làm gì mà Network layer không làm?**
> - **Multiplexing (sender):** Nhận message từ nhiều process, đóng gói thành segment, chuyển xuống network layer
> - **Demultiplexing (receiver):** Nhận segment từ network layer, mở gói, chuyển đến đúng process (socket)
> 
> → IP chỉ đảm bảo gói tin đến đúng **máy**, TCP/UDP đảm bảo đến đúng **ứng dụng** trên máy đó.

---

> [!question] C3-2. Multiplexing & Demultiplexing
> Multiplexing và demultiplexing khác nhau như thế nào? Cặp thông tin nào được dùng để demultiplex đúng socket?

> [!success]- 📌 Đáp án & Giải thích
> 
> **Multiplexing** (tại sender):
> - Thu thập message từ **nhiều socket** khác nhau
> - Đóng gói mỗi message thành segment, thêm **header** (có source port, dest port)
> - Chuyển xuống network layer
> 
> **Demultiplexing** (tại receiver):
> - Nhận segment từ network layer
> - Đọc **dest port** trong header
> - Chuyển message đến **đúng socket**
> 
> ---
> 
> **Thông tin dùng để demultiplex:**
> 
> | Giao thức | Thông tin định danh socket |
> |---|---|
> | **UDP** | Dest IP + **Dest port** (2-tuple) |
> | **TCP** | **Source IP + Source port + Dest IP + Dest port** (4-tuple) |
> 
> **Tại sao TCP cần 4-tuple?**
> - TCP là connection-oriented → mỗi kết nối = 1 socket riêng
> - Web server port 80 có thể có hàng nghìn socket đồng thời (mỗi client 1 socket)
> - Cần đủ 4 thông tin để phân biệt: request từ client A:5000 ≠ request từ client B:5000
> 
> **UDP đơn giản hơn:**
> - Connectionless → 1 port = 1 socket cho tất cả client
> - DNS server port 53 dùng 1 socket duy nhất phục vụ mọi client

---

> [!question] C3-3. Tại sao dùng UDP?
> UDP là giao thức "no frills". Tại sao nhiều ứng dụng vẫn chọn UDP thay vì TCP? Nêu 3 lý do cụ thể.

> [!success]- 📌 Đáp án & Giải thích
> 
> **UDP = "Unreliable Data Protocol"** — không đảm bảo delivery, thứ tự, hoặc toàn vẹn. Vậy tại sao dùng?
> 
> **1. Không cần thiết lập kết nối (No connection setup)**
> - TCP tốn **2 RTT** để handshake trước khi truyền dữ liệu
> - UDP gửi ngay lập tức → độ trễ thấp hơn
> - **Phù hợp:** DNS query (chỉ 1 request → 1 response, không cần handshake)
> 
> **2. Không lưu trạng thái (No connection state)**
> - TCP phải lưu buffer, seq#, window size, timer... → tốn RAM
> - UDP không lưu gì → server có thể phục vụ **nhiều client hơn** với cùng tài nguyên
> - **Phù hợp:** Game server (hàng nghìn player đồng thời)
> 
> **3. Header nhỏ (Small header)**
> - TCP header: **20 bytes**
> - UDP header: **8 bytes**
> - **Phù hợp:** VoIP (tiết kiệm băng thông)
> 
> **4. Không kiểm soát tắc nghẽn (No congestion control)**
> - TCP tự giảm tốc khi mạng tắc → delay không đồng đều
> - UDP gửi với tốc độ mong muốn → đều đặn hơn (nhưng có thể gây tắc nghẽn!)
> - **Phù hợp:** Streaming video trực tiếp (mất vài frame chấp nhận được, nhưng giật lag thì không)
> 
> ---
> 
> **Ứng dụng dùng UDP:**
> - DNS, DHCP, SNMP (query ngắn)
> - Streaming multimedia (chịu được mất mát)
> - Online gaming (delay thấp quan trọng hơn reliability)
> - **HTTP/3 (QUIC)** — xây dựng reliability ở tầng app, nhưng vẫn dùng UDP để tránh overhead TCP

---

> [!question] C3-4. UDP Checksum
> UDP checksum hoạt động như thế nào? Tại sao checksum không đảm bảo hoàn toàn phát hiện lỗi?

> [!success]- 📌 Đáp án & Giải thích
> 
> **Mục tiêu:** Phát hiện bit bị lật trong segment truyền.
> 
> **Cách tính (sender):**
> 1. Coi segment (header + pseudo header + data) là dãy số **16-bit**
> 2. Cộng tất cả theo **one's complement** (nếu tràn → wraparound carry)
> 3. Lấy **bù 1** của tổng → đặt vào trường checksum
> 
> **Kiểm tra (receiver):**
> 1. Cộng tất cả số 16-bit (bao gồm checksum)
> 2. Nếu kết quả = `1111 1111 1111 1111` → **không phát hiện lỗi**
> 3. Nếu khác → **phát hiện lỗi** → drop segment
> 
> ---
> 
> **Ví dụ tính checksum:**
> ```
> Word 1: 1110 0110 0110 0110
> Word 2: 1101 0101 0101 0101
> ──────────────────────────────
> Sum:  1 1011 1011 1011 1011  (có carry bit)
> Wraparound: 1011 1011 1011 1100
> Checksum: 0100 0100 0100 0011  (bù 1)
> ```
> 
> ---
> 
> **Tại sao không đảm bảo 100%?**
> 
> 1. **Lỗi chẵn (even errors):** Nếu 2 bit cùng vị trí lật (ví dụ: bit 5 của word 1 và word 2), tổng không đổi → không phát hiện ra
> 2. **Burst errors lớn:** Nhiều bit lỗi có thể triệt tiêu nhau trong phép cộng
> 3. **Collision:** Với 16-bit checksum, có $2^{16}$ giá trị → xác suất va chạm (2 segment khác nhau có cùng checksum) ≈ $1.5 \times 10^{-5}$
> 
> **Tuy nhiên:** Checksum vẫn phát hiện được **phần lớn** lỗi thực tế (> 99.99%), đủ cho UDP (ứng dụng tự lo phần còn lại nếu cần)

---

> [!question] C3-5. Sự tiến hóa của RDT
> Mô tả sự tiến hóa từ **rdt1.0** → **rdt3.0**. Mỗi phiên bản giải quyết vấn đề gì của phiên bản trước?

> [!success]- 📌 Đáp án & Giải thích
> 
> | Phiên bản | Giả định về kênh | Cơ chế thêm vào | Giải quyết vấn đề gì |
> |---|---|---|---|
> | **rdt1.0** | Kênh hoàn toàn tin cậy | (không có) | Baseline — quá đơn giản |
> | **rdt2.0** | Có **bit errors** | Checksum + ACK/NAK | Phát hiện & sửa lỗi bit |
> | **rdt2.1** | Bit errors + **ACK/NAK có thể bị lỗi** | Sequence number (0/1) | Phát hiện gói trùng lặp |
> | **rdt2.2** | (như 2.1) | Bỏ NAK, chỉ dùng ACK | Đơn giản hóa (NAK = ACK cũ) |
> | **rdt3.0** | Bit errors + **Packet loss** | Timer (timeout) | Xử lý mất gói/ACK |
> 
> ---
> 
> **Chi tiết từng bước:**
> 
> **rdt1.0:** Sender gửi, receiver nhận. Không có gì đặc biệt (giả định mạng hoàn hảo).
> 
> **rdt2.0:** Thêm **checksum** để phát hiện lỗi:
> - Receiver gửi **ACK** nếu OK, **NAK** nếu lỗi
> - Sender nhận NAK → **retransmit**
> - **Vấn đề:** Nếu ACK/NAK bị lỗi thì sao? Sender không biết có nên gửi lại không.
> 
> **rdt2.1:** Thêm **sequence number** (0 hoặc 1):
> - Mỗi gói có seq# → receiver biết gói mới hay gói trùng (retransmission)
> - Nếu receiver nhận gói trùng → gửi lại ACK (không chuyển lên app)
> - **Vấn đề giải quyết:** ACK bị lỗi không còn là vấn đề (sender gửi lại, receiver phát hiện duplicate)
> 
> **rdt2.2:** Bỏ NAK, chỉ dùng ACK:
> - Thay vì gửi NAK cho gói n, gửi **ACK cho gói n-1** (gói nhận đúng cuối cùng)
> - Sender thấy **duplicate ACK** → biết gói tiếp theo bị lỗi
> - **Lợi ích:** Đơn giản hóa, TCP dùng cơ chế này
> 
> **rdt3.0:** Thêm **timer** để xử lý **packet loss**:
> - Sender khởi động timer sau khi gửi gói
> - Nếu **timeout** (không nhận ACK) → retransmit
> - Xử lý 4 kịch bản: (a) không mất gói, (b) mất data, (c) mất ACK, (d) ACK trễ
> - **Giải pháp hoàn chỉnh** nhưng hiệu suất thấp (stop-and-wait)

---

> [!question] C3-6. Stop-and-Wait vs. Pipelining
> Tại sao **stop-and-wait** có hiệu suất thấp? **Go-Back-N** và **Selective Repeat** khắc phục điều đó như thế nào?

> [!success]- 📌 Đáp án & Giải thích
> 
> **Stop-and-Wait:** Sender gửi 1 gói → chờ ACK → gửi gói tiếp theo.
> 
> **Hiệu suất (utilization):**
> $$U_{\text{sender}} = \frac{d_{\text{trans}}}{d_{\text{trans}} + 2 \times d_{\text{prop}}}$$
> 
> **Ví dụ:** $d_{\text{trans}} = 0.008$ ms, $d_{\text{prop}} = 25$ ms (liên kết xa)
> $$U = \frac{0.008}{0.008 + 50} \approx 0.016\% \text{ (!)}$$
> 
> → Sender **nhàn rỗi > 99.9% thời gian**, chờ ACK!
> 
> ---
> 
> **Giải pháp: Pipelining** — gửi nhiều gói mà không cần đợi ACK từng gói.
> 
> **Go-Back-N (GBN):**
> - Sender có thể gửi tối đa $N$ gói chưa ACK (sliding window)
> - Receiver **chỉ nhận theo thứ tự**: gói out-of-order bị discard
> - Nếu gói $k$ bị mất → receiver loại bỏ tất cả gói $> k$, gửi **ACK $k-1$** (cumulative)
> - Sender timeout → **retransmit từ gói $k$ trở đi** (cả window)
> - **Nhược điểm:** Mất 1 gói → phải gửi lại cả đống gói sau đó (lãng phí)
> 
> **Selective Repeat (SR):**
> - Receiver **buffer các gói out-of-order**, chỉ yêu cầu gửi lại gói bị mất
> - Mỗi gói có **timer riêng**
> - Sender chỉ retransmit **gói bị mất** (không phải cả window)
> - **Phức tạp hơn** nhưng hiệu quả hơn GBN
> - TCP dùng **hybrid** của GBN + SR
> 
> ---
> 
> **So sánh:**
> | | Stop-and-Wait | Go-Back-N | Selective Repeat |
> |---|---|---|---|
> | Window size | 1 | N | N |
> | Receiver buffer | Không cần | Không cần | Cần |
> | Retransmit | 1 gói | Từ gói lỗi đến cuối window | Chỉ gói lỗi |
> | Hiệu suất | Thấp | Trung bình | Cao |

---

> [!question] C3-7. TCP 3-Way Handshake
> Mô tả **3-way handshake** của TCP. Tại sao cần đúng 3 bước, không phải 2?

> [!success]- 📌 Đáp án & Giải thích
> 
> **Ba bước thiết lập kết nối TCP:**
> 
> ```
> Client                          Server
>   │                               │
>   │  ① SYN (seq=x)               │
>   │─────────────────────────────>│
>   │                               │ Server chấp nhận, cấp phát tài nguyên
>   │                               │
>   │  ② SYN-ACK (seq=y, ack=x+1)  │
>   │<─────────────────────────────│
>   │                               │
>   │ Client cấp phát tài nguyên    │
>   │                               │
>   │  ③ ACK (seq=x+1, ack=y+1)    │
>   │─────────────────────────────>│
>   │                               │
>   │  [Kết nối thiết lập]         │
>   │  Data transfer...            │
> ```
> 
> **Giải thích từng bước:**
> 
> **① SYN (Synchronize):**
> - Client gửi segment có flag **SYN=1**, seq# ban đầu = $x$ (random)
> - "Tôi muốn kết nối, seq# của tôi bắt đầu từ $x$"
> 
> **② SYN-ACK:**
> - Server trả lời: "OK, tôi nhận được $x$, seq# của tôi bắt đầu từ $y$"
> - Flag **SYN=1, ACK=1**, ack# = $x+1$ (mong đợi byte tiếp theo từ client)
> 
> **③ ACK:**
> - Client xác nhận: "Tôi nhận được $y$, bắt đầu truyền dữ liệu"
> - Flag **ACK=1**, ack# = $y+1$
> 
> ---
> 
> **Tại sao cần 3 bước, không phải 2?**
> 
> **Vấn đề với 2-way handshake:**
> Giả sử chỉ có SYN và SYN-ACK:
> 
> ```
> Kịch bản tấn công:
> 1. Client gửi SYN (seq=x)
> 2. Segment này bị delay lâu trên mạng
> 3. Client gửi SYN mới (seq=x'), server trả SYN-ACK, kết nối bình thường
> 4. SYN cũ (seq=x) cuối cùng đến server
> 5. Server tưởng là request mới → mở kết nối thứ 2 (!)
> 6. Client không bao giờ gửi data → server giữ tài nguyên vô ích
> ```
> 
> **Bước 3 (ACK) giải quyết:**
> - Server chờ ACK cuối cùng từ client trước khi coi kết nối là ESTABLISHED
> - Client cũ không gửi ACK cho SYN-ACK của kết nối zombie → server timeout và đóng
> - **Đồng bộ 2 chiều:** cả hai đều xác nhận seq# của nhau

---

> [!question] C3-8. TCP Timeout Estimation
> TCP ước tính timeout như thế nào? Giải thích ý nghĩa của **EstimatedRTT**, **DevRTT**, và công thức timeout.

> [!success]- 📌 Đáp án & Giải thích
> 
> **Vấn đề:** Timeout quá ngắn → retransmit không cần thiết; quá dài → phản ứng chậm với packet loss.
> 
> **Giải pháp:** Ước tính **động** dựa trên RTT đo được.
> 
> ---
> 
> **① EstimatedRTT** — trung bình trơn mũ (EWMA):
> 
> $$\text{EstimatedRTT} = (1-\alpha) \cdot \text{EstimatedRTT} + \alpha \cdot \text{SampleRTT}$$
> 
> - $\alpha = 0.125$ (điển hình)
> - **SampleRTT:** RTT đo được từ 1 segment (thời gian gửi → nhận ACK)
> - **Ý nghĩa:** Lấy trung bình có trọng số, mẫu mới chiếm 12.5%, mẫu cũ giữ lại 87.5% → **mượt, không nhạy với spike**
> 
> ---
> 
> **② DevRTT** — độ lệch chuẩn (variance):
> 
> $$\text{DevRTT} = (1-\beta) \cdot \text{DevRTT} + \beta \cdot |\text{SampleRTT} - \text{EstimatedRTT}|$$
> 
> - $\beta = 0.25$ (điển hình)
> - **Ý nghĩa:** Đo **sự biến động** của RTT — nếu mạng không ổn định, DevRTT lớn
> 
> ---
> 
> **③ TimeoutInterval:**
> 
> $$\text{TimeoutInterval} = \text{EstimatedRTT} + 4 \cdot \text{DevRTT}$$
> 
> - **Tại sao + 4×DevRTT?** Cho "buffer" an toàn — nếu RTT dao động nhiều, timeout cần dài hơn
> - Công thức này từ **Jacobson's algorithm** (1988), giảm retransmit không cần thiết từ 30% xuống 3%
> 
> ---
> 
> **Ví dụ:**
> ```
> SampleRTT = 100 ms
> EstimatedRTT = 90 ms
> DevRTT = 5 ms
> 
> → EstimatedRTT_new = 0.875×90 + 0.125×100 = 91.25 ms
> → DevRTT_new = 0.75×5 + 0.25×|100-90| = 6.25 ms
> → Timeout = 91.25 + 4×6.25 = 116.25 ms
> ```

---

> [!question] C3-9. Flow Control vs. Congestion Control
> Giải thích **flow control** trong TCP. `rwnd` và `cwnd` khác nhau như thế nào về nguồn gốc và mục đích?

> [!success]- 📌 Đáp án & Giải thích
> 
> | | Flow Control (`rwnd`) | Congestion Control (`cwnd`) |
> |---|---|---|
> | **Mục đích** | Bảo vệ **receiver** khỏi bị tràn buffer | Bảo vệ **mạng** khỏi tắc nghẽn |
> | **Nguồn gốc** | Receiver thông báo cho sender | Sender tự điều chỉnh dựa trên loss/delay |
> | **Trường trong TCP** | **Receive Window** (header) | Không có trường (tính toán nội bộ) |
> | **Giá trị** | Số byte còn trống trong buffer receiver | Số byte sender được gửi mỗi RTT |
> 
> ---
> 
> **Flow Control (rwnd):**
> 
> ```
> Receiver buffer: [========        ] ← 40% đầy
>                   ↑ 60% còn trống = rwnd
> 
> Receiver gửi trong header: rwnd = 6000 bytes
> Sender đảm bảo: LastByteSent - LastByteAcked ≤ rwnd
> ```
> 
> **Nếu rwnd = 0:** Sender **dừng gửi** (trừ 1-byte probe để kiểm tra khi nào buffer trống)
> 
> ---
> 
> **Congestion Control (cwnd):**
> 
> Sender tự điều chỉnh `cwnd` dựa trên tình trạng mạng:
> - **Slow Start:** cwnd tăng mũ (×2 mỗi RTT)
> - **Congestion Avoidance:** cwnd tăng tuyến tính (+1 MSS mỗi RTT)
> - **Fast Recovery:** cwnd cắt giảm khi phát hiện loss (3 dup ACKs → cwnd/2)
> 
> ---
> 
> **Kết hợp cả hai:**
> 
> $$\text{Effective window} = \min(\text{rwnd}, \text{cwnd})$$
> 
> Sender tuân theo **giá trị nhỏ hơn** — bảo vệ cả receiver lẫn mạng.

---

> [!question] C3-10. AIMD
> Mô tả thuật toán **AIMD** (Additive Increase Multiplicative Decrease). Phân biệt phản ứng của TCP Reno khi gặp **3 duplicate ACKs** vs. **timeout**.

> [!success]- 📌 Đáp án & Giải thích
> 
> **AIMD** = thuật toán cốt lõi của TCP congestion control.
> 
> **Additive Increase (Tăng cộng):**
> - Mỗi RTT không có loss → $\text{cwnd} = \text{cwnd} + 1 \text{ MSS}$
> - Tăng **tuyến tính** → thăm dò băng thông có sẵn một cách thận trọng
> 
> **Multiplicative Decrease (Giảm nhân):**
> - Phát hiện loss → $\text{cwnd} = \text{cwnd} / 2$
> - Giảm **mũ** → phản ứng nhanh với tắc nghẽn
> 
> ---
> 
> **Đồ thị dạng "răng cưa" (sawtooth):**
> ```
> cwnd
>   │     ╱╲      ╱╲      ╱╲
>   │    ╱  ╲    ╱  ╲    ╱  ╲
>   │   ╱    ╲  ╱    ╲  ╱    ╲
>   │  ╱      ╲╱      ╲╱      ╲
>   └─────────────────────────────► time
>       loss    loss    loss
> ```
> 
> ---
> 
> **TCP Reno: Phân biệt 2 loại loss**
> 
> | Tín hiệu loss | Mức độ nghiêm trọng | Phản ứng TCP Reno |
> |---|---|---|
> | **3 duplicate ACKs** | Mất gói nhẹ (mạng vẫn hoạt động) | **Fast Recovery:** cwnd → cwnd/2, ssthresh → cwnd/2 |
> | **Timeout** | Mất gói nặng (mạng tắc nghẽn nghiêm trọng) | **Slow Start:** cwnd → 1 MSS, ssthresh → cwnd/2 |
> 
> **Lý do phân biệt:**
> - **3 dup ACKs** có nghĩa receiver vẫn nhận được gói (chỉ thiếu 1 gói) → mạng chưa sập hoàn toàn → giảm nhẹ (cwnd/2)
> - **Timeout** có nghĩa không có ACK nào → mạng có thể sập hoặc tắc nghẽn nặng → reset về đầu (cwnd=1)
> 
> ---
> 
> **TCP Tahoe (cũ hơn):** Cả 2 trường hợp đều → cwnd = 1 MSS (không phân biệt)

---

> [!question] C3-11. Slow Start
> **Slow Start** hoạt động như thế nào? Khi nào TCP chuyển từ Slow Start sang Congestion Avoidance?

> [!success]- 📌 Đáp án & Giải thích
> 
> **Slow Start** = giai đoạn đầu của TCP connection (mặc dù tên là "slow" nhưng tăng rất nhanh!)
> 
> **Cách hoạt động:**
> 1. Bắt đầu: $\text{cwnd} = 1 \text{ MSS}$
> 2. Mỗi ACK nhận được → $\text{cwnd} = \text{cwnd} + 1 \text{ MSS}$
> 3. **Kết quả:** cwnd **tăng gấp đôi mỗi RTT** (tăng mũ)
> 
> ```
> RTT 1: cwnd = 1 MSS → gửi 1 segment → nhận 1 ACK → cwnd = 2
> RTT 2: cwnd = 2 MSS → gửi 2 segments → nhận 2 ACKs → cwnd = 4
> RTT 3: cwnd = 4 MSS → gửi 4 segments → nhận 4 ACKs → cwnd = 8
> RTT 4: cwnd = 8 MSS → ...
> ```
> 
> ---
> 
> **Khi nào chuyển sang Congestion Avoidance?**
> 
> Khi $\text{cwnd} \geq \text{ssthresh}$ (slow start threshold):
> 
> | Giai đoạn | Điều kiện | Tốc độ tăng cwnd |
> |---|---|---|
> | **Slow Start** | cwnd < ssthresh | **Mũ** (×2 mỗi RTT) |
> | **Congestion Avoidance** | cwnd ≥ ssthresh | **Tuyến tính** (+1 MSS mỗi RTT) |
> 
> **ssthresh ban đầu:** thường rất lớn (64 KB hoặc vô hạn)
> 
> **ssthresh sau loss:**
> - Khi phát hiện loss → $\text{ssthresh} = \text{cwnd} / 2$
> - Nếu timeout → cwnd = 1, bắt đầu lại Slow Start
> - Nếu 3 dup ACKs → cwnd = ssthresh (vào Congestion Avoidance ngay)
> 
> ---
> 
> **Tại sao cần Slow Start?**
> - Khi kết nối mới, sender **không biết** mạng có thể chịu bao nhiêu
> - Tăng mũ giúp nhanh chóng tìm ra **bandwidth khả dụng**
> - Khi đạt gần giới hạn (loss xảy ra) → chuyển sang tăng tuyến tính để "ổn định"

---

> [!question] C3-12. TCP CUBIC
> **TCP CUBIC** cải tiến TCP Reno ở điểm nào? Viết công thức cửa sổ của CUBIC.

> [!success]- 📌 Đáp án & Giải thích
> 
> **TCP CUBIC** = thuật toán congestion control mặc định trên **Linux** (từ kernel 2.6.19, 2007).
> 
> **Vấn đề của TCP Reno:**
> - AIMD tăng **quá chậm** trên mạng tốc độ cao và RTT lớn
> - Ví dụ: Liên kết 10 Gbps, RTT = 100 ms, cần hàng giờ để đạt full utilization sau loss!
> 
> ---
> 
> **CUBIC cải tiến:**
> 
> **Ý tưởng:** Tốc độ tăng cwnd phụ thuộc vào **thời gian** kể từ lần loss cuối, không phụ thuộc RTT.
> 
> **Công thức:**
> 
> $$W(t) = C \cdot (t - K)^3 + W_{\max}$$
> 
> - $W(t)$: window size tại thời điểm $t$
> - $W_{\max}$: window size khi xảy ra loss gần nhất
> - $K = \sqrt[3]{\frac{W_{\max} \cdot \beta}{C}}$ (thời điểm đạt lại $W_{\max}$)
> - $C = 0.4$ (hằng số scaling)
> - $\beta = 0.7$ (multiplicative decrease factor — nhẹ hơn Reno 0.5)
> 
> ---
> 
> **Đồ thị hình khối (cubic):**
> ```
> cwnd
>   │         ╱─────╲
>   │        ╱       ╲
>   │       ╱         ╲
>   │   ___╱           ╲___
>   │  ╱                   ╲
>   └─────────────────────────► time
>       loss    Wmax    loss
>          ↑     ↑
>        tăng   giảm
>        nhanh  chậm
> ```
> 
> **Hành vi:**
> 1. Sau loss, cwnd giảm xuống $W_{\max} \times \beta$ (0.7× thay vì 0.5×)
> 2. **Concave phase** (lõm): tăng **nhanh** để quay về $W_{\max}$ (thăm dò)
> 3. **Convex phase** (lồi): tăng **chậm** quanh $W_{\max}$ (thận trọng)
> 4. Vượt qua $W_{\max}$ → tăng nhanh lại để tìm bandwidth mới
> 
> ---
> 
> **So sánh:**
> | | TCP Reno (AIMD) | TCP CUBIC |
> |---|---|---|
> | Tăng cwnd | +1 MSS/RTT | Theo $(t-K)^3$ |
> | Phụ thuộc RTT | ✅ Có (RTT lớn → tăng chậm) | ❌ Không (RTT-independent) |
> | Giảm khi loss | 0.5× | 0.7× |
> | Phù hợp | Mạng RTT thấp | Mạng tốc độ cao, RTT lớn |
> | Fairness | Tốt với cùng RTT | Tốt với RTT khác nhau |

---

## 🟡 Phần B – Trắc nghiệm

> [!question] C3-T1. Port Number Length
> Port number có độ dài bao nhiêu bit?
> 
> A. 8 bit  
> B. **16 bit**  
> C. 32 bit  
> D. 64 bit

> [!success]- 📌 Đáp án & Giải thích
> **Đáp án: B – 16 bit**
> 
> Port number: **0 → 65535** ($2^{16} - 1$)
> 
> **Phân loại:**
> - **0–1023:** Well-known ports (HTTP=80, HTTPS=443, SSH=22, DNS=53...)
> - **1024–49151:** Registered ports (dành cho ứng dụng đăng ký với IANA)
> - **49152–65535:** Dynamic/private ports (ephemeral — OS cấp tự động cho client)

---

> [!question] C3-T2. UDP Demultiplexing
> UDP demultiplexing dựa trên:
> 
> A. Chỉ destination port  
> B. Source IP + source port  
> C. **Destination IP + destination port**  
> D. Tất cả 4-tuple

> [!success]- 📌 Đáp án & Giải thích
> **Đáp án: C – Dest IP + Dest port**
> 
> UDP **connectionless** → mỗi port tương ứng **1 socket** duy nhất phục vụ tất cả client.
> 
> **Ví dụ:** DNS server port 53:
> ```
> Client A:5000 → Server:53  ┐
> Client B:6000 → Server:53  ├─→ Cùng 1 socket
> Client C:7000 → Server:53  ┘
> ```
> 
> Server chỉ cần biết **dest port = 53** để chuyển đến đúng socket (không quan tâm source).
> 
> **Ngược lại, TCP cần 4-tuple** vì mỗi connection = 1 socket riêng.

---

> [!question] C3-T3. RDT Sequence Number
> Trong rdt2.1 (stop-and-wait), sequence number cần tối thiểu bao nhiêu bit?
> 
> A. 8 bit  
> B. 2 bit  
> C. 4 bit  
> D. **1 bit**

> [!success]- 📌 Đáp án & Giải thích
> **Đáp án: D – 1 bit (0 hoặc 1)**
> 
> Với stop-and-wait:
> - Sender chờ ACK trước khi gửi gói tiếp theo
> - Chỉ có **tối đa 2 gói** trong "pipeline": gói hiện tại (chưa ACK) và gói trước đó (đã ACK)
> - **1 bit** đủ để phân biệt: gói 0 ≠ gói 1
> 
> **Nếu có pipelining (Go-Back-N, SR):** cần nhiều bit hơn
> - Window size = N → cần $\lceil \log_2(N+1) \rceil$ bits
> - Ví dụ: N=7 → cần 3 bits (0–7)

---

> [!question] C3-T4. TCP Fast Recovery
> Khi TCP nhận được **3 duplicate ACKs** (TCP Reno), nó sẽ:
> 
> A. Đặt cwnd = 1 MSS  
> B. **Đặt cwnd = cwnd/2 và vào Congestion Avoidance**  
> C. Tăng gấp đôi cwnd  
> D. Đóng kết nối

> [!success]- 📌 Đáp án & Giải thích
> **Đáp án: B**
> 
> **Fast Retransmit + Fast Recovery:**
> 1. Nhận 3 dup ACKs → **retransmit ngay** gói bị mất (không đợi timeout)
> 2. $\text{ssthresh} = \text{cwnd} / 2$
> 3. $\text{cwnd} = \text{ssthresh} + 3 \text{ MSS}$
> 4. Vào **Congestion Avoidance** (không quay về Slow Start)
> 
> **Lý do:** 3 dup ACKs chứng tỏ mạng vẫn chuyển tiếp gói (chỉ thiếu 1 gói) → chưa tắc nghẽn nặng → giảm nhẹ thôi.

---

> [!question] C3-T5. TCP Throughput (AIMD)
> Throughput trung bình của TCP với window size max $W$ và RTT là:
> 
> A. $W / RTT$  
> B. **$\dfrac{3W}{4 \cdot RTT}$**  
> C. $W / (2 \cdot RTT)$  
> D. $2W / RTT$

> [!success]- 📌 Đáp án & Giải thích
> **Đáp án: B**
> 
> Với AIMD, window dao động từ $W/2$ đến $W$ (dạng răng cưa).
> 
> **Throughput trung bình:**
> $$\text{Throughput} = \frac{\text{Avg window}}{RTT} = \frac{(W/2 + W)/2}{RTT} = \frac{3W/4}{RTT} = \frac{3W}{4 \cdot RTT}$$
> 
> **Công thức đầy đủ với loss rate $p$:**
> $$\text{Throughput} \approx \frac{1.22 \cdot MSS}{RTT \cdot \sqrt{p}}$$
> 
> → TCP throughput **giảm khi RTT tăng** hoặc **loss rate tăng**

---

> [!question] C3-T6. UDP Applications
> Ứng dụng nào SAU ĐÂY dùng UDP thay vì TCP?
> 
> A. File download (FTP)  
> B. Email (SMTP)  
> C. **DNS query**  
> D. Web page (HTTP/1.1)

> [!success]- 📌 Đáp án & Giải thích
> **Đáp án: C – DNS**
> 
> DNS dùng **UDP port 53** vì:
> - Query ngắn (< 512 bytes thường) → 1 request, 1 response
> - Không cần handshake (tiết kiệm 2 RTT)
> - Nếu không nhận response → client tự gửi lại (reliability ở tầng app)
> 
> **Ngoại lệ:** DNS query lớn (> 512 bytes, ví dụ DNSSEC) có thể dùng TCP.
> 
> **Các ứng dụng khác:**
> - FTP, SMTP, HTTP/1.1 đều dùng TCP (cần reliability)

---

## 🔴 Phần C – Bài tập tính toán

> [!question] C3-BT1. Stop-and-Wait Utilization
> Hai host cách nhau $d = 15000$ km, tốc độ $R = 1$ Gbps, gói tin $L = 1000$ bytes, $s = 3 \times 10^8$ m/s.
> 
> a) Tính $d_{\text{prop}}$ (một chiều).  
> b) Tính $d_{\text{trans}}$.  
> c) Tính hiệu suất $U_{\text{sender}}$ của stop-and-wait.

> [!success]- 📌 Đáp án & Giải thích
> 
> **a) Propagation delay:**
> $$d_{\text{prop}} = \frac{d}{s} = \frac{15 \times 10^6 \text{ m}}{3 \times 10^8 \text{ m/s}} = 0.05 \text{ s} = \mathbf{50 \text{ ms}}$$
> 
> ---
> 
> **b) Transmission delay:**
> $$d_{\text{trans}} = \frac{L}{R} = \frac{1000 \times 8 \text{ bits}}{10^9 \text{ bps}} = 8 \times 10^{-6} \text{ s} = \mathbf{0.008 \text{ ms}}$$
> 
> ---
> 
> **c) Utilization:**
> 
> Với stop-and-wait, sender gửi 1 gói → chờ ACK (RTT = $2 \times d_{\text{prop}}$) → gửi tiếp.
> 
> $$U = \frac{d_{\text{trans}}}{d_{\text{trans}} + 2 \cdot d_{\text{prop}}} = \frac{0.008}{0.008 + 100} = \frac{0.008}{100.008} \approx \mathbf{0.00008 = 0.008\%}$$
> 
> **Kết luận:** Sender chỉ làm việc **0.008% thời gian**, 99.992% thời gian đang chờ ACK! Đây là lý do vì sao cần **pipelining**.
> 
> ---
> 
> **Nếu có pipelining với window = N packets:**
> $$U \approx \min\left(1, \frac{N \cdot d_{\text{trans}}}{RTT}\right)$$
> 
> Để đạt 100% utilization, cần:
> $$N \geq \frac{RTT}{d_{\text{trans}}} = \frac{100}{0.008} = 12500 \text{ gói}$$

---

> [!question] C3-BT2. UDP Checksum
> Tính checksum UDP cho hai word 16-bit:
> - Word 1: `1010 0101 1010 0101`  
> - Word 2: `0110 0111 0000 1101`

> [!success]- 📌 Đáp án & Giải thích
> 
> **Bước 1: Cộng hai word**
> ```
>   1010 0101 1010 0101
> + 0110 0111 0000 1101
> ───────────────────────
> = 0001 0000 1011 0010  (có carry bit ở đầu)
> ```
> 
> **Bước 2: Wraparound carry**
> ```
> Carry:                1
> Sum:   0001 0000 1011 0010
>      + ───────────────────1
> ───────────────────────────
>      = 0001 0000 1011 0011
> ```
> 
> **Bước 3: One's complement (bù 1)**
> ```
> Sum:      0001 0000 1011 0011
> Checksum: 1110 1111 0100 1100  (đảo tất cả bit)
> ```
> 
> **Kết quả:** Checksum = **`1110 1111 0100 1100`**
> 
> ---
> 
> **Kiểm tra (receiver):**
> ```
>   1010 0101 1010 0101  (word 1)
> + 0110 0111 0000 1101  (word 2)
> + 1110 1111 0100 1100  (checksum)
> ───────────────────────
> = 1111 1111 1111 1111  ✅ Tất cả bit = 1 → không phát hiện lỗi
> ```

---

> [!question] C3-BT3. TCP Sequence & ACK
> TCP sender gửi 3 segment liên tiếp, mỗi segment 500 bytes, bắt đầu từ seq# = 0.
> 
> a) Seq# của 3 segment là bao nhiêu?  
> b) Sau khi nhận segment 1 và 2 thành công, receiver gửi ACK bao nhiêu?  
> c) Nếu segment 2 bị mất, receiver gửi ACK bao nhiêu?

> [!success]- 📌 Đáp án & Giải thích
> 
> **a) Sequence numbers:**
> - Segment 1: seq# = **0** (byte 0–499)
> - Segment 2: seq# = **500** (byte 500–999)
> - Segment 3: seq# = **1000** (byte 1000–1499)
> 
> *(TCP seq# là số byte đầu tiên trong segment, không phải số segment)*
> 
> ---
> 
> **b) Nhận segment 1 + 2 thành công:**
> 
> Receiver gửi **ACK = 1000** (cumulative ACK)
> 
> Ý nghĩa: "Tôi đã nhận đủ byte 0–999, mong đợi byte 1000 tiếp theo"
> 
> ---
> 
> **c) Segment 2 bị mất:**
> 
> ```
> Nhận segment 1 (seq=0) → OK → ACK 500
> Segment 2 (seq=500) bị mất
> Nhận segment 3 (seq=1000) → out-of-order → buffer
>                           → gửi lại ACK 500 (duplicate ACK)
> ```
> 
> Receiver gửi **ACK = 500** (vẫn mong đợi byte 500)
> 
> Nếu sender nhận **3 duplicate ACK 500** → Fast Retransmit (gửi lại segment 2 ngay, không đợi timeout)

---

> [!question] C3-BT4. TCP Slow Start Trace
> TCP bắt đầu với `cwnd = 1 MSS`, `ssthresh = 8 MSS`. Không có mất gói.
> 
> Mô tả giá trị `cwnd` qua các RTT: 1, 2, 3, 4, 5, 6.

> [!success]- 📌 Đáp án & Giải thích
> 
> | RTT | cwnd (MSS) | Giai đoạn | Giải thích |
> |-----|------------|-----------|------------|
> | 1 | **1** | Slow Start | Bắt đầu |
> | 2 | **2** | Slow Start | Nhận 1 ACK → cwnd = 1+1 = 2 |
> | 3 | **4** | Slow Start | Nhận 2 ACKs → cwnd = 2+2 = 4 |
> | 4 | **8** | Slow Start → CA | Nhận 4 ACKs → cwnd = 4+4 = 8 (đạt ssthresh) |
> | 5 | **9** | Congestion Avoidance | cwnd ≥ ssthresh → tăng +1 MSS/RTT |
> | 6 | **10** | Congestion Avoidance | Tiếp tục +1 MSS/RTT |
> 
> **Lưu ý:** Tại RTT 4, cwnd vừa đạt ssthresh → một số implementation chuyển sang CA ngay, số khác chuyển từ RTT 5. Ở đây dùng quy ước: đạt ssthresh → chuyển sang CA từ RTT tiếp theo.

---

> [!question] C3-BT5. TCP AIMD Throughput
> TCP có RTT = 100 ms, packet loss rate $p = 0.001$, MSS = 1460 bytes.
> 
> Ước tính throughput theo công thức:
> $$\text{Throughput} \approx \frac{1.22 \cdot MSS}{RTT \cdot \sqrt{p}}$$

> [!success]- 📌 Đáp án & Giải thích
> 
> Thay số:
> $$\text{Throughput} \approx \frac{1.22 \times 1460}{0.1 \times \sqrt{0.001}}$$
> 
> $$= \frac{1781.2}{0.1 \times 0.03162}$$
> 
> $$= \frac{1781.2}{0.003162}$$
> 
> $$\approx 563{,}000 \text{ bytes/s}$$
> 
> $$= 563 \text{ KB/s} \approx \mathbf{4.5 \text{ Mbps}}$$
> 
> ---
> 
> **Nhận xét:**
> 
> **1. Tác động của loss rate:**
> - $p = 0.001$ (0.1% loss) → throughput ≈ 4.5 Mbps
> - $p = 0.0001$ (0.01% loss) → throughput ≈ 14.2 Mbps (tăng $\sqrt{10} \approx 3.16×$)
> 
> **2. Tác động của RTT:**
> - RTT = 100 ms → 4.5 Mbps
> - RTT = 10 ms → 45 Mbps (tăng 10×)
> 
> → TCP throughput rất nhạy cảm với **RTT** và **loss rate**.

---

## 📊 Bảng tổng hợp

**So sánh TCP vs. UDP:**

| Tiêu chí | TCP | UDP |
|---|---|---|
| **Kết nối** | Connection-oriented (3-way handshake) | Connectionless |
| **Độ tin cậy** | Reliable, in-order delivery | Best-effort (unreliable) |
| **Flow control** | ✅ (rwnd) | ❌ |
| **Congestion control** | ✅ (cwnd, AIMD/CUBIC) | ❌ |
| **Header size** | 20 bytes (minimum) | 8 bytes |
| **Overhead** | Cao (handshake, ACK, retransmit) | Thấp |
| **Tốc độ** | Chậm hơn (do các cơ chế trên) | Nhanh hơn |
| **Ứng dụng** | HTTP, SMTP, FTP, SSH | DNS, DHCP, streaming, HTTP/3 |

---

**So sánh Go-Back-N vs. Selective Repeat:**

| | Go-Back-N | Selective Repeat |
|---|---|---|
| **Receiver buffer** | Không cần (chỉ nhận theo thứ tự) | Cần (buffer out-of-order) |
| **ACK** | Cumulative (ACK n → nhận đủ đến n) | Individual (ACK từng gói) |
| **Retransmit** | Từ gói lỗi đến cuối window | Chỉ gói lỗi |
| **Hiệu quả** | Trung bình | Cao (ít retransmit hơn) |
| **Phức tạp** | Thấp | Cao |
| **Window size** | Sender $\leq 2^m - 1$, Receiver = 1 | Cả hai $\leq 2^{m-1}$ |

---

*Xem thêm: [[C1 – Câu hỏi ôn tập]] · [[C2 – Câu hỏi ôn tập]]*
