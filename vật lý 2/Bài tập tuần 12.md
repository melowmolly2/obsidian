# Bài tập tiêu biểu tuần 12

Mỗi dạng bài dưới đây chọn một bài đại diện, kèm lời giải gọn.

## Bài 1: Nhiễu xạ một khe, tìm bước sóng

Cho $a=0.750\text{ mm}$, $R=2.00\text{ m}$, $y_1=1.35\text{ mm}$ (cực tiểu thứ nhất).

$$\sin\theta_1\approx\frac{y_1}{R}=\frac{1.35\times10^{-3}}{2.00}=6.75\times10^{-4}$$

$$\lambda=a\sin\theta_1=0.750\times10^{-3}\cdot 6.75\times10^{-4}\approx 5.06\times10^{-7}\text{ m}\approx 506\text{ nm}$$

## Bài 4: Giao thoa hai khe có xét nhiễu xạ

Cho $\lambda=568\text{ nm}$, $R=0.750\text{ m}$, $d=0.640\text{ mm}$, $a=0.434\text{ mm}$, $y=0.900\text{ mm}$, $I_0=5.00\times10^{-4}\text{ W/m}^2$.

$$\sin\theta\approx\frac{y}{R}=1.20\times10^{-3}$$

Pha giao thoa:  
$$\frac{\phi}{2}=\frac{\pi d\sin\theta}{\lambda}=\pi(1.352)=4.248\text{ rad}\ \Rightarrow\ \cos^2\frac{\phi}{2}\approx 0.201$$

Pha nhiễu xạ:  
$$\frac{\beta}{2}=\frac{\pi a\sin\theta}{\lambda}=\pi(0.9169)=2.881\text{ rad}\ \Rightarrow\ \left[\frac{\sin(\beta/2)}{\beta/2}\right]^2\approx 8.03\times10^{-3}$$

$$I=I_0\cos^2\frac{\phi}{2}\left[\frac{\sin(\beta/2)}{\beta/2}\right]^2\approx 5.00\times10^{-4},(0.201)(8.03\times10^{-3})\approx 8.1\times10^{-7}\ \text{W/m}^2$$

(Máy tính để chế độ radian.)

## Bài 5: Hai khe với $d=3a$

**(a)** Bỏ qua nhiễu xạ, các cực đại tiếp theo thỏa $d\sin\theta=m\lambda$:

$$\theta_m=\arcsin\frac{m\lambda}{d},\quad m=1,2,3,4$$

**(b)** Với $d=3a$:  
$$\frac{\beta}{2}=\frac{\pi a\sin\theta}{\lambda}=\frac{\pi a m}{d}=\frac{m\pi}{3}$$

$$\frac{I_m}{I_0}=\left[\frac{\sin(m\pi/3)}{m\pi/3}\right]^2$$

|$m$|$I_m/I_0$|
|---|---|
|1|$0.684$|
|2|$0.171$|
|3|$0$|
|4|$0.0427$|

**(c)** Cực đại bậc $m=3$ bị mất, vì nó trùng cực tiểu nhiễu xạ bậc 1 ($a\sin\theta=\lambda$). Tương tự mất $m=6,9,\dots$

## Bài 6: Cách tử nhiễu xạ

Cho $\lambda=632.8\text{ nm}$, $\theta_1=17.8^\circ$.

**(a)**  
$$d=\frac{\lambda}{\sin\theta_1}=\frac{632.8\times10^{-9}}{0.3057}\approx2.07\times10^{-6}\text{ m}$$

$$N=\frac1d\approx4.83\times10^{5}\text{ vạch/m}\approx 4.83\times10^{3}\text{ vạch/cm}$$

**(b)**  
$$m_{max}<\frac{d}{\lambda}=\frac{1}{\sin\theta_1}=3.27\ \Rightarrow\ m\le3$$

Ngoài hai vân bậc một còn có **5 vân sáng**: $m=0$ ($\theta=0^\circ$), $m=\pm2$ ($\sin\theta=0.611\Rightarrow\theta\approx\pm37.7^\circ$), $m=\pm3$ ($\sin\theta=0.917\Rightarrow\theta\approx\pm66.5^\circ$).

## Bài 7: Nhiễu xạ Bragg

Cho $d=0.440\text{ nm}$, $\theta=39.4^\circ$, $m=1$.

$$\lambda=2d\sin\theta=2(0.440)(0.6347)\approx0.559\text{ nm}$$

## Bài 8: Đĩa Airy

Cho $\lambda=620\text{ nm}$, $D=7.4\text{ mm}$, $R=4.5\text{ m}$.

$$d_{Airy}=\frac{2.44,\lambda R}{D}=\frac{2.44(620\times10^{-9})(4.5)}{7.4\times10^{-3}}\approx9.2\times10^{-4}\text{ m}\approx0.92\text{ mm}$$

## Bài 36.44: Nhiếp ảnh và tiêu chuẩn Rayleigh

Cho $f=135\text{ mm}$, $R=11.5\text{ m}$, $\lambda=550\text{ nm}$, công thức $s=1.22,\dfrac{\lambda R}{D}$ với $D=\dfrac{f}{N}$.

**(a)** $f/4.00$: $D=33.75\text{ mm}$  
$$s=\frac{1.22(550\times10^{-9})(11.5)}{33.75\times10^{-3}}\approx2.3\times10^{-4}\text{ m}=0.23\text{ mm}$$

**(b)** $f/22.0$: $D=6.14\text{ mm}$  
$$s=\frac{1.22(550\times10^{-9})(11.5)}{6.14\times10^{-3}}\approx1.26\times10^{-3}\text{ m}\approx1.26\text{ mm}$$

Khẩu độ nhỏ làm chi tiết phân giải được thô hơn khoảng 5.5 lần, đổi lại độ sâu trường ảnh lớn hơn.

## Bài 9: Một khe, đếm vân tối

Cho $a=0.0250\text{ mm}$, $\lambda=632.8\text{ nm}$, $I_0=8.50\text{ W/m}^2$.

**(a)** Cực tiểu khi $a\sin\theta=m\lambda$ với $|\sin\theta|<1$:  
$$|m|<\frac{a}{\lambda}=39.5\ \Rightarrow\ |m|\le39$$  
Tổng cộng **78 vân tối** (39 mỗi bên).

**(b)** Vân tối xa tâm nhất là $m=39$:  
$$\sin\theta=\frac{39\lambda}{a}=0.987\ \Rightarrow\ \theta\approx80.8^\circ$$

**(c)** Vân sáng ngay trước nó nằm giữa $m=38$ ($\theta\approx74.1^\circ$) và $m=39$ ($\theta\approx80.8^\circ$), nên $\theta\approx77.5^\circ$.

$$\frac{\beta}{2}=\frac{\pi a\sin\theta}{\lambda}\approx121.2\text{ rad}$$

$$I=I_0\left[\frac{\sin(\beta/2)}{\beta/2}\right]^2\approx8.50\left(\frac{0.978}{121.2}\right)^2\approx5.5\times10^{-4}\text{ W/m}^2$$

Kết quả (c) rất nhạy với việc làm tròn góc, nên đáp số của bạn có thể lệch nhẹ tùy cách làm tròn.

Bạn muốn mình giải chi tiết thêm bài nào, hoặc làm nốt Bài 2 và Bài 3 không?