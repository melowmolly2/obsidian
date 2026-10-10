Mình đã đọc hết 93 slide của Tuần 05 (Khái quát dữ liệu 1/7). Tuần này đặt nền tảng xác suất: không gian mẫu, biến cố, tiên đề, xác suất có điều kiện, độc lập, xác suất toàn phần và định lý Bayes. Ký hiệu phần bù dưới đây mình viết là $A^c$.

## 1. Vì sao cần xác suất

- Chuỗi khái quát: tổng thể ⟶ mẫu ngẫu nhiên ⟶ thống kê từ mẫu. Tỷ lệ lỗi quan sát được thay đổi giữa các mẫu ngay cả khi chất lượng lô không đổi.
- Xác suất dùng để mô tả biến thiên do ngẫu nhiên, định lượng mức bất định của kết luận, và xây dựng phân phối mẫu cho các tuần suy luận sau.

## 2. Không gian mẫu và biến cố

- **Phép thử ngẫu nhiên:** lặp lại được trong điều kiện tương tự, biết trước các kết quả có thể, chưa biết kết quả cụ thể.
- **Không gian mẫu $\Omega$:** tập mọi kết quả có thể. Có thể hữu hạn (${1,\dots,6}$), đếm được hoặc không đếm được (thời gian chờ $\Omega=[0,+\infty)$).
- **Biến cố:** một tập con của $\Omega$.
- **Phép toán:**
    - $A \subseteq B$: mọi kết quả của $A$ đều thuộc $B$.
    - Hợp $A\cup B$: ít nhất một biến cố xảy ra. Giao $A\cap B$: cả hai cùng xảy ra.
    - Phần bù $A^c=\Omega\setminus A$, hiệu $A\setminus B = A\cap B^c$.
- **Xung khắc:** $A\cap B=\emptyset$. **Đối nhau:** $A\cap A^c=\emptyset$ và $A\cup A^c=\Omega$. Hai biến cố xung khắc chưa chắc đối nhau, ví dụ vé mức "thấp" và "cao" xung khắc nhưng không đối nhau.
- **De Morgan:**

$$(A\cup B)^c = A^c\cap B^c, \qquad (A\cap B)^c = A^c\cup B^c$$

- **Cách biểu diễn bằng ký hiệu tập hợp (hai máy chủ):**
    - ít nhất một sự cố: $A\cup B$;
    - cả hai bình thường: $A^c\cap B^c = (A\cup B)^c$;
    - không đồng thời cả hai sự cố: $(A\cap B)^c = A^c\cup B^c$;
    - chỉ máy 1 sự cố: $A\cap B^c$.
- Với ba nhà máy, "đúng một trong ba đúng hạn" là hợp của ba trường hợp đôi một xung khắc, ví dụ $(A_1\cap A_2^c\cap A_3^c)\cup\cdots$.

## 3. Tiên đề và hệ quả

$$P(A)\ge 0, \qquad P(\Omega)=1, \qquad P\Big(\bigcup_i A_i\Big)=\sum_i P(A_i)\ \text{ nếu } A_i \text{ đôi một rời nhau}$$

**Hệ quả:**

$$P(\emptyset)=0, \quad P(A^c)=1-P(A), \quad A\subseteq B\Rightarrow P(A)\le P(B), \quad P(A\setminus B)=P(A)-P(A\cap B)$$

**Kết quả đồng khả năng:** nếu $\Omega$ hữu hạn và các kết quả thật sự đồng khả năng thì

$$P(A)=\frac{|A|}{|\Omega|}$$

Công thức này chỉ dùng khi đồng khả năng. Ví dụ: tung đồng xu rồi (ngửa thì tung tiếp, sấp thì gieo xúc xắc) cho $\Omega={HH,HT,T1,\dots,T6}$ nhưng $8$ kết quả không đồng khả năng: $P(HH)=\tfrac14$, $P(T1)=P(T)P(1\mid T)=\tfrac1{12}$.

**Tần suất tương đối dài hạn:** khi lặp độc lập nhiều lần, tần suất của $A$ ổn định quanh $P(A)$.

## 4. Quy tắc cộng

$$P(A\cup B)=P(A)+P(B)-P(A\cap B)$$

Nếu $A,B$ xung khắc thì bỏ số hạng $P(A\cap B)$.

Ví dụ $137$ hộ (Internet $I$, truyền hình $T$):

$$P(I\cup T)=\frac{86}{137}+\frac{107}{137}-\frac{69}{137}=\frac{124}{137}\approx 0.905$$

Cũng có thể dùng phần bù: chỉ $13$ hộ không dùng dịch vụ nào.

## 5. Xác suất có điều kiện, quy tắc nhân, độc lập

**Xác suất có điều kiện** (với $P(B)>0$):

