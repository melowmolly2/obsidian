Đây là phần cần nhớ của **Bài 1: Giới thiệu Trí tuệ nhân tạo**, 55 slide. Các slide về lịch sử AI (42-48) và các slide về lĩnh vực ứng dụng (37-41) chỉ là hình ảnh nên mình chưa đọc được nội dung. Bạn nên tự xem lại các slide đó.

## 1. Thông tin môn học (INT3401E)

- Giảng viên: TS. Lê Đức Trọng, Khoa CNTT, VNU-UET.
- Nội dung môn: tác tử (agents), tìm kiếm, giải quyết vấn đề, logic, biểu diễn tri thức, suy diễn, học máy, MDP, học tăng cường.
- Điều kiện tiên quyết: nguyên lý lập trình, toán rời rạc, thiết kế phần mềm. Bài tập lập trình **bắt buộc dùng Python**.
- Chấm điểm: 30% (giữa kỳ + bài tập) + 10% chuyên cần + **60% cuối kỳ**.
- Tài liệu chính: AIMA (Russell & Norvig), CS221 (Stanford), giáo trình của Đinh Mạnh Tường và Từ Minh Phương.

**Quy định học thuật:**

- Được thảo luận nhưng bài làm phải là của cá nhân.
- Cấm chia sẻ hoặc sao chép code. Code lấy từ sách hoặc thư viện phải ghi rõ nguồn.
- **Được dùng AI sinh văn bản (ChatGPT, Gemini, …) như một cộng tác viên**, nhưng:
    - không được hỏi trực tiếp lấy đáp án hoặc chép lời giải;
    - phải ghi nhận việc dùng và viết một đoạn mô tả cách dùng;
    - dùng AI để hoàn thành phần lớn bài hoặc bài thi là vi phạm quy chế.

## 2. Vì sao học AI

Quan hệ bao hàm: Artificial Intelligence ⊃ Machine Learning ⊃ Deep Learning / Generative AI.

**Một số cột mốc nổi bật:**

- **AlphaGo:** tháng 3/2016 thắng kỳ thủ cờ vây Lee Sedol (Hàn Quốc) với tỉ số 4-1. Năm 2017, **AlphaGo Zero** thắng AlphaGo gốc với tỉ số 100-0.
- **ImageNet:** lỗi phân loại ảnh của hệ thống tốt nhất giảm từ $26%$ (2011) xuống $3.1%$ (2016), thấp hơn con người.
- **ChatGPT:** OpenAI ra mắt tháng 11/2022, dựa trên GPT-3 (kiến trúc transformer, 175 tỷ tham số, ngữ cảnh 2048 token). Theo slide, đạt 10 triệu người dùng sau 40 ngày.
- **DeepSeek-R1:** ra mắt ngày 23/1/2025, là mô hình suy luận mã nguồn mở, tương tự o1 của OpenAI.
- **OpenClaw (2025-2026):**
    - Là AI Agent tự hành mã nguồn mở, điều khiển máy tính qua các ứng dụng nhắn tin (WhatsApp, Telegram, Zalo, Slack, Discord).
    - Biến "trợ lý ảo" thành "nhân viên ảo".
    - Đạt 100.000 sao trên GitHub ngày 30/1/2026.
- **Ở Việt Nam:** VinAI, FPT.AI, Viettel-AI, Zalo.AI. Các chương trình AI4Life, AI4VN. Slide cũng nhắc Chiến lược quốc gia về AI đến 2030, tầm nhìn 2045.

AI đang tác động tới trí tưởng tượng của công chúng, kinh tế và chính trị.

## 3. AI là gì

Định nghĩa trong slide: AI là khoa học và kỹ thuật tạo ra máy móc thông minh, thực hiện được các tác vụ mà khi con người làm thì đòi hỏi trí thông minh.

**Bốn cách nhìn về AI** (chia theo hai trục):

