# Các giai đoạn phát triển phần mềm truyền thống

Nội dung đầu tiên chúng ta tìm hiểu sẽ chỉ ra các giai đoạn trong công việc phát triển phần mềm truyền thống được trình bày trong bài học theo quan điểm của Barry Bohem bao gồm:
- Kỹ thuật yêu cầu
- Thiết kế 
- Thực hiện
- Xác minh và thẩm định
- Bảo trì
<iframe width="560" height="315" src="https://www.youtube.com/embed/9M_gr1W9HuU?si=AdCuuGASNNa0mfDW" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## 1. Kỹ thuật yêu cầu

**Kỹ thuật yêu cầu** là lĩnh vực liên quan đến xác định các yêu cầu của các bên liên quan mà sẽ được giải quyết bởi phần mềm

Tại sao giai đoạn này lại quan trọng? Bởi vì việc phát hiện lỗi càn muôn trong quá trình phát triển sẽ dẫn đến chi phí sửa chữa càng cao. Do đó, giai đoạn này có vai trò rất quan trọng để giảm rủi ro và chi phí phát sinh trong quá trình xây dựng hệ thống. 

Các bước có thể thu thập được yêu cầu phần mềm:
- **Khơi gợi yêu cầu** từ các bên liên quan và các nguồn khác
- **Phân tích yêu cầu**, bao gồm sự nghiên cứu và hiểu sâu hơn về các yêu cầu mang tính tập hợp
- **Đặc tả các yêu cầu**, trong đó các yêu cầu mang tính tập hợp được trình bày, tổ chức và lưu trữ phù hợp để có thể chia sẻ chung.
- **Xác thực các yêu cầu** để bảo đảm rằng chúng đã hoàn chỉnh, nhất quán, không dư thừa, thỏa mãn một tập hợp các thuộc tính quan trọng cho các yêu cầu. 
- **Quản lý yêu cầu**, để giải thích cho các thay đổi đối với các yêu cầu trong suốt vòng đời của dự án.
## 2. Thiết kế 

Thiết kế phần mềm là giai đoạn mà các yêu cầu phần mềm được phân tích để đưa ra một mô tả về cấu trúc và tổ chức bê ntrong của hệ thống. Và mô tả này sẽ là cơ sở cho cấu trúc của hệ thống thực. Một cách truyền thống, giai đoạn thiết kế phần mềm đưa ra một chuỗi các hoạt động thiết kế, bao gồm:
- Thiết kế kiến trúc
- Thiết kế giao diện
- Thiết kế thành phần
- Thiết kế thuật toán
- ...
Nếu chúng ta đọc các cuốn sách hay giáo trình khác nhau, các hoạt động thiết kế có thể được mô tả theo nhiều cách khác nhau. Ý tưởng cốt lõi và điểm quan trọng ở đây là chúng ta đi từ góc nhìn bao quát hơn về hệ thống (thiết kế kiến rúc) đến một góc nhìn hẹp hơn (thiết kế thuật toán). Và các hoạt động này dẫn đến một bộ các sản phẩm thiết kế mô tả các đặc điểm khác nhau của hệ thống. 
<iframe width="560" height="315" src="https://www.youtube.com/embed/ZEhYRLMEbVw?si=i2_PJpaNO0Czrtrf" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
## 3. Thực hiện phần mềm
Sau khi nhận được tài liệu thiết kế hệ thống, công việc được chia thành các mô-đun/đơn vị và công việc lập trình được bắt đầu. Trong giai đoạn này mã nguồn được tạo ra, do đó, nó là trọng tậm chính cho phát triển phần mềm. Đây là giai đoạn dài nhất của vòng đời phát triền phần mềm. 

Có 4 quy tắc cơ bản có thể ảnh hưởng đến cách thức mà một phần mềm được xây dựng:
- **Giảm mức độ phức tạp:** Xây dựng phần mềm đơn giản hơn để hiểu và sử dụng
- **Dự đoán về sự điều chỉnh**: Xây dựng phần mềm mà có thể dễ dàng kiểm tra qua các hoạt động xác minh và thẩm định tiếp theo. 
- **Hỗ trợ kiểm thử, thẩm định:** Xây dựng phần mềm mà có thể dễ dàng kiểm tra qua các hoạt động xác minh và thẩm định tiếp theo. 
- **Tuân thủ các chuẩn tắc**: Các chuẩn ở đây có thể là chuẩn nội bộ hoặc chuẩn bên ngoài liên quan đến phần mềm. 
<iframe width="560" height="315" src="https://www.youtube.com/embed/skpVpuB8VBY?si=P4ItOPVd-XjcD_2M" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
## 4. Xác minh và thẩm định
Sau khi xây dụng hệ thống, xác minh và thẩm định là giai đoạn tiếp theo cảu phát triển phần mềm nhằm mục đích kiểm tra xem hệ thống phần mềm có đáp ứng được đặc điểm kỹ thuật của nó cũng như đáp uns được mục tiêu dự định hay không. 

