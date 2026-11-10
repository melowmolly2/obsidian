---
tags:
  - mmt/ôn-tập
  - mmt/câu-hỏi
  - mmt/chương-1
---

up:: [[Mạng máy tính MOC]]
next:: [[C2 – Câu hỏi ôn tập]]

# 📝 Chương 1 – Computer Networks & the Internet

> Dựa trên giáo trình *Computer Networking: A Top-Down Approach* – Kurose & Ross, 8th ed.
> Nguồn ghi chú: [[1.1 Internet là gì, giao thức là gì]] · [[1.2 The Network Edge]] · [[1.3 The Network Core]] · [[1.4 Performance]] · [[1.5 Protocol layers and Their Service Models]] · [[1.6 Network Security]]

---

## 🔵 Phần A – Lý thuyết (tự luận)

> [!question] C1-1. Hai góc nhìn về Internet
> Internet có thể được nhìn nhận theo hai góc độ. Hãy giải thích và phân biệt hai góc nhìn đó.

> [!success]- 📌 Đáp án & Giải thích
> 
> **Góc nhìn 1 – "Nuts & Bolts" (Thành phần cấu tạo):**
> Nhìn Internet như một tập hợp phần cứng và phần mềm cụ thể:
> - **Hosts (end systems):** hàng tỷ thiết bị chạy ứng dụng ở rìa mạng (laptop, điện thoại, máy chủ, tủ lạnh thông minh…)
> - **Packet switches:** chuyển tiếp các gói tin — gồm **router** (tầng mạng) và **link-layer switch** (tầng liên kết)
> - **Communication links:** cáp quang, đồng trục, sóng vô tuyến, vệ tinh — mỗi loại có **bandwidth** (băng thông) riêng
> - **Networks:** tập hợp thiết bị + router + liên kết do một tổ chức quản lý
> - **Internet = "network of networks":** các ISP kết nối với nhau theo cấu trúc phân cấp
> - **Chuẩn hóa:** do **IETF** quản lý, công bố qua tài liệu **RFC** (Request for Comments)
> 
> **Góc nhìn 2 – "Services" (Dịch vụ):**
> Nhìn Internet như hạ tầng cung cấp dịch vụ cho ứng dụng:
> - Internet là nền tảng cho Web, email, streaming, game online, mạng xã hội…
> - Cung cấp **programming interface (socket API)** để các ứng dụng phân tán giao tiếp
> - Giống như dịch vụ bưu chính: người dùng không cần biết thư đi đường nào, chỉ cần bỏ thư vào hộp
> 
> **Phân biệt:** Góc nhìn 1 hỏi "Internet làm bằng gì?", góc nhìn 2 hỏi "Internet làm được gì?"

---

> [!question] C1-2. RFC và IETF
> RFC và IETF là gì? Chúng đóng vai trò gì trong hệ sinh thái Internet?

> [!success]- 📌 Đáp án & Giải thích
> 
> - **IETF (Internet Engineering Task Force):** tổ chức phi lợi nhuận, mở, chịu trách nhiệm **phát triển và chuẩn hóa** các giao thức Internet. Bất kỳ ai cũng có thể tham gia đóng góp.
> - **RFC (Request for Comments):** tài liệu kỹ thuật chính thức do IETF công bố, mô tả chi tiết các giao thức, kiến trúc, và quy trình của Internet.
>   - Ví dụ: RFC 793 định nghĩa TCP, RFC 2616 định nghĩa HTTP/1.1, RFC 1034–1035 định nghĩa DNS
>   - Tên "Request for Comments" bắt nguồn từ thời ARPAnet — ban đầu chỉ là các bản thảo mời góp ý, nhưng nay đã trở thành **tiêu chuẩn bắt buộc**
> 
> **Ý nghĩa:** Nhờ IETF và RFC, các thiết bị từ nhiều nhà sản xuất khác nhau có thể giao tiếp với nhau một cách thống nhất — đây là nền tảng của tính liên vận hành (interoperability) của Internet.

---

> [!question] C1-3. Bốn thành phần gây Packet Delay
> Liệt kê và giải thích 4 thành phần gây ra packet delay tại một nút mạng. Viết công thức tổng quát.

