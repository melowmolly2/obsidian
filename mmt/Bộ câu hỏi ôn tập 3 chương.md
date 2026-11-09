---
tags:
  - mmt/ôn-tập
  - mmt/câu-hỏi
---

up:: [[Mạng máy tính MOC]]

# 📝 Bộ câu hỏi ôn tập – Chương 1, 2, 3

> Dựa trên giáo trình *Computer Networking: A Top-Down Approach* – Kurose & Ross, 8th ed.

---

## 🌐 CHƯƠNG 1 – Computer Networks & the Internet

### Phần A – Câu hỏi lý thuyết (tự luận ngắn)

**C1-1.** Internet có thể được nhìn nhận theo hai góc độ. Hãy giải thích hai góc nhìn đó và phân biệt chúng.

> 💡 **Gợi ý:** "nuts & bolts" vs. "services" — xem [[1.1 Internet là gì, giao thức là gì]]

---

**C1-2.** RFC và IETF là gì? Chúng đóng vai trò gì trong hệ sinh thái Internet?

---

**C1-3.** Liệt kê và giải thích 4 thành phần gây ra *packet delay* tại một nút mạng. Viết công thức tổng quát.

$$d_{\text{nodal}} = \; ?$$

> 💡 Xem [[1.4 Performance]]

---

**C1-4.** Phân biệt **transmission delay** và **propagation delay**. Cho ví dụ minh họa bằng số.

---

**C1-5.** Giải thích khái niệm **traffic intensity** ($La/R$). Điều gì xảy ra khi $La/R \to 1$?

---

**C1-6.** So sánh **packet switching** và **circuit switching** theo 3 tiêu chí: hiệu quả sử dụng tài nguyên, tính phù hợp với traffic bursty, và đảm bảo chất lượng dịch vụ.

> 💡 Xem [[1.3 The Network Core]]

---

**C1-7.** Trong mô hình phân tầng Internet 5 tầng, mỗi tầng đảm nhiệm vai trò gì? Kể tên giao thức tiêu biểu ở mỗi tầng.

> 💡 Xem [[1.5 Protocol layers and Their Service Models]]

---

**C1-8.** **Encapsulation** là gì? Hãy mô tả quá trình đóng gói dữ liệu từ tầng Application xuống tầng Link.

---

**C1-9.** Mô tả 3 kiểu tấn công mạng phổ biến: **packet sniffing**, **IP spoofing**, và **DoS/DDoS**. Phân biệt DoS và DDoS.

> 💡 Xem [[1.6 Network Security]]

---

**C1-10.** Tại sao Internet ban đầu không được thiết kế với bảo mật? Điều này dẫn đến hậu quả gì ngày nay?

---

### Phần B – Trắc nghiệm

**C1-T1.** Thiết bị nào dưới đây là **packet switch**?
- A. Máy tính xách tay  
- B. Router  
- C. Cáp quang  
- D. Modem DSL  

<details><summary>📌 Đáp án</summary>B – Router</details>

---

**C1-T2.** Trong packet switching, router áp dụng nguyên tắc nào trước khi truyền gói tin ra liên kết tiếp theo?
- A. Cut-through switching  
- B. Store-and-forward  
- C. Circuit reservation  
- D. Token passing  

<details><summary>📌 Đáp án</summary>B – Store-and-forward</details>

---

**C1-T3.** Khi $La/R = 1$, queueing delay sẽ:
- A. Bằng 0  
- B. Tăng tuyến tính  
- C. Tiến tới vô cực  
- D. Giảm về 0  

<details><summary>📌 Đáp án</summary>C – Tiến tới vô cực</details>

---

**C1-T4.** Throughput **end-to-end** của một đường truyền qua nhiều liên kết được xác định bởi:
- A. Tổng băng thông các liên kết  
- B. Liên kết có băng thông lớn nhất  
- C. **Bottleneck link** – liên kết có băng thông nhỏ nhất  
- D. Băng thông trung bình  

<details><summary>📌 Đáp án</summary>C – Bottleneck link</details>

