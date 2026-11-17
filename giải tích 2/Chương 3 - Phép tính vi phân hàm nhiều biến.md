# Chương 3 - Phép tính vi phân hàm nhiều biến

Quay lại: [[MOC - Giải tích 2]]

> [!abstract] Mục tiêu chương 3
> Nghiên cứu vi phân của hàm $z = f(x,y)$ và $w = f(x,y,z)$: giới hạn đa chiều, đạo hàm riêng, vi phân toàn phần, quy tắc chuỗi, đạo hàm theo hướng, gradient và bài toán tối ưu hóa (cực trị tự do và cực trị có ràng buộc Lagrange).

---

## 1. Giới hạn và Tính liên tục của hàm nhiều biến

### 1.1. Cách chứng minh giới hạn không tồn tại
$$\lim_{(x,y) \to (0,0)} f(x,y)$$
> [!tip] Phương pháp 2 quỹ đạo
> Cho $(x,y) \to (0,0)$ theo các hướng khác nhau:
> 1. Theo chùm đường thẳng: $y = mx$. Nếu giới hạn phụ thuộc vào tham số $m \implies$ Giới hạn không tồn tại.
> 2. Theo đường cong bậc cao: $y = kx^2$ hoặc $x = ky^2$ (dùng khi bậc của $x$ và $y$ ở mẫu số không đều nhau).

### 1.2. Cách tính giới hạn khi tồn tại
- **Đổi sang tọa độ cực**: Đặt $x = r\cos\theta, y = r\sin\theta$. Khi $(x,y) \to (0,0) \iff r \to 0^+$.
  Nếu biểu thức đưa về dạng $g(r) h(\theta)$ với $h(\theta)$ bị chặn và $\lim_{r \to 0^+} g(r) = 0 \implies \lim = 0$.
- **Nguyên lý kẹp**: $|f(x,y) - L| \le g(x,y)$ với $\lim_{(x,y)\to(a,b)} g(x,y) = 0$.

---

## 2. Đạo hàm riêng và Vi phân toàn phần

### 2.1. Đạo hàm riêng
- $f_x(x,y) = \frac{\partial f}{\partial x}$: Coi $y$ là hằng số, lấy đạo hàm bình thường theo $x$.
- $f_y(x,y) = \frac{\partial f}{\partial y}$: Coi $x$ là hằng số, lấy đạo hàm bình thường theo $y$.
- **Định lý Clairaut (Đạo hàm hỗn hợp bằng nhau)**:
  Nếu các đạo hàm riêng cấp hai $f_{xy}$ và $f_{yx}$ liên tục trên miền lân cận thì:
  $$f_{xy} = f_{yx} \quad \left(\frac{\partial^2 f}{\partial y \partial x} = \frac{\partial^2 f}{\partial x \partial y}\right)$$

### 2.2. Mặt phẳng tiếp xúc & Xấp xỉ tuyến tính
Cho mặt phẳng tiếp xúc với mặt cong $z = f(x,y)$ tại điểm $P_0(x_0, y_0, z_0)$:
$$z - z_0 = f_x(x_0, y_0)(x - x_0) + f_y(x_0, y_0)(y - y_0)$$
- **Xấp xỉ tuyến tính (Linearization)**:
  $$L(x,y) = f(x_0, y_0) + f_x(x_0, y_0)(x - x_0) + f_y(x_0, y_0)(y - y_0)$$
- **Vi phân toàn phần**:
  $$dz = \frac{\partial f}{\partial x} dx + \frac{\partial f}{\partial y} dy$$
  Ứng dụng ước lượng sai số: $\Delta z \approx dz = f_x \Delta x + f_y \Delta y$.

---

## 3. Quy tắc chuỗi (Chain Rule) & Đạo hàm hàm ẩn

### 3.1. Quy tắc chuỗi
- **Trường hợp 1 biến độc lập**: $z = f(x,y)$ với $x = g(t), y = h(t)$:
  $$\frac{dz}{dt} = \frac{\partial f}{\partial x} \frac{dx}{dt} + \frac{\partial f}{\partial y} \frac{dy}{dt}$$
- **Trường hợp nhiều biến độc lập**: $z = f(x,y)$ với $x = g(u,v), y = h(u,v)$:
  $$\frac{\partial z}{\partial u} = \frac{\partial z}{\partial x}\frac{\partial x}{\partial u} + \frac{\partial z}{\partial y}\frac{\partial y}{\partial u}, \quad \frac{\partial z}{\partial v} = \frac{\partial z}{\partial x}\frac{\partial x}{\partial v} + \frac{\partial z}{\partial y}\frac{\partial y}{\partial v}$$

### 3.2. Đạo hàm của hàm ẩn
- Nếu phương trình $F(x,y) = 0$ xác định ẩn $y = y(x)$ và $F_y \neq 0$:
  $$\frac{dy}{dx} = -\frac{F_x}{F_y}$$
