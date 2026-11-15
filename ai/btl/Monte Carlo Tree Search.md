# Monte Carlo Tree Search (MCTS) + UCT

## 1. Ý tưởng chính

MCTS là thuật toán tìm kiếm dùng cho các bài toán ra quyết định tuần tự (cờ vây, cờ vua, game AI, lập kế hoạch...). Thay vì duyệt toàn bộ cây trạng thái (quá lớn), MCTS:

- Dần dần xây dựng một cây tìm kiếm không đối xứng, tập trung vào những nhánh có triển vọng.
- Ước lượng giá trị của một trạng thái bằng các lần mô phỏng ngẫu nhiên (rollout/playout) đến khi game kết thúc.

Nó không cần hàm đánh giá heuristic, chỉ cần biết luật chơi (hàm sinh nước đi hợp lệ và kết quả cuối game).

## 2. Bốn pha của một vòng lặp

Mỗi node $v$ lưu hai số: $N(v)$ là số lần node được thăm và $W(v)$ là tổng phần thưởng tích lũy. Lặp lại 4 bước cho đến khi hết thời gian hoặc hết số lần lặp:

1. **Selection (Chọn)**: từ gốc, đi xuống cây theo một chính sách chọn con (ở đây là UCT) cho đến khi gặp node chưa được mở rộng hết.
2. **Expansion (Mở rộng)**: thêm một (hoặc vài) node con mới ứng với nước đi chưa thử.
3. **Simulation (Mô phỏng)**: từ node mới, chơi ngẫu nhiên (hoặc theo chính sách nhẹ) đến trạng thái kết thúc, nhận kết quả $z$ (ví dụ thắng $=1$, hòa $=0.5$, thua $=0$).
4. **Backpropagation (Lan truyền ngược)**: đi ngược từ node mới lên gốc, cập nhật

$$N(v) \leftarrow N(v)+1, \qquad W(v) \leftarrow W(v)+z$$

Với game hai người, cần đổi góc nhìn ($z \to 1-z$) ở mỗi tầng, vì nước đi tốt cho người này là xấu cho người kia.

Sau cùng, nước đi được chọn thường là con của gốc có $N$ lớn nhất (robust child), vì ổn định hơn chọn theo tỉ lệ thắng cao nhất.

## 3. Vấn đề cốt lõi: exploration vs. exploitation

Ở pha Selection, ta cần cân bằng:

- **Exploitation**: chọn nhánh hiện có tỉ lệ thắng cao.
- **Exploration**: thử nhánh ít được thăm, vì ước lượng của chúng còn nhiễu và có thể thực ra tốt hơn.

Đây chính là bài toán **multi-armed bandit**.

## 4. UCB1 và UCT

**UCB1** (Upper Confidence Bound) cho bandit: chọn cần gạt $i$ maximize

$$\text{UCB1}_i = \bar{X}_i + c\sqrt{\frac{\ln n}{n_i}}$$

với $\bar{X}_i$ là phần thưởng trung bình của cần $i$, $n_i$ là số lần kéo cần $i$, $n$ là tổng số lần kéo.

**UCT** (Upper Confidence bounds applied to Trees, Kocsis & Szepesvári, 2006) áp dụng UCB1 tại _mỗi node_ của cây. Tại node cha $v$, chọn con $v_i$ maximize

$$\text{UCT}(v_i) = \underbrace{\frac{W(v_i)}{N(v_i)}}_{\text{exploitation}} + c,\underbrace{\sqrt{\frac{\ln N(v)}{N(v_i)}}}_{\text{exploration}}$$

- Hạng tử đầu là tỉ lệ thắng trung bình của con $v_i$.
- Hạng tử sau lớn khi $N(v_i)$ nhỏ (con ít được thăm) và tăng chậm theo $\ln N(v)$, nên mọi nhánh đều sẽ được thử lại theo thời gian.
- Hằng số $c$ điều chỉnh mức khám phá. Về lý thuyết $c=\sqrt{2}$ khi phần thưởng nằm trong $[0,1]$. Trong thực tế thường tinh chỉnh bằng thực nghiệm.
- Con chưa được thăm ($N(v_i)=0$) coi như $\text{UCT}=+\infty$, nên luôn được thử trước.

**Tính chất lý thuyết**: UCT hội tụ về nước đi tối ưu (minimax) khi số lần mô phỏng $\to\infty$.

## 5. Giả mã

```python
def mcts(root_state, iterations, c=1.41):
    root = Node(root_state)
    for _ in range(iterations):
        node = root
        # 1. Selection
        while node.is_fully_expanded() and not node.is_terminal():
            node = max(node.children, key=lambda ch:
                ch.W / ch.N + c * math.sqrt(math.log(node.N) / ch.N))
        # 2. Expansion
        if not node.is_terminal():
            node = node.expand()          # thêm 1 con mới
        # 3. Simulation
        z = node.rollout()                # chơi ngẫu nhiên đến cuối
        # 4. Backpropagation
        while node is not None:
            node.N += 1
            node.W += z                   # đổi góc nhìn nếu game 2 người
            node = node.parent
    return max(root.children, key=lambda ch: ch.N).move
```

## 6. Ưu và nhược điểm

**Ưu điểm**

- Không cần hàm heuristic đặc thù cho bài toán.
- Là thuật toán _anytime_: dừng lúc nào cũng có đáp án tốt nhất hiện tại.
- Xử lý tốt hệ số nhánh lớn (như cờ vây).
- Tự tập trung vào phần cây đáng quan tâm.

**Nhược điểm**

- Rollout ngẫu nhiên có thể bỏ sót các "bẫy" chiến thuật (nước đi duy nhất thắng).
- Cần nhiều mô phỏng để ước lượng ổn định.
- Tốn bộ nhớ vì lưu cây.

## 7. Mở rộng

- **AlphaGo / AlphaZero**: thay UCT bằng **PUCT**, kết hợp prior $P(s,a)$ từ mạng nơ-ron:

$$a^* = \arg\max_a \left( Q(s,a) + c_{\text{puct}}, P(s,a),\frac{\sqrt{N(s)}}{1+N(s,a)} \right)$$

Rollout ngẫu nhiên cũng được thay bằng giá trị $V(s)$ do mạng dự đoán.

- **RAVE / AMAF**, **progressive widening** (cho không gian hành động liên tục), **heavy playouts**...

