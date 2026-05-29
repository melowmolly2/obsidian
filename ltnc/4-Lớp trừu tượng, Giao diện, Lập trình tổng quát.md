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
		Shape(int _x, int _y){
			x=_x;
			y=_y;
		}
	}
	class Circle extends Shape {...}
	Shape s = new Shape(10,10);
	//compile errỏr
	Shape s1 = new Circle();
	```
## Phương thức trừu tượng
- Để thống nhất giao diện, có thể khai báo các phương thức trừu tượng (abstract method) tại lớp cơ sở và cài đặt chi tiết tại các lớp dẫn xuất
	- Các lớp dẫn xuất cài đặt các phiên bản khác nhau của phương thức trừu tượng được kế thừa
- Phương thức trừu tượng
	- $\rightarrow$ Bắt buộc phải định nghĩa lại tại lớp dẫn xuất
![](../Assets/Pasted%20image%2020260529174740.png)
## Phương thức khuôn mẫu - template method
![](../Assets/Pasted%20image%2020260529174807.png)
## Giao diện - `interface`
- `interface` là mức trừu tượng cao
- `interface`