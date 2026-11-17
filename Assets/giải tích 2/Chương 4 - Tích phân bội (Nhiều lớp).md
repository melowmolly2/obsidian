# Chương 4 - Tích phân bội (Nhiều lớp)

Quay lại: [[MOC - Giải tích 2]]

> [!abstract] Mục tiêu chương 4
> Thành thạo tính tích phân 2 lớp, 3 lớp trên các miền hình học phức tạp; kỹ năng đổi thứ tự lấy tích phân; chuyển đổi linh hoạt giữa hệ tọa độ Descartes, cực, trụ, cầu và phương pháp Jacobian tổng quát.

---

## 1. Tích phân 2 lớp trên $\mathbb{R}^2$

### 1.1. Định nghĩa & Định lý Fubini
- **Tích phân trên hình chữ nhật $R = [a, b] \times [c, d]$**:
  $$\iint_R f(x,y)\,dA = \int_a^b \left[ \int_c^d f(x,y)\,dy \right] dx = \int_c^d \left[ \int_a^b f(x,y)\,dx \right] dy$$
- Nếu hàm số tách biến được: $f(x,y) = g(x)h(y)$ thì:
  $$\iint_R g(x)h(y)\,dA = \left(\int_a^b g(x)\,dx\right) \left(\int_c^d h(y)\,dy\right)$$

### 1.2. Miền tổng quát & Đổi thứ tự lấy tích phân
- **Miền loại I (Chiếu xuống trục $Ox$)**: $D = \{(x,y) \mid a \le x \le b,\; g_1(x) \le y \le g_2(x)\}$
  $$\iint_D f(x,y)\,dA = \int_a^b \left( \int_{g_1(x)}^{g_2(x)} f(x,y)\,dy \right) dx$$
- **Miền loại II (Chiếu xuống trục $Oy$)**: $D = \{(x,y) \mid c \le y \le d,\; h_1(y) \le x \le h_2(y)\}$
  $$\iint_D f(x,y)\,dA = \int_c^d \left( \int_{h_1(y)}^{h_2(y)} f(x,y)\,dx \right) dy$$

> [!tip] Thuật toán đổi thứ tự lấy tích phân
> 1. Rút ra các bất đẳng thức biên từ cận tích phân ban đầu.
> 2. Phác họa hình vẽ miền $D$ trên mặt phẳng $Oxy$.
> 3. Cắt miền theo chiều còn lại (từ dưới lên hoặc từ trái sang phải) để thiết lập cận mới.

---

## 2. Tọa độ cực (Polar Coordinates)

Sử dụng khi miền $D$ có chứa hình tròn, hình quạt hoặc biểu thức xuất hiện $x^2 + y^2$.
- **Công thức đổi biến**:
  $$\begin{cases} x = r\cos\theta \\ y = r\sin\theta \end{cases} \implies x^2 + y^2 = r^2$$
- **Yếu tố diện tích (Jacobian)**:
  $$dA = dx\,dy = r\,dr\,d\theta \quad \text{(Lưu ý nhân thêm } r\text{)}$$
- **Công thức**:
  $$\iint_D f(x,y)\,dA = \int_{\alpha}^{\beta} \int_{h_1(\theta)}^{h_2(\theta)} f(r\cos\theta, r\sin\theta)\,r\,dr\,d\theta$$

---

## 3. Ứng dụng hình học và vật lý của tích phân 2 lớp

1. **Diện tích miền phẳng**: $A(D) = \iint_D 1\,dA$.
2. **Thể tích vật thể**: $V = \iint_D [z_{\text{trên}}(x,y) - z_{\text{dưới}}(x,y)]\,dA$.
3. **Khối lượng tấm phẳng** có mật độ diện tích $\rho(x,y)$:
   $$m = \iint_D \rho(x,y)\,dA$$
4. **Trọng tâm (Center of Mass) $(\bar{x}, \bar{y})$**:
   $$\bar{x} = \frac{M_y}{m} = \frac{1}{m} \iint_D x\,\rho(x,y)\,dA, \quad \bar{y} = \frac{M_x}{m} = \frac{1}{m} \iint_D y\,\rho(x,y)\,dA$$
5. **Mômen quán tính**:
   $$I_x = \iint_D y^2 \rho(x,y)\,dA, \quad I_y = \iint_D x^2 \rho(x,y)\,dA, \quad I_0 = I_x + I_y = \iint_D (x^2 + y^2)\rho(x,y)\,dA$$

