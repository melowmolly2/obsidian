Chương 1 **"Các chiến lược tìm kiếm mù"** trong tài liệu bao gồm 4 nội dung lý thuyết trọng tâm sau đây:

### 1. Biểu diễn vấn đề trong không gian trạng thái

Để giải quyết một bài toán bằng phương pháp tìm kiếm, trước tiên cần biểu diễn vấn đề đó trong không gian trạng thái $U$. Một mô hình biểu diễn bài toán bao gồm 3 yếu tố cơ bản:

- **Trạng thái ban đầu ($u_0 \in U$)**: Cảnh huống khởi đầu của bài toán.
- **Tập hợp các toán tử ($R: U \rightarrow U$)**: Các phép biến đổi hoặc hành động dẫn từ một trạng thái tới trạng thái khác.
- **Tập hợp trạng thái kết thúc ($T \subseteq U$)**: Tập các trạng thái thỏa mãn mục tiêu của bài toán (trạng thái đích).

Không gian trạng thái thường được mô hình hóa dưới dạng một **đồ thị định hướng**, trong đó các đỉnh biểu diễn trạng thái và các cung thể hiện toán tử biến đổi.

- **Ví dụ điển hình**: Bài toán 8 số, bài toán Triệu phú và kẻ cướp, bài toán du khách tìm đường đi giữa các thành phố.

---

### 2. Phát triển trạng thái và Cây tìm kiếm

- **Phát triển trạng thái (State Expansion)**: Là việc áp dụng các toán tử lên trạng thái $u$ hiện tại để sinh ra các trạng thái kề $v$.
- **Cây tìm kiếm (Search Tree)**: Là cấu trúc cây trong đó gốc tương ứng với trạng thái ban đầu $u_0$, và các đỉnh con tương ứng với các trạng thái kề. Chiến lược tìm kiếm chính là phương pháp xây dựng cây tìm kiếm từng bước cho đến khi gặp trạng thái đích.

---

### 3. Các chiến lược tìm kiếm mù (Blind Search Strategies)

Chiến lược tìm kiếm mù không sử dụng thêm bất kỳ tri thức bổ sung nào về bài toán mà chỉ xét các trạng thái theo một thứ tự hệ thống:

1. **Tìm kiếm theo bề rộng (Breadth-First Search - BFS)**:
    
    - **Cơ chế**: Trạng thái nào được sinh ra trước sẽ được phát triển trước; danh sách trạng thái chờ phát triển $L$ được quản lý dưới dạng **hàng đợi (FIFO)**.
    - **Đặc điểm**: Luôn tìm ra nghiệm nếu bài toán có nghiệm và tìm được đường đi ngắn nhất (ít bước nhất).
    - **Độ phức tạp**: Thời gian là $O(b^d)$ và không gian bộ nhớ là $O(b^d)$ (với $b$ là nhân tố nhánh, $d$ là độ sâu của nghiệm).
2. **Tìm kiếm theo độ sâu (Depth-First Search - DFS)**:
    
    - **Cơ chế**: Trạng thái sinh ra sau cùng sẽ được phát triển trước; danh sách $L$ được quản lý dưới dạng **ngăn xếp (LIFO)**.
    - **Đặc điểm**: Tiết kiệm bộ nhớ đáng kể so với BFS; tuy nhiên nếu cây tìm kiếm chứa nhánh vô hạn hoặc chu trình, thuật toán có thể bị kẹt và không bao giờ dừng.
    - **Độ phức tạp**: Thời gian trong trường hợp xấu nhất là $O(b^d)$, không gian bộ nhớ chỉ là $O(d \cdot b)$.
3. **Xử lý trạng thái lặp (Repeated States)**:
    
    - Nhằm tránh lãng phí thời gian phát triển lại các trạng thái đã gặp thông qua các kỹ thuật: không sinh đỉnh trùng cha, không sinh đỉnh nằm trên đường đi hiện tại, hoặc lưu các trạng thái đã phát triển vào tập $Q$ (cài đặt bằng bảng băm).
4. **Tìm kiếm sâu lặp (Iterative Deepening Search - IDS)**:
    
    - **Cơ chế**: Lặp lại quá trình tìm kiếm sâu hạn chế (Depth-Limited Search) với độ sâu giới hạn tăng dần $d = 0, 1, 2, \dots, MAX$.
    - **Ưu điểm**: Kết hợp hoàn hảo tính đầy đủ và tối ưu đường đi của BFS với mức tiêu tốn bộ nhớ nhỏ như DFS ($O(d \cdot b)$). Độ phức tạp thời gian vẫn là $O(b^d)$.

---

### 4. Quy vấn đề về các vấn đề con và Tìm kiếm trên đồ thị Và/Hoặc

- **Rút gọn vấn đề (Problem Reduction)**: Là phương pháp chia bài toán lớn thành các bài toán con đơn giản hơn cho tới khi dẫn tới các bài toán sơ cấp đã biết cách giải.
- **Đồ thị và Cây Và/Hoặc (AND/OR Graph/Tree)**:
    - **Đỉnh VÀ (AND node)**: Biểu diễn tập các bài toán con mà phải giải quyết **tất cả** các bài toán con đó.
    - **Đỉnh HOẶC (OR node)**: Biểu diễn các lựa chọn mà chỉ cần giải quyết **một trong các** tập bài toán con.
    - **Cây nghiệm (Solution Tree)**: Cây có gốc là bài toán ban đầu và tất cả các lá đều là các bài toán sơ cấp.
- **Thủ tục tìm kiếm đệ quy**: Sử dụng thuật toán đệ quy `Solvable(u)` theo chiều sâu để xác định và đánh dấu các đỉnh là _giải được_ (Solvable) hay _không giải được_ (Unsolvable).

💡 Bạn có muốn đi sâu phân tích chi tiết thuật toán nào (như **BFS**, **DFS**, **Tìm kiếm sâu lặp** hoặc **Đồ thị AND/OR**) kèm ví dụ các bước thực hiện không?