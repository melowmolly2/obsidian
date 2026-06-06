
# BÁO CÁO BÀI TẬP LỚN MÔN LẬP TRÌNH NÂNG CAO
**Đề tài:** Phát triển hệ thống đấu giá trực tuyến (Online Auction System)

---

## 1. Giới thiệu mục tiêu và phạm vi thực hiện
**Mục tiêu:** 
Xây dựng nền tảng đấu giá trực tuyến hoàn chỉnh theo mô hình Client-Server [4], áp dụng triệt để các nguyên lý Lập trình hướng đối tượng (OOP) như kế thừa, đa hình, đóng gói [4]. Đồng thời, hệ thống triển khai các mẫu thiết kế (Design Patterns) như MVC, Observer, Singleton để giải quyết các bài toán kỹ thuật nâng cao về xử lý đồng thời (Concurrent Bidding) và cập nhật thời gian thực (Realtime Update) [5-8].

**Phạm vi hệ thống:**
Hệ thống cho phép người dùng đăng ký, đăng nhập và hoạt động dưới 3 vai trò chính [9]:
*   **Admin:** Quản lý toàn bộ hệ thống, kiểm duyệt/ban người dùng [9, 10].
*   **Seller:** Đăng bán vật phẩm, quản lý phiên đấu giá [9].
*   **Bidder:** Tham gia đặt giá cạnh tranh, sử dụng tính năng đấu giá tự động (Auto-bidding) và theo dõi lịch sử giá [2, 5, 9].

---

## 2. Kiến trúc tổng thể của hệ thống
Hệ thống tuân thủ kiến trúc **Client-Server** kết hợp mô hình **MVC** ở cả hai phía, đảm bảo tính tách biệt rành mạch giữa giao diện và logic dữ liệu [4, 11].



