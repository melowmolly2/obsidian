# Lý thuyết cần nhớ: Chương 12, sóng điện từ (Tuần 9)

## 1. Tính chất cơ bản của sóng điện từ

- Sóng ngang, $\vec{E} \perp \vec{B} \perp$ phương truyền, và $\vec{E}\times\vec{B}$ cùng hướng truyền sóng.
- $\vec{E}$ và $\vec{B}$ cùng pha.
- Trong chân không:  
    $$c=\frac{1}{\sqrt{\varepsilon_0\mu_0}}\approx 3{,}00\times10^{8}\ \text{m/s},\qquad E_{max}=cB_{max}$$

**Trong vật liệu** (Bài 1):  
$$v=\frac{1}{\sqrt{\varepsilon\mu}}=\frac{c}{\sqrt{K,K_m}},\qquad E_{max}=vB_{max}$$  
trong đó $K$ là hằng số điện môi, $K_m$ là độ từ thẩm tương đối.

## 2. Sóng hình sin (Bài 1, 2)

$$v=\lambda f,\qquad k=\frac{2\pi}{\lambda},\qquad \omega=2\pi f=vk$$

Sóng truyền theo $+x$, điện trường theo $\hat{j}$, từ trường theo $\hat{k}$:  
$$\vec{E}=E_{max}\cos(kx-\omega t),\hat{j},\qquad \vec{B}=B_{max}\cos(kx-\omega t),\hat{k}$$

## 3. Năng lượng và cường độ sóng (Bài 3 đến 7, 9)

**Mật độ năng lượng:**  
$$u=\frac{1}{2}\varepsilon_0E^2+\frac{B^2}{2\mu_0}=\varepsilon_0E^2$$

**Vectơ Poynting:**  
$$\vec{S}=\frac{1}{\mu_0}\vec{E}\times\vec{B}$$

**Cường độ sóng** (giá trị trung bình theo thời gian của $S$):  
$$I=S_{av}=\frac{E_{max}B_{max}}{2\mu_0}=\frac{E_{max}^2}{2\mu_0c}=\frac{1}{2}\varepsilon_0cE_{max}^2=\varepsilon_0 c,E_{rms}^2$$  
$$E_{rms}=\frac{E_{max}}{\sqrt2}$$

Nhớ thêm $I=u_{av},c$.

## 4. Công suất và năng lượng

- Nguồn điểm phát đều mọi hướng (Bài 3, 5, 9):  
    $$I=\frac{P}{4\pi r^2}\ \Rightarrow\ P=4\pi r^2 I$$
- Công suất qua diện tích vuông góc với phương truyền (Bài 4, 6, 9c): $P=IA$
- Năng lượng qua diện tích $A$ trong thời gian $t$ (Bài 4): $U=IAt$
- Bài 3: chỉ $5%$ công suất là ánh sáng nhìn thấy, nên $I_{vis}=\dfrac{0{,}05,P}{4\pi R^2}$ với $R$ là bán kính bóng đèn.

## 5. Sóng dừng, lò vi sóng (Bài 8)

- Thành kim loại là nút của điện trường.
- Khoảng cách giữa hai nút liên tiếp, hoặc giữa hai mặt phẳng bụng liên tiếp, là $\dfrac{\lambda}{2}$.
- Với lò dài $L$ có $n$ mặt phẳng bụng:  
    $$L=n\frac{\lambda}{2}\ \Rightarrow\ \lambda=\frac{2L}{n},\qquad f=\frac{c}{\lambda}$$
- Phần (c): giữ $n=5$, thay $L\to L+5{,}0\ \text{cm}$ rồi tính lại $\lambda$ và $f$.

## 6. Sóng điện từ trong dây dẫn (Bài 10)

Phương trình sóng trong dây dẫn tốt:  
$$\frac{\partial^2E_y}{\partial x^2}=\frac{\mu}{\rho}\frac{\partial E_y}{\partial t}$$

**Kiểm tra nghiệm** $E_y=E_{max}e^{-k_Cx}\cos(k_Cx-\omega t)$:  
$$\frac{\partial^2E_y}{\partial x^2}=2k_C^2E_{max}e^{-k_Cx}\sin(k_Cx-\omega t),\qquad \frac{\partial E_y}{\partial t}=\omega E_{max}e^{-k_Cx}\sin(k_Cx-\omega t)$$  
So sánh hai vế:  
$$2k_C^2=\frac{\mu\omega}{\rho}\ \Rightarrow\ k_C=\sqrt{\frac{\omega\mu}{2\rho}}$$

**Ý nghĩa vật lý:**

- Thừa số $e^{-k_Cx}$ làm biên độ giảm dần theo hàm mũ.
- Điện trường làm các điện tích tự do chuyển động, tạo dòng điện gây nhiệt $i^2R$. Năng lượng này lấy từ chính sóng, nên sóng bị suy giảm.
- Biên độ giảm còn $1/e$ tại độ sâu thấm (skin depth):  
    $$\delta=\frac{1}{k_C}=\sqrt{\frac{2\rho}{\omega\mu}}$$
- Với đồng, $f=1{,}0$ MHz, $\rho=1{,}72\times10^{-8}\ \Omega\cdot\text{m}$, $\mu=\mu_0$:  
    $$\delta=\sqrt{\frac{2(1{,}72\times10^{-8})}{(2\pi\times10^{6})(4\pi\times10^{-7})}}\approx 6{,}6\times10^{-5}\ \text{m}\approx 0{,}066\ \text{mm}$$  
    Khoảng này rất nhỏ nên sóng gần như không xuyên qua được kim loại mà bị phản xạ ở bề mặt.

## 7. Mẹo làm bài

- Đổi đơn vị trước: $\mu\text{T}=10^{-6}$ T, nm $=10^{-9}$ m, $1{,}4\ \text{kW/m}^2=1400\ \text{W/m}^2$.
- Từ $I$, tìm $E_{max}$ bằng $E_{max}=\sqrt{2\mu_0cI}$, rồi tìm $B_{max}=E_{max}/c$.
- Phân biệt biên độ ($E_{max}$) với giá trị hiệu dụng ($E_{rms}$) khi đề nói "hiệu dụng" (Bài 6b).
- Bài 7 (c): mật độ năng lượng trung bình $u_{av}=\dfrac{1}{2}\varepsilon_0E_{max}^2$, bao gồm cả phần điện và phần từ.

Nếu muốn, mình có thể giải chi tiết từng bài hoặc ra thêm bài tương tự để luyện.