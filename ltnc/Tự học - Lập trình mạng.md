# 🌐 Lý thuyết Lập trình Mạng — UET.CS2043

---

## 1. Tổng quan

Phần lớn ứng dụng hiện đại là ứng dụng mạng: web, mobile, game online, IoT, giao tiếp giữa các dịch vụ trong hệ thống lớn.

---

## 2. Địa chỉ IP & Port

### Địa chỉ IP
| | Public IP | Private IP |
|---|---|---|
| **Cấp bởi** | ISP (nhà mạng) | Router trong mạng nội bộ |
| **Phạm vi** | Toàn mạng Internet | Chỉ trong mạng nội bộ |

- **IPv4**: 32-bit, gồm 4 octet thập phân — ví dụ: `104.25.221.55`
- **IPv6**: 128-bit, gồm 8 nhóm hex — ví dụ: `2342:0415:2CA1:0000:0000:0566:5671:23b4`

### Port (Số hiệu cổng)
- Dùng để **phân biệt các ứng dụng** trên cùng một máy (cùng IP)
- Phạm vi: **0 – 65535**
- Ví dụ: Trình duyệt dùng port 80/443, Database MySQL dùng 3306

---

## 3. Giao thức TCP vs UDP

| | TCP | UDP |
|---|---|---|
| Loại kết nối | Hướng kết nối | Không kết nối |
| Độ tin cậy | ✅ Đảm bảo đúng thứ tự, không mất mát | ❌ Không đảm bảo |
| Tốc độ | Chậm hơn | Nhanh hơn |
| Ứng dụng | Chat, truyền file | Streaming, game, voice call |

---

## 4. Mô hình mạng TCP/IP (4 tầng)

| Tầng | Chức năng |
|---|---|
| **Application** | Nơi ứng dụng (trình duyệt, app mobile) giao tiếp với mạng |
| **Transport** | Đảm bảo dữ liệu gửi đúng cách (TCP/UDP) |
| **Internet** | Quản lý đường đi, định địa chỉ IP, tính toán đường tốt nhất |
| **Network Access (Link)** | Quản lý tín hiệu vật lý, phần cứng mạng |

---

## 5. Socket

$$\text{Socket} = \text{Địa chỉ IP} + \text{Port}$$

Socket đóng vai trò là "ổ cắm" để ứng dụng kết nối vào đường ống mạng.

---

## 6. Mô hình Client – Server

- **Server**: Cung cấp tài nguyên/dịch vụ, **luôn ở trạng thái chờ**
- **Client**: Sử dụng tài nguyên, **chủ động gửi yêu cầu**

### Quy trình hoạt động của Server:
1. **Binding to Port** — mở cổng lắng nghe
2. **Listening** — chờ kết nối
3. **Accepting** — chấp nhận kết nối từ client
4. **Serving** — xử lý yêu cầu

### Quy trình hoạt động của Client:
1. Xác định IP và Port của Server
2. **Connect** — yêu cầu kết nối
3. **Read/Write** — trao đổi dữ liệu
4. **Close** — đóng kết nối

---

## 7. Cơ chế TCP Handshake (Bắt tay 3 bước)

$$\text{Client} \xrightarrow{SYN} \text{Server} \xrightarrow{SYN-ACK} \text{Client} \xrightarrow{ACK} \text{Server}$$

Mục đích: Thiết lập sự **đồng bộ và tin cậy** trước khi truyền dữ liệu.

---

## 8. Lập trình Socket (Java)

### Stream dữ liệu
- **Input Stream**: Dữ liệu đi **vào** ứng dụng từ mạng
- **Output Stream**: Dữ liệu đi **ra** khỏi ứng dụng vào mạng

### Server (ứng dụng Echo):
```java
// B1. Mở cổng lắng nghe
ServerSocket serverSocket = new ServerSocket(5000);

// B2. Chờ client kết nối (BLOCK đến khi có client)
Socket clientSocket = serverSocket.accept();

// B3. Thiết lập luồng đọc/ghi
BufferedReader reader = new BufferedReader(new InputStreamReader(clientSocket.getInputStream()));
PrintWriter writer = new PrintWriter(clientSocket.getOutputStream(), true); // true = auto-flush

// B4. Vòng lặp xử lý
String line;
while ((line = reader.readLine()) != null) {
    System.out.println("Client nói: " + line);
    writer.println("Echo: " + line);
}
clientSocket.close();
```

### Client:
```java
// Kết nối đến Server
Socket socket = new Socket("127.0.0.1", 5000);

BufferedReader networkIn = new BufferedReader(new InputStreamReader(socket.getInputStream()));
PrintWriter networkOut = new PrintWriter(socket.getOutputStream(), true);
BufferedReader userIn = new BufferedReader(new InputStreamReader(System.in));

String userInput;
while ((userInput = userIn.readLine()) != null) {
    networkOut.println(userInput);      // Gửi lên Server
    System.out.println(networkIn.readLine()); // Đọc phản hồi
}
```

---

## 9. Đa luồng trong lập trình mạng

### Vấn đề
Server đơn luồng chỉ phục vụ **1 client tại một thời điểm** → Client B bị "đứng hình".

### Giải pháp: Mỗi client một Thread
```java
// Mỗi client được giao cho một ClientHandler riêng
public class ClientHandler implements Runnable {
    private Socket clientSocket;
    public ClientHandler(Socket socket) { this.clientSocket = socket; }

    @Override
    public void run() { /* logic đọc/ghi */ }
}

// Vòng lắng nghe chính
ServerSocket server = new ServerSocket(5000);
while (true) {
    Socket client = server.accept();
    new Thread(new ClientHandler(client)).start(); // Thread riêng cho mỗi client
}
```

### Vấn đề tiềm năng ⚠️
Nếu có **1 triệu client** → tạo 1 triệu Thread → **tràn RAM**.  
→ Giải pháp thực tế: dùng **Thread Pool** (ExecutorService).

---

## 10. REST API

- Xây dựng trên **HTTP** (tầng Application)
- Các phương thức chuẩn: `GET` | `POST` | `PUT` | `DELETE`
- Dữ liệu đóng gói dạng **JSON**

### Khi nào dùng Socket? Khi nào dùng REST?

| | Socket | REST API |
|---|---|---|
| **Ưu điểm** | Thời gian thực, độ trễ cực thấp, kết nối liên tục | Dễ triển khai, stateless, đa nền tảng |
| **Ứng dụng** | Game online, chat trực tuyến, IoT liên tục | Web thông thường, mạng xã hội, hệ thống quản lý |

---

Nếu bạn cần giải thích sâu hơn phần nào (code, bài tập, so sánh...) cứ hỏi nhé!