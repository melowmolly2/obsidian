Mình đã đọc hết 94 slide của Tuần 07. Tuần này học kỳ vọng, phương sai, i.i.d. và tổng/trung bình, Chebyshev, luật số lớn, biến ngẫu nhiên liên tục, các phân phối liên tục và Định lý giới hạn trung tâm. Đây cũng là tuần cuối trước kiểm tra giữa kỳ (Tuần 8).

## 1. Kỳ vọng

$$E(X)=\sum_x x,p_X(x)$$

Kỳ vọng là trung bình có trọng số (trọng số là xác suất) và không nhất thiết là giá trị $X$ có thể nhận. Ví dụ hai sản phẩm (mỗi cái đạt với xác suất $0.8$): $E(X)=0(0.04)+1(0.32)+2(0.64)=1.6$.

**Tính chất** (với $a,b,c$ là hằng số):

$$E(c)=c, \qquad E(aX)=aE(X), \qquad E(aX+bY)=aE(X)+bE(Y)$$

Ví dụ chi phí $C=50+20X$ thì $E(C)=50+20(1.6)=82$ nghìn đồng.

**Kỳ vọng của hàm:**

$$E[g(X)]=\sum_x g(x)P(X=x), \qquad E[g(X)]\neq g(E(X)) \text{ nói chung}$$

Ví dụ chia bánh: $X=\dfrac{1}{N+1}$ có $E(X)=\dfrac{7}{12}$ nhưng $\dfrac{1}{E(N+1)}=\dfrac12$.

**Kỳ vọng các phân phối rời rạc:**

|Phân phối|$E(X)$|$\text{Var}(X)$|
|---|---|---|
|Bernoulli$(p)$|$p$|$p(1-p)$|
|Nhị thức$(n,p)$|$np$|$np(1-p)$|
|Siêu bội$(N,K,n)$, $p=K/N$|$nK/N$|$np(1-p)\dfrac{N-n}{N-1}$|
|Poisson$(\lambda)$|$\lambda$|$\lambda$|

## 2. Phương sai và độ lệch chuẩn

$$\text{Var}(X)=E[(X-\mu)^2]=E(X^2)-[E(X)]^2, \qquad SD(X)=\sqrt{\text{Var}(X)}$$

- Phương sai có đơn vị bình phương, SD cùng đơn vị với $X$.
- Ví dụ hai sản phẩm: $E(X^2)=2.88$, $\text{Var}(X)=2.88-1.6^2=0.32$, $SD\approx0.566$.

**Tính chất:**

$$\text{Var}(c)=0, \qquad \text{Var}(aX+b)=a^2,\text{Var}(X), \qquad SD(aX+b)=|a|,SD(X)$$

$$\text{Var}(X\pm Y)=\text{Var}(X)+\text{Var}(Y) \quad (X,Y \text{ độc lập})$$

- Phương sai cộng được (với biến độc lập), độ lệch chuẩn thì **không** cộng.
- Ví dụ nhiệt độ $Y=1.8X+32$ với $E(X)=25$, $SD(X)=3$: $E(Y)=77$, $\text{Var}(Y)=1.8^2\cdot9=29.16$, $SD(Y)=5.4$. Cộng $32$ chỉ dịch tâm, không đổi độ phân tán.

## 3. i.i.d., mô hình chiếc hộp, tổng và trung bình

- **i.i.d.:** độc lập (thông tin về biến khác không đổi phân phối của một biến) và cùng phân phối (cùng PMF/CDF).
- **Mô hình chiếc hộp:** rút một lá thăm có ghi số; số trên lá là giá trị của biến ngẫu nhiên. Rút **có hoàn lại** từ cùng một hộp cho các biến i.i.d. Kỳ vọng của một lần rút là trung bình các số trong hộp, phương sai là trung bình bình phương độ lệch so với trung bình hộp.
- Với $X_1,\dots,X_n$ i.i.d., kỳ vọng $\mu$, phương sai $\sigma^2$:

