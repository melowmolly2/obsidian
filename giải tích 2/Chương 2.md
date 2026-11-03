# Tóm tắt lý thuyết Chương 2: Hàm véc-tơ

File gồm 101 slide, chia thành 4 phần. Các công thức dưới đây dùng $\lvert\cdot\rvert$ thay cho `|` để tránh lỗi bảng như lần trước.

## 2.1. Hàm véc-tơ và đường cong trong không gian

- **Định nghĩa:** hàm véc-tơ $\mathbf{r}:D\subseteq\mathbb{R}\to\mathbb{R}^n$ gán mỗi $t$ với một véc-tơ. Trong $\mathbb{R}^3$:  
    $$\mathbf{r}(t)=\langle f(t),g(t),h(t)\rangle=f(t)\mathbf{i}+g(t)\mathbf{j}+h(t)\mathbf{k}$$  
    trong đó $f,g,h$ là các **hàm thành phần**. Tập xác định là tập các $t$ làm cho mọi hàm thành phần đều xác định.
- **Giới hạn và liên tục** tính theo từng thành phần:  
    $$\lim_{t\to t_0}\mathbf{r}(t)=\Big\langle\lim_{t\to t_0}f(t),\ \lim_{t\to t_0}g(t),\ \lim_{t\to t_0}h(t)\Big\rangle$$  
    $\mathbf{r}$ liên tục tại $a$ khi $\lim_{t\to a}\mathbf{r}(t)=\mathbf{r}(a)$, tức là mọi hàm thành phần đều liên tục tại $a$.
- **Đường cong không gian** $C$ là tập các điểm $(x,y,z)$ với $x=f(t),\ y=g(t),\ z=h(t)$ (phương trình tham số, $t$ là tham số).
- **Ví dụ quan trọng:**
    - Đường xoắn ốc (helix) $\mathbf{r}(t)=\langle\cos t,\sin t,t\rangle$ nằm trên mặt trụ $x^2+y^2=1$.
    - Đường cong là giao của hai mặt: chiếu lên một mặt phẳng để chọn tham số, rồi suy ra biến còn lại. Với giao của $x^2+y^2=1$ và $y+z=2$:  
        $$x=\cos t,\ y=\sin t,\ z=2-\sin t,\quad 0\le t\le2\pi$$

## 2.2. Đạo hàm và tích phân của hàm véc-tơ

