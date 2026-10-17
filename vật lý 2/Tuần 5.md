# Lý thuyết tuần 5 cần nhớ

Bài tập tuần này gồm Chương 7 (Từ trường và lực từ) và Chương 8 (Từ trường của phần tử dòng điện).

## CHƯƠNG 7: TỪ TRƯỜNG VÀ LỰC TỪ

### 7.2. Lực từ lên điện tích chuyển động

$$\vec F = q,\vec v\times\vec B,\qquad F=|q|,vB\sin\phi$$

- $\phi$ là góc giữa $\vec v$ và $\vec B$. Lực luôn vuông góc với cả $\vec v$ và $\vec B$, nên **không sinh công**.
- Với $q>0$, dùng quy tắc bàn tay phải. Với $q<0$, lực ngược chiều.
- Đơn vị: $1\ \text{T}=1\ \dfrac{\text{N}}{\text{A·m}}$, $1\ \text{G}=10^{-4}\ \text{T}$.
- Tích có hướng theo thành phần:  
    $$\vec v\times\vec B=\begin{vmatrix}\hat i&\hat j&\hat k\ v_x&v_y&v_z\ B_x&B_y&B_z\end{vmatrix}$$
- **Bài 2b:** thành phần của $\vec B$ song song với $\vec v$ không tạo lực ($\sin 0=0$), nên không thể xác định từ phép đo lực. Ở bài này đó là $B_y$.
- Luôn có $\vec F\perp\vec B$, tức $\vec B\cdot\vec F=0$ (dùng để kiểm tra Bài 2c, 2d).

### 7.3. Từ thông

$$\Phi_B=\int \vec B\cdot d\vec A,\qquad \Phi_B=BA\cos\phi\ \ (\text{B đều, mặt phẳng})$$

- Đơn vị: $1\ \text{Wb}=1\ \text{T·m}^2$.
- Định luật Gauss cho từ trường: $\displaystyle\oint \vec B\cdot d\vec A=0$, nên tổng thông lượng qua mặt kín bằng 0 (Bài 4d).
- Bài 4: $\vec B\parallel +z$, nên chỉ mặt có pháp tuyến dọc theo $z$ hoặc có thành phần theo $z$ mới có thông lượng khác 0. Với mặt nghiêng, dùng $\Phi=B,A_{\perp}$, trong đó $A_\perp$ là diện tích hình chiếu lên mặt phẳng $xy$. Pháp tuyến hướng ra ngoài mặt kín.

### 7.4. Chuyển động của hạt trong từ trường đều ($\vec v\perp\vec B$)

$$R=\frac{mv}{|q|B},\qquad \omega=\frac{|q|B}{m},\qquad T=\frac{2\pi m}{|q|B},\qquad a=\frac{v^2}{R}=\frac{|q|vB}{m}$$

- $T$ **không phụ thuộc vào $v$**.
- Nếu $\vec v$ có thành phần song song với $\vec B$ thì quỹ đạo là đường xoắn ốc, với bước $p=v_\parallel T$.
- Gia tốc hướng vào tâm quỹ đạo, có độ lớn không đổi.
- **Xác định hướng $\vec B$:** từ chiều lực tại A (hướng vào tâm) dùng $\vec F=q\vec v\times\vec B$. Chú ý electron mang điện âm.
- **Bài 5, 6:** ở đây $R=\dfrac{AB}{2}$. Với proton thì $m$ đổi nên độ lớn $B$ đổi, và hướng $B$ ngược với electron.
- **Bài 7:** hạt có $q=+3e$, $m=12m_p$. Tính $v=\dfrac{qBR}{m}$. Trọng lực bỏ qua được vì rất nhỏ so với lực từ, và tốc độ không đổi vì lực từ không sinh công.

### 7.5. Ứng dụng

- **Bộ chọn vận tốc** (chùm không lệch khi $\vec F_E+\vec F_B=0$):  
    $$qE=qvB\ \Rightarrow\ v=\frac{E}{B}$$  
    Hai lực ngược chiều nhau. Do đó nếu đổi hướng $\vec B$ thì phải đổi hướng $\vec E$ tương ứng (Bài 8b).
