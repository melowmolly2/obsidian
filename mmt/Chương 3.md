Mình sẽ đọc file PDF trước để tóm tắt đúng nội dung chương 3.Dưới đây là phần lý thuyết cần nhớ của chương 3 (Transport Layer, Kurose & Ross, bản 8, 154 slide), mình gom theo thứ tự các mục trong chương.

## 1. Dịch vụ tầng giao vận

- Tầng giao vận cung cấp **truyền thông logic giữa các tiến trình** trên các host khác nhau. Tầng mạng (IP) thì truyền thông giữa các **host**.
- Bên gửi chia message của ứng dụng thành segment. Bên nhận ghép segment lại thành message rồi chuyển lên tầng ứng dụng.
- **TCP**: tin cậy, đúng thứ tự, có kiểm soát tắc nghẽn, kiểm soát luồng, có thiết lập kết nối.
- **UDP**: không tin cậy, có thể đến sai thứ tự, là bản mở rộng "tối giản" của IP best-effort.
- Cả hai đều **không đảm bảo** độ trễ hay băng thông.

## 2. Ghép kênh / phân kênh (mux/demux)

- **Mux** (bên gửi): lấy dữ liệu từ nhiều socket và thêm header tầng giao vận.
- **Demux** (bên nhận): dùng thông tin header để đưa segment đến đúng socket.
- **UDP** phân kênh chỉ bằng **dest port**. Các gói khác source IP hoặc source port nhưng cùng dest port vẫn vào **cùng một socket**.
- **TCP** phân kênh bằng **bộ 4 giá trị**: (source IP, source port, dest IP, dest port). Mỗi client kết nối đến server có một socket riêng.
- Ví dụ trong slide: 3 segment cùng đến (B, port 80) nhưng được phân vào 3 socket khác nhau.

## 3. UDP

