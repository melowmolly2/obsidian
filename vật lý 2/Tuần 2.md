# Lý thuyết tuần 2 cần nhớ

Bài tập này gồm **Chương 3 (Điện thế)** và **Chương 4 (Điện dung, tụ điện)**. Hằng số cần dùng: $k=\dfrac{1}{4\pi\varepsilon_0}=8{,}99\times10^{9}\ \text{N·m}^2/\text{C}^2$ và $\varepsilon_0=8{,}854\times10^{-12}\ \text{F/m}$.

## Chương 3: Điện thế

### 1. Thế năng điện và công của lực điện

- Công của lực điện bằng độ giảm thế năng:  
    $$W_{a\to b}=U_a-U_b=-\Delta U=\int_a^b q\vec E\cdot d\vec l$$
- Thế năng của hai điện tích điểm:  
    $$U=\frac{1}{4\pi\varepsilon_0}\frac{q,q_0}{r}$$
- Bảo toàn cơ năng (khi chỉ có lực điện): $K_a+U_a=K_b+U_b$. Dùng cho Bài 1, 2, 3, 8.
- Với điện tích $q$ (có dấu) di chuyển từ $a$ đến $b$:  
    $$W_{a\to b}=q,(V_a-V_b)=qV_{ab}$$

### 2. Điện thế

- Định nghĩa và hiệu điện thế:  
    $$V=\frac{U}{q_0},\qquad V_{ab}=V_a-V_b=\int_a^b\vec E\cdot d\vec l$$
- Điện tích điểm (chọn $V_\infty=0$): $V=\dfrac{kq}{r}$
- Nhiều điện tích: $V=k\sum_i \dfrac{q_i}{r_i}$. Đây là phép cộng **đại số**, **không phải vector** và phải giữ dấu của $q_i$. Dùng cho Bài 4, 5, 6.
- Phân bố liên tục: $V=k\displaystyle\int\frac{dq}{r}$

### 3. Liên hệ giữa $\vec E$ và $V$

$$E_x=-\frac{\partial V}{\partial x},\qquad E_r=-\frac{dV}{dr}$$

- $\vec E$ hướng về phía điện thế **giảm**.
- Trong điện trường đều: $V_{ab}=Ed$ (dọc theo chiều $\vec E$). Dùng cho Bài 3(b) với $E=\dfrac{|V_{AB}|}{d}$.

### 4. Mặt đẳng thế

- $\vec E$ luôn **vuông góc** với mặt đẳng thế, và không có công khi di chuyển trên mặt đẳng thế.
- Mặt đẳng thế **dày hơn (gần nhau hơn)** ở nơi $E$ lớn.
- Vật dẫn ở cân bằng tĩnh điện: toàn bộ vật là một khối đẳng thế, và $\vec E$ vuông góc với bề mặt.
- Dùng cho Bài 10 và Bài 11(b, c).

### 5. Các công thức điện thế hay gặp

|Hệ|Điện thế|
|---|---|
|Vỏ cầu mỏng bán kính $R$, điện tích $q$|$V=\dfrac{kq}{R}$ khi $r\le R$ (không đổi); $V=\dfrac{kq}{r}$ khi $r\ge R$|
|Hai vỏ cầu đồng tâm (Bài 7)|Cộng điện thế của từng vỏ (nguyên lý chồng chất)|
|Vòng dây tích điện, trên trục|$V=\dfrac{kQ}{\sqrt{x^2+a^2}}$ (Bài 8)|
|Dây thẳng dài / hình trụ dài, mật độ dài $\lambda$|$V_a-V_b=\dfrac{\lambda}{2\pi\varepsilon_0}\ln\dfrac{r_b}{r_a}$|
|Mặt phẳng vô hạn, mật độ mặt $\sigma$|$E=\dfrac{\sigma}{2\varepsilon_0}$, $V$ biến thiên tuyến tính theo khoảng cách|

Lưu ý khi làm bài:

- **Bài 7:** thế do vỏ nhỏ và vỏ lớn tại cùng một điểm được cộng lại. Trong vỏ lớn ($r<R_2$), thế do vỏ lớn là hằng số $\dfrac{kq_2}{R_2}$.
- **Bài 9:** bên trong vỏ trụ thì $E=0$, nên điện thế bằng hằng số và bằng thế trên bề mặt. Khi đó (b) cho $V=0$. Với (a), dùng công thức hiệu thế của dây dài với $r_a=6$ cm và $r_b=10$ cm.
- **Bài 10:** tấm tích điện **âm**, nên đi ra xa thì điện thế **tăng** (tiến về $0$ từ phía âm). Kết luận này không phụ thuộc điểm chọn làm mốc, vì hiệu thế mới có ý nghĩa vật lý. Khoảng cách giữa các mặt đẳng thế là $d=\dfrac{\Delta V}{E}=\dfrac{2\varepsilon_0\Delta V}{|\sigma|}$, và đó là các mặt phẳng song song với tấm.

