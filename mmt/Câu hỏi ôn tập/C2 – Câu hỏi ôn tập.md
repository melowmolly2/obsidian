---
tags:
  - mmt/ôn-tập
  - mmt/câu-hỏi
  - mmt/chương-2
---

up:: [[Mạng máy tính MOC]]
prev:: [[C1 – Câu hỏi ôn tập]]
next:: [[C3 – Câu hỏi ôn tập]]

# 📝 Chương 2 – Application Layer

> Dựa trên giáo trình *Computer Networking: A Top-Down Approach* – Kurose & Ross, 8th ed.
> Nguồn ghi chú: [[2.1 Principles of Network Applications]] · [[2.2 The Web and HTTP]] · [[2.3 Email]] · [[2.4 DNS]] · [[2.5 Video Streaming + CDNS]] · [[2.6 Socket Programming]]

---

## 🔵 Phần A – Lý thuyết (tự luận)

> [!question] C2-1. Client-Server vs. Peer-to-Peer
> So sánh mô hình **client-server** và **peer-to-peer (P2P)**. Cho ví dụ ứng dụng tương ứng.

> [!success]- 📌 Đáp án & Giải thích
> 
> | Tiêu chí | Client-Server | Peer-to-Peer (P2P) |
> |---|---|---|
> | **Server** | Luôn hoạt động (always-on) | Không có server cố định |
> | **Địa chỉ IP** | Server có IP cố định | Peer có IP động |
> | **Khả năng mở rộng** | Cần tăng server khi tải tăng | Tự co giãn (self-scalability) |
> | **Giao tiếp** | Client không giao tiếp trực tiếp | Peer giao tiếp trực tiếp với nhau |
> | **Quản lý** | Tập trung, dễ kiểm soát | Phân tán, phức tạp hơn |
> | **Chi phí** | Cần data center, infrastructure lớn | Chi phí infrastructure thấp hơn |
> 
> **Ví dụ Client-Server:**
> - Web (HTTP): trình duyệt → web server
> - Email (SMTP/IMAP): mail client → mail server
> - Video streaming: Netflix/YouTube app → CDN server
> 
> **Ví dụ P2P:**
> - File sharing: BitTorrent (mỗi peer vừa tải vừa chia sẻ)
> - Cryptocurrency: Bitcoin (mỗi node lưu blockchain)
> - Video call: Skype ban đầu (trước khi chuyển sang hybrid)
> 
> **Hybrid model:** Nhiều ứng dụng kết hợp cả hai (ví dụ: Spotify dùng server để quản lý nhưng dùng P2P để phân phối nhạc)

---

> [!question] C2-2. Socket là gì?
> Socket là gì? Tại sao được ví như "cái cửa" giữa process và mạng?

> [!success]- 📌 Đáp án & Giải thích
> 
> **Socket** là giao diện lập trình (API) giữa **application layer** và **transport layer** — là "cửa" mà process gửi/nhận message qua mạng.
> 
> ```
> ┌─────────────────────┐
> │   Application       │
> │   (Process)         │
> └──────┬──────────────┘
>        │ send()/recv()
>     ┌──▼────┐  ← Socket (cái cửa)
>     │ 🚪     │
>     └───┬───┘
>         │
> ┌───────▼─────────────┐
> │  Transport Layer    │
> │  (TCP/UDP)          │
> └─────────────────────┘
> ```
> 
> **Tại sao ví như cái cửa?**
> - Process chỉ kiểm soát **phía trên socket** (tầng application) — tạo message, chọn giao thức transport (TCP/UDP), chọn port
> - **Phía dưới socket** do hệ điều hành kiểm soát — routing, congestion control, retransmission (với TCP) nằm ngoài tầm tay lập trình viên
> - Giống như bạn bỏ thư vào hộp thư (socket) rồi bưu điện (OS + network) lo phần còn lại
> 
> **Định danh socket:** Cần **IP address + port number** để định vị chính xác process đích (ví dụ: `192.168.1.10:80`)

---

> [!question] C2-3. HTTP là Stateless
> HTTP là giao thức **stateless**. Điều đó có nghĩa gì? Cookie ra đời để giải quyết vấn đề gì?

