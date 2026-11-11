# Chương 2: Lớp Ứng dụng (Application Layer)

> Nguồn: *Computer Networking: A Top-Down Approach, 9th ed.* - Chapter 2

---

## 2.1 Kiến trúc ứng dụng mạng

| Kiến trúc | Đặc điểm | Ví dụ |
|-----------|----------|-------|
| **Client-Server** | Server luôn on, IP cố định, data center, farm server cho scale | Web, Email, DNS |
| **P2P (Peer-to-Peer)** | Không server chuyên dụng, peer = client + server, tự scale | BitTorrent, Bitcoin, IPFS |
| **Hybrid** | Kết hợp cả hai (CDN, login server + P2P data) | Skype (old), Spotify (old) |

---

## 2.2 Giao tiếp giữa tiến trình (Process Communication)

### Socket API
- **Socket** = cửa ngõ giữa ứng dụng và transport layer
- **Address** = IP address + Port number
- **Well-known ports**:
  |Port|Protocol|Service|
  |------|----------|---------|
  | 20/21 | TCP | FTP |
  | 22 | TCP | SSH |
  | 25 | TCP | SMTP |
  | 53 | UDP/TCP | DNS |
  | 80 | TCP | HTTP |
  | 110 | TCP | POP3 |
  | 143 | TCP | IMAP |
  | 443 | TCP | HTTPS |
  | 993 | TCP | IMAPS |
  | 995 | TCP | POP3S |

### Multiplexing/Demultiplexing
- **Transport layer** dùng port để phân biệt tiến trình
- **UDP**: destination port
- **TCP**: 4-tuple (src IP, src port, dst IP, dst port)

---

## 2.3 Dịch vụ vận chuyển ứng dụng cần

| Yêu cầu ứng dụng | Transport phù hợp |
|------------------|-------------------|
| Tin cậy, thứ tự, flow control | **TCP** |
| Độ trễ thấp, mất gói chấp nhận được, multicast | **UDP** |
| An ninh (mã hóa, xác thực, toàn vẹn) | **TLS/SSL** (trên TCP) |
| Tin cậy + An ninh | **TCP + TLS** (HTTPS, SMTPS, IMAPS) |
| Độ trễ thấp + An ninh | **QUIC** (UDP + TLS 1.3 built-in) |

---

## 2.4 Web & HTTP

### Đặc điểm HTTP
- **Request-Response** model
- **Stateless**: Server không lưu state giữa các request
- **Text-based** (HTTP/1.x), **Binary** (HTTP/2, HTTP/3)

### Phiên bản HTTP
| Phiên bản    | Năm  | Đặc điểm chính                                                                  |
| ------------ | ---- | ------------------------------------------------------------------------------- |
| **HTTP/0.9** | 1991 | Chỉ GET, no headers                                                             |
| **HTTP/1.0** | 1996 | Headers, non-persistent (mặc định)                                              |
| **HTTP/1.1** | 1997 | Persistent, pipelining, chunked, Host header, cache control                     |
| **HTTP/2**   | 2015 | Binary framing, multiplexing, header compression (HPACK), server push, priority |
| **HTTP/3**   | 2022 | **QUIC** (UDP), 0-RTT, no head-of-line blocking, connection migration           |

### HTTP Message Format

**Request**:
```
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0
Accept: text/html
Accept-Language: en-US
Connection: keep-alive

[body - optional for GET]
```

**Response**:
```
HTTP/1.1 200 OK
Date: Mon, 10 Nov 2026 10:00:00 GMT
Server: Apache/2.4
Content-Type: text/html; charset=UTF-8
Content-Length: 1234
Cache-Control: max-age=3600

<!DOCTYPE html>...
```

### Status Codes
| Mã | Tên | Ý nghĩa |
|----|-----|---------|
| **200** | OK | Thành công |
| **301** | Moved Permanently | Redirect vĩnh viễn |
| **302** | Found | Redirect tạm thời |
| **304** | Not Modified | Cache hit (Conditional GET) |
| **400** | Bad Request | Lỗi cú pháp |
| **401** | Unauthorized | Cần authentication |
| **403** | Forbidden | Không có quyền |
| **404** | Not Found | Không tìm thấy |
| **500** | Internal Server Error | Lỗi server |
| **503** | Service Unavailable | Server quá tải/bảo trì |

### Cookie & Session (State trên stateless)
```
Server → Set-Cookie: sessionid=abc123; Expires=Wed, 11 Nov 2026 10:00:00 GMT; Secure; HttpOnly; SameSite=Lax
Client → Cookie: sessionid=abc123
```
- **Session cookie**: Hết hạn khi đóng trình duyệt
- **Persistent cookie**: Có `Expires`/`Max-Age`
- **Secure**: Chỉ gửi qua HTTPS
- **HttpOnly**: Không truy cập qua JavaScript (chống XSS)
- **SameSite**: Strict/Lax/None (chống CSRF)

### Web Cache (Proxy Cache)
- **Lợi ích**: Giảm độ trễ user, giảm băng thông origin server, giảm tải Internet backbone
- **Conditional GET**: `If-Modified-Since` / `If-None-Match (ETag)` → **304 Not Modified**

---

## 2.5 Email (Electronic Mail)

### Kiến trúc
```
User Agent (MUA) ←→ Mail Server (MTA) ←→ Mail Server (MTA) ←→ User Agent (MUA)
    ↑                                                               ↑
 SMTP (send)                                                    POP3/IMAP (receive)
```

### Giao thức
| Giao thức | Port | Chức năng | Đặc điểm |
|-----------|------|-----------|----------|
| **SMTP** | 25 (587 submission) | Gửi mail (Push) | TCP, 7-bit ASCII, persistent connection |
| **POP3** | 110 (995 SSL) | Kéo mail về client | Thường xóa trên server, offline access |
| **IMAP** | 143 (993 SSL) | Đồng bộ mail | Giữ mail trên server, folder sync, multiple clients |

