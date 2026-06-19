## Công
- Công là một đại lượng vô hướng
- Dương, âm hoặc bằng 0
- Để tìm tổng công thực hiện lên một vật thể đang chuyển động, hãy tính tổng các lượng công được thực hiện bởi mỗi lực tác dụng lên vật. Tổng công cũng bằng công do hợp lực thực hiện lên vật. 
---
## Động năng và định lý Công - Động năng
- Ý nghĩa:
	- Động năng của một vật có tốc độ $v$ bằng công đã thực hiện để tăng tốc nó từ trạng thái nghỉ đến tốc độ $v$. 
	$$ k = \frac 12 mv^2$$
---

	
- Chúng ta chỉ áp dụng định lý công - động năng cho vật coi là chất điểm (nghĩa là vật nhỏ, chuyển động đơn giản, không quay, và không biến dạng).
- Với các hệ phức tạp hơn (vật lớn, vật quay, hoặc hệ nhiều vật liên kết), thì sẽ xuất hiện những vấn đề sau:
	- Mỗi phần của vật có thể chuyển động khác nhau
	- Vật có thể vừa trượt vừa quay
	- Có thể có lực tác dụng giữa các phần tử bên trong hệ
---

- Khi đó, ta cần phân tích kỹ từng phần, hoặc chia nhỏ vật thành nhiều chất điểm để áp dụng định lý. 

## Công và động năng khi lực thay đổi
- Hình (a) trình bày chuyển động thẳng của một vật theo trục $x$ chịu tác dụng của lực $F_x$ thay đổi khi chuyển động. Giả sử vật chuyển từ điểm $x_1$ đến $x_2$, (b) là đồ thị của thành phần $x$ của lực theo hướng $x$. Công do lực thực hiện khi dịch chuyển từ $x_1$ sang $x_2$ xấp xỉ bằng: $W=F_{ax} \Delta x_a + F_{bx}\Delta x_b +\cdots$(xem hình c). 
![](../Assets/Pasted%20image%2020260618211942.png)
- Khi số đoạn rất lớn và chiều rộng của mỗi đoạn rất nhỏ, tổng này trở thành tích phân của $F_x$ từ $x_1$ đến $x_2$ như dưới đây:
![](../Assets/Pasted%20image%2020260618212047.png)
- Trường hợp đặc biệt khi $F_x$ là không thay đổi, chúng ta có thể đưa nó ra ngoài dấu tích phân như sau:
$$ W=\int_{x_1}^{x_2} F_x dx = F_x \int_{x_1}^{x_2}dx=F_x(x_2-x_1)$$
- Đặt $s=x_2-x_1$ là tổng độ dịch chuyển của vật. Như vậy, khi lực không đổi $F,$(6.7) trở thành $W=Fs$. 
- $\rightarrow$ Công là diện tích dưới đường cong của $F_x$ là một hàm của $x$. 
- Khi kéo dãn lò xo vượt quá chiều dài tự nhiên của nó một lượng $x$, ta càn tác dụng một lực có cùng độ lớn ở mỗi đầu (6.18). Nếu độ giãn $x$ nhỏ, lực tác dụng vào đầu bên phải là: $$F_x = kx \qquad (6.8)$$![](../Assets/Pasted%20image%2020260618212428.png)
- Để kéo dãn một lò xo, ta phải thực hiện công. Nghĩa là, ta cần tác dụng lực ngược chiều vào hai đầu của lò xo. 
- Nếu giữ đầu bên trái cố định (lực chúng ta tác dụng vào đầu này không thực hiện công), thì lực ở đầu kia di chuyển từ 0 đến cực đại thực hiện công: $$W=\int_0^{X} F_x dx = \int_0^X kxdx = \frac 12 kX^2 \qquad (6.9)$$
- Phương trình (6.9) giả thiết rằng lò xo ban đầu không bị kéo giãn. Nếu ban đầu lò xo đã được kéo giãn một khoảng cách $x_1$, thì công thực hiện để kéo giãn nó đến một khoảng lớn hơn $x_2$ (6.20a) là: $$W=\int_{x_1}^{x_2}F_xdx=\int_{x_1}^{x_2}kxdx=\frac 12 kx_2^2-\frac12kx_1^2\qquad (6.10)$$
 ![](../Assets/Pasted%20image%2020260618212753.png)
