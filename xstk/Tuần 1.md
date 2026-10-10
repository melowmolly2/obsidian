# Lý thuyết Tuần 1 cần nhớ (UET.MAT1052)

**Câu hỏi xuyên suốt:** _Ta có dữ liệu gì, và dữ liệu đó cho phép ta kết luận đến đâu?_

## 1. Chuỗi suy luận

Câu hỏi → Đơn vị và biến → Quá trình tạo dữ liệu → Dữ liệu → Phân tích → Khẳng định.

Dữ liệu không tự nhiên xuất hiện. **Quá trình tạo dữ liệu** gồm các quyết định: lấy ai/cái gì, đo bằng cách nào, đo bao nhiêu lần, có can thiệp hay chỉ quan sát, có gộp dữ liệu hay không. Muốn đánh giá một kết luận thì phải đi ngược chuỗi này.

## 2. Bốn loại khẳng định

|Loại|Mục tiêu|Mẫu câu|
|---|---|---|
|**Tóm tắt**|Mô tả các đơn vị _đã quan sát_|"Trong dữ liệu này, …"|
|**Tổng quát hóa**|Nói về _tập đơn vị rộng hơn_ dữ liệu|"Trong quần thể …, …"|
|**Nhân quả**|Thay đổi biến này _làm thay đổi_ biến kia (có can thiệp)|"Nếu thay đổi X, Y sẽ …"|
|**Dự đoán**|Đoán _một giá trị chưa biết_ của trường hợp cụ thể|"Biết X, ta đoán Y của trường hợp mới …"|

Cách phân biệt (không dựa vào từ khóa):

- Đối tượng của kết luận là ai/cái gì?
- Có nói về can thiệp không?
- Giá trị nào đang chưa biết?

Điểm dễ nhầm:

- Cùng một con số (ví dụ 70%) nhưng **phạm vi** khẳng định khác nhau thì loại khẳng định khác nhau.
- Tổng quát hóa và dự đoán đều "dùng dữ liệu cũ nói về điều chưa quan sát". Khác nhau ở đích: **đặc trưng của cả tập đơn vị** (tổng quát hóa) hay **giá trị của một đơn vị/trường hợp cụ thể** (dự đoán). Thời gian hiện tại/tương lai không phải tiêu chí.
- Có thể dự đoán tốt mà không chứng minh được nhân quả.

**Đọc khẳng định theo hai lớp** (với câu về mối liên hệ giữa hai biến):

1. _Phạm vi:_ mô tả dữ liệu đã quan sát hay tổng quát hóa ra ngoài?
2. _Vai trò của mối quan hệ:_ chỉ mô tả sự đi cùng nhau, dùng để dự đoán, hay tuyên bố nhân quả?

"Mối liên hệ" **không phải nhãn thứ năm**; nó vẫn có thể là tóm tắt hoặc tổng quát hóa tùy phạm vi. Và **mối liên hệ không phải bằng chứng tự động cho nhân quả**.

Ví dụ nhân quả vs liên hệ (GPA và giờ học): dữ liệu quan sát chỉ cho biết các sinh viên vốn học nhiều/ít khác nhau thế nào. Các yếu tố gây nhiễu có thể là năng lực nền, độ khó học phần, động cơ, sức khỏe, việc làm thêm, sai số tự báo cáo. Muốn kết luận nhân quả cần thay đổi **thiết kế thu thập dữ liệu** (có can thiệp, so sánh phù hợp), không chỉ đổi tên cột hay định dạng bảng.

**Bằng chứng cần tăng theo độ mạnh của khẳng định:**

- Tóm tắt: phép đo và xử lý dữ liệu đáng tin cậy.
- Liên hệ: mô tả/so sánh quan hệ; muốn nói rộng hơn cần cơ chế lấy mẫu phù hợp.
- Dự đoán: kiểm tra trên các trường hợp mới.
- Nhân quả: thiết kế tách được tác động khỏi các yếu tố khác.

Khi tổng quát hóa, luôn hỏi: **ai/cái gì có mặt trong dữ liệu và ai/cái gì bị bỏ ngoài** (ví dụ thú cưng không đăng ký ở Seattle). Mẫu ngẫu nhiên làm tổng quát hóa có cơ sở hơn; định lượng độ bất định thuộc Tuần 09.

## 3. Biến, giá trị, đơn vị quan sát

- **Biến:** đặc tính của một đơn vị có thể đo và ghi lại.
- **Giá trị:** kết quả cụ thể của biến trên một quan sát.
- **Đơn vị quan sát:** lớp đối tượng mà trên đó các biến được quan sát. Đơn vị quan sát **không phải là một biến**.

