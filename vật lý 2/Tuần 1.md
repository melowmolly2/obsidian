# Lý thuyết cần nhớ tuần 1 (Chương 1 và 2: Điện tích, điện trường, định luật Gauss)

## Hằng số

$$k=\frac{1}{4\pi\varepsilon_0}\approx 8.99\times10^{9}\ \mathrm{N\cdot m^2/C^2},\qquad \varepsilon_0\approx 8.85\times10^{-12}\ \mathrm{C^2/(N\cdot m^2)}$$

$$e=1.6\times10^{-19}\ \mathrm{C},\quad m_e=9.11\times10^{-31}\ \mathrm{kg},\quad m_p=1.67\times10^{-27}\ \mathrm{kg},\quad N_A=6.02\times10^{23}\ \mathrm{mol^{-1}}$$

---

## CHƯƠNG 1: Điện tích và điện trường

### 1. Điện tích

- Điện tích bị lượng tử hóa: $q=\pm Ne$. Điện tích được bảo toàn.
- Số electron trong một vật có khối lượng $m$ (bài 1):

$$N=\frac{m}{M},N_A,Z$$

với $M$ là khối lượng mol và $Z$ là số hiệu nguyên tử.

### 2. Định luật Coulomb

$$F=k\frac{|q_1q_2|}{r^2}$$

- Cùng dấu thì đẩy, trái dấu thì hút. Lực nằm trên đường thẳng nối hai điện tích.
- Nhiều điện tích thì dùng **nguyên lý chồng chất**: $\vec F=\sum \vec F_i$. Phải cộng vectơ, nên chọn trục và phân tích thành phần (bài 4, 12, 13).

### 3. Điện trường

$$\vec E=\frac{\vec F}{q_0},\qquad \vec F=q\vec E$$

- Điện tích điểm: $E=k\dfrac{|q|}{r^2}$. Hướng ra xa nếu $q>0$, hướng vào nếu $q<0$.
- Điện tích dương chịu lực cùng chiều $\vec E$, điện tích âm chịu lực ngược chiều $\vec E$.
- Hệ điện tích: $\vec E=\sum \vec E_i$.
- Phân bố liên tục: $d\vec E=k\dfrac{dq}{r^2}\hat r$, với $dq=\lambda,dl$ (dây), $\sigma,dA$ (mặt), $\rho,dV$ (khối). Dùng đối xứng để triệt tiêu các thành phần vuông góc.

### 4. Các kết quả điện trường cần thuộc

|Hệ|Điện trường|
|---|---|
|Dây thẳng dài vô hạn (cách $r$)|$E=\dfrac{\lambda}{2\pi\varepsilon_0 r}$|
|Vòng dây bán kính $a$, điểm trên trục cách tâm $x$|$E_x=\dfrac{kQx}{(x^2+a^2)^{3/2}}$|
|Đĩa bán kính $R$, điểm trên trục cách tâm $x$|$E=\dfrac{\sigma}{2\varepsilon_0}\left(1-\dfrac{x}{\sqrt{x^2+R^2}}\right)$|
|Thanh dài $a$ (từ $0$ đến $a$), điểm trên trục tại $x>a$|$E=\dfrac{kQ}{x(x-a)}=\dfrac{kQ}{(a+r),r}$|
|Mặt phẳng vô hạn|$E=\dfrac{\sigma}{2\varepsilon_0}$|

Cách làm bài đĩa (bài 7): đĩa tích điện đều thì $\sigma=\dfrac{Q}{\pi R^2}$. Khi điện tích dồn ra vành ngoài thì dùng công thức vòng dây, khi dồn vào tâm thì coi như điện tích điểm.

Kiểm tra giới hạn (bài 9, 14c): khi $x\gg a$ thì mọi vật tích điện đều tiến về điện tích điểm, $E\to \dfrac{kQ}{x^2}$.

### 5. Chuyển động của hạt mang điện trong điện trường đều (bài 5, 6)

$$a=\frac{qE}{m}$$

- Chuyển động thẳng biến đổi đều: $v^2=v_0^2+2a,s,\quad v=v_0+at,\quad s=v_0t+\tfrac12at^2$.
- Hạt bay vào vuông góc với điện trường thì chuyển động giống ném ngang: theo phương ban đầu là đều, theo phương điện trường là biến đổi đều với gia tốc $a=\dfrac{qE}{m}$.
- Proton và electron có cùng $|q|$ nhưng $m_p\gg m_e$, nên gia tốc của electron lớn hơn nhiều và hai hạt lệch ngược chiều nhau.
- So sánh với trọng lực: $\dfrac{eE}{m g}$ thường rất lớn, nên trọng lực thường bỏ qua được.

### 6. Lưỡng cực điện (bài 10, 11)

- Mô-men lưỡng cực: $p=qd$. Vectơ $\vec p$ hướng từ điện tích âm sang điện tích dương.
- Mô-men xoắn và thế năng:

$$\vec\tau=\vec p\times\vec E,\quad \tau=pE\sin\phi,\qquad U=-\vec p\cdot\vec E$$

- Điện trường của lưỡng cực tại điểm xa trên trục ($x\gg d$):

$$E=\frac{1}{4\pi\varepsilon_0}\frac{2p}{x^3}$$

### 7. Điều kiện cân bằng (bài 13)

Điện tích thứ ba cân bằng khi lực tổng hợp lên nó bằng $0$. Để cả hệ cân bằng thì lực tổng hợp lên mỗi điện tích cũng phải bằng $0$. Điện tích thứ ba nằm giữa hai điện tích cùng dấu và phải khác dấu với chúng.

---

## CHƯƠNG 2: Định luật Gauss

### 1. Thông lượng điện

