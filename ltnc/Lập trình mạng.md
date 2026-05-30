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
```java
String line;  
// Vòng lặp: Đọc dữ liệu cho đến khi client ngắt kết nối (line == null)  
        while ((line = reader.readLine()) != null) {  
        System.out.println("Client nói: " + line);  
writer.println("Echo: " + line); // Gửi phản hồi vào writer  
}  
clientSocket.close(); // Đóng kết nối khi xong việc
```
## Khởi tạo Client
```Java
Socket socket = new Socket("127.0.0.1", 5000);
```
## Thiết lập luồng (tại Client)
```Java
// Luồng đọc dữ liệu từ Server  
BufferedReader networkIn = new BufferedReader(new InputStreamReader(socket.getInputStream()));  
// Luồng gửi dữ liệu lên Server  
PrintWriter networkOut = new PrintWriter(socket.getOutputStream(), true);  
// Luồng đọc từ bàn phím người dùng  
BufferedReader userIn = new BufferedReader(new InputStreamReader(System.in));
```
## Vòng lặp chính (tại Client)
```Java
String userInput;  

while ((userInput = userIn.readLine()) != null) {   networkOut.println(userInput); // Gửi đi  
System.out.println(networkIn.readLine()); // Đọc phản hồi  
}
```