Ví dụ: `nganh_hoc` là biến, "Khoa học máy tính" là một giá trị, một sinh viên là đơn vị quan sát. `Title` là biến, "Iron Man" là một giá trị.

## 4. Phân loại biến

```
Biến
├── Biến số (độ lớn có ý nghĩa định lượng)
│     ├── Liên tục (giá trị trên khoảng của trục số thực)
│     └── Rời rạc (giá trị tách rời, thường là số đếm)
└── Biến phân loại (các mức/categories)
      ├── Danh nghĩa (không có thứ tự tự nhiên)
      └── Thứ bậc (có thứ tự tự nhiên)
```

**Cảnh báo quan trọng:** "được lưu bằng số" ≠ "biến số".

- `ma_sinh_vien = 24001234` là nhãn định danh, tức biến phân loại **danh nghĩa**.
- Thang 1–5 có thể là mức đánh giá (phân loại **thứ bậc**) hoặc số lỗi đếm được (biến số **rời rạc**). Phải biết ý nghĩa của thang.
- Tên cột cũng gây nhiễu: `number` trong `email50` lưu nhóm "không có / nhỏ / lớn", nên là phân loại thứ bậc.

**Ví dụ đã học:**

|Bộ dữ liệu|Biến|Loại|
|---|---|---|
|email50|`spam`|phân loại danh nghĩa (nhị phân)|
||`cc`, `image`|số rời rạc|
||`number`|phân loại thứ bậc|
|loan50|`term` (số tháng)|số rời rạc|
||`grade` (A–G)|phân loại thứ bậc|
||`state`|phân loại danh nghĩa|
||`interest_rate`|số (xử lý như liên tục)|
|Palmer penguins|`bill_length_mm`, `bill_depth_mm`, `flipper_length_mm`, `body_mass_g`|4 biến số liên tục|
||`island`, `species`, `sex`|3 biến phân loại danh nghĩa|

Một hàng có thể chứa đồng thời nhiều loại biến.

**Vì sao loại biến quan trọng:** nó định hướng cách ghi nhận, trực quan hóa, tóm tắt (phép toán nào có ý nghĩa) và mô hình hóa.

## 5. Khung dữ liệu (data frame)

- **Hàng = quan sát; cột = biến; ô = giá trị quan sát được.**
- Câu hỏi đầu tiên khi gặp bảng mới: **"Mỗi hàng đại diện cho điều gì?"**
- Số hàng/cột chỉ có ý nghĩa khi hiểu hàng/cột đại diện cho gì. Cùng số hàng, cột không đảm bảo cùng đơn vị quan sát.

**Một hàng không nhất thiết là "một người":** có thể là sinh viên–môn học–học kỳ, bộ pin × cảm biến × thời điểm, quốc gia–năm, khoản vay, thư điện tử…

**Mức chi tiết (granularity):**

- Đặc tính ở mức cao hơn (ví dụ `birth_year` của sinh viên) sẽ **lặp lại** trên nhiều dòng của cùng đơn vị. Muốn mỗi sinh viên một dòng thì cần một bảng khác ở mức sinh viên.
- **Chọn đơn vị quan sát và mức chi tiết sao cho mỗi hàng giữ đúng thông tin cần để trả lời câu hỏi.** Không có một cấu trúc hàng duy nhất tối ưu cho mọi câu hỏi (ví dụ so sánh các cảm biến cùng bộ pin cùng thời điểm cần mức bộ pin × cảm biến × thời điểm, còn tìm bộ pin có nhiệt độ trung bình cao nhất thì có thể gộp về một hàng/bộ pin).

## 6. Gộp dữ liệu làm thay đổi câu hỏi

Gộp dữ liệu (ví dụ từ server × time sang một hàng/máy chủ) không chỉ làm bảng ngắn hơn mà còn:

- **Mất thông tin:** vị trí theo thời gian, đỉnh bất thường, dao động trong từng máy.
- **Đổi đơn vị quan sát** và **đổi ý nghĩa** của đại lượng ("độ trễ trung bình" là trung bình giữa các phép đo hay giữa các máy chủ).
- Trung bình của các trung bình ≠ trung bình của mọi phép đo gốc khi số phép đo mỗi máy khác nhau. Cách đầu cho mỗi máy trọng số bằng nhau, cách sau cho máy nhiều phép đo trọng số lớn hơn.

## 7. Số hàng ≠ số đơn vị độc lập

