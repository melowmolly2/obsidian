# ⚡ Cheat Sheet: Chương 2 – Tầng ứng dụng (Application Layer)

up:: [[Mạng máy tính MOC]]

## 1. Kiến trúc ứng dụng
- **Client-Server:** Server luôn bật, IP cố định; Client khởi tạo kết nối.
- **P2P:** Không server trung tâm, peer trực tiếp kết nối (BitTorrent). Khả năng mở rộng tốt.

## 2. HTTP (HyperText Transfer Protocol)
- **Non-persistent HTTP:** Mỗi object cần 1 TCP connection riêng (tốn 2RTT/object + handshake).
- **Persistent HTTP:** Tái sử dụng TCP connection cho nhiều object (có/không pipelining).
- **Cookies:** Duy trì trạng thái (stateful session) qua HTTP vô trạng thái (stateless).
- **Web Caching (Proxy):** Giảm response time, giảm traffic đường trục.

## 3. DNS (Domain Name System)
- **Chức năng:** Phân giải tên miền (hostname $\leftrightarrow$ IP address).
- **Cấu trúc phân cấp:** Root servers $\to$ TLD servers (.com, .edu) $\to$ Authoritative servers.
- **Bản ghi DNS (Resource Records):** `(Name, Value, Type, TTL)`.
  - `A`: hostname $\to$ IPv4.
  - `AAAA`: hostname $\to$ IPv6.
  - `CNAME`: alias $\to$ canonical name.
  - `MX`: mail server name.

## 4. Email (SMTP, IMAP, POP3)
- **SMTP:** Đẩy mail từ client $\to$ server và server $\to$ server (Port 25, persistent).
- **IMAP / POP3:** Kéo mail từ server $\to$ client đọc (IMAP đồng bộ trạng thái trên server, POP3 tải về xóa).

## 5. Video Streaming & CDN
- **DASH:** Dynamic Adaptive Streaming over HTTP. Video chia nhỏ thành chunks, client tự động chọn bitrate thích hợp dựa trên băng thông hiện tại.
- **CDN (Content Distribution Network):** Lưu trữ bản sao video/content ở edge servers gần user (Enter deep vs Bring home).
