
# BÁO CÁO BÀI TẬP LỚN MÔN LẬP TRÌNH NÂNG CAO
**Đề tài:** Phát triển hệ thống đấu giá trực tuyến (Online Auction System)

---

## 1. Giới thiệu mục tiêu và phạm vi thực hiện
**Mục tiêu:** 
Xây dựng nền tảng đấu giá trực tuyến hoàn chỉnh theo mô hình Client-Server, áp dụng triệt để các nguyên lý Lập trình hướng đối tượng (OOP) như kế thừa, đa hình, đóng gói. Đồng thời, hệ thống triển khai các mẫu thiết kế (Design Patterns) như MVC, Observer để giải quyết các bài toán kỹ thuật nâng cao về xử lý đồng thời (Concurrent Bidding) và cập nhật thời gian thực (Realtime Update).

**Phạm vi hệ thống:**
Hệ thống cho phép người dùng đăng ký, đăng nhập và hoạt động dưới 3 vai trò chính:
*   **Admin:** Quản lý toàn bộ hệ thống, kiểm duyệt/ban người dùng.
*   **Seller:** Đăng bán vật phẩm, quản lý phiên đấu giá.
*   **Bidder:** Tham gia đặt giá cạnh tranh, sử dụng tính năng đấu giá tự động (Auto-bidding) và theo dõi lịch sử giá.

---

## 2. Kiến trúc tổng thể của hệ thống
Hệ thống tuân thủ kiến trúc **Client-Server** kết hợp mô hình **MVC** ở cả hai phía, đảm bảo tính tách biệt rành mạch giữa giao diện và logic dữ liệu.
![](Assets/Pasted%20image%2020260606205246.png)



**Mô tả kiến trúc:**

- **Phía Client (JavaFX):** Tầng UI hiển thị giao diện qua các file FXML. Tầng Mạng (`ApiClient`) sử dụng giao thức REST để gửi Request chủ động. Hai bộ lắng nghe (`PriceStreamListener`, `BalanceStreamListener`) duy trì kết nối để nhận luồng dữ liệu thời gian thực.
- **Phía Server (Spring Boot):** Xử lý toàn bộ logic nghiệp vụ (Auth, Bids, Items). Chỉ có Server mới được quyền truy xuất cơ sở dữ liệu qua Spring Data JPA (`Repository`).
- **Luồng Real-time:** Khi có giao dịch thành công làm thay đổi dữ liệu, tầng Service sẽ kích hoạt các Sinks (`ItemPricesSink`, `UserBalanceSink`) để lập tức đẩy Server-Sent Events (SSE) về Client.

--------------------------------------------------------------------------------

## 3. Các chức năng đạt được, hướng giải quyết và lý do

### 3.1. Các chức năng cốt lõi bắt buộc

- **Quản lý người dùng & Sản phẩm:** Phân quyền chặt chẽ bằng JWT. Kế thừa tính năng theo OOP (`Bidder`, `Seller`, `Admin` extends `User`). Quản lý luồng vòng đời sản phẩm nghiêm ngặt qua 3 trạng thái: `OPEN → RUNNING → FINISHED`.
- **Giao diện người dùng (GUI):** Xây dựng hoàn thiện bằng JavaFX. Tách biệt rõ ràng các màn hình như Dashboard (`DashboardTab`), Danh sách phiên (`BrowseTab`), Quản lý của Seller (`MySaleTab`) và Màn hình đấu giá trực tiếp (`BidderViewPage`, `SellerViewPage`), giúp trải nghiệm mượt mà.
- **Xử lý Ngoại lệ (Global Exception):** Chủ động bắt các lỗi thao tác như "đặt giá thấp hơn giá hiện tại", "đấu giá phiên đã đóng" hoặc lỗi kết nối, đảm bảo ứng dụng không bị crash.

### 3.2. Xử lý Đấu giá Đồng thời (Concurrent Bidding)

- **Yêu cầu:** Giải quyết vấn đề nhiều Bidder đặt giá cùng một mili-giây, ngăn chặn rủi ro _Lost update_, rollback sai hoặc hai người cùng thắng.
- **Hướng giải quyết:** Thay vì tự triển khai đồng bộ hóa thủ công (`synchronized`), hệ thống khai thác sức mạnh của framework Spring Boot. Mỗi REST request gọi lên được xử lý bằng một luồng độc lập trong Thread-pool của Tomcat. Logic giao dịch được bọc bởi annotation `@Transactional` kết hợp cơ chế khóa (Lock) của cơ sở dữ liệu.
- **Lý do:** Cách tiếp cận này tận dụng hệ sinh thái sẵn có để đảm bảo tính ACID cho dữ liệu, tránh rủi ro Deadlock và tối ưu hóa hiệu suất so với việc lock luồng thủ công ở mức ứng dụng.


### 3.3. Cập nhật dữ liệu thời gian thực và Xử lý Đa luồng tại Client (JavaFX)
*   **Vấn đề đa luồng ở Client:** Trong JavaFX, quy tắc an toàn luồng (Thread-safety) bắt buộc mọi thao tác thay đổi giao diện phải được thực thi trên luồng chính (**JavaFX Application Thread**). Nếu hệ thống bắt luồng chính phải chờ phản hồi từ Server, ứng dụng sẽ bị treo (freeze).
*   **Hướng giải quyết và Kỹ thuật áp dụng:** 
    *   **Xử lý bất đồng bộ (Asynchronous):** Toàn bộ các thao tác gọi REST API và các bộ lắng nghe luồng sự kiện (như `PriceStreamListener` và `BalanceStreamListener`) đều được giao phó cho các **Background Threads** độc lập quản lý mạng.
    *   **Đồng bộ hóa giao diện (UI Synchronization):** Khi các tiến trình nền (Callbacks/Listeners) nhận được tín hiệu đẩy (Push) từ Server, chúng không trực tiếp can thiệp vào UI. Thay vào đó, chúng sử dụng cơ chế **`Platform.runLater()`** để đưa các tác vụ cập nhật giao diện (Runnable) vào hàng đợi.