> [!success]- 📌 Đáp án & Giải thích
> 
> $$d_{\text{nodal}} = d_{\text{proc}} + d_{\text{queue}} + d_{\text{trans}} + d_{\text{prop}}$$
> 
> | Ký hiệu | Tên | Giải thích | Độ lớn thường gặp |
> |---|---|---|---|
> | $d_{\text{proc}}$ | **Nodal processing delay** | Thời gian router kiểm tra lỗi bit và xác định liên kết ra | < vài microsecond |
> | $d_{\text{queue}}$ | **Queueing delay** | Thời gian gói tin chờ trong buffer để được truyền | 0 → vô cực (tùy tắc nghẽn) |
> | $d_{\text{trans}}$ | **Transmission delay** | Thời gian đẩy toàn bộ gói tin lên liên kết: $d_{\text{trans}} = L/R$ | ms với liên kết chậm |
> | $d_{\text{prop}}$ | **Propagation delay** | Thời gian tín hiệu lan truyền vật lý qua liên kết: $d_{\text{prop}} = d/s$ | ms → hàng chục ms |
> 
> **Lưu ý quan trọng:** $d_{\text{trans}}$ và $d_{\text{prop}}$ hoàn toàn độc lập:
> - $d_{\text{trans}}$ phụ thuộc **tốc độ liên kết** và **kích thước gói**
> - $d_{\text{prop}}$ phụ thuộc **chiều dài vật lý** của liên kết và **môi trường** truyền dẫn

---

> [!question] C1-4. Transmission Delay vs. Propagation Delay
> Phân biệt transmission delay và propagation delay. Cho ví dụ minh họa bằng số.

> [!success]- 📌 Đáp án & Giải thích
> 
> **Transmission delay** – thời gian để router đẩy hết tất cả bit của gói tin lên liên kết:
> $$d_{\text{trans}} = \frac{L}{R}$$
> - $L$ = kích thước gói (bits), $R$ = tốc độ liên kết (bps)
> - **Phụ thuộc vào router và liên kết**, không phụ thuộc khoảng cách
> 
> **Propagation delay** – thời gian tín hiệu điện/quang lan truyền vật lý từ điểm A đến điểm B:
> $$d_{\text{prop}} = \frac{d}{s}$$
> - $d$ = chiều dài liên kết (m), $s \approx 2 \times 10^8$ m/s (trong cáp quang/đồng)
> - **Phụ thuộc vào môi trường vật lý**, không liên quan đến kích thước gói
> 
> **Ví dụ so sánh:**
> Gói tin $L = 1000$ bytes = 8000 bits, liên kết $R = 1$ Gbps, dài $d = 5000$ km:
> $$d_{\text{trans}} = \frac{8000}{10^9} = 8 \times 10^{-6} \text{ s} = 0.008 \text{ ms}$$
> $$d_{\text{prop}} = \frac{5 \times 10^6}{2 \times 10^8} = 0.025 \text{ s} = 25 \text{ ms}$$
> → Trên liên kết tốc độ cao và đường dài, $d_{\text{prop}} \gg d_{\text{trans}}$

---

> [!question] C1-5. Traffic Intensity
> Giải thích khái niệm traffic intensity ($La/R$). Điều gì xảy ra khi $La/R \to 1$?

> [!success]- 📌 Đáp án & Giải thích
> 
> $$\text{Traffic Intensity} = \frac{La}{R}$$
> - $L$ = kích thước gói (bits)
> - $a$ = tốc độ đến trung bình (gói/giây)
> - $R$ = tốc độ liên kết (bps)
> - $La$ = tổng bit đến mỗi giây; $R$ = tổng bit có thể xử lý mỗi giây
> 
> **Ý nghĩa:**
> | Giá trị $La/R$ | Tình trạng |
> |---|---|
> | $\approx 0$ | Hàng đợi gần như trống, delay nhỏ |
> | $\to 1$ | Hàng đợi tích lũy nhanh, delay tăng **vô hạn** |
> | $> 1$ | Dữ liệu đến nhanh hơn xử lý → **mất gói (packet loss)** |
> 
> **Tại sao $La/R \to 1$ gây delay vô hạn?** Vì ngay cả khi tải trung bình = 99% capacity, những đợt bursty ngắn cũng đủ làm buffer tràn. Đây là lý do kỹ sư mạng **không bao giờ thiết kế mạng ở 100% utilization**.

---

> [!question] C1-6. Packet Switching vs. Circuit Switching
> So sánh packet switching và circuit switching theo 3 tiêu chí: hiệu quả tài nguyên, phù hợp traffic bursty, và đảm bảo QoS.

