### **CHƯƠNG 3: ĐỊNH THỨC (DETERMINANTS)**

Chương 3 trình bày toàn bộ lý thuyết về **Định thức (Determinant)** — một đại lượng số đặc trưng gán cho mỗi ma trận vuông. Định thức giữ vai trò then chốt trong việc kiểm tra tính khả nghịch của ma trận, giải hệ phương trình tuyến tính bằng công thức tường minh và cung cấp ý nghĩa hình học về diện tích, thể tích.

---

### **1. Định nghĩa Quy nạp & Khai triển Laplace**

#### **a. Định nghĩa quy nạp**

- **Ma trận cấp 1:** Với ma trận \(A = [a]\), định thức được định nghĩa là \(|A| = a\).
- **Minor (Định thức con) \(A_{ij}\):** Cho ma trận vuông \(A = [a_{ij}]\) cấp \(n \ge 2\), minor \(A_{ij}\) của phần tử \(a_{ij}\) là định thức của ma trận vuông cấp \(n-1\) thu được bằng cách xóa đi hàng thứ \(i\) và cột thứ \(j\) của \(A\).
- **Cofactor (Đối nhân tử hay Phần bù đại số) \(C_{ij}\):** Được xác định bởi công thức \(C_{ij} = (-1)^{i+j} A_{ij}\).

#### **b. Định lý Khai triển Laplace**

Định thức của ma trận vuông \(A\) cấp \(n\) có thể được tính bằng cách khai triển theo bất kỳ hàng nào hoặc bất kỳ cột nào:

- **Khai triển theo hàng thứ \(i\):** \[\det(A) = |A| = \sum_{j=1}^{n} a_{ij}C_{ij} = a_{i1}C_{i1} + a_{i2}C_{i2} + \dots + a_{in}C_{in} \quad\]
- **Khai triển theo cột thứ \(j\):** \[\det(A) = |A| = \sum_{i=1}^{n} a_{ij}C_{ij} = a_{1j}C_{1j} + a_{2j}C_{2j} + \dots + a_{nj}C_{nj} \quad\]

#### **c. Quy tắc Sarrus & Ma trận Tam giác**

- **Quy tắc Sarrus (Ma trận cấp 3):** Ta viết thêm cột 1 và cột 2 vào bên phải ma trận, rồi tính tổng các tích dọc theo các đường chéo đi xuống trừ đi tổng các tích dọc theo các đường chéo đi lên.
- **Mẹo tính nhanh:** Ta nên ưu tiên chọn hàng hoặc cột chứa nhiều phần tử bằng 0 nhất để khai triển nhằm giảm số lượng đối nhân tử cần tính.
- **Định thức ma trận tam giác:** Nếu \(A\) là ma trận tam giác trên hoặc tam giác dưới, định thức \(\det(A)\) chính bằng tích của tất cả các phần tử nằm trên đường chéo chính: \[\det(A) = a_{11} \cdot a_{22} \dots a_{nn} \quad\]

---

### **2. Ảnh hưởng của Phép biến đổi Sơ cấp lên Định thức**

Giá trị định thức biến đổi theo quy luật cụ thể khi áp dụng các phép biến đổi sơ cấp theo hàng hoặc theo cột:

1. **Đổi chỗ hai hàng (hoặc hai cột):** Định thức đổi dấu: \[\det(B) = -\det(A) \quad\]
2. **Nhân một hàng (hoặc một cột) với số \(\alpha \neq 0\):** Định thức tăng lên \(\alpha\) lần: \[\det(B) = \alpha \det(A) \quad\]
3. **Cộng vào một hàng (hoặc cột) một bội số của hàng (hoặc cột) khác:** Định thức hoàn toàn không thay đổi: \[\det(B) = \det(A) \quad\]

#### **Ma trận Sơ cấp & Tương đương dạng bậc thang**

- Với ma trận sơ cấp \(E\), ta có hệ thức \(|EA| = |E||A|\), trong đó \(|E| = 1\) đối với phép thay thế hàng, \(|E| = -1\) đối với phép trao đổi hàng, và \(|E| = r\) đối với phép nhân tỉ lệ \(r\).
- **Nhân vô hướng toàn bộ ma trận:** Nếu \(A\) là ma trận vuông cấp \(n\) và \(c \in \mathbb{R}\), ta có công thức: \[\det(cA) = c^n \det(A) \quad\]
- **Mối liên hệ với dạng bậc thang:** Nếu biến đổi \(A\) về ma trận dạng bậc thang \(U\), ta thu được \(|A| = c \cdot |U| = c \cdot (u_{11}u_{22}\dots u_{nn})\) với \(c \neq 0\). Ma trận \(A\) khả nghịch khi và chỉ khi \(\det(A) \neq 0\).

