### **CHƯƠNG 2: ĐẠI SỐ MA TRẬN (MATRIX ALGEBRA)**

Chương 2 tập trung vào cấu trúc đại số của ma trận, các phép toán ma trận, khái niệm ma trận nghịch đảo, phương pháp phân tích ma trận LU và các ứng dụng thực tế quan trọng như mô hình kinh tế Leontief.

---

### **1. Các phép toán trên Ma trận & Tính chất Đại số**

#### **a. Khái niệm Ma trận**

- **Ma trận** cỡ $m \times n$ là một bảng chữ nhật gồm $m$ hàng và $n$ cột chứa các số thực hoặc số phức. Phần tử nằm ở hàng $i$, cột $j$ được ký hiệu là $a_{ij}$.
- **Ma trận không ($\mathbf{0}_{mn}$):** Là ma trận cỡ $m \times n$ có tất cả các phần tử đều bằng 0.

#### **b. Phép cộng và Nhân với một số thực (Vô hướng)**

- **Phép cộng:** Cho hai ma trận cùng kích cỡ $A, B$ cỡ $m \times n$. Ma trận tổng $A + B$ nhận được bằng cách cộng các phần tử ở vị trí tương ứng: $(A + B)_{ij} = a_{ij} + b_{ij}$.
- **Phép nhân vô hướng:** Cho ma trận $A$ cỡ $m \times n$ và số thực $c$. Ma trận $cA$ nhận được bằng cách nhân mọi phần tử của $A$ với $c$: $(cA)_{ij} = c \cdot a_{ij}$.

> **Định lý 2.1 (Tính chất của phép cộng và nhân vô hướng):** Cho $A, B, C$ là các ma trận cỡ $m \times n$ và $c, d$ là các số thực:
> 
> 1. $A + B = B + A$ (Giao hoán).
> 2. $(A + B) + C = A + (B + C)$ (Kết hợp).
> 3. $A + \mathbf{0} = A$ (Phần tử trung hòa).
> 4. $A + (-A) = \mathbf{0}$.
> 5. $c(A + B) = cA + cB$ (Phân phối).
> 6. $(c + d)A = cA + dA$ (Phân phối).
> 7. $c(dA) = (cd)A$ (Kết hợp nhân vô hướng).
> 8. $1A = A$.

#### **c. Phép nhân hai ma trận ($AB$)**

- **Điều kiện thực hiện:** Tích $AB$ chỉ xác định khi **số cột của $A$ bằng số hàng của $B$**. Nếu $A$ cỡ $m \times n$ và $B$ cỡ $n \times p$, ma trận tích $AB$ sẽ có kích cỡ $m \times p$.
    
- **Công thức phần tử:** Phần tử ở hàng $i$, cột $j$ của $AB$ được tính bằng tích vô hướng của hàng $i$ ma trận $A$ với cột $j$ ma trận $B$: $$(AB)_{ij} = a_{i1}b_{1j} + a_{i2}b_{2j} + \dots + a_{in}b_{nj}$$
    
- **Các tính chất đại số của phép nhân ma trận:**
    
    - Kết hợp: $A(BC) = (AB)C$.
    - Phân phối: $A(B + C) = AB + AC$ và $(B + C)A = BA + CA$.
    - Phần tử đơn vị: $I_m A = A = A I_n$ (với $I_k$ là ma trận đơn vị cấp $k$).
    - **LƯU Ý CỰC KỲ QUAN TRỌNG:**
        1. Phép nhân ma trận **KHÔNG CÓ tính chất giao hoán**: Nói chung $AB \neq BA$.
        2. **Luật giản ước không tổng quát:** Từ $AC = BC$, ta **chưa thể suy ra** $A = B$ (trừ khi $C$ là ma trận khả nghịch).
        3. Tích $AB = \mathbf{0}$ **không nhất thiết** dẫn đến $A = \mathbf{0}$ hoặc $B = \mathbf{0}$.

#### **d. Ma trận chuyển vị (Transpose)**

- Ma trận chuyển vị của $A$ cỡ $m \times n$, ký hiệu $A^T$, là ma trận cỡ $n \times m$ nhận được bằng cách đổi các hàng của $A$ thành các cột tương ứng: $(A^T)_{ij} = a_{ji}$.
- **Tính chất của phép chuyển vị:**
    1. $(A^T)^T = A$.
    2. $(A + B)^T = A^T + B^T$.
    3. $(cA)^T = c A^T$.
    4. $(AB)^T = B^T A^T$ _(chú ý đảo thứ tự ma trận khi lấy chuyển vị của một tích)_.

---

### **2. Ma trận Nghịch đảo & Ma trận Sơ cấp**

#### **a. Định nghĩa Ma trận Khả nghịch**

Một ma trận vuông $A$ cấp $n$ được gọi là **khả nghịch (invertible)** nếu tồn tại một ma trận vuông $B$ cấp $n$ sao cho: $$A B = B A = I_n$$ Ma trận $B$ là duy nhất và được gọi là **ma trận nghịch đảo** của $A$, ký hiệu là $A^{-1}$.

