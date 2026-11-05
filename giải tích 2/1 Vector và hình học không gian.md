

# Tóm tắt lý thuyết Chương 1: Véc-tơ và hình học không gian

File gồm 177 slide, chia thành 6 phần (1.1–1.6) như dưới đây.

## 1.1. Hệ tọa độ 3 chiều

- Mỗi điểm trong không gian tương ứng 1-1 với bộ ba số thực $(a,b,c)\in\mathbb{R}^3$. Hướng trục $z$ xác định bằng quy tắc bàn tay phải. Ba mặt phẳng tọa độ chia không gian thành 8 góc phần tám (octant).
- Các mặt phẳng song song mặt tọa độ: $x=k,\ y=k,\ z=k$.
- Một phương trình theo $x,y,z$ biểu diễn một mặt trong $\mathbb{R}^3$. Ví dụ $x^2+y^2=1$ là mặt trụ tròn (không ràng buộc $z$).
- **Khoảng cách hai điểm:**
$$|P_1P_2|=\sqrt{(x_2-x_1)^2+(y_2-y_1)^2+(z_2-z_1)^2}$$
- **Mặt cầu** tâm $C(h,k,l)$, bán kính $r$:
$$(x-h)^2+(y-k)^2+(z-l)^2=r^2$$
Muốn nhận dạng một mặt cầu thì hoàn thành bình phương (Ví dụ 6).

## 1.2. Véc-tơ

- **Phép toán hình học:** cộng theo quy tắc tam giác hoặc hình bình hành, $\mathbf{u}-\mathbf{v}=\mathbf{u}+(-\mathbf{v})$, nhân với số thực $c\mathbf{v}$ (độ dài $|c||\mathbf{v}|$). Hai véc-tơ song song khi véc-tơ này là bội của véc-tơ kia.
- **Véc-tơ $\overrightarrow{AB}$:**
$$\overrightarrow{AB}=\langle x_2-x_1,\ y_2-y_1,\ z_2-z_1\rangle$$
- **Độ dài:**
$$|\mathbf{a}|=\sqrt{a_1^2+a_2^2+a_3^2}$$
- **Theo thành phần:** cộng, trừ và nhân vô hướng đều làm trên từng thành phần. Tám tính chất của phép toán (giao hoán, kết hợp, phân phối, …) đúng trong $\mathbb{R}^n$.
- **Cơ sở chuẩn tắc:** $\mathbf{i}=\langle1,0,0\rangle,\ \mathbf{j}=\langle0,1,0\rangle,\ \mathbf{k}=\langle0,0,1\rangle$, và $\mathbf{a}=a_1\mathbf{i}+a_2\mathbf{j}+a_3\mathbf{k}$.
- **Véc-tơ đơn vị** theo hướng $\mathbf{a}\neq\mathbf{0}$:
$$\mathbf{u}=\frac{1}{|\mathbf{a}|}\mathbf{a}$$
- **Ứng dụng:** lực căng dây (cân bằng lực $\mathbf{T}_1+\mathbf{T}_2=-\mathbf{w}$), vận tốc thuyền/máy bay cộng với dòng nước/gió.

## 1.3. Tích vô hướng (tích chấm)

- **Định nghĩa:**
$$\mathbf{a}\cdot\mathbf{b}=a_1b_1+\dots+a_nb_n$$
Kết quả là một số, không phải véc-tơ.
- **Tính chất:** $\mathbf{a}\cdot\mathbf{a}=|\mathbf{a}|^2$, giao hoán, phân phối, $(c\mathbf{a})\cdot\mathbf{b}=c(\mathbf{a}\cdot\mathbf{b})$, $\mathbf{0}\cdot\mathbf{a}=0$.
- **Công thức hình học** (chứng minh bằng định lý cosine):
$$\mathbf{a}\cdot\mathbf{b}=|\mathbf{a}||\mathbf{b}|\cos\theta\quad\Rightarrow\quad\cos\theta=\frac{\mathbf{a}\cdot\mathbf{b}}{|\mathbf{a}||\mathbf{b}|}$$
- **Dấu của tích chấm:** $\mathbf{a}\cdot\mathbf{b}>0$ thì $\theta$ nhọn, $\mathbf{a}\cdot\mathbf{b}<0$ thì $\theta$ tù, và
$$\mathbf{a}\perp\mathbf{b}\iff\mathbf{a}\cdot\mathbf{b}=0$$
- **Cosine định hướng** (các góc $\alpha,\beta,\gamma$ với trục $x,y,z$):
$$\cos\alpha=\frac{a_1}{|\mathbf{a}|},\ \cos\beta=\frac{a_2}{|\mathbf{a}|},\ \cos\gamma=\frac{a_3}{|\mathbf{a}|},\qquad \cos^2\alpha+\cos^2\beta+\cos^2\gamma=1$$
Chúng chính là các thành phần của véc-tơ đơn vị $\frac{1}{|\mathbf{a}|}\mathbf{a}$.
- **Hình chiếu của $\mathbf{b}$ lên $\mathbf{a}$:**
$$\mathrm{comp}_{\mathbf{a}}\mathbf{b}=\frac{\mathbf{a}\cdot\mathbf{b}}{|\mathbf{a}|},\qquad \mathrm{proj}_{\mathbf{a}}\mathbf{b}=\frac{\mathbf{a}\cdot\mathbf{b}}{|\mathbf{a}|^2}\mathbf{a}$$
- **Công của lực hằng:**
$$W=\mathbf{F}\cdot\mathbf{D}=|\mathbf{F}||\mathbf{D}|\cos\theta$$

