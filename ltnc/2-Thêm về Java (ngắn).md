
# UET.CS2043 - Lập trình nâng cao: Thêm về Java

Tài liệu này tổng hợp các kiến thức nền tảng và nâng cao về cấu trúc chương trình, quản lý bộ nhớ, và các đặc trưng hướng đối tượng trong ngôn ngữ Java [1].

## 1. Cấu trúc Chương trình và Đối tượng
*   **Tổ chức mã nguồn:** Chương trình Java bao gồm một tập các đối tượng. Mỗi lớp thường được đặc tả trong một tệp nguồn riêng (tên tệp trùng với tên lớp), giúp tăng tính độc lập, dễ mô-đun hóa, dễ sửa đổi và tiết kiệm thời gian biên dịch [1].
*   **Thao tác với đối tượng:** Các đối tượng không được thao tác trực tiếp mà thông qua các **tham chiếu (references)** [2]. Tham chiếu đóng vai trò giống như con trỏ, và mọi đối tượng đều phải được tạo tường minh bằng toán tử `new` [3, 4].

## 2. Kiểm soát truy cập và Đặc trưng Phương thức
Java cung cấp các phạm vi truy cập để che giấu thông tin và đóng gói dữ liệu:
*   `public`: Có thể truy cập ở bất kỳ đâu và bởi bất kỳ ai [3].
*   `protected`: Chỉ có thể truy cập bởi chính lớp đó, các lớp con (subclass), hoặc các lớp trong cùng gói (package) [3, 5].
*   `private`: Chỉ được phép truy cập nội bộ bên trong lớp đó [5].

**Nạp chồng phương thức (Overloading):** Cho phép định nghĩa nhiều phương thức có cùng tên trong một lớp, nhưng bắt buộc phải khác nhau về danh sách tham số truyền vào [6].

## 3. Phương thức khởi tạo (Constructor)
*   Là phương thức đặc biệt được gọi tự động (bởi toán tử `new`) ngay sau khi đối tượng được tạo ra nhằm khởi tạo giá trị cho các thuộc tính [6, 7].
*   **Đặc điểm:** Tên trùng với tên lớp và không có kiểu trả về [7]. Nếu lập trình viên không khai báo, hệ thống sẽ tự động gọi constructor mặc định (phương thức rỗng) [7].
*   **Khởi tạo sao chép (Copy constructor):** Là kỹ thuật khởi tạo một đối tượng mới dựa trên dữ liệu sao chép từ một đối tượng khác đã tồn tại [8, 9].

## 4. Quản lý Bộ nhớ: Stack và Heap
Java phân tách rõ ràng nơi lưu trữ các loại dữ liệu:
*   **Dữ liệu nguyên thủy (Primitive):** Bao gồm `byte, int, long, float, double, boolean, char`. Chúng không phải là đối tượng và được lưu trữ trực tiếp trên vùng nhớ **Stack** [10-12].
*   **Tham chiếu đối tượng (Reference):** Bản thân biến tham chiếu được lưu trên **Stack** (hoặc vùng static), nhưng đối tượng thực tế mà nó trỏ tới lại được cấp phát động trên vùng nhớ **Heap** [12].
*   **Phép gán `=` đối với tham chiếu:** Không sao chép nội dung của đối tượng mà chỉ sao chép địa chỉ tham chiếu, khiến hai biến cùng trỏ về một đối tượng trên Heap [4, 13].

## 5. So sánh đối tượng và Thu hồi bộ nhớ
*   **Toán tử `==`**: Dùng để so sánh giá trị của kiểu nguyên thủy. Đối với kiểu tham chiếu, nó chỉ kiểm tra xem hai biến có trỏ đến cùng một đối tượng hay không (so sánh địa chỉ), chứ KHÔNG so sánh nội dung bên trong [14].
*   **Phương thức `equals()`**: Để so sánh nội dung của hai đối tượng, lập trình viên cần sử dụng và ghi đè (override) phương thức `equals()` [14, 15].
*   **Thu hồi bộ nhớ (Garbage Collection - GC):** Máy ảo JVM tự động dọn dẹp và thu hồi các đối tượng trên Heap khi chúng không còn tham chiếu nào trỏ tới (số đếm tham chiếu = 0). Điều này giúp lập trình viên không cần viết lệnh giải phóng bộ nhớ thủ công, tránh lỗi rò rỉ hoặc quên giải phóng tài nguyên [15, 16].

## 6. Truyền tham số và Tham chiếu `this`
*   **Truyền giá trị (Pass-by-value):** Java chỉ hỗ trợ truyền giá trị. Khi truyền kiểu nguyên thủy, giá trị được sao chép. Khi truyền đối tượng, **địa chỉ tham chiếu** được sao chép (bạn có thể thay đổi nội dung đối tượng, nhưng không thể trỏ tham chiếu đó sang đối tượng khác từ bên trong hàm) [17, 18].
*   **Tham chiếu `this`:** Là con trỏ ngầm định trỏ tới chính đối tượng đang gọi phương thức. `this` dùng để giải quyết xung đột tên biến, truyền đối tượng hiện tại làm tham số, làm giá trị trả về, hoặc gọi một constructor khác cùng lớp [19-21].

## 7. Thành phần Tĩnh (`static`)
*   **Thuộc tính/Phương thức `static`:** Thuộc về bản thân **Lớp (Class)** thay vì từng đối tượng cụ thể. Dữ liệu tĩnh được chia sẻ chung giữa tất cả các thể hiện của lớp đó [21, 22].
*   Phương thức tĩnh không thể truy cập trực tiếp các thành phần `non-static` (thành phần thông thường) và không thể sử dụng từ khóa `this` vì nó không phụ thuộc vào bất kỳ đối tượng cụ thể nào [23].

## 8. Gói (Package) và Hợp thành (Composition)
*   **Package:** Giúp tổ chức và quản lý không gian tên (namespace) của các lớp. Lệnh `package` phải nằm ở dòng đầu tiên của tệp. Lớp không có từ khóa phạm vi truy cập sẽ mang mức "mặc định" (chỉ truy cập được trong cùng gói) [24, 25].
*   **Hợp thành (Composition - "Has-a"):** Là phương pháp tái sử dụng mã nguồn bằng cách khai báo các đối tượng khác làm thuộc tính bên trong một lớp. Các đối tượng bị chứa này cần được khởi tạo tường minh (qua `new`) [26].

## 9. Luồng dữ liệu chuẩn và Tham số dòng lệnh
*   **I/O chuẩn:** Khi ứng dụng chạy, JVM tự tạo 3 đối tượng: `System.out` (luồng ra), `System.err` (luồng lỗi), và `System.in` (luồng vào) [27].
*   **Scanner:** Là lớp tiện ích để lấy dữ liệu từ `System.in`, hỗ trợ đọc kiểu nguyên thủy (`nextInt()`, `nextLong()`) và xâu ký tự (`next()`) [28, 29].
*   **Tham số dòng lệnh:** Giá trị truyền vào lúc khởi chạy chương trình (ví dụ: `java MyApp hello world`) sẽ được bắt thông qua mảng `String[] args` tại phương thức `main` [30].
```