> [!success]- 📌 Đáp án & Giải thích
> 
> **Stateless** = "phi trạng thái": server **không lưu thông tin** về các request trước đó của client.
> 
> **Ví dụ:**
> - Bạn gửi request 1: "Cho tôi trang chủ"
> - Server trả về trang chủ, sau đó **quên mất** bạn là ai
> - Bạn gửi request 2: "Cho tôi giỏ hàng"
> - Server không biết request 2 đến từ cùng người với request 1
> 
> **Ưu điểm của stateless:**
> - Đơn giản, dễ scale (server không cần nhớ hàng triệu session)
> - Server crash không mất state
> 
> **Nhược điểm:**
> - Không thể cá nhân hóa trải nghiệm (login, giỏ hàng, preference...)
> 
> **Giải pháp: Cookie**
> ```
> Request 1 (lần đầu):
>   Client → GET /index.html
>   Server → 200 OK
>            Set-Cookie: userID=1234
> 
> Request 2 (lần sau):
>   Client → GET /cart
>            Cookie: userID=1234
>   Server → (đọc cookie) "À, đây là user 1234!" → trả về giỏ hàng của user đó
> ```
> 
> Cookie cho phép server **ủy thác việc lưu state cho client** — client gửi kèm cookie mỗi request, server dùng cookie như "vé số" để tra cứu thông tin trong database.

---

> [!question] C2-4. Non-persistent vs. Persistent HTTP
> Giải thích sự khác biệt giữa **non-persistent HTTP** và **persistent HTTP**. Tính thời gian phản hồi theo RTT.

> [!success]- 📌 Đáp án & Giải thích
> 
> | | Non-persistent HTTP | Persistent HTTP (HTTP/1.1+) |
> |---|---|---|
> | **Kết nối TCP** | Mở/đóng **mỗi object** | Mở **một lần**, dùng cho nhiều object |
> | **RTT/object** | 2 RTT + transmission time | ~1 RTT (với pipelining) |
> | **Overhead** | Cao (nhiều TCP handshake) | Thấp |
> | **Tình trạng OS** | Tốn tài nguyên (nhiều socket) | Tiết kiệm tài nguyên |
> 
> **Non-persistent response time cho 1 object:**
> $$\text{Time} = 2 \times RTT + d_{\text{trans}}$$
> - RTT 1: TCP 3-way handshake
> - RTT 2: HTTP GET request + phần đầu response
> - $d_{\text{trans}}$: thời gian truyền file
> 
> **Ví dụ:** Web page có 1 HTML + 10 ảnh (11 objects):
> - **Non-persistent:** $11 \times (2 \times RTT) = 22 \text{ RTT}$ (+ transmission time)
> - **Persistent với pipelining:** $1 \text{ RTT (handshake)} + 1 \text{ RTT (requests)} \approx 2–3 \text{ RTT}$ (+ transmission)
> 
> → Persistent HTTP nhanh hơn **7–10×** cho trang nhiều object!

---

> [!question] C2-5. HTTP Methods
> Liệt kê 4 HTTP method chính và mục đích của từng method.

> [!success]- 📌 Đáp án & Giải thích
> 
> | Method | Mục đích | Upload data? | Idempotent? |
> |---|---|---|---|
> | **GET** | Lấy tài nguyên từ server | Không (hoặc qua query string) | ✅ Có |
> | **POST** | Gửi dữ liệu đến server (form, upload) | ✅ Có (trong body) | ❌ Không |
> | **PUT** | Upload/thay thế tài nguyên lên server | ✅ Có | ✅ Có |
> | **HEAD** | Lấy header (không lấy body) | Không | ✅ Có |
> | **DELETE** | Xóa tài nguyên | Không | ✅ Có |
> 
> **Idempotent** = gọi nhiều lần cho cùng kết quả (GET file 10 lần = GET 1 lần; POST form 10 lần = tạo 10 record khác nhau)
> 
> **Ví dụ thực tế:**
> - `GET /users/123` → lấy thông tin user 123
> - `POST /users` → tạo user mới
> - `PUT /users/123` → cập nhật toàn bộ user 123
> - `DELETE /users/123` → xóa user 123
> - `HEAD /large-file.zip` → kiểm tra kích thước file trước khi tải

---

> [!question] C2-6. Tại sao DNS không tập trung?
> Tại sao DNS không tập trung vào một server duy nhất? Nêu ít nhất 3 lý do.

