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


Dưới đây là một số dạng bài tập trọng tâm tiêu biểu của Tuần 3 về Công và Năng lượng:

- **Dạng 1: Tính công bằng tích vô hướng.** Cho biểu thức véctơ của lực $\vec{F}$ và độ dịch chuyển $\vec{s}$ (ví dụ: $\vec{F} = 30\hat{i} - 40\hat{j}$ và $\vec{s} = -9,0\hat{i} - 3,0\hat{j}$), yêu cầu tính công do lực thực hiện.
- **Dạng 2: Tính công của từng lực trên hệ vật.** Cho một hệ vật chuyển động trên mặt phẳng (có ma sát hoặc vắt qua ròng rọc). Yêu cầu tính công của lực căng dây, trọng lực, lực ma sát, lực pháp tuyến và tổng công thực hiện lên vật.
- **Dạng 3: Áp dụng Định lý Công - Động năng.** Tính vận tốc của một vật (ví dụ: hòn đá ném thẳng đứng với vận tốc ban đầu cho trước) tại một độ cao cụ thể bằng cách sử dụng công của trọng lực và sự biến thiên động năng.
- **Dạng 4: Bảo toàn cơ năng (có và không có ma sát).** Phân tích chuyển động của vật trên quỹ đạo phức tạp như vòng lượn siêu tốc, đoạn dốc, hoặc đệm tuyết để tìm giới hạn độ cao, vận tốc tại một điểm, hoặc xác định hệ số ma sát trượt.



**Bài 1: Tính công bằng tích vô hướng (Bài 6.8)**

- **Dữ kiện:** Lực $\vec{F} = (30\text{ N})\hat{i} - (40\text{ N})\hat{j}$; Độ dịch chuyển $\vec{s} = (-9,0\text{ m})\hat{i} - (3,0\text{ m})\hat{j}$.
- **Giải:**
    - Công được tính bằng tích vô hướng của hai véctơ: $W = \vec{F} \cdot \vec{s} = F_x s_x + F_y s_y$.
    - Thay số: $W = (30)(-9,0) + (-40)(-3,0) = -270 + 120 = -150\text{ J}$.
    - _Ý nghĩa:_ Công âm cho thấy lực cản trở chuyển động của xe.


 **Bài 6.24**:

- **Dữ kiện:** Trọng lượng $w = 3 \text{ N}$ $\Rightarrow m = \frac{w}{g} = \frac{3}{9,8} \approx 0,306 \text{ kg}$. Tại độ cao $y_2 = 15,0 \text{ m}$, vận tốc $v_2 = 25,0 \text{ m/s}$.

**a) Vận tốc ngay khi vừa rời mặt đất ($v_1$ tại $y_1 = 0$):**

- Áp dụng định lý Công - Động năng cho đoạn từ mặt đất lên 15 m: $W_{tot} = K_2 - K_1$.
- Công của trọng lực: $W_{tot} = -w(y_2 - y_1) = -3 \times 15 = -45 \text{ J}$.
- Động năng tại 15 m: $K_2 = \frac{1}{2}mv_2^2 = \frac{1}{2}(0,306)(25^2) \approx 95,6 \text{ J}$.
- Thay vào phương trình: $-45 = 95,6 - K_1 \Rightarrow K_1 = 140,6 \text{ J}$.
- Từ $K_1 = \frac{1}{2}mv_1^2$, ta tính được vận tốc ban đầu: $v_1 = \sqrt{\frac{2 \times 140,6}{0,306}} \approx 30,3 \text{ m/s}$.

**b) Độ cao cực đại ($h_{max}$):**

- Tại độ cao cực đại, vận tốc $v_3 = 0$ nên $K_3 = 0$.
- Áp dụng định lý Công - Động năng từ mặt đất lên đỉnh: $-w \cdot h_{max} = K_3 - K_1$.
- $-3 \cdot h_{max} = 0 - 140,6 \Rightarrow h_{max} \approx 46,9 \text{ m}$.


**Bài 3: Bảo toàn cơ năng - Vòng lượn siêu tốc (Bài 7.42)**