> [!success]- 📌 Đáp án & Giải thích
> 
> | Tiêu chí | Packet Switching | Circuit Switching |
> |---|---|---|
> | **Hiệu quả tài nguyên** | ✅ Cao — chia sẻ liên kết theo nhu cầu thực tế; không dùng thì nhường cho người khác | ❌ Thấp — dành riêng tài nguyên cố định ngay cả khi không có dữ liệu |
> | **Phù hợp traffic bursty** | ✅ Rất phù hợp — xử lý từng gói độc lập, tận dụng khoảng trống | ❌ Kém — dữ liệu bursty làm lãng phí kênh đặt sẵn |
> | **Đảm bảo QoS** | ❌ Không đảm bảo — có thể có delay và mất gói | ✅ Đảm bảo — bandwidth và delay cố định cho mỗi kết nối |
> 
> **Ví dụ minh họa:**
> - Liên kết 1 Mbps, mỗi user cần 100 Kbps khi active (10% thời gian)
> - Circuit switching: tối đa **10 user** đồng thời
> - Packet switching: có thể phục vụ **35 user** với xác suất > 2 user active < 0.04%
> 
> **Kết luận:** Internet dùng packet switching vì Web/email là traffic bursty. Mạng điện thoại truyền thống dùng circuit switching vì cần đảm bảo chất lượng giọng nói.

---

> [!question] C1-7. Internet Protocol Stack 5 tầng
> Trong mô hình phân tầng Internet 5 tầng, mỗi tầng đảm nhiệm vai trò gì? Kể tên giao thức tiêu biểu ở mỗi tầng.

> [!success]- 📌 Đáp án & Giải thích
> 
> | Tầng | Tên | Vai trò | Giao thức tiêu biểu | Đơn vị dữ liệu |
> |---|---|---|---|---|
> | 5 | **Application** | Hỗ trợ ứng dụng mạng của người dùng | HTTP, SMTP, IMAP, DNS, FTP | Message |
> | 4 | **Transport** | Truyền dữ liệu **giữa các process** (end-to-end) | TCP, UDP | Segment |
> | 3 | **Network** | Định tuyến **datagram** từ nguồn đến đích | IP, OSPF, BGP | Datagram |
> | 2 | **Link** | Truyền dữ liệu qua **một liên kết** (hop-by-hop) | Ethernet, WiFi (802.11), PPP | Frame |
> | 1 | **Physical** | Truyền **bit** qua môi trường vật lý | — (tín hiệu điện, quang, sóng) | Bit |
> 
> **Tại sao phân tầng?**  
> - Cấu trúc rõ ràng, dễ hiểu mối quan hệ giữa các thành phần  
> - **Modular hóa:** thay đổi một tầng không ảnh hưởng các tầng khác (ví dụ: đổi từ Ethernet sang WiFi không cần sửa TCP)

---

> [!question] C1-8. Encapsulation
> Encapsulation là gì? Mô tả quá trình đóng gói dữ liệu từ tầng Application xuống tầng Link.

> [!success]- 📌 Đáp án & Giải thích
> 
> **Encapsulation** là quá trình mỗi tầng **thêm header (và đôi khi trailer) riêng** vào dữ liệu nhận từ tầng trên, trước khi chuyển xuống tầng dưới.
> 
> **Hành trình của một HTTP request:**
> ```
> Application  →  [HTTP message]
> Transport    →  [TCP header | HTTP message]           ← segment
> Network      →  [IP header | TCP header | HTTP msg]   ← datagram
> Link         →  [ETH hdr | IP hdr | TCP hdr | msg | ETH trailer] ← frame
> Physical     →  Bit stream
> ```
> 
> **Tại router trung gian:**
> - Router chỉ xử lý đến tầng **Network** — đọc IP header, quyết định chuyển tiếp, đóng gói lại thành frame mới
> - Router **không** đọc TCP header hay HTTP content
> 
> **Ý nghĩa của encapsulation:** Các tầng giao tiếp theo kiểu "peer-to-peer" — tầng Transport phía gửi "nói chuyện" với tầng Transport phía nhận, dù về vật lý dữ liệu đi qua nhiều router trung gian.

---

> [!question] C1-9. Ba kiểu tấn công mạng phổ biến
> Mô tả packet sniffing, IP spoofing, và DoS/DDoS. Phân biệt DoS và DDoS.

