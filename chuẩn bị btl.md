

Frontend

Dự án dử dụng mô hình gần giống MVC
Kiến trúc project chia thành các tầng:
Controller: xử lí javafx, sự kiện,
Service: xử lí nghiệp vụ client, validate, gọi API,
Network: cấu hình Retrofit, Stream realtime, ...,
DTO: class request/response,
Model: trạng thái phiên đăng nhập, balance,


Luồng đi:
User -> Controller -> Service -> Network -> Backend

Entry point của App: AuctionLauncher.java

*Phần controller

Mới vào là có Landing Page, có thể vào Login Page hoặc Register Page
Đăng nhập xong sẽ có 1 cái Framework.fxml, Framework chứa mọi thứ ở trong: các tab Dashboard, MySale, Browse Auction, Account.

Trong browseAuction, khi lướt sẽ có các Card.fxml, ấn vào Card.fxml sẽ tuỳ vào người ấn mà chuyển trang. Nếu là seller thì đưa qua SellerViewPage.fxml, nếu là Bidder thì đưa qua BidderViewPage.fxml

Mỗi trang trên browseAuction có size = 4, có thể chuyển trang khi có nhiều hơn 4

SceneManager.java: Phụ trách chuyển hướng màn hình: 
changeScreen(): chuyển hướng toàn bộ màn hình,
changeContent(): thay đổi nội dung trong Framework,

Retrofit Callback chạy ở trong 1 background thread, Platform.runLater(). Cập nhật UI trên thread chính.

Bid history Visualization: Biểu đồ hiển thị trục Ox là lần bid, Oy là % thay đổi theo giá gốc. Dữ liệu biểu đồ lưu trong 1 cái list, khi thoát sẽ mất. Chart được cập nhật realtime từ priceListener
Để tránh gọi API quá nhiều, controller dùng bidHistoryLoading và lastBidHistoryRequestMillis với khoảng cách tối thiểu 1.5 giây.

ContentLifecycle là interface tạo để quản lý vòng đời của các content trong SceneManager. Những màn có tài nguyên chạy nền như realtime price stream sẽ implement interface này. Khi đổi content, SceneManager gọi dispose() của màn cũ để dừng stream, đóng connection và tránh thread cũ tiếp tục cập nhật UI.

Hệ thống thông báo: AppPopup.java có các hàm static như info, error, warning được chạy trên Platform.runLater(), có tác dụng thông báo dùng chung toàn app.


*Phần Network

Khi đăng nhập, server cấp cho user 1 cái access token, khi frontend cần truy cập vào backend, cần có access token.

Access token được đính kèm ở phần Head có dạng "Authorization: Bearer <accessToken>", phần Body chứa nội dung, phần nội dung đó được định nghĩa ở DTO.

Retrofit là 1 thư viện HTTP Client, giúp ứng dụng giao tiếp với REST API một cách đơn giản. Lí do lựa chọn công nghệ này? Giảm lượng code xử lí HTTP, tự động chuyển đổi JSON qua object Java. (giảm thời gian viết code)

AuthInterceptor.java, mọi request xác thực đều đi qua interceptor, tại đây sẽ được gắn token vào, giúp code service gọn hơn


*Phần model và DTO:
AccountSession.java: balance được lưu ở đây

*Phần service: chịu trách nhiệm xử lí logic nghiệp vụ, gọi API Retrofit bằng .enque(), trả về kết quả cho controller thông qua callback như onSuccess() hoặc onError()

Dự án này bao nhiêu phần trăm là AI làm? 50%
Điểm yếu của frontend này là gì? Token đang lưu trong memory static nên tắt app sẽ mất session

backup question:

- frontend có bị block UI không? không, vì đã sử dụng Platform.runLater(). Khi gọi REST API thì sử dụng .enqueue(), các Listener thì dùng ở các thread khác rồi.
- Design patter của frontend thế nào? Tổ chức theo MVC. Có cả Observer Pattern (realtime) nữa

