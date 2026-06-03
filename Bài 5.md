# BÁO CÁO CÁ NHÂN: ỨNG DỤNG TRÍ TUỆ NHÂN TẠO TẠO SINH TRONG SÁNG TẠO NỘI DUNG SỐ

**Thông tin sinh viên:**

- **Họ và tên:** Phạm Thiên Minh
- **Mã sinh viên:** 25021887
- **Học phần:** Nhập môn công nghệ số và ứng dụng trí tuệ nhân tạo

## I. GIỚI THIỆU DỰ ÁN VÀ CÔNG CỤ SỬ DỤNG

**1. Lựa chọn dự án:**

Sản phẩm sáng tạo được lựa chọn là một Video thuyết trình ngắn (thời lượng 7 phút) với chủ đề: _"Ứng dụng AI trong tối ưu hóa quy trình CI/CD và Kỹ thuật phần mềm"_. Sản phẩm yêu cầu sự kết hợp giữa kiến thức chuyên môn về lập trình và tư duy hình ảnh để truyền tải thông tin kỹ thuật một cách trực quan.

**2. Công cụ AI tạo sinh đã sử dụng:**

Để hoàn thiện dự án, tôi đã thiết lập quy trình làm việc kết hợp 3 công cụ AI thuộc 3 nhóm khác nhau:

- **Công cụ tạo văn bản:** Gemini (Hỗ trợ xây dựng cấu trúc kịch bản và rà soát lỗi logic).
    
- **Công cụ tạo hình ảnh:** Midjourney (Tạo các tư liệu hình ảnh minh họa chất lượng cao).
    
- **Công cụ hỗ trợ thiết kế:** Canva AI - Magic Design & Magic Animate (Tích hợp, tạo hiệu ứng chuyển động và hậu kỳ video).
    

## II. QUÁ TRÌNH SÁNG TẠO VÀ TÍCH HỢP (Đóng góp cá nhân > 50%)

Thay vì phó mặc hoàn toàn cho máy móc, tôi áp dụng quy trình kiểm soát chặt chẽ, trong đó AI đảm nhận khoảng 40% khối lượng (tạo vật liệu thô), 60% còn lại là tư duy dẫn chuyện và kiểm chứng kỹ thuật của cá nhân.

**1. Giai đoạn 1: Xây dựng kịch bản với Gemini**

- **Prompt đã sử dụng:** _"Hãy đóng vai một kỹ sư phần mềm. Viết một kịch bản video dài 3 phút giải thích cách tích hợp AI vào pipeline CI/CD trên GitHub Actions. Phân chia rõ cột 'Hình ảnh/Video' và cột 'Lời bình (Voiceover)'. Ngôn ngữ chuyên nghiệp, có đề cập đến quá trình build Maven và test bằng JaCoCo."_
- **Kết quả & Chỉnh sửa (Tích hợp sáng tạo):** Gemini cung cấp một khung kịch bản khá đầy đủ các bước. Tuy nhiên, ở phần minh chứng độ phức tạp thuật toán, AI đưa ra một biến đổi bất đẳng thức sai logic. Tôi đã phải trực tiếp chỉnh sửa và chuẩn hóa lại công thức toán học thành $|f(x)|+|f(0)| \ge |f(x)-f(0)|$ để đảm bảo tính chính xác tuyệt đối. Ngoài ra, tôi viết lại toàn bộ phần mở đầu (hook) theo cấu trúc narrative (kể chuyện) để tăng tính lôi cuốn, thay vì lối liệt kê khô khan của AI.

> _[Chèn Ảnh 1: Ảnh chụp màn hình giao diện chat với Gemini, hiển thị prompt chi tiết]_
> 
> _[Chèn Ảnh 2: Ảnh chụp màn hình bản kịch bản trên Google Docs, với các đoạn highlight thể hiện phần chỉnh sửa, bổ sung công thức và viết lại lời bình của Phạm Thiên Minh]_

**2. Giai đoạn 2: Khởi tạo tư liệu thị giác với Midjourney**

- **Prompt đã sử dụng:** _"A cinematic shot of a futuristic server room, glowing blue and green data streams representing continuous integration, depth of field, dramatic lighting, 8k resolution, --ar 16:9 --v 6.0"_
- **Kết quả & Chỉnh sửa (Tích hợp sáng tạo):** Midjourney xuất ra các hình ảnh có chất lượng ánh sáng (cinematography) rất xuất sắc. Tuy nhiên, AI thường mắc lỗi tạo ra các đoạn code vô nghĩa (gibberish text) trên các màn hình máy tính trong ảnh. Để khắc phục, tôi đã đưa ảnh vào Photoshop, xóa bỏ các đoạn text lỗi này, sau đó tự chèn các đoạn mã Java thực tế (chứa các thread `ExecutorService` và `Callable`) của mình lên trên bề mặt màn hình mô phỏng để tăng tính chân thực.
    

> _[Chèn Ảnh 3: Ảnh chụp màn hình giao diện Discord lúc gửi prompt cho con bot Midjourney]_
> _[Chèn Ảnh 4: Ảnh so sánh (Before/After) giữa ảnh gốc của Midjourney và ảnh đã được tôi chỉnh sửa lại bằng Photoshop/Canva]_

**3. Giai đoạn 3: Thiết kế chuyển động và Hậu kỳ với Canva AI**

