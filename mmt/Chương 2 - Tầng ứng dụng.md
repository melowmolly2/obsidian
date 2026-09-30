## 📚 Chương 2: Tầng Ứng Dụng — Lý thuyết cần nhớ

---

## 1. Nguyên tắc cơ bản của ứng dụng mạng

### Hai mô hình kiến trúc

| | **Client-Server** | **P2P (Peer-to-Peer)** |
|---|---|---|
| Server | Luôn hoạt động, IP cố định | Không có server luôn hoạt động |
| Client | IP động, không liên lạc trực tiếp nhau | Các peer liên lạc trực tiếp |
| Ví dụ | HTTP, IMAP, FTP | BitTorrent, Skype |
| Mở rộng | Hạn chế (phụ thuộc server) | Tự mở rộng (peer mới = tài nguyên mới) |

### Socket & Địa chỉ tiến trình
- **Process:** chương trình đang chạy trong host.
- **Socket:** "cánh cửa" giữa tiến trình và tầng transport — tiến trình gửi/nhận dữ liệu qua socket.
- **Địa chỉ tiến trình = IP + Port number** (vì nhiều tiến trình có thể chạy trên cùng một host).
- Port phổ biến: HTTP = **80**, Mail (SMTP) = **25**.

### Yêu cầu của ứng dụng với tầng Transport

| Ứng dụng | Mất dữ liệu | Băng thông | Nhạy cảm thời gian |
|---|---|---|---|
| File transfer, email, web | Không được mất | Đàn hồi (elastic) | Không |
| Audio/video thời gian thực | Chịu được mất | Vài Kbps–Mbps | Có (10ms–vài giây) |
| Game tương tác | Chịu được mất | Kbps+ | Có |
| Nhắn tin | Không được mất | Đàn hồi | Không quan trọng |

### TCP vs UDP

| | **TCP** | **UDP** |
|---|---|---|
| Độ tin cậy | **Có** (đảm bảo giao đúng, đủ) | Không |
| Kiểm soát luồng | Có | Không |
| Kiểm soát tắc nghẽn | Có | Không |
| Kết nối | Có (handshake) | Không |
| Tốc độ | Chậm hơn | **Nhanh hơn** |
| Dùng cho | HTTP, FTP, SMTP | DNS, video call, game |

> ❓ **Tại sao cần UDP?** Vì TCP quá "nặng" cho các ứng dụng cần tốc độ hơn độ tin cậy (video call, game).

### TLS (Transport Layer Security)
- TCP/UDP vanilla **không mã hóa** — password gửi dưới dạng cleartext!
- **TLS** = bọc thêm lớp mã hóa, xác thực, toàn vẹn dữ liệu **trên TCP**.
- TLS được implement ở **tầng Application** (thư viện), không phải tầng Transport.

---

## 2. HTTP (Web)

### Tổng quan
- **HTTP** = HyperText Transfer Protocol — giao thức tầng ứng dụng của Web.
- Dùng **TCP, port 80**.
- **Stateless:** server **không lưu** thông tin về các request trước của client.
- Web page = file HTML gốc + các object (ảnh, CSS...) tham chiếu qua URL.

### Hai loại kết nối

| | **Non-persistent HTTP** | **Persistent HTTP (1.1)** |
|---|---|---|
| TCP connection | Một object / một connection | Nhiều object / một connection |
| Thời gian tải | **2 RTT + thời gian truyền file** mỗi object | **1 RTT** cho các object sau |
| Nhược điểm | Tốn overhead OS | Mặc định trong HTTP/1.1 |

$$\text{Non-persistent HTTP response time} = 2\text{RTT} + T_{trans}$$

### HTTP Methods

| Method | Chức năng |
|---|---|
| **GET** | Lấy tài nguyên; có thể gửi dữ liệu qua URL (`?key=value`) |
| **POST** | Gửi dữ liệu lên server trong body |
| **HEAD** | Chỉ lấy header, không lấy body |
| **PUT** | Upload/thay thế file trên server |

### HTTP Status Codes quan trọng

| Code | Ý nghĩa |
|---|---|
| **200 OK** | Thành công |
| **301 Moved Permanently** | Đã chuyển địa chỉ |
| **304 Not Modified** | Cache còn hợp lệ (dùng với Conditional GET) |
| **400 Bad Request** | Server không hiểu request |
| **404 Not Found** | Không tìm thấy tài nguyên |
| **505 HTTP Version Not Supported** | Phiên bản HTTP không hỗ trợ |

### Cookies
- HTTP stateless → dùng **cookie** để duy trì trạng thái.
- 4 thành phần: header trong HTTP response → header trong HTTP request tiếp theo → file cookie ở browser → database ở server.
- **First-party cookie:** từ web bạn truy cập.
- **Third-party cookie (tracking cookie):** từ web bạn **không** chọn truy cập → theo dõi hành vi xuyên web.

