# Lý thuyết cần nhớ – Tuần 8 (Chương 11: Mạch điện xoay chiều)

## 1. Nguồn xoay chiều

$$v = V\cos\omega t,\qquad i = I\cos(\omega t - \phi),\qquad \omega = 2\pi f$$

- Giá trị hiệu dụng (rms): $V_{rms} = \dfrac{V}{\sqrt{2}}$, $\quad I_{rms} = \dfrac{I}{\sqrt{2}}$
- Giá trị trung bình của nửa chu kỳ (dòng chỉnh lưu): $V_{av} = \dfrac{2}{\pi}V$. Trung bình cả chu kỳ của sóng sin bằng 0.
- Bài 1 dùng trực tiếp hai công thức này.

## 2. Ba phần tử riêng lẻ

|Phần tử|Quan hệ biên độ|Pha của $v$ so với $i$|
|---|---|---|
|Điện trở $R$|$V_R = IR$|Cùng pha|
|Cuộn cảm $L$|$V_L = IX_L,\ \ X_L=\omega L$|$v_L$ **sớm** pha $90^\circ$|
|Tụ điện $C$|$V_C = IX_C,\ \ X_C=\dfrac{1}{\omega C}$|$v_C$ **trễ** pha $90^\circ$|

Với mạch chỉ có cuộn cảm (Bài 2): $\phi = +90^\circ$ (điện áp nguồn sớm pha hơn dòng điện), và $I = \dfrac{V}{\omega L}$, suy ra $f = \dfrac{V}{2\pi L I}$.

## 3. Mạch LRC nối tiếp

$$Z=\sqrt{R^2+(X_L-X_C)^2},\qquad V = IZ,\qquad \tan\phi=\frac{X_L-X_C}{R}$$

- $\phi>0$ (tức $X_L>X_C$): mạch cảm kháng, điện áp nguồn **sớm** pha hơn dòng điện.
- $\phi<0$ (tức $X_C>X_L$): mạch dung kháng, điện áp nguồn **trễ** pha hơn dòng điện (Bài 8a: $\phi=-54^\circ$).
- Từ $\tan\phi$ suy ra $X_L = X_C + R\tan\phi$.

**Điện áp tức thời và biên độ** (Bài 4):

$$v = v_R+v_L+v_C \quad(\text{luôn đúng tại mọi thời điểm})$$

$$V=\sqrt{V_R^2+(V_L-V_C)^2}\ \ne\ V_R+V_L+V_C$$

Các biên độ không cộng số học được vì $v_R, v_L, v_C$ lệch pha nhau (đạt cực đại ở các thời điểm khác nhau). Đây là câu trả lời cho phần "giải thích tại sao" ở Bài 4b.

Cách làm Bài 3 và Bài 4a: viết $i(t)$ từ biên độ $I=V/Z$ và góc $\phi$. Sau đó $v_R = IR\cos(\omega t-\phi)$, $v_L=-IX_L\sin(\omega t-\phi)$, $v_C=\dfrac{I}{\omega C}\sin(\omega t-\phi)$. Nhớ đổi sang radian khi tính.

## 4. Công suất

$$P_{av}=V_{rms}I_{rms}\cos\phi = I_{rms}^2R=\frac{V_{rms}^2R}{Z^2},\qquad \cos\phi=\frac{R}{Z}\ \ (\text{hệ số công suất})$$

- Chỉ điện trở tiêu thụ công suất. Cuộn cảm và tụ điện chỉ tích và trả năng lượng, nên công suất nguồn cung cấp bằng công suất tiêu tán trên $R$ (Bài 5a = Bài 5b).
- Bài 8 (31.51): biết $P$ và $R$, tính $I_{rms}=\sqrt{P/R}$. Từ $\tan\phi$ tính $X_L$, rồi $V_{rms}=I_{rms}Z$.

## 5. Cộng hưởng

$$\omega_0=\frac{1}{\sqrt{LC}},\qquad X_L=X_C,\quad Z=R,\quad \phi=0$$

- Dòng điện cực đại: $I=\dfrac{V}{R}$, công suất cực đại.
- Bài 6: tại cộng hưởng, $I=\dfrac{V_C}{X_C}$, suy ra $V=IR$ (vì $Z=R$).
- Bài 9 (đáp số theo $R, C, L, V$):

$$I_R=\frac{V}{R},\qquad V_C=V_L=\frac{V}{R}\sqrt{\frac{L}{C}}$$

$$U_{C,\max}=\tfrac12 CV_C^2=\frac{LV^2}{2R^2},\qquad U_{L,\max}=\tfrac12 LI^2=\frac{LV^2}{2R^2}$$

Tại cộng hưởng, năng lượng cực đại trong tụ và trong cuộn cảm bằng nhau.

## 6. Năng lượng trong L và C (Bài 8 – 31.58)

$$U_L=\tfrac12 Li^2\ \Rightarrow\ U_{L,\max}=\tfrac12 LI^2,\qquad U_C=\frac{q^2}{2C}\ \Rightarrow\ U_{C,\max}=\frac{q_{\max}^2}{2C}=\frac{I^2}{2\omega^2C}$$

Vì $q$ và $i$ lệch pha $90^\circ$ nên khi $i$ cực đại thì $q=0$. Do đó khi năng lượng trong cuộn cảm cực đại, năng lượng trong tụ điện bằng $0$ (câu b).

## 7. Máy biến áp lý tưởng (Bài 7)

$$\frac{V_2}{V_1}=\frac{N_2}{N_1},\qquad \frac{I_1}{I_2}=\frac{N_2}{N_1},\qquad P_1=P_2=V_2I_2$$

- (a) Tỉ số vòng dây: $\dfrac{N_2}{N_1}=\dfrac{13,000}{120}$.
- (b) $P=V_2I_2$ với $I_2 = 8{,}50$ mA.
- (c) Định mức cầu chì: $I_1=I_2\dfrac{N_2}{N_1}$.

## 8. Những lỗi hay gặp

1. Đề cho biên độ hay giá trị hiệu dụng? Công suất dùng rms, còn $v(t)$ dùng biên độ.
2. Đổi đơn vị: mH → H, nF/µF → F, kHz → Hz, ms → s.
3. Phân biệt tần số $f$ và tần số góc $\omega=2\pi f$.
4. Máy tính ở chế độ radian khi tính $\sin(\omega t)$ (Bài 3, Bài 4).
5. Xác định đúng dấu của $\phi$ ("nguồn sớm/trễ pha so với dòng điện").

Mình có thể giải chi tiết từng bài nếu bạn muốn.