> [!success]- 📌 Đáp án & Giải thích
> 
> **❌ Tập trung DNS vào 1 server là ý tưởng tồi vì:**
> 
> **1. Single Point of Failure (Điểm hỏng duy nhất):**
> - Server sập → toàn bộ Internet ngừng hoạt động (không phân giải được tên → không vào được web)
> 
> **2. Traffic Volume (Lưu lượng cực lớn):**
> - Comcast xử lý **600 tỷ** DNS query/ngày
> - Akamai xử lý **2,2 nghìn tỷ** query/ngày
> - 1 server không thể chịu được lượng query này
> 
> **3. Distant Centralized Database (Cơ sở dữ liệu xa người dùng):**
> - Nếu DNS server đặt ở Mỹ, người dùng Việt Nam phải query qua Thái Bình Dương → delay cao (> 200 ms RTT)
> 
> **4. Maintenance (Khó bảo trì):**
> - Hàng triệu tên miền được tạo/xóa mỗi ngày
> - 1 database tập trung không thể cập nhật kịp thời
> 
> **✅ Giải pháp: Phân tán + Phân cấp**
> DNS dùng kiến trúc **hierarchical, distributed** với 3 cấp: Root → TLD (.com, .edu...) → Authoritative (amazon.com, umass.edu...)

---

> [!question] C2-7. Kiến trúc DNS phân cấp
> Mô tả 3 loại DNS server trong kiến trúc phân cấp. Phân biệt **iterative query** và **recursive query**.

> [!success]- 📌 Đáp án & Giải thích
> 
> **Ba cấp DNS server:**
> 
> | Cấp | Vai trò | Số lượng |
> |---|---|---|
> | **Root DNS servers** | Chỉ đường đến TLD servers; xử lý query cuối cùng khi cache không có | 13 server logic (hàng trăm server vật lý) |
> | **TLD servers** | Quản lý các domain thuộc .com, .org, .edu, .vn... | Hàng chục server/TLD |
> | **Authoritative servers** | Lưu DNS record chính thức của tổ chức (ví dụ: MIT có authoritative server cho mit.edu) | Hàng triệu server |
> 
> **Iterative query** – Local DNS tự đi hỏi từng cấp:
> ```
> Client → Local DNS: "gaia.cs.umass.edu là gì?"
> Local DNS → Root: "umass.edu ở đâu?"
>    Root → Local DNS: "Hỏi .edu TLD server (IP: X)"
> Local DNS → TLD: "umass.edu ở đâu?"
>    TLD → Local DNS: "Hỏi umass.edu server (IP: Y)"
> Local DNS → Authoritative: "gaia.cs.umass.edu?"
>    Auth → Local DNS: "128.119.245.12"
> Local DNS → Client: "128.119.245.12"
> ```
> → **Gánh nặng trên Local DNS** (phải query nhiều lần)
> 
> **Recursive query** – đẩy gánh nặng lên server trên:
> ```
> Client → Local DNS: "gaia.cs.umass.edu?"
> Local DNS → Root: "gaia.cs.umass.edu?"
>    Root → TLD: "gaia.cs.umass.edu?"
>       TLD → Auth: "gaia.cs.umass.edu?"
>       Auth → TLD: "128.119.245.12"
>    TLD → Root: "128.119.245.12"
> Root → Local DNS: "128.119.245.12"
> Local DNS → Client: "128.119.245.12"
> ```
> → **Gánh nặng trên Root/TLD** (không được khuyến khích, dễ quá tải)

---

> [!question] C2-8. DNS Resource Record
> DNS Resource Record (RR) có dạng `(Name, Value, Type, TTL)`. Giải thích ý nghĩa các trường **Type A**, **Type NS**, **Type CNAME**, **Type MX**.

