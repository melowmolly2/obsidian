### **CHƯƠNG 1: HỆ PHƯƠNG TRÌNH TUYẾN TÍNH (SYSTEMS OF LINEAR EQUATIONS)**

Chương 1 cung cấp toàn bộ lý thuyết nền tảng về hệ phương trình tuyến tính, thuật toán rút gọn hàng (khử Gauss/Gauss-Jordan), phương trình vector, phương trình ma trận, tính độc lập tuyến tính và khái niệm ánh xạ tuyến tính.

---

### **1. Khái niệm Hệ phương trình tuyến tính & Biểu diễn ma trận**

#### **a. Định nghĩa hệ phương trình tuyến tính**

- **Phương trình tuyến tính** theo các biến $x_1, x_2, \dots, x_n$ có dạng tổng quát: $$a_1x_1 + a_2x_2 + \dots + a_nx_n = b$$ Trong đó $a_1, \dots, a_n$ là các hệ số thực (hoặc phức) và $b$ là hằng số vế phải.
- **Hệ phương trình tuyến tính** là một tập hợp gồm một hoặc nhiều phương trình tuyến tính có cùng các biến số.
- **Trạng thái nghiệm của hệ:** Bất kỳ hệ phương trình tuyến tính nào cũng rơi vào đúng một trong ba trường hợp:
    1. **Vô nghiệm (Inconsistent):** Không tồn tại bộ số nào thỏa mãn tất cả các phương trình.
    2. **Có nghiệm duy nhất (Consistent - Unique solution):** Có đúng một bộ số thỏa mãn hệ.
    3. **Có vô số nghiệm (Consistent - Infinitely many solutions):** Có vô hạn bộ số thỏa mãn hệ. Một hệ được gọi là **tương thích (consistent)** nếu nó có ít nhất một nghiệm (duy nhất hoặc vô số nghiệm).

#### **b. Biểu diễn qua ma trận**

Xét hệ phương trình tuyến tính gồm $m$ phương trình và $n$ ẩn:

- **Ma trận hệ số (Coefficient matrix) $A$:** Chứa các hệ số xếp theo thứ tự ẩn số, có kích cỡ $m \times n$.
- **Ma trận hệ số mở rộng (Augmented matrix) $[A \mid \mathbf{b}]$:** Nhận được bằng cách bổ sung thêm cột hằng số $\mathbf{b}$ vào bên phải ma trận hệ số $A$, có kích cỡ $m \times (n+1)$.

---

### **2. Các phép biến đổi sơ cấp theo hàng & Dạng bậc thang**

#### **a. Ba phép biến đổi sơ cấp theo hàng (Elementary Row Operations)**

Để giải hệ phương trình tuyến tính, ta thực hiện các phép biến đổi sơ cấp trên ma trận hệ số mở rộng mà không làm thay đổi tập nghiệm của hệ:

1. **Đổi chỗ hai hàng ($R_i \leftrightarrow R_j$)**.
2. **Nhân một hàng với một số khác 0 ($c R_i \to R_i$ với $c \neq 0$)**.
3. **Cộng vào một hàng một bội số của hàng khác ($R_i + c R_j \to R_i$)**.

Two ma trận được gọi là **tương đương theo hàng (row equivalent)** nếu ma trận này có thể chuyển thành ma trận kia thông qua một dãy hữu hạn các phép biến đổi sơ cấp theo hàng.

> **Định lý 1.2:** Nếu ma trận mở rộng của hai hệ phương trình tuyến tính tương đương theo hàng với nhau thì hai hệ đó có cùng tập nghiệm.

#### **b. Dạng bậc thang (REF) và Dạng bậc thang rút gọn (RREF)**

Một ma trận ở **dạng bậc thang theo hàng (Row Echelon Form - REF)** nếu thỏa mãn:

1. Các hàng bằng 0 (nếu có) nằm ở dưới cùng của ma trận.
2. Trong một hàng khác 0, hệ số khác 0 đầu tiên tính từ trái sang phải (gọi là **hệ số dẫn đầu - leading entry**) của hàng dưới nằm ở cột bên phải so với hệ số dẫn đầu của hàng trên.
3. Các vị trí bên dưới các hệ số dẫn đầu đều bằng 0.

Một ma trận ở **dạng bậc thang rút gọn theo hàng (Reduced Row Echelon Form - RREF)** nếu nó ở dạng REF và thỏa mãn thêm: 4. Các hệ số dẫn đầu của các hàng khác 0 đều bằng **1** (gọi là số 1 dẫn đầu). 5. Mỗi số 1 dẫn đầu là phần tử khác 0 duy nhất trong cột chứa nó (các vị trí phía trên và phía dưới nó đều bằng 0).