- **Dữ kiện:** Xe trượt không ma sát từ độ cao $h$ vào vòng lượn bán kính $R$.
- **Giải (Tìm $h$ tối thiểu để xe không rơi ở đỉnh vòng):**
    - _Điều kiện động lực học:_ Tại đỉnh vòng (độ cao $2R$), lực hướng tâm là trọng lực và phản lực $\Rightarrow mg + n = m\frac{v^2}{R}$. Để xe không rơi, $n \ge 0 \Rightarrow v_{min}^2 = gR$.
    - _Bảo toàn cơ năng:_ Từ lúc thả ($v=0$) đến đỉnh vòng: $mgh = mg(2R) + \frac{1}{2}mv_{min}^2$.
    - Thay $v_{min}^2 = gR$ vào: $mgh = 2mgR + 0,5mgR = 2,5mgR \Rightarrow h = 2,5R$.

**Bài 4: Năng lượng khi có lực cản/ma sát (Bài 7.54)**

- **Dữ kiện:** Vận động viên $m = 60,0\text{ kg}$ trượt từ dốc cao $h = 65,0\text{ m}$. Công của lực ma sát $W_{khác} = -10,5\text{ kJ} = -10500\text{ J}$.
- **Giải (Tính vận tốc ở chân dốc):**
    - Sử dụng định luật bảo toàn năng lượng tổng quát: $K_1 + U_1 + W_{khác} = K_2 + U_2$.
    - Ban đầu ở đỉnh dốc: $K_1 = 0$, $U_1 = mgh = 60 \times 9,8 \times 65 = 38220\text{ J}$.
    - Lúc tới chân dốc: $U_2 = 0$, $K_2 = \frac{1}{2}mv_2^2 = 30v_2^2$.
    - Thay vào phương trình: $0 + 38220 - 10500 = 30v_2^2 \Rightarrow 27720 = 30v_2^2 \Rightarrow v_2 = \sqrt{924} \approx 30,4\text{ m/s}$.


Dưới đây là một số bài tập tiêu biểu của Tuần 5 với số liệu cụ thể, tập trung vào Động học quay và Năng lượng quay:

- **Dạng 1: Động học quay với gia tốc góc không đổi (Bài 9.8):** Một bánh xe quay quanh trục Oz. Vận tốc góc $\omega_z = -6,00 \text{ rad/s}$ tại $t = 0$, tăng tuyến tính và đạt $+4,00 \text{ rad/s}$ ở $t = 7,00 \text{ s}$. Yêu cầu: Xác định dấu của gia tốc góc, khoảng thời gian tốc độ quay tăng/giảm, và tính độ dịch chuyển góc tại $t = 7,00 \text{ s}$.
- **Dạng 2: Gia tốc của một điểm trên vật rắn quay (Bài 9.21):** Một bánh xe đường kính $40,0 \text{ cm}$ bắt đầu quay từ trạng thái đứng yên với gia tốc góc không đổi là $3,00 \text{ rad/s}^2$. Yêu cầu tính gia tốc hướng tâm của một điểm trên vành bánh xe tại thời điểm bánh xe vừa hoàn thành vòng quay thứ hai.
- **Dạng 3: Động năng quay và Mômen quán tính (Bài 9.34):** Một cánh quạt máy bay có chiều dài $2,08 \text{ m}$ (tính từ tâm đến đầu cánh) và khối lượng $117 \text{ kg}$ đang quay với tốc độ $2400 \text{ vòng/phút}$ quanh trục qua tâm. Coi cánh quạt như một thanh mỏng, hãy tính động năng quay của cánh quạt đó.


**1. Bài 9.8: Động học quay với gia tốc góc không đổi**

