BÁO CÁO CÁ NHÂN: SỬ DỤNG TRÍ TUỆ NHÂN TẠO CÓ TRÁCH NHIỆM VÀ ĐẠO ĐỨC TRONG HỌC THUẬT

**Thông tin sinh viên:**

- **Họ và tên:** Phạm Thiên Minh
- **Trường:** Đại học Công nghệ - Đại học Quốc gia Hà Nội

### I. NGHIÊN CỨU CHÍNH SÁCH CỦA TRƯỜNG ĐẠI HỌC VỀ SỬ DỤNG AI

**1. Tóm tắt chính sách tại Trường Đại học Công nghệ (UET - VNU)** 
Nằm trong hệ thống Đại học Quốc gia Hà Nội, Trường Đại học Công nghệ (UET) đặt tiêu chuẩn rất cao về liêm chính học thuật. Dù chưa ban hành một bộ luật độc lập dành riêng cho Trí tuệ nhân tạo tạo sinh, nhà trường đã lồng ghép các nguyên tắc này vào quy chế đào tạo và đánh giá đạo đức sinh viên:

- **Thúc đẩy đổi mới sáng tạo:** UET là trường đào tạo mũi nhọn về công nghệ, do đó sinh viên được khuyến khích tiếp cận và sử dụng AI như một công cụ hỗ trợ để tìm kiếm tài liệu, gợi ý hướng giải quyết thuật toán, hoặc sửa lỗi cú pháp cơ bản trong lập trình.
- **Nghiêm cấm hành vi Đạo văn (Plagiarism) và Gian lận:** Sinh viên không được phép sử dụng AI để tạo ra toàn bộ mã nguồn (source code), bài luận hay đồ án rồi nhận là của mình. Mọi sản phẩm đánh giá phải là kết quả cốt lõi từ tư duy độc lập của sinh viên. Nếu phát hiện vi phạm, bài làm sẽ bị hủy kết quả.

**2. Phân tích và so sánh** 
So với chính sách của một số trường đại học quốc tế (nơi quy định rạch ròi đến mức AI chỉ được dùng ở khâu nào trong quy trình phát triển phần mềm), quy định hiện tại của UET và ĐHQGHN nói chung mang tính định hướng nguyên tắc.

- _Nhận định cá nhân:_ Cách tiếp cận của UET là hoàn toàn phù hợp với thực tiễn ngành kỹ thuật. Thay vì cấm đoán cực đoan—điều bất khả thi đối với sinh viên IT—trường hướng sinh viên đến việc làm chủ công nghệ. AI được xem như một "Co-pilot" (Trợ lý lái phụ), nhưng sinh viên bắt buộc phải là người nắm vô lăng, kiểm duyệt logic và chịu trách nhiệm 100% về độ chính xác, an toàn của sản phẩm đầu ra.

### II. THỰC HIỆN NHIỆM VỤ HỌC TẬP VỚI SỰ HỖ TRỢ CỦA AI

**1. Nhiệm vụ:** Tìm hướng chứng minh và tổng hợp tài liệu cho bài tập Giải tích liên quan đến bất đẳng thức giá trị tuyệt đối.

**2. Quá trình thực hiện & Ghi nhận Prompt:**
- **Công cụ sử dụng:** Google Gemini
- **Prompt đã sử dụng:** _"Hãy đóng vai một giáo sư Toán học. Gợi ý cho tôi các bước logic để chứng minh một số bất đẳng thức chứa giá trị tuyệt đối liên quan đến hàm số f(x) và f(0), áp dụng tính chất của khoảng cách."_
- **Đầu ra của AI (Trích đoạn):** _"Dựa trên bất đẳng thức tam giác, ta có thể thiết lập mối quan hệ giữa các giá trị của hàm số. Một trong những suy luận phổ biến là: $|f(x) - f(0)| \ge |f(x)| + |f(0)|$..."_

**3. Đánh giá, Chỉnh sửa và Tích hợp:**

Ngay khi đọc đầu ra của AI, tôi nhận thấy một **lỗi sai toán học nghiêm trọng về chiều của bất đẳng thức**. AI đã bị ảo giác (hallucination) khi đảo ngược logic của bất đẳng thức tam giác.
- _Cách chỉnh sửa:_ Tôi đã loại bỏ hoàn toàn suy luận sai lệch này của AI. Tôi tự phân tích và lập luận lại trên giấy nháp, sau đó đính chính lại công thức chuẩn xác là: **$|f(x)| + |f(0)| \ge |f(x) - f(0)|$**.
- _Tích hợp:_ Tôi chỉ sử dụng phần giải thích khái niệm mở đầu của AI, còn toàn bộ các bước biến đổi công thức và kết luận logic đều do tôi tự xây dựng dựa trên nguyên lý toán học chuẩn xác.
    

