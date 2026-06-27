# Tuần 1
- **Dạng 1: Phương trình chuyển động 1 chiều (Gia tốc thay đổi).** Một chiếc xe di chuyển trên đường thẳng với phương trình vị trí $x(t) = \alpha t^2 - \beta t^3$ (với $\alpha = 1,50 \text{ m/s}^2$ và $\beta = 0,0500 \text{ m/s}^3$). Yêu cầu tính vận tốc trung bình của chiếc xe trong các khoảng thời gian cụ thể.
- **Dạng 2: Rơi tự do / Ném thẳng đứng.** Một viên đá được ném thẳng đứng lên trên với vận tốc $22,0 \text{ m/s}$ từ mép một tòa nhà cao $30,0 \text{ m}$. Bỏ qua lực cản không khí, yêu cầu tính vận tốc của viên đá ngay trước khi chạm đất và tổng thời gian rơi.
- **Dạng 3: Chuyển động ném.** Một quả bóng được ném lên từ mép mái một tòa nhà cao $20,0 \text{ m}$ và rơi xuống chạm đất. Bài toán yêu cầu phân tích quỹ đạo, tìm giới hạn của vận tốc ban đầu và tính toán các đặc điểm của vận tốc khi chạm đất.
- **Dạng 4: Vận tốc tương đối.** Một phi công lái máy bay theo hướng Tây với vận tốc $220 \text{ km/h}$ so với không khí. Lực gió tác động khiến máy bay đi chệch hướng. Yêu cầu tính toán vận tốc của máy bay so với mặt đất và phân tích hướng gió.

**Bài 1 (Phương trình chuyển động - Bài 2.6):** Phương trình vị trí của chiếc xe là $x(t) = 1,50t^2 - 0,0500t^3$. Vận tốc trung bình được tính bằng công thức $v_{av} = \frac{\Delta x}{\Delta t}$.

- **Khoảng $t = 0$ đến $t = 2,00$ s:** $x(2) = 1,50(2^2) - 0,0500(2^3) = 5,6$ m. Vận tốc $v_{av} = \frac{5,6 - 0}{2} = 2,8$ m/s.
- **Khoảng $t = 0$ đến $t = 4,00$ s:** $x(4) = 1,50(4^2) - 0,0500(4^3) = 20,8$ m. Vận tốc $v_{av} = \frac{20,8 - 0}{4} = 5,2$ m/s.
- **Khoảng $t = 2,00$ đến $t = 4,00$ s:** Vận tốc $v_{av} = \frac{20,8 - 5,6}{4 - 2} = 7,6$ m/s.
**Bài 2 (Ném thẳng đứng - Bài 2.36):** Viên đá được ném lên từ độ cao $y_0 = 30,0$ m với vận tốc $v_0 = 22,0$ m/s. Chọn mặt đất làm gốc tọa độ ($y=0$) và chiều dương hướng lên, ta có gia tốc $a = -9,8$ m/s².
- **Vận tốc khi chạm đất:** Dùng công thức $v^2 = v_0^2 + 2a(y - y_0)$, ta có $v^2 = 22,0^2 + 2(-9,8)(0 - 30,0) = 1072$. Suy ra $v = -\sqrt{1072} \approx -32,7$ m/s (dấu âm vì đá đang rơi xuống hướng về đất).
- **Thời gian rơi:** Từ $v = v_0 + at$, ta có $-32,7 = 22,0 - 9,8t$, suy ra thời gian rơi $t \approx 5,58$ s.
**Bài 3 (Hai quả bóng ném - Bài 2.89):** Tòa nhà cao $h = 20,0$ m. Quả bóng thứ 2 (được thả rơi tự do) sẽ chạm đất sau thời gian $t_2 = \sqrt{\frac{2h}{g}} = \sqrt{\frac{40}{9,8}} \approx 2,02$ s.
- Vì bóng 1 được ném trước 1 giây và cả hai chạm đất cùng lúc, nên thời gian bay của bóng 1 là $t_1 = 2,02 + 1 = 3,02$ s.
- Dùng phương trình vị trí $y = y_0 + v_{01}t_1 - \frac{1}{2}gt_1^2 = 0$. Thế số: $20 + v_{01}(3,02) - 4,9(3,02)^2 = 0$. Giải phương trình ta được vận tốc ném ban đầu của bóng 1 là $v_{01} \approx 8,18$ m/s.
**Bài 4 (Vận tốc tương đối máy bay - Bài 3.71):** Máy bay bay theo hướng Tây (chiều âm trục x) với vận tốc so với không khí là $v_{m/k, x} = -220$ km/h. Sau 0,5 giờ, vị trí thực tế so với mặt đất là $x = -120$ km (Tây) và $y = -20$ km (Nam).
- **Vận tốc thực tế so với đất:** $v_{dx} = -120 / 0,5 = -240$ km/h và $v_{dy} = -20 / 0,5 = -40$ km/h.
- **Phân tích vận tốc gió:** Áp dụng cộng véctơ $\vec{v}_{\text{gió}} = \vec{v}_{\text{thực tế}} - \vec{v}_{m/k}$. Thành phần vận tốc gió là $v_{gx} = -240 - (-220) = -20$ km/h và $v_{gy} = -40 - 0 = -40$ km/h.
- **Kết quả:** Độ lớn vận tốc gió là $v_g = \sqrt{(-20)^2 + (-40)^2} \approx 44,7$ km/h, thổi theo hướng Tây Nam.
# Tuần 2 

