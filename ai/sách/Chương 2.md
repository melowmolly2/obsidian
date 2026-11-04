Chương 2 **"Các chiến lược tìm kiếm kinh nghiệm"** (Heuristic Search) trong tài liệu trình bày phương pháp sử dụng thông tin tri thức bổ sung để hướng dẫn quá trình tìm kiếm hiệu quả hơn so với tìm kiếm mù. Dưới đây là tóm tắt lý thuyết trọng tâm của chương:

---

### 1. Hàm đánh giá và Tìm kiếm kinh nghiệm

- **Hàm đánh giá $h(u)$**: Với mỗi trạng thái $u$, hàm $h(u)$ cho một giá trị số đánh giá "sự gần đích" của $u$. Trạng thái có $h(u)$ càng nhỏ được xem là càng có nhiều hứa hẹn dẫn tới đích.
- **Ví dụ về hàm đánh giá**:
    - _Bài toán tìm đường_: Độ dài đường chim bay từ vị trí hiện tại tới đích.
    - _Bài toán 8 số_:
        - $h_1(u)$: Số quân không nằm đúng vị trí trong trạng thái đích.
        - $h_2(u)$: Tổng khoảng cách (Manhattan) dịch chuyển theo hàng/cột của các quân từ vị trí hiện tại đến vị trí đích.
- **3 bước giải quyết bài toán bằng tìm kiếm kinh nghiệm**:
    1. Biểu diễn trạng thái và các toán tử.
    2. Xây dựng hàm đánh giá.
    3. Thiết kế chiến lược chọn trạng thái để phát triển ở mỗi bước.
- **Mối liên hệ giữa các chiến lược**:
    - **Tìm kiếm tốt nhất - đầu tiên** = Tìm kiếm theo bề rộng + Hàm đánh giá.
    - **Tìm kiếm leo đồi** = Tìm kiếm theo độ sâu + Hàm đánh giá.

---

### 2. Tìm kiếm tốt nhất - đầu tiên (Best-First Search)

- **Cơ chế**: Là thuật toán tìm kiếm theo bề rộng được hướng dẫn bởi hàm đánh giá. Tại mỗi bước, thuật toán chọn trạng thái có giá trị $h(u)$ nhỏ nhất (tốt nhất) trong tất cả các trạng thái chờ phát triển.
- **Cài đặt thuật toán**:
    - Sử dụng danh sách $L$ lưu các trạng thái chờ phát triển.
    - Danh sách $L$ luôn được sắp xếp theo **thứ tự tăng dần** của hàm đánh giá.
    - Khi phát triển $u$, các trạng thái con $v$ kề $u$ được chèn vào $L$ sao cho danh sách luôn duy trì thứ tự sắp xếp.

---

### 3. Tìm kiếm leo đồi (Hill-Climbing Search)

- **Cơ chế**: Là thuật toán tìm kiếm theo độ sâu được hướng dẫn bởi hàm đánh giá. Khi phát triển đỉnh $u$, ở bước tiếp theo thuật toán chỉ chọn trong số các **đỉnh con kề $u$** đỉnh có giá trị $h(v)$ tốt nhất để phát triển tiếp.
- **Cài đặt thuật toán**:
    - Sử dụng danh sách tạm $L_1$ lưu các trạng thái kề $u$.
    - Sắp xếp $L_1$ theo thứ tự tăng dần của hàm đánh giá.
    - Chuyển danh sách $L_1$ vào **đầu danh sách $L$** để ưu tiên phát triển đỉnh con tốt nhất.

---

### 4. Tìm kiếm BEAM (Beam Search)

- **Cơ chế**: Giống như tìm kiếm theo bề rộng, phát triển các đỉnh theo từng mức của cây tìm kiếm.
- **Đặc điểm**: Để tránh bùng nổ trạng thái, tại mỗi mức thuật toán chỉ giữ lại và phát triển **$k$ đỉnh tốt nhất** (dựa vào hàm đánh giá).
- **Ưu điểm**: Ở bất kỳ mức nào cũng chỉ có tối đa $k$ đỉnh được phát triển, giúp tiết kiệm không gian và thời gian tính toán so với $b^d$ đỉnh trong tìm kiếm theo bề rộng thông thường.

---

💡 Bạn có muốn đi vào ví dụ từng bước chạy thuật toán (như **Best-First Search** hoặc **Hill-Climbing**) trên đồ thị cụ thể không?