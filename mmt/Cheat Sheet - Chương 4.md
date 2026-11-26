# ⚡ Cheat Sheet: Chương 4 – Tầng mạng: Data Plane (Network Layer)

up:: [[Mạng máy tính MOC]]

## 1. Chức năng chính tầng mạng
- **Forwarding (Chuyển tiếp):** Chuyển gói tin từ input link sang output link phù hợp trên 1 router (Cục bộ, Data Plane).
- **Routing (Định tuyến):** Xác định đường đi từ source $\to$ dest qua toàn mạng (Toàn cục, Control Plane).

## 2. Cấu trúc Router (Router Architecture)
- **Input ports:** Line termination $\to$ Physical layer $\to$ Link layer $\to$ Lookup (Forwarding table) $\to$ Switching fabric.
- **Switching fabrics:** Chuyển packet từ input sang output qua memory, bus, hoặc crossbar.
- **Output ports:** Buffer (queueing khi tắc nghẽn), scheduling (FIFO, WFQ).
- **Head-of-the-Line (HOL) Blocking:** Gói ở đầu hàng đợi bị kẹt chặn các gói phía sau.

## 3. IPv4 & Subnetting
- **IPv4 Datagram Header:** 20 bytes (min), TTL, Protocol (TCP=6, UDP=17), Source/Dest IP.
- **Subnet:** Mạng con gồm các thiết bị có chung phần prefix IP.
- **CIDR (Classless Interdomain Routing):** `a.b.c.d/x` ($x$ là số bit network prefix).
- **DHCP (Dynamic Host Configuration Protocol):** Cấp phát IP tự động (DORA: Discover $\to$ Offer $\to$ Request $\to$ ACK).
- **NAT (Network Address Translation):** Chuyển đổi IP nội bộ $\to$ IP public qua NAT translation table (Port mapping).

## 4. IPv6
- **Lý do ra đời:** Cạn kiệt địa chỉ IPv4 (32-bit $\to$ 128-bit).
- **Cải tiến:** Header cố định 40 bytes, không fragmentation ở router, bỏ checksum.

## 5. Generalized Forwarding & SDN (Software-Defined Networking)
- **Match-plus-action:** Match dựa trên các trường header nhiều tầng $\to$ Action (forward, drop, rewrite).
- **OpenFlow API:** Giao diện điều khiển giữa Control Plane (SDN controller) và Data Plane (switches).
- **Middleboxes:** Firewall, NAT, IDS (thực hiện xử lý chuyên sâu gói tin).
