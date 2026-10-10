Mình đọc file Tuần 04 trước rồi tổng hợp cho bạn.Mình đã đọc hết 99 slide của Tuần 04 (Tóm tắt dữ liệu 3/3). Tuần này học tương quan, hồi quy tuyến tính đơn và đa biến, phần dư và bình phương tối thiểu.

## 1. Biểu đồ phân tán và hệ số tương quan

**Đọc biểu đồ phân tán theo 4 câu hỏi:** hướng (dương/âm), dạng (tuyến tính/phi tuyến), độ mạnh, quan sát bất thường. Một con số tóm tắt chỉ có ý nghĩa sau khi đã nhìn cấu trúc dữ liệu.

**Hệ số tương quan Pearson:**

$$r = \frac{1}{n-1}\sum_{i=1}^{n}\left(\frac{x_i-\bar{x}}{s_x}\right)\left(\frac{y_i-\bar{y}}{s_y}\right)$$

Mỗi biến được chuẩn hóa về đơn vị độ lệch chuẩn. Hai độ lệch cùng dấu đóng góp dương, trái dấu đóng góp âm.

**Tính chất:**

- $-1 \le r \le 1$ và $r$ không có đơn vị.
- $r>0$ là liên hệ tuyến tính dương, $r<0$ là âm, $|r|$ càng gần $1$ thì các điểm càng gần một đường thẳng.
- $r = 0$ chỉ có nghĩa là không có liên hệ **tuyến tính**, không có nghĩa hai biến không liên hệ.
- Với $x' = a + bx$:
    - cộng hằng số hoặc nhân hệ số dương thì $r$ không đổi;
    - nhân hệ số âm ($b<0$) thì $r$ đổi dấu: $r(bx,y) = -r(x,y)$.

Ví dụ nghèo đói–tốt nghiệp trung học (50 bang + Đặc khu Columbia): $r \approx -0.747$, liên hệ âm, khá tuyến tính, độ mạnh vừa đến khá.

**Phản ví dụ cho $r=0$:** $x=(-2,-1,0,1,2)$, $y=(4,1,0,1,4)$, tức $y=x^2$. Biết $x$ xác định chính xác $y$ nhưng $r=0$, vì $\bar{x}=0$ và $\sum x_i y_i=\sum x_i^3=0$.

**Điểm ảnh hưởng mạnh (đòn bẩy cao):** $x=(1,2,3,4,5)$, $y=(1.2,1.8,3.1,3.9,5.1)$ có $r\approx 0.995$ và $\hat{y}\approx 0.05+0.99x$. Thêm điểm $(10,0)$ thì $r\approx -0.259$ và $\hat{y}\approx 3.149-0.152x$. Cả dấu của $r$ lẫn hệ số góc đều đảo. Cần so sánh mô hình có/không có điểm đó.

## 2. Hồi quy tuyến tính đơn giản

$$\hat{y} = b_0 + b_1 x$$

với $\hat{y}$ là giá trị khớp, $b_0$ là hệ số chặn, $b_1$ là hệ số góc, $x$ là biến giải thích.

**Ví dụ:** $\widehat{Poverty} = 64.68 - 0.62,Graduates$. Mỗi $1$ điểm phần trăm tốt nghiệp tăng thêm thì tỷ lệ nghèo khớp thấp hơn trung bình khoảng $0.62$ điểm phần trăm. Đây là mô tả liên hệ, chưa phải nhân quả.

Với $Graduates=85.1$: $\widehat{Poverty}=64.68-0.62(85.1)\approx 11.92$, và đây là giá trị khớp, không phải giá trị quan sát.

**Đơn vị:**

- Đổi $x$ từ điểm phần trăm sang tỷ lệ $0$–$1$ thì $b_1$ lớn lên $100$ lần nhưng $r$ không đổi.
- Không dùng độ lớn $b_1$ như độ mạnh liên hệ nếu bỏ qua đơn vị.

**Hệ số chặn:** $b_0=64.68$ ứng với $Graduates=0$, nằm rất xa dữ liệu (ngoại suy). Về đại số thì cần, nhưng không đáng diễn giải thực tế.

**Ngoại suy:** thay $x=20$ vào phương trình thì tính được về đại số, nhưng về thống kê rất đáng nghi vì giả định cấu trúc tuyến tính tiếp tục đúng ngoài vùng dữ liệu.

## 3. Phần dư và bình phương tối thiểu

$$\text{Dữ liệu} = \text{Giá trị khớp} + \text{Phần dư}, \qquad e_i = y_i - \hat{y}_i$$

- $e_i>0$: điểm nằm trên đường; $e_i<0$: nằm dưới đường. Hình học: khoảng cách thẳng đứng từ điểm đến đường khớp.
- Ví dụ Rhode Island ($Graduates=81$, $Poverty=10.3$): $\hat{y}=14.46$, $e=10.3-14.46=-4.16$. Nghĩa là tỷ lệ nghèo quan sát thấp hơn giá trị khớp $4.16$ điểm phần trăm.

