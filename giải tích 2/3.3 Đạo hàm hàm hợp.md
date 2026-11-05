

Đây là tóm tắt lý thuyết **Chương 3.3** — Đạo hàm hàm hợp, đạo hàm theo hướng, gradient, hàm ẩn.

---

## 4. Đạo hàm của hàm hợp (Chain Rule)

### Version 1: $z = f(x,y)$, $x = g(t)$, $y = h(t)$

$$\frac{dz}{dt} = \frac{\partial f}{\partial x}\frac{dx}{dt} + \frac{\partial f}{\partial y}\frac{dy}{dt}$$

### Version 2: $z = f(x,y)$, $x = g(s,t)$, $y = h(s,t)$

$$\frac{\partial z}{\partial s} = \frac{\partial z}{\partial x}\frac{\partial x}{\partial s} + \frac{\partial z}{\partial y}\frac{\partial y}{\partial s}, \qquad \frac{\partial z}{\partial t} = \frac{\partial z}{\partial x}\frac{\partial x}{\partial t} + \frac{\partial z}{\partial y}\frac{\partial y}{\partial t}$$

---

## 5. Đạo hàm riêng của hàm ẩn

### Hàm ẩn 1 biến: $F(x,y) = 0 \Rightarrow y = f(x)$

$$\frac{dy}{dx} = -\frac{F_x}{F_y} \quad (\text{với } F_y \neq 0)$$

**Điều kiện tồn tại (Định lý hàm ẩn):** $F(a,b)=0$, $F_y(a,b)\neq 0$, $F_x, F_y$ liên tục trên lân cận của $(a,b)$.

### Hàm ẩn 2 biến: $F(x,y,z) = 0 \Rightarrow z = f(x,y)$

$$\frac{\partial z}{\partial x} = -\frac{F_x}{F_z}, \qquad \frac{\partial z}{\partial y} = -\frac{F_y}{F_z} \quad (\text{với } F_z \neq 0)$$

---

## 6. Đạo hàm theo hướng & Gradient

### Định nghĩa đạo hàm theo hướng

Với $\mathbf{u} = (a,b)$ là vector đơn vị:

$$D_{\mathbf{u}}f(x_0,y_0) = \lim_{h\to 0} \frac{f(x_0+ha,\, y_0+hb) - f(x_0,y_0)}{h}$$

### Công thức tính (nếu $f$ khả vi)

$$D_{\mathbf{u}}f(x,y) = f_x(x,y)\,a + f_y(x,y)\,b$$

Nếu $\mathbf{u}$ tạo góc $\theta$ với $Ox$:

$$D_{\mathbf{u}}f(x,y) = f_x\cos\theta + f_y\sin\theta$$

### Vector Gradient

$$\nabla f(x,y) = \bigl(f_x(x,y),\, f_y(x,y)\bigr)$$

Từ đó: $D_{\mathbf{u}}f = \nabla f \cdot \mathbf{u}$

Với hàm 3 biến: $\nabla f = (f_x, f_y, f_z)$, và $D_{\mathbf{u}}f = \nabla f \cdot \mathbf{u}$.

### Giá trị lớn nhất của đạo hàm theo hướng

$$\max_{\mathbf{u}} D_{\mathbf{u}}f(\mathbf{x}) = \|\nabla f(\mathbf{x})\|$$

đạt được khi $\mathbf{u}$ **cùng hướng** với $\nabla f$.

> **Hệ quả:** $f$ giảm nhanh nhất theo hướng $-\nabla f$ — cơ sở của **Gradient Descent**.

---

## 7. Mặt phẳng tiếp xúc & Pháp tuyến với mặt mức

Mặt $S$: $F(x,y,z) = k$, điểm $P(x_0,y_0,z_0)$.

- Vector pháp tuyến: $\nabla F(x_0,y_0,z_0)$
- **Mặt phẳng tiếp xúc:**

$$F_x(x_0,y_0,z_0)(x-x_0) + F_y(x_0,y_0,z_0)(y-y_0) + F_z(x_0,y_0,z_0)(z-z_0) = 0$$

- **Đường pháp tuyến:**

$$\frac{x-x_0}{F_x} = \frac{y-y_0}{F_y} = \frac{z-z_0}{F_z}$$

---

## Gradient Descent (GD)

Thuật toán tối thiểu hóa $\min f(\mathbf{x})$ bằng cập nhật lặp:

$$\mathbf{x}_{n+1} = \mathbf{x}_n - \eta\,\nabla f(\mathbf{x}_n)$$

$\eta > 0$: **learning rate**. Dừng khi $\|\nabla J(\theta)\| < \varepsilon$. Ứng dụng rộng rãi trong ML (hồi quy, mạng nơ-ron).