|Đại lượng|Kỳ vọng|Phương sai|SD|
|---|---|---|---|
|Tổng $S_n=X_1+\cdots+X_n$|$n\mu$|$n\sigma^2$|$\sigma\sqrt n$|
|Trung bình $\bar X_n=S_n/n$|$\mu$|$\sigma^2/n$|$\sigma/\sqrt n$|

Các công thức này đúng với mọi $n\ge1$, không cần xấp xỉ chuẩn.

**Ví dụ hộp ${0,0,1,1,1,2,3,3,4,4}$:** $\mu=1.9$, $E(X^2)=5.7$, $\sigma^2=5.7-1.9^2=2.09$, $\sigma\approx1.4457$.

||$n=25$|$n=100$|
|---|---|---|
|$E(S_n)$|$47.5$|$190$|
|$SD(S_n)=\sqrt{n\cdot2.09}$|$7.228$|$14.457$|
|$E(\bar X_n)$|$1.9$|$1.9$|
|$SD(\bar X_n)=\sqrt{2.09/n}$|$0.289$|$0.145$|

Tăng $n$ gấp $4$: SD của tổng tăng gấp $2$, SD của trung bình giảm một nửa.

## 4. Chebyshev và luật số lớn yếu

**Bất đẳng thức Chebyshev:** với mọi $\varepsilon>0$,

$$P(|X-\mu|\ge\varepsilon)\le\frac{\sigma^2}{\varepsilon^2}, \qquad P(|\bar X_n-\mu|\ge\varepsilon)\le\frac{\sigma^2}{n\varepsilon^2}$$

Đây là cận trên, không cần giả sử phân phối chuẩn.

**Ví dụ nhiệt độ lò** ($\sigma=1$, sai khác $\le0.2$ với xác suất $\ge99%$): $\dfrac{1}{n(0.2)^2}=\dfrac{25}{n}\le0.01\Rightarrow n\ge2500$. Đây là số đủ theo Chebyshev, không nhất thiết là số tối thiểu thực tế.

**Luật số lớn yếu:** với i.i.d. có kỳ vọng $\mu$ và $E(|X_1|)<\infty$,

$$P(|\bar X_n-\mu|>\varepsilon)\to0 \quad \text{khi } n\to\infty \quad (\text{hội tụ theo xác suất})$$

- Khi phương sai hữu hạn, Chebyshev giải thích vì $\sigma^2/(n\varepsilon^2)\to0$; luật số lớn yếu không đòi hỏi phương sai hữu hạn.
- **Hiểu lầm:** sau $10$ lần sấp, lần $11$ vẫn có xác suất ngửa là $0.5$ (các lần độc lập). Tỷ lệ tích lũy không hội tụ đơn điệu; luật chỉ nói về giới hạn khi $n\to\infty$.

## 5. Biến ngẫu nhiên liên tục

**Hàm mật độ $f_X$:**

$$f_X(x)\ge0, \qquad \int_{-\infty}^{\infty}f_X(x),dx=1, \qquad P(a<X\le b)=\int_a^b f_X(x),dx$$

Xác suất bằng diện tích dưới đường mật độ, và $P(X=a)=0$.

**CDF:**

$$F_X(x)=P(X\le x)=\int_{-\infty}^x f_X(t),dt, \qquad P(a<X<b)=F(b)-F(a)$$

**Kỳ vọng và phương sai:**

$$\mu=\int_{-\infty}^{\infty}xf_X(x),dx, \qquad \text{Var}(X)=\int(x-\mu)^2f_X(x),dx=E(X^2)-\mu^2$$

**Ví dụ $f(x)=2x$ trên $(0,1)$:**

- $F_X(x)=0$ khi $x\le0$; $x^2$ khi $0<x<1$; $1$ khi $x\ge1$.
- $P(0.2<X<0.6)=0.6^2-0.2^2=0.32$.
- $E(X)=\dfrac23$, $E(X^2)=\dfrac12$, $\text{Var}(X)=\dfrac12-\dfrac49=\dfrac1{18}$.

