# Lý thuyết cần nhớ: Nhiễu xạ (Chương 36, tuần 12)

## 1. Nhiễu xạ qua một khe (Bài 1, 2, 3, 9)

**Điều kiện cực tiểu** (vân tối), với $a$ là bề rộng khe:

$$a\sin\theta = m\lambda,\qquad m=\pm1,\pm2,\dots$$

**Vị trí trên màn** (góc nhỏ, màn cách khe $R$):

$$y_m \approx \frac{m\lambda R}{a}$$

**Bề rộng vân sáng trung tâm** (khoảng cách giữa hai cực tiểu $m=\pm1$):

$$w_0 = \frac{2\lambda R}{a}$$

**Cường độ sáng:**

$$I=I_0\left[\frac{\sin(\beta/2)}{\beta/2}\right]^2,\qquad \beta=\frac{2\pi a}{\lambda}\sin\theta$$

- Cực đại phụ nằm gần trung điểm hai cực tiểu liền kề. Lấy $\beta/2 \approx (m+\tfrac12)\pi$ thì  
    $$I \approx \frac{I_0}{\pi^2,(m+\frac12)^2}$$
- Số vân tối tối đa: $|m|<\dfrac{a}{\lambda}$, vì $|\sin\theta|\le 1$.
- Khi $\theta = 90^\circ$: $a=\lambda$ cho cực tiểu đầu tiên.

## 2. Giao thoa hai khe có xét nhiễu xạ (Bài 4, 5)

$$I=I_0\cos^2!\left(\frac{\phi}{2}\right)\left[\frac{\sin(\beta/2)}{\beta/2}\right]^2$$

$$\phi=\frac{2\pi d}{\lambda}\sin\theta,\qquad \beta=\frac{2\pi a}{\lambda}\sin\theta$$

- **Cực đại giao thoa:** $d\sin\theta = m\lambda$
- **Cực tiểu giao thoa:** $d\sin\theta=\left(m+\tfrac12\right)\lambda$
- **Cực tiểu nhiễu xạ:** $a\sin\theta = m'\lambda$
- **Cực đại bị mất:** xảy ra khi hai điều kiện trùng góc, tức là  
    $$\frac{d}{a}=\frac{m}{m'}$$  
    Với $d=3a$, các cực đại bậc $m=3,6,\dots$ bị mất.
- Với góc nhỏ: $\sin\theta\approx \tan\theta \approx y/R$.
- Trong Bài 4, $I_0$ là cường độ tại tâm. Tính $\phi$ và $\beta$ riêng, rồi thay vào công thức.

## 3. Cách tử nhiễu xạ (Bài 6)

$$d\sin\theta = m\lambda,\qquad d=\frac{1}{N}\ (N: \text{số vạch trên một đơn vị dài})$$

- Đổi đơn vị: $N$ vạch/cm thì $d = 1/N$ cm.
- Bậc cực đại cao nhất: $m_{max}<\dfrac{d}{\lambda}$, và chỉ lấy phần nguyên.
- Các vân phụ gồm các bậc $m=0,\pm1,\pm2,\dots$ đến $m_{max}$, trừ hai vân bậc một đã cho.

## 4. Nhiễu xạ tia X, định luật Bragg (Bài 7)

$$2d\sin\theta = m\lambda,\qquad m=1,2,3,\dots$$

Góc $\theta$ ở đây đo **so với mặt phẳng tinh thể**, không phải so với pháp tuyến.

## 5. Nhiễu xạ qua lỗ tròn, đĩa Airy (Bài 8)

**Cực tiểu đầu tiên:**

$$\sin\theta_1 = 1.22,\frac{\lambda}{D}$$

**Đường kính đĩa Airy** trên màn cách lỗ $R$:

$$d_{Airy}=2R\tan\theta_1\approx \frac{2.44,\lambda R}{D}$$

## 6. Tiêu chuẩn Rayleigh và nhiếp ảnh (Bài 36.44)

**Góc phân giải nhỏ nhất:**

$$\theta_{min}=1.22,\frac{\lambda}{D}$$

**Chi tiết nhỏ nhất phân giải được** trên vật cách ống kính $R$:

$$s=R,\theta_{min}=1.22,\frac{\lambda R}{D}$$

**Khẩu độ $f/N$:**

$$N=\frac{f}{D}\ \Rightarrow\ D=\frac{f}{N}$$

- $f/4.00$ cho $D$ lớn, nên $s$ nhỏ (phân giải tốt).
- $f/22.0$ cho $D$ nhỏ, nên $s$ lớn (phân giải kém hơn nhưng độ sâu trường ảnh lớn hơn).

## 7. Lưu ý khi làm bài

- Đổi đơn vị về mét: nm = $10^{-9}$ m, mm = $10^{-3}$ m.
- Chỉ dùng xấp xỉ $\sin\theta\approx\tan\theta\approx\theta$ khi góc nhỏ. Với góc lớn (như $45^\circ$, $90^\circ$), dùng $\sin\theta$ trực tiếp.
- Khi tính $\beta,\phi$ bằng $\sin(\cdot)$ hay $\cos(\cdot)$ của đại lượng này, **máy tính phải để chế độ radian**.
- Phân biệt rõ $a$ (bề rộng khe, quyết định nhiễu xạ) và $d$ (khoảng cách tâm hai khe, quyết định giao thoa).

Nếu bạn muốn, mình có thể giải chi tiết bài nào bạn đang vướng.