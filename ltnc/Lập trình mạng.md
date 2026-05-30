## Khởi tạo server
```Java
ServerSocket serverSocket = new ServerSocket (5000);
System.out.println("Server đang khởi động tại port 5000...");

Socket clientSocket = serverSocket.accept();
System.outprintln("Đã có khách kết nối:" + clientSocket); 
```
## Thiết lập luồng (tại Server)
```java
// Lấy luồng từ Socket của Client  
InputStream is = clientSocket.getInputStream();  
OutputStream os = clientSocket.getOutputStream();  
// Bọc luồng để xử lý text thay vì byte  
// BufferedReader: Giúp đọc theo từng dòng với readLine  
BufferedReader reader = new BufferedReader(new  
        InputStreamReader(is));  
// PrintWriter: Dùng để gửi text đi  
// 'true' nghĩa là auto-flush, đẩy dữ liệu đi ngay lập tức  
PrintWriter writer = new PrintWriter(os, true)
```
## Vòng lặp chính (tại Server)
