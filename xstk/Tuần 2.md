Mình đã đọc hết 114 slide của Tuần 02 (Tóm tắt dữ liệu 1/3), đây là phần cần nhớ.

## 1. Tư duy xuyên suốt

- Tóm tắt luôn bỏ đi một phần thông tin. Câu hỏi đúng là "tóm tắt nào giữ lại đúng thông tin cần cho câu hỏi?".
- Quy trình: loại biến + câu hỏi → chọn tóm tắt → diễn giải.
- Một tóm tắt đúng số học vẫn có thể trả lời sai câu hỏi (sai mẫu số, che mất cấu trúc nhóm).

## 2. Dữ liệu phân loại

**Công cụ:** số đếm, tỉ lệ, biểu đồ cột, bảng liên hợp (contingency table).

**Đọc bảng liên hợp:**

- Ô là một tổ hợp hai mức.
- Tổng hàng và tổng cột là số đếm biên.
- Tổng chung là toàn bộ quan sát.

**Mẫu số quyết định câu hỏi.** Với ô "Người lớn & Sống sót" = 654 trong bảng Titanic (tổng 2201, người lớn 2092, sống sót 711):

| Câu hỏi                   | Tỉ lệ                              |
| ------------------------- | ---------------------------------- |
| Trên toàn bộ hành khách   | $\dfrac{654}{2201}$                |
| Trong nhóm người lớn      | $\dfrac{654}{2092} \approx 31.3\%$ |
| Trong nhóm người sống sót | $\dfrac{654}{711} \approx 92.0\%$  |

Tỉ lệ sống sót của trẻ em là $\dfrac{57}{109} \approx 52.3\%$. Không được so sánh số đếm thô ($654 > 57$) khi hai nhóm khác kích thước.

**Phân phối biên và phân phối có điều kiện:**

- Phân phối biên mô tả một biến mà không cố định biến kia.
- Phân phối có điều kiện mô tả một biến trong một mức cụ thể của biến kia.
- Hai hướng điều kiện hóa kể hai câu chuyện khác nhau (island trong từng species khác với species trong từng island).

**Mối liên hệ mô tả (association):** hai biến phân loại có liên hệ nếu phân phối có điều kiện của biến này thay đổi theo mức của biến kia. Mối liên hệ không suy ra được quan hệ nhân quả.

**Biểu đồ:**

- Biểu đồ cột dùng cho các mức phân loại.
- Histogram dùng cho các khoảng trên thang số, và tính kề nhau của khoảng có ý nghĩa. Tiêu chí phân biệt là ý nghĩa của trục x, không phải khoảng cách giữa các cột.
- Biểu đồ số đếm nhấn mạnh quy mô, biểu đồ tần suất tương đối nhấn mạnh cơ cấu. Một đồ thị đúng vẫn có thể hỗ trợ lập luận sai.

## 3. Dữ liệu số: hình dạng và trung tâm

**Mô tả phân phối gồm 4 ý:** hình dạng (số mốt, đối xứng hay lệch), trung tâm, độ phân tán, giá trị bất thường.

**Lưu ý về histogram và ngoại lai:**

- Độ rộng khoảng chia là một quyết định phân tích. Vùng giá trị chính và đuôi dài thường ổn định, còn số đỉnh và khoảng trống có thể đổi theo cách chia.
- Giá trị bất thường có thể là giá trị thật hiếm, một nhóm khác, hoặc lỗi đo/nhập liệu. Không tự động xóa.

**Trung bình mẫu:**

$$\bar{x} = \frac{1}{n}\sum_{i=1}^{n} x_i$$

Trung bình dùng độ lớn của mọi quan sát nên nhạy với giá trị cực đoan.

**Trung bình tối thiểu hóa tổng sai số bình phương.** Đặt $S(a) = \sum_{i=1}^{n}(x_i - a)^2$.

Cách 1 (giải tích):