$$P(A\mid B)=\frac{P(A\cap B)}{P(B)}$$

Biết $B$ xảy ra thì không gian tham chiếu thu hẹp còn $B$. Ví dụ: $P(T\mid I)=\dfrac{69}{86}\approx 0.802$ khác $P(I\mid T)=\dfrac{69}{107}\approx 0.645$ vì cùng tử số nhưng khác mẫu số.

**Quy tắc nhân:**

$$P(A\cap B)=P(A)P(B\mid A)=P(B)P(A\mid B)$$

$$P(A\cap B\cap C)=P(A)P(B\mid A)P(C\mid A\cap B)$$

Ví dụ lấy $2$ quân không hoàn lại (túi $3$ xanh, $7$ khác): $P=\dfrac{3}{10}\cdot\dfrac{2}{9}=\dfrac{1}{15}$.

**Độc lập:**

$$P(A\cap B)=P(A)P(B)$$

Với $P(A),P(B)>0$ thì tương đương $P(A\mid B)=P(A)$ hoặc $P(B\mid A)=P(B)$.

- Có hoàn lại thì các lần lấy độc lập; không hoàn lại thì thường phụ thuộc.
- Độc lập là phát biểu về phân phối xác suất, không dựa vào việc hai biến cố "có vẻ không liên quan".
- Ví dụ: gieo hai xúc xắc, $E={\text{tổng}=6}$, $F={\text{xúc xắc 1}=4}$ có $P(E\mid F)=\tfrac16\neq P(E)=\tfrac{5}{36}$, nên phụ thuộc.
- Kiểm tra độc lập trong bảng: nhóm học và phụ đạo độc lập vì $P(A\mid B)=\dfrac{18}{54}=\dfrac{1}{3}=P(A)=\dfrac{42}{126}$.

**Xung khắc không phải độc lập.** Nếu $P(A),P(B)>0$ và $A,B$ xung khắc thì $P(A\cap B)=0\neq P(A)P(B)$, nên chúng phụ thuộc. Ví dụ mặt $1$ và mặt $6$ khi gieo xúc xắc: xung khắc nhưng phụ thuộc.

**Ví dụ điều kiện:** biết hai xúc xắc ra số khác nhau thì $P(\text{ít nhất một mặt }6)=\dfrac{10/36}{30/36}=\dfrac13$. Cặp $(6,6)$ thuộc $A$ nhưng không thuộc $B$.

## 6. Xác suất toàn phần và định lý Bayes

**Xác suất toàn phần:** nếu $A_1,\dots,A_k$ là phân hoạch của $\Omega$ (đôi một xung khắc, hợp bằng $\Omega$) thì

$$P(B)=\sum_{i=1}^{k}P(B\mid A_i)P(A_i)$$

**Định lý Bayes** (với $P(B)>0$):

$$P(A_j\mid B)=\frac{P(B\mid A_j)P(A_j)}{\sum_{i=1}^{k}P(B\mid A_i)P(A_i)}$$

Bayes cập nhật xác suất của "nguyên nhân" $A_j$ sau khi quan sát kết quả $B$.

**Sơ đồ cây:** nhân các xác suất dọc theo một nhánh, cộng xác suất các nhánh rời nhau cùng dẫn đến kết quả cần xét.

**Ví dụ hai dây chuyền** (A: $60%$, lỗi $2%$; B: $40%$, lỗi $5%$):

$$P(L)=0.02(0.60)+0.05(0.40)=0.032, \qquad P(B\mid L)=\frac{0.05(0.40)}{0.032}=0.625$$

Dây chuyền B chỉ tạo $40%$ sản lượng nhưng chiếm $62.5%$ sản phẩm lỗi. Lưu ý $P(L\mid B)=0.05$ khác $P(B\mid L)=0.625$.

**Ví dụ ba tài khoản email** ($70%,20%,10%$; tỷ lệ rác $1%,2%,5%$): $P(\text{rác})=0.016$. Hậu nghiệm:

|Tài khoản|$P(A_i)$|$P(A_i\mid \text{rác})$|
|---|---|---|
|1|$0.70$|$0.4375$|
|2|$0.20$|$0.2500$|
|3|$0.10$|$0.3125$|

Tài khoản $3$ có tỷ lệ rác cao nhất nhưng tài khoản $1$ vẫn là nguồn có khả năng cao nhất vì nhận nhiều thư hơn.

**Mô hình SIR** (cảm nhiễm $60%$, đang nhiễm $10%$, hồi phục $30%$; xác suất dương tính lần lượt $0.05$, $0.99$, $0.35$):

$$P(+)=0.60(0.05)+0.10(0.99)+0.30(0.35)=0.234, \qquad P(\text{nhiễm}\mid +)=\frac{0.099}{0.234}\approx 0.423$$

