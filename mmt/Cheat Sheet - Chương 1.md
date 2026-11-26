# ⚡ Cheat Sheet: Chương 1 – Mạng máy tính & Internet (Kurose & Ross)

up:: [[Mạng máy tính MOC]]

## 1. Thành phần mạng (Nuts & Bolts)
- **End systems (Hosts):** Thiết bị chạy ứng dụng (laptop, server, IoT).
- **Packet switches:** Router (tầng mạng), Link-layer switch (tầng liên kết). Chuyển tiếp gói tin.
- **Communication links:** Cáp quang, đồng, sóng vô tuyến. Băng thông $R$ (bps).
- **ISP:** Nhà cung cấp dịch vụ mạng (Tier 1, regional, access).

## 2. Chuyển mạch gói vs Chuyển mạch kênh
- **Packet switching:** Chia dữ liệu thành packets. Thống kê ghép kênh (statistical multiplexing). Dễ tắc nghẽn, mất gói.
- **Circuit switching:** Dự trữ tài nguyên (dedicated circuit). Lãng phí nếu im lặng. Dùng trong ĐTDN truyền thống.

## 3. Bốn nguồn Delay
$$d_{\text{nodal}} = d_{\text{proc}} + d_{\text{queue}} + d_{\text{trans}} + d_{\text{prop}}$$
- **Processing ($d_{\text{proc}}$):** Kiểm tra lỗi bit, tìm link ra (< $\mu s$).
- **Queueing ($d_{\text{queue}}$):** Chờ trong buffer router. Phụ thuộc tắc nghẽn.
- **Transmission ($d_{\text{trans}}$):** $L/R$ ($L$ = bits, $R$ = link bandwidth).
- **Propagation ($d_{\text{prop}}$):** $d/s$ ($d$ = chiều dài link, $s \approx 2\times 10^8$ m/s).

## 4. Traffic Intensity & Loss
- $\text{Traffic Intensity} = \frac{La}{R}$ ($a$ = tốc độ gói đến).
  - $\to 0$: Delay nhỏ.
  - $\to 1$: Delay lớn.
  - $> 1$: Delay vô hạn, hàng đợi bùng nổ.
- **Packet Loss:** Buffer hữu hạn. Tràn buffer $\to$ gói bị drop.

## 5. Throughput
- **End-end throughput:** $\min(R_s, R_c, \dots)$ (Bottleneck link = link nhỏ nhất trên đường đi).

## 6. Mô hình 5 tầng (Internet Protocol Stack)
1. **Application:** HTTP, SMTP, DNS (`[[C2. Application layer/2.1 Principles of Network Applications|Chương 2]]`)
2. **Transport:** TCP, UDP (`[[C3. Transport Layer/3.1 Giới thiệu về Transport Layer|Chương 3]]`)
3. **Network:** IP, Routing (`[[C4. Network Layer - Data Plane/4.1 Overview of Network Layer|Chương 4]]`)
4. **Link:** Ethernet, WiFi
5. **Physical:** Bits qua dây dẫn