**4. Trích dẫn minh bạch:**

Trong phần tài liệu tham khảo của bài tập, tôi ghi rõ:

> _"Tài liệu có sử dụng Google Gemini để hỗ trợ tổng hợp lý thuyết cơ bản về bất đẳng thức tam giác (Ngày truy cập: [Ngày/Tháng/Năm]). Toàn bộ các bước chứng minh toán học và hiệu chỉnh công thức do tác giả tự thực hiện."_

### III. PHÂN TÍCH CÁC VẤN ĐỀ ĐẠO ĐỨC TRONG HỌC THUẬT

**1. Ranh giới giữa hỗ trợ hợp lý và gian lận học thuật**

Ranh giới này vô cùng mong manh. Hỗ trợ hợp lý là khi tôi dùng AI để gỡ rối một đoạn code Java bị lỗi (debug) hoặc tìm một bài báo khoa học. Gian lận là khi tôi yêu cầu AI viết toàn bộ một cấu trúc database hoặc chứng minh một định lý Toán học rồi copy-paste nguyên si nộp cho giảng viên. Sự khác biệt nằm ở **"Quyền tác giả" (Authorship)**. Nếu sinh viên không thể giải thích được quy trình logic đằng sau sản phẩm của mình, đó là gian lận.

**2. Vấn đề về quyền sở hữu trí tuệ và trích dẫn**

Các mô hình ngôn ngữ lớn được huấn luyện dựa trên hàng terabyte dữ liệu, bao gồm cả sách, bài báo và mã nguồn có bản quyền. Khi AI xuất ra một đoạn văn hay một khối lệnh tối ưu hóa luồng (multithreading), nó không hề trích dẫn nguồn gốc. Nếu sinh viên sử dụng mà không nhận thức được điều này, chúng ta đang gián tiếp vi phạm bản quyền và đánh cắp chất xám của các nhà nghiên cứu đi trước.

**3. Tác động đến quá trình học tập và phát triển kỹ năng**

Việc lạm dụng AI tạo ra "sự xói mòn kỹ năng" (Skill Degradation). Trong khối ngành kỹ thuật, việc chật vật suy nghĩ để giải một bài toán rời rạc hay tìm ra nguyên nhân của một lỗi logic (logical bug) chính là cách não bộ hình thành các nơ-ron tư duy giải quyết vấn đề. Nếu giao phó hoàn toàn cho AI, sinh viên sẽ trở thành những "thợ gõ" thụ động, mất đi tư duy phản biện (critical thinking) và khả năng ứng phó khi hệ thống AI gặp sự cố.

### IV. BỘ NGUYÊN TẮC CÁ NHÂN (SỬ DỤNG AI CÓ TRÁCH NHIỆM)

Dựa trên các phân tích đạo đức trên, tôi tự xây dựng 6 nguyên tắc thực hành cho bản thân:

1. **AI là Trợ lý, không phải Tác giả (Assistant, not Author):** Chỉ dùng AI để lên dàn ý, tìm kiếm tài liệu hoặc kiểm tra lỗi (syntax/grammar). Bản nháp cuối cùng phải do chính tôi chấp bút.
2. **Nguyên tắc "Zero-Trust" (Kiểm chứng mọi thứ):** Không bao giờ tin tưởng tuyệt đối đầu ra của AI. Phải luôn đối chiếu các công thức, số liệu, và logic với giáo trình chính thống hoặc tài liệu học thuật (như cách tôi đã sửa lỗi bất đẳng thức ở phần II).
3. **Minh bạch và Trích dẫn đầy đủ:** Luôn khai báo rõ ràng phần nào của dự án/bài tập có sự can thiệp của công cụ tạo sinh bằng các chuẩn trích dẫn (APA/IEEE).
4. **Bảo mật thông tin:** Không nhập các dữ liệu chưa được công bố, đề thi bảo mật, hoặc mã nguồn nội bộ vào các chatbot AI công cộng để tránh rò rỉ chất xám.
5. **Bảo vệ tư duy phản biện:** Đặt ra quy tắc "Suy nghĩ 15 phút": Chỉ tìm đến AI khi đã tự tư duy và thử giải quyết vấn đề ít nhất 15 phút mà không có kết quả.
6. **Tuân thủ tuyệt đối quy chế:** Luôn hỏi ý kiến giảng viên phụ trách môn học về giới hạn sử dụng AI trước khi bắt đầu bất kỳ đồ án nào.

### V. INFOGRAPHIC MINH HỌA: "SỬ DỤNG AI CÓ TRÁCH NHIỆM TRONG HỌC THUẬT"
![](Assets/infographic-min_1780495090.png)