> **Định lý 1.3 (Tính duy nhất):** Mỗi ma trận đều tương đương theo hàng với **một và chỉ một** ma trận dạng bậc thang rút gọn (RREF) duy nhất.

#### **c. Vị trí chốt, Cột chốt và Phân loại biến**

- **Vị trí chốt (Pivot position):** Là vị trí tương ứng với số 1 dẫn đầu trong dạng RREF của ma trận.
- **Cột chốt (Pivot column):** Là cột chứa vị trí chốt.
- **Chốt (Pivot):** Là số khác 0 nằm ở vị trí chốt được sử dụng để khử các phần tử khác trong cùng cột về 0.
- **Biến cơ bản (Basic variables):** Là các ẩn số ứng với các cột chốt.
- **Biến tự do (Free variables):** Là các ẩn số không ứng với cột chốt nào.

#### **d. Thuật toán rút gọn hàng & Tiêu chuẩn tồn tại, duy nhất nghiệm**

Thuật toán rút gọn hàng gồm 2 giai đoạn:

- **Giai đoạn tiến (Forward phase):** Dùng các phép biến đổi sơ cấp đưa ma trận về dạng bậc thang (REF).
- **Giai đoạn lùi (Backward phase):** Biến đổi các chốt về 1 và khử các phần tử phía trên chốt về 0 để đưa về dạng RREF.

> **Định lý Tồn tại và Duy nhất nghiệm:**
> 
> 1. Hệ phương trình tuyến tính **có nghiệm (tương thích)** khi và chỉ khi dạng bậc thang của ma trận mở rộng **không chứa hàng có dạng $[0 \quad 0 \quad \dots \quad 0 \mid b]$ với $b \neq 0$** (tức là cột ngoài cùng bên phải không phải cột chốt).
> 2. Nếu hệ tương thích:
>     - Hệ có **nghiệm duy nhất** khi và chỉ khi **không có biến tự do** (mọi cột của ma trận hệ số đều là cột chốt).
>     - Hệ có **vô số nghiệm** khi và chỉ khi **có ít nhất một biến tự do**.

---

### **3. Phương trình Vector & Khái niệm SPAN**

#### **a. Biểu diễn Vector & Tổ hợp tuyến tính**

- Một vector cột trong $\mathbb{R}^n$ là một ma trận kích cỡ $n \times 1$.
- Vector $\mathbf{b}$ được gọi là **tổ hợp tuyến tính (linear combination)** của các vector $\mathbf{v}_1, \mathbf{v}_2, \dots, \mathbf{v}_p$ nếu tồn tại các số thực $c_1, c_2, \dots, c_p$ sao cho: $$\mathbf{b} = c_1\mathbf{v}_1 + c_2\mathbf{v}_2 + \dots + c_p\mathbf{v}_p$$

> **Mối liên hệ phương trình vector:** Phương trình vector $x_1\mathbf{a}_1 + x_2\mathbf{a}_2 + \dots + x_n\mathbf{a}_n = \mathbf{b}$ có cùng tập nghiệm với hệ phương trình tuyến tính có ma trận hệ số mở rộng là $[\mathbf{a}_1 \quad \mathbf{a}_2 \quad \dots \quad \mathbf{a}_n \quad \mathbf{b}]$. Vector $\mathbf{b}$ là tổ hợp tuyến tính của các $\mathbf{a}_i$ khi và chỉ khi hệ phương trình có ma trận mở rộng đó tương thích.

#### **b. Tập sinh (SPAN)**

- Nếu $\mathbf{v}_1, \dots, \mathbf{v}_p$ là các vector trong $\mathbb{R}^n$, tập hợp tất cả các tổ hợp tuyến tính của chúng được gọi là **tập sinh bởi $\mathbf{v}_1, \dots, \mathbf{v}_p$**, ký hiệu là $\text{Span}{\mathbf{v}_1, \dots, \mathbf{v}_p}$: $$\text{Span}{\mathbf{v}_1, \dots, \mathbf{v}_p} = {c_1\mathbf{v}_1 + \dots + c_p\mathbf{v}_p \mid c_i \in \mathbb{R}}$$
- **Mô tả hình học trong $\mathbb{R}^3$:**
    - Nếu $\mathbf{v} \neq \mathbf{0}$, $\text{Span}{\mathbf{v}}$ là đường thẳng đi qua gốc tọa độ $\mathbf{0}$ và điểm $\mathbf{v}$.
    - Nếu $\mathbf{u}, \mathbf{v} \neq \mathbf{0}$ và $\mathbf{u}$ không phải bội của $\mathbf{v}$, $\text{Span}{\mathbf{u}, \mathbf{v}}$ là mặt phẳng đi qua gốc tọa độ chứa $\mathbf{u}$ và $\mathbf{v}$.

---

