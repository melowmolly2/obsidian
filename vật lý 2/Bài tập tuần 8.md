# Bài tập tiêu biểu – Tuần 8

Mình chọn 6 bài đại diện cho các dạng chính: giá trị hiệu dụng, LRC tức thời, công suất, cộng hưởng, độ lệch pha và năng lượng. Các bài còn lại (2, 3, 7, 9) làm tương tự bằng công thức ở phần lý thuyết.

---

## Bài 1 (31.3): Giá trị rms và trung bình

$$V_{rms}=\frac{V}{\sqrt2}=\frac{45{,}0}{\sqrt2}\approx 31{,}8\ \text{V}$$

$$V_{av}=\frac{2}{\pi}V=\frac{2\cdot 45{,}0}{\pi}\approx 28{,}6\ \text{V}$$

---

## Bài 4 (31.16): LRC nối tiếp, giá trị tức thời

Cho $R=200,\Omega$, $L=0{,}900$ H, $C=6{,}00,\mu$F, $V=30{,}0$ V, $\omega=250$ rad/s.

**Bước 1: Trở kháng và góc pha**

$$X_L=\omega L=225\ \Omega,\qquad X_C=\frac{1}{\omega C}=\frac{1}{250\cdot 6\cdot10^{-6}}\approx 666{,}7\ \Omega$$

$$Z=\sqrt{R^2+(X_L-X_C)^2}=\sqrt{200^2+(-441{,}7)^2}\approx 484{,}9\ \Omega$$

$$I=\frac{V}{Z}\approx 0{,}0619\ \text{A},\qquad \phi=\arctan\frac{X_L-X_C}{R}=\arctan(-2{,}208)\approx -65{,}6^\circ=-1{,}146\ \text{rad}$$

**(a) Tại $t=20{,}0$ ms** ($\omega t = 5{,}00$ rad, $\omega t-\phi=6{,}146$ rad $\Rightarrow \cos=0{,}9905,\ \sin=-0{,}1372$):

$$v=V\cos\omega t=30\cos(5{,}00)\approx 8{,}51\ \text{V}$$

$$v_R=IR\cos(\omega t-\phi)\approx 12{,}3\ \text{V}$$

$$v_L=-IX_L\sin(\omega t-\phi)\approx +1{,}91\ \text{V}$$

$$v_C=IX_C\sin(\omega t-\phi)\approx -5{,}66\ \text{V}$$

$$v_R+v_L+v_C\approx 8{,}5\ \text{V}=v\ \checkmark$$

**(b) Biên độ**

$$V_R=IR\approx 12{,}4\ \text{V},\quad V_L=IX_L\approx 13{,}9\ \text{V},\quad V_C=IX_C\approx 41{,}2\ \text{V}$$

$$V_R+V_L+V_C\approx 67{,}5\ \text{V}\ \neq\ V=30{,}0\ \text{V}$$

**Giải thích:** $v=v_R+v_L+v_C$ đúng tại mọi thời điểm, nhưng các điện áp này lệch pha nhau nên không đạt cực đại cùng lúc. Vì vậy biên độ phải cộng như vectơ (phasor):

$$V=\sqrt{V_R^2+(V_L-V_C)^2}$$

---

## Bài 5 (31.20): Công suất

Cho $L=20{,}0$ mH, $C=140$ nF, $R=350,\Omega$, $V_{rms}=120$ V, $f=1{,}25$ kHz.

$$\omega=2\pi f\approx 7854\ \text{rad/s},\quad X_L\approx 157\ \Omega,\quad X_C=\frac{1}{\omega C}\approx 909\ \Omega$$

$$Z=\sqrt{350^2+(157-909)^2}\approx 830\ \Omega,\qquad I_{rms}=\frac{V_{rms}}{Z}\approx 0{,}145\ \text{A}$$

**(a)** Công suất máy phát cung cấp:

$$P=V_{rms}I_{rms}\cos\phi,\quad \cos\phi=\frac{R}{Z}\approx 0{,}422\ \Rightarrow\ P\approx 7{,}32\ \text{W}$$

**(b)** Công suất tiêu tán trên điện trở:

$$P_R=I_{rms}^2R\approx 7{,}32\ \text{W}$$

Hai kết quả bằng nhau vì chỉ có điện trở tiêu thụ năng lượng.

---

## Bài 6 (31.26): Cộng hưởng

Tại cộng hưởng $X_L=X_C$ nên $Z=R$.

$$I=\frac{V_C}{X_C}=\frac{600}{200}=3{,}00\ \text{A}$$

$$V=IR=3{,}00\cdot 300=900\ \text{V}$$

---

## Bài 8 (31.51): Biết độ lệch pha và công suất

Cho $\phi=-54{,}0^\circ$ (nguồn trễ pha), $X_C=350,\Omega$, $R=180,\Omega$, $P=140$ W.

**(a)** Từ $\tan\phi=\dfrac{X_L-X_C}{R}$:

$$X_L=X_C+R\tan\phi=350+180\tan(-54^\circ)\approx 102\ \Omega$$

**(b)** $P=I_{rms}^2R$:

$$I_{rms}=\sqrt{\frac{P}{R}}=\sqrt{\frac{140}{180}}\approx 0{,}882\ \text{A}$$

**(c)**

$$Z=\frac{R}{\cos\phi}=\frac{180}{\cos 54^\circ}\approx 306\ \Omega,\qquad V_{rms}=I_{rms}Z\approx 270\ \text{V}$$

---

## Bài 8 (31.58): Năng lượng trong L và C

Cho $R=60{,}0,\Omega$, $L=0{,}800$ H, $C=3{,}00\cdot10^{-4}$ F, $V=90{,}0$ V, $\omega=120$ rad/s.

$$X_L=96{,}0\ \Omega,\quad X_C=\frac{1}{\omega C}\approx 27{,}8\ \Omega$$

$$Z=\sqrt{60^2+(96{,}0-27{,}8)^2}\approx 90{,}9\ \Omega,\qquad I=\frac{V}{Z}\approx 0{,}991\ \text{A}$$

**(a)**

$$U_{L,\max}=\tfrac12LI^2=\tfrac12(0{,}800)(0{,}991)^2\approx 0{,}393\ \text{J}$$

**(b)** Khi $i$ cực đại thì $q=0$ (lệch pha $90^\circ$), nên năng lượng trong tụ điện bằng **0**.

**(c)**

$$U_{C,\max}=\frac{I^2}{2\omega^2C}=\frac{(0{,}991)^2}{2(120)^2(3{,}00\cdot10^{-4})}\approx 0{,}114\ \text{J}$$

---

## Tóm tắt quy trình giải bài LRC

1. Đổi đơn vị, tính $\omega=2\pi f$.
2. Tính $X_L,\ X_C \Rightarrow Z \Rightarrow I=V/Z$.
3. Tính $\phi$ từ $\tan\phi=\dfrac{X_L-X_C}{R}$ và xác định dấu.
4. Chọn đúng loại giá trị: biên độ cho $v(t)$, rms cho công suất.

Bạn muốn mình giải chi tiết các bài còn lại (2, 3, 7, 9) không?