```mermaid
flowchart TD
    %% TẦNG 1: FRONTEND UI
    subgraph Layer1 [1. Tầng Giao Diện Client - JavaFX]
        direction TB
        UI_Auth(LoginPage / RegisterPage) ~~~ UI_Admin(AdminPage)
        UI_Admin ~~~ UI_Seller(SellerViewPage)
        UI_Seller ~~~ UI_Bidder(BidderViewPage)
    end

    %% TẦNG 2: FRONTEND NETWORK
    subgraph Layer2 [2. Tầng Mạng Client]
        direction TB
        Net_Req(ApiClient / AuctionApi) ~~~ Net_Listen(Price / Balance StreamListener)
    end

    %% TẦNG 3: BACKEND CONTROLLER
    subgraph Layer3 [3. Tầng API Controllers - Spring Boot]
        direction TB
        Ctrl_Auth(AuthController) ~~~ Ctrl_Admin(AdminController)
        Ctrl_Admin ~~~ Ctrl_Auction(AuctionController / BidController)
        Ctrl_Auction ~~~ Ctrl_Item(ItemController)
    end

    %% TẦNG 4: BACKEND SERVICE & SINK
    subgraph Layer4 [4. Tầng Dịch Vụ & Luồng - Spring Boot]
        direction TB
        Svc_Auth(AuthService) ~~~ Svc_Admin(AdminService)
        Svc_Admin ~~~ Svc_Auction(AuctionService & BidService)
        Svc_Auction ~~~ Svc_Item(ItemService)
        Svc_Item ~~~ Sinks[[Sinks: ItemPrices / UserBalance]]
    end

    %% TẦNG 5: BACKEND DATABASE
    subgraph Layer5 [5. Tầng Cơ Sở Dữ Liệu]
        direction TB
        DB[(Cơ Sở Dữ Liệu / JPA Repositories)]
    end

    %% LUỒNG GIAO TIẾP
    Layer1 -->|1. Thao tác| Layer2
    Layer2 == "2. Gửi REST API (HTTP)" ==> Layer3
    Layer3 -->|3. Điều phối| Layer4
    Layer4 -->|4. Truy xuất / Cập nhật| Layer5

    %% LUỒNG REAL-TIME
    Layer4 -. "5. Đẩy Luồng (SSE)" .-> Layer2
    Layer2 -. "6. Tự động cập nhật" .-> Layer1

    classDef clientLayer fill:#e3f2fd,stroke:#1565c0,stroke-width:2px;
    classDef serverLayer fill:#e8f5e9,stroke:#2e7d32,stroke-width:2px;
    classDef dbLayer fill:#fff3e0,stroke:#ef6c00,stroke-width:2px;
    class Layer1,Layer2 clientLayer;
    class Layer3,Layer4 serverLayer;
    class Layer5 dbLayer;
````

**Mô tả kiến trúc:**

- **Phía Client (JavaFX):** Tầng UI hiển thị giao diện qua các file FXML. Tầng Mạng (`ApiClient`) sử dụng giao thức REST để gửi Request chủ động. Hai bộ lắng nghe (`PriceStreamListener`, `BalanceStreamListener`) duy trì kết nối để nhận luồng dữ liệu thời gian thực.
- **Phía Server (Spring Boot):** Xử lý toàn bộ logic nghiệp vụ (Auth, Bids, Items). Chỉ có Server mới được quyền truy xuất cơ sở dữ liệu qua Spring Data JPA (`Repository`).
- **Luồng Real-time:** Khi có giao dịch thành công làm thay đổi dữ liệu, tầng Service sẽ kích hoạt các Sinks (`ItemPricesSink`, `UserBalanceSink`) để lập tức đẩy Server-Sent Events (SSE) về Client.

--------------------------------------------------------------------------------

## 3. Các chức năng đạt được, hướng giải quyết và lý do

3.1. Các chức năng cốt lõi bắt buộc

- **Quản lý người dùng & Sản phẩm:** Phân quyền chặt chẽ bằng JWT. Kế thừa tính năng theo OOP (`Bidder`, `Seller`, `Admin` extends `User`). Quản lý luồng vòng đời sản phẩm nghiêm ngặt qua 3 trạng thái: `OPEN → RUNNING → FINISHED`.
- **Giao diện người dùng (GUI):** Xây dựng hoàn thiện bằng JavaFX. Tách biệt rõ ràng các màn hình như Dashboard (`DashboardTab`), Danh sách phiên (`BrowseTab`), Quản lý của Seller (`MySaleTab`) và Màn hình đấu giá trực tiếp (`BidderViewPage`, `SellerViewPage`), giúp trải nghiệm mượt mà.
- **Xử lý Ngoại lệ (Global Exception):** Chủ động bắt các lỗi thao tác như "đặt giá thấp hơn giá hiện tại", "đấu giá phiên đã đóng" hoặc lỗi kết nối, đảm bảo ứng dụng không bị crash.

3.2. Xử lý Đấu giá Đồng thời (Concurrent Bidding)

- **Yêu cầu:** Giải quyết vấn đề nhiều Bidder đặt giá cùng một mili-giây, ngăn chặn rủi ro _Lost update_, rollback sai hoặc hai người cùng thắng.
- **Hướng giải quyết:** Thay vì tự triển khai đồng bộ hóa thủ công (`synchronized`), hệ thống khai thác sức mạnh của framework Spring Boot. Mỗi REST request gọi lên được xử lý bằng một luồng độc lập trong Thread-pool của Tomcat. Logic giao dịch được bọc bởi annotation `@Transactional` kết hợp cơ chế khóa (Lock) của cơ sở dữ liệu.
- **Lý do:** Cách tiếp cận này tận dụng hệ sinh thái sẵn có để đảm bảo tính ACID cho dữ liệu, tránh rủi ro Deadlock và tối ưu hóa hiệu suất so với việc lock luồng thủ công ở mức ứng dụng.

3.3. Cập nhật dữ liệu thời gian thực (Realtime Update)

- **Yêu cầu:** Giao diện đấu giá phải nhảy giá ngay lập tức khi có người trả cao hơn, cấm sử dụng kỹ thuật Polling (hỏi liên tục).
- **Hướng giải quyết:** Triển khai mô hình luồng Server-Sent Events (SSE). Tại backend, `ItemPricesSink` và `UserBalanceSink` quản lý các luồng phát. Tại frontend, `PriceStreamListener` và `BalanceStreamListener` đóng vai trò là các Observer để lắng nghe biến động.
- **Lý do:** Mô hình SSE Push-based giúp Server chủ động đẩy dữ liệu đi chỉ khi có thay đổi thực sự, tiết kiệm tối đa băng thông và tài nguyên so với việc Client gọi API liên tục. Đây là biểu hiện thực tế của mẫu thiết kế **Observer Pattern nâng cao**.

3.4. Chức năng nâng cao

- **Auto-Bidding (Đấu giá tự động):** Cho phép người dùng thiết lập mức giá tối đa (`maxBid`) và bước giá (`increment`) thông qua `AutoBidRequest`. Hệ thống tự động tranh giá thay cho người dùng khi luồng giá bị đẩy lên cao, đảm bảo không vượt quá ngưỡng maxBid.
- **Bid History Visualization (Lịch sử giá Realtime):** Tích hợp việc ghi nhận lại toàn bộ tiến trình đặt giá. Thông qua các luồng `BidHistoryResponse` và `BidHistoryCallback`, người dùng có thể thấy sự thay đổi liên tục của các lượt trả giá hợp lệ ngay trên giao diện mà không cần làm mới trang.

--------------------------------------------------------------------------------

4. Phân chia công việc thành viên nhóm

_(Tổng tỷ lệ đóng góp của các thành viên bằng đúng điểm chung của nhóm theo yêu cầu__)_

|STT|Họ và Tên|Mã Sinh Viên|Vai trò / Công việc đảm nhận|Đánh giá hoàn thành|Tỷ lệ đóng góp|
|---|---|---|---|---|---|
|1|[Tên Sinh Viên 1]|[MSV 1]|Xây dựng Server Spring Boot, API Đấu giá, Xử lý Concurrent Bidding|100%|... %|
|2|[Tên Sinh Viên 2]|[MSV 2]|Thiết kế UI JavaFX (Seller/Bidder View, Tabs), Xử lý luồng Real-time (Sinks/Listeners)|100%|... %|
|3|[Tên Sinh Viên 3]|[MSV 3]|Quản lý Auth (JWT), Database, chức năng Admin, Auto-Bidding|100%|... %|
|4|[Tên Sinh Viên 4]|[MSV 4]|Tích hợp hệ thống, xử lý Bid History, viết báo cáo & quay Video Demo|100%|... %|

- **Link GitHub Repository:** [Điền link GitHub nhóm]
- **Link thư mục Drive (chứa Video demo):** [Điền link Drive]