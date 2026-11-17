# Chương 2 - Hàm véc-tơ và Chuyển động không gian

Quay lại: [[MOC - Giải tích 2]]

> [!abstract] Mục tiêu chương 2
> Nghiên cứu đường cong tham số trong không gian $\mathbb{R}^3$, vi tích phân của hàm véc-tơ, hình học vi phân (độ cong $\kappa$, khung Frenet $\mathbf{T}, \mathbf{N}, \mathbf{B}$) và cơ học chuyển động (phân tích gia tốc).

---

## 1. Định nghĩa và Vi tích phân của hàm véc-tơ

### 1.1. Khái niệm cơ bản
- Hàm véc-tơ: $\mathbf{r}(t) = \langle f(t), g(t), h(t) \rangle = f(t)\mathbf{i} + g(t)\mathbf{j} + h(t)\mathbf{k}$ với $t \in D \subseteq \mathbb{R}$.
- Miền xác định: $D = D_f \cap D_g \cap D_h$.
- Giới hạn & Tính liên tục: Tính theo từng thành phần độc lập.

### 1.2. Đạo hàm và Đường tiếp tuyến
$$\mathbf{r}'(t) = \lim_{h \to 0} \frac{\mathbf{r}(t+h) - \mathbf{r}(t)}{h} = \langle f'(t), g'(t), h'(t) \rangle$$
- $\mathbf{r}'(t)$ là **véc-tơ tiếp tuyến** với đường cong tại $\mathbf{r}(t)$ (chỉ theo chiều $t$ tăng).
- **Phương trình đường tiếp tuyến** tại $t = t_0$:
  $$\mathbf{L}(t) = \mathbf{r}(t_0) + t \mathbf{r}'(t_0)$$

### 1.3. Các quy tắc tính đạo hàm quan trọng
1. $[\mathbf{u}(t) \cdot \mathbf{v}(t)]' = \mathbf{u}'(t) \cdot \mathbf{v}(t) + \mathbf{u}(t) \cdot \mathbf{v}'(t)$
2. $[\mathbf{u}(t) \times \mathbf{v}(t)]' = \mathbf{u}'(t) \times \mathbf{v}(t) + \mathbf{u}(t) \times \mathbf{v}'(t)$ *(cần giữ đúng thứ tự tích có hướng!)*
3. **Định lý trực giao**: Nếu $\|\mathbf{r}(t)\| = c$ (hằng số không đổi) với mọi $t$, thì:
   $$\mathbf{r}'(t) \perp \mathbf{r}(t) \iff \mathbf{r}(t) \cdot \mathbf{r}'(t) = 0$$
   *(Ý nghĩa: Chuyển động trên mặt cầu thì véc-tơ vận tốc luôn tiếp xúc mặt cầu, vuông góc bán kính).*

---

## 2. Độ dài cung và Độ cong (Curvature)

### 2.1. Độ dài cung (Arc Length)
Độ dài đường cong từ $t = a$ đến $t = b$:
$$L = \int_a^b \|\mathbf{r}'(t)\|\,dt = \int_a^b \sqrt{[f'(t)]^2 + [g'(t)]^2 + [h'(t)]^2}\,dt$$
- Hàm độ dài cung: $s(t) = \int_{a}^t \|\mathbf{r}'(u)\|\,du \implies \frac{ds}{dt} = \|\mathbf{r}'(t)\|$.

### 2.2. Độ cong $\kappa$
Đo mức độ đổi hướng nhanh hay chậm của đường cong theo độ dài cung:
$$\kappa = \left\|\frac{d\mathbf{T}}{ds}\right\| = \frac{\|\mathbf{T}'(t)\|}{\|\mathbf{r}'(t)\|}$$