$$S'(a) = -2\sum_{i=1}^{n}(x_i - a) = 0 ;\Longrightarrow; a = \bar{x}, \qquad S''(a) = 2n > 0$$

Cách 2 (đẳng thức phân rã), dùng $\sum_i (x_i - \bar{x}) = 0$:

$$\sum_{i=1}^{n}(x_i - a)^2 = \sum_{i=1}^{n}(x_i - \bar{x})^2 + n(a - \bar{x})^2$$

Phần thứ nhất không phụ thuộc $a$, phần thứ hai $\ge 0$, nên min đạt duy nhất tại $a = \bar{x}$. Đẳng thức này còn cho biết chọn $a \neq \bar{x}$ thì mất thêm đúng $n(a-\bar{x})^2$. Ví dụ với dữ liệu $2, 4, 9$ có $\bar{x} = 5$:

$$L(c) = 26 + 3(c-5)^2$$

Chọn trung bình là một quyết định mô hình hóa (mất mát bình phương). Đổi hàm mất mát thì đổi tâm tối ưu: trung vị gắn với mất mát tuyệt đối.

**Trung vị:** giá trị chia dữ liệu đã sắp xếp thành hai nửa, phụ thuộc thứ hạng nên bền vững.

Ví dụ STAT20 với dãy $8, 11, 7, 7, 8, 11, 9, 6, 10, 7, 9$:

| |Trung bình|Trung vị|
|---|---|---|
|Gốc|$8.45$|$8$|
|Thay $6$ bằng $-200$|$-10.27$|$8$|

**Quan hệ trung bình–trung vị với hình dạng:** đuôi kéo về phía thấp thì trung bình nhỏ hơn trung vị (ví dụ trung bình $76\%$, trung vị $80\%$). Đuôi kéo về phía cao thì ngược lại.

## 4. Độ phân tán và biểu đồ hộp

**Phương sai và độ lệch chuẩn mẫu:**

$$s^2 = \frac{1}{n-1}\sum_{i=1}^{n}(x_i - \bar{x})^2, \qquad s = \sqrt{s^2}$$

$s$ có cùng đơn vị với dữ liệu, còn $s^2$ có đơn vị bình phương (ví dụ giấc ngủ: phương sai $4.11$ giờ², SD $2.03$ giờ). Cùng trung tâm vẫn có thể khác độ phân tán, ví dụ ${7,8,9}$ và ${1,8,15}$ đều có trung bình = trung vị = $8$ nhưng range lần lượt là $2$ và $14$.

**Tứ phân vị và IQR:**

$$IQR = Q_3 - Q_1$$

- $Q_1$, trung vị, $Q_3$ lần lượt là phân vị $25%$, $50%$, $75%$.
- IQR là độ rộng của $50%$ quan sát ở giữa.
- Tóm tắt năm số: $\min, Q_1, \text{trung vị}, Q_3, \max$.
- Các cặp thường đi cùng nhau: trung bình ↔ SD, trung vị ↔ IQR.

**Biểu đồ hộp:**

- Hiển thị trung vị, $Q_1$, $Q_3$, râu và điểm bất thường.
- Với quy ước mặc định `whis=1.5`, hai hàng rào là $Q_1 - 1.5,IQR$ và $Q_3 + 1.5,IQR$.
- Râu vươn tới quan sát xa nhất còn nằm trong hàng rào, nên đầu râu không phải lúc nào cũng là min/max.
- Điểm ngoài hàng rào được vẽ riêng.
- Biểu đồ hộp nén mạnh hình dạng, có thể che số đỉnh, khoảng trống, cụm. Vì vậy nên xem thêm histogram hoặc biểu đồ chấm.

Ví dụ bài điểm thi: $Q_1 = 72.5$, $Q_3 = 82.5$, $IQR = 10$, hàng rào là $57.5$ và $97.5$. Điểm $57$ là ngoại lai tiềm năng, râu dưới dừng ở $66$.

