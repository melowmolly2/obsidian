---
tags:
  - mmt/ôn-tập
  - mmt/câu-hỏi
  - mmt/chương-4
---


# 📝 Chương 4 – Network Layer: Data Plane

> Dựa trên giáo trình *Computer Networking: A Top-Down Approach* – Kurose & Ross, 8th ed.
> Nguồn ghi chú: [[../C4. Network Layer - Data Plane/4.1 Overview of Network Layer]] · [[../C4. Network Layer - Data Plane/4.2 What's Inside a Router]] · [[../C4. Network Layer - Data Plane/4.3 The Internet Protocol (IPv4, DHCP, NAT, IPv6)]] · [[../C4. Network Layer - Data Plane/4.4 Generalized Forwarding and SDN]] · [[../C4. Network Layer - Data Plane/4.5 Middleboxes]]

---

## 🔵 Phần A – Lý thuyết (Tự luận)

> [!question] C4-1. Forwarding vs. Routing (Data Plane vs. Control Plane)
> Phân biệt hai chức năng cốt lõi của tầng mạng: **Forwarding** (chuyển tiếp) và **Routing** (định tuyến). Cho biết phạm vi, tốc độ thực thi và ví dụ thực tế minh họa.

> [!success]- 📌 Đáp án & Giải thích
> 
> | Tiêu chí | Forwarding (Chuyển tiếp) | Routing (Định tuyến) |
> |---|---|---|
> | **Mặt phẳng** | **Data Plane** | **Control Plane** |
> | **Định nghĩa** | Di chuyển gói tin từ cổng vào sang cổng ra thích hợp của một router. | Xác định lộ trình (route/path) từ nguồn tới đích trên toàn bộ mạng lưới router. |
> | **Phạm vi** | **Cục bộ (Local, per-router)** | **Toàn mạng (Network-wide)** |
> | **Thời gian** | Cực nhanh: **Nanosecond** (thực thi bằng phần cứng ASIC/FPGA). | Chậm hơn: **Millisecond / Second** (phần mềm thuật toán định tuyến). |
> | **Ví dụ (Analogy)** | Chạy qua một nút giao thông / ngã tư đơn lẻ. | Lập kế hoạch lộ trình cho toàn bộ chuyến đi xa. |
> 
> - **Data plane:** Nhận datagram ở input port, tra bảng chuyển tiếp (Forwarding Table / Flow Table), đẩy qua switching fabric ra output port.
> - **Control plane:** Tính toán và phân phối bảng chuyển tiếp. Có 2 cách tiếp cận:
>   1. *Per-router:* Các router tự chạy thuật toán định tuyến (OSPF, BGP) và trao đổi thông tin với nhau.
>   2. *SDN:* Một remote controller tập trung tính toán bảng luồng và cài đặt xuống router/switch qua phần mềm.

---

> [!question] C4-2. Mô hình Dịch vụ Best-Effort của Internet
> Mô hình dịch vụ **Best-Effort** của Internet đảm bảo những gì? Tại sao một mô hình "không bảo đảm gì" lại thành công vượt bậc so với các mô hình phức tạp như ATM hay Intserv?

> [!success]- 📌 Đáp án & Giải thích
> 
> **Mô hình Best-Effort không bảo đảm bất kỳ điều gì:**
> - Không đảm bảo gói tin chắc chắn tới đích (có thể mất gói).
> - Không đảm bảo thứ tự gói (có thể bị đảo lộn).
> - Không đảm bảo băng thông tối thiểu.
> - Không đảm bảo độ trễ tối đa (delay bound hay jitter).
> 
> **Lý do mô hình Best-Effort thành công và thống trị:**
> 1. **Cơ chế tối giản:** Router lõi mạng không cần lưu trạng thái từng luồng kết nối, thiết bị rẻ, dễ sản xuất, dễ mở rộng quy mô (scalability) ra hàng tỷ thiết bị.
> 2. **Cung cấp băng thông dồi dào (Over-provisioning):** Nâng cấp băng thông liên kết mạng giúp các ứng dụng thời gian thực (VoIP, streaming video) hoạt động "đủ tốt trong phần lớn thời gian".
> 3. **Trí thông minh ở biên mạng:** Bù đắp cho lõi mạng bằng:
>    - Thuật toán TCP Congestion Control ở tầng giao vận.
>    - Các mạng phân phối nội dung (CDN) và Data Center đặt máy chủ sát cạnh người dùng.
>    - Ứng dụng thích ứng tốc độ (như DASH video).

---

> [!question] C4-3. Kiến trúc Router & Chuyển mạch phi tập trung
> Kể tên 4 thành phần chính của một generic router. Giải thích tại sao router hiện đại cần cơ chế **chuyển mạch phi tập trung (decentralized switching)** tại cổng vào?

> [!success]- 📌 Đáp án & Giải thích
> 
> **4 thành phần chính:**
> 1. **Input Ports (Cổng vào):** Nhận tín hiệu bit vật lý, xử lý frame tầng link, tra bảng chuyển tiếp và xếp hàng.
> 2. **Switching Fabric (Cấu trúc chuyển mạch):** Mạng kết nối nội bộ chuyển gói tin từ cổng vào sang cổng ra.
> 3. **Output Ports (Cổng ra):** Nhận gói từ fabric, lưu vào bộ đệm, lập lịch phát gói lên đường truyền vật lý.
> 4. **Routing Processor (CPU định tuyến):** Chạy các giao thức định tuyến (control plane), tính toán bảng chuyển tiếp, quản lý hệ thống.
> 
> **Tại sao cần Chuyển mạch phi tập trung (Decentralized Switching)?**
> - Nếu mỗi gói tin đến cổng vào đều phải hỏi Routing Processor (CPU) để biết cổng ra, CPU sẽ trở thành nút thắt cổ chai nghiêm trọng.
> - Cơ chế phi tập trung: Mỗi input port lưu một **bản sao bóng (shadow copy)** của bảng chuyển tiếp trong bộ nhớ cục bộ. Input port tự tra cứu độc lập ở cấp phần cứng, hoàn thành xử lý gói tin ở **tốc độ đường truyền (line speed)** trong vài nanosecond.

---

> [!question] C4-4. Longest Prefix Matching và TCAM
> Nguyên tắc **Longest Prefix Matching** là gì? Bộ nhớ **TCAM** giải quyết bài toán tra cứu này như thế nào?

> [!success]- 📌 Đáp án & Giải thích
> 
> - **Longest Prefix Matching (Khớp tiền tố dài nhất):** Khi tra cứu địa chỉ IP đích của gói tin trong bảng chuyển tiếp, nếu địa chỉ khớp với nhiều mục (entries), router sẽ chuyển tiếp gói tin theo mục có **số lượng bit tiền tố khớp nhiều nhất (tiền tố dài nhất)**.
> - **Lý do cần:** Dải địa chỉ IP phân bổ không đều đặn theo từng khối riêng biệt; một tổ chức có thể nằm trong một khối địa chỉ tổng hợp lớn nhưng lại có tuyến đường riêng rẽ.
> - **TCAM (Ternary Content Addressable Memory):**
>   - Bộ nhớ tìm kiếm theo nội dung trong **1 chu kỳ xung nhịp ($O(1)$)**, không phụ thuộc vào kích thước bảng chuyển tiếp.
>   - "Ternary" nghĩa là hỗ trợ 3 trạng thái cho mỗi bit: `0`, `1`, và `*` (wildcard/don't care).
>   - Router cấp doanh nghiệp/ISP (như Cisco Catalyst) có thể tra cứu bảng gồm hàng triệu dòng định tuyến trong TCAM mà không bị giảm tốc độ đường truyền.

---

> [!question] C4-5. Head-of-the-Line (HOL) Blocking
> Hiện tượng **HOL Blocking** xảy ra ở đâu trong router? Giải thích nguyên nhân và hậu quả bằng ví dụ.

> [!success]- 📌 Đáp án & Giải thích
> 
> - **Vị trí xảy ra:** Tại hàng đợi ở **Cổng vào (Input Port)** khi tốc độ chuyển mạch chậm hơn tổng tốc độ dữ liệu đến từ các cổng vào.
> - **Nguyên nhân:** Hai cổng vào khác nhau cùng có gói tin ở đầu hàng đợi muốn đi tới cùng **một cổng ra**. Chỉ một gói được đi qua fabric, gói còn lại bị nghẽn lại ở đầu hàng đợi.
> - **Hậu quả (HOL Blocking):** Gói tin bị nghẽn ở đầu hàng đợi sẽ **chặn toàn bộ các gói tin phía sau nó di chuyển**, ngay cả khi các gói phía sau muốn đi tới các cổng ra khác đang hoàn toàn rảnh rỗi!
> - **Ví dụ:** Cổng 1 có Gói A (đến Cổng ra 1) và Gói B (đến Cổng ra 2). Cổng 2 cũng có Gói C (đến Cổng ra 1). Nếu Gói C được ưu tiên qua trước, Gói A bị giữ lại $\to$ Gói B nằm sau Gói A cũng bị kẹt lại theo, dù Cổng ra 2 hoàn toàn rảnh rỗi.

---

> [!question] C4-6. Kích thước Bộ đệm Cổng ra & Bufferbloat
> Router cần bao nhiêu bộ đệm ở cổng ra? So sánh công thức truyền thống RFC 3439 và công thức hiện đại. **Bufferbloat** là gì?

> [!success]- 📌 Đáp án & Giải thích
> 
> - **Công thức truyền thống (RFC 3439):**
>   $$B = \text{RTT} \times C$$
>   *(với $C$ là dung lượng đường truyền, RTT là thời gian khứ hồi điển hình cỡ 250 ms).*
> - **Công thức hiện đại (khi có $N$ luồng TCP cùng qua nút nghẽn):**
>   $$B = \frac{\text{RTT} \times C}{\sqrt{N}}$$
>   *(Nhờ hiệu ứng thống kê trung hòa giữa các luồng TCP độc lập, kích thước đệm có thể giảm đáng kể).*
> - **Bufferbloat (Hiện tượng phình bộ đệm):**
>   - Do giá bộ nhớ rẻ, các nhà sản xuất trang bị bộ đệm router gia đình quá lớn.
>   - Khi xảy ra tắc nghẽn, các bộ đệm khổng lồ này chứa đầy gói tin mà không chịu vứt bỏ (drop), khiến độ trễ hàng đợi tăng vọt từ vài chục ms lên hàng nghìn ms (vài giây!).
>   - Hậu quả: Làm tê liệt các ứng dụng tương tác thời gian thực (game online, gọi video, web browsing) dù đường truyền có tốc độ Mbps rất cao.

---

> [!question] C4-7. Các Giải thuật Lập lịch Gói tin (Packet Scheduling)
> Nêu nguyên lý và so sánh 4 giải thuật lập lịch: **FIFO**, **Priority Scheduling**, **Round Robin (RR)** và **Weighted Fair Queuing (WFQ)**.

> [!success]- 📌 Đáp án & Giải thích
> 
> 1. **FIFO / FCFS:** Gói nào đến trước phát trước. Đơn giản nhất, không phân biệt đối xử lưu lượng.
> 2. **Priority Scheduling:** Phân loại gói thành các hàng đợi có mức ưu tiên khác nhau (High, Low). Luôn gửi gói ở hàng đợi ưu tiên cao trước. Trong cùng một mức ưu tiên: áp dụng FIFO.
> 3. **Round Robin (RR):** Phân loại gói thành nhiều lớp. Server quét tuần hoàn qua từng lớp: gửi 1 gói từ Lớp 1 $\to$ 1 gói từ Lớp 2 $\to$ lặp lại tuần hoàn.
> 4. **Weighted Fair Queuing (WFQ):**
>    - Là dạng tổng quát hóa của Round Robin có trọng số.
>    - Mỗi lớp $i$ được gán một trọng số $w_i$.
>    - Băng thông lớp $i$ nhận được tỉ lệ thuận với trọng số:
>      $$\text{Tỉ lệ băng thông} = \frac{w_i}{\sum_j w_j}$$
>    - **Ưu điểm:** Đảm bảo băng thông tối thiểu cho từng lớp dịch vụ, ngăn chặn một luồng xấu chiếm dụng hết tài nguyên.

---

> [!question] C4-8. Cấu trúc IPv4 Datagram
> Kể tên các trường quan trọng trong IPv4 header. Nêu vai trò của: `TTL`, `Protocol`, `Header Checksum`, và `Type of Service (ToS)`.

> [!success]- 📌 Đáp án & Giải thích
> 
> - Header IPv4 tối thiểu dài **20 bytes** (5 từ 32-bit).
> - **Time to Live (TTL):** Giới hạn thời gian sống / số hop của gói tin trên mạng (giảm 1 tại mỗi router). Ngăn chặn gói tin chạy vòng lặp vĩnh viễn khi mạng có lỗi định tuyến. Khi $\text{TTL} = 0$, router hủy gói và gửi thông báo ICMP về nguồn.
> - **Protocol:** Xác định giao thức tầng giao vận tiếp nhận payload khi tới host đích: TCP (`6`), UDP (`17`), ICMP (`1`).
> - **Header Checksum:** Kiểm tra tính toàn vẹn của IPv4 header (không kiểm tra data). Phải tính toán lại tại mỗi router vì trường TTL bị giảm đi 1.
> - **Type of Service (ToS):** Phục vụ phân loại chất lượng dịch vụ (Diffserv - 6 bits) và cảnh báo tắc nghẽn sớm (ECN - 2 bits).

---

> [!question] C4-9. Quy trình 4 bước của DHCP
> Trình bày chi tiết 4 bước trong quá trình cấp phát địa chỉ IP động của **DHCP**. Tại sao cần bước Request thứ ba khi Server đã Offer ở bước hai?

> [!success]- 📌 Đáp án & Giải thích
> 
> **4 bước bắt tay:**
> 1. **DHCP Discover:** Client mới gia nhập gửi broadcast (`src: 0.0.0.0:68`, `dest: 255.255.255.255:67`) để tìm máy chủ DHCP.
> 2. **DHCP Offer:** Một hoặc nhiều DHCP server phản hồi broadcast đề xuất cấp địa chỉ IP (`yiaddr`), thời hạn cho thuê (lease time), và transaction ID.
> 3. **DHCP Request:** Client gửi broadcast chọn chính thức một trong các server đã offer, thông báo địa chỉ IP mà nó muốn nhận.
> 4. **DHCP ACK:** Server được chọn gửi broadcast xác nhận cấp phát kèm theo các thông số cấu hình: Default Gateway, DNS Server, Subnet Mask.
> 
> **Tại sao cần bước Request thứ 3?**
> - Vì trên cùng một mạng LAN có thể có **nhiều DHCP server cùng phản hồi Offer**.
> - Bước Request gửi broadcast công khai báo cho server được chọn biết client đã chấp nhận, đồng thời ngầm báo cho các DHCP server khác biết rằng lời mời của họ bị từ chối để họ **thu hồi và tái sử dụng địa chỉ IP đã offer** cho thiết bị khác.

---

> [!question] C4-10. NAT (Network Address Translation)
> NAT giải quyết vấn đề gì? Cách thức hoạt động của bảng biên dịch NAT? Nêu các ưu điểm và các điểm gây tranh cãi về mặt kiến trúc mạng.

> [!success]- 📌 Đáp án & Giải thích
> 
> - **Mục tiêu:** Cho phép hàng trăm thiết bị trong mạng nội bộ (dùng dải IP riêng: `10.0.0.0/8`, `172.16.0.0/12`, `192.168.0.0/16`) cùng chia sẻ **một địa chỉ IPv4 công cộng duy nhất** ra ngoài Internet.
> - **Cách hoạt động:**
>   - Gói đi ra: Router NAT thay thế `(Source IP nội bộ, Source Port)` bằng `(NAT IP công cộng, Port mới)` và ghi vào **Bảng NAT (NAT Table)**.
>   - Gói đi vào: Router NAT kiểm tra cổng đích, tra bảng NAT và đổi lại thành `(IP nội bộ, Port gốc)`.
> - **Ưu điểm:** Tiết kiệm không gian IPv4; bảo mật tự nhiên (ẩn cấu trúc mạng nội bộ trước bên ngoài); đổi ISP không cần cấu hình lại IP máy tính con.
> - **Tranh cãi (Controversies):**
>   1. *Vi phạm mô hình phân tầng:* Thiết bị Layer 3 (router) lại đọc và sửa số Port thuộc Layer 4 (Transport).
>   2. *Vi phạm nguyên lý End-to-End:* Các nút mạng trung gian can thiệp sâu vào nội dung truyền thông.
>   3. *Khó khăn khi thiết lập kết nối từ ngoài vào (NAT Traversal):* Bên ngoài không thể chủ động khởi tạo kết nối tới server nằm sau NAT nếu không có cấu hình Port Forwarding, UPnP, hoặc Relay Server trung gian.

---

> [!question] C4-11. IPv6 và Kỹ thuật Tunneling
> Nêu các điểm cải tiến cốt lõi của IPv6 so với IPv4. Giải thích cơ chế **Đường hầm (Tunneling)** dùng trong quá trình chuyển đổi từ IPv4 sang IPv6.

> [!success]- 📌 Đáp án & Giải thích
> 
> **Cải tiến của IPv6:**
> - **Không gian địa chỉ 128-bit:** Khoảng $3.4 \times 10^{38}$ địa chỉ, giải quyết vĩnh viễn nguy cơ cạn kiệt IP.
> - **Header kích thước cố định 40 bytes:** Giúp router phần cứng xử lý nhanh hơn nhiều.
> - **Bỏ trường Checksum:** Tăng tốc chuyển tiếp (tầng liên kết và giao vận đã kiểm tra lỗi).
> - **Bỏ phân mảnh tại Router:** Router không chia nhỏ gói; nếu gói lớn hơn MTU, router gửi ICMPv6 *"Packet Too Big"* về nguồn để bên gửi tự điều chỉnh.
> - **Flow Label:** Hỗ trợ nhận diện và ưu tiên luồng dữ liệu thời gian thực.
> 
> **Cơ chế Tunneling (Đường hầm):**
> - Không thể nâng cấp đồng loạt mọi router trên thế giới cùng một lúc ("flag day" bất khả thi).
> - Khi một gói tin IPv6 cần đi qua một vùng mạng IPv4 trung gian, router biên sẽ **đóng gói toàn bộ IPv6 datagram vào trong trường dữ liệu của một IPv4 datagram** (*"packet within a packet"*).
> - Các router IPv4 ở giữa chuyển tiếp gói tin như một IPv4 datagram bình thường. Đến đầu ra của đường hầm, router đích bóc tách vỏ IPv4 và trả lại IPv6 datagram nguyên vẹn.

---

> [!question] C4-12. Generalized Forwarding & OpenFlow
> Mô hình **Match-plus-Action** thống nhất các thiết bị mạng truyền thống (Router, L2 Switch, Firewall, NAT) như thế nào trong chuẩn OpenFlow?

> [!success]- 📌 Đáp án & Giải thích
> 
> Trong mạng SDN/OpenFlow, mọi thiết bị chuyển mạch đều được trừu tượng hóa bằng **Bảng luồng (Flow Table)** với nguyên lý Match-plus-Action:
> 
> | Thiết bị truyền thống | Trường so khớp (Match) | Hành động thực thi (Action) |
> |---|---|---|
> | **Router** | Tiền tố IP đích dài nhất (Destination IP prefix) | Chuyển tiếp ra cổng xuất tương ứng |
> | **L2 Switch** | Địa chỉ MAC đích (Destination MAC) | Chuyển tiếp ra cổng hoặc Flood |
> | **Firewall** | Địa chỉ IP + Cổng dịch vụ TCP/UDP | Permit (Cho phép) hoặc Drop (Loại bỏ) |
> | **NAT** | Địa chỉ IP + Cổng dịch vụ | Rewrite (Sửa lại IP và số Port) |
> 
> $\implies$ Thay vì cần 4 loại phần cứng chuyên dụng khác nhau, người quản trị mạng chỉ cần một loại OpenFlow switch duy nhất và lập trình các quy tắc (flow rules) từ xa qua SDN Controller.

---

> [!question] C4-13. Middleboxes và Nguyên lý End-to-End
> Middlebox là gì (theo RFC 3234)? Nêu nội dung **Nguyên lý Đầu-Cuối (The End-to-End Argument)** của Saltzer, Reed và Clark (1981) và ý nghĩa của nó đối với thiết kế mạng.

> [!success]- 📌 Đáp án & Giải thích
> 
> - **Định nghĩa Middlebox (RFC 3234):** Bất kỳ thiết bị trung gian nào thực hiện các chức năng ngoài chức năng tiêu chuẩn của một IP router thông thường trên đường truyền dữ liệu giữa nguồn và đích (ví dụ: NAT, Firewall, Load Balancer, Cache, IDS).
> - **Nội dung Nguyên lý End-to-End (1981):**
>   > *"Một chức năng chỉ có thể được triển khai hoàn chỉnh và chính xác khi có sự hiểu biết và hỗ trợ của ứng dụng nằm tại các điểm đầu cuối của hệ thống truyền thông. Do đó, việc cung cấp chức năng đó như một đặc tính của bản thân hệ thống truyền thông là không khả thi."*
> - **Ý nghĩa thiết kế:**
>   - Lõi mạng (router) nên giữ ở mức **tối giản, trung lập và chuyển tiếp gói tin nhanh nhất có thể**.
>   - Không nên nhồi nhét các tính năng phức tạp (như truyền tin cậy từng chặng hop-by-hop) vào lõi mạng vì ứng dụng ở đầu cuối đằng nào cũng phải tự kiểm tra lỗi lại từ đầu.
>   - Sự xuất hiện ồ ạt của Middlebox ở lõi mạng hiện đại đã vi phạm nguyên lý này, tạo nên hiện tượng phình to vòng eo đồng hồ cát ("love handles"), nhưng lại là sự đánh đổi thực dụng để giải quyết bài toán cạn kiệt IP (NAT) và an ninh mạng (Firewall).

---

## 🟢 Phần B – Trắc nghiệm Nhanh

> [!question] TN-1. Chức năng nào sau đây thuộc về Data Plane của tầng mạng?
> A. Tính toán đường đi ngắn nhất bằng thuật toán Dijkstra  
> B. Tra cứu bảng chuyển tiếp và đưa gói tin từ cổng vào sang cổng ra  
> C. Trao đổi thông điệp OSPF giữa các router  
> D. Cài đặt luật định tuyến từ SDN controller xuống switch qua mạng  

> [!success]- 📌 Đáp án: **B**
> Data plane là chức năng cục bộ, phần cứng nanosecond: nhận gói tin và chuyển tiếp từ input port sang output port. Các phương án A, C, D đều thuộc về Control Plane.

---

> [!question] TN-2. Tại sao router dùng thuật toán Longest Prefix Matching thay vì Exact Matching?
> A. Vì bộ nhớ RAM không đủ để chứa địa chỉ 32-bit  
> B. Để cho phép gom cụm tuyến đường (route aggregation) và định tuyến phân cấp linh hoạt  
> C. Vì địa chỉ IP không có cấu trúc  
> D. Để giảm thời gian xử lý của bộ vi xử lý CPU  

> [!success]- 📌 Đáp án: **B**
> Nhờ Longest Prefix Matching, ISP có thể quảng bá một dải mạng lớn gom cụm (`/20`), trong khi các tổ chức con có dải chi tiết hơn (`/23`) vẫn được định tuyến chính xác tới đích mà không làm bùng nổ kích thước bảng định tuyến Internet.

---

> [!question] TN-3. Hiện tượng Head-of-the-Line (HOL) Blocking xảy ra tại đâu trong router?
> A. Hàng đợi tại cổng ra (Output port queue)  
> B. Hàng đợi tại cổng vào (Input port queue)  
> C. Bộ vi xử lý định tuyến (Routing processor)  
> D. Bên trong cấu trúc chuyển mạch (Switching fabric)  

> [!success]- 📌 Đáp án: **B**
> HOL Blocking xảy ra khi gói tin đứng đầu hàng đợi cổng vào bị nghẽn ở cổng ra, chặn toàn bộ các gói tin phía sau nó di chuyển.

---

> [!question] TN-4. Trường nào sau đây có mặt trong header IPv4 nhưng đã BỊ LOẠI BỎ hoàn toàn trong header IPv6 cơ bản?
> A. Hop Limit  
> B. Next Header  
> C. Header Checksum  
> D. Version  

> [!success]- 📌 Đáp án: **C**
> IPv6 đã loại bỏ trường **Header Checksum** (để tăng tốc độ xử lý tại router) và loại bỏ trường phân mảnh ra khỏi header chính (chuyển sang extension header).

---

> [!question] TN-5. Trong OpenFlow 1.0, một Flow Entry KHÔNG bao gồm thành phần nào sau đây?
> A. Match (Các trường header so khớp)  
> B. Action (Hành động thực thi cho gói khớp)  
> C. Counters / Stats (Bộ đếm thống kê gói và byte)  
> D. Subnet Mask Calculator (Bộ tính toán mặt nạ mạng con)  

> [!success]- 📌 Đáp án: **D**
> Một flow entry chuẩn gồm: Match fields, Actions, Counters/Stats, Priority, Timeout, Cookie.

---

> [!question] TN-6. Quy tắc nào sau đây thuộc 3 quy tắc "Bright Line" về Net Neutrality của FCC 2015?
> A. No Encryption  
> B. No Paid Prioritization  
> C. Mandatory Caching  
> D. Open Source Routing  

> [!success]- 📌 Đáp án: **B**
> 3 quy tắc Bright Line của FCC gồm: *No Blocking* (Không chặn), *No Throttling* (Không bóp băng thông), và *No Paid Prioritization* (Không bán làn ưu tiên).

---

## 🟣 Phần C – Bài tập Vận dụng & Tính toán

### BT1. Bài toán Phân mảnh IPv4 Datagram

> [!question] Đề bài
> Một IP datagram có tổng kích thước $3500\text{ bytes}$ (trong đó có $20\text{ bytes}$ IPv4 header và $3480\text{ bytes}$ dữ liệu) đi vào liên kết mạng có $\text{MTU} = 1000\text{ bytes}$.
> 1. Datagram gốc được chia thành bao nhiêu mảnh (fragments)?
> 2. Xác định các thông số cho từng mảnh: `Total Length`, `Identification`, `MF Flag`, và `Fragment Offset`.

> [!success]- 📌 Lời giải chi tiết
> 
> **Bước 1: Tính lượng dữ liệu tối đa mỗi mảnh có thể mang**
> - Kích thước frame tối đa: $\text{MTU} = 1000\text{ bytes}$.
> - Header mỗi mảnh: $20\text{ bytes}$.
> - Dữ liệu tối đa lý thuyết: $1000 - 20 = 980\text{ bytes}$.
> - Vì trường **Fragment Offset** tính theo đơn vị khối **8 bytes**, lượng data trong mỗi mảnh (trừ mảnh cuối) **bắt buộc phải chia hết cho 8**:
>   $$\lfloor 980 / 8 \rfloor \times 8 = 122 \times 8 = 976\text{ bytes}$$
> - Vậy mỗi mảnh trung gian chứa tối đa **976 bytes** data.
> 
> **Bước 2: Phân chia 3480 bytes dữ liệu:**
> - Mảnh 1: chứa $976\text{ bytes}$ (bytes $0 \to 975$). Còn lại: $3480 - 976 = 2504\text{ bytes}$.
> - Mảnh 2: chứa $976\text{ bytes}$ (bytes $976 \to 1951$). Còn lại: $2504 - 976 = 1528\text{ bytes}$.
> - Mảnh 3: chứa $976\text{ bytes}$ (bytes $1952 \to 2927$). Còn lại: $1528 - 976 = 552\text{ bytes}$.
> - Mảnh 4: chứa $552\text{ bytes}$ còn lại (bytes $2928 \to 3479$).
> 
> $\implies$ Datagram gốc được chia thành **4 mảnh**.
> 
> **Bước 3: Lập bảng thông số từng mảnh:**
> 
> | Mảnh | Total Length (bytes) | Data length (bytes) | Identification | MF Flag | Fragment Offset |
> |---|---|---|---|---|---|
> | **Mảnh 1** | $976 + 20 = \mathbf{996}$ | 976 | `x` | **1** | $0 / 8 = \mathbf{0}$ |
> | **Mảnh 2** | $976 + 20 = \mathbf{996}$ | 976 | `x` | **1** | $976 / 8 = \mathbf{122}$ |
> | **Mảnh 3** | $976 + 20 = \mathbf{996}$ | 976 | `x` | **1** | $(976 + 976) / 8 = \mathbf{244}$ |
> | **Mảnh 4** | $552 + 20 = \mathbf{572}$ | 552 | `x` | **0** | $(976 \times 3) / 8 = \mathbf{366}$ |

---

### BT2. Bài toán Longest Prefix Matching

> [!question] Đề bài
> Cho bảng chuyển tiếp của một router như sau:
> 
> | Tiền tố địa chỉ đích (Prefix) | Cổng ra (Interface) |
> |---|---|
> | `200.16.0.0 / 16` | Cổng `1` |
> | `200.16.64.0 / 18` | Cổng `2` |
> | `200.16.64.0 / 20` | Cổng `3` |
> | `Mặc định (Default)` | Cổng `4` |
> 
> Xác định cổng ra cho các gói tin có địa chỉ IP đích sau:
> 1. Gói tin A: `200.16.68.10`
> 2. Gói tin B: `200.16.100.5`
> 3. Gói tin C: `200.16.32.1`
> 4. Gói tin D: `198.51.100.1`

> [!success]- 📌 Lời giải chi tiết
> 
> Chuyển đổi các tiền tố sang dạng nhị phân ở octet thứ 3:
> - Cổng 1: `200.16.0.0 / 16` $\to$ Khớp 16 bits đầu (`200.16.***`).
> - Cổng 2: `200.16.64.0 / 18` $\to$ Octet 3: $64 = \mathbf{01}000000_2$. Khớp 18 bits đầu (`200.16.01******`).
> - Cổng 3: `200.16.64.0 / 20` $\to$ Octet 3: $64 = \mathbf{0100}0000_2$. Khớp 20 bits đầu (`200.16.0100****`).
> 
> **Phân tích từng gói:**
> 1. **Gói A (`200.16.68.10`):**
>    - Octet 3: $68 = \mathbf{0100}0100_2$.
>    - Khớp Cổng 1 (/16), Cổng 2 (/18: `01`), và Cổng 3 (/20: `0100`).
>    - Tiền tố dài nhất là `/20` $\implies$ **Chọn Cổng 3**.
> 2. **Gói B (`200.16.100.5`):**
>    - Octet 3: $100 = \mathbf{01}100100_2$.
>    - Khớp Cổng 1 (/16) và Cổng 2 (/18: `01`). Không khớp Cổng 3 (/20 cần `0100`, ở đây là `0110`).
>    - Tiền tố dài nhất là `/18` $\implies$ **Chọn Cổng 2**.
> 3. **Gói C (`200.16.32.1`):**
>    - Octet 3: $32 = \mathbf{00}100000_2$.
>    - Khớp Cổng 1 (/16). Không khớp Cổng 2 hay Cổng 3 (cần bắt đầu bằng `01`).
>    - $\implies$ **Chọn Cổng 1**.
> 4. **Gói D (`198.51.100.1`):**
>    - Không khớp bất kỳ tiền tố nào của `200.16.*`.
>    - $\implies$ **Chọn Cổng 4 (Mặc định)**.

---

### BT3. Bài toán Phân chia Mạng con CIDR

> [!question] Đề bài
> Một tổ chức được cấp khối địa chỉ `192.168.1.0/24`. Người quản trị cần chia khối này thành 3 mạng con (Subnets) để cấp cho 3 phòng ban:
> - Phòng ban A: Cần tối đa 100 hosts.
> - Phòng ban B: Cần tối đa 50 hosts.
> - Phòng ban C: Cần tối đa 25 hosts.
> 
> Hãy xác định: Subnet address, Subnet mask (dạng `/x`), Dải IP sử dụng được cho host, và Địa chỉ Broadcast cho từng phòng ban.

> [!success]- 📌 Lời giải chi tiết
> 
> **Nguyên tắc phân bổ:** Cấp phát cho mạng cần nhiều host nhất trước để tránh phân mảnh không gian địa chỉ.
> 
> 1. **Phòng ban A (cần 100 hosts):**
>    - Cần $2^h - 2 \ge 100 \implies h = 7$ bits host ($2^7 - 2 = 126$ hosts).
>    - Prefix: $32 - 7 = \mathbf{/25}$. Subnet mask: `255.255.255.128`.
>    - **Subnet Address:** `192.168.1.0/25`
>    - **Dải IP host:** `192.168.1.1` $\to$ `192.168.1.126`
>    - **Broadcast:** `192.168.1.127`
> 
> 2. **Phòng ban B (cần 50 hosts):**
>    - Không gian còn lại bắt đầu từ `192.168.1.128`.
>    - Cần $2^h - 2 \ge 50 \implies h = 6$ bits host ($2^6 - 2 = 62$ hosts).
>    - Prefix: $32 - 6 = \mathbf{/26}$. Subnet mask: `255.255.255.192`.
>    - **Subnet Address:** `192.168.1.128/26`
>    - **Dải IP host:** `192.168.1.129` $\to$ `192.168.1.190`
>    - **Broadcast:** `192.168.1.191`
> 
> 3. **Phòng ban C (cần 25 hosts):**
>    - Không gian còn lại bắt đầu từ `192.168.1.192`.
>    - Cần $2^h - 2 \ge 25 \implies h = 5$ bits host ($2^5 - 2 = 30$ hosts).
>    - Prefix: $32 - 5 = \mathbf{/27}$. Subnet mask: `255.255.255.224`.
>    - **Subnet Address:** `192.168.1.192/27`
>    - **Dải IP host:** `192.168.1.193` $\to$ `192.168.1.222`
>    - **Broadcast:** `192.168.1.223`
>    - *(Dải `192.168.1.224/27` còn lại dự phòng cho tương lai).*

---

### BT4. Bài toán Lập lịch Weighted Fair Queuing (WFQ)

> [!question] Đề bài
> Một đường truyền ra có băng thông $R = 60\text{ Mbps}$ dùng bộ lập lịch WFQ phục vụ 3 lớp lưu lượng với các trọng số tương ứng:
> - Lớp 1 (Video streaming): trọng số $w_1 = 3$
> - Lớp 2 (Web traffic): trọng số $w_2 = 2$
> - Lớp 3 (File download): trọng số $w_3 = 1$
> 
> 1. Khi cả 3 lớp đều có gói tin liên tục trong hàng đợi, băng thông mỗi lớp nhận được là bao nhiêu?
> 2. Giả sử Lớp 1 tạm thời không có gói tin nào đến, băng thông của Lớp 2 và Lớp 3 sẽ được điều chỉnh thế nào?

> [!success]- 📌 Lời giải chi tiết
> 
> **Câu 1: Cả 3 lớp cùng hoạt động:**
> - Tổng trọng số: $\sum w_j = w_1 + w_2 + w_3 = 3 + 2 + 1 = 6$.
> - Băng thông Lớp 1:
>   $$R_1 = \frac{w_1}{\sum w_j} \times R = \frac{3}{6} \times 60\text{ Mbps} = \mathbf{30\text{ Mbps}}$$
> - Băng thông Lớp 2:
>   $$R_2 = \frac{w_2}{\sum w_j} \times R = \frac{2}{6} \times 60\text{ Mbps} = \mathbf{20\text{ Mbps}}$$
> - Băng thông Lớp 3:
>   $$R_3 = \frac{w_3}{\sum w_j} \times R = \frac{1}{6} \times 60\text{ Mbps} = \mathbf{10\text{ Mbps}}$$
> 
> **Câu 2: Lớp 1 không có dữ liệu (chỉ còn Lớp 2 và Lớp 3):**
> - WFQ là cơ chế "work-conserving" (không để đường truyền nhàn rỗi nếu còn gói cần gửi).
> - Tổng trọng số đang hoạt động: $w_2 + w_3 = 2 + 1 = 3$.
> - Băng thông Lớp 2 được phân bổ lại:
>   $$R'_2 = \frac{2}{3} \times 60\text{ Mbps} = \mathbf{40\text{ Mbps}}$$
> - Băng thông Lớp 3 được phân bổ lại:
>   $$R'_3 = \frac{1}{3} \times 60\text{ Mbps} = \mathbf{20\text{ Mbps}}$$

---
📚 *Giáo trình: Computer Networking: A Top-Down Approach, 8th ed. – Kurose & Ross*

---

## Điều hướng
up:: [[../Mạng máy tính MOC]]
prev:: [[C3 – Câu hỏi ôn tập]]