### Web Cache (Proxy Server)
- Cache lưu bản sao object → trả về trực tiếp cho client không cần gọi đến origin server.
- Lợi ích: **giảm thời gian phản hồi**, **giảm tải trên access link**.
- **Conditional GET:** Client gửi `If-Modified-Since: <date>` → server trả `304 Not Modified` nếu cache vẫn hợp lệ (không gửi lại object).

### HTTP/1.1 → HTTP/2 → HTTP/3

| Version | Đặc điểm chính |
|---|---|
| **HTTP/1.1** | Persistent, pipelined GET nhưng trả lời **theo thứ tự FCFS** → **HOL blocking** |
| **HTTP/2** | Chia object thành **frames**, xen kẽ frames → giảm HOL blocking; server **push** chủ động; ưu tiên theo client |
| **HTTP/3** | Dùng **UDP** thay TCP → kiểm soát lỗi/tắc nghẽn per-object; bảo mật tích hợp |

---

## 3. Email (SMTP & IMAP)

### Kiến trúc Email
```
User Agent → [SMTP] → Mail Server → [SMTP] → Mail Server → [IMAP/HTTP] → User Agent
```

### SMTP (Simple Mail Transfer Protocol)
- Dùng **TCP, port 25**.
- **Client push** (đẩy mail): ngược với HTTP là client pull.
- Message và lệnh phải ở **ASCII 7-bit**.
- Kết thúc message bằng `CRLF.CRLF`.
- **Persistent connection** giữa các mail server.

**Quy trình gửi mail (Alice → Bob):**
1. Alice soạn mail trên User Agent.
2. UA gửi tới mail server Alice qua SMTP.
3. Mail server Alice mở TCP đến mail server Bob.
4. Gửi mail qua TCP.
5. Mail server Bob lưu vào mailbox Bob.
6. Bob dùng IMAP/HTTP để đọc mail.

**Sample SMTP interaction:**
```
S: 220 hamburger.edu
C: HELO crepes.fr
C: MAIL FROM: <alice@crepes.fr>
C: RCPT TO: <bob@hamburger.edu>
C: DATA
C: [nội dung]
C: .          ← kết thúc bằng dấu chấm trên dòng riêng
C: QUIT
```

### So sánh SMTP vs HTTP

| | **SMTP** | **HTTP** |
|---|---|---|
| Hướng | **Push** (client đẩy) | **Pull** (client kéo) |
| Dữ liệu | ASCII 7-bit | Không giới hạn |
| Objects | Nhiều object trong 1 message | Mỗi object 1 response |
| Kết nối | Persistent | Persistent (HTTP/1.1) |

### IMAP
- Dùng để **lấy** email từ server về User Agent.
- Lưu message **trên server**, hỗ trợ thư mục, xóa, tìm kiếm.

---

## 4. DNS (Domain Name System)

### DNS là gì?
- Chuyển đổi **hostname ↔ IP address** (và ngược lại).
- Là cơ sở dữ liệu **phân tán & phân cấp**, giao thức tầng Application.
- Dùng **UDP, port 53**.

### Tại sao không dùng DNS tập trung?
Single point of failure + nghẽn cổ chai + không mở rộng được → **không khả thi**.

### Phân cấp DNS
```
Root DNS Servers
       ↓
TLD DNS Servers (.com, .org, .edu, .vn...)
       ↓
Authoritative DNS Servers (amazon.com, google.com...)
       + Local DNS Server (của ISP — không thuộc phân cấp)
```

- **Root:** 13 logical servers, mỗi cái được replicate ~200 lần.
- **TLD (Top-Level Domain):** quản lý `.com`, `.org`, `.edu`, `.vn`...
- **Authoritative:** server DNS của từng tổ chức, lưu bản ghi chính thức.
- **Local DNS:** của ISP, cache kết quả, là điểm đầu tiên client hỏi.

### Hai kiểu truy vấn DNS

| | **Iterated** | **Recursive** |
|---|---|---|
| Cơ chế | Server trả lời "hỏi server kia đi" | Server tự đi hỏi thay client |
| Tải | Phân tán | Tập trung ở server trên |
| Phổ biến | ✅ Thường dùng hơn | Ít phổ biến hơn |

### DNS Records (Resource Records — RR)
Format: `(name, value, type, TTL)`

| Type | name | value |
|---|---|---|
| **A** | hostname | **IP address** |
| **NS** | domain (vd: foo.com) | hostname của authoritative server |
| **CNAME** | alias name | canonical (tên thật) |
| **MX** | domain | tên mail server SMTP |

### DNS Caching
- Sau khi học được mapping → lưu cache, trả lời nhanh hơn.
- Cache có **TTL** (time-to-live) — hết hạn thì xóa.
- Có thể **lỗi thời** nếu IP thay đổi trước khi TTL hết.