- **Quá trình:** Tôi upload hình ảnh, lời bình đã thu âm lên Canva. Sử dụng _Magic Animate_ để tạo hiệu ứng xuất hiện cho các block text và _Beat Sync_ để khớp các cảnh quay với nhịp điệu nhạc nền.
- **Kết quả & Chỉnh sửa (Tích hợp sáng tạo):** Chức năng AI của Canva giúp tiết kiệm thời gian tạo keyframe. Dù vậy, AI cắt cảnh đôi lúc bị lệch nhịp so với lời thuyết trình. Tôi đã phải can thiệp thủ công trên timeline, điều chỉnh lại nhịp độ cắt cảnh (pacing) và áp dụng các quy tắc về bố cục 1/3 để các dòng text không che khuất chủ thể bức ảnh.

> _[Chèn Ảnh 5: Ảnh chụp không gian làm việc của Canva, hiển thị timeline video, các lớp âm thanh, hình ảnh và công cụ Magic Animate đang được kích hoạt]_

## III. SO SÁNH VÀ PHÂN TÍCH CÔNG CỤ

Qua quá trình thực hiện, sự khác biệt về hiệu năng và đặc thù của 3 công cụ AI được bộc lộ rất rõ ràng:

- **Gemini (Văn bản):** Điểm mạnh lớn nhất là khả năng hệ thống hóa ý tưởng nhanh chóng và nắm bắt tốt các thuật ngữ chuyên ngành (CI/CD, JaCoCo). Tuy nhiên, điểm hạn chế chí mạng là AI thỉnh thoảng sinh ra "ảo giác" (hallucination) trong các suy luận toán học hoặc logic lập trình phức tạp. Điều này đòi hỏi người dùng phải có nền tảng chuyên môn vững để "khám lỗi" (debug) nội dung.
    
- **Midjourney (Hình ảnh):** Vượt trội hoàn toàn về mặt thẩm mỹ, có khả năng hiểu các thuật ngữ về góc máy, ánh sáng điện ảnh (cinematic lighting). Tuy nhiên, rào cản lớn nhất là khả năng kiểm soát chi tiết nhỏ. Midjourney rất tệ trong việc render văn bản cụ thể và khó duy trì tính nhất quán của một vật thể qua nhiều bức ảnh khác nhau.
    
- **Canva AI (Thiết kế/Video):** Điểm mạnh là giao diện thân thiện, biến các thao tác hoạt hình phức tạp thành một cú click chuột (Magic Animate). Dù vậy, thuật toán AI của Canva mang tính "công nghiệp" và dập khuôn. Nó thiếu đi sự tinh tế và khả năng tùy biến sâu theo từng khung hình (frame-by-frame) như các phần mềm dựng phim chuyên nghiệp truyền thống.
    

## IV. PHÂN TÍCH VÀI TRÒ CỦA AI VÀ VẤN ĐỀ ĐẠO ĐỨC

**1. Vai trò của AI và sự thay đổi trong quy trình sáng tạo**

Sự xuất hiện của Gen AI đã định hình lại hoàn toàn cách tôi tiếp cận một dự án nội dung số. Thay vì bắt đầu từ một "trang giấy trắng", tốn hàng giờ để tự vẽ phác thảo hay gõ từng dòng ý tưởng, tôi giờ đây bắt đầu với vai trò của một **Người giám tuyển (Curator) và Đạo diễn (Director)**.

AI giúp triệt tiêu hoàn toàn "hội chứng sợ trang giấy trắng", đảm nhận việc tạo ra khối lượng lớn vật liệu thô trong thời gian ngắn. Tuy nhiên, hồn cốt của sản phẩm—nhịp điệu kể chuyện, độ chính xác của thông tin kỹ thuật, và thông điệp cốt lõi—vẫn phụ thuộc hoàn toàn vào tư duy phân tích của con người. Quy trình sáng tạo chuyển dịch từ _Sản xuất thủ công (Creation)_ sang _Định hướng và Tinh chỉnh (Curation & Refinement)_.

**2. Các vấn đề đạo đức cần cân nhắc**

Việc sử dụng rộng rãi AI tạo sinh đặt ra ba vấn đề đạo đức nghiêm túc mà người làm nội dung phải đối mặt:

- **Bản quyền dữ liệu huấn luyện:** Các bức ảnh tuyệt đẹp từ Midjourney được tạo ra nhờ việc học hỏi từ hàng triệu tác phẩm có bản quyền của các họa sĩ trên internet mà chưa có sự đồng ý.
    
- **Tính minh bạch (Transparency):** Khán giả có quyền được biết một sản phẩm có sự can thiệp của máy móc hay không. Việc nhận vơ 100% công sức cho một video do AI tạo ra là vi phạm liêm chính học thuật. Do đó, tôi đã đính kèm một nhãn nhỏ "Assisted by AI" ở góc màn hình trong sản phẩm cuối cùng.
    
- **Sự lan truyền thông tin sai lệch (Misinformation):** Khi AI bị ảo giác và đưa ra một công thức sai (như trong trường hợp kịch bản của tôi), nếu người tạo nội dung lười biếng và không rà soát, những kiến thức sai lệch này sẽ được đóng gói dưới một vỏ bọc video vô cùng chuyên nghiệp và đáng tin cậy, gây hại trực tiếp đến người tiếp nhận.
    

## V. KẾT LUẬN

Dự án đã chứng minh rằng: AI tạo sinh là một đòn bẩy công nghệ mạnh mẽ, nhưng nó không thể thay thế năng lực tư duy phê phán và gu thẩm mỹ cá nhân. Để tạo ra một sản phẩm số có giá trị thực sự, sự kết hợp hài hòa giữa "trí tuệ nhân tạo" và "sự tinh tế của con người" là điều kiện tiên quyết.

_(Đính kèm thư mục chứa sản phẩm Video MP4 cuối cùng và các file kịch bản thô)_