### **CHƯƠNG 4: KHÔNG GIAN VECTOR (VECTOR SPACES)**

Chương 4 mở rộng cấu trúc đại số của các vector từ các không gian cụ thể như \(\mathbb{R}^2, \mathbb{R}^3\) lên một cấu trúc trừu tượng và tổng quát gọi là **Không gian vector**. Nội dung bao gồm không gian con, các không gian con của ma trận, cơ sở, hệ tọa độ, số chiều và ma trận chuyển cơ sở.

---

### **1. Định nghĩa Không gian vector & Không gian con**

#### **a. Định nghĩa Không gian vector**

Một **không gian vector** là một tập hợp \(V\) khác rỗng (các phần tử được gọi là các vector), đi kèm với phép cộng vector và phép nhân vector với một số thực thỏa mãn **10 tiên đề** sau với mọi \(\mathbf{u}, \mathbf{v}, \mathbf{w} \in V\) và mọi số thực \(c, d\):

1. \(\mathbf{u} + \mathbf{v} \in V\) (Tính đóng của phép cộng).
2. \(\mathbf{u} + \mathbf{v} = \mathbf{v} + \mathbf{u}\) (Tính giao hoán).
3. \((\mathbf{u} + \mathbf{v}) + \mathbf{w} = \mathbf{u} + (\mathbf{v} + \mathbf{w})\) (Tính kết hợp).
4. Tồn tại vector không \(\mathbf{0} \in V\) sao cho \(\mathbf{u} + \mathbf{0} = \mathbf{u}\).
5. Với mỗi \(\mathbf{u} \in V\), tồn tại vector đối \(-\mathbf{u} \in V\) sao cho \(\mathbf{u} + (-\mathbf{u}) = \mathbf{0}\).
6. \(c\mathbf{u} \in V\) (Tính đóng của phép nhân vô hướng).
7. \(c(\mathbf{u} + \mathbf{v}) = c\mathbf{u} + c\mathbf{v}\) (Tính phân phối 1).
8. \((c + d)\mathbf{u} = c\mathbf{u} + d\mathbf{u}\) (Tính phân phối 2).
9. \(c(d\mathbf{u}) = (cd)\mathbf{u}\) (Tính kết hợp nhân vô hướng).
10. \(1\mathbf{u} = \mathbf{u}\) (Tính chất phần tử đơn vị).

- **Các ví dụ cơ bản:**
    - Không gian \(\mathbb{R}^n\).
    - Không gian các dãy số vô hạn \(\mathbb{S}\) (tín hiệu thời gian rời rạc).
    - Không gian các đa thức một biến có bậc không quá \(n\), ký hiệu là \(P_n\).
    - Không gian các hàm số thực liên tục trên một khoảng \(C[a, b]\).

#### **b. Không gian con (Subspace)**

Một tập con \(H\) của không gian vector \(V\) được gọi là một **không gian con** của \(V\) nếu \(H\) thỏa mãn 3 tính chất:

1. Vector không \(\mathbf{0}\) của \(V\) nằm trong \(H\).
2. \(H\) đóng đối với phép cộng: \(\mathbf{u} + \mathbf{v} \in H\) với mọi \(\mathbf{u}, \mathbf{v} \in H\).
3. \(H\) đóng đối với phép nhân vô hướng: \(c\mathbf{u} \in H\) với mọi \(\mathbf{u} \in H\) và \(c \in \mathbb{R}\).

_Chú ý:_ Điều kiện (2) và (3) có thể viết gộp thành: \(c\mathbf{u} + d\mathbf{v} \in H\) với mọi \(\mathbf{u}, \mathbf{v} \in H\) và mọi vô hướng \(c, d\).