### Định lý công - năng lượng cho chuyển động thẳng, lực biến đổi
Đây là một cách phát biểu khác của định lý công - năng lượng khi một lực biến đổi theo vị trí. Lưu ý rằng, gia tốc $a$ của hạt có thể dược biểu diễn theo nhiều cách khác nhau, sử dụng $a_x= \frac{dv_x}{dt}$, $v_x=\frac{dx}{dt}$ và quy tắc chuỗi cho đạo hàm:$$a_x=\frac{dv_x}{dt}=\frac{dv_x}{dx},\, \frac{dx}{dt}=v_x\frac{dv_x}{dx}\qquad (6.11)$$
- Từ kết quả (6.7), tổng công thực hiện bởi lực $F_x$ là:
$$W_{tot}=\int_{x_1}^{x_2}F_xdx=\int_{x_1}^{x_2}ma_xdx=\int_{x_1}^{x_2}mv_x\frac{dv_x}{dx}dx\qquad (6.12)$$
- Bây giờ $\frac{dv_x}{dx}dx$ là sự thay đổi vật tốc $dv_x$ trong quá trì dịch chuyển $dx$, chúng ta có thể sử dụng (6.12). Điều này thay đổi biến tích phân từ $x$ sang $v_x$, nghĩa là chúng ta thay đổi các giới hạn từ $x_1$ và $x_2$ thành các vận tốc tương ứng $v_1$ và $v_2$: $$W_{tot}=\int_{v_1}^{v_2}mv_xdv_x$$
- Nguyên hàm của $v_xdv_x$ đơn giản là $\frac{v_x}2$. Thay các cận trên và dưới, chúng ta tìm được: $$W_{tot}=\frac 12 mv_2^2-\frac 12 mv_1^2\qquad (6.13)$$
	Đây là phương trình giống như phương trình (6.6). 
	$\rightarrow$ Vì vậy định lý công - động năng vẫn đúng ngay cả khi không có giả định là tổng hợp lực bằng không. 
### Định lý công - động năng cho chuyển động dọc theo một đường cong

--- start-multi-column: ID_pt3y
```column-settings
Number of Columns: 2
Largest Column: left
Border: disabled
Shadow: disabled
```

- HÌnh 6.23a cho thấy một vật chuyển động từ $P_1$ đến $P_2$ dọc theo một đường cong. Gọi $\vec F$ là lực tại một điểm điển hình dọc theo quỹ đạo, và gọi $\phi$ là góc giữa $\vec F$ và $d\vec l$ tại điểm này. Khi đó, yếu dố công nhỏ $dW$ thực hiện lên hạt trong quá trình dịch chuyển $d\vec l$ có thể được viết là: $$dW = \vec F \cdot d\vec l = F \cos \theta dl = F_{II}dl$$
- Trong đó $F_{II}=F\cos \phi$ là thành phần của $\vec F$ theo phương song song với $d\vec l$ (Hình 6.23b). Công do $\vec F$ thực hiện để hạt di chuyển từ $P_1$ đến $P_2$ là: $$W=\int_{P_1}^{P_2}\vec F\cdot d\vec l=\int_{P_1}^{P_2}F\cos \theta dl = \int_{P_1}^{P_2}F_{II}dl\qquad (6.14)$$
- Tích phân 14 được gọi là tích phân đường. 

--- end-column --- 

![](../Assets/Pasted%20image%2020260618215351.png)