> [!success]- 📌 Đáp án & Giải thích
> 
> **🕵️ Packet Sniffing (Nghe lén gói tin):**
> - Xảy ra trên mạng **broadcast** (Ethernet chung, WiFi)
> - Card mạng đặt ở chế độ **promiscuous** → đọc tất cả gói tin đi qua, kể cả không phải của mình
> - Nguy hiểm vì có thể thu thập được **mật khẩu, thông tin thẻ tín dụng** (nếu không mã hóa)
> - Công cụ: **Wireshark** (hợp pháp để debug), tcpdump
> - **Phòng chống:** Dùng HTTPS/TLS để mã hóa, VPN, tách mạng bằng switch (thay hub)
> 
> **🎭 IP Spoofing (Giả mạo địa chỉ IP):**
> - Kẻ tấn công tạo gói tin với **source IP giả mạo** (giả vờ là người khác)
> - Nạn nhân tưởng gói tin đến từ nguồn tin cậy
> - Thường kết hợp với các tấn công khác (DDoS reflection)
> - **Phòng chống:** Ingress filtering tại ISP — lọc gói tin có source IP không hợp lệ
> 
> **💥 DoS vs. DDoS:**
> | | DoS (Denial of Service) | DDoS (Distributed DoS) |
> |---|---|---|
> | Nguồn tấn công | **1 máy** | **Nhiều máy** (botnet) |
> | Mức độ | Yếu hơn | Mạnh hơn, khó chặn hơn |
> | Mục tiêu | Làm tài nguyên (server, link) quá tải | Như DoS nhưng quy mô lớn hơn nhiều |
> | Cách thực hiện | Gửi traffic giả đến mục tiêu | Chiếm nhiều máy (zombie), chỉ huy đồng loạt tấn công |

---

> [!question] C1-10. Tại sao Internet không có bảo mật từ đầu?
> Tại sao Internet ban đầu không được thiết kế với bảo mật? Hậu quả ngày nay là gì?

> [!success]- 📌 Đáp án & Giải thích
> 
> **Lý do lịch sử:**
> - Internet (ARPAnet) được thiết kế những năm 1960–70 với tư duy: **"một nhóm nhỏ người dùng tin tưởng nhau, kết nối vào mạng minh bạch"**
> - Mục tiêu ban đầu là kết nối các trường đại học và cơ quan nghiên cứu — không ai nghĩ đến kẻ tấn công
> - Ưu tiên là **khả năng kết nối và đơn giản**, không phải bảo mật
> 
> **Hậu quả ngày nay:**
> - Các giao thức nền tảng (IP, TCP, DNS, BGP) thiếu cơ chế xác thực và mã hóa tích hợp
> - Các nhà thiết kế giao thức phải **"chạy theo để vá lỗ hổng"** — thêm TLS vào HTTP, DNSSEC vào DNS, IPsec vào IP...
> - Bảo mật phải được cân nhắc **ở mọi tầng** thay vì chỉ một tầng tập trung
> - Chi phí bảo mật ngày nay rất cao vì phải retrofit (bổ sung sau) thay vì build-in từ đầu
> 
> **Bài học:** Bảo mật cần được thiết kế ngay từ đầu (security by design), không thể thêm vào sau.

---

## 🟡 Phần B – Trắc nghiệm

> [!question] C1-T1. Packet switch là gì?
> Thiết bị nào dưới đây là **packet switch**?
> 
> A. Máy tính xách tay  
> B. **Router**  
> C. Cáp quang  
> D. Modem DSL

> [!success]- 📌 Đáp án & Giải thích
> **Đáp án: B – Router**
> 
> - **Router** là packet switch hoạt động ở tầng **Network** — đọc địa chỉ IP và chuyển tiếp gói tin
> - **Link-layer switch** cũng là packet switch nhưng hoạt động ở tầng **Link** — đọc địa chỉ MAC
> - Máy tính là **end system (host)**, không phải switch
> - Cáp quang là **physical medium** (môi trường truyền dẫn)
> - Modem DSL là thiết bị truy cập, không chuyển tiếp gói tin trong lõi mạng

---

> [!question] C1-T2. Store-and-forward
> Trong packet switching, router áp dụng nguyên tắc nào trước khi truyền gói tin ra liên kết tiếp theo?
> 
> A. Cut-through switching  
> B. **Store-and-forward**  
> C. Circuit reservation  
> D. Token passing