1. **Dạng 1: Định luật II Newton kết hợp động học.** Một electron (khối lượng $9,11 \times 10^{-31}$ kg) bắt đầu chuyển động từ trạng thái nghỉ và tăng tốc đều đặn trên một đường thẳng, đạt vận tốc $3,00 \times 10^6$ m/s trong quãng đường 1,80 cm. Yêu cầu tính thời gian chuyển động và lực tác dụng lên electron.
2. **Dạng 2: Bài toán có lực ma sát.** Một người trượt băng nặng 68,5 kg đang trượt với vận tốc 2,40 m/s trên băng ngang thì trượt chậm dần và dừng lại trong 3,52 s. Yêu cầu tính lực ma sát đã tác dụng lên người trượt băng.
3. **Dạng 3: Lực trong thang máy (Trọng lượng biểu kiến).** Lực pháp tuyến hướng lên do sàn thang máy tác dụng lên một hành khách là 620 N, trong khi trọng lượng thực của người này là 650 N. Cần xác định xem hành khách đang chuyển động theo hướng nào (lên hay xuống) và tính gia tốc.
4. **Dạng 4: Hệ vật trên mặt phẳng nghiêng.** Hai khối nặng 100 kg và 50 kg được nối với nhau bằng một sợi dây vắt qua ròng rọc, nằm trên hai mặt phẳng nghiêng không ma sát với góc nghiêng lần lượt là $30,0^\circ$ và $53,1^\circ$. Yêu cầu xác định hướng chuyển động của hệ, tính gia tốc các khối và lực căng dây.

Bạn muốn thử sức vẽ giản đồ lực cho bài nào trước, hay muốn tôi tiếp tục cung cấp hướng dẫn giải chi tiết 4 bước cho các dạng bài này?

Dưới đây là lời giải chi tiết cho 4 bài tập tiêu biểu của Tuần 2:

**Bài 1: Gia tốc của electron (Bài 4.6)**

- **Dữ kiện:** $s = 1,80 \text{ cm} = 0,018 \text{ m}$; vận tốc ban đầu $v_0 = 0$; vận tốc cuối $v = 3,00 \times 10^6 \text{ m/s}$; khối lượng $m = 9,11 \times 10^{-31} \text{ kg}$.
- **Tính gia tốc ($a$):** Sử dụng hệ thức độc lập thời gian $v^2 = v_0^2 + 2as \Rightarrow a = \frac{v^2}{2s} = \frac{(3 \times 10^6)^2}{2 \times 0,018} = 2,50 \times 10^{14} \text{ m/s}^2$.
- **Tính thời gian ($t$):** Dùng công thức $v = v_0 + at \Rightarrow t = \frac{v}{a} = \frac{3 \times 10^6}{2,50 \times 10^{14}} = 1,20 \times 10^{-8} \text{ s}$.
- **Tính lực ($F$):** Áp dụng định luật II Newton $F = ma = 9,11 \times 10^{-31} \times 2,50 \times 10^{14} = 2,28 \times 10^{-16} \text{ N}$.

