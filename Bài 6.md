BÁO CÁO CÁ NHÂN: SỬ DỤNG TRÍ TUỆ NHÂN TẠO CÓ TRÁCH NHIỆM VÀ ĐẠO ĐỨC TRONG HỌC THUẬT

**Thông tin sinh viên:**

- **Họ và tên:** Phạm Thiên Minh
    
- **Trường:** Đại học Bách khoa Hà Nội (HUST)
    

### I. NGHIÊN CỨU CHÍNH SÁCH CỦA TRƯỜNG ĐẠI HỌC VỀ SỬ DỤNG AI

**1. Tóm tắt chính sách tại Đại học Bách khoa Hà Nội (HUST)**

Đại học Bách khoa Hà Nội luôn đề cao tính liêm chính học thuật (Academic Integrity). Trước sự bùng nổ của AI tạo sinh (GenAI), dù chưa có một bộ luật độc lập hoàn toàn tách biệt, HUST đã tích hợp các quy định về AI vào quy chế đào tạo và chuẩn mực đạo đức sinh viên. Các điểm cốt lõi bao gồm:

- **Khuyến khích ứng dụng đổi mới:** Sinh viên được phép sử dụng AI như một công cụ hỗ trợ tìm kiếm tài liệu, gợi ý ý tưởng (brainstorming), hoặc sửa lỗi ngữ pháp cơ bản.
    
- **Nghiêm cấm đạo văn do AI tạo ra (AI Plagiarism):** Việc sử dụng AI để tạo ra toàn bộ hoặc một phần đáng kể (core content) của bài tập, đồ án, tiểu luận mà không có sự đóng góp cá nhân và không trích dẫn nguồn sẽ bị coi là gian lận học thuật. Mọi sản phẩm nộp lên phải là kết quả của tư duy độc lập.
    

**2. Phân tích và so sánh**

So với chính sách của một số trường đại học công nghệ lớn trên thế giới (như MIT hay Stanford) - nơi quy định rõ ràng từng công đoạn được dùng AI (được dùng để debug code nhưng không được dùng để viết logic thuật toán cốt lõi) - quy định hiện tại ở Việt Nam vẫn mang tính nguyên tắc chung.

- _Nhận định cá nhân:_ Chính sách của HUST là một hướng tiếp cận "mở" và phù hợp với thực tiễn khối ngành kỹ thuật. Khác với việc cấm đoán cực đoan, trường hướng sinh viên đến mô hình "Centaur" (Nửa người nửa máy) – nơi con người giữ vai trò định hướng và chịu trách nhiệm, còn máy móc tăng tốc độ xử lý vật liệu thô.
    

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

_(Ghi chú cho việc nộp bài: Dưới đây là bản thiết kế nội dung chi tiết. Bạn có thể sử dụng Canva, chọn một template "Process Infographic" hoặc "Rules Infographic" và điền nội dung này vào để xuất thành file ảnh đính kèm vào báo cáo)._

**[Chèn Infographic tại đây]**

- **Tiêu đề chính (Chữ to, in đậm, trung tâm):** 6 BƯỚC SỬ DỤNG AI CÓ TRÁCH NHIỆM TRONG HỌC THUẬT
    
- **Màu sắc chủ đạo:** Xanh dương (thể hiện sự công nghệ, học thuật) và Vàng/Cam (thể hiện sự cảnh báo, tư duy).
    
- **Cấu trúc 3 trụ cột chính (Chia làm 3 cột hoặc 3 khối hình học):**
    
    - **Khối 1: TƯ DUY (Biểu tượng não bộ)**
        
        - _Nội dung:_ Tự suy nghĩ trước khi hỏi (Quy tắc 15 phút). AI là trợ lý đồng hành, tư duy cốt lõi phải là của bạn.
            
    - **Khối 2: KIỂM CHỨNG (Biểu tượng kính lúp/dấu tick)**
        
        - _Nội dung:_ Nguyên tắc Zero-Trust. Luôn kiểm tra chéo (Cross-check) mọi thuật toán, trích dẫn, công thức toán học do AI tạo ra. Chống "ảo giác AI".
            
    - **Khối 3: MINH BẠCH (Biểu tượng dấu ngoặc kép trích dẫn)**
        
        - _Nội dung:_ Tôn trọng bản quyền. Trích dẫn rõ ràng tên công cụ, câu lệnh (prompt) và phạm vi sử dụng trong phần Tài liệu tham khảo.
            
- **Phần footer (Dưới cùng):**
    
    - _Slogan:_ "Công nghệ nâng bước tư duy - Liêm chính kiến tạo giá trị."
        
    - _Tên tác giả:_ Phạm Thiên Minh.