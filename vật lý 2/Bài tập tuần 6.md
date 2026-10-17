# Bài tập tiêu biểu tuần 6

Mình chọn mỗi dạng một bài, giải chi tiết. Các bài còn lại làm tương tự.

---

## Chương 9

### Bài 1 (29.7): Khung chữ nhật cạnh dây thẳng dài

**(a)** Từ trường của dây thẳng dài tại khoảng cách $r$:

$$B=\frac{\mu_0 i}{2\pi r}$$

Từ trường hướng vào trong mặt phẳng hình vẽ ở bên phải dây (quy tắc nắm tay phải).

**(b)** Dải hẹp rộng $dr$, dài $L$ có diện tích $dA=L,dr$:

$$d\Phi_B=B,L,dr=\frac{\mu_0 i L}{2\pi}\frac{dr}{r}$$

**(c)** Tích phân từ $r=a$ đến $r=b$:

$$\Phi_B=\frac{\mu_0 iL}{2\pi}\ln\frac{b}{a}$$

**(d)**

$$|\mathcal E|=\frac{d\Phi_B}{dt}=\frac{\mu_0 L}{2\pi}\ln\frac{b}{a},\frac{di}{dt}$$

**(e)** Thay $a=0.120\ \text{m}$, $b=0.240\ \text{m}$, $L=0.360\ \text{m}$, $\dfrac{di}{dt}=9.60\ \text{A/s}$:

$$|\mathcal E|=(2\times10^{-7})(0.360)(\ln 2)(9.60)\approx 4.79\times10^{-7}\ \text{V}$$

---

### Bài 2 (29.23): Vòng dây tròn, $B(t)=(0.380\ \text{T/s}^3),t^3$

Tìm thời điểm $B=1.33\ \text{T}$:

$$t^3=\frac{1.33}{0.380}=3.50\ \Rightarrow\ t^2=3.50^{2/3}\approx 2.305\ \text{s}^2$$

Tốc độ biến thiên của từ trường:

$$\frac{dB}{dt}=3(0.380),t^2=1.14,t^2\approx 2.63\ \text{T/s}$$

Suất điện động và dòng điện, với $A=\pi r^2=\pi(0.0250)^2=1.96\times10^{-3}\ \text{m}^2$:

$$|\mathcal E|=A\frac{dB}{dt}\approx 5.16\times10^{-3}\ \text{V},\qquad i=\frac{|\mathcal E|}{R}=\frac{5.16\times10^{-3}}{0.390}\approx 1.32\times10^{-2}\ \text{A}$$

**Chiều:** $\vec B$ hướng vào trong mặt phẳng và đang tăng. Từ trường cảm ứng phải hướng ra ngoài, nên dòng điện **ngược chiều kim đồng hồ**.

**Đáp số:** $i\approx 13.2\ \text{mA}$, ngược chiều kim đồng hồ.

---

### Bài 3 (29.35): Khung chữ nhật đi vào, qua và ra khỏi từ trường

Cạnh vuông góc với vận tốc có độ dài $L=0.750\ \text{m}$, $v=3.0\ \text{m/s}$, $B=1.25\ \text{T}$, $R=12.5\ \Omega$.

$$\mathcal E=vBL=(3.0)(1.25)(0.750)=2.81\ \text{V},\qquad i=\frac{\mathcal E}{R}=\frac{2.81}{12.5}=0.225\ \text{A}$$

|Giai đoạn|$\Phi_B$|Dòng điện cảm ứng|
|---|---|---|
|(a) Đi vào|Tăng (từ trường hướng ra ngoài)|$0.225\ \text{A}$, **cùng chiều kim đồng hồ**|
|(b) Nằm hoàn toàn trong|Không đổi|$0$|
|(c) Đi ra|Giảm|$0.225\ \text{A}$, **ngược chiều kim đồng hồ**|

**(d) Đồ thị** $i(t)$: là các đoạn nằm ngang. Lúc vào $i=+0.225\ \text{A}$ (lấy chiều cùng chiều kim đồng hồ làm dương) trong thời gian $\Delta t=\dfrac{0.500}{3.0}\approx 0.167\ \text{s}$. Sau đó $i=0$ trong suốt thời gian khung nằm trong từ trường. Khi ra, $i=-0.225\ \text{A}$ trong $0.167\ \text{s}$.

---

### Bài 4 (29.38) và Bài 5 (29.39): Điện trường cảm ứng quanh cuộn cảm

Từ trường trong cuộn cảm:

$$B=\mu_0 n i\ \Rightarrow\ \frac{dB}{dt}=\mu_0 n\frac{di}{dt}$$

**Bài 4:** $n=900$ vòng/m, $R=2.50\ \text{cm}$, $\dfrac{di}{dt}=36.0\ \text{A/s}$:

$$\frac{dB}{dt}=(4\pi\times10^{-7})(900)(36.0)\approx 4.07\times10^{-2}\ \text{T/s}$$

Bên trong cuộn ($r<R$):

$$E=\frac r2\left|\frac{dB}{dt}\right|$$

- (a) $r=0.500\ \text{cm}$: $E=\dfrac{0.00500}{2}(4.07\times10^{-2})\approx 1.02\times10^{-4}\ \text{V/m}$
- (b) $r=1.00\ \text{cm}$: $E\approx 2.04\times10^{-4}\ \text{V/m}$

**Bài 5:** $n=400$ vòng/m, $R=1.10\ \text{cm}$, điểm xét $r=3.50\ \text{cm}>R$ nên dùng công thức bên ngoài:

$$E=\frac{R^2}{2r},\mu_0 n\frac{di}{dt}\ \Rightarrow\ \frac{di}{dt}=\frac{2rE}{\mu_0 n R^2}$$