---

**C1-T5.** Công cụ nào thường dùng để thực hiện packet sniffing?
- A. Ping  
- B. Traceroute  
- C. Wireshark  
- D. Nmap  

<details><summary>📌 Đáp án</summary>C – Wireshark</details>

---

### Phần C – Bài tập tính toán

**C1-BT1 – Transmission delay đơn giản**

Một file $F = 8 \times 10^6$ bit được gửi qua liên kết tốc độ $R = 1$ Mbps.

a) Tính $d_{\text{trans}}$.  
b) Nếu $R = 100$ Mbps thì $d_{\text{trans}}$ bằng bao nhiêu?

<details><summary>📌 Đáp án</summary>

a) $d_{\text{trans}} = \dfrac{8 \times 10^6}{10^6} = 8$ giây

b) $d_{\text{trans}} = \dfrac{8 \times 10^6}{10^8} = 0.08$ giây = 80 ms

</details>

---

**C1-BT2 – Store-and-forward với 2 router**

Một gói tin $L = 10$ Kbits đi qua 3 liên kết (2 router ở giữa), mỗi liên kết tốc độ $R = 10$ Mbps. Bỏ qua delay khác.

Tính tổng thời gian từ nguồn đến đích.

<details><summary>📌 Đáp án</summary>

Với store-and-forward qua $N$ liên kết:
$$d_{\text{end-to-end}} = N \times \frac{L}{R} = 3 \times \frac{10 \times 10^3}{10 \times 10^6} = 3 \times 10^{-3} \text{ s} = 3 \text{ ms}$$

</details>

---

**C1-BT3 – Propagation delay**

Một liên kết dài $d = 5000$ km mang gói tin 10 Kbits, tốc độ $R = 1$ Gbps. Tốc độ lan truyền $s = 2 \times 10^8$ m/s.

a) Tính $d_{\text{prop}}$.  
b) Tính $d_{\text{trans}}$.  
c) Thành phần nào lớn hơn? Rút ra nhận xét.

<details><summary>📌 Đáp án</summary>

a) $d_{\text{prop}} = \dfrac{5 \times 10^6}{2 \times 10^8} = 0.025$ s = 25 ms

b) $d_{\text{trans}} = \dfrac{10 \times 10^3}{10^9} = 10^{-5}$ s = 0.01 ms

c) $d_{\text{prop}} \gg d_{\text{trans}}$ → với liên kết tốc độ cao và đường dài, propagation delay chiếm ưu thế.

</details>

---

**C1-BT4 – Packet switching vs. Circuit switching**

Một liên kết 1 Mbps, mỗi user dùng 100 Kbps khi active, xác suất active = 10%.

a) Với circuit switching, phục vụ tối đa bao nhiêu user?  
b) Tính xác suất để có nhiều hơn 2 user active cùng lúc khi có 10 user dùng packet switching.

<details><summary>📌 Đáp án</summary>

a) $\dfrac{1 \text{ Mbps}}{100 \text{ Kbps}} = 10$ user

b) Với $n=10$, $p=0.1$, $X \sim \text{Binomial}(10, 0.1)$:
$$P(X > 2) = 1 - P(X=0) - P(X=1) - P(X=2)$$
$$= 1 - 0.9^{10} - 10 \cdot 0.1 \cdot 0.9^9 - 45 \cdot 0.01 \cdot 0.9^8 \approx 0.07$$

→ Chỉ 7% thời gian bị tắc nghẽn; packet switching hiệu quả hơn với traffic bursty.

</details>

---

## 🌐 CHƯƠNG 2 – Application Layer

### Phần A – Câu hỏi lý thuyết (tự luận ngắn)

**C2-1.** So sánh mô hình **client-server** và **peer-to-peer (P2P)**. Cho ví dụ ứng dụng tương ứng cho mỗi mô hình.

> 💡 Xem [[2.1 Principles of Network Applications]]

---

**C2-2.** **Socket** là gì? Tại sao socket được ví như "cái cửa" giữa process và mạng?