## 1.4. Tích có hướng (chỉ trong $\mathbb{R}^3$)

- **Định nghĩa:**
$$\mathbf{a}\times\mathbf{b}=\langle a_2b_3-a_3b_2,\ a_3b_1-a_1b_3,\ a_1b_2-a_2b_1\rangle=\begin{vmatrix}\mathbf{i}&\mathbf{j}&\mathbf{k}\\a_1&a_2&a_3\\b_1&b_2&b_3\end{vmatrix}$$
- **Hướng và độ lớn:** $\mathbf{a}\times\mathbf{b}$ vuông góc với cả $\mathbf{a}$ và $\mathbf{b}$ (hướng theo quy tắc bàn tay phải), và
$$|\mathbf{a}\times\mathbf{b}|=|\mathbf{a}||\mathbf{b}|\sin\theta$$
- **Song song:** $\mathbf{a}\parallel\mathbf{b}\iff\mathbf{a}\times\mathbf{b}=\mathbf{0}$.
- **Diện tích:** $|\mathbf{a}\times\mathbf{b}|$ là diện tích hình bình hành tạo bởi $\mathbf{a},\mathbf{b}$. Diện tích tam giác bằng một nửa giá trị đó.
- **Cơ sở chuẩn tắc:** $\mathbf{i}\times\mathbf{j}=\mathbf{k},\ \mathbf{j}\times\mathbf{k}=\mathbf{i},\ \mathbf{k}\times\mathbf{i}=\mathbf{j}$.
- **Tính chất:**
  - $\mathbf{a}\times\mathbf{b}=-\mathbf{b}\times\mathbf{a}$, nên **không giao hoán**.
  - $(\mathbf{a}\times\mathbf{b})\times\mathbf{c}\neq\mathbf{a}\times(\mathbf{b}\times\mathbf{c})$ nói chung, nên **không kết hợp**.
  - Có tính phân phối, và $(c\mathbf{a})\times\mathbf{b}=c(\mathbf{a}\times\mathbf{b})$.
  - $\mathbf{a}\cdot(\mathbf{b}\times\mathbf{c})=(\mathbf{a}\times\mathbf{b})\cdot\mathbf{c}$.
  - $\mathbf{a}\times(\mathbf{b}\times\mathbf{c})=(\mathbf{a}\cdot\mathbf{c})\mathbf{b}-(\mathbf{a}\cdot\mathbf{b})\mathbf{c}$.
- **Tích vô hướng ba:**
$$\mathbf{a}\cdot(\mathbf{b}\times\mathbf{c})=\begin{vmatrix}a_1&a_2&a_3\\b_1&b_2&b_3\\c_1&c_2&c_3\end{vmatrix}$$
Thể tích hình hộp là $V=|\mathbf{a}\cdot(\mathbf{b}\times\mathbf{c})|$. Ba véc-tơ **đồng phẳng** khi tích này bằng $0$.
- **Mô-men xoắn:**
$$\boldsymbol{\tau}=\mathbf{r}\times\mathbf{F},\qquad |\boldsymbol{\tau}|=|\mathbf{r}||\mathbf{F}|\sin\theta$$

## 1.5. Đường thẳng và mặt phẳng

**Đường thẳng** qua $P_0(x_0,y_0,z_0)$ với véc-tơ chỉ phương $\mathbf{v}=\langle a,b,c\rangle$:
- Phương trình véc-tơ: $\mathbf{r}=\mathbf{r}_0+t\mathbf{v}$
- Phương trình tham số: $x=x_0+at,\ y=y_0+bt,\ z=z_0+ct$
- Phương trình đối xứng (khi $a,b,c\neq0$):
$$\frac{x-x_0}{a}=\frac{y-y_0}{b}=\frac{z-z_0}{c}$$
- Nếu một số chỉ phương bằng $0$ (ví dụ $a=0$) thì viết $x=x_0,\ \dfrac{y-y_0}{b}=\dfrac{z-z_0}{c}$.
- Đường thẳng qua hai điểm: lấy $\mathbf{v}=\mathbf{r}_1-\mathbf{r}_0$. **Đoạn thẳng** là
$$\mathbf{r}(t)=(1-t)\mathbf{r}_0+t\mathbf{r}_1,\quad 0\le t\le1$$
- Phương trình đường thẳng không duy nhất (đổi điểm hoặc véc-tơ chỉ phương).
- **Hai đường thẳng chéo nhau** khi không song song và không cắt nhau (hệ phương trình tham số vô nghiệm).