- **Lý do dùng UDP**: không cần bắt tay (không tốn RTT), không lưu trạng thái kết nối, header nhỏ, không bị giới hạn bởi kiểm soát tắc nghẽn.
- **Ứng dụng**: streaming multimedia, DNS, SNMP, HTTP/3.
- Nếu cần tin cậy trên UDP thì phải thêm vào ở tầng ứng dụng (như QUIC).
- **Header UDP**: source port, dest port, length, checksum (mỗi trường 16 bit).
- **Internet checksum**:
    - Coi nội dung segment như dãy số nguyên 16 bit, cộng theo kiểu **bù 1 (one's complement)**.
    - Nếu có nhớ (carry) ở bit cao nhất thì cộng lại vào kết quả (wraparound).
    - Checksum = bù 1 của tổng.
    - Bên nhận tính lại và so sánh. Không khớp thì có lỗi. Khớp thì **chưa chắc không lỗi**, vì hai bit đổi ngược chiều nhau có thể không làm đổi tổng, nên bảo vệ yếu.

## 4. Nguyên lý truyền dữ liệu tin cậy (rdt)

Bên gửi và bên nhận **không biết trạng thái của nhau** nếu không có message trao đổi. Đó là lý do cần giao thức.

|Phiên bản|Kênh giả định|Cơ chế thêm vào|
|---|---|---|
|rdt1.0|Hoàn toàn tin cậy|Không cần gì|
|rdt2.0|Có lỗi bit|Checksum, ACK, NAK, truyền lại (**stop-and-wait**)|
|rdt2.1|ACK/NAK cũng có thể lỗi|**Số thứ tự** (chỉ cần 0 và 1), bên nhận loại gói trùng|
|rdt2.2|Giống 2.1, không dùng NAK|Gửi ACK của gói cuối nhận đúng (kèm seq #). **Duplicate ACK** = NAK. TCP dùng cách này|
|rdt3.0|Có lỗi và **mất gói**|Thêm **timer**, truyền lại khi timeout|

**Hiệu suất stop-and-wait:**

$$U_{sender}=\frac{L/R}{RTT+L/R}$$

Ví dụ trong slide: liên kết 1 Gbps, trễ lan truyền 15 ms, gói 8000 bit:

- $D_{trans}=\dfrac{L}{R}=\dfrac{8000}{10^9}=8\ \mu s$
- $U_{sender}=\dfrac{0.008}{30.008}\approx 0.00027$, nghĩa là rất tệ.

**Pipelining**: gửi nhiều gói chưa được ACK cùng lúc, nên cần tăng dải seq # và có bộ đệm. Với 3 gói thì $U_{sender}=\dfrac{3L/R}{RTT+L/R}\approx 0.0008$, tức tăng 3 lần.

### Go-Back-N (GBN)

- **Bên gửi**: cửa sổ tối đa $N$ gói liên tiếp chưa ACK; dùng **ACK tích lũy** $ACK(n)$ (xác nhận mọi gói đến $n$); **một timer** cho gói cũ nhất.
- Khi **timeout(n)**: gửi lại gói $n$ và **tất cả gói sau nó** trong cửa sổ.
- **Bên nhận**: chỉ nhớ `rcv_base` (hoặc `expectedseqnum`); gói sai thứ tự thì **loại bỏ** và gửi lại ACK của gói đúng thứ tự cao nhất.

### Selective Repeat (SR)

- Bên nhận **ACK riêng từng gói** nhận đúng, **đệm** gói lệch thứ tự rồi chuyển lên theo đúng thứ tự.
- Bên gửi có **timer riêng cho mỗi gói**, chỉ gửi lại **đúng gói** bị timeout.
- Gói $n$ trong $[rcvbase-N,\ rcvbase-1]$ vẫn phải gửi lại $ACK(n)$.
- **Nghịch lý kích thước cửa sổ**: nếu seq # dùng $k$ bit thì cần $N \le 2^{k-1}$ (cửa sổ tối đa bằng **một nửa** không gian seq #). Ví dụ slide: seq # 0–3 mà cửa sổ = 3 thì bên nhận không phân biệt được gói mới và gói gửi lại.

## 5. TCP

### Đặc điểm

Điểm-điểm; luồng byte tin cậy, đúng thứ tự, không có ranh giới message; full duplex; có MSS; ACK tích lũy; pipelining; hướng kết nối (bắt tay); có kiểm soát luồng.

### Seq # và ACK

- **Seq #** = số thứ tự (trong luồng byte) của **byte đầu tiên** trong segment.
- **ACK #** = seq # của **byte tiếp theo mong đợi**.
- Ví dụ telnet trong slide: A gửi `Seq=42, ACK=79, 'C'`, B trả `Seq=79, ACK=43`, A trả `Seq=43, ACK=80`.
- Cách xử lý segment sai thứ tự do bên cài đặt quyết định.

### Ước lượng RTT và timeout

$$EstimatedRTT=(1-\alpha)\cdot EstimatedRTT+\alpha\cdot SampleRTT,\quad \alpha=0.125$$

$$DevRTT=(1-\beta)\cdot DevRTT+\beta\cdot|SampleRTT-EstimatedRTT|,\quad \beta=0.25$$

$$TimeoutInterval=EstimatedRTT+4\cdot DevRTT$$

SampleRTT **bỏ qua** các segment bị truyền lại.

### Sinh ACK ở bên nhận (RFC 5681)

|Sự kiện|Hành động|
|---|---|
|Segment đúng thứ tự, mọi thứ trước đó đã ACK|**Delayed ACK**: chờ tối đa 500 ms|
|Segment đúng thứ tự, có 1 ACK đang chờ|Gửi ngay **1 ACK tích lũy** cho cả hai|
|Segment đến cao hơn mong đợi (có khoảng trống)|Gửi ngay **duplicate ACK**|
|Segment lấp đầy (một phần hoặc hoàn toàn) khoảng trống|Gửi ACK ngay nếu nó bắt đầu ở đầu dưới của khoảng trống|

### Truyền lại

- **Timeout**: gửi lại segment chưa ACK có seq # nhỏ nhất, rồi khởi động lại timer.
- **Fast retransmit**: nhận **3 duplicate ACK** (tức 3 ACK thêm cho cùng dữ liệu) thì gửi lại ngay, không chờ timeout.

### Kiểm soát luồng (flow control)

- Bên nhận báo **rwnd** (vùng đệm trống) trong header:

$$rwnd=RcvBuffer-(LastByteRcvd-LastByteRead)$$

- Bên gửi giữ lượng dữ liệu chưa ACK $\le rwnd$ để **không làm tràn bộ đệm** bên nhận.

### Quản lý kết nối

- **Bắt tay 2 bước không đủ**: gây half-open connection và nhận dữ liệu trùng, do trễ thay đổi, gói bị gửi lại, đảo thứ tự.
- **Bắt tay 3 bước (3-way handshake)**:
    1. Client gửi `SYN=1, Seq=x`.
    2. Server gửi `SYN=1, Seq=y, ACK=1, ACKnum=x+1` (SYNACK).
    3. Client gửi `ACK=1, ACKnum=y+1` (segment này có thể mang dữ liệu).
- **Đóng kết nối**: mỗi bên gửi **FIN**, bên kia trả ACK. Client chuyển qua `FIN_WAIT_1 → FIN_WAIT_2 → TIMED_WAIT` (chờ $2\times$ max segment lifetime) `→ CLOSED`. Server đi qua `CLOSE_WAIT → LAST_ACK → CLOSED`.

## 6. Nguyên lý kiểm soát tắc nghẽn

- **Tắc nghẽn**: quá nhiều nguồn gửi quá nhiều dữ liệu quá nhanh. Biểu hiện là **trễ lớn** (xếp hàng ở router) và **mất gói** (tràn bộ đệm).
- **Khác flow control**: flow control là một bên gửi quá nhanh so với **một** bên nhận. Congestion control là **nhiều** bên gửi quá nhanh so với mạng.
- **Các kịch bản và "chi phí" của tắc nghẽn**:
    - Kịch bản 1 (bộ đệm vô hạn): throughput tối đa mỗi kết nối là $R/2$, trễ tăng vọt khi tiến gần $R/2$.
    - Kịch bản 2 (bộ đệm hữu hạn, có truyền lại): tốn công truyền lại. Timeout sớm còn gây **bản sao không cần thiết**, làm giảm throughput.
    - Kịch bản 3 (nhiều chặng): gói bị rớt ở hạ nguồn làm **lãng phí** băng thông và bộ đệm thượng nguồn.
- **Hai hướng tiếp cận**:
    - **End-end**: không có phản hồi từ mạng, suy luận từ mất gói và trễ. **TCP dùng cách này**.
    - **Network-assisted**: router phản hồi trực tiếp (ECN, ATM, DECbit).

## 7. Kiểm soát tắc nghẽn của TCP

- **Giới hạn gửi**: $LastByteSent-LastByteAcked<cwnd$, và tốc độ gửi xấp xỉ $\dfrac{cwnd}{RTT}$ byte/s.
- **AIMD** (Additive Increase, Multiplicative Decrease):
    - Tăng 1 MSS mỗi RTT cho đến khi mất gói (đồ thị **răng cưa**).
    - Khi mất gói: giảm một nửa nếu phát hiện bằng 3 dup ACK (**Reno**), hoặc về 1 MSS nếu bằng timeout (**Tahoe**).
- **Slow start**:
    - Bắt đầu với $cwnd=1$ MSS và **nhân đôi mỗi RTT** (cộng 1 MSS cho mỗi ACK nhận được).
    - Khi mất gói do timeout: $ssthresh=cwnd/2$, $cwnd=1$ MSS.
    - Khi $cwnd\ge ssthresh$ thì chuyển sang **congestion avoidance** (tăng tuyến tính, mỗi ACK cộng $MSS\cdot\dfrac{MSS}{cwnd}$).
    - Khi nhận 3 dup ACK: $ssthresh=cwnd/2$, $cwnd=ssthresh+3$ MSS, vào **fast recovery**.
- **TCP CUBIC** (mặc định trên Linux): sau khi giảm cửa sổ, ghi nhớ $W_{max}$ (tốc độ lúc xảy ra mất gói), **tăng nhanh** khi còn xa $W_{max}$ và **chậm lại** khi gần $W_{max}$. Cửa sổ tăng theo **hàm bậc ba** của khoảng cách đến thời điểm $K$.
- **Delay-based** (ví dụ BBR): giữ "đường ống vừa đầy chứ không đầy hơn", tránh gây mất gói.

$$\text{throughput}_{uncongested}=\frac{cwnd}{RTT_{min}}$$

- Nếu throughput đo được gần mức này thì tăng $cwnd$ tuyến tính.
- Nếu thấp hơn nhiều thì giảm $cwnd$ tuyến tính.
- **ECN**: router đánh dấu 2 bit trong header IP; đích đặt bit **ECE** trong ACK để báo cho bên gửi.
- **Công bằng (fairness)**: $K$ phiên TCP dùng chung nút cổ chai băng thông $R$ thì mỗi phiên đạt $\dfrac{R}{K}$.
    - TCP công bằng trong điều kiện lý tưởng: cùng RTT, số phiên cố định, chỉ ở pha congestion avoidance.
    - UDP không bị giới hạn bởi congestion control. Mở nhiều kết nối TCP song song cũng chiếm phần lớn hơn. Ví dụ: đã có 9 kết nối, ứng dụng mới mở 1 kết nối được $R/10$, mở 11 kết nối được $R/2$.

## 8. Tiến hóa của tầng giao vận: QUIC

- QUIC là giao thức tầng ứng dụng chạy trên **UDP**, là nền của **HTTP/3**.
- **Một** lần bắt tay duy nhất cho độ tin cậy, kiểm soát tắc nghẽn, xác thực và mã hóa. TCP+TLS cần **2** lần bắt tay nối tiếp.
- Nhiều **stream** được ghép trên một kết nối QUIC, mỗi stream có rdt riêng và dùng chung congestion control, nên **không bị HOL blocking** như HTTP/2 trên TCP.

## 9. Công thức hay vào đề

- Hiệu suất stop-and-wait: $U=\dfrac{L/R}{RTT+L/R}$.
- Throughput TCP trung bình (bỏ qua slow start): $\dfrac{3}{4}\cdot\dfrac{W}{RTT}$ byte/s. Cửa sổ trung bình là $\dfrac{3}{4}W$, với $W$ là kích thước cửa sổ lúc xảy ra mất gói.
- Throughput theo xác suất mất gói $L$ (Mathis): $\dfrac{1.22\cdot MSS}{RTT\sqrt{L}}$. Ví dụ slide: gói 1500 byte, RTT 100 ms, muốn 10 Gbps thì cần $W=83{,}333$ segment và $L=2\cdot10^{-10}$.
- Timeout: $TimeoutInterval=EstimatedRTT+4\cdot DevRTT$.
- Bắt tay 3 bước: $x\to(y,\ x+1)\to y+1$.

Nếu muốn, mình có thể đóng gói phần này thành file (Word/PDF), hoặc làm bộ câu hỏi trắc nghiệm để bạn ôn.