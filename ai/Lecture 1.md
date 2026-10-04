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
- **ImageNet:** lỗi phân loại ảnh của hệ thống tốt nhất giảm từ 26% (2011) xuống 3.1% (2016), thấp hơn con người.
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

| |Giống con người|Lý trí (rational)|
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

## 5. Lịch sử AI 

## Dòng thời gian tóm tắt

|Giai đoạn|Tên|Nội dung chính|
|---|---|---|
|1950|Turing Test|Alan Turing đặt vấn đề máy có hành xử thông minh được không|
|1956|AI ra đời|Hội thảo mùa hè Dartmouth đặt tên "AI"|
|1952-1969|Giai đoạn hào hứng (enthusiasm)|Máy tính làm được "X", nhưng nhiều bài toán chỉ là bài toán đồ chơi|
|1966-1973|Va chạm thực tế (reality)|Gặp ba giới hạn lớn, nhiều khoản tài trợ bị cắt|
|1969-1988|Hệ chuyên gia (expert systems)|Thêm tri thức chuyên ngành để dẫn dắt tìm kiếm|
|1988 trở đi|Mùa đông AI (AI winter)|Bong bóng hệ chuyên gia vỡ|
|1986 trở đi|Mạng nơ-ron (neural nets)|Perceptron nhiều lớp và lan truyền ngược|
|2000 đến nay|Thống kê (stat)|Học máy truyền thống, khai phá dữ liệu|
|2010 đến nay|Học sâu và LLM|Deep Learning, Large Language Models|

## Chi tiết từng giai đoạn

**1950: Turing Test**

- Câu hỏi đổi từ "Máy có biết nghĩ không?" thành "Có phân biệt được máy với người qua hội thoại không?".
- Hình thức: văn bản vào, văn bản ra (text in / text out). Chatbot minh họa là A.L.I.C.E.
- Bài báo gốc: Turing (1950), _Computing machinery and intelligence_, Mind, 59, 433-460. Bài này còn nhắc tới thuật toán di truyền và nhân bản người.

**1956: Hội thảo Dartmouth**

- Đây là lúc **tên gọi "AI" xuất hiện**.
- Các nhân vật lớn: John McCarthy, Marvin Minsky, Claude Shannon, Nathaniel Rochester, Trenchard More, Arthur Samuel, Ray Solomonoff, Oliver Selfridge, Allen Newell, Herbert Simon.
- Giới nghiên cứu **chưa có đồng thuận** về AI là gì.

**1952-1969: Hào hứng ban đầu**

- Máy tính làm được: giải câu đố, chứng minh định lý hình học, chơi cờ đam (checkers), Lisp, thế giới khối (block world), ELIZA, perceptron.
- Hạn chế: nhiều thành tựu chỉ là **toy problems** (bài toán đồ chơi).

**1966-1973: Va chạm thực tế**

- **Cú pháp mà không có tri thức miền thì không hiệu quả.** Ví dụ dịch máy: câu "The spirit is willing but the flesh is weak" (Anh → Nga → Anh) bị dịch thành "The vodka is good but the meat is rotten". Chính phủ Mỹ cắt tài trợ cho dịch máy.
- **Bùng nổ tổ hợp (intractability):** độ phức tạp hàm mũ. Chính phủ Anh ngừng hỗ trợ AI dựa trên **báo cáo Lighthill**.
- **Giới hạn lý thuyết:** perceptron không giải được hàm **XOR**, nên nghiên cứu mạng nơ-ron bị đình trệ.

**1969-1988: Hệ thống dựa trên tri thức**

- Thêm tri thức chuyên ngành để dẫn dắt tìm kiếm.
- **CYC:** mô tả thế giới bằng hàng triệu luật.
- **Hệ chuyên gia** được thương mại hóa trong thập niên 80: mỗi công ty lớn của Mỹ có một nhóm AI, thành ngành công nghiệp trị giá hàng tỷ đô la.

**Từ 1988: Mùa đông AI**

- Các nhà đầu tư mạo hiểm rót vốn ồ ạt và các lời hứa quá mức.
- Bong bóng vỡ: nguồn vốn cho AI cạn, các công ty AI sụp đổ.

**Từ 1986: Mạng nơ-ron**

- Perceptron nhiều lớp (multi-layer perceptron) và thuật toán lan truyền ngược (back-propagation) được tái khám phá.
- Cuộc tranh luận giữa các trường phái:
    - **Connectionists** (mạng nơ-ron);
    - **Symbolic models** (Newell, Simon);
    - **Logicist** (McCarthy).
- Bản chất thật của hướng này là **học máy thống kê**.

**2000 đến nay: Thống kê**

- Học máy với các mô hình truyền thống: HMM, SVM, Gaussian processes, mô hình đồ thị (mạng Bayes, CRF).
- Khai phá dữ liệu (data mining).
- Từ **2010**: học sâu và mô hình ngôn ngữ lớn.

## Cách nhớ nhanh

Lịch sử AI đi theo chu kỳ **kỳ vọng cao rồi thất vọng**:

$$\text{hào hứng (50-60s)} \to \text{thực tế phũ phàng (66-73)} \to \text{hệ chuyên gia (70-80s)} \to \text{AI winter (1988)} \to \text{thống kê} \to \text{học sâu / LLM}$$

Ba nguyên nhân khiến giai đoạn đầu thất bại, hay được hỏi: thiếu tri thức miền, độ phức tạp hàm mũ, và giới hạn lý thuyết của perceptron (XOR).

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
- Nhớ các cột mốc: AlphaGo (2016), ImageNet (26% $\to$ 3.1%), ChatGPT (11/2022), DeepSeek-R1 (1/2025).
- Nắm rõ chính sách dùng AI sinh văn bản và cách tính điểm của môn.