||Giống con người|Lý trí (rational)|
|---|---|---|
|**Suy nghĩ**|Thinking humanly|Thinking rationally|
|**Hành động**|Acting humanly|Acting rationally|

- Lưu ý của slide: con người không hoàn hảo, nên "lý trí" là một chuẩn khác "giống người".
- Ở bài sau, tác tử hợp lý (rational agent) là tác tử chọn hành động để cực đại hóa độ thỏa dụng kỳ vọng.

## 4. Alan Turing và Turing Test

- **Alan Turing** (1912-1954) là nhà toán học, logic học, giải mã và khoa học máy tính người Anh, được coi là cha đẻ của AI.
- Lịch sử AI bắt đầu từ bài báo _Computing Machinery and Intelligence_ (Mind, 1950).
- Turing đổi câu hỏi "Máy có biết nghĩ không?" thành "Máy có hành xử thông minh được không?". **Turing Test (Imitation Game)** là định nghĩa thao tác của trí thông minh.
- Để qua được Turing Test, máy cần 4 khả năng:
    1. Xử lý ngôn ngữ tự nhiên (NLP).
    2. Biểu diễn tri thức (knowledge representation).
    3. Suy diễn tự động (automated reasoning).
    4. Học máy (machine learning).

## 5. Lịch sử AI (giai đoạn gần đây)

- **2000 đến nay:** thống kê và học máy, với các mô hình truyền thống như HMM, SVM, Gaussian processes, mô hình đồ thị (mạng Bayes, CRF), cùng khai phá dữ liệu.
- **2010 đến nay:** học sâu và mô hình ngôn ngữ lớn (Deep Learning / LLM).

## 6. Đặc điểm của các bài toán AI

- Tác động xã hội lớn, ảnh hưởng tới hàng tỷ người.
- Đa dạng (ngôn ngữ, trò chơi, robot).
- Phức tạp, thực sự khó.

## 7. AI có trách nhiệm và AI đạo đức

- **Responsible AI:** hiểu, bảo vệ và kiểm soát dữ liệu, mô hình và quy trình để xây dựng giải pháp đáng tin cậy.
- **Ethical AI:** AI tuân theo các nguyên tắc đạo đức rõ ràng về giá trị cơ bản, gồm quyền cá nhân, quyền riêng tư, **không phân biệt đối xử** và **không thao túng**.

## 8. Các chủ đề của môn học

- **Giải quyết vấn đề bằng tìm kiếm:** tìm kiếm mù, tìm kiếm có thông tin, bài toán thỏa mãn ràng buộc (CSP).
- **Chơi trò chơi:** tìm kiếm đối kháng (adversarial search).
- **Biểu diễn tri thức:** logic mệnh đề, logic vị từ, cơ chế suy diễn, suy diễn xác suất.
- **Học máy:** Naive Bayes, mạng nơ-ron, học sâu, học tăng cường, xử lý ngôn ngữ tự nhiên và thị giác máy tính.
- **AI có trách nhiệm và AI đạo đức.**

## 9. Thông điệp tổng kết

- AI không có phép màu: đó là toán học, khoa học máy tính và cách khéo léo gắn chúng với bài toán thực tế.
- AI là lĩnh vực phát triển nhanh và thú vị.
- Ta có thể trực tiếp góp phần làm thế giới tốt đẹp hơn.

## Mẹo ôn thi

- Học thuộc **bốn cách nhìn về AI** và **bốn năng lực cần có để qua Turing Test**.
- Nhớ các cột mốc: AlphaGo (2016), ImageNet ($26% \to 3.1%$), ChatGPT (11/2022), DeepSeek-R1 (1/2025).
- Nắm rõ chính sách dùng AI sinh văn bản và cách tính điểm của môn.

Nếu bạn gửi ảnh chụp các slide lịch sử AI (42-48), mình sẽ bổ sung phần mốc thời gian. Mình cũng có thể làm bộ trắc nghiệm hoặc flashcard cho cả ba tuần.