**Thẩm định** là hoạt động trả lời cho câu hỏi: Có phải chúng ta đã xây dụng hệ thống mà khách hàng mong muốn?

**Xác minh** trả lời một câu hỏi khác, có phải chúng ta đã xây dụng hệ thống đúng theo đặc tả hay không. Có nhiều cấp độ xác minh khác nhau: Đơn vị, tích hợp, hệ thống. 
<iframe width="560" height="315" src="https://www.youtube.com/embed/gQrSxbfUjug?si=5eN-QU6ijPOI0l3p" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
## 5. Bảo trì
Khi phần mềm đã triển khai cho khác hàng, nhiều yêu cầu mới vẫn được đặt ra như: Có sự thay đổi về môi trường sử dụng phần mềm, khách hàng muốn có thêm chức năng, hệ thống đang sử dụng cần tích hợp vào các hệ thống khác hay khách hàng phát hiện ra lỗi mới, vv. 

Từ đó dẫn đến các công việc bảo trì tương ứng. Bảo trì phần mềm là hoạt động duy trì sản phầm phần mềm khi nó phát triển qua suốt vòng đời của mình, đặc biệt trong việc phản hồi các báo cáo lỗi, yêu cầu tính năng và thay đổi môi trường. Các tổ chức phát triển thực hiện ba loại hoạt động bảo trì. 
- Sửa chữa để loại bỏ các vấn đề với code
- Hoàn chỉnh để đáp ứng yêu cầu về tính năng
- Cải thiện phần mềm 
Đây thường là giai đoạn tốn kém nhất trong vòng đời của phần mềm. 
<iframe width="560" height="315" src="https://www.youtube.com/embed/0Y8YLMJ3ERw?si=0gcowmZZ6KABN8O8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

# Mô hình quy trình phần mềm 
Tại thời điểm này, chúng ta đã biết các hoạt động có khả năng, các giai đoạn thể hiện trong suốt quá trình phát triển phần mềm. Nhưng có những nội dung rất quan trọng chúng ta vẫn chưa thảo luận. Đó là **nên đặt những hoạt động này cùng nhau như thế nào để phát triển phần mềm**? Để trả lời được câu hỏi này, hãy bắt đầu tìm hiểu về khái niệm mô hình quy trình phát triển phần mềm (mô hình vòng đời phần mềm). 

Mô hình quy trình phát triển phần mềm là một mô hình giả định những gì sẽ được thực hiện từ bước đầu tiên cho đến bước cuối cùng của một quy trình phát triển phần mềm. Chức năng chính của mô hình là xác định thứ tự sắp xếp của các hoạt động khác nhau để ta biết được những hành động nào nên làm trước và những hành động nên thực hiện sau đó. Một chức năng quan trọng khác chính là xác định tiêu chí chuyển tiếp giữa các hoạt động: **Khi nào chúng ta sẽ chuyển sang giai đoạn tiếp theo. 


<iframe width="560" height="315" src="https://www.youtube.com/embed/laSrDtYtkXU?si=w9MTtSGdjgGIt9AB" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## 1. Mô hình thác nước
![](../Assets/Pasted%20image%2020260611155243.png)
Trong mô hình thác nước, dự án tiến triển theo một chuối thứ tự các bước: kiến trúc hệ thống, phân tích yêu cầu, thiết kế, triển khai thực hiện, kiểm thử và bảo trì. Cuối mỗi giai đoạn, chúng ta cần xem xét xác định xem dự án đẫ sẵn sàng để tiến lên giai đoạn tiếp theo hay chưa. 

Mô hình thác nước phù hợp với việc xây dựng các sản phẩm phần mềm ổn định, các công nghệ liên quan được biết đến rộng rãi và đã được tìm hiểu rõ. Trong các bài toán như vậy, mô hình thác nước giúp chúng ta tìm ra được **các lỗi trong các giai đoạn đầu**, cũng như giúp giảm thiểu chi phí và ruiro cho phát triển phần mềm tổng thể. 

