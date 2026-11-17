# Chương 6 - Phương trình vi phân cấp 2

Quay lại: [[MOC - Giải tích 2]]

> [!abstract] Mục tiêu chương 6
> Nắm vững cấu trúc nghiệm của phương trình vi phân tuyến tính cấp 2; phương pháp tìm nghiệm của phương trình hệ số hằng (thuần nhất & không thuần nhất); ứng dụng vào dao động cơ học lò xo và mạch điện RLC; phương pháp giải bằng chuỗi lũy thừa tại điểm chính quy.

---

## 1. Phương trình vi phân tuyến tính cấp 2 thuần nhất hệ số hằng

Dạng phương trình:
$$a y'' + b y' + c y = 0 \quad (a \neq 0,\; a, b, c \in \mathbb{R})$$
- Xét **Phương trình đặc trưng**:
  $$a r^2 + b r + c = 0, \quad \Delta = b^2 - 4ac$$

| Biệt thức $\Delta$ | Nghiệm đặc trưng $r$ | Nghiệm tổng quát $y(x)$ |
|---|---|---|
| $\Delta > 0$ | Hai nghiệm thực phân biệt $r_1 \neq r_2$ | $y(x) = c_1 e^{r_1 x} + c_2 e^{r_2 x}$ |
| $\Delta = 0$ | Nghiệm kép thực $r_1 = r_2 = r = -\frac{b}{2a}$ | $y(x) = (c_1 + c_2 x) e^{r x}$ |
| $\Delta < 0$ | Cặp nghiệm phức liên hợp $r = \alpha \pm i\beta$ | $y(x) = e^{\alpha x} (c_1 \cos\beta x + c_2 \sin\beta x)$ |

---

## 2. Phương trình tuyến tính cấp 2 không thuần nhất

