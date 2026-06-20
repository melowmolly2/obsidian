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
- Công suất tức thời $P$ là giới hạn của biểu thức này khi $\Delta t \to 0$: $$P=F_{II}v\qquad (6.18)$$
	trong đó $v$ là vận tốc tức thời. Chúng ta cũng có thể biển diễn (6.18) dưới dạng tích vô hướng: $$P=\vec F \cdot \vec v\qquad (6.19)$$
## Thế năng trường hấp dẫn
- Giả sử một vật có khối lượng $m$ di chuyển dọc theo trục $y$, lực tác dụng lên vật với độ lớn $w=mg$, và có thể một số lực khác $\vec F_{khác}$. Trong trường hợp này, ta giả thiết vật ở gần mặt đất nên trọng lực là không đổi. Mục tiêu cảu ta là tìm công mà trọng lực thực hiện khi vật di chuyển từ độ cao $y_1$ xuống độ cao thấp hơn $y_2$. 
- Trọng lực và độ dịch chuyển cùng hướng. Vì vậy, công $W_{\text{hấp dẫn}}$ là dương: $$W_{\text{hấp dẫn}}=F\cdot s=w(y_1-y_2)=mgy_1-mgy_2\qquad(7.1)$$
![](../Assets/Pasted%20image%2020260619152433.png)
- Biểu thức cho công khi vật chuyển động lên trên và $y_2$ lớn hơn $y_1$ (Hình 7.2b). Khi đó, đại lượng $y_1-y_2$ là âm, và $W_{\text{hấp dẫn}}$ là âm vì trọng lực và độ dịch chuyển ngược chiều nhau. Phương trình (7.1) biểu diễn $W_{\text{hấp dẫn}}$ theo các giá trị của đại lượng $mgy$ ở đầu và cuối độ dịch chuyển. Đại lượng này được gọi là **thế năng (trường) hấp dẫn)**, $U_{\text{hấp dẫn}}$:
![](../Assets/Pasted%20image%2020260619152629.png)
![](../Assets/Pasted%20image%2020260619152646.png)
- Giá trị ban đầu của nó là $U_{hd}=mgy_1$ và giá trị cuối cùng là $U_{hd}=mgy_2$. Sự thay đổi trong $U_{hd}$ là giá trị cuối cùng trừ đi giá trị ban đầu, hay $\Delta U_{hd}=U_{hd2}-U_{hd1}$. Sử dụng (7.2), chúng ta có thể viết lại (7.1) cho công thực hiện bởi lực hấp dẫn trong quá trình dịch chuyển từ $y_1$ đến $y_2$:$$ W_{hd}=U_{hd1}-U_{hd2}=-U_{hd2}-U_{hd1}=-\Delta U_{hd}\qquad(7.3)$$
	Lưu ý: Khi vật chuyển động lên, $y$ tăng, công do lực hấp dẫn thực hiện là âm, và thế năng tăng ($\Delta U_{hd}>0$). Khi vật chuyển động xuống, $y$ giảm, lực hấp dẫn thực hiện công dương, và thế năng giảm ($\Delta U_{hd}<0$). 
### Bảo toàn cơ năng
- Giả sử trọng lcujw là lực duy nhất tác dụng lên vật, tức là $\vec F_{khác}=0$. Khi đó, vật đang rơi tự do không có sức cản không khí, và có thể đang chuyển động lên hoặc xuống. Gọi tốc độ của nó tại điểm $y_1$ là $v_1$ và tốc độ của nó tại $y_2$ là $v_2$. Theo định lý công - động năng, phương trình (6.6), tổng công thực hiện lên vật bằng sự thay đổi động năng: $$W_{tot}=\Delta K=K_2-K_1$$
	Nếu trọng lực là lực duy nhất tác dụng, thì từ (7.3) ta có: $$W_{tot}=W_{hp}=U_{hd1}-U_{hd2}=-\Delta U_{hd}$$
- Kết hợp các phương trình này, chúng ta có được:![](../Assets/Pasted%20image%2020260619155541.png)
- Tổng của động năng $K+U_{hd}$ được gọi là $E$, tổng cơ năng của hệ. 
- $E=K+U_{hd}=const$ (chỉ đúng khi chỉ có trọng lực thực hiện công)
	**Chú ý: trọng lực hay gọi là lực trọng trường**
- Một đại lượng luôn không đổi gọi là đại lượng bảo toàn. Khi chỉ có lực hấp dẫn thực hiện công, tổng cơ năng là không đổi - tức là nó được bảo toàn (Hình 7.3). Đây là ví dụ đầu tiên của chúng ta về bảo toàn cơ năng. ![](../Assets/Pasted%20image%2020260619155745.png)
	Lưu ý: Khi làm việc với thế năng hấp dẫn, chúng ta có thể chọn mốc thế năng ($y=0$) tại độ cao bất kỳ. Nếu dịch chuyển gốc tọa độ cho $y$, các giá trị của $y_1$ và $y_2$ thay đổi, cũng như các giá trị của $U_{hd1}$ và $U_{hd2}$. Nhưng sự dịch chuyển này không ảnh hưởng đến hiệu số độ cao $y_2-y_1$ hoặc đến hiệu số thế năng hấp dẫn. 
### Các vấn đề sử dụng cơ năng I
- Khi sử dụng phương pháp năng lượng, trước tiên hãy xác định trạng thái ban đầu và trạng thái cuối cùng (vị trí và vận tốc của các vật thể được đề cập.) Sử dụng chỉ số 1 cho trạng thái ban đầu và chỉ số 2 cho trạng thái cuối cùng. Vẽ các phác thảo thể hiện các trạng thái này). 
- Định nghĩa một hệ tọa độ, và chọn mức mà tại đó $y=0$. Chọn chiều dương của trục $y$ hướng lên. 
- Xác định bất kỳ lực nào thực hiện công lên mỗi vật thể và mà không thể được mô tả dưới dạng thế năng. Phác thảo biểu đồ vật thể tự do cho mỗi vật thể.
- Liệt kê các đại lượng đã biết và chưa biết, bao gồm tọa độ và vận tốc tại mỗi điểm. Xác định các biến cần tính toán. 
### Thế năng trọng trường cho chuyển động dọc theo một quỹ đạo cong

--- start-multi-column: ID_sccm
```column-settings
Number of Columns: 2
Largest Column: left
Border: disabled
Shadow: disabled
```
Trong hai ví dụ ở trên, vật thể di chuyển dọc theo một đường thẳng đúng. Điều gì sẽ xảy ra khi quỹ đạo nghiêng hoặc cong (7.7a). Vật thể chịu tác dụng của lực hấp dẫn $\vec w = m\vec g$ và có thể cả các lực khác mà tổng hợp lực của chúng ta gọi là $\vec F_{khác}$. 


--- column-end ---

![](../Assets/Pasted%20image%2020260620102445.png)
--- end-multi-column
- Để tìm công $W_{hd}$ thực hiển bởi lực hấp dẫn trong quá trình dịch chuyển này, chúng ta chia quỹ đạo thành các đoạn nhỏ $\Delta \vec s$. Công thực hiện bởi lực hấp  dẫn trên đoạn này là tích vô hướng của lực và độ dịch chuyển. Theo các vecto đơn vị, lực là $\vec W=m\vec g = -mg\hat j$ và độ dịch chuyển là $\Delta s=\Delta x\hat i +\Delta y \hat j$ $-mg\hat j\cdot (\Delta x\hat i+\Delta y\hat j)=-mg\Delta y$$   

