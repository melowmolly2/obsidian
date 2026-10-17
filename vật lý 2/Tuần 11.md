# Lý thuyết cần nhớ tuần 11 (Chương 13 và 14)

## Chương 13: Bản chất và sự truyền ánh sáng

**1. Chiết suất, vận tốc và bước sóng**

$$n=\frac{c}{v},\qquad \lambda=\frac{\lambda_0}{n},\qquad v=f\lambda$$

- Khi ánh sáng đổi môi trường, **tần số $f$ không đổi**. Chỉ $v$ và $\lambda$ thay đổi.
- Từ môi trường 1 sang môi trường 2: $\lambda_2=\lambda_1\dfrac{n_1}{n_2}$ (Bài 4).

**2. Phản xạ và khúc xạ (Snell)**

$$\theta_r=\theta_a,\qquad n_a\sin\theta_a=n_b\sin\theta_b$$

- Các góc đều đo **so với pháp tuyến**. Nếu đề cho góc với **bề mặt** (Bài 5) thì đổi lại: $\theta=90^\circ-\alpha_{\text{bề mặt}}$.
- Phản xạ và khúc xạ cùng lúc xảy ra, nên góc giữa tia phản xạ và bề mặt cũng là $90^\circ-\theta_a$.

**3. Phản xạ toàn phần**

- Điều kiện: ánh sáng đi từ môi trường chiết quang hơn sang kém hơn ($n_a>n_b$) và góc tới $\theta_a\ge\theta_{\text{th}}$.

$$\sin\theta_{\text{th}}=\frac{n_b}{n_a}$$

- Bài 8 dùng góc tới hạn để tìm $n$ của chất lỏng, rồi áp dụng Snell cho hai chiều truyền. Khi tia đi từ không khí vào chất lỏng thì không có phản xạ toàn phần.

**4. Tán sắc**

- $n$ phụ thuộc $\lambda$, nên mỗi màu bị khúc xạ một góc khác nhau.
- Độ tách góc: $\Delta\theta=\theta_{\text{đỏ}}-\theta_{\text{tím}}$. Tính từng góc khúc xạ bằng Snell rồi trừ nhau (Bài 9).

**5. Phân cực**

- **Định luật Malus** (ánh sáng đã phân cực, qua kính lọc có trục lệch góc $\varphi$ so với phương phân cực):

$$I=I_{\max}\cos^2\varphi$$

- **Ánh sáng không phân cực** qua kính lọc đầu tiên: $I_1=\dfrac{I_0}{2}$ (cường độ giảm một nửa).
- **Nhiều kính lọc xếp chồng:** cứ qua mỗi kính thì nhân thêm $\cos^2$ của **góc lệch giữa hai trục liền kề**. Ví dụ với ba kính:

$$I=\frac{I_0}{2}\cos^2(\varphi_2-\varphi_1)\cos^2(\varphi_3-\varphi_2)$$

- Dùng **góc giữa hai kính liền kề**, không dùng góc so với kính thứ nhất. Khi bỏ một kính ở giữa, phải tính lại góc giữa hai kính còn lại (Bài 12, 13).
- **Góc Brewster** (phân cực hoàn toàn khi phản xạ):

$$\tan\theta_p=\frac{n_b}{n_a}$$

- Ở góc Brewster, tia phản xạ **vuông góc** với tia khúc xạ: $\theta_p+\theta_b=90^\circ$.
- Bài 10 hỏi "phân cực hoàn toàn" nên dùng **góc Brewster**, không dùng góc tới hạn.

## Chương 14: Giao thoa ánh sáng và sóng

**1. Điều kiện giao thoa**

Đặt $\Delta r=|r_1-r_2|$ là hiệu đường đi. Với hai nguồn **kết hợp, cùng pha**:

$$\text{Cực đại (tăng cường): }\Delta r=m\lambda,\qquad \text{Cực tiểu (triệt tiêu): }\Delta r=\left(m+\tfrac12\right)\lambda$$

Với $m=0,\pm1,\pm2,\dots$

- Bài 1 (hai loa): tìm $\lambda=\dfrac{v}{f}$. Ở điểm giữa, $\Delta r=0$ nên là giao thoa tăng cường. Khi đi lệch một đoạn $x$ so với tâm, $\Delta r=2x$.

**2. Thí nghiệm Young (hai khe)**

$$\text{Cực đại sáng: } d\sin\theta=m\lambda,\qquad \text{Cực tiểu tối: } d\sin\theta=\left(m+\tfrac12\right)\lambda$$

Với góc nhỏ ($\sin\theta\approx\tan\theta=y/R$):

$$y_m=\frac{m\lambda R}{d}$$