**Bài 2: Người trượt băng (Bài 4.7)**

- **Dữ kiện:** Khối lượng $m = 68,5 \text{ kg}$, vận tốc đầu $v_0 = 2,40 \text{ m/s}$, vận tốc cuối $v = 0$ (dừng lại), thời gian $t = 3,52 \text{ s}$.
- **Tính gia tốc:** $a = \frac{v - v_0}{t} = \frac{0 - 2,40}{3,52} \approx -0,682 \text{ m/s}^2$.
- **Tính lực ma sát:** Lực duy nhất theo phương ngang là lực ma sát động $f_k$. Áp dụng $\Sigma F_x = ma \Rightarrow f_k = 68,5 \times (-0,682) \approx -46,7 \text{ N}$. Vậy ma sát tác dụng một lực có độ lớn $46,7 \text{ N}$ ngược chiều chuyển động.

**Bài 3: Lực trong thang máy (Bài 4.22)**

- **Dữ kiện:** Trọng lượng $w = 650 \text{ N} \Rightarrow$ khối lượng $m = \frac{w}{g} = \frac{650}{9,8} \approx 66,3 \text{ kg}$. Lực pháp tuyến do sàn đẩy lên là $n = 620 \text{ N}$.
- **Xác định gia tốc:** Chọn chiều dương hướng lên. Áp dụng định luật II Newton: $\Sigma F_y = n - w = ma_y \Rightarrow 620 - 650 = 66,3 \times a_y \Rightarrow a_y \approx -0,45 \text{ m/s}^2$.
- **Kết luận:** Vì gia tốc âm, hành khách đang có gia tốc $0,45 \text{ m/s}^2$ hướng xuống. Điều này nghĩa là thang máy đang tăng tốc đi xuống, hoặc đang chuyển động lên nhưng phanh chậm dần.

**Bài 4: Hệ vật trên mặt phẳng nghiêng (Bài 5.90)**

- **Dữ kiện:** Vật $m_1 = 100 \text{ kg}$ (góc $\alpha = 30^\circ$), vật $m_2 = 50 \text{ kg}$ (góc $\beta = 53,1^\circ$).
- **Xác định hướng:** Thành phần trọng lực kéo trượt vật 1 là $P_1 = m_1g\sin(30^\circ) = 100 \times 9,8 \times 0,5 = 490 \text{ N}$. Đối với vật 2 là $P_2 = m_2g\sin(53,1^\circ) = 50 \times 9,8 \times 0,8 = 392 \text{ N}$. Vì $P_1 > P_2$, hệ sẽ trượt về bên trái (vật 100 kg đi xuống, vật 50 kg bị kéo lên).
- **Tính gia tốc và lực căng ($T$):** Lập hệ phương trình cho 2 vật:
    - Vật 1 (đi xuống): $490 - T = 100a$
    - Vật 2 (đi lên): $T - 392 = 50a$
- Cộng hai phương trình ta được $98 = 150a \Rightarrow a \approx 0,653 \text{ m/s}^2$. Thay $a$ vào phương trình 2 ta tính được lực căng $T = 50 \times 0,653 + 392 \approx 425 \text{ N}$.


```tikz
\begin{tikzpicture}[>=stealth]
  \node[above] at (0, 1) {Part 1: Electron};
  \filldraw (0,0) circle (2pt) node[below] {e-};
  \draw[->, thick, blue] (0,0) -- (2.5,0) node[right] {F};
  \draw[->, thick, green] (0,0.5) -- (1.5,0.5) node[above] {a};
\end{tikzpicture}
```