## Chương 4: Điện dung và tụ điện

### 1. Định nghĩa

$$C=\frac{Q}{V_{ab}}$$  
$C$ chỉ phụ thuộc hình học (và chất điện môi), không phụ thuộc $Q$ hay $V$.

### 2. Các loại tụ (chân không/không khí)

|Loại|Điện dung|
|---|---|
|Tụ phẳng|$C=\dfrac{\varepsilon_0A}{d}$|
|Tụ trụ (chiều dài $L$)|$C=\dfrac{2\pi\varepsilon_0L}{\ln(r_b/r_a)}$|
|Tụ cầu|$C=4\pi\varepsilon_0\dfrac{r_ar_b}{r_b-r_a}$|

Một số công thức đi kèm:

- Tụ phẳng: $E=\dfrac{\sigma}{\varepsilon_0}=\dfrac{V}{d}$, với $\sigma=\dfrac{Q}{A}$ (Bài 1).
- Tụ trụ: dùng $\lambda=\dfrac{Q}{L}=C'V$ với $C'=\dfrac{C}{L}$ (Bài 3).
- Tụ cầu: điện trường ngay ngoài quả cầu trong là $E=\dfrac{kQ}{r_a^2}$ (Bài 4).

### 3. Mắc tụ điện

- **Nối tiếp:** $\dfrac{1}{C_{td}}=\sum\dfrac{1}{C_i}$. Điện tích **bằng nhau**, hiệu điện thế **chia ra**: $V=\sum V_i$.
- **Song song:** $C_{td}=\sum C_i$. Hiệu điện thế **bằng nhau**, điện tích **chia ra**: $Q=\sum Q_i$.
- Với mạch hỗn hợp (Bài 5, 6): rút gọn từng nhánh để tìm $C_{td}$, rồi đi ngược lại để tìm $Q$ và $V$ trên từng tụ.

### 4. Năng lượng

$$U=\frac{Q^2}{2C}=\frac12CV^2=\frac12QV$$  
Mật độ năng lượng điện trường:  
$$u=\frac12\varepsilon_0E^2$$  
Công thức này dùng chung cho **mọi** dạng tụ, kể cả tụ cầu (Bài 9). Với tụ cầu, $E$ **không đều** nên $u$ phụ thuộc $r$ (khác tụ phẳng).

### 5. Điện môi

Khi lấp đầy bằng điện môi có hằng số $K$:  
$$C=KC_0,\qquad \varepsilon=K\varepsilon_0,\qquad E=\frac{E_0}{K}\ \ (\text{cùng } Q)$$  
$$u=\frac12K\varepsilon_0E^2$$  
Phân biệt hai trường hợp (rất hay ra thi):

||**Ngắt nguồn** ($Q$ không đổi)|**Vẫn nối nguồn** ($V$ không đổi)|
|---|---|---|
|Điện dung|$C\to KC_0$|$C\to KC_0$|
|Điện tích|$Q$ giữ nguyên|$Q\to KQ_0$|
|Hiệu điện thế|$V\to V_0/K$|$V$ giữ nguyên|
|Năng lượng|$U\to U_0/K$|$U\to KU_0$|

Cũng dùng cho cách thay đổi khoảng cách $d$ (Bài 8): vì $C\propto\dfrac1d$, giảm $d$ đi một nửa thì $C$ tăng gấp đôi.

- Ngắt nguồn: $U=\dfrac{Q^2}{2C}$ giảm một nửa.
- Nối nguồn: $U=\dfrac12CV^2$ tăng gấp đôi.

### 6. Đánh thủng điện môi

- Điện trường tối đa chịu được là $E_m$, nên hiệu thế tối đa là $V_{max}=E_m,d$ (Bài 7c).
- Thiết kế tụ (Bài 10): từ $d=\dfrac{V_{max}}{E_m}$ và $C=\dfrac{K\varepsilon_0A}{d}$ suy ra $A_{min}=\dfrac{C,d}{K\varepsilon_0}$.

### 7. Các lỗi hay gặp

- Quên đổi đơn vị: $\mu\text{C}=10^{-6}$, $\text{nC}=10^{-9}$, $\text{pF}=10^{-12}$, $\text{cm}$ và $\text{mm}$ về mét.
- Quên dấu của $q$ khi tính điện thế và công. Hãy kiểm tra dấu kết quả bằng lập luận (công dương hay âm, điện thế cao hay thấp).
- Nhầm khi nào $Q$ cố định và khi nào $V$ cố định.
- Với mạch tụ, nhầm quy tắc nối tiếp và song song (ngược với điện trở).

Bạn muốn mình giải chi tiết bài nào, hoặc làm bộ đáp án cho cả hai chương không?