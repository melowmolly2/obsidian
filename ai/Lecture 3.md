## 1. Heuristic và hàm đánh giá

- **Heuristic** (kinh nghiệm) là hàm $h(n)$ ước lượng khoảng cách từ trạng thái $n$ tới đích.
- Quy ước: $h(n) = 0$ nếu $n$ là đích.
- Hàm này phụ thuộc từng bài toán cụ thể. Nó giúp hướng tìm kiếm về phía đích thay vì lan ra khắp nơi như tìm kiếm mù.
- Một heuristic **hữu ích** khi thỏa hai điều kiện:
    - **Chính xác**: $h(n) \approx d(n)$, với $d(n)$ là khoảng cách thật tới đích.
    - **Rẻ**: tính được trong thời gian ít hơn $O(b^d)$.
- Ví dụ: khoảng cách Manhattan và khoảng cách Euclid cho bài toán tìm đường. Với bản đồ Romania, slide dùng khoảng cách đường chim bay tới Bucharest.
- **Heuristic cho 8-puzzle:**
    - $h_1(n)$ = số ô sai vị trí.
    - $h_2(n)$ = tổng khoảng cách Manhattan của các ô tới vị trí đúng.
    - Ví dụ slide 10: $h_1 = 8$, $h_2 = 3+1+2+1+1+1+1+2+2 = 14$.
    - Ví dụ slide 54: $h_1(S) = 8$, $h_2(S) = 3+1+2+2+2+3+3+2 = 18$.
- **Ba pha của heuristic search:**
    1. Tìm cách biểu diễn trạng thái.
    2. Xây dựng hàm đánh giá.
    3. Thiết kế chiến lược chọn trạng thái để mở rộng.

## 2. Greedy Best-first Search

- **Greedy = BFS + heuristic.** Luôn mở rộng nút có $h$ nhỏ nhất, kể cả ở tầng trên.
- Thuật toán: danh sách $L$ luôn được sắp xếp từ tốt đến xấu theo hàm đánh giá. Lấy phần tử đầu ra mở rộng, rồi chèn các con vào $L$ đúng thứ tự.
- Tính chất:
    - **Không đầy đủ**: có thể lặp vô hạn, ví dụ Iasi → Neamt → Iasi → …. Đầy đủ nếu không gian hữu hạn và có kiểm tra trạng thái lặp.
    - Thời gian $O(b^m)$, không gian $O(b^m)$ vì giữ mọi nút trong bộ nhớ.
    - **Không tối ưu.**
    - Heuristic tốt có thể giảm mạnh thời gian và bộ nhớ. Theo slide, trường hợp tốt nhất là $O(bd)$.
- **Ví dụ Romania:**
    - Greedy đi Arad → Sibiu → Fagaras → Bucharest với chi phí $140 + 99 + 211 = 450$.
    - Đường tối ưu là Arad → Sibiu → Rimnicu Vilcea → Pitesti → Bucharest với chi phí $140 + 80 + 97 + 101 = 418$.
- **Bài tập Ex 2 (S → t):** theo hình, greedy đi $S \to a \to e \to d \to t$ với chi phí $1+5+1+2 = 9$, trong khi $S \to a \to d \to t$ chỉ tốn $1+3+2 = 6$.

## 3. Beam Search

- Giống best-first nhưng chỉ giữ lại **$k$ nút tốt nhất** (độ rộng WIDTH = $k$) ở mỗi tầng, các nút còn lại bị bỏ.
- Ưu điểm: bộ nhớ không đổi, bằng WIDTH.
- Thời gian: cỡ $\text{WIDTH} \cdot m \cdot b$, hoặc $\text{WIDTH} \cdot d \cdot b$ nếu không tìm thấy nghiệm.
- Nhược điểm: **không đầy đủ**, vì có thể bỏ mất nút dẫn tới đích.
- Tối ưu hóa trong slide: bỏ các lá không phải đích.

## 4. Hill-climbing Search

- **Hill-climbing = DFS + heuristic.** Trong các con của $u$, chọn con có $h$ nhỏ nhất để đi tiếp trước.
- Thuật toán:
    - Đưa các con của $u$ vào danh sách $L_1$.
    - Sắp xếp $L_1$ tăng dần theo hàm đánh giá.
    - Chèn $L_1$ vào **đầu** $L$.
