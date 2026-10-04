## 1. Bài toán tìm kiếm

Một bài toán tìm kiếm gồm 5 thành phần:

- **Trạng thái đầu** (start state).
- **Hành động** (actions) khả dụng ở mỗi trạng thái.
- **Mô hình chuyển trạng thái** (transition model): làm hành động $a$ ở trạng thái $s$ thì sang trạng thái nào.
- **Kiểm tra đích** (goal test).
- **Chi phí đường đi** (path cost): tổng các chi phí bước đi, với $c(s,a,s') \ge 0$.

**Nghiệm** là một dãy hành động đưa trạng thái đầu tới trạng thái đích. **Nghiệm tối ưu** là nghiệm có chi phí đường đi nhỏ nhất.

**Tác tử hợp lý (rational agent)** chọn hành động để cực đại hóa độ thỏa dụng kỳ vọng (expected utility). **PEAS** mô tả môi trường tác vụ: Performance measure, Environment, Actuators, Sensors.

Môi trường được phân loại theo 5 tiêu chí:

- quan sát đầy đủ hay một phần;
- đơn tác tử hay đa tác tử;
- xác định hay ngẫu nhiên;
- tĩnh hay động;
- rời rạc hay liên tục.

**Ví dụ 8-puzzle:**

- Trạng thái: vị trí các ô số.
- Hành động: dịch ô trống trái, phải, lên, xuống.
- Kiểm tra đích: trạng thái có khớp trạng thái đích không.
- Chi phí: 1 cho mỗi bước đi.

Slide ghi 8-puzzle có "362,800 trạng thái". Con số đúng là $9! = 362,880$, trong đó chỉ một nửa, tức $9!/2 = 181,440$, là đạt tới được. Với 15-puzzle là khoảng $10^{12}$ và 24-puzzle là khoảng $10^{25}$.

## 2. Không gian trạng thái và cây tìm kiếm

- **Đồ thị không gian trạng thái**: nút là trạng thái, cung là hành động. Mỗi trạng thái xuất hiện **một lần**. Đồ thị này thường quá lớn nên không dựng ra đầy đủ.
- **Cây tìm kiếm**: gốc là trạng thái đầu, con của một nút là các trạng thái kế tiếp. Cây có nhiều cấu trúc lặp, thậm chí có thể vô hạn dù đồ thị rất nhỏ.
- **Nút khác trạng thái**: nút là cấu trúc dữ liệu lưu thêm con trỏ cha, chi phí đường đi, v.v.
- **Frontier** (biên) là danh sách các nút đã sinh ra nhưng chưa mở rộng.
- **Chiến lược tìm kiếm** chính là thứ tự mở rộng nút, tức cách chọn nút lấy ra khỏi frontier. Kiểu cấu trúc dữ liệu của frontier quyết định thuật toán:
    - hàng đợi FIFO cho BFS;
    - ngăn xếp LIFO cho DFS;
    - hàng đợi ưu tiên cho UCS.

**TREE_SEARCH và GRAPH_SEARCH:**

- GRAPH_SEARCH có thêm tập **explored** (đã mở rộng). Chỉ thêm con vào frontier nếu trạng thái đó chưa nằm trong frontier hoặc explored.
- Nhờ vậy tránh được **trạng thái lặp** (repeated states).

## 3. Bốn tiêu chí đánh giá và các tham số

Bốn tiêu chí:

- **Completeness** (đầy đủ): có luôn tìm ra nghiệm nếu nghiệm tồn tại không.
- **Time complexity** (độ phức tạp thời gian).
- **Space complexity** (độ phức tạp không gian).
- **Optimality** (tối ưu): có đảm bảo nghiệm chi phí nhỏ nhất không.

Ba tham số:

- $b$: hệ số nhánh tối đa.
- $d$: độ sâu của nghiệm chi phí nhỏ nhất.
- $m$: độ sâu tối đa của không gian trạng thái, có thể là $\infty$.

## 4. Các thuật toán

**BFS (tìm kiếm theo chiều rộng)**

- Mở rộng nút nông nhất trước, duyệt theo từng tầng, dùng hàng đợi FIFO.
- Thời gian: $1 + b + b^2 + \dots + b^d = O(b^d)$.
- Không gian: $O(b^d)$. Đây là điểm yếu chính của BFS, vì bộ nhớ cạn trước thời gian.
- Đầy đủ nếu $b$ hữu hạn. Tối ưu nếu chi phí mỗi bước bằng nhau.
- Ví dụ trong slide: với $b = 10$, độ sâu $d = 8$ cần 31 giờ và 11 GB; độ sâu $d = 12$ cần 35 năm và 111 TB.

**DFS (tìm kiếm theo chiều sâu)**

- Mở rộng nút sâu nhất trước, dùng ngăn xếp LIFO.
- Thời gian trường hợp xấu nhất: $b^m + b^{m-1} + \dots + 1 = \dfrac{b^{m+1}-1}{b-1} = O(b^m)$.
- Không gian: $(b-1),m + 1 = O(bm)$, rất nhỏ so với BFS.
- **Không đầy đủ** nếu không gian vô hạn (đầy đủ nếu hữu hạn). **Không tối ưu**.

**Depth-limited search (DLS)**

- Là DFS có giới hạn độ sâu $l$. DFS là trường hợp đặc biệt của DLS.
- Đầy đủ nếu $l \ge d$. Không tối ưu.
- Thời gian $O(b^l)$, không gian $O(bl)$.

**Iterative deepening search (IDS)**

- Chạy DLS với $l = 0, 1, 2, \dots$ cho tới khi tìm thấy nghiệm.
- Kết hợp ưu điểm không gian của DFS với ưu điểm thời gian và nghiệm nông của BFS.
- Số lần mở rộng: $(d+1)\cdot 1 + d\cdot b + (d-1) b^2 + \dots + 1\cdot b^d = O(b^d)$.
- Không gian $O(bd)$. Đầy đủ. Tối ưu nếu chi phí mỗi bước bằng 1.
- Lặp lại công việc nhưng không đáng kể, vì phần lớn công việc nằm ở tầng sâu nhất.
- Nên dùng khi không gian lớn và chưa biết độ sâu nghiệm.

**Uniform-cost search (UCS)**

- Mở rộng nút có chi phí đường đi $g(n)$ nhỏ nhất, dùng hàng đợi ưu tiên theo $g(n)$.
- Tương đương BFS nếu mọi bước có chi phí bằng nhau, và tương đương thuật toán Dijkstra nói chung.
- Gọi $C^*$ là chi phí nghiệm tối ưu và $\varepsilon$ là chi phí cung nhỏ nhất. Độ sâu hiệu dụng khoảng $C^*/\varepsilon$, nên thời gian và không gian đều là $O!\left(b^{C^*/\varepsilon}\right)$.
- Đầy đủ nếu $\varepsilon > 0$ và $C^*$ hữu hạn. **Tối ưu**.
- Chứng minh tối ưu (phản chứng):
    - Giả sử UCS dừng tại đích $n$ nhưng tồn tại đích $n'$ với $g(n') < g(n)$.
    - Theo tính chất tách đồ thị (graph separation), có một nút $n''$ trên frontier nằm trên đường đi tối ưu tới $n'$.
    - Khi đó $g(n'') \le g(n') < g(n)$, nên $n''$ phải được mở rộng trước. Mâu thuẫn.

## 5. Bảng so sánh (slide 125)

|Tiêu chí|BFS|UCS|DFS|DLS|IDS|
|---|---|---|---|---|---|
|Thời gian|$b^d$|$b^{C^*/\varepsilon}$|$b^m$|$b^l$|$b^d$|
|Không gian|$b^d$|$b^{C^*/\varepsilon}$|$bm$|$bl$|$bd$|
|Tối ưu?|Có*|Có|Không|Không|Có*|
|Đầy đủ?|Có|Có|Không|Có nếu $l \ge d$|Có|

* Với điều kiện chi phí mỗi bước bằng nhau. Slide ghi cột UCS là $b^d$ cho gọn, còn chính xác theo phần UCS là $b^{C^*/\varepsilon}$.

## 6. Độ phức tạp thuật toán

- $T(n) = O(f(n))$ nghĩa là tồn tại $n_0, k$ sao cho với mọi $n > n_0$ thì $T(n) \le k,f(n)$.
- Ví dụ trong slide: $100n + 1000$ chỉ tốt hơn $n^2 + 1$ khi $n > 110$.
- **Tháp Hà Nội** là ví dụ về bùng nổ hàm mũ: $n$ đĩa cần $2^n - 1$ bước.
    - 3 đĩa cần $2^3 - 1 = 7$ bước.
    - 64 đĩa cần $2^{64} - 1 \approx 1.6 \times 10^{19}$ bước.
    - Với tốc độ 1 đĩa/giây thì mất khoảng $5 \times 10^{11}$ năm, gấp khoảng 33 lần tuổi vũ trụ ($1.5 \times 10^{10}$ năm).
    - Với máy tính $10^9$ bước/giây thì vẫn mất khoảng 500 năm.

## 7. Mẹo ôn thi

- **BFS và UCS** tối ưu nhưng tốn bộ nhớ.
- **DFS** tiết kiệm bộ nhớ nhưng không đầy đủ và không tối ưu.
- **IDS** thường là lựa chọn tốt khi không gian lớn và chưa biết độ sâu nghiệm.
- Slide có bài tập "Find path from A to K" (BFS và DFS) và câu hỏi "When will BFS outperform DFS?". Nên tự làm hai bài này.
- Ví dụ UCS trong slide: thứ tự mở rộng là $(S, p, d, b, e, a, r, f, e, G)$.

Nếu muốn, mình có thể làm thêm bộ câu hỏi trắc nghiệm hoặc flashcard để ôn phần này. 