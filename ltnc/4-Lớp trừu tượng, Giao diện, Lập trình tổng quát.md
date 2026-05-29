## Lớp trừu tượng - abstract class
- Có thể tạo ra các lớp cơ sở (khuôn mẫu) để lớp dẫn xuất kế thừa ==mà không tạo ra các đối tượng== thực của lớp
	- i.e. lớp Dog, Cat, Cow... kế thừa từ lớp Animal, Rectangle, Circle,... kế thừa từ lớp Shape
	- Thực tế không có đối tượng nào là Animal, Shape, ...
- Khai báo lốp trừu tượng - abstract class
	- Không thể tạo ra đối tượng
	- Xây dựng lớp khuôn mẫu với các thuộc tính và hành vi mà các lớp dẫn xuất bắt buộc phải có
	```Java
	abstract class Shape{
		protected int x,y;
		Shape(int x)
	}
	```
## Phương thức trừu tượng
- Để thống nhất giao diện, có thể khai báo các phương thức trừu tượng (abstract method) tại lớp cơ sở và cài đặt chi tiết tại các lớp dẫn xuất
	- Các lớp dẫn xuất cài đặt các phiên bản khác nhau của phương thức trừu tượng được kế thừa
- Phương thức trừu tượng
	- $\rightarrow$ Bắt buộc phải định nghĩa lại tại lớp dẫn xuất
	- 