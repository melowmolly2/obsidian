# Chương 1 - Véc-tơ và Hình học không gian

Quay lại: [[MOC - Giải tích 2]]

> [!abstract] Mục tiêu chương 1
> Nắm vững đại số véc-tơ trong $\mathbb{R}^3$, cách biểu diễn đường thẳng, mặt phẳng và phân loại các mặt bậc hai – nền tảng trực quan bắt buộc cho tích phân bội và giải tích véc-tơ.

---

## 1. Hệ tọa độ 3 chiều & Mặt cầu

### 1.1. Khoảng cách giữa hai điểm
Cho $P_1(x_1, y_1, z_1)$ và $P_2(x_2, y_2, z_2)$:
$$|P_1 P_2| = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2 + (z_2 - z_1)^2}$$

### 1.2. Phương trình mặt cầu
- **Dạng chính tắc**: Tâm $C(h, k, l)$, bán kính $R$:
  $$(x - h)^2 + (y - k)^2 + (z - l)^2 = R^2$$
- **Dạng khai triển**:
  $$x^2 + y^2 + z^2 + 2ax + 2by + 2cz + d = 0$$
  Điều kiện là mặt cầu: $a^2 + b^2 + c^2 - d > 0$.
  Tâm $C(-a, -b, -c)$, bán kính $R = \sqrt{a^2 + b^2 + c^2 - d}$.

---

## 2. Các phép toán véc-tơ

Cho $\mathbf{a} = \langle a_1, a_2, a_3 \rangle$, $\mathbf{b} = \langle b_1, b_2, b_3 \rangle$.

### 2.1. Tích vô hướng (Dot Product)
$$\mathbf{a} \cdot \mathbf{b} = a_1 b_1 + a_2 b_2 + a_3 b_3 = \|\mathbf{a}\| \|\mathbf{b}\| \cos\theta$$
- **Điều kiện vuông góc**: $\mathbf{a} \perp \mathbf{b} \iff \mathbf{a} \cdot \mathbf{b} = 0$.
- **Hình chiếu vô hướng** của $\mathbf{b}$ lên $\mathbf{a}$: $\text{comp}_{\mathbf{a}}\mathbf{b} = \frac{\mathbf{a} \cdot \mathbf{b}}{\|\mathbf{a}\|}$.
- **Hình chiếu véc-tơ** của $\mathbf{b}$ lên $\mathbf{a}$: $\text{proj}_{\mathbf{a}}\mathbf{b} = \left(\frac{\mathbf{a} \cdot \mathbf{b}}{\|\mathbf{a}\|^2}\right)\mathbf{a}$.

### 2.2. Tích có hướng (Cross Product)
Chỉ áp dụng trong không gian 3 chiều:
$$\mathbf{a} \times \mathbf{b} = \begin{vmatrix} \mathbf{i} & \mathbf{j} & \mathbf{k} \\ a_1 & a_2 & a_3 \\ b_1 & b_2 & b_3 \end{vmatrix} = \langle a_2 b_3 - a_3 b_2,\; a_3 b_1 - a_1 b_3,\; a_1 b_2 - a_2 b_1 \rangle$$
- **Tính chất hình học**:
  - $(\mathbf{a} \times \mathbf{b}) \perp \mathbf{a}$ và $(\mathbf{a} \times \mathbf{b}) \perp \mathbf{b}$.
  - $\|\mathbf{a} \times \mathbf{b}\| = \|\mathbf{a}\| \|\mathbf{b}\| \sin\theta$ = **Diện tích hình bình hành** tạo bởi $\mathbf{a}$ và $\mathbf{b}$.
  - $S_{\triangle ABC} = \frac{1}{2} \|\vec{AB} \times \vec{AC}\|$.
  - $\mathbf{a} \parallel \mathbf{b} \iff \mathbf{a} \times \mathbf{b} = \mathbf{0}$.
  - Phản giao hoán: $\mathbf{a} \times \mathbf{b} = - (\mathbf{b} \times \mathbf{a})$.

### 2.3. Tích hỗn hợp (Scalar Triple Product)
$$(\mathbf{a} \times \mathbf{b}) \cdot \mathbf{c} = \begin{vmatrix} a_1 & a_2 & a_3 \\ b_1 & b_2 & b_3 \\ c_1 & c_2 & c_3 \end{vmatrix}$$
- **Ý nghĩa hình học**: $|(\mathbf{a} \times \mathbf{b}) \cdot \mathbf{c}|$ = **Thể tích hình hộp** dựng trên 3 véc-tơ $\mathbf{a}, \mathbf{b}, \mathbf{c}$.
- **Thể tích tứ diện**: $V = \frac{1}{6} |(\mathbf{a} \times \mathbf{b}) \cdot \mathbf{c}|$.
- 3 véc-tơ **đồng phẳng** $\iff (\mathbf{a} \times \mathbf{b}) \cdot \mathbf{c} = 0$.

---

## 3. Đường thẳng và Mặt phẳng trong $\mathbb{R}^3$

