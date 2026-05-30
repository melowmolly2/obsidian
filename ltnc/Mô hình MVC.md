## MVC (Model - View - Controller)
- Ứng dụng quá lớn, khó bảo trỉ, tái sử dụng, làm việc nhóm
- Giải pháp: "chia để trị" với MVC
- MVC là một trong những mẫu kiến trúc phổ biến nhaasts cho ứng dụng Web
![](../Assets/Pasted%20image%2020260530102910.png)
- Lợi ích:
	- Tách biệt mối quan tâm về nghiệp vụ cho các thành phần
	- Tăng khả năng bảo trì và mở rộng
	- Song song hóa quá trình phát triển
	- Tái sử dụng mã nguồn
## Các thành phần trong MVC
- Model: 
	- Các lớp liên quan đến dữ liệu
	- Phần logic tương tác đến lưu trữ dữ liệu
- View: 
	- Hiển thị giao diện đến người dùng
	- Xử lý việc hiển thị dữ liệu
- Controller: 
	- Xử lý các tương tác với View và Model
## Ví dụ: MVC
![](../Assets/Pasted%20image%2020260530103102.png)
![](../Assets/Pasted%20image%2020260530103120.png)

# Serialization và lưu trữ dữ liệu \[Model\] 
## Làm sao để lưu trữ dữ liệu?
Chuyển đổi dữ liệu dạng text để lưu trữ vào file
![](../Assets/Pasted%20image%2020260530103249.png)
![](../Assets/Pasted%20image%2020260530103301.png)
## Serialization (tuần tự hóa)
Serialization đơn giản là quá trình chuyển đổi đối tượng Java thành dạng dữ liệu có thể truyền hoặc lưu trữ
![](../Assets/Pasted%20image%2020260530103341.png)
Lợi ích:
- Đọc và ghi một đối tượng thông qua I/O streams
- Đối tượng có thể được ghi vào file, truyền qua mạng network hoặc database, v.v.
- Dễ dàng import ngược lại
- Giảm thiểu sai sót khi chuyển đổi dữ liệu sang dạng văn bản
- 