> [!success]- 📌 Đáp án & Giải thích
> **Đáp án: B – Store-and-forward**
> 
> Router phải **nhận đầy đủ toàn bộ gói tin** vào buffer trước khi bắt đầu truyền sang liên kết tiếp theo. Lý do:
> - Cần kiểm tra header để biết đích đến
> - Cần kiểm tra lỗi (CRC checksum)
> 
> **Hệ quả:** Với $N$ liên kết, tổng delay = $N \times \dfrac{L}{R}$ (bỏ qua delay khác)
> 
> *(Cut-through switching là kỹ thuật của một số switch đặc biệt, truyền ngay khi đọc đủ header — không phải cơ chế chuẩn của router Internet)*

---

> [!question] C1-T3. Traffic Intensity → Delay
> Khi $La/R \to 1$, queueing delay sẽ:
> 
> A. Bằng 0  
> B. Tăng tuyến tính  
> C. **Tiến tới vô cực**  
> D. Giảm về 0

> [!success]- 📌 Đáp án & Giải thích
> **Đáp án: C – Tiến tới vô cực**
> 
> Đây là kết quả từ lý thuyết hàng đợi (queueing theory). Khi $La/R \to 1$:
> - Tốc độ đến $\approx$ tốc độ phục vụ
> - Bất kỳ đợt bursty nhỏ nào cũng gây hàng đợi tích lũy
> - Queueing delay tăng theo hàm **phi tuyến** và tiến tới $+\infty$
> 
> Thực tế: Khi buffer đầy → gói tin bị **drop (packet loss)** thay vì chờ vô hạn

---

> [!question] C1-T4. Throughput và Bottleneck
> Throughput end-to-end qua nhiều liên kết được xác định bởi:
> 
> A. Tổng băng thông các liên kết  
> B. Liên kết có băng thông lớn nhất  
> C. **Bottleneck link – liên kết có băng thông nhỏ nhất**  
> D. Băng thông trung bình

> [!success]- 📌 Đáp án & Giải thích
> **Đáp án: C – Bottleneck link**
> 
> $$\text{Throughput} = \min(R_1, R_2, \ldots, R_N)$$
> 
> Giống như nước chảy qua ống hẹp — dù các đoạn khác rộng đến đâu, tốc độ bị giới hạn bởi đoạn hẹp nhất.
> 
> **Ví dụ thực tế:** Nếu server kết nối Internet với 100 Gbps nhưng đường dây ADSL của bạn chỉ 100 Mbps → throughput thực tế là 100 Mbps (bottleneck ở access link của bạn)

---

> [!question] C1-T5. Công cụ Packet Sniffing
> Công cụ nào thường dùng để thực hiện packet sniffing?
> 
> A. Ping  
> B. Traceroute  
> C. **Wireshark**  
> D. Nmap

> [!success]- 📌 Đáp án & Giải thích
> **Đáp án: C – Wireshark**
> 
> - **Wireshark:** phân tích gói tin (packet analyzer), đặt card mạng ở chế độ promiscuous, bắt và decode tất cả gói tin. Dùng hợp pháp để debug mạng trong lab.
> - **Ping:** kiểm tra kết nối bằng ICMP Echo
> - **Traceroute:** truy vết đường đi của gói tin qua các router
> - **Nmap:** quét cổng và dịch vụ của một host

---

## 🔴 Phần C – Bài tập tính toán

> [!question] C1-BT1. Transmission Delay
> Một file $F = 8 \times 10^6$ bits được gửi qua liên kết tốc độ $R = 1$ Mbps.
> 
> a) Tính $d_{\text{trans}}$.  
> b) Nếu $R = 100$ Mbps thì sao?

> [!success]- 📌 Đáp án & Giải thích
> 
> **a)** $R = 1 \text{ Mbps} = 10^6 \text{ bps}$
> $$d_{\text{trans}} = \frac{L}{R} = \frac{8 \times 10^6}{10^6} = \mathbf{8 \text{ giây}}$$
> 
> **b)** $R = 100 \text{ Mbps} = 10^8 \text{ bps}$
> $$d_{\text{trans}} = \frac{8 \times 10^6}{10^8} = 0.08 \text{ s} = \mathbf{80 \text{ ms}}$$
> 
> **Nhận xét:** Tăng tốc độ liên kết lên 100× → thời gian truyền giảm 100× (tỷ lệ nghịch tuyến tính). Đây là lý do vì sao nâng cấp bandwidth là giải pháp hiệu quả nhất cho vấn đề transmission delay.