---

**C2-3.** HTTP là giao thức **stateless**. Điều đó có nghĩa là gì? Cookie ra đời để giải quyết vấn đề gì?

> 💡 Xem [[2.2 The Web and HTTP]]

---

**C2-4.** Giải thích sự khác biệt giữa **non-persistent HTTP** và **persistent HTTP**. Tính thời gian phản hồi của mỗi loại theo RTT.

---

**C2-5.** Liệt kê 4 HTTP method chính và mục đích của từng method.

---

**C2-6.** Tại sao DNS không tập trung vào một server duy nhất? Nêu ít nhất 3 lý do.

> 💡 Xem [[2.4 DNS]]

---

**C2-7.** Mô tả 3 loại DNS server trong kiến trúc phân cấp. Phân biệt **iterative query** và **recursive query**.

---

**C2-8.** DNS Resource Record (RR) có dạng `(Name, Value, Type, TTL)`. Giải thích ý nghĩa các trường **Type A**, **Type NS**, **Type CNAME**, **Type MX**.

---

**C2-9.** **DASH** (Dynamic Adaptive Streaming over HTTP) hoạt động như thế nào? Manifest file dùng để làm gì?

> 💡 Xem [[2.5 Video Streaming + CDNS]]

---

**C2-10.** CDN sử dụng hai chiến lược phân phối server. Hãy giải thích và so sánh **Enter Deep** và **Bring Home**.

---

### Phần B – Trắc nghiệm

**C2-T1.** HTTP sử dụng giao thức transport nào, và tại sao?
- A. UDP – vì nhanh hơn  
- B. TCP – vì cần truyền tin cậy  
- C. IP – vì là giao thức nền tảng  
- D. SMTP – vì là text-based  

<details><summary>📌 Đáp án</summary>B – TCP, port 80, vì web cần đảm bảo toàn vẹn dữ liệu.</details>

---

**C2-T2.** Với non-persistent HTTP, để tải 1 HTML + 5 ảnh (6 objects tổng), cần tối thiểu bao nhiêu RTT (bỏ qua transmission time)?
- A. 2  
- B. 6  
- C. 12  
- D. 7  

<details><summary>📌 Đáp án</summary>C – 12 RTT (mỗi object tốn 2 RTT: 1 thiết lập TCP + 1 GET)</details>

---

**C2-T3.** Loại DNS query nào đặt toàn bộ gánh nặng phân giải lên local DNS server?
- A. Iterative query  
- B. Recursive query  
- C. Authoritative query  
- D. Broadcast query  

<details><summary>📌 Đáp án</summary>B – Recursive query</details>

---

**C2-T4.** Trong SMTP, giao thức nào được dùng để **lấy** mail từ mail server về user agent?
- A. SMTP  
- B. HTTP  
- C. IMAP  
- D. FTP  

<details><summary>📌 Đáp án</summary>C – IMAP (hoặc POP3)</details>

---

**C2-T5.** Caching ở **web proxy** giúp ích cho người dùng theo cách nào?
- A. Mã hóa nội dung web  
- B. Giảm thời gian phản hồi và giảm lưu lượng ra Internet  
- C. Tăng tốc kết nối TCP  
- D. Phân giải DNS nhanh hơn  

<details><summary>📌 Đáp án</summary>B</details>

---

### Phần C – Bài tập tính toán

**C2-BT1 – RTT với non-persistent HTTP**

Một web page gồm 1 file HTML và 10 ảnh JPEG, mỗi object có transmission time là 0.5 RTT. RTT = 20 ms.

a) Tính tổng thời gian tải trang với non-persistent HTTP (không dùng parallel connections).  
b) Nếu dùng persistent HTTP?

<details><summary>📌 Đáp án</summary>

**a) Non-persistent:**
- Mỗi object = 2 RTT + 1 file trans time = 2×20 + 10 = 50 ms
- 11 objects × 50 ms = **550 ms**

