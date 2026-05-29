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
	- Kí hiệu `<>` được sử dụng để bọc lấy các kiểu tổng quát
	- `return_type` là kiểu trả về của phương thức tổng quát
	- `name_func` là tên của phương thức tổng quát
## Tạo phương thức tổng quát
- Phương thức tổng quát có các đặc điểm sau:
	- Sử dụng ít nhất một kiểu tổng quát
	- Có thể nằm trong lớp/giao diện tổng quát hoặc không
	- Có thể là phương thức tĩnh hoặc không tĩnh
## Ví dụ
Viết phương thức tổng quát `compare` để so sánh hai đối tương `p1` và `p2`. Trong đó, `p1` và `p2` đều thuộc lớp tổng quát `Pair`. 
Hai đối tượng kiểu `Pair` bằng nhau khi giá trị `value` và khóa `key` đều bằng nhau.
```Java
// Pair.java
public class Pair<K, V> { private K key; private V value; }
// Utils.java
public class Util {
    public static <K, V> boolean compare(
                    Pair<K, V> p1, Pair<K, V> p2) {
        return p1.getKey().equals(p2.getKey()) &&
               p1.getValue().equals(p2.getValue());
    }
}
```
```Java
// UtilTest.java
public static void main(String[] args) {
    Pair<Integer, String> p1 = new Pair<>(1, "apple");
    Pair<Integer, String> p2 = new Pair<>(2, "pear");
    boolean same = Util.compare(p1, p2); // False
}
```
# Khởi tạo kiểu tổng quát
- Hai nhu cầu tường gặp khi khởi tạo kiểu tổng quát
	- Khởi tạo đối tượng có kiểu tổng quát
	- Khởi tạo mảng dữ liệu (trong đó các phần tử có kiểu tổng quát) - gọi là mảng tổng quát
## Vấn đề khi khởi tạo đối tượng có kiểu tổng quát
- Không thể tạo trực tiếp đối tượng có kiểu tổng quát bằng cách dùng từ khóa `new`
- Trình biên dịch của Java cần biết rõ kiểu tổng quát `T` là cái gì mới có thể biên dịch
- Ví dụ: Xét lớp tổng quát `Box`
	```Java
	public class Box<T> {
	private T t = new T(); // lỗi
	}
	```
	Lớp này không thể biên dịch thành công do cố tình khởi tạo một đối tượng có kiểu tổng quát `T`. 
	```
	$javac Box.java
	Box.java:2: error: unexpected type
	    private T t = new T();
	                      ^
	  required: class
	  found:    type parameter T
	  where T is a type-variable:
	    T extends Object declared in class Box
	1 error
	```
## Vấn đề khi khởi tạo mảng tổng quát
- Không thể tạo trực tiếp mảng tổng quát bằng cách dùng từ khóa `new`
- Trình biên dịch của Java cần biết rõ kiểu tổng quát `T` của các phần từ mảng là cái gì mới có thể biên dịch
- Ví dụ: Xét lớp tổng quát `BoxArray`
	```Java
	public class BoxArray<T> {
		private T[] t = new T[5]; 
	} // lỗi
	```
	Lớp này không thể biên dịch thành công do coos tình khởi tạo một mảng tổng quát
	```
	$javac BoxArray.java
	BoxArray.java:2: error: generic array creation
		private T[] t = new T[5];
		
	1 error
	```
## Giải pháp
- Java hỗ trợ cơ chế reflection để khởi tạo: 
	- đối tượng có kiểu tổng quát
	- mảng tổng quát
- Sử dụng phương thức `newInstance()` của lớp Class để tạo một đối tượng từ tên đối tượng
	- Tên đối tượng được thể hiện dưới dạng xâu
## Ví dụ khởi tạo đối tượng có kiểu tổng quát
```Java
public class GenericInstance<T> {
    //Khai báo biến obj kiểu T
    private T obj;

    //Sử dụng đối tượng Class<T>, khai báo biến aClazz
    public GenericInstance(Class<T> aClazz) 
            throws InstantiationException, IllegalAccessException {
        //Tạo đối tượng thông qua hàm newInstance()
        this.obj = (T) aClazz.newInstance();
    }

    public T getObj() {
        return obj;
    }
}
```
## Ví dụ khởi tạo mảng tổng quát 
```Java
public class GenericArrayContructor<T> {
    private final int size = 10;
    private Class<T> aClazz;

    private T[] myArray;

    public GenericArrayContructor(Class<T> aClazz) {
        this.aClazz = aClazz;
        myArray = (T[]) Array.newInstance(aClazz, size);
    }

    public T[] getMyArray() {
        return this.myArray;
    }
}
```