**Mô hình hằng số:** chọn $a$ để $S(a)=\sum(y_i-a)^2$ nhỏ nhất thì $\dfrac{dS}{da}=-2\sum(y_i-a)=0 \Rightarrow a=\bar{y}$. Trung bình là hằng số tối ưu theo tiêu chuẩn này.

**Bình phương tối thiểu cho đường thẳng:** chọn $b_0,b_1$ để

$$SSE=\sum_{i=1}^{n}\left[y_i-(b_0+b_1x_i)\right]^2$$

nhỏ nhất. Bình phương phần dư phạt mạnh phần dư lớn, đại số thuận tiện, được phần mềm hỗ trợ rộng rãi.

**Hai điều kiện chuẩn** (đặt đạo hàm riêng bằng $0$):

$$\sum e_i = 0, \qquad \sum x_i e_i = 0$$

Phần dư cân bằng quanh $0$ và không còn xu hướng tuyến tính theo $x$.

**Suy ra $b_0,b_1$:**

$$b_0 = \bar{y} - b_1\bar{x}, \qquad b_1 = \frac{\sum(x_i-\bar{x})(y_i-\bar{y})}{\sum(x_i-\bar{x})^2} = r,\frac{s_y}{s_x}$$

Hệ quả: đường khớp đi qua $(\bar{x},\bar{y})$ và $b_1$ luôn cùng dấu với $r$.

**Ví dụ:** $\bar{x}=86.01$, $s_x=3.73$, $\bar{y}=11.35$, $s_y=3.10$, $r=-0.75$:

$$b_1 = -0.75\cdot\frac{3.10}{3.73}\approx -0.62, \qquad b_0 = 11.35-(-0.62)(86.01)\approx 64.68$$

**Biểu đồ phần dư (chẩn đoán mô tả):**

- Đường cong có hệ thống: dạng tuyến tính chưa tóm tắt hết, cần xét phi tuyến.
- Dạng "phễu": độ biến thiên của $Y$ quanh đường khớp thay đổi theo $x$.
- Phần dư tốt không chứng minh mô hình "đúng" và không cho kết luận nhân quả.

## 4. Hồi quy tuyến tính đa biến

$$\hat{y} = b_0 + b_1x_1 + b_2x_2 + \cdots + b_px_p$$

- Vẫn tối thiểu hóa $SSE=\sum(y_i-\hat{y}_i)^2$.
- **Cách đọc $b_j$:** khi $x_j$ tăng $1$ đơn vị, giá trị khớp của $y$ thay đổi $b_j$, **giữ các biến giải thích khác cố định**.

**Biến phân loại bằng biến chỉ báo:** ví dụ $D=0$ (bìa cứng, mức tham chiếu), $D=1$ (bìa mềm):

$$\widehat{weight} = 197.96 + 0.72,volume - 184.05,D$$

Hai đường song song (không có tương tác), cùng hệ số góc, khác hệ số chặn:

- $D=0$: $\widehat{weight}=197.96+0.72,volume$.
- $D=1$: $\widehat{weight}=13.91+0.72,volume$.

**Diễn giải:**

- Hệ số $volume$: cùng loại bìa, thể tích lớn hơn $1\ \text{cm}^3$ thì khớp nặng hơn khoảng $0.72$ g.
- Hệ số cover: cùng thể tích, sách bìa mềm nhẹ hơn bìa cứng khoảng $184.05$ g.
- Hệ số chặn: khối lượng khớp của sách bìa cứng thể tích $0$, không có ý nghĩa thực tế.
- Giá trị khớp cho sách bìa mềm $600\ \text{cm}^3$: $197.96+0.72(600)-184.05=445.91$ g.

**Zagat (ba biến số):** $\widehat{price} = -24.5 + 1.64,food + 1.88,decor$.

- Hệ số $1.64$: so sánh hai nhà hàng cùng điểm $decor$, nhà hàng có $food$ cao hơn $1$ điểm được khớp với giá cao hơn trung bình khoảng $1.64$ đơn vị giá.
- Với $food=24$, $decor=20$, $price=60$: $\hat{y}=52.46$, $e=60-52.46=7.54$.

## 5. Các bẫy khi diễn giải hệ số

