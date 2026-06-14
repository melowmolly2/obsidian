# TÀI LIỆU ĐẶC TẢ YÊU CẦU (SRS)
**Dự án: Hệ thống Web Quản lý Dự án Công ty X**

## 1. Giới thiệu tổng quan về tài liệu
**1.1. Mục đích của tài liệu:**
Tài liệu này cung cấp mô tả chi tiết về Hệ thống Web quản lý dự án cho Công ty X. Phần mềm giúp quản lý các kế hoạch thực hiện (milestones), bản chuyển giao (releases) và các vấn đề (issues) của các dự án nhằm tối ưu hóa công việc và theo dõi tiến độ hiệu quả.

**1.2. Phạm vi của tài liệu:**
Hệ thống được triển khai ở mức phòng ban và trung tâm của Công ty X. Nó xác định các tính năng quản lý dự án và thiết lập cơ sở phân quyền để nhân sự có thể làm việc chéo giữa các bộ phận khi được cấp quyền.

## 2. Tổng quan hệ thống và đặc tả chức năng
**2.1. Đặc tả người dùng:**
*   **Thành viên trực thuộc (Phòng ban/Trung tâm):** Có quyền mặc định truy cập để quản lý thông tin các dự án, issues, milestones và releases thuộc bộ phận mình.
*   **Nhân sự ngoài bộ phận:** Các thành viên phòng ban khác được phân quyền truy cập dự án để xem hoặc quản lý thông tin issue tùy mức độ quyền.

**2.2. Sơ đồ ngữ cảnh (Context Diagram)**
*Sơ đồ thể hiện sự tương tác giữa các nhóm người dùng và hệ thống.*

```mermaid
graph TD
    A[Thành viên bộ phận] -->|Truy cập mặc định toàn quyền| S((Hệ thống Web Quản lý Dự án Công ty X))
    B[Nhân sự ngoài bộ phận] -->|Truy cập theo phân quyền| S
    S -->|Cung cấp thông tin tiến độ, issues, milestones| A
    S -->|Cung cấp thông tin được phép xem| B
````

**2.3. Sơ đồ Use-case tổng quát** _Sơ đồ thể hiện các chức năng chính của hệ thống dựa trên nền tảng GitLab._

```mermaid
flowchart LR
    A((Thành viên bộ phận))
    B((Nhân sự ngoài bộ phận))

    UC1([Quản lý thông tin dự án])
    UC2([Quản lý Milestones])
    UC3([Quản lý Releases])
    UC4([Quản lý Issues])

    A --> UC1
    A --> UC2
    A --> UC3
    A --> UC4

    B -.->|Được phân quyền| UC2
    B -.->|Được phân quyền| UC4
```

## 3. Đặc tả yêu cầu chức năng (Chi tiết Use Case)

**3.1. Đặc tả Use Case: Quản lý Issues (Tạo mới Issue)**

| **Đặc điểm**     | **Mô tả**                                                                                                                                                                                                     |
| :--------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Tên Use Case** | Tạo mới Issue                                                                                                                                                                                                 |
| **Điều kiện**    | Người dùng đã đăng nhập. Là thành viên bộ phận quản lý dự án hoặc nhân sự ngoài đã được phân quyền.                                                                                                           |
| **Luồng chính**  | 1. Chọn dự án cần thao tác.2. Truy cập menu "Issues".3. Hệ thống hiển thị danh sách issues.4. Chọn "Tạo Issue".5. Điền thông tin (Tiêu đề, mô tả, Assignee, Milestone).6. Hệ thống lưu và hiển thị Issue mới. |
| **Luồng phụ**    | Nếu truy cập dự án không có quyền, hệ thống báo lỗi không đủ quyền hoặc ẩn menu "Issues".                                                                                                                     |

**3.2. Hệ thống cấp quyền**

| **Chức năng**              | **Thành viên trực thuộc** | **Nhân sự ngoài (Được cấp quyền)** |
| :------------------------- | :------------------------ | :--------------------------------- |
| Xem dữ liệu dự án          | X                         | X                                  |
| Cập nhật Milestones/Issues | X                         | X (Tùy dự án)                      |
| Xóa dữ liệu                | X                         |                                    |

## 4. Yêu cầu phi chức năng

1. **Tính bảo mật:** Dữ liệu dự án của phòng ban chỉ được truy cập bởi thành viên phòng ban đó. Nhân sự ngoài phải qua phân quyền rõ ràng trên hệ thống.
2. **Tính sẵn sàng:** Hệ thống hoạt động 24/7 để nhân sự các trung tâm/phòng ban khác nhau cập nhật tiến độ liên tục.
3. **Khả năng sử dụng:** Giao diện trực quan, menu cấu trúc dạng cây bên trái (Projects, Members, Releases, Issues, Milestones) tương tự GitLab.
