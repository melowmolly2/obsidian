## Tổng quan
- Câu trả lời cho câu hỏi "làm thế nào để tôi có thể..." khi xây dựng phần mềm
- MTK là những giải pháp đã được sử dụng trong các phần mềm khác nhau và xem là tốt nhất (best practice)
- Mốc quan trọng: 1995, Gang of Four (GoF) Gamma, Helm, Johnson, và Vlissides; Design Patterns: Elements of Reusable Object-Oriented Software, Addison Wesley, 1995.
- MTK giải quyết các vấn đề phi chức năng:
	- Khả năng thay đổi
	- Khả năng tương tác
	- Khả năng tái sử dụng
	- Đổ tin cậy
- Có 3 loại MTK:
	- Khởi tạo (creational): liên quan đến khởi tạo đối tượng
	- Cấu trúc (structural): liên quan đến tổ chức lớp và đối tượng
	- Hành vi (behavioral): liên quan đến việc gán các chức năng cho lớp
## Nội dung chính của một MTK
- Tên: tên của MTK, thường có nghĩa để người dùng dễ hình dung; Ví dụ: Bridge, Mediator, Flyweight
- Ngữ cảnh: ngữ cảnh để áp dụng MTK, ví dụ
- Vấn đề giải quyết: dự định của MTK, mục tiêu (trong điều kiện ràng buộc)
- Giải pháp: các lớp, đối tượng và mối quan hệ giữa các phần từ được đề xuất
- Kết quả: thảo luận về kết quả mang lại của MTK
## Singleton
- Ngữ cảnh: Trong một số ứng dụng, việc chỉ có duy nhất một đối tượng (của một lớp đặc biệt nào đó) được tạo ra là rất quan trọng. Ví dụ: kết nối DB, Window manager, file system, ... 
- Vấn đề: Làm thế nào để chúng ta có thể đảm bảo chỉ duy nhất 1 đối tượng thuộc một lớp nào đó được tạo ra?
- Giải pháp:
	- Lớp có phương thức khởi tạo là `private`
	- Phương thức `getInstance()` được sử dụng để tạo đối tượng
	- Trong lần gọi đầu tiên, phương thức `getInstance()` này sẽ tạo ra một đối tượng
	- Trong những lần gọi tiếp theo, `getInstance()` không tạo thêm đối tượng mà chỉ trả về đối tượng đã tạo ra
- Smell: Global Data/Mutable State
	- Scattered global variables or multiple instances of a resource (like a database connection) can lead to data races and unpredictable behavior. 
- 