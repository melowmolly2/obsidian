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
- trong đó:
	- `T1, T2, ..., Tn` là các kiểu tổng quát
	- Kí hiệu `<>` được sử dụng để bọc lấy các kiểu tổng quát
- Khai báo/ Khởi tạo một đối tượng thuộc lớp tổng quát tương tự như các lớp không tổng quát, điểm khác biệt duy nhất là phải xác định tường minh kiểu tổng quát
## Quy ước đặt tên kiểu tổng quát
- E: Element
- K, V: Key, Value
- N: Number
- T: Type
- S, U, V, v..v: kiểu thứ 2, thứ 3, thứ 4, v.v
## Ví dụ
- Ví dụ 1: Tạo một lớp tổng quát `Box`, lớp này có một kiểu tổng quát `T`
	```Java
	public class Box<T> {
		private T t;
		public void set{T t} {this.t=t;}
		public T get() {return t;}
	}
	```
- Khai báo và khởi tạo một đối tượng thuộc lớp tổng quát `Box`, trong đó kiểu tổng quát `T` là lớp `Integer`
	```Java
	Box<Integer> integerBox = new Box<Integer>(); 
	```
- Ví dụ 2: Tạo lớp tổng quát `Pair` lưu `key` và `value`, trong đó `key` và `value` là hai kiểu tổng quát
	```Java
	public class Pair<K,V> {
		private K key;
		private V value; 
		public void setKey(K key){this.key=key;}
		public K getKey(){return key;}
	}
	```
- Khai báo và khởi tạo trong đó `Key` có kiểu `String,value` có kiểu `Integer` 
```Java
Pair<String,Integer> p1= new Pair<String,Integer>("Even", 8);
```
## Thừa kế lớp tổng quát
- Các cách để thừa kế lớp tổng quát
	- Chỉ định rõ rằng kiểu tổng quát của lớp tổng quát
		- Ví dụ: Xác định K là `String`, V là `Integer` khi định nghĩa lớp `ContactEntry`
		```Java
public class ContactEntry extends Pair <String, Integer>{...}
		```
	- Chỉ định rõ một phần trong các kiểu tổng quát
		- Ví dụ: Xác định K là `String` khi định nghĩa lớp `ContactEntry`
		```Java
public class ContactEntry<V> extends Pair <String, V>{...} 
		```
	- Giữ nguyên tất cả các kiểu tổng quát
	```Java
	public class ContactEntry<K,V> extends Pair <K,V>{...}
	```
	- Thêm tham số tổng quát
	```Java
	public class ContactEntry<K,V,T> extends Pair <K,V>{...}
	```
# Giao diện tổng quát
## Cấu trúc
- Tương tự như lớp tổng quát, giao diện tổng quát được viết với cấu trúc như sau:
	```Java
	interface name<T1, T2, ... ,Tn>{
	/* ... */
	}
	```
	, trong đó:
	- `T1, T2, ..., Tn` là các kiểu tổng quát
	- Kí hiệu `<>` được sử dụng để bọc lấy các kiểu tổng quát
- Implement một giao diện tổng quát tương tự như thừa kế một lớp tổng quát
## Ví dụ
- Tạo một interface `GenericDao` có kiểu tổng quát `T`
	```Java
	public interface GenericDao<T> {
		void insert(T obj);
		void update(T obj); 
	}
	```
- Một class cài đặt từ giao diện trên
	```Java
	public abstract class AbstractGenericDao<T> implements GenericDao<T>{}
	```
# Phương thức tổng quát
## Cấu trúc
- Phương thức tổng quát được viết với cấu trúc như sau:
	```Java
	<T1, T2, ... , Tn> return_type name_func{...} {
	/* ... */
	}
	```
	, trong đó:
	- `T1, T2, ... , Tn` là các kiểu tổng quát
	- Kí hiệu `<>` được sử dụng để bọc lấy các kiểu tổng 