- **Dữ kiện:** $\omega_{0z} = -6,00 \text{ rad/s}$; tại $t = 7,00 \text{ s}$ thì $\omega_z = +4,00 \text{ rad/s}$.
- **(a) Dấu của gia tốc góc:** Sử dụng công thức $\alpha_z = \frac{\Delta\omega_z}{\Delta t} = \frac{4,00 - (-6,00)}{7,00} = \frac{10}{7} \approx 1,43 \text{ rad/s}^2$. Vì kết quả lớn hơn 0 nên gia tốc góc mang dấu **dương**.
- **(b) Khoảng thời gian tốc độ tăng/giảm:** Tốc độ quay là độ lớn của vận tốc góc ($|\omega_z|$).
    - Từ $t = 0$ đến khi dừng lại ($\omega_z = 0$), tốc độ giảm từ 6 xuống 0. Thời gian để dừng là $t = \frac{0 - (-6)}{10/7} = 4,20 \text{ s}$. Vậy tốc độ **giảm** trong khoảng $t = 0$ đến $t = 4,20 \text{ s}$.
    - Từ $t = 4,20 \text{ s}$ đến $t = 7,00 \text{ s}$, vận tốc góc tăng từ 0 đến +4, do đó tốc độ **tăng**.
- **(c) Độ dịch chuyển góc:** Áp dụng phương trình $\Delta\theta = \omega_{0z}t + \frac{1}{2}\alpha_z t^2$. Thay số ta có: $\Delta\theta = (-6,00)(7,00) + \frac{1}{2}(\frac{10}{7})(7,00)^2 = -42,0 + 35,0 = -7,00 \text{ rad}$.

**2. Bài 9.21: Gia tốc hướng tâm trên vật rắn quay**

- **Dữ kiện:** Bán kính $R = \frac{40,0}{2} = 20,0 \text{ cm} = 0,200 \text{ m}$; $\omega_{0z} = 0$; $\alpha_z = 3,00 \text{ rad/s}^2$. Bánh xe hoàn thành 2 vòng, tương đương $\Delta\theta = 2 \times 2\pi = 4\pi \text{ rad}$.
- **Tính vận tốc góc bình phương:** Áp dụng hệ thức độc lập thời gian $\omega_z^2 = \omega_{0z}^2 + 2\alpha_z\Delta\theta$. Suy ra $\omega_z^2 = 0 + 2(3,00)(4\pi) = 24\pi \text{ (rad/s)}^2$.
- **Tính gia tốc hướng tâm:** $a_{rad} = \omega_z^2 R = (24\pi)(0,200) = 4,8\pi \approx 15,1 \text{ m/s}^2$.

**3. Bài 9.34: Động năng quay của cánh quạt**

- **Dữ kiện:** Chiều dài (từ đầu cánh đến đầu cánh) $L = 2,08 \text{ m}$; khối lượng $m = 117 \text{ kg}$; $\omega = 2400 \text{ vòng/phút}$.
- **Đổi đơn vị:** $\omega = 2400 \times \frac{2\pi}{60} = 80\pi \approx 251 \text{ rad/s}$.
- **Tính Mômen quán tính:** Coi cánh quạt như một thanh mảnh quay quanh trục đi qua khối tâm, $I = \frac{1}{12}mL^2$. Thay số: $I = \frac{1}{12}(117)(2,08)^2 \approx 42,2 \text{ kg}\cdot\text{m}^2$.
- **Tính động năng quay:** $K = \frac{1}{2}I\omega^2 = \frac{1}{2}(42,2)(80\pi)^2 \approx 1,33 \times 10^6 \text{ J}$.

Bạn đã hiểu rõ cách áp dụng các công thức động học quay này chưa, hay chúng ta tiếp tục sang các bài toán về Động lực học của chuyển động quay (Mômen lực và định luật II Newton) ở Tuần 6 luôn nhé?

Dưới đây là một số bài tập tiêu biểu của Tuần 6 (Động lực học của chuyển động quay) với đề bài cụ thể:

