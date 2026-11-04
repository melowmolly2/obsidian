# Tóm tắt lý thuyết Chương 3 (phần 1): Hàm nhiều biến

## 3.1. Hàm hai biến

**Định nghĩa.** Cho $D\subseteq\mathbb{R}^2$. Hàm $f: D\to\mathbb{R}$ là quy tắc gán mỗi cặp $(x,y)\in D$ với đúng một số thực $f(x,y)$. Ta viết $z=f(x,y)$, trong đó $x,y$ là biến độc lập và $z$ là biến phụ thuộc.

**Tập xác định.** Nếu hàm cho bởi công thức mà không nêu rõ tập xác định, thì $D$ là tập mọi $(x,y)$ làm công thức có nghĩa.

Ví dụ: $f(x,y)=\dfrac{\sqrt{x+y+1}}{x-1}$ có
$$D=\{(x,y)\in\mathbb{R}^2 \mid x+y\ge -1,\ x\ne 1\}.$$

**Tập giá trị.** Là tập mọi giá trị mà hàm có thể nhận.

Ví dụ: $g(x,y)=\sqrt{9-x^2-y^2}$ có $D=\{x^2+y^2\le 9\}$ và tập giá trị $[0,3]$.

**Đồ thị.** Đồ thị của $f$ là
$$\{(x,y,z)\in\mathbb{R}^3 \mid (x,y)\in D,\ z=f(x,y)\},$$
là một mặt $S$ trong không gian.

- **Hàm tuyến tính** $f(x,y)=ax+by+c$ có đồ thị là mặt phẳng $ax+by-z+c=0$.
- $g(x,y)=\sqrt{9-x^2-y^2}$ có đồ thị là nửa trên của mặt cầu $x^2+y^2+z^2=9$, vì $z\ge 0$.
- Mặt cầu $x^2+y^2+z^2=c^2$ không phải đồ thị của một hàm hai biến. Nó gồm hai hàm: $z=\pm\sqrt{c^2-x^2-y^2}$.

**Đường mức.** Là các đường cong có phương trình $f(x,y)=k$, với $k$ thuộc tập giá trị của $f$. Chúng là hình chiếu lên mặt phẳng $Oxy$ của giao tuyến giữa đồ thị và mặt phẳng $z=k$. Đường mức dày thì đồ thị dốc, đường mức thưa thì đồ thị thoải.

| Hàm | Đường mức |
|---|---|
| $f=6-3x-2y$ | $3x+2y+(k-6)=0$: các đường thẳng song song, hệ số góc $-\tfrac32$ |
| $g=\sqrt{9-x^2-y^2}$ | $x^2+y^2=9-k^2$ $(0\le k\le 3)$: các đường tròn đồng tâm |
| $f=4x^2+y^2+1$ | $\dfrac{x^2}{\frac14(k-1)}+\dfrac{y^2}{k-1}=1$ $(k>1)$: các ellipse, đồ thị là elliptic paraboloid |

## 3.2. Hàm ba biến hoặc nhiều biến hơn

Hàm $n$ biến gán mỗi bộ $(x_1,\dots,x_n)\in D\subseteq\mathbb{R}^n$ với đúng một số thực $f(x_1,\dots,x_n)$.

- **Tập xác định.** Ví dụ $f(x,y,z)=\ln(z-y)+xy\sin z$ có $D=\{(x,y,z)\mid y<z\}$, là nửa không gian.
- **Mặt mức** (thay cho đồ thị, vì đồ thị nằm trong không gian 4 chiều): $f(x,y,z)=k$. Ví dụ $f=x^2+y^2+z^2$ có mặt mức $x^2+y^2+z^2=k$ $(k\ge 0)$, là các mặt cầu tâm $O$ bán kính $\sqrt{k}$.
- **Dạng tuyến tính $n$ biến:**
$$C=f(\mathbf{x})=c_1x_1+\dots+c_nx_n=\mathbf{c}\cdot\mathbf{x}.$$

## 3.3. Giới hạn và tính liên tục

### Định nghĩa giới hạn (hai biến)
$$\lim_{(x,y)\to(a,b)}f(x,y)=L$$
nếu $\forall\varepsilon>0,\ \exists\delta>0$ sao cho
$$(x,y)\in D,\quad 0<\sqrt{(x-a)^2+(y-b)^2}<\delta \ \Rightarrow\ |f(x,y)-L|<\varepsilon.$$

### Ý tưởng cốt lõi
Với hàm một biến, $x\to a$ chỉ có 2 hướng (trái, phải). Với hàm hai biến, $(x,y)\to(a,b)$ theo vô số đường. Nếu giới hạn tồn tại thì giới hạn dọc **mọi** đường đều bằng nhau.

**Phương pháp chứng minh giới hạn không tồn tại:** chỉ ra hai đường đi cho hai giới hạn khác nhau.