### **4. Phương trình Ma trận $A\mathbf{x} = \mathbf{b}$**

#### **a. Định nghĩa tích $A\mathbf{x}$**

Nếu $A$ là ma trận $m \times n$ có các cột là $\mathbf{a}_1, \dots, \mathbf{a}_n$ và $\mathbf{x} \in \mathbb{R}^n$, tích $A\mathbf{x}$ được định nghĩa là tổ hợp tuyến tính của các cột của $A$ với trọng số là các thành phần của $\mathbf{x}$: $$A\mathbf{x} = \begin{bmatrix} \mathbf{a}_1 & \mathbf{a}_2 & \dots & \mathbf{a}_n \end{bmatrix} \begin{bmatrix} x_1 \ \vdots \ x_n \end{bmatrix} = x_1\mathbf{a}_1 + x_2\mathbf{a}_2 + \dots + x_n\mathbf{a}_n$$ _Chú ý:_ Phép nhân $A\mathbf{x}$ chỉ xác định khi số cột của $A$ bằng số dòng của $\mathbf{x}$.

#### **b. Điều kiện để $A\mathbf{x} = \mathbf{b}$ có nghiệm với mọi $\mathbf{b}$**

> **Định lý 1.4.2:** Cho $A$ là ma trận $m \times n$. Các mệnh đề sau là tương đương:
> 
> 1. Với mỗi $\mathbf{b} \in \mathbb{R}^m$, phương trình $A\mathbf{x} = \mathbf{b}$ đều có nghiệm.
> 2. Mỗi $\mathbf{b} \in \mathbb{R}^m$ là một tổ hợp tuyến tính của các cột của $A$.
> 3. Các cột của $A$ sinh ra $\mathbb{R}^m$ (tức là $\text{Span}{\mathbf{a}_1, \dots, \mathbf{a}_n} = \mathbb{R}^m$).
> 4. Ma trận $A$ có **vị trí chốt ở mỗi hàng**.

#### **c. Tính chất tuyến tính của $A\mathbf{x}$**

Với mọi $\mathbf{u}, \mathbf{v} \in \mathbb{R}^n$ và số thực $c$:

- $A(\mathbf{u} + \mathbf{v}) = A\mathbf{u} + A\mathbf{v}$
- $A(c\mathbf{u}) = c(A\mathbf{u})$

---

### **5. Hệ thuần nhất và Hệ không thuần nhất**

#### **a. Hệ phương trình tuyến tính thuần nhất ($A\mathbf{x} = \mathbf{0}$)**

- Hệ phương trình được gọi là **thuần nhất** nếu hằng số vế phải bằng 0 ($A\mathbf{x} = \mathbf{0}$).
- Hệ thuần nhất luôn tương thích vì luôn có **nghiệm tầm thường (trivial solution)** $\mathbf{x} = \mathbf{0}$.
- Hệ thuần nhất có **nghiệm không tầm thường (nontrivial solution)** ($\mathbf{x} \neq \mathbf{0}$) khi và chỉ khi **hệ có ít nhất một biến tự do**.

#### **b. Dạng vector tham số và Mối liên hệ nghiệm**

- Dạng biểu diễn tập nghiệm của hệ phương trình bằng tổ hợp tuyến tính của các vector với tham số là các biến tự do được gọi là **dạng vector tham số (parametric vector form)**.

> **Định lý 1.5 (Tịnh tiến tập nghiệm):** Giả sử phương trình không thuần nhất $A\mathbf{x} = \mathbf{b}$ có một nghiệm riêng là $\mathbf{p}$. Khi đó, tập tất cả các nghiệm của $A\mathbf{x} = \mathbf{b}$ là tập hợp các vector có dạng: $$\mathbf{x} = \mathbf{p} + \mathbf{v}_h$$ Trong đó $\mathbf{v}_h$ là một nghiệm bất kỳ của hệ thuần nhất tương ứng $A\mathbf{x} = \mathbf{0}$. _Ý nghĩa hình học:_ Tập nghiệm của $A\mathbf{x} = \mathbf{b}$ là sự dịch chuyển (tịnh tiến) của tập nghiệm $A\mathbf{x} = \mathbf{0}$ theo vector $\mathbf{p}$.

---

### **6. Sự độc lập tuyến tính (Linear Independence)**

#### **a. Định nghĩa**

- Tập hợp các vector ${\mathbf{v}_1, \dots, \mathbf{v}_p}$ trong $\mathbb{R}^n$ được gọi là **độc lập tuyến tính (linearly independent)** nếu phương trình vector: $$c_1\mathbf{v}_1 + c_2\mathbf{v}_2 + \dots + c_p\mathbf{v}_p = \mathbf{0}$$ chỉ có **nghiệm duy nhất** $c_1 = c_2 = \dots = c_p = 0$.
- Nếu tồn tại các hệ số $c_1, \dots, c_p$ không đồng thời bằng 0 sao cho đẳng thức trên xảy ra, tập hợp được gọi là **phụ thuộc tuyến tính (linearly dependent)**.

