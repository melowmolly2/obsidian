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
- `interface` bao gồm:
	- Phương thức trừu tượng - abstract method
	- Hằng số: mặc định là `public static final`
	- Mặc định là `public` 
- Từ khóa ; `interface` và `implements`
	```Java
	interface Config {
		int MAX_CONN = 20;
		void display(); //it will be public
	}
	```
## Các giao diện kế thừa
![](../Assets/Pasted%20image%2020260529175024.png)
## Giao diện khai báo như 1 kiểu dữ liệu 
![](../Assets/Pasted%20image%2020260529175132.png)
## Interface - "Hợp đồng lập trình" 
```Java
// 1. The Contract: Defines the "What"
public interface PaymentProcessor {
    void process(double amount);
}

// 2. The Implementation: Defines the "How"
public class StripeProcessor implements PaymentProcessor {
    public void process(double amount) { /* Stripe-specific logic */ }
}

// 3. The Durable Consumer: Only cares about the Contract
public class CheckoutService {
    private final PaymentProcessor processor; // Composition: "Has-a" processor

    // Dependency Injection: Inject any class that honors the contract
    public CheckoutService(PaymentProcessor processor) {
        this.processor = processor;
    }

    public void completePurchase(double total) {
        processor.process(total); // No "hidden" parent logic can break this
    }
}
```
# Lập trình tổng quát
## Định nghĩa
- Lập trình tổng quát (generic programming) là một dạng lập trình máy tính trong đó:
	- Khi định nghĩa lớp/giao diện/phương thức, kiểu dữ liệu không cần xác định tường minh
	- Khi sử dụng lớp/giao diện/phương thức, những kiểu dữ liệu không tường minh sẽ phải xác định rõ kiểu
- Để cho đơn giản
	- Lớp/giao diện/phương thức được lập trình tổng quát gọi tắt là lớp/giao diện/phương thức tổng quát
- Java hỗ trợ 3 loại tổng quát
	- Lớp tổng quát (generic class)
	- Giao diện tổng quát (generic interface)
	- Phương thức tổng quát (generic method)
# Lớp tổng quát
## Cấu trúc
- Lớp tổng quát được viết với cấu trúc như sau:
	```Java
	class name<T1, T2, ..., Tn> {/* ... */}
	```
	-