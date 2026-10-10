Mình đọc file Tuần 03 trước rồi tổng hợp lý thuyết cho bạn.Mình đã đọc hết 94 slide của Tuần 03 (Tóm tắt dữ liệu 2/3). Tuần này chuyển từ "chọn biểu đồ" sang "xây dựng biểu đồ", rồi học lọc, nhóm và điều kiện hóa.

## 1. Ngữ pháp đồ họa (Grammar of Graphics)

Một biểu đồ có thể "phân tích cú pháp" thành các thành phần:

$$\text{Biểu đồ} = \text{Dữ liệu} + \text{Ánh xạ} + \text{Dạng hình học} ;(+; \text{Nhóm / ô phân nhỏ khi cần})$$

**Ba quyết định cốt lõi:**

1. **Dữ liệu:** có đủ biến cần thiết để trả lời câu hỏi không? Biểu đồ không thể thêm một biến mà dữ liệu không có.
2. **Thuộc tính hình ảnh (ánh xạ):** để biến điều khiển một đặc trưng trực quan, như `x`, `y`, `color`, `alpha`, `size`, `shape`, `fill`.
3. **Dạng hình học:** quan sát được thể hiện bằng dấu hiệu nào.

|Dạng hình học|Nhấn mạnh|
|---|---|
|Điểm|từng quan sát; quan hệ hai biến số|
|Đường|diễn biến theo thứ tự có ý nghĩa|
|Cột|số đếm/tỉ lệ theo mức phân loại|
|Biểu đồ tần suất (histogram)|hình dạng phân phối một biến số|
|Biểu đồ hộp|trung tâm và độ phân tán theo nhóm|

**Nhóm / faceting:** dùng biến thứ ba để tô màu hoặc chia ô, và đây là một dạng trực quan của điều kiện hóa.

**Các điểm cần nhớ:**

- **Ánh xạ khác thiết lập.**
    - `aes(color="species")`: màu thay đổi theo dữ liệu, đó là ánh xạ.
    - `geom_point(color="steelblue")`: mọi điểm một màu cố định, đó là thiết lập.
- Đổi dạng hình học không đổi dữ liệu hay ánh xạ, chỉ đổi cách mã hóa và thông điệp. Ví dụ năm → x, số ca sinh → y: đường nhấn mạnh xu hướng liên tục, điểm làm rõ từng giá trị.
- Không có dạng hình học "tốt nhất trong chân không". Nhiều lớp hơn không phải lúc nào cũng tốt hơn: thêm lớp khi nó phục vụ câu hỏi, vì nhiều lớp làm chồng lấp và tăng tải thị giác.
- Dạng hình học phải hợp với **đơn vị quan sát** và câu hỏi, không chỉ hợp với kiểu dữ liệu của trục x. Ví dụ: không nối đường giữa các sinh viên khác nhau chỉ vì "năm học có thứ tự", vì làm vậy tạo ra một "quỹ đạo" mà dữ liệu không có. Biểu đồ hộp mới tóm tắt phân phối trong từng nhóm.

## 2. plotnine trong Python

```python
ggplot(penguins, aes(x="bill_length_mm", y="bill_depth_mm", color="species")) + geom_point()
```

Đọc mã theo ba câu hỏi: dữ liệu nào, ánh xạ nào, dạng hình học nào.

- Dòng thiếu giá trị ở biến được ánh xạ không được vẽ. Ví dụ penguins có 344 hàng nhưng chỉ 342 hàng đủ hai số đo mỏ.
- Việt hóa nhãn bằng `labs(x=..., y=..., color=...)`, không cần đổi tên biến. Tên biến là cấu trúc dữ liệu, còn nhãn là giao tiếp với người đọc.

## 3. Điều kiện hóa (theo nghĩa phân tích dữ liệu)

Điều kiện hóa là nghiên cứu $Y$ hoặc mối liên hệ $(X,Y)$ **trong** $Z = z$, bằng cách lọc, chia nhóm, so sánh cùng một thống kê giữa các nhóm, hoặc tách biểu đồ. Đây chưa phải xác suất có điều kiện, phần đó học ở Tuần 05.