- **Lưu ý quan trọng:**
    - Tập chỉ gồm vector không \({\mathbf{0}}\) là không gian con của \(V\).
    - Đường thẳng hoặc mặt phẳng trong \(\mathbb{R}^3\) không đi qua gốc tọa độ **không phải** là không gian con của \(\mathbb{R}^3\).
    - \(\mathbb{R}^2\) không phải là không gian con của \(\mathbb{R}^3\) vì các phần tử của \(\mathbb{R}^2\) có 2 thành phần còn \(\mathbb{R}^3\) có 3 thành phần.

#### **c. Không gian con sinh bởi một tập (Span)**

Nếu \(S = {\mathbf{v}_1, \dots, \mathbf{v}_k}\) là một tập vector trong không gian \(V\), thì tập tất cả các tổ hợp tuyến tính của chúng, ký hiệu là \(\text{Span}(S) = \text{Span}{\mathbf{v}_1, \dots, \mathbf{v}_k}\), luôn là một **không gian con** của \(V\).

---

### **2. Các không gian con cơ bản của Ma trận & Ánh xạ tuyến tính**

Xét ma trận \(A\) kích cỡ \(m \times n\):

#### **a. Không gian hạch (Null Space - \(\text{Nul } A\))**

- **Định nghĩa:** \(\text{Nul } A\) là tập hợp tất cả các nghiệm của hệ phương trình tuyến tính thuần nhất \(A\mathbf{x} = \mathbf{0}\): \[\text{Nul } A = {\mathbf{x} \in \mathbb{R}^n \mid A\mathbf{x} = \mathbf{0}}\]
- **Định lý 4.2.1:** \(\text{Nul } A\) là một không gian con của \(\mathbb{R}^n\).

#### **b. Không gian cột (Column Space - \(\text{Col } A\))**

- **Định nghĩa:** \(\text{Col } A\) là tập hợp tất cả các tổ hợp tuyến tính của các cột của \(A\). Nếu \(A = [\mathbf{a}_1 \dots \mathbf{a}_n]\), thì \(\text{Col } A = \text{Span}{\mathbf{a}_1, \dots, \mathbf{a}_n}\).
- **Định lý 4.2.2:** \(\text{Col } A\) là một không gian con của \(\mathbb{R}^m\). \(\text{Col } A\) chính là ảnh của ánh xạ tuyến tính \(\mathbf{x} \mapsto A\mathbf{x}\).

#### **c. Không gian dòng (Row Space - \(\text{Row } A\))**

- **Định nghĩa:** \(\text{Row } A\) là tập hợp tất cả các tổ hợp tuyến tính của các dòng của ma trận \(A\).
- **Mối liên hệ:** Vì các dòng của \(A\) chính là các cột của ma trận chuyển vị \(A^T\), ta có \(\text{Row } A = \text{Col } A^T\).

#### **d. So sánh giữa \(\text{Nul } A\) và \(\text{Col } A\) đối với ma trận \(A\) cỡ \(m \times n\)**

|Tiêu chí|Không gian hạch (\(\text{Nul } A\))|Không gian cột (\(\text{Col } A\))|
|:--|:--|:--|
|**Chứa trong**|Là không gian con của \(\mathbb{R}^n\).|Là không gian con của \(\mathbb{R}^m\).|
|**Định nghĩa**|Định nghĩa ngầm qua điều kiện \(A\mathbf{x} = \mathbf{0}\).|Định nghĩa tường minh qua các cột của \(A\).|
|**Kiểm tra phần tử**|Dễ: Kiểm tra \(A\mathbf{v} = \mathbf{0}\).|Cần giải hệ phương trình \(A\mathbf{x} = \mathbf{v}\).|
|**Tính chất hệ**|\(\text{Nul } A = {\mathbf{0}} \iff A\mathbf{x} = \mathbf{0}\) chỉ có nghiệm tầm thường.|\(\text{Col } A = \mathbb{R}^m \iff A\mathbf{x} = \mathbf{b}\) có nghiệm với mọi \(\mathbf{b} \in \mathbb{R}^m\).|

#### **e. Hạt nhân (Kernel) và Ảnh (Range) của Ánh xạ tuyến tính**

Cho ánh xạ tuyến tính \(T: V \to W\):