**b) Persistent với pipelining:**
- 1 RTT thiết lập kết nối
- 1 RTT gửi request cho tất cả objects
- 11 × 0.5 RTT trans time = 5.5 RTT = 110 ms
- Tổng ≈ 40 + 110 + một vài RTT overhead ≈ **~170 ms** (cải thiện đáng kể)

</details>

---

**C2-BT2 – DNS caching và TTL**

Local DNS server cache TTL = 20 giây. Các query đến cùng domain `gaia.cs.umass.edu`:
- $t = 0$: query đầu tiên (cache rỗng)
- $t = 10$: query lần 2
- $t = 25$: query lần 3

Giả sử full iterative resolution mất 8 time units, kết quả được cache từ $t=0$.

Hỏi: Mỗi query mất bao nhiêu time units?

<details><summary>📌 Đáp án</summary>

- $t=0$: Cache rỗng → **8 units** (full resolution)
- $t=10$: Cache còn hiệu lực (TTL chưa hết, $10 < 20$) → **2 units** (local server phục vụ trực tiếp)
- $t=25$: Cache đã hết hạn ($25 > 20$) → **8 units** (full resolution lại)

</details>

---

**C2-BT3 – Web cache & conditional GET**

Một web cache nhận được request cho object có `Last-Modified: Mon, 1 Jan 2024`. Cache gửi conditional GET với `If-Modified-Since: Mon, 1 Jan 2024` đến origin server. Server trả về **304 Not Modified**.

a) Cache có gửi object đến client không? Từ đâu?  
b) HTTP status code nào thể hiện object **đã** thay đổi?

<details><summary>📌 Đáp án</summary>

a) Có, cache gửi bản đã lưu cho client (không tải lại từ server) → tiết kiệm băng thông.

b) **200 OK** kèm theo object mới.

</details>

---

## 🌐 CHƯƠNG 3 – Transport Layer

### Phần A – Câu hỏi lý thuyết (tự luận ngắn)

**C3-1.** Phân biệt **transport layer** và **network layer** về phạm vi cung cấp dịch vụ. Dùng ví dụ Ann–Bill để minh họa.

> 💡 Xem [[3.1 Giới thiệu về Transport Layer]]

---

**C3-2.** **Multiplexing** và **demultiplexing** khác nhau như thế nào? Cặp thông tin nào được dùng để demultiplex đúng socket?

> 💡 Xem [[3.2 Multiplexing, Demultiplexing]]

---

**C3-3.** UDP là giao thức "no frills". Tại sao nhiều ứng dụng vẫn chọn UDP thay vì TCP? Nêu 3 lý do cụ thể.

> 💡 Xem [[3.3 UDP]]

---

**C3-4.** UDP checksum hoạt động như thế nào? Tại sao checksum không đảm bảo hoàn toàn phát hiện lỗi?

---

**C3-5.** Mô tả sự tiến hóa từ **rdt1.0** → **rdt3.0**. Mỗi phiên bản giải quyết vấn đề gì của phiên bản trước?

> 💡 Xem [[3.4 RDT]]

---

**C3-6.** Tại sao **stop-and-wait** có hiệu suất thấp? **Go-Back-N** và **Selective Repeat** khắc phục điều đó như thế nào?

---

**C3-7.** Mô tả **3-way handshake** của TCP. Tại sao cần đúng 3 bước, không phải 2?

> 💡 Xem [[3.5 TCP]]

---

**C3-8.** TCP ước tính timeout như thế nào? Giải thích ý nghĩa của **EstimatedRTT**, **DevRTT**, và công thức:

$$\text{TimeoutInterval} = \text{EstimatedRTT} + 4 \cdot \text{DevRTT}$$

---

**C3-9.** Giải thích **flow control** trong TCP. `rwnd` và `cwnd` khác nhau như thế nào về nguồn gốc và mục đích?

---

**C3-10.** Mô tả thuật toán **AIMD** (Additive Increase Multiplicative Decrease). Phân biệt phản ứng của TCP Reno khi gặp **3 duplicate ACKs** vs. **timeout**.

