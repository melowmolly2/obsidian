# Lý thuyết cần nhớ – Tuần 3 (Chương 25 và 26)

## Chương 25: Dòng điện, điện trở, suất điện động

**Cường độ dòng điện và mật độ dòng**

$$I=\frac{dQ}{dt},\qquad J=\frac{I}{A}=n|q|v_d\quad\Rightarrow\quad I=n|q|v_dA$$

- $n$ là mật độ electron tự do (m⁻³), $|q|=e=1.60\times10^{-19}\ \text{C}$, $v_d$ là tốc độ trôi.
- Tiết diện dây tròn: $A=\dfrac{\pi d^2}{4}=\pi r^2$. Dây vuông cạnh $a$: $A=a^2$.
- Thời gian electron đi hết dây dài $L$: $t=\dfrac{L}{v_d}$.

**Điện trở suất và định luật Ôm**

$$\vec E=\rho\vec J\ \Rightarrow\ E=\rho J,\qquad R=\frac{\rho L}{A},\qquad V=IR,\qquad E=\frac{V}{L}$$

- Với dây dẫn đồng chất: $E=\dfrac{V}{L}=\dfrac{IR}{L}=\dfrac{\rho I}{A}$ (dùng cho Bài 2, 4).
- Bài 4: tìm $\rho$ từ $R=\dfrac{V}{I}$ và $\rho=\dfrac{RA}{L}$.
- Cần nhớ (hoặc tra bảng) $\rho_{\text{Cu}}\approx1.72\times10^{-8}\ \Omega\cdot\text{m}$ và $\rho_{\text{Ag}}\approx1.47\times10^{-8}\ \Omega\cdot\text{m}$ ở nhiệt độ phòng.
- Phụ thuộc nhiệt độ: $\rho(T)=\rho_0\left[1+\alpha(T-T_0)\right]$.

**Suất điện động và điện trở trong**

- Pin đang phát điện: $V_{ab}=\mathcal E-Ir$ (hiệu điện thế đầu cực nhỏ hơn $\mathcal E$).
- Pin đang được sạc: $V_{ab}=\mathcal E+Ir$.
- Mạch kín gồm pin và điện trở ngoài $R$:

$$I=\frac{\mathcal E}{R+r}$$

- Bài 5: $V_{ab}=\mathcal E-Ir\Rightarrow r=\dfrac{\mathcal E-V_{ab}}{I}$, sau đó $R=\dfrac{V_{ab}}{I}$.
- Bài 6: công tắc mở thì $V=\mathcal E$. Công tắc đóng thì $V=\mathcal E-Ir=IR$.

**Công suất**

$$P=VI=I^2R=\frac{V^2}{R}$$

- Nguồn phát công suất $P=\mathcal EI$, công suất hao phí trong pin là $I^2r$.
- Bài 7 (bóng đèn): $R=\dfrac{V^2}{P}$ với $V=120\ \text{V}$ và $I=\dfrac{P}{V}$. Bóng công suất lớn hơn thì điện trở nhỏ hơn.

**Tụ điện ở trạng thái dừng (Bài 8, chương 25)**

- Khi tụ đã sạc đầy, dòng qua nhánh tụ bằng 0, tụ coi như hở mạch.
- Hiệu điện thế trên tụ là $V_C=\dfrac{Q}{C}$, và bằng hiệu điện thế trên điện trở song song với tụ ($R_1$).
- Dòng chạy qua $R_2$ và $R_1$ nối tiếp: $I=\dfrac{V_{R_1}}{R_1}$, rồi $\mathcal E=I(R_1+R_2)$.

---

## Chương 26: Mạch điện một chiều

**Điện trở mắc nối tiếp và song song**

||Nối tiếp|Song song|
|---|---|---|
|Dòng điện|Giống nhau|Chia ra, $I=\sum I_i$|
|Hiệu điện thế|Chia ra, $V=\sum V_i$|Giống nhau|
|Điện trở tương đương|$R_{eq}=R_1+R_2+\dots$|$\dfrac{1}{R_{eq}}=\dfrac{1}{R_1}+\dfrac{1}{R_2}+\dots$|