$$\frac{di}{dt}=\frac{2(0.0350)(8.00\times10^{-6})}{(4\pi\times10^{-7})(400)(0.0110)^2}\approx 9.21\ \text{A/s}$$

---

### Bài 6 (29.44): Tụ điện phẳng và dòng điện dịch

Dữ liệu: $A=5.00\times10^{-4}\ \text{m}^2$, $d=2.00\times10^{-3}\ \text{m}$, $i_C=1.80\times10^{-3}\ \text{A}$, $t=0.500\times10^{-6}\ \text{s}$.

**(a)**

$$q=i_Ct=9.00\times10^{-10}\ \text{C}$$

$$E=\frac{q}{\varepsilon_0A}=\frac{9.00\times10^{-10}}{(8.85\times10^{-12})(5.00\times10^{-4})}\approx 2.03\times10^{5}\ \text{V/m}$$

$$V=Ed\approx 407\ \text{V}$$

**(b)**

$$\frac{dE}{dt}=\frac{i_C}{\varepsilon_0A}\approx 4.07\times10^{11}\ \text{V/(m·s)}$$

Giá trị này **không đổi theo thời gian** vì $i_C$ không đổi.

**(c)**

$$j_D=\varepsilon_0\frac{dE}{dt}=\frac{i_C}{A}=3.60\ \text{A/m}^2,\qquad i_D=j_DA=1.80\ \text{mA}$$

Vậy $i_D=i_C$: dòng điện dịch giữa hai bản bằng dòng điện dẫn ở dây nối, nên dòng điện là liên tục.

---

## Chương 10

### Bài 1 (30.6): Hỗ cảm của hai cuộn toroid chồng lên nhau

**(a)** Từ trường của cuộn 1 là $B=\dfrac{\mu_0N_1i_1}{2\pi r}$, nên từ thông qua mỗi vòng của cuộn 2 là $\Phi_{B2}=BA$:

$$M=\frac{N_2\Phi_{B2}}{i_1}=\frac{\mu_0N_1N_2A}{2\pi r}$$

**(b)**

$$M=\frac{(4\pi\times10^{-7})(500)(300)(0.800\times10^{-4})}{2\pi(0.100)}=2.40\times10^{-5}\ \text{H}=24.0\ \mu\text{H}$$

---

### Bài 2 (30.10): Tìm số vòng của cuộn toroid

Từ $|\mathcal E|=L\left|\dfrac{di}{dt}\right|$:

$$L=\frac{12.6\times10^{-3}}{0.0260}\approx 0.485\ \text{H}$$

Từ $L=\dfrac{N\Phi_B}{i}$:

$$N=\frac{Li}{\Phi_B}=\frac{(0.485)(1.40)}{0.00285}\approx 238\ \text{vòng}$$

---

### Bài 3 (30.19): Solenoid, năng lượng từ trường

Dữ liệu: $\ell=0.250\ \text{m}$, $A=0.500\times10^{-4}\ \text{m}^2$, $N=400$, $i=80.0\ \text{A}$.

**(a)**

$$B=\frac{\mu_0Ni}{\ell}=\frac{(4\pi\times10^{-7})(400)(80.0)}{0.250}\approx 0.161\ \text{T}$$

**(b)**

$$u=\frac{B^2}{2\mu_0}\approx 1.03\times10^{4}\ \text{J/m}^3$$

**(c)**

$$U=uA\ell=(1.03\times10^4)(0.500\times10^{-4})(0.250)\approx 0.129\ \text{J}$$

**(d)**

$$L=\frac{\mu_0N^2A}{\ell}=\frac{(4\pi\times10^{-7})(400)^2(0.500\times10^{-4})}{0.250}\approx 4.02\times10^{-5}\ \text{H}$$

Kiểm tra: $\dfrac12Li^2=\dfrac12(4.02\times10^{-5})(80.0)^2\approx 0.129\ \text{J}$, khớp với (c).

---

### Bài 4 (30.34): Mạch LC

Dữ liệu: $C=18.0\ \mu\text{F}$, $V=22.5\ \text{V}$, $L=12.0\ \text{mH}$.

**(a)** Điện tích ban đầu của tụ:

$$Q=CV=4.05\times10^{-4}\ \text{C}$$

Bảo toàn năng lượng $\dfrac{Q^2}{2C}=\dfrac12LI_{\max}^2$:

$$I_{\max}=V\sqrt{\frac CL}=22.5\sqrt{\frac{18.0\times10^{-6}}{12.0\times10^{-3}}}\approx 0.871\ \text{A}$$

Khi dòng điện cực đại, toàn bộ năng lượng nằm trong cuộn cảm nên **điện tích trên tụ bằng $0$**.

**(b)**

$$\omega=\frac{1}{\sqrt{LC}}\approx 2.15\times10^{3}\ \text{rad/s},\qquad T=2\pi\sqrt{LC}\approx 2.92\ \text{ms}$$

- Xả hoàn toàn lần đầu: $t=\dfrac T4\approx 0.730\ \text{ms}$
- Xả hoàn toàn lần thứ hai: $t=\dfrac{3T}{4}\approx 2.19\ \text{ms}$

**(c) Đồ thị:**

$$q(t)=Q\cos\omega t,\qquad i(t)=-\omega Q\sin\omega t$$

Cả hai là hàm điều hòa chu kỳ $T$, lệch pha nhau $90^\circ$. $q$ bắt đầu từ cực đại $Q$, giảm về $0$ tại $T/4$. Lúc đó $|i|$ đạt cực đại $0.871\ \text{A}$.

---

Bạn muốn mình làm thêm bài nào chưa có ở đây, hay tạo bộ đề tương tự để luyện tập không?