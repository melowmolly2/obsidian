# Lý thuyết tuần 6: Chương 9 (cảm ứng điện từ) và Chương 10 (độ tự cảm)

## Chương 9: Cảm ứng điện từ và phương trình Maxwell

**1. Từ thông**

$$\Phi_B=\int \vec B\cdot d\vec A=\int B\cos\varphi,dA \qquad (1\ \text{Wb}=1\ \text{T·m}^2)$$

Với từ trường đều và mặt phẳng: $\Phi_B = BA\cos\varphi$.

**2. Định luật Faraday và Lenz**

$$\mathcal E=-N\frac{d\Phi_B}{dt},\qquad i=\frac{|\mathcal E|}{R}$$

- Dấu trừ (Lenz): dòng cảm ứng có chiều **chống lại sự biến thiên từ thông** sinh ra nó.
- Cách xác định chiều:
    1. Xem $\Phi_B$ đang tăng hay giảm.
    2. Từ trường cảm ứng ngược chiều $\vec B$ nếu $\Phi_B$ tăng, cùng chiều nếu $\Phi_B$ giảm.
    3. Dùng quy tắc nắm tay phải để suy ra chiều dòng.

**3. Suất điện động chuyển động**

Thanh (hoặc cạnh khung) dài $L$ chuyển động với vận tốc $v$ vuông góc với $\vec B$:

$$\mathcal E=vBL,\qquad i=\frac{vBL}{R}$$

Khung chữ nhật (Bài 3):

- Khi **đi vào** từ trường, chỉ có cạnh vuông góc với vận tốc cắt từ trường, nên $\mathcal E = vBL$.
- Khi **nằm hoàn toàn trong** từ trường, $\Phi_B$ không đổi nên $\mathcal E = 0$ và $i = 0$.
- Khi **đi ra**, $\mathcal E$ có độ lớn như lúc vào nhưng **chiều dòng điện ngược lại**.

**4. Điện trường cảm ứng (không bảo toàn)**

$$\oint \vec E\cdot d\vec l=-\frac{d\Phi_B}{dt}$$

Với cuộn dây solenoid bán kính $R$, $\dfrac{dB}{dt}=\mu_0 n\dfrac{di}{dt}$:

$$E=\frac{r}{2}\left|\frac{dB}{dt}\right|\quad(r<R),\qquad E=\frac{R^2}{2r}\left|\frac{dB}{dt}\right|\quad(r>R)$$

Dùng cho Bài 4 và Bài 5, trong đó $n$ là số vòng trên mỗi mét.

**5. Từ trường của dây dẫn thẳng dài** (Bài 1)

$$B=\frac{\mu_0 i}{2\pi r}$$

Chia khung thành dải hẹp rộng $dr$, dài $L$:

$$d\Phi_B=B,L,dr ;\Rightarrow; \Phi_B=\frac{\mu_0 iL}{2\pi}\ln\frac{b}{a},\qquad \mathcal E=\frac{\mu_0 L}{2\pi}\ln\frac{b}{a},\frac{di}{dt}$$

**6. Dòng điện dịch và định luật Ampère–Maxwell** (Bài 6)

$$\oint \vec B\cdot d\vec l=\mu_0\left(i_C+i_D\right)_{\text{enc}},\qquad i_D=\varepsilon_0\frac{d\Phi_E}{dt},\qquad j_D=\varepsilon_0\frac{dE}{dt}$$

Với tụ điện phẳng diện tích $A$, khoảng cách $d$:

$$E=\frac{q}{\varepsilon_0 A},\qquad V=Ed,\qquad q=i_Ct\ (\text{khi } i_C \text{ không đổi})$$

$$\frac{dE}{dt}=\frac{i_C}{\varepsilon_0A},\qquad i_D=j_DA=i_C$$

Dòng điện dịch giữa hai bản bằng dòng điện dẫn $i_C$ ở dây nối, nên dòng điện luôn liên tục.

---

## Chương 10: Độ tự cảm

**1. Hỗ cảm**

$$M=\frac{N_2\Phi_{B2}}{i_1}=\frac{N_1\Phi_{B1}}{i_2},\qquad \mathcal E_2=-M\frac{di_1}{dt}$$

Hai cuộn toroid chồng lên nhau, cùng $A$ và $r$ (Bài 1): từ trường cuộn 1 là $B=\dfrac{\mu_0N_1 i_1}{2\pi r}$, suy ra

$$M=\frac{\mu_0N_1N_2A}{2\pi r}$$

**2. Tự cảm**

$$L=\frac{N\Phi_B}{i},\qquad \mathcal E=-L\frac{di}{dt}$$

|Loại cuộn cảm|Từ trường|Độ tự cảm|
|---|---|---|
|Solenoid dài $\ell$|$B=\mu_0\dfrac{N}{\ell}i$|$L=\dfrac{\mu_0N^2A}{\ell}$|
|Toroid|$B=\dfrac{\mu_0Ni}{2\pi r}$|$L=\dfrac{\mu_0N^2A}{2\pi r}$|

Bài 2: từ $\mathcal E=L\dfrac{di}{dt}$ tính $L$, rồi dùng $L=\dfrac{N\Phi_B}{i}$ để tìm $N$.

**3. Năng lượng từ trường**

$$U=\frac12Li^2,\qquad u=\frac{B^2}{2\mu_0},\qquad U=u\cdot V_{\text{thể tích}}$$

Bài 3: tính $B$ trong solenoid, rồi $u$, rồi $U=u\cdot A\ell$, rồi kiểm tra bằng $L=\dfrac{\mu_0N^2A}{\ell}$ và $U=\dfrac12Li^2$.

**4. Mạch LC** (Bài 4)

Tụ điện nạp đến $V$ rồi nối với cuộn cảm, nên lúc $t=0$ có $q=Q=CV$ và $i=0$.

$$\omega=\frac{1}{\sqrt{LC}},\qquad T=2\pi\sqrt{LC}$$

$$q(t)=Q\cos\omega t,\qquad i(t)=-\omega Q\sin\omega t,\qquad I_{\max}=\omega Q=V\sqrt{\frac{C}{L}}$$

Bảo toàn năng lượng:

$$\frac{Q^2}{2C}=\frac12LI_{\max}^2$$

- Khi $i=I_{\max}$ thì $q=0$.
- Tụ xả hết **lần đầu** tại $t=\dfrac T4$, **lần thứ hai** tại $t=\dfrac{3T}{4}$.
- Đồ thị: $q$ có dạng cosin, $i$ có dạng sin (lệch pha $90^\circ$ so với $q$), cả hai đều dao động điều hòa với chu kỳ $T$.

---

## Mẹo làm bài

- Đổi đơn vị trước khi tính: cm → m, $\mu$s → s, mH → H, $\mu$F → F, cm² → m².
- Hằng số: $\mu_0=4\pi\times10^{-7}\ \text{T·m/A}$, $\varepsilon_0=8.85\times10^{-12}\ \text{F/m}$.
- Bài về chiều dòng điện: luôn xét $\Phi_B$ tăng hay giảm trước, rồi mới áp dụng Lenz.

Bạn muốn mình giải chi tiết bài nào, hoặc làm cả bộ bài tập luôn không?