Dạng phương trình:
$$a y'' + b y' + c y = G(x)$$
- **Cấu trúc nghiệm tổng quát**:
  $$y(x) = y_h(x) + y_p(x)$$
  Trong đó:
  - $y_h(x)$: Nghiệm tổng quát của phương trình thuần nhất tương ứng ($ay'' + by' + cy = 0$).
  - $y_p(x)$: Một nghiệm riêng bất kỳ của phương trình không thuần nhất.

### 2.1. Phương pháp hệ số bất định (Dùng cho hàm đặc biệt)

| Vế phải $G(x)$ | Dạng nghiệm riêng $y_p(x)$ | Quy tắc số mũ $s$ |
|---|---|---|
| $P_n(x) e^{\alpha x}$ | $y_p(x) = x^s Q_n(x) e^{\alpha x}$ | - $s = 0$ nếu $\alpha$ không là nghiệm PT đặc trưng.<br>- $s = 1$ nếu $\alpha$ là nghiệm đơn.<br>- $s = 2$ nếu $\alpha$ là nghiệm kép. |
| $e^{\alpha x} [P_m(x) \cos\beta x + Q_n(x) \sin\beta x]$ | $y_p(x) = x^s e^{\alpha x} [A_k(x) \cos\beta x + B_k(x) \sin\beta x]$<br>*(với $k = \max(m, n)$)* | - $s = 0$ nếu $\alpha + i\beta$ không là nghiệm PT đặc trưng.<br>- $s = 1$ nếu $\alpha + i\beta$ là nghiệm PT đặc trưng. |

### 2.2. Phương pháp biến thiên hằng số (Variation of Parameters)
Áp dụng cho mọi vế phải $G(x)$ liên tục (như $\tan x, \sec x, \frac{1}{1+e^x}, \dots$).
- Đưa về dạng chuẩn: $y'' + P(x) y' + Q(x) y = \frac{G(x)}{a}$.
- Đặt định thức Wronskian của 2 nghiệm thuần nhất $y_1, y_2$:
  $$W(y_1, y_2) = \begin{vmatrix} y_1 & y_2 \\ y_1' & y_2' \end{vmatrix} = y_1 y_2' - y_2 y_1'$$
- Nghiệm riêng có dạng $y_p(x) = u_1(x) y_1(x) + u_2(x) y_2(x)$, với $u_1, u_2$ thỏa mãn:
  $$u_1'(x) = \frac{-y_2(x) G(x)}{a\, W(y_1, y_2)}, \quad u_2'(x) = \frac{y_1(x) G(x)}{a\, W(y_1, y_2)}$$
- Lấy nguyên hàm để suy ra $u_1(x), u_2(x)$.

---

## 3. Ứng dụng dao động cơ học & Mạch điện RLC

### 3.1. Mô hình dao động con lắc lò xo
$$m \frac{d^2 x}{dt^2} + c \frac{dx}{dt} + k x = F(t)$$
- $m > 0$: Khối lượng vật nặng.
- $c \ge 0$: Hệ số cản môi trường (ma sát).
- $k > 0$: Độ cứng của lò xo.
- $F(t)$: Ngoại lực tuần hoàn tác dụng.

#### Các chế độ dao động tự do ($F(t) = 0$):
1. **Không cản ($c = 0$)**: Dao động điều hòa đơn với tần số góc riêng $\omega_0 = \sqrt{\frac{k}{m}}$:
   $$x(t) = c_1 \cos\omega_0 t + c_2 \sin\omega_0 t = A \cos(\omega_0 t - \delta)$$
2. **Có cản ($c > 0$)**:
   - $c^2 - 4mk > 0$: **Tắt dần quá mức (Overdamping)** (không có dao động, từ từ về 0).
   - $c^2 - 4mk = 0$: **Tắt dần tới hạn (Critical damping)** (về vị trí cân bằng nhanh nhất).
   - $c^2 - 4mk < 0$: **Tắt dần dao động (Underdamping)**:
     $$x(t) = e^{-\gamma t} A \cos(\omega_1 t - \delta) \quad \text{với } \gamma = \frac{c}{2m},\; \omega_1 = \sqrt{\omega_0^2 - \gamma^2}$$
3. **Hiện tượng cộng hưởng (Resonance)**: Khi không có cản ($c = 0$) và ngoại lực tuần hoàn $F(t) = F_0 \cos\omega t$ có tần số bằng đúng tần số riêng ($\omega = \omega_0$), nghiệm riêng xuất hiện thừa số $t \sin\omega_0 t$, làm biên độ tăng vô hạn theo thời gian.

### 3.2. Mạch điện RLC nối tiếp
$$L \frac{d^2 Q}{dt^2} + R \frac{dQ}{dt} + \frac{1}{C} Q = E(t)$$
*(Tương đồng hoàn toàn: $L \leftrightarrow m$, $R \leftrightarrow c$, $\frac{1}{C} \leftrightarrow k$, điện tích $Q \leftrightarrow$ li độ $x$)*.

---

## 4. Phương pháp giải bằng chuỗi lũy thừa (Power Series Solutions)

Áp dụng giải phương trình tuyến tính hệ số biến thiên $P(x) y'' + Q(x) y' + R(x) y = 0$ tại điểm chính quy $x_0 = 0$ ($P(0) \neq 0$).

### Quy trình 5 bước thực hiện
1. **Giả sử nghiệm**:
   $$y(x) = \sum_{n=0}^\infty c_n x^n = c_0 + c_1 x + c_2 x^2 + \dots$$
2. **Tính đạo hàm**:
   $$y'(x) = \sum_{n=1}^\infty n c_n x^{n-1}, \quad y''(x) = \sum_{n=2}^\infty n(n-1) c_n x^{n-2}$$
3. **Thay vào phương trình vi phân**, phân phối các lũy thừa của $x$ vào từng tổng.
4. **Dịch chuyển chỉ số (Shift index)**: Đổi biến chỉ số sao cho mọi số hạng đều có chung dạng lũy thừa $x^k$.
5. **Đồng nhất hệ số**: Cho tổng các hệ số của mỗi $x^k$ bằng $0$ để rút ra **Hệ thức truy hồi (Recurrence Relation)**:
   $$c_{k+2} = \dots c_k \dots$$
6. **Khai triển các hệ số**: Tính $c_2, c_3, c_4, \dots$ theo 2 hằng số tự do $c_0, c_1$. Viết nghiệm tổng quát $y(x) = c_0 y_1(x) + c_1 y_2(x)$.