- Tính chất:
    - **Đầy đủ** (nhờ quay lui), theo slide.
    - Thời gian và bộ nhớ như DFS trong trường hợp xấu nhất.
    - **Không tối ưu.**

## 5. A* Search

- Hàm đánh giá:  
    $$f(n) = g(n) + h(n)$$
    - $g(n)$: chi phí thực từ nút gốc tới $n$.
    - $h(n)$: chi phí ước lượng của đường rẻ nhất từ $n$ tới đích.
    - $f(n)$: tổng chi phí ước lượng của nghiệm rẻ nhất đi qua $n$.
- So sánh ba thuật toán:
    - Greedy chỉ tối thiểu hóa $h(n)$: nhanh nhưng không tối ưu.
    - UCS chỉ tối thiểu hóa $g(n)$: tối ưu nhưng chậm.
    - A* kết hợp cả hai: giữ hiệu quả của greedy nhưng tránh mở rộng những đường đã quá đắt.
- Thuật toán: với mỗi con $v$ của $u$, tính $g(v) = g(u) + k(u,v)$ và $f(v) = g(v) + h(v)$, rồi chèn vào $L$ sắp theo $f$.
- **Kiểm tra đích khi lấy nút ra khỏi hàng đợi để mở rộng**, không phải khi sinh ra nút. Nhờ vậy nút đích dưới tối ưu có thể được sinh ra nhưng không bao giờ được mở rộng.

### Heuristic chấp nhận được (admissible)

$$0 \le h(n) \le h^*(n)$$

với $h^*(n)$ là chi phí thật tới đích gần nhất. Nói cách khác, $h$ phải **lạc quan** và không được đánh giá quá cao.

**Ví dụ phản chứng (slide 46):**

- Có $h(a) = 6$ nhưng chi phí thật từ $a$ tới $t$ chỉ là 3, nên $h$ không admissible.
- Khi đó $f(a) = 1 + 6 = 7$ và $f(t) = 5 + 0 = 5$.
- A* mở rộng $t$ trước và dừng với chi phí 5, trong khi đường tối ưu $s \to a \to t$ chỉ tốn $1 + 3 = 4$.

### Chứng minh A* tối ưu

Giả sử $G_2$ là đích dưới tối ưu đang nằm trong frontier. Gọi $n$ là nút chưa mở rộng nằm trên đường ngắn nhất tới đích tối ưu $G$. Khi đó:

$$f(G_2) > f(G)$$  
$$h(n) \le h^*(n) \Rightarrow g(n) + h(n) \le g(n) + h^*(n)$$  
$$\Rightarrow f(n) \le f(G) < f(G_2)$$

Vì $f(n) < f(G_2)$ nên A* không bao giờ chọn $G_2$ để mở rộng.

### Tính nhất quán (consistency)

$$h(A) - h(C) \le \text{cost}(A \to C) \quad\Longleftrightarrow\quad h(A) \le \text{cost}(A \to C) + h(C)$$

Đây là bất đẳng thức tam giác. Admissibility so sánh $h$ với chi phí thật tới đích, còn consistency so sánh $h$ với chi phí thật của **từng bước**.

### Tính chất của A*

|Tiêu chí|Kết quả|
|---|---|
|Đầy đủ|Có (trừ khi có vô hạn nút với $f \le f(G)$)|
|Tối ưu|Có, nếu $h$ admissible|
|Thời gian|Hàm mũ|
|Không gian|Giữ mọi nút trong bộ nhớ|

## 6. Thiết kế heuristic

- **Dominance (áp đảo):** nếu $h_2(n) \ge h_1(n)$ với mọi $n$ và cả hai đều admissible thì $h_2$ **áp đảo** $h_1$, và $h_2$ tốt hơn cho tìm kiếm.
- Số nút trung bình phải mở rộng với 8-puzzle:

|Độ sâu|IDS|A*($h_1$)|A*($h_2$)|
|---|---|---|---|
|$d = 12$|3,644,035|227|73|
|$d = 24$|$\sim 54 \times 10^9$|39,135|1,641|

- **Bài toán nới lỏng (relaxed problem):**
    - Bỏ bớt ràng buộc của hành động.
    - Chi phí nghiệm tối ưu của bài toán nới lỏng là một heuristic admissible cho bài toán gốc.
    - Nếu ô được chuyển tới **bất kỳ đâu** thì ta được $h_1$.
    - Nếu ô được chuyển sang **ô kề** (bỏ qua các ô khác) thì ta được $h_2$.