- Khoảng vân: $\Delta y=\dfrac{\lambda R}{d}$ (khoảng cách giữa hai vân sáng hoặc hai vân tối liền kề).
- Vân sáng thứ $m$ không tính vân trung tâm: $y_m=m\dfrac{\lambda R}{d}$ (Bài 2 với $m=20$).
- Vạch tối thứ hai và thứ ba là hai vạch tối kề nhau, nên khoảng cách giữa chúng đúng bằng $\dfrac{\lambda R}{d}$ (Bài 3).

**3. Cường độ giao thoa**

$$I=I_0\cos^2\frac{\phi}{2},\qquad \phi=\frac{2\pi}{\lambda}\Delta r$$

**4. Giao thoa trên màng mỏng**

Quy tắc đảo pha khi phản xạ:

- Phản xạ ở mặt phân cách đi từ môi trường chiết quang **kém sang hơn** ($n_{\text{tới}}<n_{\text{sau}}$) thì **đảo pha $\pi$** (tương đương lệch thêm $\lambda/2$).
- Phản xạ từ môi trường chiết quang hơn sang kém hơn thì **không đảo pha**.

Với ánh sáng chiếu vuông góc, màng dày $t$, chiết suất $n$:

- **Một** mặt đảo pha (hoặc không mặt nào, hay cả hai, thì khác nhau, cần đếm số lần đảo pha):
    - Số lần đảo pha là **0 hoặc 2**: tăng cường khi $2nt=m\lambda$, triệt tiêu khi $2nt=\left(m+\tfrac12\right)\lambda$.
    - Số lần đảo pha là **1**: tăng cường khi $2nt=\left(m+\tfrac12\right)\lambda$, triệt tiêu khi $2nt=m\lambda$.
- Bước sóng $\lambda$ ở đây là bước sóng **trong chân không** (nếu dùng $\lambda/n$ trong màng thì bỏ $n$ ở vế trái).
- Độ dày **nhỏ nhất** ứng với giá trị $m$ nhỏ nhất thoả điều kiện, và $t>0$. Bài 6 cần xác định xem có một hay hai lần đảo pha, dựa vào chiết suất màng so với không khí và nước.

**5. Nêm không khí**

Hai tấm kính tạo nêm không khí, đỉnh nêm có $t=0$:

- Tia phản xạ ở mặt trên của lớp không khí (kính → không khí): không đảo pha.
- Tia phản xạ ở mặt dưới của lớp không khí (không khí → kính): đảo pha.
- Vậy chỉ có **một** lần đảo pha. Do đó:
    - Vân **tối** khi $2t=m\lambda$ (đỉnh nêm là vân tối vì $t=0$).
    - Vân **sáng** khi $2t=\left(m+\tfrac12\right)\lambda$.
- Với nêm có góc nhỏ $\theta$ và độ dày $t=x\theta$, khoảng cách giữa hai vân tối liền kề là $\Delta x=\dfrac{\lambda}{2\theta}$, suy ra

$$\theta=\frac{\lambda}{2\Delta x}$$

- Bài 4: đổi mật độ vân $15{,}0$ vân/cm thành $\Delta x=\dfrac{1}{15}$ cm, rồi tính $\theta$ (đơn vị rad, đổi sang độ nếu cần).
- Bài 5: nêm dài $L=9{,}00$ cm, độ dày đầu kia $h=0{,}0800$ mm. Tổng số vân $\approx \dfrac{2h}{\lambda}$, nên số vân trên mỗi cm là $\dfrac{2h}{\lambda L}$.

## Những chỗ dễ sai

1. **Góc so với pháp tuyến hay so với bề mặt?** Kiểm tra kỹ đề (Bài 5, 7).
2. **Đổi đơn vị:** nm, mm, cm, m; ns thành s (Bài 6: $t=\dfrac{L}{v}-\dfrac{L}{c}$ là độ trễ).
3. **Bài 11 – 13 (Malus):** góc lấy **giữa hai kính liền kề**, và nhớ hệ số $\tfrac12$ ở kính đầu cho ánh sáng không phân cực.
4. **Bài 10:** phân cực hoàn toàn thì dùng Brewster, không phải góc tới hạn.
5. **Giao thoa:** phân biệt "vân sáng thứ $m$" với "vạch tối thứ $m$" (tối bắt đầu từ $m+\tfrac12$).
6. **Màng mỏng, nêm:** luôn đếm số lần đảo pha trước khi chọn công thức tăng cường hay triệt tiêu.
7. **Máy tính:** chuyển sang chế độ **độ** khi tính $\sin,\cos,\tan$ với góc cho bằng độ.

Bạn muốn mình giải chi tiết bài nào, hoặc tổng hợp công thức thành bảng một trang để ôn thi không?