> 💡 Xem [[3.7 TCP Congestion Control]]

---

**C3-11.** **Slow Start** hoạt động như thế nào? Khi nào TCP chuyển từ Slow Start sang Congestion Avoidance?

---

**C3-12.** **TCP CUBIC** cải tiến TCP Reno ở điểm nào? Viết công thức cửa sổ của CUBIC.

---

### Phần B – Trắc nghiệm

**C3-T1.** Port number có độ dài bao nhiêu bit?
- A. 8 bit  
- B. 16 bit  
- C. 32 bit  
- D. 64 bit  

<details><summary>📌 Đáp án</summary>B – 16 bit (0 đến 65535)</details>

---

**C3-T2.** UDP demultiplexing dựa trên:
- A. Chỉ destination port  
- B. Source IP + source port  
- C. **Destination IP + destination port**  
- D. Tất cả 4-tuple  

<details><summary>📌 Đáp án</summary>C – UDP chỉ cần dest IP + dest port để định hướng đến socket</details>

---

**C3-T3.** Trong rdt2.1, sequence number cần tối thiểu bao nhiêu bit?
- A. 8 bit  
- B. 2 bit  
- C. 4 bit  
- D. **1 bit** (0 hoặc 1)  

<details><summary>📌 Đáp án</summary>D – Chỉ cần 1 bit (0/1) vì stop-and-wait</details>

---

**C3-T4.** Khi TCP nhận được 3 ACK trùng lặp (TCP Reno), nó sẽ:
- A. Đặt cwnd = 1 MSS  
- B. Đặt cwnd = cwnd / 2 và không vào Slow Start  
- C. Tăng gấp đôi cwnd  
- D. Đóng kết nối  

<details><summary>📌 Đáp án</summary>B – Fast Retransmit + Fast Recovery: cwnd → cwnd/2, ssthresh = cwnd/2</details>

---

**C3-T5.** Throughput trung bình của TCP (AIMD) với window size $W$ và RTT là:

- A. $\dfrac{W}{RTT}$  
- B. $\dfrac{3W}{4 \cdot RTT}$  
- C. $\dfrac{W}{2 \cdot RTT}$  
- D. $\dfrac{2W}{RTT}$  

<details><summary>📌 Đáp án</summary>B – $\approx \dfrac{3}{4} \cdot \dfrac{W}{RTT}$</details>

---

**C3-T6.** Ứng dụng nào SAU ĐÂY dùng UDP thay vì TCP?
- A. File tải xuống (FTP)  
- B. Email (SMTP)  
- C. DNS query  
- D. Tải trang web (HTTP/1.1)  

<details><summary>📌 Đáp án</summary>C – DNS dùng UDP (port 53) vì query ngắn, không cần thiết lập kết nối</details>

---

### Phần C – Bài tập tính toán

**C3-BT1 – Hiệu suất Stop-and-Wait**

Hai host cách nhau $d = 15000$ km, tốc độ $R = 1$ Gbps, gói tin $L = 1000$ bytes. Tốc độ lan truyền $s = 3 \times 10^8$ m/s.

a) Tính $d_{\text{prop}}$ (một chiều).  
b) Tính $d_{\text{trans}}$.  
c) Tính hiệu suất $U_{\text{sender}}$ của stop-and-wait.

<details><summary>📌 Đáp án</summary>

a) $d_{\text{prop}} = \dfrac{15 \times 10^6}{3 \times 10^8} = 0.05$ s = 50 ms

b) $d_{\text{trans}} = \dfrac{8000}{10^9} = 8 \times 10^{-6}$ s = 0.008 ms

c) $$U = \frac{d_{\text{trans}}}{d_{\text{trans}} + 2 \cdot d_{\text{prop}}} = \frac{0.008}{0.008 + 100} \approx 0.008\%$$

→ Cực kỳ thấp! Lý do cần pipelining.

</details>

---

**C3-BT2 – UDP Checksum**