### Bảo mật DNS
- **DDoS:** tấn công flood vào root/TLD server.
- **Spoofing/Cache Poisoning:** trả lời DNS giả → chuyển hướng người dùng.
- **DNSSEC:** ký số để xác thực DNS record.

---

## 5. P2P & BitTorrent

### Thời gian phân phối file

$$D_{c-s} \geq \max\left(\frac{NF}{u_s},\ \frac{F}{d_{min}}\right) \quad \text{(Client-Server — tăng tuyến tính theo N)}$$

$$D_{P2P} \geq \max\left(\frac{F}{u_s},\ \frac{F}{d_{min}},\ \frac{NF}{u_s + \sum u_i}\right) \quad \text{(P2P — tăng chậm hơn)}$$

→ **P2P hiệu quả hơn** khi N lớn vì peer mới vừa tiêu thụ vừa đóng góp băng thông.

### BitTorrent
- File chia thành **chunks 256 KB**.
- **Tracker:** theo dõi danh sách peers trong torrent.
- **Chiến lược yêu cầu:** download chunk **rarest first** (hiếm nhất trước).
- **Chiến lược gửi — Tit-for-tat:**
  - Gửi cho **4 peers** đang upload cho mình nhanh nhất.
  - Cứ 30 giây **"optimistically unchoke"** 1 peer ngẫu nhiên.
  - Peer tốt hơn → chia sẻ nhiều hơn → nhận lại nhiều hơn.

---

## 6. Video Streaming & CDN

### DASH (Dynamic Adaptive Streaming over HTTP)
- Video được chia thành **chunks**, mỗi chunk được mã hóa ở **nhiều bitrate khác nhau**.
- **Manifest file:** liệt kê URL của các chunk ở các chất lượng.
- **Client tự quyết định:**
  - Khi nào request chunk.
  - Chất lượng nào phù hợp với băng thông hiện tại.
  - Lấy chunk từ CDN server nào.
- **CBR** (Constant Bit Rate) vs **VBR** (Variable Bit Rate) — VBR hiệu quả hơn.

### CDN (Content Distribution Network)
- **Vấn đề:** Làm sao stream cho hàng triệu người đồng thời?
- **Giải pháp CDN:** Lưu nhiều bản sao nội dung tại **các server phân tán địa lý**.
  - **Enter deep:** đặt server CDN sâu trong access network, gần người dùng (Akamai: 240,000 servers).
  - **Bring home:** ít cluster lớn hơn, đặt gần điểm truy cập (Limelight).
- Client được redirect đến CDN server **gần nhất / ít tắc nghẽn nhất**.

---

## 7. Socket Programming

### UDP Socket
- Không có kết nối (connectionless) — **không handshake**.
- Mỗi datagram phải đính kèm **IP + port đích**.
- Có thể mất gói hoặc nhận sai thứ tự.

```python
# Client UDP
clientSocket = socket(AF_INET, SOCK_DGRAM)
clientSocket.sendto(message, (serverName, serverPort))
reply, serverAddr = clientSocket.recvfrom(2048)
```

### TCP Socket
- **Phải thiết lập kết nối** trước (3-way handshake).
- Server có **welcoming socket** (lắng nghe) và **connection socket** (giao tiếp với từng client).
- Đảm bảo dữ liệu đến **đúng thứ tự, không mất**.

```python
# Server TCP
serverSocket = socket(AF_INET, SOCK_STREAM)
serverSocket.bind(('', port))
serverSocket.listen(1)                        # welcoming socket
connSocket, addr = serverSocket.accept()      # tạo connection socket mới cho mỗi client
```

### So sánh UDP vs TCP Socket

| | **UDP** | **TCP** |
|---|---|---|
| Kết nối | Không | Có (accept/connect) |
| Gắn địa chỉ | Mỗi packet | Chỉ khi connect |
| Độ tin cậy | Không | Có |
| API | `sendto/recvfrom` | `send/recv` |

---

## 🔑 Tóm tắt các con số & từ khóa cần nhớ

| Mục | Cần nhớ |
|---|---|
| HTTP port | **80** (TCP) |
| SMTP port | **25** (TCP) |
| DNS port | **53** (UDP) |
| HTTP stateless | Dùng **cookie** để duy trì trạng thái |
| Non-persistent HTTP | **2RTT + T_trans** mỗi object |
| Conditional GET | `If-Modified-Since` → `304 Not Modified` |
| HOL blocking | HTTP/1.1 → giải quyết bằng **HTTP/2 (framing)** |
| DNS resolution | **Iterated** (phổ biến) vs **Recursive** |
| DNS record types | **A, NS, CNAME, MX** |
| DASH | Client chủ động chọn chất lượng video theo băng thông |
| BitTorrent | Rarest first + **Tit-for-tat** (unchoke 4 best + 1 random) |
| CDN | Enter deep (Akamai) vs Bring home (Limelight) |
| TLS | Mã hóa TCP, implement ở **tầng Application** |