- **Kernel (Hạt nhân):** \(\text{Ker } T = {\mathbf{u} \in V \mid T(\mathbf{u}) = \mathbf{0}}\), là một không gian con của \(V\).
- **Range (Ảnh):** \(\text{Im } T = {T(\mathbf{x}) \in W \mid \mathbf{x} \in V}\), là một không gian con của \(W\).

---

### **3. Độc lập tuyến tính & Cơ sở**

#### **a. Định nghĩa Độc lập tuyến tính**

Tập \(S = {\mathbf{v}_1, \dots, \mathbf{v}_p}\) trong không gian vector \(V\) được gọi là **độc lập tuyến tính** nếu phương trình vector \(c_1\mathbf{v}_1 + \dots + c_p\mathbf{v}_p = \mathbf{0}\) chỉ có nghiệm tầm thường \(c_1 = \dots = c_p = 0\). Nếu có nghiệm không tầm thường, \(S\) được gọi là **phụ thuộc tuyến tính**.

#### **b. Định nghĩa Cơ sở (Basis)**

Một tập vector \(\mathcal{B} = {\mathbf{b}_1, \dots, \mathbf{b}_n}\) trong \(V\) được gọi là một **cơ sở** của không gian \(V\) nếu:

1. \(\mathcal{B}\) độc lập tuyến tính.
2. \(\mathcal{B}\) là tập sinh của \(V\) (tức \(V = \text{Span }\mathcal{B}\)).

#### **c. Phương pháp tìm cơ sở cho các không gian con của Ma trận**

- **Cơ sở của \(\text{Col } A\):** Định lý 4.3.3 khẳng định **các cột chốt của ma trận \(A\)** tạo thành một cơ sở của \(\text{Col } A\). _(Lưu ý: Phải lấy các cột tương ứng trên ma trận gốc \(A\), không lấy trên dạng REF)_.
- **Cơ sở của \(\text{Row } A\):** Các dòng khác 0 trong dạng bậc thang (REF) của \(A\) tạo thành một cơ sở của \(\text{Row } A\).
- **Cơ sở của \(\text{Nul } A\):** Đưa hệ \(A\mathbf{x} = \mathbf{0}\) về dạng RREF, viết nghiệm dưới dạng vector tham số theo các ẩn tự do; các vector nhân với ẩn tự do tạo thành cơ sở của \(\text{Nul } A\).

---

### **4. Hệ tọa độ & Đẳng cấu**

#### **a. Định lý Biểu diễn duy nhất (Định lý 4.4.1)**

Giả sử \(\mathcal{B} = {\mathbf{b}_1, \dots, \mathbf{b}_n}\) là một cơ sở của không gian vector \(V\). Khi đó với mỗi vector \(\mathbf{x} \in V\), tồn tại **duy nhất** một bộ các số thực \(c_1, \dots, c_n\) sao cho: \[\mathbf{x} = c_1\mathbf{b}_1 + \dots + c_n\mathbf{b}_n\]

#### **b. Vector tọa độ & Ánh xạ tọa độ**

- Vector \([\mathbf{x}]_\mathcal{B} = \begin{bmatrix} c_1 \ \vdots \ c_n \end{bmatrix} \in \mathbb{R}^n\) được gọi là **vector tọa độ của \(\mathbf{x}\) đối với cơ sở \(\mathcal{B}\)**.
- **Định lý 4.4.2:** Ánh xạ tọa độ \(\mathbf{x} \mapsto [\mathbf{x}]_\mathcal{B}\) là một **song ánh tuyến tính** từ \(V\) vào \(\mathbb{R}^n\). Ánh xạ này gọi là một **đẳng cấu (Isomorphism)**, kết nối không gian tổng quát \(V\) với không gian \(\mathbb{R}^n\).

---

### **5. Số chiều & Hạng của Ma trận**

#### **a. Định nghĩa Số chiều (Dimension)**

