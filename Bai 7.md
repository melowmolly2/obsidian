# BÁO CÁO CÁ NHÂN: ỨNG DỤNG CÔNG CỤ AI (CONSENSUS) TRONG TỔNG QUAN TÀI LIỆU KHOA HỌC

**Thông tin sinh viên:**
- **Họ và tên:** Phạm Thiên Minh
- **Mã sinh viên:** 25021887
- **Trường:** Đại học Công nghệ - ĐHQGHN (UET - VNU)
### I. CHỦ ĐỀ VÀ CÂU HỎI NGHIÊN CỨU
- **Chủ đề nghiên cứu:** Ứng dụng của Trí tuệ Nhân tạo (Machine Learning/Deep Learning) trong việc tối ưu hóa quy trình Tích hợp và Phân phối liên tục (CI/CD) và dự đoán lỗi phần mềm.
- **Đánh giá chủ đề:** Đây là một chủ đề hẹp, có tính chuyên sâu cao trong lĩnh vực Kỹ thuật Phần mềm. Việc tích hợp các mô hình học máy vào pipeline CI/CD (như GitHub Actions, Jenkins) để tự động hóa việc rà soát code Java, Spring Boot hay tối ưu hóa thời gian chạy Maven build đang là xu hướng nghiên cứu có tiềm năng ứng dụng thực tiễn rất lớn.
- **Câu hỏi nghiên cứu cốt lõi:** _Các mô hình học máy nào đang được sử dụng hiệu quả nhất để ưu tiên các ca kiểm thử (test case prioritization) và dự đoán sự thất bại của các bản build (build failure prediction) trong hệ thống CI/CD?_

### II. QUÁ TRÌNH TÌM KIẾM VÀ LỰA CHỌN TÀI LIỆU
- **Công cụ sử dụng:** Consensus (Công cụ AI chuyên tìm kiếm và trích xuất dữ liệu trực tiếp từ các bài báo khoa học đã qua bình duyệt - peer-reviewed).
- **Câu lệnh (Query) đã sử dụng:** _"Machine learning models for build failure prediction and test case prioritization in continuous integration"_
- **Kết quả:** AI đã quét qua cơ sở dữ liệu hàng triệu bài báo. Dựa trên tính năng lọc của Consensus (lọc bài báo từ năm 2021 trở lại đây, có trích dẫn cao), tôi đã chọn ra được **6 bài báo** (vượt yêu cầu 5 bài) có liên quan chặt chẽ nhất đến chủ đề hẹp đã chọn.
![](Assets/Pasted%20image%2020260604104217.png)

|

### IV. NHẬN XÉT VÀ PHÂN TÍCH TỔNG HỢP
Dựa trên kết quả trích xuất tự động từ công cụ Consensus và phân tích chéo 6 bài báo trên, tôi rút ra các kết luận sâu sắc sau:
1. **Sự dịch chuyển về công nghệ:** Đang có một sự chuyển dịch rõ rệt từ các mô hình học máy truyền thống (như SVM, Decision Trees ở các bài số 5, 6) sang các kiến trúc học sâu hiện đại (Deep Learning, Transformers ở bài số 3, 4) để xử lý dữ liệu phi cấu trúc như log file trong CI/CD.    
2. **Hiệu quả thực tiễn:** Việc ứng dụng AI giúp tiết kiệm rõ rệt tài nguyên điện toán (giảm 25% tài nguyên, 30% thời gian test). Điều này vô cùng hữu ích khi triển khai các dự án có kiến trúc vi dịch vụ (microservices) yêu cầu build/test liên tục.
3. **Thách thức cốt lõi:** Dù AI có độ chính xác cao, bài toán về tính minh bạch (Explainable AI - Bài số 3) và độ trễ do chi phí tính toán (Overhead - Bài số 1, 4) vẫn là những rào cản lớn nhất ngăn cản việc áp dụng 100% các mô hình này vào môi trường sản xuất thực tế.
4. **Đánh giá công cụ:** Consensus đã chứng minh được hiệu năng vượt trội trong việc tiết kiệm thời gian tổng quan tài liệu. Tính năng "Synthesize" của nó giúp tôi nhanh chóng nhìn thấy sự đồng thuận của giới khoa học về độ chính xác của mô hình Random Forest, thay vì phải đọc thủ công từng bản PDF hàng chục trang.