> [!tip] Công thức thực chiến tính độ cong $\kappa$ (Không cần tìm $\mathbf{T}$)
> Dùng công thức trực tiếp từ đạo hàm cấp 1 và cấp 2:
> $$\kappa(t) = \frac{\|\mathbf{r}'(t) \times \mathbf{r}''(t)\|}{\|\mathbf{r}'(t)\|^3}$$
> 
> Với đồ thị hàm phẳng $y = f(x)$:
> $$\kappa(x) = \frac{|f''(x)|}{\left[1 + (f'(x))^2\right]^{3/2}}$$

---

## 3. Khung tọa độ động Frenet - Serret & Các mặt phẳng

Tại mỗi điểm chính quy ($\mathbf{r}'(t) \neq \mathbf{0}, \kappa \neq 0$), ta xác định hệ tam diện trực chuẩn:
1. **Véc-tơ tiếp tuyến đơn vị**:
   $$\mathbf{T}(t) = \frac{\mathbf{r}'(t)}{\|\mathbf{r}'(t)\|}$$
2. **Véc-tơ pháp tuyến chính đơn vị**:
   $$\mathbf{N}(t) = \frac{\mathbf{T}'(t)}{\|\mathbf{T}'(t)\|}$$
3. **Véc-tơ song pháp tuyến đơn vị**:
   $$\mathbf{B}(t) = \mathbf{T}(t) \times \mathbf{N}(t) = \frac{\mathbf{r}'(t) \times \mathbf{r}''(t)}{\|\mathbf{r}'(t) \times \mathbf{r}''(t)\|}$$

### Ba mặt phẳng cơ bản tại điểm $P_0$
| Tên mặt phẳng | Véc-tơ pháp tuyến | Chứa hai véc-tơ | Ứng dụng |
|---|---|---|---|
| **Mặt phẳng pháp tuyến (Normal plane)** | $\mathbf{T}$ (hoặc $\mathbf{r}'(t_0)$) | $\mathbf{N}, \mathbf{B}$ | Vuông góc quỹ đạo chuyển động |
| **Mặt phẳng mật tiếp (Osculating plane)** | $\mathbf{B}$ (hoặc $\mathbf{r}' \times \mathbf{r}''$) | $\mathbf{T}, \mathbf{N}$ | Mặt phẳng bám sát đường cong nhất |
| **Mặt phẳng trực đối (Rectifying plane)**| $\mathbf{N}$ | $\mathbf{T}, \mathbf{B}$ | Mặt phẳng chứa tiếp tuyến & song pháp |

### Đường tròn mật tiếp (Osculating Circle)
- Bán kính cong: $\rho = \frac{1}{\kappa}$.
- Tâm cong: $C = P_0 + \rho \mathbf{N}$.
- Nằm hoàn toàn trong mặt phẳng mật tiếp.

---

## 4. Chuyển động trong không gian: Vận tốc và Gia tốc

- Véc-tơ vận tốc: $\mathbf{v}(t) = \mathbf{r}'(t)$.
- Tốc độ (độ lớn vận tốc): $v(t) = \|\mathbf{v}(t)\| = \frac{ds}{dt}$.
- Véc-tơ gia tốc: $\mathbf{a}(t) = \mathbf{v}'(t) = \mathbf{r}''(t)$.

### Phân tích gia tốc thành thành phần tiếp tuyến và pháp tuyến
$$\mathbf{a} = a_T \mathbf{T} + a_N \mathbf{N}$$
*(Lưu ý: Gia tốc không có thành phần theo $\mathbf{B}$, tức là luôn nằm trong mặt phẳng mật tiếp).*

Công thức tính nhanh $a_T$ và $a_N$:
$$a_T = v' = \frac{\mathbf{r}'(t) \cdot \mathbf{r}''(t)}{\|\mathbf{r}'(t)\|}$$
$$a_N = \kappa v^2 = \frac{\|\mathbf{r}'(t) \times \mathbf{r}''(t)\|}{\|\mathbf{r}'(t)\|}$$
Kiểm tra lại: $\|\mathbf{a}\|^2 = a_T^2 + a_N^2$.

---

## 5. Các định luật Kepler về chuyển động hành tinh
1. **Định luật 1 (Quỹ đạo)**: Quỹ đạo của mỗi hành tinh là một đường Elip với Mặt Trời nằm tại một trong hai tiêu điểm.
2. **Định luật 2 (Diện tích)**: Véc-tơ bán kính từ Mặt Trời đến hành tinh quét những diện tích bằng nhau trong những khoảng thời gian bằng nhau ($\frac{dA}{dt} = \frac{1}{2}\|\mathbf{r} \times \mathbf{v}\| = \text{const}$).
3. **Định luật 3 (Chu kỳ)**: Bình phương chu kỳ quay tỉ lệ thuận với lập phương bán trục lớn của elip: $\frac{T^2}{a^3} = \frac{4\pi^2}{GM}$.