- **Hệ số đơn biến và đã điều chỉnh khác nhau:** $Y\sim X_1$ hỏi về liên hệ tổng thể; $Y\sim X_1+X_2$ hỏi về liên hệ ở cùng mức $X_2$. Hệ số của $X_1$ có thể đổi, thậm chí đổi dấu, vì hai mô hình trả lời hai câu hỏi khác nhau. Không chọn hệ số chỉ vì trị tuyệt đối lớn hơn.
- **Đường chung che mất cấu trúc nhóm:** nhóm A $(1,3),(2,2),(3,1)$ và nhóm B $(4,13),(5,12),(6,11)$.
    - Bỏ qua nhóm: $\hat{Y}=-1.20+2.343X$.
    - Giữ nhóm: $\hat{Y}=4.00-1.00X+13.00,I(B)$.
    - Hệ số của $X$ đổi dấu vì đường chung chủ yếu nối hai cụm; trong từng nhóm, $X$ tăng $1$ thì $Y$ giảm $1$. Đây là dạng đảo dấu kiểu Simpson trong hồi quy.
- **"Giữ biến khác cố định" không phải phép thuật nhân quả.** Nó không bảo đảm đã đo hết các biến gây nhiễu, mô hình tuyến tính là đúng, hay dữ liệu có thiết kế nhân quả. Điều kiện nhân quả sẽ học ở Tuần 12–13.
- **Mô tả khác nhân quả:** hồi quy quan sát trả lời "các biến cùng thay đổi thế nào", còn nhân quả hỏi "điều gì thay đổi nếu can thiệp".
- Cùng đường hồi quy có thể đến từ hai cơ chế khác nhau, và chỉ từ biểu đồ phân tán cùng hệ số hồi quy thì không phân biệt được. Ví dụ: băng thông cao thường đi cùng máy chủ mới, nên đường hồi quy trộn ảnh hưởng của phần cứng; khác với thí nghiệm giới hạn băng thông trên cùng loại máy.
- **Sửa câu diễn giải sai:** không viết "tăng $food$ thêm $1$ làm giá tăng $1.64$ đô-la". Viết: "so sánh các nhà hàng có cùng $decor$, nhà hàng có $food$ cao hơn $1$ được khớp với giá cao hơn trung bình khoảng $1.64$ đơn vị giá". Hệ số $food$ trong $price\sim food$ không buộc bằng $1.64$ vì mô hình đó không giữ $decor$ cố định.

## 6. Python (chỉ để kiểm chứng)

```python
df["Poverty"].corr(df["Graduates"])               # r ≈ -0.747
m1 = smf.ols("Poverty ~ Graduates", data=df).fit(); m1.params
fitted, resid = m1.fittedvalues, m1.resid         # y = fitted + resid
m2 = smf.ols("price ~ food + decor", data=zagat).fit()
m3 = smf.ols("weight ~ volume + C(cover)", data=books).fit()
```

- `C(cover)` mã hóa biến chỉ báo; phải xác định mức tham chiếu trước khi diễn giải hệ số nhóm.
- Ví dụ phần dư: `fitted = 11.36`, `resid = 5.44` thì $y_i=11.36+5.44=16.80$, quan sát cao hơn giá trị khớp $5.44$ điểm phần trăm.

## 7. Chọn công cụ tóm tắt

- **Dữ liệu gần đường thẳng, không có điểm cực đoan:** tương quan và hồi quy tuyến tính phù hợp, sau khi kiểm tra phần dư.
- **Quan hệ dạng chữ U:** $r$ có thể gần $0$ dù quan hệ mạnh; đường thẳng bỏ sót cấu trúc phi tuyến.
- **Một điểm rất xa theo trục $x$:** có đòn bẩy cao, đổi mạnh $r$ và $b_1$; cần so sánh mô hình có và không có điểm đó.
- **Quy trình chung:** đồ thị → mô hình/tóm tắt số → kiểm tra phần dư → diễn giải trong ngữ cảnh.

## 8. Ghi nhớ cuối

1. Xem biểu đồ trước khi đọc một con số.
2. $r$ đo hướng và độ mạnh của liên hệ tuyến tính, không phải mọi dạng quan hệ.
3. Bình phương tối thiểu tối thiểu hóa $\sum e_i^2$ và thỏa $\sum e_i=0$, $\sum x_ie_i=0$.
4. Trong hồi quy đơn, $b_1=r,\dfrac{s_y}{s_x}$ và đường khớp đi qua $(\bar{x},\bar{y})$.
5. Hệ số góc phải đi cùng đơn vị và ngữ cảnh; hệ số chặn có thể không có ý nghĩa thực tế.
6. Điểm ảnh hưởng mạnh, phi tuyến và cấu trúc nhóm có thể làm tóm tắt tuyến tính gây hiểu lầm.
7. Trong hồi quy nhiều biến, mỗi hệ số được đọc khi giữ các biến còn lại cố định; hệ số có thể đổi dấu khi phép so sánh thay đổi.
8. Hệ số hồi quy và tương quan từ dữ liệu quan sát không tự động là tác động nhân quả.

**Tuần 05 sẽ học:** biến cố, xác suất, xác suất có điều kiện, độc lập và các quy tắc tính xác suất.

Nếu cần, mình có thể làm bộ câu hỏi trắc nghiệm hoặc flashcard cho Tuần 02–04.