**Mặt phẳng** qua $P_0$ với véc-tơ pháp tuyến $\mathbf{n}=\langle a,b,c\rangle$:
$$\mathbf{n}\cdot(\mathbf{r}-\mathbf{r}_0)=0\iff a(x-x_0)+b(y-y_0)+c(z-z_0)=0\iff ax+by+cz+d=0$$
- Mặt phẳng qua 3 điểm $P,Q,R$: lấy $\mathbf{n}=\overrightarrow{PQ}\times\overrightarrow{PR}$.
- **Giao điểm đường thẳng và mặt phẳng:** thay phương trình tham số vào phương trình mặt phẳng, giải $t$.
- **Hai mặt phẳng:** song song khi $\mathbf{n}_1\parallel\mathbf{n}_2$. Nếu không song song thì góc giữa chúng là góc nhọn giữa hai pháp tuyến:
$$\cos\theta=\frac{|\mathbf{n}_1\cdot\mathbf{n}_2|}{|\mathbf{n}_1||\mathbf{n}_2|}$$
Giao tuyến có véc-tơ chỉ phương $\mathbf{v}=\mathbf{n}_1\times\mathbf{n}_2$, và cần thêm một điểm chung (ví dụ cho $z=0$).
- **Khoảng cách từ điểm đến mặt phẳng:**
$$D=\frac{|ax_1+by_1+cz_1+d|}{\sqrt{a^2+b^2+c^2}}$$
- **Khoảng cách giữa hai mặt phẳng song song:** lấy một điểm trên mặt này rồi tính khoảng cách đến mặt kia.
- **Khoảng cách giữa hai đường chéo nhau:** đặt chúng lên hai mặt phẳng song song với pháp tuyến $\mathbf{n}=\mathbf{v}_1\times\mathbf{v}_2$, rồi tính khoảng cách giữa hai mặt phẳng đó.

## 1.6. Mặt trụ và mặt bậc hai

- **Vết (mặt cắt ngang):** giao của mặt với các mặt phẳng song song mặt tọa độ. Vẽ mặt bằng cách khảo sát các vết.
- **Mặt trụ:** phương trình thiếu một trong các biến $x,y,z$. Ví dụ $z=x^2$ là trụ parabol với đường sinh song song trục $y$; $x^2+y^2=1$ là trụ tròn.
- **Mặt bậc hai:** phương trình bậc hai theo $x,y,z$. Bằng tịnh tiến và quay, đưa về dạng chuẩn $Ax^2+By^2+Cz^2+J=0$ hoặc $Ax^2+By^2+Iz=0$.

Sáu dạng chuẩn cơ bản (bảng ở slide 169 là hình ảnh, các dạng dưới đây là dạng chuẩn thường dùng):

| Mặt                   | Phương trình chuẩn                                      | Đặc điểm các vết                                   | 
| --------------------- | ------------------------------------------------------- | -------------------------------------------------- | 
| Ellipsoid             | $\dfrac{x^2}{a^2}+\dfrac{y^2}{b^2}+\dfrac{z^2}{c^2}=1$  | Mọi vết là ellipse                                 |                                
| Hyperboloid một tầng  | $\dfrac{x^2}{a^2}+\dfrac{y^2}{b^2}-\dfrac{z^2}{c^2}=1$  | Ngang: ellipse; dọc: hyperbol                      |                                 
| Hyperboloid hai tầng  | $-\dfrac{x^2}{a^2}-\dfrac{y^2}{b^2}+\dfrac{z^2}{c^2}=1$ | Ngang ($\lvert z \rvert >c$): ellipse; dọc: hyperbol |
| Elliptic paraboloid   | $\dfrac{z}{c}=\dfrac{x^2}{a^2}+\dfrac{y^2}{b^2}$        | Ngang: ellipse; dọc: parabol                       |                                 
| Hyperbolic paraboloid | $\dfrac{z}{c}=\dfrac{x^2}{a^2}-\dfrac{y^2}{b^2}$        | Ngang: hyperbol; dọc: parabol (mặt yên ngựa)       |                                 
| Mặt nón elliptic      | $\dfrac{z^2}{c^2}=\dfrac{x^2}{a^2}+\dfrac{y^2}{b^2}$    | Ngang: ellipse; dọc: cặp đường thẳng hoặc hyperbol |

Cách nhận dạng: chia hai vế để đưa về dạng chuẩn, hoàn thành bình phương để tìm tâm hoặc đỉnh (Ví dụ 7, 8). Số dấu âm trong phương trình có $=1$ cho biết loại hyperboloid.

**Ứng dụng:** Trái Đất xấp xỉ ellipsoid, chảo vệ tinh và ăng-ten dùng paraboloid, tháp làm mát lò phản ứng dùng hyperboloid một tầng.

---

Bài tập cuối các phần (slide 33, 69, 88, 177) đều giải được bằng các công thức trên. Bạn muốn mình làm tiếp phần nào: giải các bài tập đó, soạn bộ câu hỏi ôn tập, hay gom bản tóm tắt này thành file để lưu?