*   **Lý do lựa chọn:** Việc thiết kế luồng như trên giúp tách biệt hoàn toàn tầng xử lý mạng (Network Layer) và tầng hiển thị (UI Layer). Ứng dụng client duy trì được sự mượt mà, không bị "nghẽn" ngay cả khi nhận hàng loạt luồng dữ liệu giá/số dư liên tục từ hàng nghìn request SSE trả về.


### 3.4. Các chức năng nâng cao (Advanced Features)

- **Auto-Bidding:** Người dùng đặt giới hạn (`maxBid`) và bước giá (`increment`). Backend (thông qua `AutoBidResolver`) sẽ tự động đại diện người dùng nâng giá cạnh tranh khi bị đối thủ vượt mặt, tiết kiệm thời gian theo dõi.
- **Gia hạn phiên (Anti-Sniping):** Nếu phát hiện lượt Bid hợp lệ vào những phút cuối cùng, hệ thống tự động cộng thêm thời gian (extra_time) vào thời hạn chốt phiên, đảm bảo tính công bằng tuyệt đối.
- **Bid History Visualization:** Hiển thị trực quan biến động giá thông qua biểu đồ đường (LineChart) trên JavaFX được kết nối trực tiếp với luồng SSE.

### 3.5. Triển khai & Tích hợp (CI/CD)

- **Hướng giải quyết:** Dự án sử dụng hệ thống build **Gradle** cho Backend và **Maven** cho Frontend. Xây dựng hơn 100 kịch bản kiểm thử API tự động (API Integration Tests) thông qua Python Pytest và tích hợp quy trình **GitHub Actions (CI/CD)**.
- **Lý do:** Tự động hóa quá trình kiểm thử mỗi khi có lệnh Push/Pull Request, đảm bảo mã nguồn luôn đạt chất lượng cao nhất theo chuẩn công nghiệp thực tế.

--------------------------------------------------------------------------------


## 4. Phân chia công việc và sự đóng góp của các thành viên
*(Lưu ý: Đánh giá dựa trên tiêu chí tổng tỷ lệ đóng góp của các cá nhân phân bổ bằng đúng điểm chung của toàn nhóm)*

| STT | Họ và Tên           | Mã Sinh Viên | Vai trò và Trách nhiệm chuyên môn                                                                                                                                                                                                                                                                                                                       | Đánh giá hoàn thành | Tỷ lệ đóng góp |
| :-: | :------------------ | :----------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | :-----------------: | :------------: |
|  1  | **Nguyễn Anh Quân** |              | **Kỹ sư Phát triển Giao diện (Frontend Developer):** <br>Thiết kế và kiến tạo toàn bộ hệ sinh thái giao diện người dùng (GUI) trên nền tảng JavaFX. Triển khai tích hợp các bộ lắng nghe luồng dữ liệu thời gian thực (Real-time SSE) và tối ưu hóa trải nghiệm tương tác (UX/UI) thông qua kiến trúc MVC đa tầng ở phía máy khách.                     |        100%         |      30%       |
|  2  | **Nguyễn Duy Anh**  |              | **Kỹ sư Phát triển Máy chủ (Backend Developer):** <br>Xây dựng và tinh chỉnh nền tảng máy chủ cốt lõi với framework Spring Boot. Hiện thực hóa các thuật toán xử lý tranh chấp đấu giá đồng thời (Concurrent Bidding), quản trị luồng bảo mật JWT và thiết lập cơ chế phát sóng sự kiện (Observer Pattern) nhằm bảo chứng tính toàn vẹn dữ liệu (ACID). |        100%         |      30%       |
|  3  | **Phạm Thiên Minh** |              | **Kiến trúc sư Hệ thống & Chuyên viên Tài liệu (System Architect & Documentation):** <br>Phác thảo toàn cảnh kiến trúc phần mềm, hoạch định các sơ đồ cấu trúc (UML/Mermaid) chuẩn mực. Đồng thời, biên soạn và hệ thống hóa toàn bộ báo cáo kỹ thuật, đảm bảo tính chặt chẽ, tính hàn lâm và sự minh bạch trong tài liệu vận hành dự án.               |        100%         |      20%       |
|  4  | **Đinh Xuân Thông** |              | **Kỹ sư Đảm bảo Chất lượng (QA & Testing Engineer):** <br>Triển khai các kịch bản kiểm thử tự động (Unit Test/API Test) và kiểm thử thủ công. Đánh giá tính ổn định của hệ thống dưới các điều kiện tranh chấp dữ liệu khắt khe, rà soát lỗ hổng ngoại lệ (Exceptions) và bảo chứng cho chất lượng phần mềm đầu ra trước khi triển khai.                |        100%         |      20%       |

- **Link GitHub Repository:** [Link Github](https://github.com/melowmolly2/Ponzi-Auctions)
- **Link thư mục Drive (chứa Video demo):** [Link Video](https://drive.google.com/file/d/1nEZm-s0Cbj3N6QdFrHalJgr5wZXoLLvT/view)
- 