#### **b. Công thức tính ma trận nghịch đảo cấp 2**

Cho ma trận $A = \begin{bmatrix} a & b \ c & d \end{bmatrix}$:

- $A$ khả nghịch khi và chỉ khi $\det A = ad - bc \neq 0$.
- Khi $\det A \neq 0$, ma trận nghịch đảo được tính bằng công thức: $$A^{-1} = \frac{1}{ad - bc} \begin{bmatrix} d & -b \ -c & a \end{bmatrix}$$

#### **c. Ứng dụng giải hệ phương trình tuyến tính**

Nếu $A$ là ma trận vuông cấp $n$ khả nghịch, thì với mọi vector $\mathbf{b} \in \mathbb{R}^n$, hệ phương trình $A\mathbf{x} = \mathbf{b}$ luôn có **nghiệm duy nhất**: $$\mathbf{x} = A^{-1}\mathbf{b}$$

#### **d. Các tính chất của Ma trận Nghịch đảo**

1. $(A^{-1})^{-1} = A$.
2. **Nghịch đảo của một tích:** Nếu $A, B$ là hai ma trận vuông khả nghịch cùng cấp, thì $AB$ khả nghịch và: $$(AB)^{-1} = B^{-1} A^{-1}$$ _(Tích của nhiều ma trận khả nghịch: $(A_1 A_2 \dots A_k)^{-1} = A_k^{-1} \dots A_2^{-1} A_1^{-1}$)_.
3. $(A^T)^{-1} = (A^{-1})^T$.
4. **Luật giản ước:** Nếu $C$ khả nghịch thì $AC = BC \implies A = B$ và $CA = CB \implies A = B$.

#### **e. Ma trận Sơ cấp & Thuật toán Gauss-Jordan tìm nghịch đảo**

- **Ma trận sơ cấp (Elementary Matrix) $E$:** Là ma trận nhận được bằng cách thực hiện đúng một phép biến đổi sơ cấp theo hàng đối với ma trận đơn vị $I_n$.
- Phép biến đổi hàng trên ma trận $A$ tương ứng với việc nhân bên trái $A$ một ma trận sơ cấp $E$ tương ứng: $A \to E A$.
- Mọi ma trận sơ cấp $E$ đều khả nghịch, và $E^{-1}$ chính là ma trận sơ cấp ứng với phép biến đổi ngược lại.

> **Định lý 2.5:** Ma trận vuông $A$ cấp $n$ khả nghịch khi và chỉ khi $A$ tương đương theo hàng với $I_n$ ($A \sim I_n$). Trong trường hợp này, mọi dãy phép biến đổi sơ cấp theo hàng đưa $A$ về $I_n$ cũng sẽ đưa $I_n$ thành $A^{-1}$.

- **Thuật toán tìm $A^{-1}$ (Phương pháp Gauss-Jordan):**
    1. Lập ma trận ghép $[A \mid I_n]$ cỡ $n \times 2n$.
    2. Dùng các phép biến đổi sơ cấp theo hàng đưa $[A \mid I_n]$ về dạng $[I_n \mid B]$.
    3. Nếu đưa được về $[I_n \mid B]$ thì $A$ khả nghịch và $A^{-1} = B$. Nếu bên trái xuất hiện hàng toàn số 0 (không đưa được về $I_n$), kết luận $A$ không khả nghịch.

---

### **3. Định lý Ma trận Khả nghịch (Invertible Matrix Theorem - IMT)**

Định lý Ma trận Khả nghịch tập hợp các điều kiện tương đương cốt lõi cho một ma trận vuông $A$ cấp $n$:

> **Định lý IMT:** Cho $A$ là ma trận vuông cấp $n$. Các mệnh đề sau đây là tương đương (cùng đúng hoặc cùng sai):
> 
> 1. $A$ là ma trận khả nghịch.
> 2. $A$ tương đương theo hàng với ma trận đơn vị $I_n$ ($A \sim I_n$).
> 3. $A$ có $n$ vị trí chốt (mọi hàng và mọi cột đều chứa chốt).
> 4. Phương trình thuần nhất $A\mathbf{x} = \mathbf{0}$ chỉ có nghiệm tầm thường $\mathbf{x} = \mathbf{0}$.
> 5. Các cột của $A$ độc lập tuyến tính.
> 6. Ánh xạ tuyến tính $\mathbf{x} \mapsto A\mathbf{x}$ là đơn ánh.
> 7. Phương trình $A\mathbf{x} = \mathbf{b}$ có ít nhất một nghiệm với mọi $\mathbf{b} \in \mathbb{R}^n$.
> 8. Các cột của $A$ sinh ra không gian $\mathbb{R}^n$.
> 9. Ánh xạ tuyến tính $\mathbf{x} \mapsto A\mathbf{x}$ là toàn ánh.
> 10. Tồn tại ma trận $C$ cấp $n$ sao cho $CA = I_n$.
> 11. Tồn tại ma trận $D$ cấp $n$ sao cho $AD = I_n$.
> 12. Ma trận chuyển vị $A^T$ khả nghịch.

