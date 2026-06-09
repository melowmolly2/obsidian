# 1. Giới thiệu cơ bản về JSP Hello World
- JSP (JavaServer Pages) là một công nghệ để phát triển các trang web động. JSP giúp các nhà phát triển chèn java code vào các trang HTML bằng cách sử dụng các thẻ JSP đặc biệt. 
- JSP là một kiểu Java servlet được thiết kế để tạo ra giao diện người dùng cho một ứng dụng Java web. Các nhà phát triển web viết các JSP như các tệp văn bản kết hợp mã HTML hoặc XHTML, các phần tử XML, các action và lệnh JSP. 
- Sử dụng JSP, bạn có thể thu thập dữ liệu đầu vào từ người dùng thông qua các Form của trang web, trình bày các bản ghi từ một cơ sở dữ liệu hoặc một nguồn khác, và tạo các trang web động.
- Kiến trúc JSP bao gồm các thành phần chính nhwu sau:
	1. Client: Là một phần mềm hoặc thiết bị mà người dùng sử dụng để truy cập vào từ trang web. 
	2. Server: Là một máy tính chứa ứng dụng JSP và đáp ứng các yêu cầu từ khách hàng
	3. Web container: Là một phần mềm được chạy trên máy chủ và lắng nghe các yêu cầu từ client, xử lý các yêu cầu này và trả về kết quả
	4. JSP page: Là một tài liệu HTML hoặc XML được xử dụng để tạo ra các ứng dụng web. Trong JSP page, ta có thể sử dụng các thẻ JSP để chèn mã Java vào HTML.
	5. Servlet: Là một lớp Java đucợ sử dụng để xử lý các yêu cầu ở phía máy chủ. Servlet được sử dụng để tạo và xử lý các biểu mẫu, thực thi các truy vấn cơ sở dữ liệu và thực hiện các tác vụ khác. 
	6. JavaBeans: Là các lớp Java được sử dụng để lưu trữ và xử lý dữ liệu trong ứng dụng web. JavaBeans được sử dụng để lấy dữ liệu từ cơ sở dữ liệu, lưu dữ liệu vào cơ sở dữ liệu và thực hiện các tác vụ khác. 
- Vị trí của JSP trong một ứng dụng web:
	- JSP thực hiện tiến trình xử lý trên Server
	- Kết quả sẽ trả về một trang HTML bao gồm dữ liệu mong muốn đi kèm. 
 