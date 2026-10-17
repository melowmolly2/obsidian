# Bài tập tiêu biểu tuần 9 (Chương 12)

Mình chọn 5 bài đại diện cho 5 dạng chính: sóng trong vật liệu (Bài 1), cường độ từ nguồn điểm (Bài 3), thông số Mặt Trời (Bài 5), sóng dừng trong lò vi sóng (Bài 8), vệ tinh và tấm thu (Bài 9). Bài 10 (sóng trong dây dẫn) đã có ở phần lý thuyết.

## Bài 1: Sóng trong vật liệu từ cách điện

Cho $K=3{,}64$, $K_m=5{,}18$, $f=65{,}0$ Hz, $E_{max}=7{,}20\times10^{-3}$ V/m.

**(a)** Tốc độ sóng:  
$$v=\frac{c}{\sqrt{KK_m}}=\frac{3{,}00\times10^{8}}{\sqrt{3{,}64\cdot5{,}18}}\approx 6{,}91\times10^{7}\ \text{m/s}$$

**(b)** Bước sóng:  
$$\lambda=\frac{v}{f}=\frac{6{,}91\times10^{7}}{65{,}0}\approx 1{,}06\times10^{6}\ \text{m}$$

**(c)** Biên độ từ trường:  
$$B_{max}=\frac{E_{max}}{v}=\frac{7{,}20\times10^{-3}}{6{,}91\times10^{7}}\approx 1{,}04\times10^{-10}\ \text{T}$$

## Bài 3: Bóng đèn sợi đốt 75 W

Công suất ánh sáng nhìn thấy: $P_{vis}=0{,}05\cdot75=3{,}75$ W. Bán kính bóng $R=3{,}0\times10^{-2}$ m.

**(a)** Cường độ ánh sáng ở bề mặt:  
$$I=\frac{P_{vis}}{4\pi R^2}=\frac{3{,}75}{4\pi(3{,}0\times10^{-2})^2}\approx 3{,}3\times10^{2}\ \text{W/m}^2$$

**(b)** Biên độ trường:  
$$E_{max}=\sqrt{2\mu_0cI}=\sqrt{2(4\pi\times10^{-7})(3{,}00\times10^{8})(331{,}6)}\approx 5{,}0\times10^{2}\ \text{V/m}$$  
$$B_{max}=\frac{E_{max}}{c}\approx 1{,}7\times10^{-6}\ \text{T}$$

## Bài 5: Mặt Trời

Cho $I=1400$ W/m², khoảng cách $r=1{,}5\times10^{11}$ m.

**(a)**  
$$E_{max}=\sqrt{2\mu_0cI}=\sqrt{2(4\pi\times10^{-7})(3{,}00\times10^{8})(1400)}\approx 1{,}03\times10^{3}\ \text{V/m}$$  
$$B_{max}=\frac{E_{max}}{c}\approx 3{,}4\times10^{-6}\ \text{T}$$

**(b)** Tổng công suất:  
$$P=4\pi r^2I=4\pi(1{,}5\times10^{11})^2(1400)\approx 4{,}0\times10^{26}\ \text{W}$$

## Bài 8: Lò vi sóng

Cho $\lambda=12{,}2$ cm.

**(a)** Với $n=5$ mặt phẳng bụng:  
$$L=n\frac{\lambda}{2}=5\cdot\frac{12{,}2}{2}=30{,}5\ \text{cm}$$

**(b)** Tần số:  
$$f=\frac{c}{\lambda}=\frac{3{,}00\times10^{8}}{0{,}122}\approx 2{,}46\times10^{9}\ \text{Hz}$$

**(c)** Lò dài thêm: $L'=30{,}5+5{,}0=35{,}5$ cm, vẫn $n=5$:  
$$\lambda'=\frac{2L'}{n}=\frac{2(35{,}5)}{5}=14{,}2\ \text{cm}$$  
$$f'=\frac{c}{\lambda'}=\frac{3{,}00\times10^{8}}{0{,}142}\approx 2{,}11\times10^{9}\ \text{Hz}$$

## Bài 9: Vệ tinh phát sóng

Cho $P=250$ kW, $r=575$ km, $f=92{,}4$ MHz.

**(a)** Cường độ sóng:  
$$I=\frac{P}{4\pi r^2}=\frac{2{,}5\times10^{5}}{4\pi(5{,}75\times10^{5})^2}\approx 6{,}02\times10^{-8}\ \text{W/m}^2$$

**(b)** Biên độ trường:  
$$E_{max}=\sqrt{2\mu_0cI}\approx 6{,}74\times10^{-3}\ \text{V/m},\qquad B_{max}=\frac{E_{max}}{c}\approx 2{,}25\times10^{-11}\ \text{T}$$

**(c)** Công suất thu được, với $A=15{,}0\times0{,}400=6{,}00\ \text{m}^2$:  
$$P_{thu}=IA=(6{,}02\times10^{-8})(6{,}00)\approx 3{,}6\times10^{-7}\ \text{W}$$  
Cách tính này đủ cho sóng truyền mở rộng, vì tấm thu rất nhỏ so với khoảng cách $575$ km nên mặt sóng tại đó gần như phẳng và $I$ coi như đều trên tấm.

## Các bước chung cho dạng bài này

1. Đổi hết về đơn vị SI.
2. Tìm $I$ (từ $P/4\pi r^2$ hoặc từ đề cho).
3. Tìm $E_{max}=\sqrt{2\mu_0cI}$, rồi $B_{max}=E_{max}/c$.
4. Công suất qua diện tích vuông góc: $P=IA$.

Nếu muốn, mình giải tiếp các bài còn lại (2, 4, 6, 7) hoặc làm chi tiết Bài 10.