- **Dạng 1: Tính mômen lực cơ bản (Bài 10.1):** Tính mômen lực (độ lớn và hướng) tại điểm O do lực $\vec{F}$ gây ra đối với một thanh dài 4,00 m. Biết lực có độ lớn $F = 10,0 \text{ N}$ và tác dụng lên thanh dưới nhiều góc độ khác nhau (như vuông góc, hợp với thanh một góc $30^\circ$, $60^\circ$, $120^\circ$).
- **Dạng 2: Mômen lực và động học quay (Bài 10.8):** Một đĩa đồng nhất khối lượng 40,0 kg, bán kính 0,200 m được gắn trên một trục ngang. Có một lực không đổi $F = 30,0 \text{ N}$ tác dụng theo phương tiếp tuyến lên vành đĩa. Yêu cầu tính vận tốc tiếp tuyến và độ lớn của gia tốc tổng hợp tại một điểm trên vành sau khi đĩa đã quay được 0,200 vòng.
- **Dạng 3: Lăn không trượt và bảo toàn năng lượng (Bài 10.28):** Một bánh xe nặng 2,25 kg (coi như hình trụ rỗng thành mỏng, đường kính 85,0 cm) rơi ra khỏi xe đạp khi đang ở độ cao 75,0 m (so với chân đồi) với tốc độ ban đầu 11,0 m/s. Nếu bánh xe lăn không trượt xuống dốc, hãy tính vận tốc và tổng động năng của nó khi đến chân đồi,.

Bạn muốn chúng ta bắt đầu bằng việc thiết lập phương trình cho bài toán đĩa quay chịu lực tiếp tuyến (Bài 10.8), hay muốn xem cách giải bài toán bánh xe lăn không trượt (Bài 10.28) trước?

Dưới đây là hướng dẫn giải chi tiết cho các dạng bài tập tiêu biểu của Tuần 6 (tôi đã cập nhật đúng số liệu từ tài liệu bài tập trọng tâm của bạn):

**1. Dạng 1: Tính mômen lực (Bài 10.1)**

- **Dữ kiện:** Lực $F = 10,0 \text{ N}$ tác dụng lên một thanh dài $r = 4,00 \text{ m}$ tại các góc khác nhau.
- **Phương pháp:** Sử dụng công thức mômen lực $\tau = rF\sin\theta$, với $\theta$ là góc giữa phương của thanh và phương của lực.
- **Thực hiện:**
    - Lực tác dụng vuông góc ($\theta = 90^\circ$): $\tau = 4,00 \times 10,0 \times \sin(90^\circ) = 40,0 \text{ N}\cdot\text{m}$,.
    - Lực hợp một góc $30^\circ$: $\tau = 4,00 \times 10,0 \times \sin(30^\circ) = 20,0 \text{ N}\cdot\text{m}$,.
    - Lực tác dụng dọc theo thanh ($\theta = 0^\circ$): Thanh không quay vì $\sin(0^\circ) = 0$, suy ra $\tau = 0$,.
- **Đánh giá:** Áp dụng quy tắc bàn tay phải, nếu lực có xu hướng làm thanh quay ngược chiều kim đồng hồ, mômen lực sẽ mang dấu dương.

**2. Dạng 2: Động lực học quay và Công suất (Bài 10.29)**

- **Dữ kiện:** Một chiếc đu quay có bán kính $R = 2,40 \text{ m}$ và mômen quán tính $I = 2100 \text{ kg}\cdot\text{m}^2$. Một đứa trẻ đẩy đu quay với lực tiếp tuyến $F = 18,0 \text{ N}$ trong thời gian $t = 15,0 \text{ s}$ từ trạng thái nghỉ.
- **Thực hiện:**
    - **(a) Tốc độ góc:** Mômen lực tác dụng $\tau = F \cdot R = 18,0 \times 2,40 = 43,2 \text{ N}\cdot\text{m}$,. Gia tốc góc $\alpha = \frac{\tau}{I} = \frac{43,2}{2100} \approx 0,0206 \text{ rad/s}^2$. Vận tốc góc sau 15,0 s là $\omega = \omega_0 + \alpha t = 0 + 0,0206 \times 15,0 = 0,309 \text{ rad/s}$.
    - **(b) Công thực hiện:** Độ dịch chuyển góc $\Delta\theta = \frac{1}{2}\alpha t^2 = 0,5 \times 0,0206 \times (15,0)^2 \approx 2,32 \text{ rad}$. Công thực hiện là $W = \tau \Delta\theta = 43,2 \times 2,32 \approx 100 \text{ J}$.
    - **(c) Công suất trung bình:** $P_{av} = \frac{W}{t} = \frac{100}{15,0} \approx 6,67 \text{ W}$.