---

### **3. Các Tính chất Đại số Cốt lõi của Định thức**

- **Định thức của Ma trận Chuyển vị:** Định thức của ma trận \(A^T\) luôn bằng định thức của \(A\): \[\det(A^T) = \det(A) \quad\]
- **Định thức của Tích Ma trận:** Định thức của tích hai ma trận vuông cùng cấp bằng tích các định thức của từng ma trận: \[\det(AB) = \det(A) \cdot \det(B) \quad\]
- **Định thức của Ma trận Nghịch đảo:** Nếu \(A\) khả nghịch, định thức của \(A^{-1}\) bằng nghịch đảo định thức của \(A\): \[\det(A^{-1}) = \frac{1}{\det(A)} \quad\]

---

### **4. Ma trận Phụ hợp (Adjugate) & Công thức Ma trận Nghịch đảo**

- **Ma trận Phụ hợp (\(\text{adj}(A)\)):** Là ma trận chuyển vị của ma trận các đối nhân tử \(C_{ij}\): \[\text{adj}(A) = \begin{bmatrix} C_{11} & C_{21} & \dots & C_{n1} \ C_{12} & C_{22} & \dots & C_{n2} \ \vdots & \vdots & \ddots & \vdots \ C_{1n} & C_{2n} & \dots & C_{nn} \end{bmatrix} \quad\]
- **Hệ thức cơ bản:** Tích của ma trận \(A\) với ma trận phụ hợp thỏa mãn: \[A \cdot \text{adj}(A) = \det(A) \cdot I_n \quad\]
- **Công thức Ma trận Nghịch đảo:** Khi \(\det(A) \neq 0\), ma trận nghịch đảo \(A^{-1}\) được tính bởi: \[A^{-1} = \frac{1}{\det(A)} \text{adj}(A) \quad\]

---

### **5. Công thức Cramer Giải Hệ Phương trình Tuyến tính**

Xét hệ phương trình tuyến tính \(A\mathbf{x} = \mathbf{b}\) gồm \(n\) phương trình và \(n\) ẩn số có ma trận hệ số \(A\) thỏa mãn \(\det(A) \neq 0\).

Công thức Cramer khẳng định hệ có **nghiệm duy nhất** \(x_1, x_2, \dots, x_n\) được tính trực tiếp bởi: \[x_i = \frac{\det(A_i)}{\det(A)} \quad \text{với } i = 1, 2, \dots, n \quad\]

Trong đó, \(A_i\) là ma trận nhận được từ \(A\) bằng cách thay thế cột thứ \(i\) bằng cột hằng số vế phải \(\mathbf{b}\).

---

### **6. Ứng dụng Hình học của Định thức**

- **Diện tích hình bình hành:** Với ma trận vuông cấp 2 \(A = [\mathbf{a}_1 \quad \mathbf{a}_2]\), trị tuyệt đối \(|\det(A)|\) biểu thị diện tích của hình bình hành xác định bởi hai vector cột \(\mathbf{a}_1, \mathbf{a}_2\).
- **Thể tích hình hộp:** Với ma trận vuông cấp 3 \(A = [\mathbf{a}_1 \quad \mathbf{a}_2 \quad \mathbf{a}_3]\), trị tuyệt đối \(|\det(A)|\) biểu thị thể tích của hình hộp xác định bởi ba vector cột của \(A\).
- **Biến đổi qua Ánh xạ Tuyến tính:** Cho ánh xạ tuyến tính \(T(\mathbf{x}) = A\mathbf{x}\) xác định bởi ma trận vuông \(A\). Nếu \(S\) là một miền phẳng có diện tích hữu hạn trong \(\mathbb{R}^2\) (hoặc một khối trong \(\mathbb{R}^3\)), diện tích (hoặc thể tích) của miền ảnh \(T(S)\) được tính bởi: \[\text{Diện tích}(T(S)) = |\det(A)| \times \text{Diện tích}(S) \quad\]

---

💡 Bạn có muốn cùng giải một bài tập thực hành của Chương 3 như **tính định thức cấp 4 bằng cách khử sơ cấp đưa về ma trận tam giác**, **tìm ma trận nghịch đảo qua ma trận phụ hợp**, hay **dùng công thức Cramer** không?