> [!success]- 📌 Đáp án & Giải thích
> 
> **Cấu trúc RR:** `(Name, Value, Type, TTL)`
> - **Name:** tên miền hoặc hostname
> - **Value:** giá trị tương ứng (phụ thuộc Type)
> - **Type:** loại record
> - **TTL:** thời gian cache (giây)
> 
> | Type | Name | Value | Ý nghĩa |
> |---|---|---|---|
> | **A** | Hostname | IP address (IPv4) | Ánh xạ tên → IP |
> | **NS** | Domain | Hostname của authoritative server | Chỉ đường đến authoritative server |
> | **CNAME** | Alias | Canonical name (tên chính thức) | Tên bí danh → tên thật |
> | **MX** | Domain | Hostname của mail server | Xác định mail server cho domain |
> 
> **Ví dụ:**
> ```
> (gaia.cs.umass.edu, 128.119.245.12, A, 3600)
> → gaia.cs.umass.edu có IP là 128.119.245.12
> 
> (umass.edu, dns.umass.edu, NS, 86400)
> → Server authoritative cho umass.edu là dns.umass.edu
> 
> (www.example.com, server1.example.com, CNAME, 3600)
> → www.example.com là alias của server1.example.com
> 
> (example.com, mail.example.com, MX, 7200)
> → Email gửi đến @example.com sẽ đến mail.example.com
> ```
> 
> **Lưu ý:** Một query DNS trả về **nhiều RR** cùng lúc (ví dụ: trả cả NS record và A record của name server đó)

---

> [!question] C2-9. DASH – Adaptive Streaming
> **DASH** (Dynamic Adaptive Streaming over HTTP) hoạt động như thế nào? Manifest file dùng để làm gì?

> [!success]- 📌 Đáp án & Giải thích
> 
> **DASH** = video streaming thông minh, tự động điều chỉnh chất lượng dựa trên băng thông hiện tại.
> 
> **Cách hoạt động:**
> 
> **1. Server chuẩn bị:**
> - Chia video thành **chunks** (đoạn 2–10 giây)
> - Mỗi chunk được encode ở **nhiều bitrate** (360p, 720p, 1080p, 4K...)
> - Tạo **manifest file** (MPD – Media Presentation Description) liệt kê:
>   - URL của từng chunk
>   - Bitrate có sẵn cho mỗi chunk
>   - Thời lượng chunk
> 
> **2. Client streaming:**
> ```
> Bước 1: GET manifest.mpd
> Bước 2: Đo băng thông hiện tại
> Bước 3: Chọn bitrate phù hợp cho chunk tiếp theo
> Bước 4: GET chunk_001_1080p.mp4
> Bước 5: Phát chunk, đồng thời đo lại băng thông
> Bước 6: Nếu băng thông giảm → chọn 720p cho chunk tiếp
> ...
> ```
> 
> **Ưu điểm:**
> - Không bị giật lag (buffering) khi mạng chậm
> - Tối ưu chất lượng khi mạng tốt
> - **Client-side logic** → server đơn giản hơn, dễ scale
> 
> **Ví dụ manifest:**
> ```xml
> <Representation bandwidth="500000" width="640" height="360">
>   <BaseURL>360p/</BaseURL>
> </Representation>
> <Representation bandwidth="2000000" width="1920" height="1080">
>   <BaseURL>1080p/</BaseURL>
> </Representation>
> ```

---

> [!question] C2-10. CDN – Enter Deep vs. Bring Home
> CDN sử dụng hai chiến lược phân phối server. Giải thích và so sánh **Enter Deep** và **Bring Home**.

> [!success]- 📌 Đáp án & Giải thích
> 
> **CDN (Content Delivery Network)** = mạng lưới server phân tán toàn cầu, đặt nội dung **gần người dùng** để giảm delay và tăng throughput.
> 
> | Chiến lược | Mô tả | Ưu điểm | Nhược điểm | Ví dụ |
> |---|---|---|---|---|
> | **Enter Deep** | Đặt **nhiều cluster nhỏ** sâu vào access network ISP (gần sát người dùng) | • Delay cực thấp<br>• Throughput cao | • Chi phí bảo trì lớn<br>• Quản lý phức tạp | Akamai |
> | **Bring Home** | Đặt **ít cluster lớn** tại các IXP (Internet Exchange Point) | • Chi phí thấp hơn<br>• Dễ quản lý | • Delay cao hơn Enter Deep<br>• Throughput thấp hơn | Limelight |
> 
> **Minh họa:**
> ```
> Enter Deep:
>   Origin Server (US)
>      ├─ Cluster Hà Nội (Viettel)
>      ├─ Cluster Hà Nội (VNPT)
>      ├─ Cluster Sài Gòn (FPT)
>      └─ ... (hàng nghìn cluster)
> 
> Bring Home:
>   Origin Server (US)
>      ├─ Cluster Singapore (IXP)
>      ├─ Cluster Tokyo (IXP)
>      └─ Cluster Sydney (IXP)
>      (vài chục cluster)
> ```
> 
> **Cả hai đều dùng:**
> - **DNS-based redirection:** khi query `video.cdn.com`, DNS trả về IP của server gần nhất
> - **Caching:** lưu nội dung phổ biến, giảm tải cho origin server