- **Đạo hàm:**  
    $$\mathbf{r}'(t)=\lim_{h\to0}\frac{\mathbf{r}(t+h)-\mathbf{r}(t)}{h}=\langle f'(t),g'(t),h'(t)\rangle$$  
    (đạo hàm từng thành phần khi $f,g,h$ khả vi). Đạo hàm cấp hai: $\mathbf{r}''=(\mathbf{r}')'$.
- **Ý nghĩa hình học:** nếu $\mathbf{r}'(t)\neq\mathbf{0}$ thì $\mathbf{r}'(t)$ là véc-tơ tiếp tuyến của đường cong tại điểm $\mathbf{r}(t)$, chỉ về hướng $t$ tăng. Tiếp tuyến là đường thẳng qua điểm đó với véc-tơ chỉ phương $\mathbf{r}'(t)$.
- **Véc-tơ tiếp tuyến đơn vị:**  
    $$\mathbf{T}(t)=\frac{\mathbf{r}'(t)}{\lvert\mathbf{r}'(t)\rvert}$$
- **Quy tắc đạo hàm** ($\mathbf{u},\mathbf{v}$ khả vi, $c$ là hằng số, $f$ là hàm số thực):  
    $$\frac{d}{dt}[\mathbf{u}+\mathbf{v}]=\mathbf{u}'+\mathbf{v}',\qquad \frac{d}{dt}[c\mathbf{u}]=c\mathbf{u}',\qquad \frac{d}{dt}[f\mathbf{u}]=f'\mathbf{u}+f\mathbf{u}'$$  
    $$\frac{d}{dt}[\mathbf{u}\cdot\mathbf{v}]=\mathbf{u}'\cdot\mathbf{v}+\mathbf{u}\cdot\mathbf{v}',\qquad \frac{d}{dt}[\mathbf{u}\times\mathbf{v}]=\mathbf{u}'\times\mathbf{v}+\mathbf{u}\times\mathbf{v}'$$  
    $$\frac{d}{dt}[\mathbf{u}(f(t))]=f'(t),\mathbf{u}'(f(t))\quad\text{(quy tắc dây chuyền)}$$  
    Lưu ý: khi đạo hàm tích có hướng, **giữ nguyên thứ tự** các thừa số vì tích có hướng không giao hoán.
- **Định lý quan trọng:** nếu $\lvert\mathbf{r}(t)\rvert=c$ (hằng số) thì $\mathbf{r}'(t)\perp\mathbf{r}(t)$ với mọi $t$. Cách chứng minh: đạo hàm hai vế của $\mathbf{r}\cdot\mathbf{r}=c^2$ để được $2\mathbf{r}'\cdot\mathbf{r}=0$. Ý nghĩa: đường cong nằm trên mặt cầu tâm $O$ thì tiếp tuyến luôn vuông góc với véc-tơ vị trí.
- **Tích phân:** lấy tích phân từng thành phần.  
    $$\int_a^b\mathbf{r}(t),dt=\Big(\int_a^bf,dt\Big)\mathbf{i}+\Big(\int_a^bg,dt\Big)\mathbf{j}+\Big(\int_a^bh,dt\Big)\mathbf{k}=\mathbf{R}(t)\Big\rvert_a^b$$  
    trong đó $\mathbf{R}'=\mathbf{r}$. Nguyên hàm bất định có hằng số là một **véc-tơ hằng** $\mathbf{C}$.

## 2.3. Độ dài đường cong và độ cong

### Độ dài cung

- Độ dài đường cong $C$: $\mathbf{r}(t)$, $a\le t\le b$ ($\mathbf{r}'$ liên tục, $C$ được đi qua đúng một lần):  
    $$L=\int_a^b\lvert\mathbf{r}'(t)\rvert,dt=\int_a^b\sqrt{\Big(\frac{dx}{dt}\Big)^2+\Big(\frac{dy}{dt}\Big)^2+\Big(\frac{dz}{dt}\Big)^2},dt$$
- Độ dài không phụ thuộc cách tham số hóa (đổi biến trong tích phân). Ví dụ một cung của helix: $\lvert\mathbf{r}'\rvert=\sqrt2$, nên một vòng ($0\le t\le2\pi$) dài $2\sqrt2,\pi$.
- **Hàm độ dài cung:**  
    $$s(t)=\int_a^t\lvert\mathbf{r}'(u)\rvert,du,\qquad \frac{ds}{dt}=\lvert\mathbf{r}'(t)\rvert$$
- **Tham số hóa theo độ dài cung:** giải $t=t(s)$ rồi viết $\mathbf{r}(t(s))$. Với helix trên: $s=\sqrt2,t$ nên $\mathbf{r}=\big\langle\cos\tfrac{s}{\sqrt2},\sin\tfrac{s}{\sqrt2},\tfrac{s}{\sqrt2}\big\rangle$.

### Độ cong

- Tham số hóa $\mathbf{r}$ gọi là **trơn** nếu $\mathbf{r}'$ liên tục và $\mathbf{r}'(t)\neq\mathbf{0}$.
- **Độ cong** (tốc độ đổi hướng của đường cong):  
    $$\kappa=\Big\lvert\frac{d\mathbf{T}}{ds}\Big\rvert=\frac{\lvert\mathbf{T}'(t)\rvert}{\lvert\mathbf{r}'(t)\rvert}$$
- **Công thức tiện dùng nhất:**  
    $$\kappa=\frac{\lvert\mathbf{r}'(t)\times\mathbf{r}''(t)\rvert}{\lvert\mathbf{r}'(t)\rvert^3}$$
- **Đồ thị $y=f(x)$:**  
    $$\kappa(x)=\frac{\lvert f''(x)\rvert}{\big(1+(f'(x))^2\big)^{3/2}}$$
- Đường tròn bán kính $a$ có $\kappa=1/a$. Parabol $y=x^2$ có $\kappa(x)=\dfrac{2}{(1+4x^2)^{3/2}}$, nên $\kappa(0)=2$ và $\kappa\to0$ khi $x\to\pm\infty$.

### Khung TNB

Tại điểm có $\kappa\neq0$:  
$$\mathbf{T}=\frac{\mathbf{r}'}{\lvert\mathbf{r}'\rvert},\qquad \mathbf{N}=\frac{\mathbf{T}'}{\lvert\mathbf{T}'\rvert},\qquad \mathbf{B}=\mathbf{T}\times\mathbf{N}$$  
Đây là ba véc-tơ đơn vị đôi một vuông góc (do $\lvert\mathbf{T}\rvert=1$ nên $\mathbf{T}'\perp\mathbf{T}$). $\mathbf{N}$ là pháp tuyến chính (hướng đường cong đang quay), $\mathbf{B}$ là song pháp tuyến.

- **Mặt phẳng pháp tuyến:** chứa $\mathbf{N},\mathbf{B}$, vuông góc với $\mathbf{T}$. Pháp tuyến của nó là $\mathbf{r}'(t)$.
- **Mặt phẳng mật tiếp:** chứa $\mathbf{T},\mathbf{N}$, là mặt phẳng "ôm sát" đường cong nhất. Pháp tuyến của nó là $\mathbf{B}$.
- **Đường tròn mật tiếp:** nằm trong mặt phẳng mật tiếp, qua $P$, bán kính $1/\kappa$, tâm cách $P$ một đoạn $1/\kappa$ dọc theo $\mathbf{N}$. Ví dụ: với $y=x^2$ tại gốc, $\kappa=2$ nên đường tròn mật tiếp là $x^2+\big(y-\tfrac12\big)^2=\tfrac14$.
- Với helix: $\mathbf{N}=\langle-\cos t,-\sin t,0\rangle$, $\mathbf{B}=\tfrac{1}{\sqrt2}\langle\sin t,-\cos t,1\rangle$.

### Độ xoắn

- $\dfrac{d\mathbf{B}}{ds}=-\tau,\mathbf{N}$ (slide để bài tập chứng minh tồn tại $\tau$). **Độ xoắn:**  
    $$\tau=-\frac{d\mathbf{B}}{ds}\cdot\mathbf{N}=-\frac{\mathbf{B}'(t)\cdot\mathbf{N}(t)}{\lvert\mathbf{r}'(t)\rvert}$$
- **Công thức thực hành:**  
    $$\tau=\frac{[\mathbf{r}'\times\mathbf{r}'']\cdot\mathbf{r}'''}{\lvert\mathbf{r}'\times\mathbf{r}''\rvert^2}$$
- Ý nghĩa: $\tau$ đo mức đường cong "nhấc lên" khỏi mặt phẳng mật tiếp. Đường tròn đơn vị có $\kappa=1,\ \tau=0$. Helix $\langle\cos t,\sin t,t\rangle$ có $\kappa=\tfrac12,\ \tau=\tfrac12$.

## 2.4. Chuyển động trong không gian

- **Vận tốc, tốc độ, gia tốc:**  
    $$\mathbf{v}(t)=\mathbf{r}'(t),\qquad \lvert\mathbf{v}(t)\rvert=\frac{ds}{dt},\qquad \mathbf{a}(t)=\mathbf{v}'(t)=\mathbf{r}''(t)$$  
    Vận tốc là véc-tơ tiếp tuyến. Độ dài, độ cong, độ xoắn không phụ thuộc cách tham số hóa, còn vận tốc, tốc độ, gia tốc thì có. Ví dụ hình ảnh: con đường là đường cong, còn tham số hóa là cách bạn đi trên đường đó.
- **Từ gia tốc suy ngược ra vận tốc và vị trí:**  
    $$\mathbf{v}(t)=\mathbf{v}(t_0)+\int_{t_0}^t\mathbf{a}(u),du,\qquad \mathbf{r}(t)=\mathbf{r}(t_0)+\int_{t_0}^t\mathbf{v}(u),du$$  
    (dùng điều kiện đầu để xác định các véc-tơ hằng).
- **Định luật II Newton:** $\mathbf{F}(t)=m,\mathbf{a}(t)$.
- **Chuyển động tròn đều** $\mathbf{r}(t)=a\cos\omega t,\mathbf{i}+a\sin\omega t,\mathbf{j}$:  
    $$\mathbf{F}=-m\omega^2,\mathbf{r}(t)$$  
    Lực ngược chiều với $\mathbf{r}$ nên hướng vào tâm (lực hướng tâm).
- **Vật ném xiên** (bỏ qua sức cản không khí, góc nâng $\alpha$, tốc độ đầu $v_0$, xuất phát từ gốc):  
    $$\mathbf{a}=-g\mathbf{j},\qquad \mathbf{r}(t)=-\tfrac12gt^2\mathbf{j}+t,\mathbf{v}_0$$  
    $$x=(v_0\cos\alpha),t,\qquad y=(v_0\sin\alpha),t-\tfrac12gt^2$$  
    Quỹ đạo là một parabol. Tầm xa $d=\dfrac{v_0^2\sin2\alpha}{g}$, đạt cực đại khi $\alpha=45^\circ$. Nếu xuất phát từ độ cao $y_0$ thì cộng $y_0$ vào $y(t)$, đặt $y=0$ để tìm thời điểm chạm đất.

### Định luật Kepler (chứng minh định luật 1 từ Newton)

Ba định luật Kepler: (1) quỹ đạo là ellipse với Mặt Trời ở một tiêu điểm; (2) đường nối Mặt Trời và hành tinh quét diện tích bằng nhau trong thời gian bằng nhau; (3) bình phương chu kỳ tỉ lệ với lập phương trục chính.

Các bước chứng minh định luật 1 (đặt Mặt Trời ở gốc, dùng $\mathbf{F}=m\mathbf{a}$ và lực hấp dẫn $\mathbf{F}=-\dfrac{GMm}{r^3}\mathbf{r}$):

1. $\mathbf{a}=-\dfrac{GM}{r^3}\mathbf{r}$ song song với $\mathbf{r}$, nên $\mathbf{r}\times\mathbf{a}=\mathbf{0}$.
2. $\dfrac{d}{dt}(\mathbf{r}\times\mathbf{v})=\mathbf{0}$, suy ra $\mathbf{r}\times\mathbf{v}=\mathbf{h}$ là véc-tơ hằng. Do đó quỹ đạo nằm trong một mặt phẳng vuông góc với $\mathbf{h}$.
3. $\mathbf{h}=r^2(\mathbf{u}\times\mathbf{u}')$ với $\mathbf{u}=\mathbf{r}/r$, từ đó $\mathbf{a}\times\mathbf{h}=GM,\mathbf{u}'$ (dùng $\mathbf{u}\cdot\mathbf{u}'=0$ và công thức tích có hướng ba).
4. $(\mathbf{v}\times\mathbf{h})'=GM,\mathbf{u}'$, tích phân được $\mathbf{v}\times\mathbf{h}=GM,\mathbf{u}+\mathbf{c}$.
5. Nhân vô hướng với $\mathbf{r}$ rồi dùng tọa độ cực $(r,\theta)$:  
    $$r=\frac{ed}{1+e\cos\theta},\qquad e=\frac{c}{GM},\ d=\frac{h^2}{c}$$  
    Đây là phương trình cực của đường conic có tiêu điểm tại gốc với độ lệch tâm $e$. Quỹ đạo là đường cong đóng nên là ellipse.

---

Slide 54 và 68 (bảng tổng hợp công thức $\mathbf{T},\mathbf{N},\mathbf{B},\kappa$) là hình ảnh nên mình trình bày lại bằng công thức ở trên. Hai bài tập cuối chương trong file: tìm góc nâng và tầm xa cực đại của vật phóng 40 m/s từ đáy đường hầm cao 30 m (slide 101), cùng các phần "bài tập về nhà" chứng minh trong bài (ví dụ $\tfrac{d\mathbf{T}}{ds}\parallel\mathbf{N}$ và công thức độ xoắn).

Bạn muốn mình giải bài tập ở slide 101, làm tiếp phần chứng minh còn để trống, hay soạn bộ câu hỏi ôn tập cho chương này?