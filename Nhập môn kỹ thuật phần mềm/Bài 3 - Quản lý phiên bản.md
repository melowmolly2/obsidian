# Git
## 1. Giới thiệu về Git
Git là 1 dạng hệ thống VCS phân tán, được tạo ra và phát triển bởi Linus Torvalds từ 2005. Git cung cấp cho mỗi lập trình viên kho lưu trữ (repository) riêng chứa toàn bộ lịch sử thay đổi. 

Một số đặc điểm nổi bật nhát của Git:
- Thiết kế đơn giản
- Tốc độ nhanh
- Hỗ trợ tốt việc tạo ra và xử lý các nhánh song song đẻ nhóm phát triển có thể làm việc trong cùng một dự án. 
Sự khác biệt chính giữa Git và bất kỳ VCS nào khác (bao gồm Subversion...) là cách Git nghĩ về dữ liệu của nó. Git coi thông tin được lưu trữ là một tập hợp các snapshot - ảnh chụp toàn bộ nội dung tất cả các file tại thời điểm. Mỗi khi bạn commit, Git sẽ "chụp" và tạo ra một snapshot cùng một tham chiếu tới snapshot đó. Để hiệu quả, nếu các tệp không thay đổi, Git sẽ không lưu trữ lại file - chỉ là một liên kết đến tệp giống file trước đó mà nó đã lưu trữ. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/ISKr-W1wWqY?si=Vi-LF8bgrgzmFy8L" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
## 2. Cài đặt Git

Các bạn có thể thực hiện theo chỉ dẫn ở video dưới đây và tìm kiếm thêm các cách hướng dẫn khác trên Google để cài đặt được phiên bản Git phù hợp với hệ điều hành của bạn (Linux, MacOS và Windows)

## 3. Luồng công việc của Git (bài học quan trọng)
**4 dạng lưu trữ cơ b