- $\displaystyle\lim_{(x,y)\to(0,0)}\frac{x^2-y^2}{x^2+y^2}$: dọc $Ox$ ($y=0$) được $1$, dọc $Oy$ ($x=0$) được $-1$, nên không tồn tại.
- $\displaystyle\lim_{(x,y)\to(0,0)}\frac{xy}{x^2+y^2}$: dọc hai trục đều được $0$, nhưng dọc $y=x$ được $\tfrac12$, nên không tồn tại.
- $\displaystyle\lim_{(x,y)\to(0,0)}\frac{xy^2}{x^2+y^4}$: dọc $y=x$ được $0$, dọc $x=y^2$ được $\tfrac12$, nên không tồn tại.

Từ ví dụ 2.2 và 2.3, kết quả $0$ dọc các đường thẳng (hay dọc hai trục) **chưa đủ** để kết luận giới hạn tồn tại.

**Phương pháp chứng minh giới hạn tồn tại:** dự đoán giá trị, rồi dùng định nghĩa $\varepsilon$–$\delta$ hoặc đánh giá kẹp.

Ví dụ $\displaystyle\lim_{(x,y)\to(0,0)}\frac{3x^2y}{x^2+y^2}=0$: vì $\dfrac{x^2}{x^2+y^2}\le 1$ nên
$$\left|\frac{3x^2y}{x^2+y^2}\right|\le 3|y|=3\sqrt{y^2}\le 3\sqrt{x^2+y^2}.$$
Chọn $\delta=\varepsilon/3$ thì $0<\sqrt{x^2+y^2}<\delta\Rightarrow |f|<\varepsilon$.

### Các phép toán giới hạn (Định lý 2.1)
Nếu các giới hạn tồn tại thì:
$$\lim (f\pm g)=\lim f\pm\lim g,\qquad \lim(fg)=\lim f\cdot\lim g,\qquad \lim\frac{f}{g}=\frac{\lim f}{\lim g}\ \ (\lim g\neq 0).$$

### Tính liên tục
$f$ **liên tục tại** $(a,b)$ nếu
$$\lim_{(x,y)\to(a,b)}f(x,y)=f(a,b).$$
$f$ **liên tục trên** $D$ nếu liên tục tại mọi điểm của $D$.

**Các kết quả cần nhớ:**
- Tổng, hiệu, tích, thương (mẫu khác 0) của các hàm liên tục là hàm liên tục.
- **Đa thức** liên tục trên $\mathbb{R}^2$. Đa thức hai biến có dạng tổng các số hạng $c\,x^my^n$ với $m,n\in\mathbb{N}$.
- **Hàm hữu tỉ** (thương của hai đa thức) liên tục trên tập xác định của nó.
- **Hàm hợp:** nếu $f$ liên tục trên $A$ và $g$ liên tục trên $B$ thì $h=g\circ f$, $h(x,y)=g(f(x,y))$, liên tục trên $A$.

**Ví dụ:**
- $\displaystyle\lim_{(x,y)\to(1,2)}(x^2y^3-x^3y^2+3x+2y)=f(1,2)=11$ (đa thức nên thay trực tiếp).
- $h(x,y)=\arctan(y/x)$ liên tục tại mọi $(x,y)$ có $x\neq 0$.
- $g(x,y)=\begin{cases}\dfrac{x^2-y^2}{x^2+y^2}, & (x,y)\ne(0,0)\\[2mm] 0, & (x,y)=(0,0)\end{cases}$ xác định nhưng **không liên tục** tại $(0,0)$, vì giới hạn không tồn tại.
- $f(x,y)=\begin{cases}\dfrac{3x^2y}{x^2+y^2}, & (x,y)\ne(0,0)\\[2mm] 0, & (x,y)=(0,0)\end{cases}$ **liên tục** tại $(0,0)$, vì giới hạn bằng $0=f(0,0)$.
- $f(x,y,z)=\dfrac{1}{x^2+y^2+z^2-1}$ liên tục tại mọi điểm không thuộc mặt cầu $x^2+y^2+z^2=1$.

### Giới hạn và liên tục của hàm $n$ biến
$$\lim_{\mathbf{x}\to\mathbf{a}}f(\mathbf{x})=L \iff \forall\varepsilon>0,\ \exists\delta>0:\ 0<\|\mathbf{x}-\mathbf{a}\|<\delta\Rightarrow|f(\mathbf{x})-L|<\varepsilon.$$
$f$ liên tục tại $\mathbf{a}$ nếu $\displaystyle\lim_{\mathbf{x}\to\mathbf{a}}f(\mathbf{x})=f(\mathbf{a})$.

## Vài lỗi nhỏ trong slide cần lưu ý
- **Ví dụ 1.3:** tập giá trị viết là $\{[0,3]\}$, đúng ra là đoạn $[0,3]$.
- **Ví dụ 1.9:** "tiêu cự" ở đây thực ra là độ dài các **bán trục**: $\tfrac12\sqrt{k-1}$ (theo $x$) và $\sqrt{k-1}$ (theo $y$).
- **Định nghĩa 2.3:** điều kiện $0<\|\mathbf{x}-\mathbf{a}\|\le\delta$ nên là $<\delta$ cho thống nhất với Định nghĩa 2.1.

Nếu bạn cần, mình có thể làm thêm bài tập mẫu về tìm tập xác định, vẽ đường mức, và chứng minh giới hạn bằng $\varepsilon$–$\delta$ hoặc bằng đường đi (đổi sang tọa độ cực).