$$\Phi_E=\int \vec E\cdot d\vec A,\qquad \text{đều: }\ \Phi_E=EA\cos\phi$$

- $\phi$ là góc giữa $\vec E$ và pháp tuyến $\hat n$ của mặt.
- Với mặt kín, $\hat n$ hướng ra ngoài. Đường sức đi ra thì $\Phi>0$, đi vào thì $\Phi<0$.
- Đường sức song song với mặt thì $\Phi=0$.

### 2. Định luật Gauss

$$\Phi_E=\oint \vec E\cdot d\vec A=\frac{Q_{\text{trong}}}{\varepsilon_0}$$

- Chỉ điện tích **bên trong** mặt kín đóng góp vào thông lượng. Điện tích bên ngoài đóng góp $0$ vì đường sức vào rồi lại ra (bài 4 của chương 2).
- Nhưng $\vec E$ trên mặt là điện trường của **tất cả** các điện tích.

### 3. Chọn mặt Gauss theo đối xứng

|Đối xứng|Mặt Gauss|Kết quả|
|---|---|---|
|Cầu|Mặt cầu bán kính $r$|$E\cdot4\pi r^2=\dfrac{Q_{\text{trong}}}{\varepsilon_0}$|
|Trụ|Hình trụ đồng trục, chiều dài $l$|$E\cdot2\pi r l=\dfrac{Q_{\text{trong}}}{\varepsilon_0}$|
|Phẳng|Hình trụ nhỏ xuyên qua mặt phẳng|$E\cdot A_{\text{đáy}}\cdot(\text{số đáy có }E)=\dfrac{Q_{\text{trong}}}{\varepsilon_0}$|

### 4. Kết quả cần nhớ

- **Vỏ cầu mỏng / quả cầu dẫn tích điện**, bán kính $R$:

$$E=0\ (r<R),\qquad E=\frac{kQ}{r^2}\ (r\ge R)$$

- **Quả cầu cách điện tích điện đều theo thể tích**:

$$E=\frac{kQr}{R^3}\ (r<R),\qquad E=\frac{kQ}{r^2}\ (r>R)$$

- **Dây thẳng vô hạn**: $E=\dfrac{\lambda}{2\pi\varepsilon_0r}$.
- **Tấm phẳng vô hạn cách điện**: $E=\dfrac{\sigma}{2\varepsilon_0}$ (không phụ thuộc khoảng cách).
- **Ngay sát mặt vật dẫn**: $E=\dfrac{\sigma}{\varepsilon_0}$.
- **Hai tấm song song**: dùng chồng chất, mỗi tấm đóng góp $\dfrac{\sigma_i}{2\varepsilon_0}$ với dấu theo chiều. Hoặc dùng Gauss cho cả tấm dày.

### 5. Vật dẫn ở trạng thái cân bằng tĩnh điện

- $\vec E=0$ bên trong vật dẫn.
- Điện tích dư chỉ nằm trên bề mặt.
- Vỏ rỗng có điện tích $q$ ở trong khoang thì mặt trong của vỏ có điện tích $-q$, và mặt ngoài có $Q_{\text{vỏ}}+q$ (bài 7). Hãy tính lại mật độ điện tích mặt mới: $\sigma_{\text{mới}}=\dfrac{Q_{\text{mặt ngoài}}}{4\pi R_{\text{ngoài}}^2}$.
- Tấm dẫn khác tấm cách điện: tấm dẫn làm điện tích tập trung ra mặt, nên $E$ khác với tấm cách điện (bài 9c).

### 6. Phân bố điện tích không đều (bài 14, 15)

Điện tích chứa trong mặt Gauss được tính bằng tích phân. Với điện tích khối phụ thuộc $r$:

$$Q_{\text{trong}}=\int \rho(r),4\pi r^2,dr$$

Ví dụ $\rho=\dfrac{\alpha}{r}$ cho $Q_{\text{trong}}(r)=2\pi\alpha,(r^2-a^2)$ (cộng thêm $q$ nếu có điện tích ở tâm). Để $E$ hằng số trong vùng $a<r<b$ thì triệt tiêu số hạng chứa $\dfrac{1}{r^2}$ bằng cách chọn $q$ phù hợp.

### 7. Năng lượng và công (bài 8, 11 chương 2)

Điện trường tấm vô hạn là đều nên:

$$W=qE,d,\qquad W=\Delta K=\tfrac12mv^2-\tfrac12mv_0^2$$

---

## Mẹo làm bài

1. **Đổi đơn vị** trước: $\mathrm{nC}=10^{-9}$ C, $\mu\mathrm{C}=10^{-6}$ C, $\mathrm{mC}=10^{-3}$ C, $\mathrm{cm}=10^{-2}$ m, $\mathrm{nm}=10^{-9}$ m.
2. **Vẽ hình**, chọn trục, vẽ hướng của từng lực hoặc từng $\vec E$ trước khi tính số.
3. **Tách thành phần** khi cộng vectơ, và dùng đối xứng để loại bớt thành phần.
4. **Gauss**: nhận dạng đối xứng, chọn mặt Gauss đi qua điểm cần tính, rồi tính $Q_{\text{trong}}$.
5. Bài cân bằng (bài 12 chương 1): $T\cos\theta=mg$, $T\sin\theta=F_e=\dfrac{kq^2}{(2L\sin\theta)^2}$. Khi đổi $L$, giữ nguyên $q$ và giải lại phương trình cho $\theta$.

Nếu cần, mình có thể giải chi tiết một nhóm bài cụ thể, ví dụ vòng dây và thanh (chương 1 bài 9, 14, 15) hoặc các bài dùng định luật Gauss (chương 2).