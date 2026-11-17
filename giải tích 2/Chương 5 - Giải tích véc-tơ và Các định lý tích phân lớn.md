# Chương 5 - Giải tích véc-tơ và Các định lý tích phân lớn

Quay lại: [[MOC - Giải tích 2]]

> [!abstract] Mục tiêu chương 5
> Đây là đỉnh cao của chương trình Giải tích 2: làm chủ các khái niệm Trường véc-tơ, Toán tử Gradient, Curl, Div; phương pháp tính tích phân đường và tích phân mặt; và bộ 3 định lý thống nhất vi tích phân đa chiều: **Green - Stokes - Gauss**.

---

## 1. Tích phân đường (Line Integrals)

### 1.1. Tích phân đường loại 1 (Theo độ dài cung)
Tính khối lượng dây hoặc tích phân hàm vô hướng dọc theo đường cong $C: \mathbf{r}(t), t \in [a, b]$:
$$\int_C f(x,y,z)\,ds = \int_a^b f(\mathbf{r}(t)) \|\mathbf{r}'(t)\|\,dt = \int_a^b f(x(t), y(t), z(t)) \sqrt{(x')^2 + (y')^2 + (z')^2}\,dt$$
- **Tính chất**: Không phụ thuộc vào chiều đi trên đường cong ($\int_{-C} f\,ds = \int_C f\,ds$).

### 1.2. Tích phân đường loại 2 (Theo tọa độ / Công của lực)
Tính công sinh bởi lực $\mathbf{F} = P\mathbf{i} + Q\mathbf{j} + R\mathbf{k}$ dọc theo quỹ đạo $C$:
$$\int_C \mathbf{F} \cdot d\mathbf{r} = \int_C P\,dx + Q\,dy + R\,dz = \int_a^b \left[ P(t)\frac{dx}{dt} + Q(t)\frac{dy}{dt} + R(t)\frac{dz}{dt} \right] dt$$
- **Tính chất**: Đổi chiều đi thì đổi dấu: $\int_{-C} \mathbf{F} \cdot d\mathbf{r} = -\int_C \mathbf{F} \cdot d\mathbf{r}$.

### 1.3. Định lý cơ bản cho tích phân đường (Trường bảo toàn)
Nếu trường véc-tơ $\mathbf{F}$ là một trường gradient: $\mathbf{F} = \nabla f$ (với $f$ là hàm thế vị - potential function):
$$\int_C \mathbf{F} \cdot d\mathbf{r} = \int_C \nabla f \cdot d\mathbf{r} = f(\mathbf{r}(b)) - f(\mathbf{r}(a))$$
- **Hệ quả**:
  1. Tích phân **độc lập với đường đi**, chỉ phụ thuộc vào điểm đầu và điểm cuối.
  2. Nếu $C$ là đường cong kín: $\oint_C \mathbf{F} \cdot d\mathbf{r} = 0$.

> [!tip] Dấu hiệu nhận biết và cách tìm hàm thế vị $f$
> - Trong $\mathbb{R}^2$: Trường $\mathbf{F} = \langle P, Q \rangle$ bảo toàn trên miền đơn liên $\iff \frac{\partial P}{\partial y} = \frac{\partial Q}{\partial x}$.
> - Trong $\mathbb{R}^3$: Trường $\mathbf{F} = \langle P, Q, R \rangle$ bảo toàn trên miền đơn liên $\iff \text{curl}\,\mathbf{F} = \mathbf{0}$.
> - **Tìm $f$**: Lấy tích phân $f(x,y) = \int P\,dx + g(y)$, sau đó đạo hàm theo $y$ để đồng nhất $f_y = Q \implies g'(y)$.

---

## 2. Định lý Green trên mặt phẳng $\mathbb{R}^2$

Cho đường cong $C$ phẳng, kín, trơn từng khúc, bao quanh miền $D$ và định hướng dương (ngược chiều kim đồng hồ):
$$\oint_C P\,dx + Q\,dy = \iint_D \left( \frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y} \right) dA$$

### Ứng dụng tính diện tích miền $D$
$$A(D) = \oint_C x\,dy = -\oint_C y\,dx = \frac{1}{2} \oint_C (x\,dy - y\,dx)$$

---

## 3. Toán tử vi phân trường véc-tơ: Curl và Div

Toán tử Nabla: $\nabla = \left\langle \frac{\partial}{\partial x}, \frac{\partial}{\partial y}, \frac{\partial}{\partial z} \right\rangle$. Cho $\mathbf{F} = \langle P, Q, R \rangle$:

### 3.1. Curl (Độ xoáy / $\text{rot}$)
Đo xu hướng xoay quanh một trục của trường véc-tơ:
$$\text{curl}\,\mathbf{F} = \nabla \times \mathbf{F} = \begin{vmatrix} \mathbf{i} & \mathbf{j} & \mathbf{k} \\ \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \\ P & Q & R \end{vmatrix} = \left\langle \frac{\partial R}{\partial y} - \frac{\partial Q}{\partial z},\; \frac{\partial P}{\partial z} - \frac{\partial R}{\partial x},\; \frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y} \right\rangle$$

