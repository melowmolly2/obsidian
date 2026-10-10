Mình đã đọc hết 80 slide của Tuần 06 (Phân phối xác suất và biến ngẫu nhiên rời rạc). Tuần này học tần suất thực nghiệm, biến ngẫu nhiên, PMF, CDF và năm phân phối rời rạc thông dụng.

## 1. Xác suất lý thuyết và tần suất thực nghiệm

- **Tần suất tương đối:** nếu trong $m$ lần lặp, giá trị $x$ xuất hiện $n_x$ lần thì

$$\hat{p}_m(x)=\frac{n_x}{m}$$

- Biểu đồ lý thuyết không cần thu thập mẫu. Với cột rộng $1$, chiều cao và diện tích cột bằng $p_X(x)$, tổng diện tích bằng $1$.
- Khi số lần rút tăng, tần suất thường gần xác suất lý thuyết hơn. Tuy nhiên sai lệch không nhất thiết giảm sau mỗi lần tăng cỡ mẫu.
- **Ví dụ hộp thăm ${1,2,2,3,4}$:** $p_X=(\tfrac15,\tfrac25,\tfrac15,\tfrac15)$. Rút $50$ lần có thể cho tần suất của số $2$ là $0.48$, khác $0.40$.
- **Tổng hai xúc xắc:** $36$ cặp đồng khả năng nhưng các giá trị tổng không đồng khả năng: $P(X=2)=\tfrac1{36}$, $P(X=7)=\tfrac{6}{36}$. Mô phỏng $5000$ lần cho tần suất tổng $7$ là $0.1598$ (lý thuyết $0.1667$).
- **NumPy:** `rng.choice(..., replace=True)` mô phỏng rút có hoàn lại; `rng.integers(1, 7)` sinh số từ $1$ đến $6$; đặt seed cố định để tái tạo kết quả.

## 2. Biến ngẫu nhiên

- **Biến ngẫu nhiên:** một hàm $X:\Omega\to\mathbb{R}$ gán số thực cho kết quả của phép thử.
- Một giá trị của $X$ có thể ứng với nhiều kết quả. Ví dụ tung xu $3$ lần, $X$ là số ngửa: ${X=2}={HHT,HTH,THH}$.
- **Rời rạc:** nhận tập hữu hạn hoặc đếm được các giá trị (số yêu cầu đến máy chủ trong một phút).
- **Liên tục:** nhận giá trị trên một khoảng của trục số (thời gian phản hồi, chiều cao). Học ở Tuần 07.

## 3. Hàm khối xác suất (PMF)

$$p_X(x)=P(X=x)$$

**Tính chất:**

$$0\le p_X(x)\le 1, \qquad \sum_{x\in S}p_X(x)=1$$

Xác suất của một biến cố là tổng $p_X$ trên các giá trị thỏa biến cố, ví dụ $P(X\ge 2)=p_X(2)+p_X(3)$.

**Ví dụ:**

- Tung xu $3$ lần, $X$ là số ngửa: $p_X=(\tfrac18,\tfrac38,\tfrac38,\tfrac18)$ cho $x=0,1,2,3$.
- $X=$ số ngửa $-$ số sấp. Nếu $N$ là số ngửa thì $X=2N-3$, chỉ nhận các giá trị lẻ $-3,-1,1,3$ với xác suất $\tfrac18,\tfrac38,\tfrac38,\tfrac18$, nên $P(X=0)=0$.

## 4. Hàm phân phối tích lũy (CDF)

$$F_X(x)=P(X\le x), \qquad \text{xác định với mọi } x\in\mathbb{R}$$

**Tính chất:**

- $F_X$ nằm trong $[0,1]$ và không giảm; $F_X\to 0$ khi $x\to-\infty$, $F_X\to1$ khi $x\to+\infty$.
- Với $a<b$:

$$P(a<X\le b)=F_X(b)-F_X(a)$$

- Với biến rời rạc, $F_X$ là hàm bậc thang. Độ nhảy tại $x$ bằng $P(X=x)$, và $F_X$ **liên tục bên phải** (giá trị tại điểm nhảy lấy ở đầu trên).

**Ví dụ hai sản phẩm** (mỗi sản phẩm đạt với xác suất $0.8$): $p_X=(0.04,,0.32,,0.64)$ và

