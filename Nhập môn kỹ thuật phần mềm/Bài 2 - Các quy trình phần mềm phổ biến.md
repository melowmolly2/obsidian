# Các giai đoạn phát triển phần mềm truyền thống

Nội dung đầu tiên chúng ta tìm hiểu sẽ chỉ ra các giai đoạn trong công việc phát triển phần mềm truyền thống được trình bày trong bài học theo quan điểm của Barry Bohem bao gồm:
- Kỹ thuật yêu cầu
- Thiết kế 
- Thực hiện
- Xác minh và thẩm định
- Bảo trì
<iframe width="560" height="315" src="https://www.youtube.com/embed/9M_gr1W9HuU?si=AdCuuGASNNa0mfDW" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## 1. Kỹ thuật yêu cầu

**Kỹ thuật yêu cầu** là lĩnh vực liên quan đến xác định các yêu cầu của các bên liên quan mà sẽ được giải quyết bởi phần mềm

Tại sao giai đoạn này lại quan trọng? Bởi vì việc phát hiện lỗi càn muôn trong quá trình phát triển sẽ dẫn đến chi phí sửa chữa càng cao. Do đó, giai đoạn này có vai trò rất quan trọng để giảm rủi ro và chi phí phát sinh trong quá trình xây dựng hệ thống. 

Các bước có thể thu thập được yêu cầu phần mềm:
- **Khơi gợi yêu cầu** từ các bên liên quan và các nguồn khác
- **Phân tích yêu cầu**, bao gồm sự nghiên cứu và hiểu sâu hơn về các yêu cầu mang tính tập hợp
- **Đặc tả các yêu cầu**, trong đó các yêu cầu mang tính tập hợp được trình bày, tổ chức và lưu trữ phù hợp để có thể chia sẻ chung.
- **Xác thực các yêu cầu** để bảo đảm rằng chúng đã hoàn chỉnh, nhất quán, không dư thừa, thỏa mãn một tập hợp các thuộc tính quan trọng cho các yêu cầu. 
- **Quản lý yêu cầu**, để giải thích cho các thay đổi đối với các yêu cầu trong suốt vòng đời của dự án.
## 2. Thiết kế 

Thiết kế phần mềm là giai đoạn mà các yêu cầu phần mềm được phân tích để đưa ra một mô tả về cấu trúc và tổ chức bê ntrong của hệ thống. Và mô tả này sẽ là cơ sở cho cấu trúc của hệ thống thực. Một cách truyền thống, giai đoạn thiết kế phần mềm đưa ra một chuỗi các hoạt động thiết kế, bao gồm:
- Thiết kế kiến trúc
- Thiết kế giao diện
- Thiết kế thành phần
- Thiết kế thuật toán
- ...
Nếu chúng ta đọc các cuốn sách hay giáo trình khác nhau, các hoạt động thiết kế có thể được mô tả theo nhiều cách khác nhau. Ý tưởng cốt lõi và điểm quan trọng ở đây là chúng ta đi từ góc nhìn bao quát hơn về hệ thống (thiết kế kiến rúc) đến một góc nhìn hẹp hơn (thiết kế thuật toán). Và các hoạt động này dẫn đến một bộ các sản phẩm thiết kế mô tả các đặc điểm khác nhau của hệ thống. 
<iframe width="560" height="315" src="https://www.youtube.com/embed/ZEhYRLMEbVw?si=i2_PJpaNO0Czrtrf" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
## 3. Thực hiện phần mềm
Sau khi nhận được tài liệu thiết kế hệ thống, công việc được chia thành các mô-đun/đơn vị và công việc lập trình được bắt đầu. Trong giai đoạn này mã nguồn được tạo ra, do đó