- Một hàng là một quan sát **trong bảng**, nhưng không nhất thiết là một **đơn vị độc lập**.
- Một thiết bị đóng góp hàng nghìn phép đo lặp, các hàng cùng thiết bị thường liên hệ với nhau.
- Ví dụ: 100 thiết bị × 1.000 lần đo = 100.000 hàng, nhưng khi so sánh thiết bị loại A với loại B thì đơn vị cốt lõi là **100 thiết bị**.
- Số hàng vẫn hữu ích (ví dụ mô tả biến thiên theo thời gian) nhưng không đồng nghĩa với lượng thông tin độc lập. Nhiều hàng hơn **không** luôn cho bằng chứng mạnh hơn: số hàng không thay thế thiết kế lấy mẫu/đo lường và tính độc lập.
- Trước khi dùng ký hiệu $n$, phải nói rõ **đơn vị nào đang được đếm**, chẳng hạn $n_{\text{obs}} = 100,000$ và $n_{\text{devices}} = 100$.

## 8. Cầu nối Python/pandas

- Một biến trong bảng → `pandas.Series`; nhiều biến cùng đơn vị quan sát → `pandas.DataFrame`.
- Bốn thao tác đọc cấu trúc (cần nhớ **ý nghĩa**, không phải cú pháp):

|Lệnh|Ý nghĩa|
|---|---|
|`head()`|xem vài hàng đầu|
|`shape`|số hàng × số cột|
|`columns`|tên các biến|
|`dtypes`|kiểu lưu trữ phần mềm đang dùng|

- **`dtype` ≠ loại biến thống kê.** `dtype` cho biết cách phần mềm lưu dữ liệu (`int64`, `float64`, `object`…), còn loại biến phụ thuộc **ngữ nghĩa đo lường** và phép toán nào có ý nghĩa trên giá trị.
- `shape = (1200, 6)` chỉ cho biết 1.200 hàng, 6 cột; chưa cho biết 1.200 hàng đó có phải 1.200 đơn vị độc lập hay không.
- Các cột trong cùng DataFrame phải mô tả **cùng các đơn vị theo cùng chỉ mục (index)**, nếu không một hàng sẽ ghép giá trị của các đơn vị khác nhau và phá hỏng ý nghĩa khung dữ liệu.

## 9. Năm lầm tưởng cần phá

|Lầm tưởng|Sửa|
|---|---|
|Nhiều hàng hơn luôn cho bằng chứng mạnh hơn|Số hàng không thay thế thiết kế lấy mẫu/đo lường và tính độc lập|
|Cột nhìn như số thì là biến số|Mã định danh hoặc mức thứ bậc vẫn có thể lưu bằng số|
|Một hàng luôn là một quan sát độc lập|Một thiết bị có thể đóng góp hàng nghìn phép đo lặp|
|Liên hệ, dự đoán, nhân quả là như nhau|Trả lời các câu hỏi khác nhau, đòi hỏi bằng chứng khác nhau|
|`dtype` quyết định loại biến thống kê|`dtype` nói cách lưu; loại biến phụ thuộc ý nghĩa của giá trị|

## 10. Tóm tắt: bốn câu hỏi đầu tiên khi mở bộ dữ liệu mới

1. **Mỗi hàng đại diện cho gì?**
2. **Mỗi cột đo/ghi nhận điều gì?**
3. **Dữ liệu được tạo ra bằng cách nào?**
4. **Ta muốn dùng dữ liệu để đưa ra loại khẳng định nào?**

**Bản đồ khái niệm:** câu hỏi → đơn vị + biến cần đo → quá trình tạo dữ liệu → khung dữ liệu và mức chi tiết của hàng → phân tích → khẳng định hợp lệ.

**Bốn phân biệt cần giữ:**

1. tóm tắt ≠ tổng quát hóa;
2. mối liên hệ ≠ dự đoán ≠ nhân quả;
3. số hàng ≠ số đơn vị độc lập;
4. loại biến thống kê ≠ `dtype` phần mềm.

**Chuẩn bị Tuần 02:** ôn biến phân loại/biến số, hàng–cột–đơn vị–phép đo lặp, tóm tắt vs tổng quát hóa, và việc gộp dữ liệu làm mất thông tin. Tuần 02 chuyển sang câu hỏi "dữ liệu trông như thế nào?" (chọn bảng, đại lượng tóm tắt, biểu đồ phù hợp với từng loại biến).

Nếu bạn muốn, mình có thể tạo bộ câu hỏi trắc nghiệm hoặc flashcard để tự kiểm tra phần này.