# Hệ thống kiểm soát phiên bản

Trong bài học này, chúng ta sẽ được học về hệ thống kiểm soát phiên bản (Version Control System - VCS) và tập trung vào một công cụ điển hình là Git.

## 1. Hệ thống kiểm soát phiên bản (VCS)

VCS là một hệ thống lưu giữ các phiên bản mã nguồn của sản phẩm phần mềm, giúp các lập trình viên có thể dễ dàng lấy lại phiên bản mong muốn. 
![](../Assets/Pasted%20image%2020260613160214.png)
**Tính hữu dụng của VCS**:
- Sử dụng VCS tạo nên sự kỷ luật, bởi vì nó quản lý quy trình kiểm soát các mục/thông tin truyển từ người này sang người khác 
- VCS cho phép lưu trữ và so sánh các phiên bản khác nhau của mã nguồn. 
- Duy trì nhiều thông tin lịch sử quan trọng của các phiên bản. 
- Giúp mọi người chia sẻ mã nguồn và tài liệu dễ dàng hơn. 
- Phục hồi và chỉnh sửa lại sau những thao tác sai/lỗi với mã nguồn. 
- Tiết kiệm dung lượng ở đĩa khi chỉ sử dụng một trung tâm lưu trữ các bản sao của phần mềm (với các thuật toán lưu trữ hiệu quả).
<iframe width="560" height="315" src="https://www.youtube.com/embed/zbKdDsNNOhg?si=CyLvZduG1RJmwPOq" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
## 2. Các hoạt động chính của VCS
![](../Assets/Pasted%20image%2020260613161019.png)
VCS có 3 thao tác chính: Add, Commit, Update.
**Add**: Bổ sung/thêm các tệp tin vào kho lưu trữ 
**Commit**: Khi bạn thay đổi một tập tin ở trong kho luuw trữ, bạn cần cam kết những thay đổi của mình với trung tâm lưu trữ, để chúng có thể trở nên hiển thị với tất cả những người khác trong kho lưu trữ.
**Update**: Nếu chúng ta có một kho lưu trữ và một ai đó khác có thể chỉnh sửa các tệp tin trong kho lưu trữ, và ta muốn nhận được những thay đổi này. 
<iframe width="560" height="315" src="https://www.youtube.com/embed/R7rxewbCm38?si=7OsWTUESQa9SMkYb" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
## 4. Những điều cần tránh trong VCS
![](../Assets/Pasted%20image%2020260613162715.png)
### 4.1 Chúng ta không nên upload 2 loại file sau lên VCS:
**Tệp thực thi:** Bạn đã upload mã nguồn lên VCS do đó không cần thiết phải đẩy tệp thực thi, vì tchungs ta không thể chạy hay đọc tệp thực thi trên VCS. 
**Dữ liệu:** Chỉ upload nó lên Git khi thực sự cẩn thiết. 
### 4.2 Không nên tạo một phiên bản copy của VCS: 
Việc này là không cần thiết và có thể gây ra những sai lầm không đáng có khi bạn copy qua lại các đoạn mã nguồn, hãy học cách sử dụng các câu lệnh để kiểm soát phiên bản. 
<iframe width="560" height="315" src="https://www.youtube.com/embed/rztIbOqxp_I?si=X3VdDfV9yFpZ5O_F" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
## 5. Hai loại VCS chính
![](../Assets/Pasted%20image%2020260613163300.png)
**VCS tập trung**: Với các VCS dạng tập trung thì mã nguồn của dự án sẽ được lưu trữ trên một kho tập trung (hay kho trung tậm) trên một máy chủ. Mỗi lập trình viên muốn tạo ra sự thay đổi cho mã nguồn lưu trữ trong kho trung tâm (centralized repository) thì họ cần phải thực hiện môitj
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
**4 dạng lưu trữ cơ bản:**
- Workspace (working dir): Không gian làm việc, thư mcuj cục bộ ở trên thiết bị của bạn.
- Index (stage): Khu vực sẽ lưu trữ những thay đổi của bạn trên tập tin để nó có thể được commit. 
- Local repository (head): Kho lưu trữ cục bộ, thường nằm ở trên thiết bị của bạn. 
- Remote repository: Kho lưu trữ từ xa (hay trung tâm).
Đầu tiên, để có thể truy cập và lấy về resource từ một remote repository, chúng ta thường sử dụng `git clone "remote repository url"`. Khi đó, chúng ta sẽ có một bản sao ở thiết bị của bạn. Nếu bạn tự tạo kho lưu trữ thì không cần làm bước này. 

Nếu tập tin đang ở trên máy của bạn, nó có thể nằm ở 11 trong 3 trạng thái/dạng lưu trữ. 

Nếu bạn đang chỉnh sửa và làm việc với nó, nó sẽ nằm ở workspace. Nếu bạn muốn thêm những tập tin được thay đổi, chỉnh sửa lên stage để xem xét xem mình có commit hay không thì sẽ sử dụng lệnh `git add`. Khi đó, tập tin sẽ được đánh dấu là được xem xét để commit (nhưng chưa commit). Bên cạnh đó, `git add -u` xem xét tất cả các tệp được theo dói và thực hiện các thay đổi đối với các tệp đó nếu chúng khác hoặc nếu chúng đã bị xóa. 

Sau khi đã lên stagin,g nếu bạn muốn đẩy tệp tin lên local repository thì bạn cần `git commit`. Khi đó, những thay đổi trong tập tin của bạn sẽ được lưu trữ trong local repository. Bạn có thực thi cả bước add và commit bằng câu lệnh `git commit -a`. Câu lệnh này sẽ giúp bạn đánh dấu, sắp xếp các tệp tin đã chỉnh sửa và commit chúng. 

