# Tóm tắt lý thuyết Chương 3 (phần 2): Đạo hàm riêng

## 1. Đạo hàm riêng

**Định nghĩa.** Cho $f(x,y)$. Cố định $y=b$, đặt $g(x)=f(x,b)$. Khi đó

$$f_x(a,b)=g'(a)=\lim_{h\to 0}\frac{f(a+h,b)-f(a,b)}{h}$$

$$f_y(a,b)=\lim_{h\to 0}\frac{f(a,b+h)-f(a,b)}{h}$$

**Ký hiệu:** $f_x=\dfrac{\partial f}{\partial x}=\dfrac{\partial z}{\partial x}=f_1=D_xf$, và tương tự cho $f_y$.

**Cách tính:** để tìm $f_x$, coi $y$ là hằng số rồi lấy đạo hàm theo $x$. Với $f_y$ thì ngược lại.

**Hàm $n$ biến** $u=f(x_1,\dots,x_n)$:

$$\frac{\partial u}{\partial x_i}=\lim_{h\to0}\frac{f(x_1,\dots,x_i+h,\dots,x_n)-f(x_1,\dots,x_n)}{h}$$

Khi tính theo biến thứ $i$, coi mọi biến còn lại là hằng số.

**Ý nghĩa hình học.** Cắt mặt $S: z=f(x,y)$ bằng mặt phẳng $y=b$ được đường cong $C_1$, và bằng mặt phẳng $x=a$ được đường cong $C_2$. Khi đó $f_x(a,b)$ và $f_y(a,b)$ lần lượt là hệ số góc của tiếp tuyến với $C_1$ và $C_2$ tại $P(a,b,c)$.

## 2. Đạo hàm riêng của hàm ẩn

Với hàm ẩn $z=z(x,y)$ cho bởi $F(x,y,z)=0$, ta lấy đạo hàm hai vế theo $x$ (coi $y$ là hằng số, $z$ phụ thuộc $x$), rồi giải ra $\dfrac{\partial z}{\partial x}$. Với $x^3+y^3+z^3+6xyz=1$:

$$\frac{\partial z}{\partial x}=-\frac{x^2+2yz}{z^2+2xy},\qquad \frac{\partial z}{\partial y}=-\frac{y^2+2xz}{z^2+2xy}$$

## 3. Đạo hàm riêng cấp cao

$$f_{xx}=\frac{\partial^2 f}{\partial x^2},\quad f_{xy}=(f_x)_y=\frac{\partial^2 f}{\partial y\,\partial x},\quad f_{yx}=(f_y)_x=\frac{\partial^2 f}{\partial x\,\partial y},\quad f_{yy}=\frac{\partial^2 f}{\partial y^2}$$

Ký hiệu $f_{xy}$ nghĩa là lấy đạo hàm theo $x$ trước, rồi theo $y$.

**Định lý Clairaut.** Nếu $f_{xy}$ và $f_{yx}$ cùng liên tục trên miền $D$ chứa $(a,b)$ thì

$$f_{xy}(a,b)=f_{yx}(a,b)$$

## 4. Một số phương trình đạo hàm riêng

- **Phương trình Laplace:** $\dfrac{\partial^2 u}{\partial x^2}+\dfrac{\partial^2 u}{\partial y^2}=0$. Nghiệm của nó gọi là hàm điều hòa, ví dụ $u=e^x\sin y$.
- **Phương trình sóng:** $\dfrac{\partial^2 u}{\partial t^2}=a^2\dfrac{\partial^2 u}{\partial x^2}$. Ví dụ $u=\sin(x-at)$ thỏa mãn phương trình này.

## 5. Mặt phẳng tiếp xúc

Nếu $f$ có các đạo hàm riêng liên tục thì mặt phẳng tiếp xúc với $z=f(x,y)$ tại $P(x_0,y_0,z_0)$ là

$$z-z_0=f_x(x_0,y_0)(x-x_0)+f_y(x_0,y_0)(y-y_0)$$

Cách suy ra: mặt phẳng có dạng $z-z_0=a(x-x_0)+b(y-y_0)$. Giao của nó với $y=y_0$ phải là tiếp tuyến $T_1$ nên $a=f_x(x_0,y_0)$. Giao với $x=x_0$ là tiếp tuyến $T_2$ nên $b=f_y(x_0,y_0)$.