$$F_X(x)=\begin{cases}0 & x<0\ 0.04 & 0\le x<1\ 0.36 & 1\le x<2\ 1 & x\ge 2\end{cases}$$

Khi đó:

- $P(0<X\le 2)=F_X(2)-F_X(0)=0.96$.
- Với biến nguyên, $P(X<2)=P(X\le1)=F_X(1)=0.36$.
- $P(X=1)=F_X(1)-F_X(0)=0.32$.

**Ví dụ sáu đường dây:** $p_X=(0.10,0.15,0.20,0.25,0.20,0.06,0.04)$.

- $P(X\le 3)=0.70$ ("nhiều nhất ba" gồm $X=3$).
- $P(X<3)=0.45$ ("ít hơn ba" không gồm $X=3$).
- Số đường chưa dùng $Y=6-X$, nên $P(2\le Y\le 4)=P(2\le X\le 4)=0.65$.

## 5. Các phân phối rời rạc thông dụng

|Phân phối|Ký hiệu / tham số|PMF|Khi nào dùng|
|---|---|---|---|
|Đều rời rạc|$m$|$P(X=k)=\dfrac1m,\ k=1,\dots,m$|$m$ giá trị cùng xác suất|
|Bernoulli|$p$|$P(X=1)=p,\ P(X=0)=1-p$|một phép thử, hai kết quả|
|Nhị thức|$\text{Binomial}(n,p)$|$\dbinom nk p^k(1-p)^{n-k}$|$n$ phép thử độc lập, $p$ không đổi|
|Siêu bội|$\text{Hypergeometric}(N,K,n)$|$\dfrac{\binom Kk\binom{N-K}{n-k}}{\binom Nn}$|rút $n$ **không hoàn lại** từ tổng thể hữu hạn|
|Poisson|$\text{Poisson}(\lambda)$|$e^{-\lambda}\dfrac{\lambda^k}{k!},\ k=0,1,2,\dots$|đếm sự kiện trong khoảng cố định|

**Bốn điều kiện của mô hình nhị thức:**

1. Số phép thử $n$ cố định trước.
2. Mỗi phép thử có đúng hai kết quả.
3. Các phép thử độc lập.
4. Xác suất thành công $p$ không đổi.

Nếu $p=0$ thì luôn $X=0$; nếu $p=1$ thì luôn $X=n$.

**Siêu bội:**

- Hộp có $N$ lá, $K$ lá ghi $1$ và $N-K$ lá ghi $0$; rút $n$ lá không hoàn lại. Các lần rút phụ thuộc nhau.
- Công thức chỉ dùng khi $0\le k\le K$ và $0\le n-k\le N-K$; giá trị không thể xảy ra có xác suất $0$.

**Poisson:**

- $\lambda$ là số lần xảy ra **trung bình trong cả khoảng đang xét**.
- Dùng khi các sự kiện độc lập và tốc độ trung bình ổn định.
- Đổi độ dài khoảng thì $\lambda$ đổi theo: tốc độ $4$ yêu cầu/giây thì trong $3$ giây là $\text{Poisson}(3\times4)=\text{Poisson}(12)$.

## 6. Các ví dụ tính toán

|Bài|Mô hình|Kết quả|
|---|---|---|
|Xúc xắc, $P(X\ge5)$|đều rời rạc trên ${1,\dots,6}$|$\tfrac13$|
|Số nguyên $N$ từ $1$ đến $1000$, $Y=1$ nếu $N$ chia hết cho $3$|$Y\sim\text{Bernoulli}(0.333)$|$N$ đều nhưng $Y$ không đều trên ${0,1}$|
|$20$ câu trắc nghiệm, chọn ngẫu nhiên|$X\sim\text{Binomial}(20,0.25)$|$P(X=8)\approx0.0609$; $P(X>2)\approx0.9087$|
|$12$ sản phẩm, đạt chuẩn $0.95$|$X\sim\text{Binomial}(12,0.95)$|$P(X=11)\approx0.341$; $P(X\ge11)\approx0.882$|
|Hộp $10$ thăm ($6$ ghi $1$), rút $3$|$X\sim\text{Hypergeometric}(10,6,3)$|$P(X=2)=\dfrac{\binom62\binom41}{\binom{10}3}=\dfrac{60}{120}=0.5$|
|Hai lớp $20$ và $30$, chấm $15$ bài|$X\sim\text{Hypergeometric}(50,30,15)$|$P(X=10)\approx0.2070$; ít nhất $10$ bài cùng lớp: $\approx0.3938$|
|$\text{Poisson}(1)$||$P(X=1)=e^{-1}\approx0.3679$; $P(X\le1)=2e^{-1}\approx0.7358$|
|Máy chủ $4$ yêu cầu/giây|$X\sim\text{Poisson}(4)$|$P(X=0)=e^{-4}\approx0.0183$; $P(X>6)\approx0.111$|
|$8$ cảm biến, cảnh báo giả $0.04$|$X\sim\text{Binomial}(8,0.04)$|$P(X\ge1)=1-0.96^8\approx0.279$|