---

### **4. Ma trận Khối / Ma trận Phân khối (Partitioned Matrices)**

- Trong tính toán cỡ lớn (như trong trí tuệ nhân tạo và xử lý ảnh), ma trận được chia nhỏ thành các ma trận con gọi là các **khối (blocks)** bằng các đường kẻ ngang và dọc.
- **Các phép toán ma trận khối:**
    - **Phép cộng:** Cộng các khối ở vị trí tương ứng (với điều kiện kích cỡ các khối tương thích).
    - **Phép nhân:** Nhân các khối theo quy tắc "hàng nhân cột" tương tự như ma trận thông thường: $$A B = \begin{bmatrix} A_{11} & A_{12} \ A_{21} & A_{22} \end{bmatrix} \begin{bmatrix} B_{11} \ B_{21} \end{bmatrix} = \begin{bmatrix} A_{11}B_{11} + A_{12}B_{21} \ A_{21}B_{11} + A_{22}B_{21} \end{bmatrix}$$
- **Ma trận khối tam giác & ma trận khối đường chéo:** Giúp đơn giản hóa tính toán nghịch đảo và định thức trong các hệ thống phân tán.

---

### **5. Phân tích Ma trận LU (LU Factorization)**

#### **a. Khái niệm**

Phân tích LU là quá trình biểu diễn ma trận $A$ dưới dạng tích của hai ma trận: $$A = L \cdot U$$

- **$L$ (Unit Lower Triangular):** Ma trận tam giác dưới có các phần tử trên đường chéo chính bằng 1.
- **$U$ (Upper Triangular / Echelon Form):** Ma trận tam giác trên (chính là dạng bậc thang REF của $A$).

#### **b. Thuật toán giải hệ $A\mathbf{x} = \mathbf{b}$ bằng Phân tích LU**

Thay vì giải trực tiếp $A\mathbf{x} = \mathbf{b}$, ta giải hệ $L(U\mathbf{x}) = \mathbf{b}$ qua 2 bước thế đơn giản:

1. **Giải $L\mathbf{y} = \mathbf{b}$ để tìm $\mathbf{y}$** (dùng phép thế tiến từ trên xuống vì $L$ là ma trận tam giác dưới).
2. **Giải $U\mathbf{x} = \mathbf{y}$ để tìm $\mathbf{x}$** (dùng phép thế ngược từ dưới lên vì $U$ là ma trận tam giác trên).

#### **c. Tầm quan trọng của Phân tích LU**

Khi cần giải nhiều hệ phương trình $A\mathbf{x} = \mathbf{b}_1, A\mathbf{x} = \mathbf{b}_2, \dots$ có **cùng ma trận hệ số $A$** nhưng vế phải $\mathbf{b}$ thay đổi liên tục, phân tích LU giúp giải cực kỳ nhanh chóng mà không cần phải thực hiện lại thuật toán khử Gauss tốn kém thời gian trên $A$.

---

### **6. Ứng dụng Thực tế: Mô hình Đầu vào - Đầu ra Leontief**

Mô hình do nhà kinh tế học Wassily Leontief phát triển (đoạt giải Nobel Kinh tế năm 1973) dùng đại số ma trận để mô hình hóa sự phụ thuộc lẫn nhau giữa các ngành trong nền kinh tế.

- **Vector sản lượng ($\mathbf{x} \in \mathbb{R}^n$):** Tổng đầu ra của $n$ ngành kinh tế.
- **Ma trận tiêu thụ ($C \in \mathbb{R}^{n \times n}$):** Với $c_{ij}$ là giá trị hàng hóa của ngành $i$ cần thiết để sản xuất 1 đơn vị sản phẩm cho ngành $j$.
- **Vector nhu cầu trung gian ($C\mathbf{x}$):** Lượng sản phẩm các ngành tự tiêu thụ làm đầu vào cho sản xuất.
- **Vector nhu cầu cuối cùng ($\mathbf{d}$):** Nhu cầu của khu vực mở (người tiêu dùng, chính phủ, xuất khẩu...).

> **Phương trình cân bằng sản xuất Leontief:** $$\mathbf{x} = C\mathbf{x} + \mathbf{d} \quad \Longleftrightarrow \quad (I - C)\mathbf{x} = \mathbf{d}$$ Nếu ma trận $(I - C)$ khả nghịch, mức sản lượng cần thiết để đáp ứng đủ nhu cầu là: $$\mathbf{x} = (I - C)^{-1}\mathbf{d}$$

_Khi tổng các cột của ma trận tiêu thụ $C$ nhỏ hơn 1, ta có công thức xấp xỉ chuỗi lũy thừa:_ $$(I - C)^{-1} \approx I + C + C^2 + C^3 + \dots + C^m$$

---

🎯 Bạn có muốn cùng làm thử một bài tập thực hành của Chương 2 như **tìm ma trận nghịch đảo bằng thuật toán $[A \mid I] \sim [I \mid A^{-1}]$**, **thực hiện phân tích LU**, hay **giải bài toán mô hình Leontief** không?