#### **b. Sự độc lập tuyến tính của các cột của Ma trận**

> Các cột của ma trận $A$ độc lập tuyến tính khi và chỉ khi phương trình ma trận $A\mathbf{x} = \mathbf{0}$ **chỉ có nghiệm tầm thường** (tức là ma trận $A$ có vị trí chốt tại mọi cột / không có biến tự do).

#### **c. Tính chất đặc biệt**

- **Tập gồm 1 vector:** ${\mathbf{v}}$ độc lập tuyến tính khi và chỉ khi $\mathbf{v} \neq \mathbf{0}$.
- **Tập gồm 2 vector:** ${\mathbf{u}, \mathbf{v}}$ phụ thuộc tuyến tính khi và chỉ khi vector này là bội của vector kia.
- **Tập chứa vector không:** Bất kỳ tập vector nào chứa vector $\mathbf{0}$ đều **phụ thuộc tuyến tính**.
- **Định lý số lượng vector:** Nếu một tập gồm $p$ vector trong $\mathbb{R}^n$ với $p > n$, thì tập đó **chắc chắn phụ thuộc tuyến tính** (do số cột nhiều hơn số hàng nên luôn tồn tại ẩn tự do).

---

### **7. Ánh xạ tuyến tính (Linear Transformations)**

#### **a. Khái niệm Ánh xạ tuyến tính**

Một ánh xạ $T: \mathbb{R}^n \to \mathbb{R}^m$ được gọi là **tuyến tính** nếu với mọi $\mathbf{u}, \mathbf{v} \in \mathbb{R}^n$ và mọi số thực $c$:

1. $T(\mathbf{u} + \mathbf{v}) = T(\mathbf{u}) + T(\mathbf{v})$
2. $T(c\mathbf{u}) = c T(\mathbf{u})$

#### **b. Ma trận chuẩn tắc của Ánh xạ tuyến tính**

> **Định lý Ma trận chuẩn tắc:** Cho $T: \mathbb{R}^n \to \mathbb{R}^m$ là một ánh xạ tuyến tính. Khi đó tồn tại duy nhất một ma trận $A$ kích cỡ $m \times n$ sao cho: $$T(\mathbf{x}) = A\mathbf{x} \quad \forall \mathbf{x} \in \mathbb{R}^n$$ Ma trận $A$ được xác định bởi các cột là ảnh của các vector cơ sở chuẩn tắc $\mathbf{e}_1, \dots, \mathbf{e}_n$ của $\mathbb{R}^n$: $$A = \begin{bmatrix} T(\mathbf{e}_1) & T(\mathbf{e}_2) & \dots & T(\mathbf{e}_n) \end{bmatrix}$$ Ma trận $A$ được gọi là **ma trận chuẩn tắc (standard matrix)** của $T$.

#### **c. Toàn ánh (Surjective / Onto) và Đơn ánh (Injective / One-to-one)**

Cho $T: \mathbb{R}^n \to \mathbb{R}^m$ là ánh xạ tuyến tính với ma trận chuẩn tắc $A$:

- **Toàn ánh (Toàn cấu):** $T$ là toàn ánh nếu với mỗi $\mathbf{b} \in \mathbb{R}^m$, phương trình $T(\mathbf{x}) = \mathbf{b}$ có ít nhất một nghiệm $\mathbf{x} \in \mathbb{R}^n$.
    - _Điều kiện:_ $T$ là toàn ánh $\iff$ Các cột của $A$ sinh ra $\mathbb{R}^m \iff$ **Ma trận $A$ có vị trí chốt ở mỗi hàng**.
- **Đơn ánh (Đơn cấu):** $T$ là đơn ánh nếu với mỗi $\mathbf{b} \in \mathbb{R}^m$, phương trình $T(\mathbf{x}) = \mathbf{b}$ có nhiều nhất một nghiệm.
    - _Điều kiện:_ $T$ là đơn ánh $\iff$ Phương trình $T(\mathbf{x}) = \mathbf{0}$ chỉ có nghiệm tầm thường $\mathbf{x} = \mathbf{0} \iff$ Các cột của $A$ độc lập tuyến tính $\iff$ **Ma trận $A$ có vị trí chốt ở mỗi cột**.

---

💡 Bạn có muốn chúng ta cùng làm một số bài tập mẫu thuộc Chương 1 (như **đưa ma trận mở rộng về RREF để tìm nghiệm dưới dạng vector tham số** hay **xét tính toàn ánh/đơn ánh của ánh xạ tuyến tính**) để luyện tập không?