## 5. Phản biện và chọn tóm tắt

**Tính bền vững:** khi một quan sát bị đẩy cực đoan, trung bình và SD đổi mạnh, trung vị và IQR đổi ít. Với dãy STAT20 gốc và dãy đã thay $6$ bằng $-200$:

| |Trung bình|Trung vị|SD mẫu|IQR|
|---|---|---|---|---|
|Gốc|$8.455$|$8$|$1.695$|$2.5$|
|Sau thay|$-10.273$|$8$|$62.943$|$2.5$|

Báo cáo chỉ "trung bình $= -10.27$" che mất việc $10/11$ quan sát vẫn nằm từ $7$ đến $11$.

**Quy tắc chọn tóm tắt (kinh nghiệm, không phải luật):**

- Gần đối xứng, không có cực trị chi phối thì dùng trung bình/SD.
- Lệch mạnh hoặc có cực trị thì trung vị/IQR thường bền vững hơn.
- Mục tiêu quyết định cuối cùng: cần tổng hoặc bình quân trên toàn bộ đơn vị thì trung bình có thể là đại lượng cần; cần "một quan sát điển hình" thì trung vị có thể hợp hơn.
- Không dùng máy móc "lệch thì luôn dùng trung vị".

**Các phản ví dụ cần nhớ:**

- Trung bình $=$ trung vị không suy ra đối xứng. Ví dụ $(-4,-1,0,2,3)$ có cả hai bằng $0$ nhưng không đối xứng.
- Cùng trung bình và SD chưa chắc cùng phân phối. Ví dụ $A=(-1,-1,-1,1,1,1)$ và $B=(-2,0,0,0,1,1)$ đều có $\bar{x}=0$ và $s=\sqrt{6/5}$ nhưng hình dạng khác hẳn.
- Trung bình có thể rất kém về mặt "điển hình". Ví dụ $9,9,10,10,10,11,-100$ có $\bar{x}\approx -5.86$ nhưng trung vị $=10$.
- Cùng trung vị và IQR vẫn có thể khác số mốt, khoảng trống, đuôi.

**Biến đổi thang đo $Y = aX + b$ với $a \neq 0$:**

|Đại lượng|Công thức|
|---|---|
|Trung bình|$\bar{y} = a\bar{x} + b$|
|Trung vị|$\text{Med}(Y) = a,\text{Med}(X) + b$|
|SD mẫu|$s_Y = \lvert a\rvert, s_X$|
|IQR|$IQR_Y = \lvert a\rvert, IQR_X$|

- Hằng số $b$ chỉ dịch vị trí.
- Hệ số $a$ vừa co giãn vừa đảo thứ tự nếu $a<0$.
- SD và IQR dùng $\lvert a\rvert$ vì khoảng cách không thể âm.
- Kiểm chứng với $Y = 3X + 5$: $\bar{y}\approx 30.364$, $\text{Med}(Y)=29$, $s_Y\approx 5.085$, $IQR_Y = 7.5$.

**Cập nhật trung bình và SD khi thêm một quan sát (bài kiểm tra bù):** $24$ bạn có $\bar{x}=74$, $s=8.9$, thêm một bạn $64$ điểm:

$$\bar{x}_{\text{new}} = \frac{24\cdot 74 + 64}{25} = 73.6$$

$$s_{\text{new}} = \sqrt{\frac{23(8.9)^2 + 24(74-73.6)^2 + (64-73.6)^2}{24}} \approx 8.94$$

Trung bình giảm, SD chỉ tăng nhẹ vì điểm mới chỉ chiếm $1/25$ lớp.

## 6. Ví dụ số liệu có thể gặp lại

**Palmer Penguins** (bảng species × island, tổng $333$):

|Loài|Biscoe|Dream|Torgersen|Tổng|
|---|---|---|---|---|
|Adelie|44|55|47|146|
|Chinstrap|0|68|0|68|
|Gentoo|119|0|0|119|
|Tổng|163|123|47|333|