- **Khối phổ kế** (Bài 9): sau bộ chọn vận tốc, $v=\dfrac{E}{B_1}$ và $R=\dfrac{mv}{qB_2}$, suy ra  
    $$m=\frac{qB_2R}{v}$$  
    Ion bị ion hóa một lần nên $q=e$.
- **Lực từ lên dây dẫn:**  
    $$\vec F=I,\vec L\times\vec B,\qquad F=ILB\sin\phi,\qquad d\vec F=I,d\vec l\times\vec B$$
- **Bài 10 (thanh trên giá đỡ):** thanh vẫn tiếp xúc khi $F_B\le mg$, tức $ILB\le mg$, và $I=\dfrac{V}{R}$. Từ đó tìm $V_{\max}$. Khi $R$ giảm thì $I$ tăng, lực từ vượt trọng lực, và gia tốc ban đầu là $a=\dfrac{F_B-mg}{m}$.
- **Khung dây có dòng điện** (momen từ $\vec\mu=NI\vec A$):  
    $$\vec F_{\text{tổng}}=0\ \ (\text{B đều}),\qquad \vec\tau=\vec\mu\times\vec B,\qquad \tau=NIAB\sin\phi$$  
    $\phi$ là góc giữa pháp tuyến khung và $\vec B$. Thế năng: $U=-\vec\mu\cdot\vec B$.
- **Bài 11:** (a) pháp tuyến song song $\vec B$, nên $\phi=0$ và $\tau=0$. (b) quay $30^\circ$, nên $\phi=30^\circ$ và $\tau=IAB\sin 30^\circ$. Lực tổng vẫn bằng 0.

## CHƯƠNG 8: TỪ TRƯỜNG CỦA DÒNG ĐIỆN

Hằng số: $\mu_0=4\pi\times10^{-7}\ \text{T·m/A}$, và $\dfrac{\mu_0}{4\pi}=10^{-7}\ \text{T·m/A}$.

### 8.1. Từ trường của điện tích chuyển động ($v\ll c$)

$$\vec B=\frac{\mu_0}{4\pi}\frac{q,\vec v\times\hat r}{r^2}$$

- $\hat r$ là vectơ đơn vị từ điện tích đến điểm khảo sát.
- Với $q<0$ thì $\vec B$ ngược chiều $\vec v\times\hat r$.
- Độ lớn: $B=\dfrac{\mu_0}{4\pi}\dfrac{|q|v\sin\phi}{r^2}$. Tại điểm nằm trên đường thẳng chứa $\vec v$ (như điểm D trong Bài 1) thì $B=0$.
- Lực giữa hai điện tích chuyển động:  
    $$\frac{F_B}{F_E}=\mu_0\varepsilon_0v_1v_2=\frac{v_1v_2}{c^2}$$
- Khi tìm lực từ $q'$ tác dụng lên $q$: tính $\vec B$ do $q'$ gây ra tại vị trí $q$, rồi dùng $\vec F=q\vec v\times\vec B$.
- Cùng chiều chuyển động thì lực từ là hút, ngược chiều thì là đẩy (Bài 2c). Lực điện thì đẩy với hai điện tích cùng dấu.

### 8.2. Định luật Biot–Savart

$$d\vec B=\frac{\mu_0}{4\pi}\frac{I,d\vec l\times\hat r}{r^2},\qquad dB=\frac{\mu_0}{4\pi}\frac{I,dl,\sin\theta}{r^2}$$

- Bài 4: đoạn dây ngắn, nên $B\approx\dfrac{\mu_0}{4\pi}\dfrac{I,\Delta l\sin\theta}{r^2}$, với $\theta=90^\circ$ nếu $\hat r\perp d\vec l$. Cộng vectơ hai đóng góp (chúng cùng hướng hay không thì xét bằng quy tắc bàn tay phải).

### 8.3. Dây thẳng dài