- **Tỉ lệ biên:** gộp mọi nhóm rồi tính một tỉ lệ chung.
- **Tỉ lệ có điều kiện:** tính riêng trong từng nhóm.
- Một kết luận đúng ở mức biên không buộc phải đúng trong mọi nhóm.

**Lọc** giữ các hàng thỏa điều kiện: số hàng giảm, số cột không đổi. Ví dụ `msleep.query("log_bodywt > 12")` giữ $9$ hàng.

- `and` lấy giao, tập kết quả thường nhỏ hơn.
- `or` lấy hợp, tập kết quả lớn hơn hoặc bằng.
- Lọc hợp lệ khi tiêu chí xuất phát từ câu hỏi. Vấn đề là đổi tiêu chí sau khi xem kết quả để đạt kết luận mong muốn. Cần báo cáo rõ tập con đang phân tích.

## 4. Chuỗi xử lý và phép toán theo nhóm

Chuỗi xử lý: dữ liệu → lọc → sắp xếp → nhóm → tóm tắt → diễn giải. Mỗi bước phải trả lời được "làm thay đổi dữ liệu thế nào và vì sao cần cho câu hỏi".

- `.query()` giảm số hàng, `.sort_values()` chỉ đổi thứ tự.
- **Thứ tự thao tác có thể đổi câu hỏi.**
    - Lọc `sleep_total > 8` rồi đếm theo `vore` hỏi: "chế độ ăn nào có hơn $18$ loài ngủ trên $8$ giờ?".
    - Đếm theo `vore` rồi lọc `n > 18` hỏi: "chế độ ăn nào có hơn $18$ loài trong toàn bộ dữ liệu?".
- **Lọc hay nhóm:** hỏi về một nhóm cụ thể thì lọc rồi tóm tắt; hỏi cùng một phép tóm tắt cho mọi mức thì nhóm rồi tóm tắt.
- **`groupby(...).agg(...)`:** `dropna=False` giữ nhóm bị thiếu.
- **Trung bình của biến logic là một tỉ lệ**, vì `True`/`False` tương ứng $1$/$0$. Luôn kèm $n$ để không đánh đồng $100%$ từ $5$ quan sát với $100%$ từ hàng chục quan sát. Ví dụ `msleep` chia theo `vore`: insecti có $p=1.000$ nhưng chỉ $n=5$.
- Kiểm tra chéo "biểu đồ → dự đoán → tóm tắt số → diễn giải". Ví dụ Gentoo có độ sâu mỏ trung bình nhỏ nhất ($14.98$ so với $18.35$ của Adelie và $18.42$ của Chinstrap), khớp với cụm điểm nằm thấp trên trục y.

## 5. Nghịch lý Simpson

Ví dụ hai thuật toán (thành công / tổng):

|Độ khó|A|B|Cao hơn|
|---|---|---|---|
|Dễ|$\dfrac{81}{90}=90%$|$\dfrac{19}{20}=95%$|B|
|Khó|$\dfrac{1}{10}=10%$|$\dfrac{16}{80}=20%$|B|
|**Gộp**|$\dfrac{82}{100}=82%$|$\dfrac{35}{100}=35%$|**A**|

**Cơ chế:** tỉ lệ gộp là trung bình có trọng số của các tỉ lệ trong nhóm.

$$A: 0.90(0.90)+0.10(0.10)=0.82, \qquad B: 0.20(0.95)+0.80(0.20)=0.35$$

A xử lý $90%$ tác vụ dễ, B xử lý $80%$ tác vụ khó. Cơ cấu nhóm khác nhau có thể lấn át so sánh trong từng nhóm. Không có thông tin về cơ chế phân công tác vụ thì không kết luận nhân quả.