Nhước điểm của mô hình thác nước là **thiếu tính linh hoạt.** Khi làm việc với các dự án có yêu cầu thay đổi thường xuyên hay các công nghệ sử dụng được cập nhật liên tục và đang trong quá trình phát triển, mô hình thác nước không phải là sự lựa chọn lý tưởng. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/5A5XCuWMG4o?si=uFmDkSVJzZ-4Vqus" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
## 2. Mô hình xoắn ốc 
![](../Assets/Pasted%20image%2020260611155251.png)
Mô hình xoắn ốc là mô hình vòng đời định hướng rủi ro gia tăng. Mô hình xoắn ốc (tiếng Anh: spiral model) là quy trình phát tiển định hướng rủi ro cho các dự án phần mềm. Kết hợp của thế mạnh cảu các mô hình khác và giải quyết khó khăn của các mô hình trước còn tồn tại. 

Về cơ bản, những gì mô hình xoắn ốc quy định là cách thức phát triển phần mềm bằng việc đi qua các giai đoạn một cách lặp lại. Khi chúng ta ngày càng hiểu về phần mềm, chúng ta nhận biết ngày càng nhiều, và giải thích càng nhiều rủi ro, chúng ta sẽ càng tiến tới giải pháp cuối cùng, phiên bản hoàn thiện cuối cùng. 

Có 4 giai đoạn chính của mô hình xoắn ốc:
- Xác định mục tiêu, nhận dạng: Các yêu cầu sẽ được thu thập
- Giải quyết rủi ro: Các rủi ro và giải pháp thay thế sẽ được xác định. 
- Phát triển và kiểm tra: Phần mềm và kiểm thử cho phần mềm được đưa ra và thực thi. 
- Lập kế hoạch cho lần lặp tiếp theo: đầu ra của dự án được đánh giá và lần lặp tiếp theo được lên kế hoạch.

**Các ưu điểm của mô hình xoắn ốc:** 
- Phân tích rủi ro sâu rộng làm giảm thiểu khả năng thất bại của dự án
- Chức năng có thể được thêm vào ở giai đoạn sau vì tính chất lặp của quy trình. 
- Phần mềm được đưa ra sớm trong vòng đời, chúng ta không cần phải đợi cho đến giai đoạn cuối trước khi đưa ra một kết quả nào đó. 
- Có thể nhận được phản hồi sớm của khách hàng về những gì ta đã đưa ra.
**Nhược điểm:**
- Phân tích rủi ro phải có chuyên môn đặc biệt cao. 
- Thành công của mô hình phục thuộc rất nhiều vào phân tích rủi ro. Cho nên, phân tích rủi ro cần phải được thực hiện đúng. 
<iframe width="560" height="315" src="https://www.youtube.com/embed/mp22SDTnsQQ?si=9BVaU8IDDaBhd_7D" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
## 3. Mô hình tiến hóa bản mẫu
![](../Assets/Pasted%20image%2020260611160225.png)
Mô hình tiến hóa bản mẫu là một phương pháp phát triển phần mềm trong đó nhà phát triển hoặc nhóm phát triển tạo mẫu thử nghiệm đàu tiên. Sau khi nhận được phản hồi ban đầu từ khách hàng, các nguyên mẫu tiếp theo được sản xuất, mỗi nguyên mẫu có thêm chức năng hoặc cải tiến, cho đến khi sản phẩm cuối cùng xuất hiện. 

Có 4 giai đoạn chính trong mô hình tiến hóa bản mẫu:
- Bắt đầu từ một khái niểm khởi đầu
- Thiết kế và thực hiện một bản mẫu dựa trên khái niệm ban đầu này
- Tinh chỉnh bản mẫu cho đến khi nó được chấp nhận
- Hoàn chỉnh và phát hành bản mẫu
Khi phát triển một hệ thống sử dụng mô hình tiến hóa bản mẫu, hệ thống liên tục được cải tiến và xây dựng lại. Đây là một quy trình lý tưởng khi mà không phải tất cả các yêu cầu đều được hiểu rõ và đây là tình huống rất phổ biến trong thực tế. 

**Ưu điểm: Phản hồi ngay lập tức** - các nhà phát triển nhận được phản hồi ngay lập tức ngay khi họ đưa ra một bản mẫu và họ đưa nó cho khách hàng. Do đó, rủi ro của việc thực hiện sẽ được giảm thiểu một cách tối đa. 