---

## 🟡 Phần B – Trắc nghiệm

> [!question] C2-T1. HTTP dùng giao thức transport nào?
> HTTP sử dụng giao thức transport nào, và tại sao?
> 
> A. UDP – vì nhanh hơn  
> B. **TCP – vì cần truyền tin cậy**  
> C. IP – vì là giao thức nền tảng  
> D. SMTP – vì là text-based

> [!success]- 📌 Đáp án & Giải thích
> **Đáp án: B – TCP (port 80 cho HTTP, port 443 cho HTTPS)**
> 
> Lý do HTTP cần TCP:
> - Web page phải được tải **đầy đủ và đúng thứ tự** (1 bit lỗi có thể làm hỏng toàn bộ trang)
> - TCP đảm bảo **reliable, in-order delivery**
> - Giá trị phải trả: overhead của TCP handshake (2 RTT)
> 
> **Ngoại lệ:** HTTP/3 (mới) chuyển sang dùng **QUIC** (chạy trên UDP) để giảm latency nhưng tự xây dựng lại reliability ở tầng application

---

> [!question] C2-T2. RTT với Non-persistent HTTP
> Với non-persistent HTTP, để tải 1 HTML + 5 ảnh (6 objects), cần tối thiểu bao nhiêu RTT (bỏ qua transmission time)?
> 
> A. 2  
> B. 6  
> C. **12**  
> D. 7

> [!success]- 📌 Đáp án & Giải thích
> **Đáp án: C – 12 RTT**
> 
> Mỗi object cần:
> - 1 RTT: TCP 3-way handshake
> - 1 RTT: HTTP GET + bắt đầu nhận response
> - **Tổng: 2 RTT/object**
> 
> 6 objects × 2 RTT = **12 RTT**
> 
> *(Nếu dùng persistent HTTP: 1 RTT handshake + 1 RTT cho tất cả requests (nếu pipelining) = 2 RTT tổng)*

---

> [!question] C2-T3. DNS Query Types
> Loại DNS query nào đặt toàn bộ gánh nặng phân giải lên local DNS server?
> 
> A. **Iterative query**  
> B. Recursive query  
> C. Authoritative query  
> D. Broadcast query

> [!success]- 📌 Đáp án & Giải thích
> **Đáp án: A – Iterative query**
> 
> - **Iterative:** Root/TLD server chỉ trả về "đi hỏi server X" → local DNS phải tự đi hỏi tiếp
> - **Recursive:** Root/TLD server tự đi hỏi thay cho local DNS → gánh nặng trên Root/TLD
> 
> Thực tế: Internet dùng **iterative** để bảo vệ Root/TLD server khỏi quá tải

---

> [!question] C2-T4. Email Protocol
> Trong email, giao thức nào dùng để **lấy** mail từ mail server về user agent?
> 
> A. SMTP  
> B. HTTP  
> C. **IMAP**  
> D. FTP

> [!success]- 📌 Đáp án & Giải thích
> **Đáp án: C – IMAP (hoặc POP3)**
> 
> Vai trò các giao thức:
> - **SMTP** (Simple Mail Transfer Protocol): **gửi** mail từ sender → mail server, và giữa các mail server
> - **IMAP** (Internet Mail Access Protocol): **lấy** mail từ server về client, **giữ mail trên server** (sync nhiều thiết bị)
> - **POP3** (Post Office Protocol v3): **lấy** mail và **xóa khỏi server** (dùng 1 thiết bị)
> 
> ```
> Alice → [SMTP] → Mail Server Alice → [SMTP] → Mail Server Bob → [IMAP] → Bob
> ```

---

> [!question] C2-T5. Web Cache
> Caching ở **web proxy** giúp ích cho người dùng theo cách nào?
> 
> A. Mã hóa nội dung web  
> B. **Giảm thời gian phản hồi và giảm lưu lượng ra Internet**  
> C. Tăng tốc kết nối TCP  
> D. Phân giải DNS nhanh hơn