### MIME (Multipurpose Internet Mail Extensions)
- Mở rộng cho **non-ASCII**: attachment, UTF-8, HTML email
- **Content-Type**: `text/plain`, `text/html`, `multipart/mixed`, `image/jpeg`, `application/pdf`...
- **Base64 encoding**: Binary → ASCII (33% overhead)

---

## 2.6 DNS (Domain Name System)

### Chức năng
- **Phân giải tên miền** → IP address (A, AAAA record)
- **Phân giải ngược** (PTR record)
- **Mail routing** (MX record)
- **Load balancing** (Round-robin DNS, GeoDNS)
- **Service discovery** (SRV record)

### Kiến trúc phân cấp, phân tán
```
Root (.) → TLD (.com, .vn, .org) → Authoritative (example.com)
```
- **13 Root Server Clusters** (A-M, anycast)
- **TLD Servers**: Verisign (.com), VNNIC (.vn)...
- **Authoritative Servers**: Quản lý zone cụ thể

### Truy vấn DNS
| Loại | Mô tả |
|------|-------|
| **Recursive** | Client yêu cầu resolver giải quyết hết (mặc định stub resolver) |
| **Iterative** | Resolver hỏi lần lượt root → TLD → Authoritative (giải pháp phân tán) |

### DNS Cache & TTL
- **TTL (Time To Live)**: Thời gian cache (giây), giảm tải root/TLD
- **Negative caching**: Cache NXDOMAIN

### Resource Records (RR)
| Type | Mục đích |
|------|----------|
| **A** | IPv4 address |
| **AAAA** | IPv6 address |
| **CNAME** | Canonical name (alias) |
| **MX** | Mail exchanger (priority + hostname) |
| **NS** | Name server (delegation) |
| **TXT** | Text (SPF, DKIM, DMARC, verification) |
| **SOA** | Start of Authority (zone params) |
| **SRV** | Service location (port, priority, weight) |

### Bảo mật DNS
| Cơ chế | Mô tả |
|--------|-------|
| **DNSSEC** | Ký số zone (RRSIG, DNSKEY, DS, NSEC/NSEC3) → chain of trust |
| **DNS over HTTPS (DoH)** | DNS query trong HTTPS (port 443), chống censorship/sniffing |
| **DNS over TLS (DoT)** | DNS query trong TLS (port 853) |
| **QNAME Minimization** | Chỉ gửi phần cần thiết cho authoritative server |

---

## 2.7 P2P File Distribution (BitTorrent)

### Nguyên lý
- File chia thành **pieces** (thường 256 KB - 1 MB)
- **.torrent file / magnet link**: Metadata (piece hashes, tracker URL)
- **Tracker**: Điều phối peer list (HTTP/HTTPS/UDP)
- **DHT (Distributed Hash Table)**: Tracker-less (Kademlia)

### Tit-for-Tat (Công bằng)
- Peer **choke/unchoke** dựa trên upload rate
- **Optimistic unchoke**: Thỉnh thoảng unchoke peer mới
- **Seeders**: Đã tải xong, chỉ upload
- **Leechers**: Đang tải, vừa download vừa upload

---

## 2.8 Video Streaming & CDN

### DASH (Dynamic Adaptive Streaming over HTTP)
- **MPD (Media Presentation Description)**: XML manifest
- **Representations**: Nhiều bitrate/resolution/codec
- **Segments**: Chunk nhỏ (2-10 giây)
- **Adaptive Bitrate (ABR)**: Client tự chọn quality dựa trên bandwidth/buffer

### CDN (Content Delivery Network)
- **Edge servers** đặt gần user (PoP - Point of Presence)
- **Request routing**: DNS-based, Anycast, HTTP redirect
- **Cache hierarchy**: Origin → Regional → Edge
- **Lợi ích**: Giảm latency, giảm origin load, tăng availability, DDoS mitigation

---

## 2.9 Socket Programming

### TCP Socket (Connection-oriented)
```python
# Server
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.bind(('', 12345))
s.listen(5)
conn, addr = s.accept()
data = conn.recv(1024)
conn.send(b'Response')
conn.close()

# Client
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(('server.com', 12345))
s.send(b'Request')
data = s.recv(1024)
s.close()
```

### UDP Socket (Connectionless)
```python
# Server
s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
s.bind(('', 12345))
data, addr = s.recvfrom(1024)
s.sendto(b'Response', addr)

# Client
s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
s.sendto(b'Request', ('server.com', 12345))
data, addr = s.recvfrom(1024)
```

---

## Tóm tắt chương 2

| Chủ đề | Key Points |
|--------|------------|
| **Kiến trúc** | Client-Server vs P2P |
| **Transport needs** | TCP (reliable) vs UDP (fast) vs TLS (secure) |
| **HTTP** | Stateless, persistent, cookies, caching, HTTP/2, HTTP/3 (QUIC) |
| **Email** | SMTP (push), POP3/IMAP (pull), MIME |
| **DNS** | Hierarchical, recursive/iterative, cache, DNSSEC, DoH/DoT |
| **P2P** | BitTorrent: pieces, tracker/DHT, tit-for-tat |
| **Video/CDN** | DASH (MPD + segments), CDN edge caching |
| **Sockets** | TCP (stream) vs UDP (datagram) API |

---

## Liên kết
- [[MỤC LỤC - Lý thuyết Mạng máy tính]]
- [[Chương 1 - Giới thiệu]]
- [[Chương 3 - Lớp Vận chuyển]]