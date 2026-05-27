# Biên dịch: Write Once, Run Anywhere
![[Pasted image 20260526145016.png]]

## Java Virtual Machine
- được hiện thực phụ thuộc vào nền tảng (hardware, OS)
- Đảm bảo các chương trình Java (bytecode) có thể thực thi trên các nền tảng khác nhau (platform-independent)
- Đảm bảo an ninh 
- Thường được hiện thực như là một phần mềm 
	- JRE - Java Runtime Environment
- Java Platform: JVM + APIs
## Các loại ứng dụng Java
- Ứng dụng để bàn - Java Standard Edition (Java SE)
- Ứng dụng phân tán, ứng dụng chủ - Java Enterprise Edition (Java EE)
- Ứng dụng di động - Java Micro Edition (Java ME)
- Ứng dụng trên thẻ - Java Card 
## Biên dịch và thực thi

![[Pasted image 20260527213310.png]]
![[Pasted image 20260527213447.png]]
## JDK - Java Development Kit 
- Môi trường phát triển ứng dụng Java
- Các thành phần chính: 
	- javac: trình biên dịch, chuyển mã nguồn Java thành bytecode
	- java: trình thông dịch
	- javadoc: công cụ sinh tài liệu từ các chú thích trong mã nguồn
	- jdb: trình gỡ lỗi
## Lập trình hướng đối tượng
Khác phục các hạn chế của Lập trình thủ tục
- Đóng gói dữ liệu và xử lý (che giấu dữ liệu; truy cập qua giao diện)
- Đảm bảo nhất quán dữ liệu và các ràng buộc
- Dễ bảo trì hơn
![[Pasted image 20260527213740.png]]

## Lập trình hướng đối tượng (OOP) là gì?
- Lập trình hướng đối tượng
	- Tái hiện / ánh xạ vấn đề trong thế giới thực vào các chương trình
	- Xây dựng cơ chế tổ chức các "thực thể" (đối tượng) có thể làm gì đó hoặc yêu cầu các đối tượng khác thực hiện
	- Tạo ra "kiểu" (lớp) của các đối tượng để cho phép tạo ra chúng mà không phải định nghĩa lại thuộc tính và hành vi cho từng đối tượng. 
![[Pasted image 20260527214013.png]]

## Khái niệm cơ bản về HĐT
- Trừu tượng hóa
- Các đối tượng và lớp 
	- Trạng thái và hành vi đối tượng
	- Định danh đối tương
	- Các thông điệp
- Bao gói
	- Che giấu thông tin (cài đặt)
- Kế thừa
- Đa hình
![[Pasted image 20260527214118.png]]
## Trừu tượng hóa
- Đặc điểm của ngôn ngữ hướng đối tượng (khởi đầu bởi Smalltalk)
	- Mọi thứ đều là đối tượng (everything is an object) 
	- Hoạt động của chương trình là quá trình "nói chuyện" giữa các đối tượng bằng cách "gửi thông điệp"
	- Mỗi đối tượng có vùng nhớ riêng và được hình thành từ các đối tượng khác
	- Mỗi đối tượng có một kiểu (type)
	- Các đối tượng cùng kiểu có thể nhận cùng một thông điệp
## Các đối tượng
- Bao gồm ba thành phần
	- Trạng thái
		- Được xác định bởi giá trị bên trong (giá trị thuộc tính)
	- Hành vi 
		- Tương ứng với các phương thức
	- Định danh
		- Các đối tượng khác nhau có thể cùng trạng thái (cùng giá trị thuộc tính) nhưng khác nhau về định danh
		- Đối tượng được thao tác thông qua tham chiếu (handle) (con trỏ trong C++; tham chiếu đối tượng trong Java)
		![](../Assets/Pasted%20image%2020260527224745.png)
## Đối tượng và Tham chiếu đối tượng
![](../Assets/Pasted%20image%2020260527230253.png)

## Các thông điệp (messages)
`today.setDate(2,9,2020);`
- Là cách thức để đối tượng A yêu cầu đối tượng B thực hiện phương thức của B
- Một thông điệp bao gồm
	- Tham chiếu đối tượng đích - nhận thông điệp (today)
	- Tên của phương thức cần thực hiện (setDate)
	- Các thông tin cần thiết khác - các tham số (2, 9, 2020)
- Thông điệp được cài đặt ở dạng lời gọi hàm với tham số ngầm là đối tượng nhận thông điệp (method invocation)
- Khái niệm thông điệp tạo nên sự khác biệt cho lập trình HĐT
	- Dữ liệu trở thành chủ động
	- Với các lược đồ lập trình khác
		- Các hành động được thực hiện qua cơ chế truyền điều khiển (gọi hàm/ thủ tục)
		- Dữ liệu là bị động, các thủ tục thao tác trên dữ liệu
## Các lớp đối tượng
- Lớp (Class) 
	- Khuôn để tạo các đối tượng (các thể hiện)
	- Các đối tượng của một lớp có cùng cấu trúc và hành vi được mô tả bởi lớp đó
- Quan hệ "Kiểu dữ liệu - Biến"
	- Các lớp được thiết kế và cài đặt (kiểu dữ liệu)
	- Các đối tượng được tạo khi thực thi chương trình
```Java
class Date{  
public:  
void setDate(…);  
...  
private:  
int day;  
...  
};  
Date today = new Date();
today.setDate(2, 9, 2020);
```
## Bao gói / Che giấu thông tin
- Bao gói (encapsulation): để nhóm các thứ liên quan thành một tổng thể có định danh
	- Hàm/Thủ tục bao gói các câu lệnh
	- Đối tượng bao gói dữ liệu và thủ tục
- Che giấu thông tin: để che giấu các thông tin và chi tiết cài đặt bên trong đối với bên ngoài
	- Để các "clients" (các lập trình viên khác) xem các đối tượng như các hộp đen
	- public, private và protected
	- Giao diện (interface) & Cài đạt (implementation)
## Kế thừa
- Sử dụng lại các giao diện và cài đặt
- Các mối quan hệ "is-a"
- Cơ chế cho phép các đối tượng lớp dẫn xuất (derived class) mang đặc điểm (thuộc tính) và hành vi (phương thức) của lớp cơ sở (base class)
- Các dịch vụ tổng quát (generic) có thể được xác định và thiết kế trước khi đặc biệt hóa chúng
## Đa hình
- Đa hình: 
	- Khả năng được xem xét ở các dạng thức (forms/shapes) khác nhau
	- Có thể tồn tại ở nhiều dạng
- Đa hình đối tương: 
	- Đối tượng của các lớp dẫn xuất khác nhau có thể được  xem như thể hiện của cùng một lớp chung (lớp cơ sở)
	- Các đối tượng của các lớp khác nhau có thể hiểu cùng một thông điệp theo các cách khác nhau
		- Ví dụ: khi nhập thông điệp draw(), các đối tượng Rectangle và Triangle hiểu và thực thi thông điệp theo cách khác nhau
	
![](../Assets/Pasted%20image%2020260527232211.png)
![](../Assets/Pasted%20image%2020260527232222.png)