Tính checksum UDP cho hai word 16-bit:
- Word 1: `1010 0101 1010 0101`  
- Word 2: `0110 0111 0000 1101`

<details><summary>📌 Đáp án</summary>

Cộng:
```
  1010 0101 1010 0101
+ 0110 0111 0000 1101
= 0001 0000 1011 0010 (có carry)
+ carry bit → 0001 0000 1011 0011
```

Checksum = bù 1:
$$\overline{0001\;0000\;1011\;0011} = 1110\;1111\;0100\;1100$$

</details>

---

**C3-BT3 – TCP Sequence Number & ACK**

TCP sender gửi 3 segment liên tiếp, mỗi segment 500 bytes, bắt đầu từ seq# = 0.

a) Seq# của 3 segment lần lượt là bao nhiêu?  
b) Sau khi nhận segment 1 và 2 thành công, receiver gửi ACK bao nhiêu?  
c) Nếu segment 2 bị mất, receiver gửi ACK bao nhiêu?

<details><summary>📌 Đáp án</summary>

a) Seq# = **0**, **500**, **1000**

b) ACK = **1000** (cumulative: nhận đủ đến byte 999, mong đợi 1000)

c) ACK = **500** (chỉ nhận được segment 1; segment 2 mất → mong đợi byte 500 mãi)

</details>

---

**C3-BT4 – TCP Congestion Control: Slow Start + AIMD**

TCP bắt đầu với `cwnd = 1 MSS`, `ssthresh = 8 MSS`.

Mô tả giá trị của `cwnd` qua các RTT: RTT 1, 2, 3, 4, 5, 6. Giả sử không có mất gói.

<details><summary>📌 Đáp án</summary>

| RTT | cwnd | Ghi chú |
|-----|------|---------|
| 1 | 1 MSS | Slow Start |
| 2 | 2 MSS | Slow Start (×2) |
| 3 | 4 MSS | Slow Start (×2) |
| 4 | 8 MSS | Slow Start → đạt ssthresh |
| 5 | 9 MSS | Congestion Avoidance (+1/RTT) |
| 6 | 10 MSS | Congestion Avoidance |

</details>

---

**C3-BT5 – TCP AIMD & Throughput**

TCP có RTT = 100 ms, packet loss rate $p = 0.001$, MSS = 1460 bytes.

Ước tính throughput theo công thức AIMD:

$$\text{Throughput} \approx \frac{1.22 \cdot MSS}{RTT \cdot \sqrt{p}}$$

<details><summary>📌 Đáp án</summary>

$$\text{Throughput} \approx \frac{1.22 \times 1460}{0.1 \times \sqrt{0.001}} = \frac{1781.2}{0.1 \times 0.03162} \approx \frac{1781.2}{0.003162} \approx 563{,}000 \text{ B/s} \approx 4.5 \text{ Mbps}$$

</details>

---

## 📊 Bảng tổng hợp so sánh nhanh

| Tiêu chí | TCP | UDP |
|---|---|---|
| Kết nối | Connection-oriented (3-way handshake) | Connectionless |
| Độ tin cậy | Reliable, in-order | Best-effort |
| Flow control | ✅ (rwnd) | ❌ |
| Congestion control | ✅ (cwnd, AIMD) | ❌ |
| Header size | 20 bytes | 8 bytes |
| Ứng dụng | HTTP, SMTP, FTP | DNS, DHCP, streaming, HTTP/3 |

---

| Tầng | Tên | Đơn vị dữ liệu | Giao thức |
|---|---|---|---|
| 5 | Application | Message | HTTP, DNS, SMTP |
| 4 | Transport | Segment | TCP, UDP |
| 3 | Network | Datagram | IP, OSPF, BGP |
| 2 | Link | Frame | Ethernet, WiFi |
| 1 | Physical | Bit | — |

---

*Ghi chú: Dấu `<details>` hiển thị đáp án khi click trong một số viewer hỗ trợ HTML. Trong Obsidian, mở callout hoặc cuộn xuống để xem.*