- **Định lý 4.5.2:** Nếu không gian vector \(V\) có một cơ sở gồm \(n\) vector, thì mọi cơ sở của \(V\) đều chứa đúng \(n\) vector.
- **Định nghĩa 4.5.1:** Số lượng vector trong một cơ sở của \(V\) được gọi là **số chiều** của \(V\), ký hiệu là \(\text{dim}(V) = n\). Nếu \(V = {\mathbf{0}}\), thì \(\text{dim}(V) = 0\).
    - \(\text{dim}(\mathbb{R}^n) = n\).
    - \(\text{dim}(P_n) = n + 1\) (do có cơ sở \({1, x, \dots, x^n}\)).

#### **b. Các không gian con của \(\mathbb{R}^3\) phân loại theo số chiều**:

1. **0 chiều:** Không gian không \({\mathbf{0}}\).
2. **1 chiều:** Các đường thẳng đi qua gốc tọa độ.
3. **2 chiều:** Các mặt phẳng đi qua gốc tọa độ.
4. **3 chiều:** Toàn bộ không gian \(\mathbb{R}^3\).

#### **c. Định lý Hạng (Rank Theorem)**

- **Hạng của \(A\) (\(\text{rank}(A)\)):** Là số chiều của \(\text{Col } A\), chính bằng **số các cột chốt** (hoặc số dòng khác 0 trong dạng REF) của \(A\).
- **Số khuyết của \(A\) (\(\text{nullity}(A)\)):** Là số chiều của \(\text{Nul } A\), chính bằng **số ẩn tự do** trong hệ \(A\mathbf{x} = \mathbf{0}\).

> **Định lý 4.5.4 (Định lý Hạng):** Cho ma trận \(A\) kích cỡ \(m \times n\) (\(n\) cột): \[\text{rank}(A) + \text{nullity}(A) = n\] _(Số cột chốt + Số cột không chốt = Tổng số cột của ma trận \(A\))_.

---

### **6. Chuyển cơ sở (Change of Basis)**

Cho \(\mathcal{B} = {\mathbf{b}_1, \dots, \mathbf{b}_n}\) và \(\mathcal{C} = {\mathbf{c}_1, \dots, \mathbf{c}_n}\) là 2 cơ sở của không gian vector \(V\).

#### **a. Định lý 4.6.1**

Tồn tại duy nhất một ma trận \(P_{\mathcal{C} \leftarrow \mathcal{B}}\) kích cỡ \(n \times n\) sao cho: \[[\mathbf{x}]_\mathcal{C} = P_{\mathcal{C} \leftarrow \mathcal{B}} [\mathbf{x}]_\mathcal{B}\]

Các cột của ma trận \(P_{\mathcal{C} \leftarrow \mathcal{B}}\) là các vector tọa độ của cơ sở cũ \(\mathcal{B}\) đối với cơ sở mới \(\mathcal{C}\): \[P_{\mathcal{C} \leftarrow \mathcal{B}} = \begin{bmatrix} [\mathbf{b}_1]_\mathcal{C} & [\mathbf{b}_2]_\mathcal{C} & \dots & [\mathbf{b}_n]_\mathcal{C} \end{bmatrix}\]

#### **b. Mối liên hệ nghịch đảo**

Ma trận chuyển cơ sở \(P_{\mathcal{C} \leftarrow \mathcal{B}}\) luôn khả nghịch và ma trận chuyển ngược lại từ \(\mathcal{C}\) sang \(\mathcal{B}\) là: \[P_{\mathcal{B} \leftarrow \mathcal{C}} = \left(P_{\mathcal{C} \leftarrow \mathcal{B}}\right)^{-1}\]

---

💡 Bạn có muốn cùng làm một số bài tập thực hành tiêu biểu của Chương 4 (như **tìm cơ sở và số chiều của \(\text{Col } A, \text{Nul } A, \text{Row } A\)**, **tính vector tọa độ \([\mathbf{x}]_\mathcal{B}\)**, hoặc **tìm ma trận chuyển cơ sở**) không?