### 3.2. Divergence (Độ phân kỳ / $\text{div}$)
Đo mật độ thông lượng nguồn phát hoặc điểm hút vô hướng tại một điểm:
$$\text{div}\,\mathbf{F} = \nabla \cdot \mathbf{F} = \frac{\partial P}{\partial x} + \frac{\partial Q}{\partial y} + \frac{\partial R}{\partial z}$$

### 3.3. Hai đẳng thức vĩnh viễn (Phải thuộc lòng)
1. $\text{curl}(\nabla f) = \mathbf{0} \quad \text{(Mọi trường Gradient đều không có xoáy)}$.
2. $\text{div}(\text{curl}\,\mathbf{F}) = 0 \quad \text{(Mọi trường xoáy đều không có độ phân kỳ)}$.

---

## 4. Tích phân mặt (Surface Integrals)

### 4.1. Tích phân mặt loại 1 (Theo diện tích)
$$\iint_S f(x,y,z)\,dS = \iint_D f(\mathbf{r}(u,v)) \|\mathbf{r}_u \times \mathbf{r}_v\|\,du\,dv$$
- Nếu mặt cho bởi đồ thị $z = g(x,y)$:
  $$dS = \sqrt{1 + \left(\frac{\partial g}{\partial x}\right)^2 + \left(\frac{\partial g}{\partial y}\right)^2}\,dA$$

### 4.2. Tích phân mặt loại 2 (Thông lượng / Flux)
Thông lượng của trường $\mathbf{F}$ xuyên qua mặt định hướng $S$ có véc-tơ pháp tuyến đơn vị $\mathbf{n}$:
$$\iint_S \mathbf{F} \cdot d\mathbf{S} = \iint_S (\mathbf{F} \cdot \mathbf{n})\,dS$$
- Khi mặt cho bởi $z = g(x,y)$ với **pháp tuyến hướng lên trên**:
  $$\iint_S \mathbf{F} \cdot d\mathbf{S} = \iint_D \left( -P\frac{\partial g}{\partial x} - Q\frac{\partial g}{\partial y} + R \right) dA$$
  *(Nếu pháp tuyến hướng xuống dưới: nhân thêm dấu trừ vào toàn bộ tích phân).*

---

## 5. Hai định lý lớn: Stokes và Gauss-Ostrogradsky

### 5.1. Định lý Stokes (Mở rộng Green lên không gian 3D)
Liên hệ tích phân đường trên biên $C$ kín với tích phân mặt của xoáy trên mặt cong $S$ tựa lên biên đó:
$$\oint_C \mathbf{F} \cdot d\mathbf{r} = \iint_S (\text{curl}\,\mathbf{F}) \cdot d\mathbf{S}$$
- **Quy tắc bàn tay phải**: Nếu ngón tay khum theo chiều đi trên $C$, ngón cái chỉ chiều véc-tơ pháp tuyến $\mathbf{n}$ của $S$.
- **Ý nghĩa giải nhanh**: Ta có thể thay mặt $S$ phức tạp bằng bất kỳ mặt $S'$ nào đơn giản hơn (như mặt phẳng phẳng đậy nắp biên $C$) miễn là chung đường biên $C$!

### 5.2. Định lý Gauss - Ostrogradsky (Divergence Theorem)
Liên hệ tích phân mặt đóng $S$ (hướng ra ngoài) với tích phân 3 lớp trên khối $E$ được bao bọc:
$$\iint_S \mathbf{F} \cdot d\mathbf{S} = \iiint_E (\text{div}\,\mathbf{F})\,dV = \iiint_E \left( \frac{\partial P}{\partial x} + \frac{\partial Q}{\partial y} + \frac{\partial R}{\partial z} \right) dV$$

> [!summary] Bảng tổng kết nhận dạng khi làm bài thi
> | Biểu thức đề bài | Điều kiện hình học | Dùng ngay định lý |
> |---|---|---|
> | $\oint_C P\,dx + Q\,dy$ | Đường $C$ phẳng, kín | **Định lý Green** |
> | $\oint_C \mathbf{F} \cdot d\mathbf{r}$ trong $\mathbb{R}^3$ | Đường cong $C$ không gian, kín | **Định lý Stokes** |
> | $\iint_S \mathbf{F} \cdot d\mathbf{S}$ | Mặt $S$ **kín** (bao quanh hình khối $E$) | **Định lý Gauss** |
> | $\iint_S \mathbf{F} \cdot d\mathbf{S}$ | Mặt $S$ **hở**, trường có dạng $\mathbf{F} = \text{curl}\,\mathbf{G}$ | **Định lý Stokes** |