--- multi-column-end
<u>Lưu ý: </u> Chỉ có thành phần của hợp lực tịnh tiến song song với quỹ đạo, $F_{II}$ mới sinh công lên vật. Do đó, chỉ thành phần này mới có thể làm thay đổi tốc độ và động năng của hạt Thành phần vuông góc với quỹ đạo, $F_{\perp}=F\sin \phi$ , không làm thay đổi tốc độ, nó chỉ tác dụng để thay đổi hướng chuyển động của vật. 
## Công suất
- Công suất là tốc độ biến thiên của công theo thời gian. Tương tự như công và động năng, công suất là một đại lượng vô hướng
- Công thực hiện trung bình trên một đơn vị thời gian, hay công suất trung bình $P_{tb}$ được định nghĩa là: $$P_{tb}=\frac{\Delta W}{\Delta t} \qquad (6.15)$$
- Tốc độ thực hiện công có thể không phải là hằng số. Chúng ta định nghĩa công suất tức thời $P$ là tỉ số trong (6.15) khi $\Delta t$ tiến đến không: $$P=\lim_{\Delta t \to 0}\frac{\Delta w}{\Delta t}=\frac{dW}{dt}$$
- Đơn vị SI của công suất là watt (W). Một watt bằng 1 joule trên giây: 1W=1J/s. Kilowatt ($1kW=10^3 W$) và megawatt ($1MW=10^6W$) cũng là nhứng đơn vị thường được sử dụng. 
- Chúng ta cũng có thể biểu diễn công suất theo lực và vận tốc. Giả sử một lực $\vec F$ tác dụng lên một vật khi nó trải qua một dịch chuyển vector $\Delta \vec s$. Nếu $F_{II}$ là thành phần của $\vec F$ tiếp tuyến với quỹ đạo, thì công thực hiện bởi lực là $\Delta W = F_{II}\Delta s$. Công suất trung bình là: $$P_{tb}=\frac{F_{II}\Delta s}{\Delta t}=F_{II}\frac{\Delta s}{\Delta t}=F_{II}v_{aV}\qquad (6.17)$$
- Công suất tức thời 
```tikz
\documentclass[tikz, border=10pt]{standalone}
\usepackage{pgfplots}
\usepackage{tikz-cd}
\pgfplotsset{compat=1.18}

\begin{document}

\begin{tikzpicture}
\begin{axis}[
    no markers, 
    domain=-4:4, 
    samples=100,
    axis lines=left, 
    xlabel={$x$}, 
    ylabel={$f(x)$},
    every axis y label/.style={at=(current axis.above origin),anchor=south},
    every axis x label/.style={at=(current axis.right of origin),anchor=west},
    height=6cm, 
    width=10cm,
    xtick={-3,-2,-1,0,1,2,3},
    xticklabels={$-3\sigma$, $-2\sigma$, $-\sigma$, $\mu$, $\sigma$, $2\sigma$, $3\sigma$},
    ytick=\empty,
    enlargelimits=false, 
    clip=false, 
    axis on top,
    grid = none
]

    % Shaded area for -1 to 1 standard deviation
    \addplot [fill=cyan!20, draw=none, domain=-1:1] {gauss(x, 0, 1)} \closedcycle;

    % The standard normal distribution curve
    \addplot [very thick, cyan!80!black] {gauss(x, 0, 1)};

    % Optional: Add a label for the mean
    \draw [dashed, gray] (axis cs:0,0) -- (axis cs:0,0.4);

\end{axis}
\end{tikzpicture}

\end{document}
```
```tikz
\usepackage{tikz-cd}
\begin{document}
\begin{tikzcd}
A \arrow[r] \arrow[d] & B \arrow[d] \\
C \arrow[r] & D
\end{tikzcd}
\end{document}   
```

```tikz
\begin{document}
  \begin{tikzpicture}[domain=0:4]
    \draw[very thin,color=gray] (-0.1,-1.1) grid (3.9,3.9);
    \draw[->] (-0.2,0) -- (4.2,0) node[right] {$x$};
    \draw[->] (0,-1.2) -- (0,4.2) node[above] {$f(x)$};
    \draw[color=red]    plot (\x,\x)             node[right] {$f(x) =x$};
    \draw[color=blue]   plot (\x,{sin(\x r)})    node[right] {$f(x) = \sin x$};
    \draw[color=orange] plot (\x,{0.05*exp(\x)}) node[right] {$f(x) = \frac{1}{20} \mathrm e^x$};
  \end{tikzpicture}
\end{document}
```


```tikz
\usepackage{circuitikz}
\begin{document}

\begin{circuitikz}[american, voltage shift=0.5]
\draw (0,0)
to[isource, l=$I_0$, v=$V_0$] (0,3)
to[short, -*, i=$I_0$] (2,3)
to[R=$R_1$, i>_=$i_1$] (2,0) -- (0,0);
\draw (2,3) -- (4,3)
to[R=$R_2$, i>_=$i_2$]
(4,0) to[short, -*] (2,0);
\end{circuitikz}

\end{document}
```

```tikz
\usepackage{pgfplots}
\pgfplotsset{compat=1.16}

\begin{document}

\begin{tikzpicture}
\begin{axis}[colormap/viridis]
\addplot3[
	surf,
	samples=18,
	domain=-3:3
]
{exp(-x^2-y^2)*x};
\end{axis}
\end{tikzpicture}

\end{document}
```