**3. Dạng 3: Mômen động lượng của chất điểm (Bài 10.35)**

- **Dữ kiện:** Một tảng đá $m = 2,00 \text{ kg}$ đang trượt ngang với vận tốc $v = 12,0 \text{ m/s}$. Tại một thời điểm, nó cách gốc tọa độ khoảng $r = 8,00 \text{ m}$ với góc tạo bởi phương ngang là $36,9^\circ$.
- **Thực hiện:**
    - Mômen động lượng được tính bằng $L = mvr\sin\theta$ (với $r\sin\theta$ chính là cánh tay đòn vuông góc $r_\perp$).
    - Khoảng cách vuông góc là $r_\perp = 8,00 \times \sin(36,9^\circ) \approx 4,80 \text{ m}$.
    - Độ lớn mômen động lượng $L = 2,00 \times 12,0 \times 4,80 = 115,2 \text{ kg}\cdot\text{m}^2/\text{s}$.

Bạn có thấy các bước giải này dễ hiểu định hướng không, hay bạn muốn chúng ta chuyển tiếp sang ôn tập Tuần 8 (Lực hấp dẫn và định luật Kepler) nhé?
Dưới đây là một số bài tập tiêu biểu của Tuần 8 về Lực hấp dẫn, kèm theo dữ kiện cụ thể để bạn luyện tập:

- **Dạng 1: Lực hấp dẫn trong hệ nhiều vật (Bài 13.5):** Hai quả cầu đồng nhất có cùng khối lượng $0,260\text{ kg}$ được đặt cố định. Yêu cầu tính độ lớn và hướng gia tốc ban đầu của một quả cầu nhỏ thứ 3 (khối lượng $0,010\text{ kg}$) khi nó được thả rơi từ một điểm P chịu lực hút tổng hợp từ hai quả cầu kia.
- **Dạng 2: Gia tốc trọng trường trên hành tinh khác (Bài 13.12):** Biết khối lượng của Sao Kim bằng 81,5% khối lượng Trái Đất và bán kính bằng 94,9% bán kính Trái Đất. Bạn cần tính gia tốc trọng trường trên bề mặt Sao Kim, từ đó suy ra trọng lượng của một hòn đá trên Sao Kim nếu nó nặng $75,0\text{ N}$ khi ở trên Trái Đất.
- **Dạng 3: Động lực học quỹ đạo của vệ tinh (Bài 13.23):** Hai vệ tinh chuyển động tròn quanh một hành tinh. Vệ tinh thứ nhất ($68,0\text{ kg}$) ở quỹ đạo bán kính $7,00 \times 10^7\text{ m}$ có tốc độ $4800\text{ m/s}$. Yêu cầu tính tốc độ quỹ đạo của vệ tinh thứ hai ($84,0\text{ kg}$) nằm ở quỹ đạo bán kính $3,00 \times 10^7\text{ m}$.
- **Dạng 4: Phân bố khối lượng hình cầu (Bài 13.32):** Một vỏ cầu đồng chất có khối lượng $1000\text{ kg}$ và bán kính $5,00\text{ m}$. Bài toán yêu cầu tính lực hấp dẫn do vỏ cầu tác dụng lên một vật điểm $2,00\text{ kg}$ đặt tại các khoảng cách khác nhau tính từ tâm (ví dụ: $5,01\text{ m}$ - ngoài vỏ cầu, và $4,99\text{ m}$ - trong vỏ cầu).

Dưới đây là lời giải chi tiết cho 4 dạng bài tập tiêu biểu của Tuần 8 về Lực hấp dẫn:

**1. Bài 13.5: Lực hấp dẫn trong hệ vật**