---

## 4. Diện tích mặt cong (Surface Area)

Cho mặt cong $S$ có phương trình $z = f(x,y)$ với $(x,y) \in D$:
$$A(S) = \iint_D \sqrt{1 + \left(\frac{\partial f}{\partial x}\right)^2 + \left(\frac{\partial f}{\partial y}\right)^2}\,dA$$
- Nếu mặt cho dạng ẩn $F(x,y,z) = 0$: $dS = \frac{\|\nabla F\|}{|F_z|}\,dx\,dy$.

---

## 5. Tích phân 3 lớp trên $\mathbb{R}^3$

### 5.1. Tọa độ Descartes
Chiếu khối $E$ xuống mặt phẳng $Oxy$ thành miền $D$:
$$\iiint_E f(x,y,z)\,dV = \iint_D \left( \int_{u_1(x,y)}^{u_2(x,y)} f(x,y,z)\,dz \right) dA$$

### 5.2. Tọa độ trụ (Cylindrical Coordinates)
Rất hiệu quả cho vật thể quay quanh trục $Oz$ (mặt trụ, nón, paraboloid):
$$\begin{cases} x = r\cos\theta \\ y = r\sin\theta \\ z = z \end{cases} \implies dV = r\,dz\,dr\,d\theta$$
$$\iiint_E f(x,y,z)\,dV = \int_\alpha^\beta \int_{h_1(\theta)}^{h_2(\theta)} \int_{u_1(r\cos\theta, r\sin\theta)}^{u_2(r\cos\theta, r\sin\theta)} f(r\cos\theta, r\sin\theta, z)\,r\,dz\,dr\,d\theta$$

### 5.3. Tọa độ cầu (Spherical Coordinates)
Rất hiệu quả cho khối cầu, hình chóp nón đỉnh gốc tọa độ:
$$\begin{cases} x = \rho \sin\phi \cos\theta \\ y = \rho \sin\phi \sin\theta \\ z = \rho \cos\phi \end{cases} \quad (\rho \ge 0,\; 0 \le \phi \le \pi,\; 0 \le \theta \le 2\pi)$$
- Hệ thức: $\rho^2 = x^2 + y^2 + z^2$ và $x^2 + y^2 = \rho^2 \sin^2\phi$.
- **Yếu tố thể tích (Jacobian)**:
  $$dV = \rho^2 \sin\phi\,d\rho\,d\phi\,d\theta$$

> [!tip] Mẹo nhớ góc $\phi$ và $\theta$ trong tọa độ cầu
> - $\theta$: góc quét trong mặt phẳng $Oxy$ (từ $0$ đến $2\pi$).
> - $\phi$: góc hạ từ cực bắc (trục $Oz$ dương) xuống cực nam:
>   - Trục $Oz$ dương: $\phi = 0$.
>   - Mặt phẳng $Oxy$: $\phi = \frac{\pi}{2}$.
>   - Nón $z = \sqrt{x^2 + y^2} \implies \phi = \frac{\pi}{4}$.
>   - Nón $z = \sqrt{3(x^2 + y^2)} \implies \phi = \frac{\pi}{6}$.

---

## 6. Đổi biến tổng quát - Định thức Jacobi (Jacobian)

### 6.1. Không gian 2 chiều
Đổi biến $x = g(u,v), y = h(u,v)$:
$$J = \frac{\partial(x,y)}{\partial(u,v)} = \begin{vmatrix} \frac{\partial x}{\partial u} & \frac{\partial x}{\partial v} \\ \frac{\partial y}{\partial u} & \frac{\partial y}{\partial v} \end{vmatrix} = \frac{\partial x}{\partial u}\frac{\partial y}{\partial v} - \frac{\partial x}{\partial v}\frac{\partial y}{\partial u}$$
$$\iint_R f(x,y)\,dx\,dy = \iint_S f(x(u,v), y(u,v)) \left| \frac{\partial(x,y)}{\partial(u,v)} \right| du\,dv$$

### 6.2. Tính chất nghịch đảo Jacobian
$$\frac{\partial(x,y)}{\partial(u,v)} = \frac{1}{\frac{\partial(u,v)}{\partial(x,y)}}$$
*(Cực kỳ hữu ích khi ta biết $u = u(x,y), v = v(x,y)$ nhưng khó rút $x,y$ ngược lại).*