> [!success]- 📌 Đáp án & Giải thích
> **Đáp án: B**
> 
> Web cache (proxy server) lưu bản copy của object đã request:
> 
> **Lợi ích:**
> 1. **Giảm response time** – nếu cache hit, không cần query đến origin server (tiết kiệm RTT)
> 2. **Giảm traffic** – giảm băng thông qua access link ra Internet (tiết kiệm chi phí)
> 3. **Giảm tải origin server** – server không phải xử lý request trùng lặp
> 
> **Conditional GET:** Cache gửi `If-Modified-Since` → server trả `304 Not Modified` nếu chưa thay đổi → tiết kiệm băng thông

---

## 🔴 Phần C – Bài tập tính toán

> [!question] C2-BT1. RTT với HTTP
> Web page gồm 1 HTML + 10 ảnh JPEG. Mỗi object có transmission time = 0.5 RTT. RTT = 20 ms.
> 
> a) Tính tổng thời gian tải trang với **non-persistent HTTP** (không parallel).  
> b) Tính với **persistent HTTP có pipelining**.

> [!success]- 📌 Đáp án & Giải thích
> 
> **a) Non-persistent HTTP:**
> Mỗi object cần: **2 RTT (handshake + GET/response) + 0.5 RTT (trans)** = 2.5 RTT
> 
> 11 objects × 2.5 RTT × 20 ms = **550 ms**
> 
> ---
> 
> **b) Persistent HTTP với pipelining:**
> 
> ```
> t=0:     TCP handshake bắt đầu
> t=1 RTT: GET HTML
> t=2 RTT: Nhận xong HTML, gửi 10 GET (ảnh) cùng lúc
> t=3 RTT: Bắt đầu nhận ảnh đầu tiên
> t=3 RTT + 10×0.5RTT: Nhận xong ảnh cuối (pipelined)
> ```
> 
> **Tổng:** $1 + 1 + 0.5 + 10 \times 0.5 = 7.5 \text{ RTT} = 150 \text{ ms}$
> 
> → **Cải thiện 3.7×** so với non-persistent!

---

> [!question] C2-BT2. DNS Caching & TTL
> Local DNS cache có TTL = 20 giây. Query đến `gaia.cs.umass.edu`:
> - $t=0$: query đầu (cache rỗng)
> - $t=10$: query lần 2
> - $t=25$: query lần 3
> 
> Full resolution = 8 time units, cache hit = 2 units. Tính thời gian mỗi query.

> [!success]- 📌 Đáp án & Giải thích
> 
> **t=0:** Cache rỗng → phải full resolution (query Root → TLD → Auth)  
> → **8 units**  
> Record được cache với TTL = 20s
> 
> **t=10:** Cache còn hiệu lực ($10 < 20$) → cache hit  
> → **2 units**
> 
> **t=25:** Cache đã hết hạn ($25 > 20$) → phải full resolution lại  
> → **8 units**
> 
> **Kết luận:** TTL ngắn → truy vấn thường xuyên hơn nhưng dữ liệu mới hơn; TTL dài → ít query hơn nhưng có thể lấy dữ liệu cũ

---

> [!question] C2-BT3. Conditional GET
> Web cache nhận request cho object có `Last-Modified: Mon, 1 Jan 2024`. Cache gửi:
> ```
> GET /file.html HTTP/1.1
> If-Modified-Since: Mon, 1 Jan 2024
> ```
> Server trả về **304 Not Modified**.
> 
> a) Cache có gửi object cho client không? Từ đâu?  
> b) HTTP status code nào thể hiện object **đã** thay đổi?

> [!success]- 📌 Đáp án & Giải thích
> 
> **a)** Cache **có** gửi object cho client, từ **bản đã lưu trong cache**.
> 
> - Server trả `304 Not Modified` + **không có body** → tiết kiệm băng thông
> - Cache dùng bản cũ đã lưu để phục vụ client
> 
> **Lợi ích:**
> - Client được phục vụ (có object)
> - Băng thông giữa cache ↔ origin server tiết kiệm (chỉ truyền header, không truyền body)
> 
> ---
> 
> **b) HTTP 200 OK** kèm theo body mới
> 
> ```
> HTTP/1.1 200 OK
> Date: Tue, 2 Jan 2024
> Last-Modified: Tue, 2 Jan 2024
> Content-Length: 5000
> 
> <body mới>
> ```
> 
> Cache sẽ thay thế bản cũ bằng bản mới này.

---

*Xem thêm: [[C1 – Câu hỏi ôn tập]] · [[C3 – Câu hỏi ôn tập]]*