- Nếu phương trình $F(x,y,z) = 0$ xác định ẩn $z = z(x,y)$ và $F_z \neq 0$:
  $$\frac{\partial z}{\partial x} = -\frac{F_x}{F_z}, \quad \frac{\partial z}{\partial y} = -\frac{F_y}{F_z}$$

---

## 4. Đạo hàm theo hướng (Directional Derivative) & Gradient

### 4.1. Véc-tơ Gradient
$$\nabla f(x,y) = \left\langle \frac{\partial f}{\partial x}, \frac{\partial f}{\partial y} \right\rangle = f_x \mathbf{i} + f_y \mathbf{j}$$
(Với hàm 3 biến: $\nabla f(x,y,z) = \langle f_x, f_y, f_z \rangle$).

### 4.2. Đạo hàm theo hướng của véc-tơ đơn vị $\mathbf{u} = \langle a, b \rangle$ ($\|\mathbf{u}\| = 1$)
$$D_{\mathbf{u}}f(x_0, y_0) = \nabla f(x_0, y_0) \cdot \mathbf{u} = f_x(x_0, y_0)a + f_y(x_0, y_0)b$$

> [!warning] Bẫy thi kinh điển!
> Đề bài cho véc-tơ $\mathbf{v}$ bất kỳ, **bắt buộc phải chuẩn hóa** thành véc-tơ đơn vị $\mathbf{u} = \frac{\mathbf{v}}{\|\mathbf{v}\|}$ trước khi nhân tích vô hướng!

### 4.3. Ý nghĩa hình học của Gradient
1. **Hướng tăng nhanh nhất** của hàm số $f$ tại một điểm chính là hướng của véc-tơ gradient $\nabla f$. Giá trị tốc độ tăng cực đại là:
   $$\max D_{\mathbf{u}}f = \|\nabla f\|$$
2. **Hướng giảm nhanh nhất** là hướng $-\nabla f$ với tốc độ $-\|\nabla f\|$.
3. **Phương pháp tuyến với mặt mức**:
   Véc-tơ $\nabla F(x_0, y_0, z_0)$ luôn vuông góc với mặt mức $F(x,y,z) = k$ tại điểm $(x_0, y_0, z_0)$.
   - Phương trình mặt phẳng tiếp xúc với mặt mức $F(x,y,z) = k$:
     $$F_x(x_0, y_0, z_0)(x - x_0) + F_y(x_0, y_0, z_0)(y - y_0) + F_z(x_0, y_0, z_0)(z - z_0) = 0$$

---

## 5. Cực trị của hàm nhiều biến

### 5.1. Cực trị tự do (Hàm 2 biến)
- **Bước 1**: Tìm các điểm tới hạn (Critical Points) giải hệ:
  $$\begin{cases} f_x(x,y) = 0 \\ f_y(x,y) = 0 \end{cases}$$
- **Bước 2**: Xét dấu biệt thức Hessian tại từng điểm tới hạn $(a,b)$:
  Đặt $A = f_{xx}(a,b),\; B = f_{xy}(a,b),\; C = f_{yy}(a,b)$.
  $$D = AC - B^2 = f_{xx} f_{yy} - (f_{xy})^2$$
  - Nếu $D > 0$ và $A > 0$: Hàm đạt **Cực tiểu địa phương** tại $(a,b)$.
  - Nếu $D > 0$ và $A < 0$: Hàm đạt **Cực đại địa phương** tại $(a,b)$.
  - Nếu $D < 0$: Điểm $(a,b)$ là **Điểm yên ngựa (Saddle Point)** (không là cực trị).
  - Nếu $D = 0$: **Chưa có kết luận** (cần dùng khai triển Taylor hoặc xét lân cận).

### 5.2. Giá trị lớn nhất & nhỏ nhất trên tập đóng và bị chặn $D$
1. Tìm điểm tới hạn nằm **bên trong** $D$ và tính giá trị của $f$.
2. Tìm GTLN, GTNN của $f$ trên **biên** của $D$ (thường tham số hóa đường biên thành hàm 1 biến).
3. So sánh các giá trị để kết luận $\max_D f$ và $\min_D f$.

### 5.3. Cực trị có điều kiện - Phương pháp nhân tử Lagrange
Bài toán: Tìm cực trị của $f(x,y,z)$ thỏa mãn ràng buộc $g(x,y,z) = k$.
- **Hệ phương trình Lagrange**:
  $$\begin{cases} \nabla f(x,y,z) = \lambda \nabla g(x,y,z) \\ g(x,y,z) = k \end{cases} \iff \begin{cases} f_x = \lambda g_x \\ f_y = \lambda g_y \\ f_z = \lambda g_z \\ g(x,y,z) = k \end{cases}$$
- Nếu có hai điều kiện ràng buộc $g(x,y,z) = k$ và $h(x,y,z) = c$:
  $$\nabla f = \lambda \nabla g + \mu \nabla h$$