### 3.1. Đường thẳng
Đi qua $P_0(x_0, y_0, z_0)$ với véc-tơ chỉ phương $\mathbf{v} = \langle a, b, c \rangle$:
- **Phương trình tham số**:
  $$\begin{cases} x = x_0 + at \\ y = y_0 + bt \\ z = z_0 + ct \end{cases} \quad (t \in \mathbb{R})$$
- **Phương trình chính tắc** (khi $a, b, c \neq 0$):
  $$\frac{x - x_0}{a} = \frac{y - y_0}{b} = \frac{z - z_0}{c}$$

### 3.2. Mặt phẳng
Đi qua $P_0(x_0, y_0, z_0)$ với véc-tơ pháp tuyến $\mathbf{n} = \langle A, B, C \rangle$:
- **Phương trình**:
  $$A(x - x_0) + B(y - y_0) + C(z - z_0) = 0 \iff Ax + By + Cz + D = 0$$
- **Mẹo tìm pháp tuyến**: Nếu mặt phẳng song song với 2 véc-tơ $\mathbf{u}$ và $\mathbf{v}$ không cùng phương, chọn $\mathbf{n} = \mathbf{u} \times \mathbf{v}$.

### 3.3. Các công thức khoảng cách cốt lõi (Thi cử hay dùng)
1. **Từ điểm $P(x_0, y_0, z_0)$ đến mặt phẳng $(P): Ax + By + Cz + D = 0$**:
   $$d(P, (P)) = \frac{|Ax_0 + By_0 + Cz_0 + D|}{\sqrt{A^2 + B^2 + C^2}}$$
2. **Từ điểm $P$ đến đường thẳng $\Delta$** (đi qua $P_0$ có VTCP $\mathbf{v}$):
   $$d(P, \Delta) = \frac{\|\vec{P_0 P} \times \mathbf{v}\|}{\|\mathbf{v}\|}$$
3. **Khoảng cách giữa hai đường thẳng chéo nhau** $\Delta_1(P_1, \mathbf{v}_1)$ và $\Delta_2(P_2, \mathbf{v}_2)$:
   $$d(\Delta_1, \Delta_2) = \frac{|(\mathbf{v}_1 \times \mathbf{v}_2) \cdot \vec{P_1 P_2}|}{\|\mathbf{v}_1 \times \mathbf{v}_2\|}$$

---

## 4. Các mặt bậc hai (Quadric Surfaces)

Phương trình tổng quát bậc 2 trong không gian: $Ax^2 + By^2 + Cz^2 + \dots = 0$.

| Tên mặt | Phương trình chuẩn | Hình dáng đặc trưng & Nhận dạng |
|---|---|---|
| **Ellipsoid** | $\frac{x^2}{a^2} + \frac{y^2}{b^2} + \frac{z^2}{c^2} = 1$ | Quả bóng bầu dục; cả 3 hệ số bậc 2 đều dương. |
| **Paraboloid Elliptic** | $\frac{z}{c} = \frac{x^2}{a^2} + \frac{y^2}{b^2}$ | Cái bát ngửa/úp (chảo parabol); 2 biến bậc 2 cùng dấu, 1 biến bậc 1. |
| **Paraboloid Hyperbolic** | $\frac{z}{c} = \frac{x^2}{a^2} - \frac{y^2}{b^2}$ | Yên ngựa (Pringle chip); 2 biến bậc 2 trái dấu, 1 biến bậc 1. |
| **Mặt nón (Cone)** | $\frac{z^2}{c^2} = \frac{x^2}{a^2} + \frac{y^2}{b^2}$ | Hai chóp nón đối đỉnh tại gốc; đỉnh tại gốc tọa độ. |
| **Hyperboloid 1 tầng** | $\frac{x^2}{a^2} + \frac{y^2}{b^2} - \frac{z^2}{c^2} = 1$ | Ống thắt đáy lưng ong (tháp làm mát); **1 dấu trừ**, trục dọc theo biến mang dấu trừ. |
| **Hyperboloid 2 tầng** | $-\frac{x^2}{a^2} - \frac{y^2}{b^2} + \frac{z^2}{c^2} = 1$ | Hai mảnh chén tách rời nhau; **2 dấu trừ**, trục dọc theo biến mang dấu cộng. |
| **Mặt trụ (Cylinder)** | $x^2 + y^2 = R^2$ hoặc $z = x^2$ | Khuyết hẳn 1 biến trong phương trình; đường sinh song song với trục khuyết. |

> [!tip] Mẹo nhận dạng cực nhanh khi làm bài tích phân bội
> - Nếu thấy $z = x^2 + y^2$: Paraboloid tròn xoay đỉnh tại $(0,0,0)$, mở lên trên.
> - Nếu thấy $z = \sqrt{x^2 + y^2}$: Mặt nón nửa trên ($z \ge 0$), góc mở $45^\circ$.
> - Nếu thấy $z = \sqrt{R^2 - x^2 - y^2}$: Bán cầu trên tâm gốc, bán kính $R$.