**Từ CDF suy ra mật độ:** $F(x)=x^2/9$ trên $[0,b]$ cho $b^2/9=1\Rightarrow b=3$ và $f(x)=\dfrac{2x}{9}$ trên $(0,3)$ (đạo hàm CDF).

## 6. Các phân phối liên tục

|Phân phối|Mật độ|$E(X)$|$\text{Var}(X)$|
|---|---|---|---|
|Đều $U(a,b)$|$\dfrac1{b-a}$ trên $(a,b)$|$\dfrac{a+b}{2}$|$\dfrac{(b-a)^2}{12}$|
|Chuẩn $\mathcal N(\mu,\sigma^2)$|$\dfrac1{\sigma\sqrt{2\pi}}\exp!\Big[-\dfrac{(x-\mu)^2}{2\sigma^2}\Big]$|$\mu$|$\sigma^2$|
|Mũ $\text{Exp}(\lambda)$|$\lambda e^{-\lambda x}$, $x\ge0$|$\dfrac1\lambda$|(không nêu trong slide)|

- **Đều:** chờ xe buýt $X\sim U(0,10)$: $P(2<X<5)=\dfrac{3}{10}=0.3$, $E(X)=5$.
- **Chuẩn:** hình chuông, đối xứng quanh $\mu$. Chuẩn hóa $Z=\dfrac{X-\mu}{\sigma}\sim\mathcal N(0,1)$ và $P(X\le x)=\Phi!\left(\dfrac{x-\mu}{\sigma}\right)$.
    - Ví dụ điểm $86$ (trung bình $70$, SD $8$): $z=\dfrac{86-70}{8}=2$.
    - **Quy tắc 68–95–99.7:** $P(\mu-k\sigma<X<\mu+k\sigma)\approx0.68,\ 0.95,\ 0.997$ với $k=1,2,3$. Ví dụ chai $\mathcal N(500,2^2)$: $[498,502]$ chứa khoảng $68%$, $[496,504]$ chứa khoảng $95%$, $P(X>504)\approx2.5%$.
    - **Phân vị:** $q_p=\mu+\sigma,\Phi^{-1}(p)$. Ví dụ chai: $P(X\le503)=0.9332$, $P(498<X<502)=0.6827$, $q_{0.95}=503.29$ ml.
    - SciPy: `norm.cdf(x, loc=μ, scale=σ)` (`scale` là SD, không phải phương sai), `norm.sf`, `norm.ppf`.
- **Mũ:** lệch phải, mô hình thời gian chờ. Ví dụ chờ trung bình $2$ phút thì $\lambda=0.5$ và $P(X>3)=e^{-1.5}\approx0.2231$.
- **$\chi^2_\nu$ và $t_\nu$ (chỉ nhận biết hình dạng):** $\chi^2$ nhận giá trị $>0$; $t$ đối xứng quanh $0$, đuôi dày hơn chuẩn và tiến gần chuẩn khi $\nu$ tăng. Sẽ dùng ở các tuần suy luận sau.

## 7. Định lý giới hạn trung tâm (CLT)

Với $X_i$ i.i.d., $E(X_i)=\mu$, $0<\sigma^2<\infty$:

$$Z_n=\frac{S_n-n\mu}{\sigma\sqrt n}=\frac{\bar X_n-\mu}{\sigma/\sqrt n}\xrightarrow{d}\mathcal N(0,1)$$

$$S_n\approx\mathcal N(n\mu,,n\sigma^2), \qquad \bar X_n\approx\mathcal N(\mu,,\sigma^2/n)$$

- **Cỡ mẫu $n$** là số lần rút để tính một tổng hoặc trung bình, quyết định phương sai và chất lượng xấp xỉ. **Số lần lặp mô phỏng** (ví dụ $5000$) chỉ giúp vẽ histogram rõ hơn, không đổi cỡ mẫu.
- Từ phân phối mũ lệch phải, trung bình chuẩn hóa $Z_n$ càng gần $\mathcal N(0,1)$ khi $n=1,5,30,100$ tăng.
- Chất lượng xấp xỉ còn phụ thuộc dạng phân phối gốc.