**Ví dụ:** với $z=2x^2+y^2$ tại $P(1,1,3)$, ta có $f_x=4x$, $f_y=2y$, suy ra mặt phẳng tiếp xúc là $z=4x+2y-3$.

## 6. Xấp xỉ tuyến tính

**Hàm tuyến tính hóa** của $f$ tại $(x_0,y_0)$:

$$L(x,y)=f(x_0,y_0)+f_x(x_0,y_0)(x-x_0)+f_y(x_0,y_0)(y-y_0)$$

Khi $(x,y)$ gần $(x_0,y_0)$ thì $f(x,y)\approx L(x,y)$. Ví dụ với $f=2x^2+y^2$ tại $(1,1)$:

- $f(1.1,\,0.95)=3.3225$ và $L(1.1,\,0.95)=3.3$, rất gần nhau.
- $f(2,3)=17$ nhưng $L(2,3)=11$, sai lệch lớn vì điểm này xa $(1,1)$.

## 7. Tính khả vi

**Số gia:** $\Delta z=f(a+\Delta x,\,b+\Delta y)-f(a,b)$.

**Định nghĩa.** $f$ khả vi tại $(a,b)$ nếu

$$\Delta z=f_x(a,b)\,\Delta x+f_y(a,b)\,\Delta y+\varepsilon_1\Delta x+\varepsilon_2\Delta y$$

với $\varepsilon_1,\varepsilon_2\to0$ khi $(\Delta x,\Delta y)\to(0,0)$.

**Định lý (điều kiện đủ).** Nếu $f_x,f_y$ tồn tại trong một lân cận của $(a,b)$ và liên tục tại $(a,b)$ thì $f$ khả vi tại $(a,b)$.

## 8. Vi phân

- **Hàm 1 biến:** $dy=f'(x)\,dx$. Ở đây $dy$ là độ biến thiên của tiếp tuyến, còn $\Delta y$ là độ biến thiên của đường cong.
- **Hàm 2 biến (vi phân toàn phần):**

$$dz=f_x(x,y)\,dx+f_y(x,y)\,dy=\frac{\partial f}{\partial x}dx+\frac{\partial f}{\partial y}dy$$

  Khi $dx=\Delta x$, $dy=\Delta y$ thì $dz$ là độ biến thiên của mặt phẳng tiếp xúc, còn $\Delta z$ là độ biến thiên của mặt cong. Do đó $\Delta z\approx dz$ và $f(x,y)\approx f(a,b)+dz$.
- **Hàm $n$ biến:** $du=f_{x_1}dx_1+\dots+f_{x_n}dx_n$. Hàm khả vi nếu các đạo hàm riêng liên tục tại điểm đó.

**Ứng dụng ước lượng sai số (Ví dụ 4.4).** Hình hộp có các cạnh $75, 60, 40$ cm, mỗi số đo sai số tối đa $0.2$ cm. Với $V=xyz$:

$$dV=yz\,dx+xz\,dy+xy\,dz=60\cdot40\cdot0.2+75\cdot40\cdot0.2+75\cdot60\cdot0.2=1980\ \text{cm}^3$$

Sai số này chỉ chiếm khoảng $1\%$ so với $V=180000\ \text{cm}^3$.

## Một số lỗi đánh máy trong slide

- Slide 3, công thức (3.4): thừa một chữ $\lim$.
- Slide 10, Ví dụ 3.3: phải là $\dfrac{\partial z}{\partial x},\dfrac{\partial z}{\partial y}$, và ở vế thứ hai phải lấy đạo hàm theo $y$.
- Slide 30: $\Delta y=f'(a)\,\Delta x+\varepsilon\Delta x$ (slide ghi $(x-a)$, tương đương vì $\Delta x=x-a$ nhưng nên thống nhất ký hiệu).
- Slide 37, công thức (4.7): số hạng cuối của tổng đạo hàm phải là $(x_n-a_n)$, không phải $(x_n-a_1)$.
- Slide 39: phải là $\dfrac{\partial V}{\partial x}$ (slide ghi $\partial f$), và số hạng thứ ba là $75\times60\times0.2$. Kết quả $1980$ vẫn đúng.

Bạn muốn mình giải thêm bài tập hay làm bộ câu hỏi ôn tập cho chương này không?