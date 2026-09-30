Đọc nội dung Chapter 1 để giải thích các khái niệm cho bạn.

Dưới đây là giải thích chi tiết tất cả các khái niệm quan trọng trong **Chương 1: Giới thiệu về Mạng Máy Tính**.

---

## 📡 Chương 1: Giới thiệu Mạng Máy Tính

---

### 1. Internet là gì?

Internet có thể hiểu theo **2 góc nhìn**:

**Góc nhìn "nuts and bolts" (kỹ thuật):**
- Là **"mạng của các mạng"** — hàng tỷ thiết bị kết nối với nhau (PC, điện thoại, máy chủ, IoT...).
- **Host (end system):** các thiết bị đầu cuối chạy ứng dụng (trình duyệt, email...).
- **Packet switches:** thiết bị chuyển tiếp dữ liệu, gồm **router** (tầng mạng) và **switch** (tầng liên kết).
- **Communication links:** các đường truyền vật lý — cáp quang, cáp đồng, sóng radio, vệ tinh. Đặc trưng bởi **bandwidth (băng thông)**.
- **ISP (Internet Service Provider):** nhà cung cấp dịch vụ Internet, kết nối người dùng tới Internet.

**Góc nhìn "services" (dịch vụ):**
- Internet là **hạ tầng cung cấp dịch vụ** cho các ứng dụng: Web, email, video, game, mạng xã hội...
- Cung cấp **API lập trình** để các ứng dụng gửi/nhận dữ liệu qua mạng.

---

### 2. Protocol (Giao thức) là gì?

> **Protocol định nghĩa định dạng, thứ tự của các thông điệp gửi/nhận giữa các thực thể mạng, và các hành động thực hiện khi gửi/nhận thông điệp.**

- Ví dụ: HTTP (web), TCP, IP, WiFi, 4G/5G, Ethernet...
- **RFC (Request for Comments):** tài liệu chuẩn hóa các giao thức Internet.
- **IETF (Internet Engineering Task Force):** tổ chức ban hành các chuẩn Internet.

---

### 3. Cấu trúc Internet

Internet được chia làm 3 phần:

#### 🔵 Network Edge (Biên mạng)
- Là nơi người dùng kết nối: **clients và servers**.
- Servers thường đặt trong **data centers**.

#### 🟢 Access Network (Mạng truy cập)
Cách người dùng kết nối tới Internet:

| Loại | Công nghệ | Tốc độ |
|---|---|---|
| Cable (cáp truyền hình) | HFC (Hybrid Fiber Coax) | 40 Mbps – 1.2 Gbps down |
| DSL (đường dây điện thoại) | DSLAM | 24–52 Mbps down |
| Mạng gia đình | WiFi + Ethernet | 54–1000 Mbps |
| Di động | 4G/5G | hàng chục Mbps |
| Enterprise | Ethernet + WiFi | 100 Mbps – 10 Gbps |
| Data center | Cáp quang tốc độ cao | 10–100 Gbps |

**Phương tiện vật lý (Physical Media):**
- **Guided (có dây):** cáp đôi xoắn (UTP), cáp đồng trục, cáp quang (tốc độ cao, ít nhiễu).
- **Unguided (không dây):** WiFi, 4G/5G, Bluetooth, vệ tinh.

#### 🔴 Network Core (Lõi mạng)
- Là lưới các **router** kết nối với nhau.
- Thực hiện 2 chức năng chính:
  - **Forwarding (chuyển tiếp):** chuyển gói tin từ cổng vào → cổng ra thích hợp **(hành động cục bộ)**.
  - **Routing (định tuyến):** xác định đường đi toàn cục từ nguồn đến đích **(hành động toàn cục, dùng thuật toán định tuyến)**.

---

### 4. Packet Switching vs Circuit Switching

#### 📦 Packet Switching (Chuyển mạch gói)
- Dữ liệu bị chia thành các **gói (packets)**.
- Mỗi gói đi độc lập qua mạng, **chia sẻ tài nguyên** với gói khác.
- **Store-and-forward:** router phải nhận **toàn bộ gói** trước khi chuyển tiếp gói đó.

$$d_{truyền} = \frac{L}{R}$$

*(L = độ dài gói (bits), R = tốc độ đường truyền (bps))*

- **Queuing (xếp hàng):** Khi tốc độ đến > tốc độ xử lý → gói bị **xếp hàng chờ**.
- **Packet loss:** Nếu buffer đầy → gói bị **mất**.
- **Ưu điểm:** dùng tài nguyên hiệu quả, phù hợp dữ liệu bursty.
- **Nhược điểm:** có thể bị trễ và mất gói.

#### 📞 Circuit Switching (Chuyển mạch kênh)
- **Dành riêng tài nguyên** cho toàn bộ cuộc gọi từ đầu đến cuối.
- Hiệu năng **đảm bảo**, nhưng tài nguyên bị lãng phí nếu không dùng.
- Dùng trong mạng điện thoại truyền thống.
- Chia tài nguyên bằng **FDM** (theo tần số) hoặc **TDM** (theo thời gian).