- **Heuristic hợp thành:**  
    $$h(n) = \max\big(h_1(n), h_2(n), \dots, h_m(n)\big)$$
    - Nếu mọi $h_i$ đều admissible thì $h$ cũng admissible.
    - $h$ áp đảo tất cả các $h_i$.

## 7. Các biến thể của A*

- **Weighted A*:**
    - Lấy heuristic admissible rồi nhân với $\alpha > 1$, tức $f(n) = g(n) + \alpha, h(n)$.
    - Mở rộng ít nút hơn nhưng có thể không tối ưu. Chi phí nghiệm tìm được tối đa $\alpha$ lần chi phí tối ưu.
- **Branch and bound:**
    - Nếu trong $L$ có hai đường $P$ và $Q$ cùng kết thúc tại trạng thái $X$ với $\text{cost}_P \ge \text{cost}_Q$ thì loại $P$ khỏi $L$.
- **Ứng dụng của A*:**
    - tìm đường, lập kế hoạch tài nguyên, lập kế hoạch chuyển động cho robot;
    - phân tích ngôn ngữ, dịch máy, nhận dạng giọng nói, trò chơi điện tử.

## 8. Bảng tổng hợp các thuật toán tìm kiếm

| Thuật toán | Đầy đủ? | Tối ưu?                    | Thời gian                           | Không gian                          | Frontier                        |
| ---------- | ------- | -------------------------- | ----------------------------------- | ----------------------------------- | ------------------------------- |
| BFS        | Có      | Nếu chi phí bước bằng nhau | $O(b^d)$                            | $O(b^d)$                            | Queue                           |
| DFS        | Không   | Không                      | $O(b^m)$                            | $O(bm)$                             | Stack                           |
| IDS        | Có      | Nếu chi phí bước bằng nhau | $O(b^d)$                            | $O(bd)$                             | Stack                           |
| UCS        | Có      | Có                         | số nút có $g(n) \le C^*$            | số nút có $g(n) \le C^*$            | Priority queue theo $g(n)$      |
| Greedy     | Không   | Không                      | Xấu nhất $O(b^m)$, tốt nhất $O(bd)$ | Xấu nhất $O(b^m)$, tốt nhất $O(bd)$ | Priority queue theo $h(n)$      |
| A*         | Có      | Có                         | số nút có $g(n)+h(n) \le C^*$       | số nút có $g(n)+h(n) \le C^*$       | Priority queue theo $g(n)+h(n)$ |

## 9. Bài tập cuối slide (67): tìm đường ngắn nhất từ S tới G bằng A*

Dữ liệu: $h(S)=7$, $h(A)=10$, $h(B)=9$, $h(C)=5$, $h(G)=0$. Các cạnh: $S\text{-}A=1$, $S\text{-}B=1$, $A\text{-}B=9$, $B\text{-}C=6$, $B\text{-}G=12$, $C\text{-}G=5$.

Mình tự giải, bạn nên đối chiếu lại với đáp án của thầy:

1. Mở rộng $S$: $f(A) = 1+10 = 11$, $f(B) = 1+9 = 10$.
2. Mở rộng $B$ (nhỏ nhất): $f(C) = 7+5 = 12$, $f(G) = 13+0 = 13$.
3. Mở rộng $A$ ($f = 11$): đi qua $A$ tới $B$ tốn thêm, không cải thiện được.
4. Mở rộng $C$ ($f = 12$): $g(G) = 12$ nên $f(G) = 12$, tốt hơn 13.
5. Lấy $G$ ra và dừng. Đường đi là $S \to B \to C \to G$ với chi phí $12$.

## 10. Mẹo ôn thi

- Greedy chỉ nhìn $h$ nên nhanh nhưng dễ sai. UCS chỉ nhìn $g$ nên đúng nhưng chậm. A* nhìn cả $g + h$.
- A* tối ưu **khi $h$ admissible**. Nhớ ví dụ phản chứng ở slide 46.
- Hill-climbing là DFS có sắp xếp con. Beam search là BFS có cắt tỉa theo độ rộng $k$.
- Cần biết tính tay $h_1$, $h_2$ cho 8-puzzle và chạy A* trên đồ thị nhỏ như bài tập cuối.

Nếu muốn, mình có thể tạo bộ trắc nghiệm hoặc flashcard cho tuần 3.