$$B=\frac{\mu_0 I}{2\pi r}$$

- Hướng: nắm bàn tay phải, ngón cái theo chiều dòng điện, các ngón cuộn chỉ chiều $\vec B$ (đường sức là các đường tròn).
- Dây hữu hạn:  
    $$B=\frac{\mu_0 I}{4\pi r}\left(\sin\theta_2-\sin\theta_1\right)$$
- **Bài 5, 6, 10:** áp dụng nguyên lý chồng chất $\vec B=\vec B_1+\vec B_2+\dots$ và xét hướng từng thành phần. Tại $P_1$ (giữa hai dây cùng chiều) hai từ trường ngược chiều nhau và triệt tiêu một phần.

### 8.4. Lực giữa hai dây song song

$$\frac{F}{L}=\frac{\mu_0I_1I_2}{2\pi r}$$

- **Cùng chiều thì hút, ngược chiều thì đẩy.**
- Nếu cả hai dòng tăng gấp đôi thì $B$ tại một điểm tăng gấp đôi (tỉ lệ với $I$), còn lực tăng gấp **bốn** lần (tỉ lệ với $I_1I_2$) (Bài 7).

### 8.5. Vòng dây tròn

- Trên trục cách tâm $x$:  
    $$B_x=\frac{\mu_0 I R^2}{2,(x^2+R^2)^{3/2}}$$
- Tại tâm vòng: $B=\dfrac{\mu_0 I}{2R}$. Với $N$ vòng thì nhân $N$.
- Cung tròn góc $\theta$ (rad) tại tâm: $B=\dfrac{\mu_0 I,\theta}{4\pi R}$. Nửa vòng: $B=\dfrac{\mu_0 I}{4R}$.
- **Gợi ý Bài 8:** đoạn dây thẳng đi qua điểm P (hoặc nằm trên đường thẳng qua P) có $d\vec l\parallel\hat r$, nên $d\vec l\times\hat r=0$ và không tạo từ trường tại P. Chỉ cần tính phần bán nguyệt.

### 8.6. Định luật Ampère

$$\oint \vec B\cdot d\vec l=\mu_0,I_{\text{kín}}$$

- $I_{\text{kín}}$ là tổng đại số các dòng điện xuyên qua diện tích giới hạn bởi đường kín.
- **Quy ước dấu (Bài 9):** đi theo chiều ngược kim đồng hồ, nắm bàn tay phải thì ngón cái hướng **ra khỏi mặt giấy** (dấu chấm $\odot$). Do đó dòng **ra** là dương, dòng **vào** ($\otimes$) là âm.
- Dòng điện nằm ngoài đường kín không đóng góp vào $I_{\text{kín}}$.
- Chỉ cần liệt kê dòng nào nằm trong mỗi đường $a,b,c,d$, cộng với dấu thích hợp rồi nhân $\mu_0$.

## Hằng số hay dùng

|Đại lượng|Giá trị|
|---|---|
|$e$|$1{,}602\times10^{-19}\ \text{C}$|
|$m_e$|$9{,}109\times10^{-31}\ \text{kg}$|
|$m_p$|$1{,}673\times10^{-27}\ \text{kg}$|
|$\mu_0$|$4\pi\times10^{-7}\ \text{T·m/A}$|
|$c$|$3{,}00\times10^{8}\ \text{m/s}$|

## Mẹo làm bài

1. Luôn vẽ hình, xác định hướng $\vec v,\ \vec B,\ \vec F$ bằng quy tắc bàn tay phải **trước khi tính độ lớn**.
2. Chú ý **dấu điện tích** (electron thì đảo chiều lực).
3. Đổi đơn vị cẩn thận ($\mu\text{C}$, $\text{km/s}$, $\text{cm}$, $\text{nm}$, $\text{mm}$).
4. Có nhiều nguồn thì cộng **vectơ**, không cộng độ lớn.

Nếu bạn muốn, mình có thể giải chi tiết từng bài, hoặc làm mẫu một bài để bạn thử các bài còn lại.