**So sánh:** Với 1 Gbps link, mỗi user dùng 100 Mbps, active 10% thời gian:
- Circuit switching: chỉ phục vụ **10 user**.
- Packet switching: phục vụ **35 user** với xác suất lỗi < 0.0004.

---

### 5. Cấu trúc phân cấp ISP

$$\text{Access ISP} \rightarrow \text{Regional ISP} \rightarrow \text{Tier-1 ISP (AT\&T, Sprint...)}$$

- **IXP (Internet Exchange Point):** điểm để các ISP kết nối trực tiếp với nhau (peering).
- **Content providers** (Google, Facebook) tự xây dựng mạng riêng, bypass Tier-1 ISP để đến gần người dùng hơn.

---

### 6. Hiệu năng mạng: Delay, Loss, Throughput

#### ⏱ Trễ gói (Packet Delay)

$$d_{nodal} = d_{proc} + d_{queue} + d_{trans} + d_{prop}$$

| Thành phần | Ý nghĩa |
|---|---|
| $d_{proc}$ | Xử lý tại router (kiểm tra lỗi, tra bảng định tuyến) — < vài microsec |
| $d_{queue}$ | Chờ trong hàng đợi — phụ thuộc mức độ tắc nghẽn |
| $d_{trans} = L/R$ | Thời gian đẩy toàn bộ gói lên đường truyền |
| $d_{prop} = d/s$ | Thời gian tín hiệu lan truyền vật lý (s ≈ 2×10⁸ m/s) |

**Traffic intensity (cường độ giao thông):**

$$\frac{La}{R} \begin{cases} \approx 0 & \text{trễ nhỏ} \\ \to 1 & \text{trễ lớn} \\ > 1 & \text{trễ vô hạn!} \end{cases}$$

#### 📉 Packet Loss
- Buffer tại router có dung lượng hữu hạn.
- Khi buffer đầy → gói đến sau bị **hủy (dropped)**.
- Gói mất có thể được **gửi lại** bởi node trước, nguồn, hoặc bị mất hẳn.

#### 🚀 Throughput (Thông lượng)
- Là **tốc độ truyền bit** từ sender đến receiver (bps).
- **Bottleneck link:** đường truyền có tốc độ thấp nhất, giới hạn thông lượng đầu cuối.

$$\text{Throughput} = \min(R_s, R_c)$$

---

### 7. Bảo mật mạng

Internet ban đầu không được thiết kế có bảo mật. Các mối đe dọa phổ biến:

| Tấn công | Mô tả |
|---|---|
| **Packet sniffing** | Nghe lén gói tin trên mạng broadcast |
| **IP Spoofing** | Giả mạo địa chỉ IP nguồn |
| **DoS/DDoS** | Làm tràn ngập server bằng traffic giả để từ chối dịch vụ người dùng hợp lệ |

**Phòng thủ:**
- **Authentication** (xác thực danh tính)
- **Encryption** (mã hóa)
- **Integrity check** (chữ ký số)
- **Firewall** (tường lửa)
- **VPN** (mạng riêng ảo)

---

### 8. Mô hình phân lớp (Protocol Layers)

Mạng phức tạp → tổ chức thành **các lớp**, mỗi lớp cung cấp dịch vụ cho lớp trên.

#### Internet Protocol Stack (5 lớp):

| Lớp | Chức năng | Giao thức |
|---|---|---|
| **Application** | Hỗ trợ ứng dụng | HTTP, SMTP, DNS, FTP |
| **Transport** | Truyền dữ liệu process-to-process | TCP, UDP |
| **Network** | Định tuyến datagram nguồn→đích | IP, routing protocols |
| **Link** | Truyền dữ liệu giữa 2 node kề nhau | Ethernet, WiFi, PPP |
| **Physical** | Bit trên đường truyền vật lý | — |

#### Encapsulation (Đóng gói):
Mỗi lớp **bọc thêm header** của mình vào dữ liệu từ lớp trên:

$$M \xrightarrow{\text{Transport}} H_t|M \xrightarrow{\text{Network}} H_n|H_t|M \xrightarrow{\text{Link}} H_l|H_n|H_t|M$$

- **Message** → **Segment** → **Datagram** → **Frame**
- Giống như búp bê Matryoshka (búp bê lồng nhau).

#### Mô hình OSI (7 lớp):
Có thêm 2 lớp so với Internet stack:
- **Presentation:** mã hóa, nén dữ liệu.
- **Session:** đồng bộ hóa phiên truyền.
- Internet hiện đại tích hợp 2 chức năng này vào tầng Application nếu cần.

---

### 9. Lịch sử Internet (tóm tắt)

| Thời kỳ   | Sự kiện nổi bật                                             |
| --------- | ----------------------------------------------------------- |
| 1961–1972 | ARPAnet, lý thuyết chuyển mạch gói, email đầu tiên          |
| 1972–1980 | TCP/IP, Ethernet, mạng liên kết                             |
| 1980–1990 | DNS, FTP, kiểm soát tắc nghẽn TCP                           |
| 1990–2000 | World Wide Web (HTML/HTTP), thương mại hóa Internet         |
| 2005–nay  | 4G/5G, cloud computing, SDN, IoT (~15 tỷ thiết bị năm 2023) |