## 8. Các bài tập mẫu cần nhớ

**Kỳ vọng và phương sai (USB):** $x=1,2,4,8,16$ với xác suất $0.05,0.10,0.35,0.40,0.10$.

$$E(X)=6.45, \quad E(X^2)=57.25, \quad \text{Var}(X)=57.25-6.45^2=15.6475\ \text{GB}^2, \quad SD\approx3.9557\ \text{GB}$$

**Thang máy** ($\mathcal N(65,5^2)$, $10$ người, tải $700$ kg): $S_{10}\sim\mathcal N(650,250)$ nên

$$P(S_{10}\le700)=\Phi!\left(\frac{700-650}{5\sqrt{10}}\right)\approx\Phi(3.1623)\approx0.9992$$

**Khoảng cách tới trường** ($\text{Exp}$, trung bình $5$ km nên $\lambda=\tfrac15$, $SD=5$):

|Câu|Kết quả|
|---|---|
|$P(X>10)$|$e^{-2}\approx0.1353$|
|$P(S_{100}\le300)$, $S_{100}\approx\mathcal N(500,2500)$|$\Phi(-4)\approx0.00003$|
|$P(4.9<\bar X_{100}<5.2)$, $SD=0.5$|$\Phi(0.4)-\Phi(-0.2)\approx0.2347$|
|Chính xác một sinh viên $P(4.9<X<5.2)$|$e^{-4.9/5}-e^{-5.2/5}\approx0.0219$|
|$P(4.9<\bar X_{36}<5.2)$, $SD=5/6$|$\Phi(0.24)-\Phi(-0.12)\approx0.1426$|

Cùng khoảng nhưng kết quả khác nhau vì $SD(\bar X)$ phụ thuộc cỡ mẫu.

**Thời gian xử lý** (trung bình $12$, SD $6$, $n=64$): $\bar X\approx\mathcal N(12,,6^2/64)$, $SD=0.75$, $P(\bar X>13.5)\approx P(Z>2)\approx0.0228$.

**Linh kiện thay thế** (tuổi thọ trung bình $100$, SD $30$, cần hoạt động $\ge2000$ giờ với xác suất $\ge95%$): $S_n\approx\mathcal N(100n,900n)$ và cần

$$\frac{100n-2000}{30\sqrt n}\ge1.64485$$

Thử các số nguyên: $n=22$ cho $0.9224$, $n=23$ cho $0.9815$. Chọn $23$ linh kiện ($1$ ban đầu và $22$ dự phòng). Đây là ước tính theo CLT, không phải bảo đảm cho mọi phân phối.

## 9. Ghi nhớ cuối

- Kỳ vọng mô tả trung tâm; phương sai/SD mô tả phân tán. $\text{Var}(aX+b)=a^2\text{Var}(X)$, $SD(aX+b)=|a|SD(X)$.
- Biến độc lập: phương sai cộng, SD không cộng. Tổng có SD $\sigma\sqrt n$, trung bình có SD $\sigma/\sqrt n$.
- Chebyshev cho cận trên của xác suất sai lệch; luật số lớn yếu giải thích sự ổn định của trung bình mẫu.
- Với biến liên tục: xác suất bằng diện tích dưới mật độ, $P(X=a)=0$, và $F(b)-F(a)$ cho xác suất trên khoảng.
- Chuẩn hóa $Z=\dfrac{X-\mu}{\sigma}$ rồi dùng $\Phi$ (hoặc quy tắc 68–95–99.7).
- CLT cho phép xấp xỉ chuẩn cho tổng và trung bình; cần quan sát i.i.d. với phương sai hữu hạn.

**Tuần 8** là kiểm tra giữa kỳ (dữ liệu, thống kê mô tả, xác suất, biến ngẫu nhiên). **Tuần 9** sẽ học từ mẫu đến tổng thể và khoảng tin cậy.

Nếu cần, mình có thể làm bộ câu hỏi trắc nghiệm hoặc flashcard ôn giữa kỳ cho Tuần 02–07.