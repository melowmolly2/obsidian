## Chương trình Java
- Chương trình Java bao gồm một tập các đối tượng
- Mỗi lớp được đặc tả trong một tệp nguồn (tên tệp trùng tên lớp)
	- Mỗi dòng lệnh trong Java đều thuộc một lớp 
	- Tăng tính mô-dun hóa
	- Dễ hơn cho sửa đổi mã nguồn, giảm thời gian biên dịch
![](../Assets/Pasted%20image%2020260528102024.png)
## Các đối tượng
- Các đối tượng được thao tác qua các tham chiếu (references)
	- các tham chiếu đối tượng đóng vai trò giống như các con trỏ
- Các đối tượng phải được tạo tường minh bởi toán tử new
```Java
public class GradeBookTest {  
// phương thức main bắt đầu thực thi chương trình  
	public static void main( String args[] ) {  
// tạo đối tượng GradeBook và gán cho myGradeBook  
		GradeBook myGradeBook = new GradeBook();  
// gọi phương thức displayMessage của myGradeBook  
		myGradeBook.displayMessage();  
	}  
} // kết thúc lớp GradeBookTest
```
## Đối tượng và Tham chiếu đối tượng
```Java
...  
// tạo đối tượng GradeBook và gán cho myGradeBook  
GradeBook myGradeBook = new GradeBook();  
...
```
![](../Assets/Pasted%20image%2020260528102301.png)
## Thuộc tính, Phương thức và Kiểm soát truy cập
- Các phạm vi truy cập:
	- Public
		- Có thể truy cập ở bất kỳ dâu và bởi bất kỳ ai
	- Protected
		- Chỉ có thể truy cập bởi lớp dó và các lớp con hoặc các lớp trong cùng gói (package)
	- Private
		- Chỉ có thể truy cập bởi lớp đó
![](../Assets/Pasted%20image%2020260528102506.png)
```Java
class MyDate {  
	private int year, mon, day;  
	public int getYear() {  
		return year;  
	}  
	public void setYear(int y){  
		year=y;  
	}  
}
```
```Java
MyDate d = new MyDate();
...
d.year = 2005 // compile error

d.setYear(2005)
System.out.println(d.getYear()); 
```
## Nạp chồng phương thức (overloading)
- Có thể định nghĩa các phương thức trùng tên nhưng phải khác danh sách tham số
```Java
class MyDate {
	...
	public boolean setMonth(int m) {...}

	public boolean setMonth(String s) { …}  
}  
d.setMonth(9);  
d.setMonth(”September”);
```