Dương tính nâng xác suất từ $0.10$ lên khoảng $0.423$ nhưng không đồng nghĩa chắc chắn nhiễm.

**Hai viên bi chuyển hộp:** $P(B)=\dfrac{2}{7}\cdot\dfrac{2}{3}+\dfrac{1}{7}\cdot\dfrac{1}{3}=\dfrac{5}{21}$ và $P(A\mid B)=\dfrac{4/21}{5/21}=\dfrac{4}{5}$ (tăng từ $\tfrac23$).

**Lô linh kiện** ($P(A_0)=\tfrac12$, $P(A_1)=\tfrac{3}{10}$, $P(A_2)=\tfrac15$, lấy $2$ không hoàn lại): $P(\text{cả hai tốt})=\dfrac{389}{450}$ và $P(A_0\mid \text{cả hai tốt})=\dfrac{225}{389}\approx 0.578$. Cả hai tốt chưa bảo đảm lô không lỗi. Với "đúng một lỗi" thì $P(C)=\dfrac{59}{450}$ và $P(A_0\mid C)=0$.

## 7. Hai sai lầm kinh điển

**Sally Clark.** Công tố lấy $\left(\dfrac{1}{8543}\right)^2\approx \dfrac{1}{73\ \text{triệu}}$, mắc hai lỗi:

1. **Giả định độc lập sai:** yếu tố gia đình hoặc sinh học chung có thể làm $P(S_2\mid S_1)\neq P(S_2)$. Công thức đúng là $P(S_1\cap S_2)=P(S_1)P(S_2\mid S_1)$.
2. **Đảo chiều xác suất:** $P(\text{bằng chứng}\mid \text{vô tội})\neq P(\text{vô tội}\mid \text{bằng chứng})$. Cần xét giả thuyết cạnh tranh, xác suất ban đầu và toàn bộ bằng chứng.

**De Méré.** Ông lập luận "$4\times\tfrac16=24\times\tfrac1{36}=\tfrac23$". Sai vì các biến cố "mặt $6$ ở lần $i$" không xung khắc, nên cộng trực tiếp đếm lặp. Cách đúng là dùng phần bù và quy tắc nhân (các lần gieo độc lập):

$$P(B_1)=1-\left(\frac56\right)^4\approx 0.518, \qquad P(B_2)=1-\left(\frac{35}{36}\right)^{24}\approx 0.491$$

Trò $1$ có xác suất thắng $>\tfrac12$, trò $2$ có $<\tfrac12$. Mô phỏng $50000$ ván (NumPy) khớp lý thuyết.

**Hệ thống $n$ mô-đun độc lập**, mỗi mô-đun lỗi với xác suất $p$:

$$P(\text{ít nhất một lỗi})=1-(1-p)^n$$

Với $p=0.02$: $1-0.98^n>0.5\iff n>\dfrac{\ln 0.5}{\ln 0.98}\approx 34.31$, nên $n=35$. Không dùng $np$ làm xác suất chính xác vì $np=\sum P(A_i)$ là tổng xác suất các biến cố không xung khắc và có thể vượt $1$.

**Hai thiết bị báo cháy độc lập** ($0.95$ và $0.92$):

$$P(\text{cả hai đúng})=0.95\times 0.92=0.874$$

$$P(\text{hệ thống hoạt động})=P(A\cup B)=0.95+0.92-0.874=0.996$$

$$P(\text{không hoạt động})=1-0.996=0.004$$

## 8. Ghi nhớ cuối

- Không gian mẫu và biến cố (tập con của $\Omega$) mô tả phép thử; công thức $|A|/|\Omega|$ chỉ dùng khi đồng khả năng.
- Cộng: $P(A\cup B)=P(A)+P(B)-P(A\cap B)$; nhân: $P(A\cap B)=P(A)P(B\mid A)$; phần bù: $P(A^c)=1-P(A)$. Với "ít nhất một", thường tính qua phần bù.
- $P(A\mid B)\neq P(B\mid A)$ nói chung; mẫu số quyết định câu hỏi.
- Độc lập $\ne$ xung khắc; xung khắc có xác suất dương thì phụ thuộc.
- Có hoàn lại thì độc lập, không hoàn lại thì thường phụ thuộc.
- Xác suất toàn phần là trung bình có trọng số theo phân hoạch; Bayes cập nhật xác suất nguyên nhân sau khi quan sát kết quả.

**Tuần 06 sẽ học:** phân phối xác suất và biến ngẫu nhiên (đọc trước biến ngẫu nhiên rời rạc).

Nếu cần, mình có thể làm bộ câu hỏi trắc nghiệm hoặc flashcard cho Tuần 02–05.