- **Dữ kiện:** Hai quả cầu $M_A = M_B = 0,260\text{ kg}$ cách nhau $16,0\text{ cm}$. Quả cầu thứ ba $m_P = 0,010\text{ kg}$ cách đều A và B $10,0\text{ cm}$ (cách đường nối AB $6,0\text{ cm}$).
- **Phân tích lực:** Lực hút từ A và B lên P có độ lớn bằng nhau. Do tính đối xứng, hai thành phần lực theo phương ngang triệt tiêu lẫn nhau, lực tổng hợp $\vec{F}_{net}$ chỉ hướng thẳng đứng xuống dưới về phía trung điểm của AB.
- **Độ lớn một lực:** $F_A = G\frac{m_P M_A}{r^2} = (6,674 \times 10^{-11}) \times \frac{0,010 \times 0,260}{(0,100)^2} = 1,735 \times 10^{-11}\text{ N}$.
- **Lực tổng hợp:** Lấy hình chiếu lên phương thẳng đứng ($\cos\theta = \frac{6,0}{10,0} = 0,6$). $F_{net} = 2F_A\cos\theta = 2 \times (1,735 \times 10^{-11}) \times 0,6 = 2,08 \times 10^{-11}\text{ N}$.
- **Gia tốc:** $a = \frac{F_{net}}{m_P} = \frac{2,08 \times 10^{-11}}{0,010} = 2,08 \times 10^{-9}\text{ m/s}^2$ (hướng xuống).

**2. Bài 13.12: Gia tốc trọng trường trên hành tinh khác**

- **Dữ kiện:** Sao Kim có $M_K = 0,815 M_E$ và $R_K = 0,949 R_E$.
- **(a) Gia tốc trọng trường:** Áp dụng công thức $g = G\frac{M}{R^2}$. Ta lập tỉ lệ: $g_K = \frac{0,815}{(0,949)^2}g_E \approx 0,905 \times 9,8 \approx 8,87\text{ m/s}^2$.
- **(b) Trọng lượng hòn đá:** Trọng lượng tỉ lệ thuận với gia tốc trọng trường. Hòn đá nặng $75,0\text{ N}$ trên Trái Đất sẽ nặng $W_K = W_E \times 0,905 = 75,0 \times 0,905 \approx 67,9\text{ N}$ trên Sao Kim.

**3. Bài 13.23: Động lực học quỹ đạo của vệ tinh**

- **Dữ kiện:** Vệ tinh 1 có $r_1 = 7,00 \times 10^7\text{ m}$ và $v_1 = 4800\text{ m/s}$. Tìm $v_2$ của vệ tinh 2 ở quỹ đạo $r_2 = 3,00 \times 10^7\text{ m}$.
- **Phân tích:** Tốc độ quỹ đạo $v = \sqrt{\frac{GM}{r}}$ hoàn toàn không phụ thuộc vào khối lượng của bản thân vệ tinh.
- **Giải:** Ta lập tỉ lệ nghịch: $\frac{v_2}{v_1} = \sqrt{\frac{r_1}{r_2}} = \sqrt{\frac{7,00 \times 10^7}{3,00 \times 10^7}} \approx 1,527$. Vậy $v_2 = 4800 \times 1,527 \approx 7332\text{ m/s}$.

**4. Bài 13.32: Phân bố khối lượng hình cầu**

- **Dữ kiện:** Vỏ cầu có khối lượng $M = 1000\text{ kg}$, bán kính $R = 5,00\text{ m}$. Vật điểm $m = 2,00\text{ kg}$.
- **Lý thuyết:** Lực hấp dẫn bên ngoài vỏ cầu tính như khi toàn bộ khối lượng tập trung ở tâm. Đối với vật nằm bên trong vỏ cầu, lực hấp dẫn tổng cộng bằng 0.
- **(i) Khoảng cách 5,01 m (bên ngoài):** $F = G\frac{Mm}{r^2} = (6,674 \times 10^{-11}) \times \frac{1000 \times 2,00}{(5,01)^2} \approx 5,32 \times 10^{-9}\text{ N}$.
- **(ii) Khoảng cách 4,99 m (bên trong):** $F = 0\text{ N}$.
- **(iii) Khoảng cách 2,72 m (bên trong):** $F = 0\text{ N}$.

Bạn xem qua các bước giải này có điểm nào cần làm rõ thêm không, hay chúng ta tiếp tục sang các bài toán về Dao động tuần hoàn (Tuần 9) nhé?