**Có hoàn lại và không hoàn lại** (hộp $2$ đỏ, $2$ xanh, rút $3$ lần):

|$x$|$0$|$1$|$2$|$3$|
|---|---|---|---|---|
|Có hoàn lại ($\text{Binomial}(3,\tfrac12)$)|$\tfrac18$|$\tfrac38$|$\tfrac38$|$\tfrac18$|
|Không hoàn lại ($\text{Hypergeometric}(4,2,3)$)|$0$|$\tfrac12$|$\tfrac12$|$0$|

Không hoàn lại thì mỗi lần rút đổi thành phần hộp, nên các lần rút phụ thuộc.

**Bài hàng tồn kho:** $X\sim\text{Binomial}(15,0.75)$ là số khách chọn loại xích. Có $10$ bộ xích và $8$ bộ trục nên cần $X\le10$ và $15-X\le8$, tức $7\le X\le10$:

$$P(A)=\sum_{k=7}^{10}\binom{15}{k}(0.75)^k(0.25)^{15-k}\approx0.3093$$

Tổng tồn kho đủ lớn chưa bảo đảm đủ hàng đúng loại khách cần.

## 7. Chọn mô hình

|Tình huống|Mô hình|
|---|---|
|Một gói hàng có đúng hạn hay không|Bernoulli|
|Số gói đúng hạn trong $20$ gói độc lập|Nhị thức (nếu $p$ không đổi, độc lập)|
|Số cuộc gọi đến tổng đài trong $10$ phút|Poisson (nếu tốc độ ổn định, các khoảng rời nhau độc lập)|
|Số sinh viên thuận tay trái trong $20$ người lấy không hoàn lại từ khoa $180$ người|Siêu bội|

Mỗi mô hình chỉ phù hợp khi các điều kiện đi kèm được đáp ứng gần đúng.

## 8. SciPy

|Hàm|Ý nghĩa|
|---|---|
|`pmf(k, ...)`|$P(X=k)$|
|`cdf(k, ...)`|$P(X\le k)$|
|`sf(k, ...)`|$P(X>k)$|

- Ví dụ: `stats.binom.pmf(8, n=20, p=0.25)`, `stats.binom.sf(2, n=20, p=0.25)`.
- Poisson: tham số `mu` tương ứng $\lambda$.
- Siêu bội trong SciPy: `hypergeom(M, n, N)` với $M$ là tổng thể, $n$ là số lá ghi $1$, $N$ là cỡ mẫu, khác ký hiệu $(N,K,n)$ trên slide.

## 9. Ghi nhớ cuối

- Biểu đồ phân phối xác suất mô tả mô hình; biểu đồ tần suất thực nghiệm tóm tắt dữ liệu mô phỏng.
- PMF cho xác suất tại từng giá trị; CDF cho xác suất không vượt ngưỡng, và độ nhảy của CDF bằng PMF.
- Chú ý phân biệt "nhiều nhất" ($\le$) với "ít hơn" ($<$), và "ít nhất một" thường tính qua phần bù.
- Chọn nhị thức hay siêu bội tùy vào có hoàn lại hay không hoàn lại.

**Tuần 07 sẽ học:** kỳ vọng, phương sai, độ lệch chuẩn; biến ngẫu nhiên liên tục và xấp xỉ chuẩn; tổng và trung bình của các biến ngẫu nhiên.

Nếu cần, mình có thể làm bộ câu hỏi trắc nghiệm hoặc flashcard cho Tuần 05–06.