- Hai điện trở song song: $R_{eq}=\dfrac{R_1R_2}{R_1+R_2}$.
- Bài 1 (26.2): $\dfrac{1}{R_{ab}}=\dfrac{1}{X}+\dfrac{1}{15}+\dfrac{1}{5}+\dfrac{1}{10}$ với $R_{ab}=2.00\ \Omega$.
- Bài 3, 4 (26.11): $R_1\parallel R_2$, rồi nối tiếp với $R_3$. Dòng qua $R_3$ là tổng $I_1+I_2$, và $\mathcal E=I_3R_3+V_{12}$ với $V_{12}=I_2R_2=I_1R_1$.

**Quy tắc Kirchhoff (cho mạch phức tạp như Bài 7, 26.25)**

- Quy tắc nút: $\sum I_{\text{vào}}=\sum I_{\text{ra}}$.
- Quy tắc vòng: $\sum \Delta V=0$ khi đi hết một vòng kín.
- Quy ước dấu khi đi theo chiều đã chọn:
    - Qua điện trở cùng chiều dòng: $-IR$. Ngược chiều dòng: $+IR$.
    - Qua nguồn từ cực − sang cực +: $+\mathcal E$. Từ cực + sang cực −: $-\mathcal E$.
- Nếu giải ra dòng điện âm thì chiều thực tế ngược với chiều đã giả sử.
- Bài 6 (26.24): chọn dòng cho mỗi nhánh, viết một phương trình nút và hai phương trình vòng, rồi giải hệ.
- Bài 7(d): khi mạch đứt tại $x$ thì nhánh đó có $I=0$, nên mạch được vẽ lại và giải như mạch đơn giản.

**Công tắc đóng hay mở (Bài 5, 26.18)**

- Công tắc đóng nghĩa là $R_1$ song song $R_2$, nên $R_{ab}=\dfrac{R_1R_2}{R_1+R_2}$.
- Công tắc mở thì chỉ còn $R_2$ giữa $a$ và $b$.
- Tính tổng trở $R_{tot}=R_{ab}+R_3$, dòng tổng $I=\dfrac{\mathcal E}{R_{tot}}$, rồi $V_{ab}=I,R_{ab}$.
- Khi đóng công tắc, điện trở tương đương toàn mạch giảm nên dòng tổng tăng, $V_{ab}$ giảm.

**Dụng cụ đo lý tưởng (Bài 2 và Bài 6 chương 25)**

- Ampe kế lý tưởng: $R_A=0$, mắc nối tiếp, coi như dây dẫn.
- Vôn kế lý tưởng: $R_V=\infty$, mắc song song, không có dòng chạy qua.

**Mạch RC**

Hằng số thời gian: $\tau=RC$.

Nạp điện:

$$q(t)=C\mathcal E\left(1-e^{-t/RC}\right),\qquad v_C(t)=\mathcal E\left(1-e^{-t/RC}\right)$$

Xả điện:

$$q(t)=Q_0e^{-t/RC},\qquad v_C(t)=V_0e^{-t/RC},\qquad i(t)=\frac{V_0}{R}e^{-t/RC}$$

- Bài 8 (26.39): tụ xả qua vôn kế, nên $R=R_V=3.40\ \text{M}\Omega$. Từ $V=V_0e^{-t/\tau}$ suy ra

$$\tau=\frac{t}{\ln!\left(V_0/V\right)},\qquad C=\frac{\tau}{R}$$

---

## Mẹo làm bài

1. Đổi đơn vị trước khi tính: mm → m, μF → F, MΩ → Ω.
2. Bài về dây dẫn: tính $A$ trước, rồi mới tính $J$, $v_d$, $E$ hay $R$.
3. Bài mạch điện: rút gọn các nhánh nối tiếp/song song trước, và chỉ dùng Kirchhoff khi không rút gọn được.
4. Kiểm tra lại kết quả bằng cách xem tổng công suất nguồn phát có bằng tổng công suất tiêu thụ không.

Nếu bạn muốn, mình có thể giải chi tiết bài nào trong đề này.