**Cách tự dựng nghịch lý:** chọn một nhóm tỉ lệ cao, một nhóm tỉ lệ thấp; trong mỗi nhóm đặt B nhỉnh hơn A; cho A nhận phần lớn quan sát từ nhóm dễ, B nhận phần lớn từ nhóm khó. Ví dụ: Dễ A $\dfrac{36}{40}$, B $\dfrac{19}{20}$; Khó A $\dfrac{1}{10}$, B $\dfrac{12}{50}$. Gộp được $A=\dfrac{37}{50}=74%$ và $B=\dfrac{31}{70}\approx 44.3%$.

**Nhóm ẩn trong biểu đồ phân tán:** nhìn gộp, tải cao đi cùng thông lượng cao, nhưng trong từng loại máy chủ, tải tăng lại đi cùng thông lượng giảm. Cần hỏi mối liên hệ đang xét ở mức biên hay trong từng nhóm, và tô màu hoặc tách ô theo biến thứ ba.

## 6. Tóm tắt gộp che mất cấu trúc

Penguins: $\dfrac{172}{342}\approx 50.3%$ cá thể trên $4000$ g. Điều kiện hóa theo loài:

|Loài|Trên 4000 g|Số có dữ liệu|Tỉ lệ|
|---|---|---|---|
|Adelie|$35$|$151$|$23.2%$|
|Chinstrap|$15$|$68$|$22.1%$|
|Gentoo|$122$|$123$|$99.2%$|

Kết luận "loài ít liên quan" không được hỗ trợ. Điều kiện hóa không "sửa số liệu", nó đổi câu hỏi từ toàn bộ dữ liệu sang từng nhóm.

Ví dụ khác: Chinstrap và Gentoo trong khoảng $40\text{–}50$ mm có cùng trung bình chiều dài mỏ ($46.52$) nhưng độ sâu mỏ khác rõ ($17.82$ so với $14.78$). Vì vậy một tóm tắt đơn biến có thể bỏ lỡ khác biệt, cần xem thêm biểu đồ hai chiều.

## 7. Đồ họa trung thực

Độ trễ tăng từ $100$ ms lên $104$ ms (tức $+4%$). Biểu đồ cột mã hóa giá trị bằng chiều dài cột, nên cắt trục tung ở $98$ ms làm $4$ ms chiếm phần lớn chiều cao hiển thị. Cách trung thực hơn: trục bắt đầu từ $0$ nếu dùng cột, hoặc dùng điểm/đường kèm nhãn trực tiếp "$+4\ \text{ms}=+4%$". Đúng số chưa đủ để đúng ấn tượng.

## 8. Ghi nhớ cuối

- Biểu đồ $=$ dữ liệu $+$ ánh xạ $+$ dạng hình học (và nhóm/ô phân nhỏ khi cần).
- Ánh xạ là biến điều khiển thuộc tính, thiết lập là giá trị cố định.
- Lọc giữ hàng thỏa điều kiện; nhóm đổi cách phép tóm tắt tiếp theo được áp dụng.
- Thứ tự thao tác có thể đổi câu hỏi mà mã trả lời.
- Tóm tắt biên và có điều kiện có thể cho kết luận rất khác; Simpson là trường hợp đảo chiều.
- Điều kiện hóa làm lộ cấu trúc bị trộn lẫn nhưng không tự chứng minh nhân quả, vì còn có thể có biến ẩn, nhóm hình thành có chọn lọc, và dữ liệu quan sát không tạo ra so sánh phản thực.
- Hai khẳng định bị bác bỏ: (A) "mối liên hệ ở toàn bộ dữ liệu phải cùng chiều trong mọi nhóm" (sai, có Simpson); (B) "điều kiện hóa làm liên hệ rõ hơn là chứng minh nhân quả" (sai).
- Quy trình tự kiểm tra: câu hỏi → dữ liệu → lọc/nhóm → tóm tắt → ánh xạ → dạng hình học → diễn giải.

**Tuần 04 sẽ học:** biểu đồ phân tán, hệ số tương quan, hồi quy tuyến tính đơn và đa biến.

Nếu cần, mình có thể làm bộ câu hỏi trắc nghiệm hoặc flashcard cho Tuần 02–03.