1 câu 99% mai hỏi: "Frontend thì kết nối API thông qua cái gì?"
1. Frontend không gọi HTTP thủ công cho REST API mà dùng Retrofit. AuctionApi là interface khai báo endpoint bằng annotation như @GET, @POST, @Body, @Path, @Query. ApiClient tạo Retrofit instance với base URL [http://localhost:8080/](http://localhost:8080/ "http://localhost:8080/"), Gson để convert JSON và OkHttp để gắn interceptor token. Các service gọi .enqueue() để request bất đồng bộ, tránh block UI. AI answer
2. Retrofit
3. Nhớ tên nha
4. Thư viện retrofit 
5. Phụ trách là ApiClient
6. Các endpoint ở interface AuctionAPI
7. CRUD trong REST API
Create: @POST,
Read: @GET,
Update: @PUT,
DELETE: @DELETE,
:sunglasses:
Click to react
:thumbsup:
Click to react
:heart:
Click to react
Add Reaction
Reply
Forward
More

Alt + F4 [LC], Server Tag: LCLC — 9:56 PMSunday, June 7, 2026 9:56 PM
Tại sao lại chọn?,
+ Tại sao backend lại Gradle, frontend lại Maven: vì backend muốn ưu tiên build nhanh, còn frontend muốn ưu tiên mức độ dễ hiểu và tính cấu trúc. Thực ra do nhóm chưa có sự thống nhất ban đầu
+ Tại sao lại chọn Spring boot? Vì đây là framework Java nổi tiếng, tích hợp sẵn nhiều tính năng, giảm lượng code cấu hình, tăng tốc độ phát triển
+ Tại sao lại chọn Retrofit? Vì thư viện giảm lượng code xử lí HTTP, tự động chuyển đổi JSON qua object Java, giúp quá trình code diễn ra nhanh hơn
+ Tại sao lại chọn JWT? Nhóm chọn JWT vì hệ thống được xây dựng theo mô hình client-server với REST API. JWT cho phép xác thực stateless, không cần lưu session trên server, giúp backend dễ mở rộng và tích hợp thuận tiện với JavaFX thông qua Retrofit.
+ Tại sao chọn SQLite? Vì đây là dự án học tập ít người dùng, SQLite không cần có máy chủ riêng, cấu hình đơn giản & triển khai nhanh hơn
:CRUD trong REST API
- Create: @POST
- Read: @GET
- Update: @PUT
- DELETE: @DELETE
- Tại sao lại chọn?
+ Tại sao backend lại Gradle, frontend lại Maven: vì backend muốn ưu tiên build nhanh, còn frontend muốn ưu tiên mức độ dễ hiểu và tính cấu trúc. Thực ra do nhóm chưa có sự thống nhất ban đầu
+ Tại sao lại chọn Spring boot? Vì đây là framework Java nổi tiếng, tích hợp sẵn nhiều tính năng, giảm lượng code cấu hình, tăng tốc độ phát triển
+ Tại sao lại chọn Retrofit? Vì thư viện giảm lượng code xử lí HTTP, tự động chuyển đổi JSON qua object Java, giúp quá trình code diễn ra nhanh hơn
+ Tại sao lại chọn JWT? Nhóm chọn JWT vì hệ thống được xây dựng theo mô hình client-server với REST API. JWT cho phép xác thực stateless, không cần lưu session trên server, giúp backend dễ mở rộng và tích hợp thuận tiện với JavaFX thông qua Retrofit.
+ Tại sao chọn SQLite? Vì đây là dự án học tập ít người dùng, SQLite không cần có máy chủ riêng, cấu hình đơn giản & triển khai nhanh hơn

nếu thầy hỏi có race condition ko thì bảo là chỉ có một thread đọc và ghi cơ sở dữ liệu:
spring.datasource.hikari.maximum-pool-size=1