**Nhược điểm: Khó lập kế hoạch** - khi sử dụng mô hình tiến hóa bản mẫu, sẽ khó để lập kế hoạch trước cho khoảng thời gian mà việc phát triển sẽ chiếm, bời vì chúng ta không biết sẽ cần bao nhiêu lần lặp. Ngoài ra, quy trình tiến hóa dễ dàng trở thành cái cớ để làm những việc như là cắt bớt và sửa chữa phần mềm. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/bAEnaGG8Otc?si=FzY5H-ya1RT3jxnK" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## 4. Mô hình thống nhất
![](../Assets/Pasted%20image%2020260612204533.png)
Mô hình thống nhất (RUP hoặc IUP) là mô hình dựa theo UML, làm việc theo cách lặp lại, có nghĩa là nó thể hiện các lần lặp khác nhau. 

Mô hình RUP được phát triển bởi hãng IBM. Tiến trình này yêu cầu việc phát triển ứng dụng một cách chặt chẽ và nghiêm ngặt với việc đầu ra các mẫu được thực hiện nhanh chóng qua các cuộc làm việc với khách hàng và nhóm dự án, việc lập kế hoạch và đưa ra các chức năng hệ thống một cách tích cực. Kết quả sẽ đưa ra một ứng dụng đáp ứng các yêu cầu của người sử dụng và giúp cho quá trình lên kế hoạch và thực thi nhanh chóng. 

RUP dựa trên 4 giai đoạn
- **Giai đoạn khởi đầu (inception):** Tìm ra phạm vi của công việc, đâu là phạm vi của dự án, domain (miền) là gì.
- **Giai đoạn vận hành (elaboration):** Tập trung vào phân tích domain và xác định kiến trúc cơ bản của hệ thống. 
- **Giai đoạn xây dựng (construction):** Phần lớn các công việc phát triển phần mềm diễn ra ở giai đoạn này. 
- **Giai đoạn chuyển tiếp (transition):** Hệ thống đi từ bước phát triển sang sản xuất, đưa đến tay người sử dụng. 
<iframe width="560" height="315" src="https://www.youtube.com/embed/YgkhFH8g0J4?si=ffQ2s-JFiTgbwVeC" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
## 5. Mô hình Agile
![](../Assets/Pasted%20image%2020260612205531.png)
Agile là một nhóm các phương pháp chú trọng đến phát triển lặp và tăng trưởng. Agile là phương pháp phát triển phần mềm linh hoạt để làm sao ddauw sản phẩm đến tay khách hàng nhanh nhất. Scrum là một dạng của mô hình Agile và là Framework phổ biến nhất trong họ Agile. 

Phát triển hướng kiểm thử TDD (Test-Driven Development) là một phuognw pháp tiếp cận cải tiến để phát triển phần mềm trong đó kết hợp phương pháp Phát triển kiểm thử trước (Test First Development) và phương pháp Điều chỉnh lại mã nguồn (Refactoring). Mục tiêu quan trọng nhất của TDD là hãy nghĩ về thiết kế của bạn trước khi viết mã nguồn cho chức năng. 

<iframe width="560" height="315" src="https://www.youtube.com/embed/Pw8I0GSXjKg?si=y5ZsGggMeLT7QYaI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## 6. Lựa chọn quy trình
Việc chọn mô hình quy trình phù hợp có thể quyết định sự thành công hay thất bại của dự án. Làm thế nào để chúng ta có thể chọn một mô hình quy trình phù hợp cho 1 dự án phần mềm? 
- Liệu chúng ta có hiểu rõ yêu cầu của dự án?
- Cần hoàn thành dự án trong bao lâu?
- Mức độ rủi ro liên quan là gì?
- Chúng ta có hiểu rõ về domain của dự án không?
- Mức độ tương tác với khách hàng có đủ không?
- Chúng ta có một đội ngũ có trình độ chuyên môn cao và nắm bắt được các công nghệ đáng tin cậy?

<iframe width="560" height="315" src="https://www.youtube.com/embed/F5fuUs7oJu0?si=c46pm8rsVyv0MMLe" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
## 7. Các tài liệu theo vòng đời dự án
Khi thực hiện các công việc trong quá trình phát triển, thông thuognwf chúng ta cần viết ra tài liệu là sản phẩm kết quả. Các tài liệu này có vai trò làm các bê