# Các ký tự đại diện (Wildcard)
## Ký tự đại diện (Wildcard)
- Ký tự (?): đại diện cho một loại (type) chưa xác định
- Kiểu tham số đại diện (wildcard parameterized type)
	- Ít nhất một kiểu tham số là wildcard
		- `Collection<?>`
		- `List<? extends Number>` 
		- `Comparator<? super String>
		- `Pair<String,?>`
- ![](../Assets/Pasted%20image%2020260529192501.png)
- `<?>`: chấp nhận tất cả các loại đối số
- `<? extends type>`: chấp nhận đối tượng kế thừa từ type hoặc chính type
- `<? super type>`: chấp nhận đối tượng là cha của type hoặc chính type
- Không thể khởi tạo một đối tượng thuộc kiểu đại diện
	- Kiểu đại diện không phải là một kiểu dữ liệu cụ thể
	- Không thể sử dụng toán tử new để khởi tạo đối tượng
- Khai báo hợp lệ
	```Java
	Collection<?> coll = new ArrayList<String>();

	// Một tập hợp chỉ chứa kiểu Number hoặc kiểu con của Number
	List<? extends Number> list = new ArrayList<Long>();

	// Một đối tượng có kiểu tham số đại diện.
	// (A wildcard parameterized type)
	Pair<String,?> pair = new Pair<String,Integer>();
	```
- Khai báo không hợp lệ
	```Java
	// String không phải là kiểu con của Number, vì vậy lỗi.
	List<? extends Number> list = new ArrayList<String>();

	// String không phải là kiểu cha của Integer vì vậy lỗi
	ArrayList<? super String> cmp = new ArrayList<Integer>();
	```
## Ví dụ kiểu đại diện
```Java
public class WildCardExample1 {

    public static void main(String[] args) {

        // Một danh sách chứa các phần tử kiểu String.
        ArrayList<String> listString = new ArrayList<String>();

        listString.add("Tom");
        listString.add("Jerry");

        // Một danh sách chứa các phần tử kiểu Integer
        ArrayList<Integer> listInteger = new ArrayList<Integer>();

        listInteger.add(100);

        // Bạn không thể khai báo:
        // ArrayList<Object> list1 = listString; // ==> Error!

        // Một đối tượng kiểu tham số đại diện.
        // (wildcard parameterized object).
        ArrayList<? extends Object> list2;

        // Bạn có thể khai báo:
        list2 = listString;

        // Hoặc
        list2 = listInteger;

    }

}
```
```Java
public class WildCardExample2 {

    public static void main(String[] args) {

        List<String> names = new ArrayList<String>();
        names.add("Tom");
        names.add("Jerry");
        names.add("Donald");

        List<Integer> values = new ArrayList<Integer>();
        values.add(100);
        values.add(120);

        System.out.println("--- Names --");
        printElement(names);

        System.out.println("-- Values --");
        printElement(values);

    }

    public static void printElement(List<?> list) {
        for (Object e : list) {
            System.out.println(e);
        }
    }

}
```
# Ưu, nhược điểm của lập trình tổng quát
## Ưu điểm
- Giảm thiểu chi phí kiểm thử và bảo trì mã nguồn do không cần viết nhiều chương trình có thuật toán giống nhau cho các kiểu dữ liệu khác nhau
	- Ví dụ: Viết thuật toán sắp xếp chèn (selection sort) cho mảng lưu các số nguyên `arr1` và mảng lưu các kí tự `arr2`
	- Cách 1 (lập trình không tổng quát): viết hai phương thức sắp xếp riếng biệt cho `arr1` và `arr2`
		- Thu được hai phương thức giống hệ nhau về thuật toán nhưng khác nhau về kiểu dữ liệu
		- Tốn them chi phí kiểm thử và bảo trì
	- Cách 2 (lập trình tổng quát): Nhận thấy thuật toán sắp xếp chèn cho `arr1` và `arr2` là giống hệt nhau
		- Do đó, thay vì vi