---

> [!question] C1-BT2. Store-and-Forward qua 2 Router
> Một gói tin $L = 10$ Kbits đi qua 3 liên kết (2 router trung gian), mỗi liên kết tốc độ $R = 10$ Mbps. Bỏ qua tất cả delay khác. Tính tổng thời gian từ nguồn đến đích.

> [!success]- 📌 Đáp án & Giải thích
> 
> Với store-and-forward qua $N$ liên kết, mỗi router phải nhận đủ gói rồi mới truyền đi:
> 
> $$d_{\text{end-to-end}} = N \times \frac{L}{R}$$
> 
> Ở đây $N = 3$ liên kết:
> $$d = 3 \times \frac{10 \times 10^3}{10 \times 10^6} = 3 \times 10^{-3} \text{ s} = \mathbf{3 \text{ ms}}$$
> 
> **Tại sao $N$ lần chứ không phải $2N-1$?**  
> Với pipelining: khi router 1 đang nhận bit cuối của gói, router 2 có thể đồng thời đang truyền phần đầu → không cần đợi hoàn toàn. Với **một gói duy nhất** (không có pipelining), mỗi router phải nhận xong rồi mới truyền → tổng là $N \times L/R$.

---

> [!question] C1-BT3. Propagation Delay
> Liên kết dài $d = 5000$ km, tốc độ $R = 1$ Gbps, gói tin $L = 10$ Kbits, $s = 2 \times 10^8$ m/s.
> 
> a) Tính $d_{\text{prop}}$.  
> b) Tính $d_{\text{trans}}$.  
> c) Thành phần nào lớn hơn? Kết luận gì?

> [!success]- 📌 Đáp án & Giải thích
> 
> **a) Propagation delay:**
> $$d_{\text{prop}} = \frac{d}{s} = \frac{5 \times 10^6 \text{ m}}{2 \times 10^8 \text{ m/s}} = 0.025 \text{ s} = \mathbf{25 \text{ ms}}$$
> 
> **b) Transmission delay:**
> $$d_{\text{trans}} = \frac{L}{R} = \frac{10 \times 10^3}{10^9} = 10^{-5} \text{ s} = \mathbf{0.01 \text{ ms}}$$
> 
> **c) Nhận xét:**
> $d_{\text{prop}} = 25 \text{ ms} \gg d_{\text{trans}} = 0.01 \text{ ms}$
> 
> → Với liên kết **tốc độ cao** (1 Gbps) và **đường dài** (5000 km), propagation delay chiếm ưu thế hoàn toàn. Đây là lý do vì sao ping đến server ở châu lục khác luôn > 100 ms dù đường truyền rất nhanh.

---

> [!question] C1-BT4. Packet Switching vs. Circuit Switching
> Liên kết 1 Mbps. Mỗi user cần 100 Kbps khi active, xác suất active = 10%.
> 
> a) Circuit switching phục vụ tối đa bao nhiêu user?  
> b) Với packet switching và 35 user, tính xác suất có **hơn 10 user active** cùng lúc.  
> c) Packet switching có ưu thế hơn không? Tại sao?

> [!success]- 📌 Đáp án & Giải thích
> 
> **a) Circuit switching:**
> $$N_{\text{max}} = \frac{1 \text{ Mbps}}{100 \text{ Kbps}} = \mathbf{10 \text{ user}}$$
> Mỗi user chiếm 1/10 băng thông dù có dùng hay không.
> 
> **b) Packet switching với 35 user**, $X \sim \text{Binomial}(35, 0.1)$:
> 
> Mạng tắc nghẽn khi $X > 10$ (hơn 10 user active cùng lúc):
> 
> $$P(X > 10) = 1 - P(X \leq 10) = 1 - \sum_{k=0}^{10} \binom{35}{k} 0.1^k \cdot 0.9^{35-k}$$
> 
> Tính gần đúng → $P(X > 10) \approx \mathbf{0.04\%}$ (rất nhỏ!)
> 
> **c) Kết luận:**
> - Packet switching phục vụ **35 user** nhưng xác suất tắc nghẽn chỉ 0.04%
> - Circuit switching chỉ phục vụ **10 user** với tài nguyên lãng phí 90% thời gian
> - → Packet switching **hiệu quả hơn 3.5×** cho traffic bursty như web