Ba mẫu số khác nhau cho ô $55$:

- $\dfrac{55}{333}\approx 16.5\%$: Adelie ở Dream trên toàn bộ chim.
- $\dfrac{55}{146}\approx 37.7\%$: Adelie ở Dream trong số Adelie.
- $\dfrac{55}{123}\approx 44.7\%$: chim ở Dream là Adelie.

Với `body_mass_g`: trung vị $=4050$ g, $IQR=1225$ g, lệch phải, nên dùng trung vị + IQR để mô tả điển hình. Phản biện "loài quyết định hòn đảo" là khẳng định nhân quả, bảng chỉ cho thấy mối liên hệ.

**Bảng lỗi thiết bị (A: $100$, B: $200$):** lỗi nghiêm trọng A $=10$, B $=20$.

- Tỉ lệ lỗi nghiêm trọng đều là $\dfrac{10}{100}=\dfrac{20}{200}=10\%$.
- Kết luận "B nguy hiểm gấp đôi vì $20>10$" là sai vì dùng số đếm thô.

**Nhập cư (IMS2e), $n=910$:**

- Conservative: $\dfrac{372}{910}\approx 40.9\%$.
- Chọn Apply for citizenship trong toàn mẫu: $\dfrac{278}{910}\approx 30.5%$.
- Tỉ lệ này trong từng nhóm: conservative $\dfrac{57}{372}\approx 15.3%$, liberal $\dfrac{101}{175}\approx 57.7\%$, moderate $\dfrac{120}{363}\approx 33.1\%$.
- Các tỉ lệ có điều kiện khác nhau rõ nên có liên hệ mô tả, không kết luận nhân quả.

**Chọn tóm tắt theo hình dạng:**

- Số thú cưng/hộ: lệch phải, dùng trung vị + IQR.
- Chiều cao nam trưởng thành: gần đối xứng, dùng trung bình + SD.
- Điểm bài thi rất dễ: lệch trái, dùng trung vị + IQR.

## 7. Python/pandas (chỉ để kiểm chứng)

|Lệnh|Ý nghĩa|
|---|---|
|`value_counts()`|số đếm từng mức|
|`value_counts(normalize=True)`|tỉ lệ trên toàn bộ quan sát hợp lệ|
|`pd.crosstab(a, b, margins=True)`|bảng liên hợp kèm tổng hàng, cột, chung|
|`crosstab(..., normalize="index")`|mỗi hàng tổng $1$: phân bố cột trong từng hàng (island trong từng species)|
|`crosstab(..., normalize="columns")`|mỗi cột tổng $1$: phân bố hàng trong từng cột (species trên từng island)|
|`z.mean()`, `z.median()`, `z.std()`, `z.quantile(.75) - z.quantile(.25)`|bốn tóm tắt số|

Nguyên tắc: lập luận thống kê có trước, mã lệnh chỉ để xác nhận.

## 8. Ghi nhớ cuối

- Loại biến + câu hỏi quyết định cách tóm tắt.
- Với tỉ lệ, mẫu số là một phần của câu hỏi.
- Mối liên hệ mô tả không phải nhân quả.
- Trung bình/SD nhạy với cực trị hơn trung vị/IQR.
- Cùng trung bình và SD không có nghĩa cùng phân phối.
- Trung bình là nghiệm của bài toán tối thiểu hóa mất mát bình phương:

$$\bar{x} = \arg\min_{c}\sum_{i=1}^{n}(x_i - c)^2$$

- Tuần 03 sẽ học cách xây dựng biểu đồ (thuộc tính hình ảnh, hình học biểu diễn) và điều kiện hóa để so sánh nhóm.

Nếu cần, mình có thể làm bộ câu hỏi trắc nghiệm hoặc flashcard cho phần này.