# Thuật toán Minimax

## Ý tưởng cốt lõi

Giả sử có hai người chơi:

- **MAX**: muốn **tối đa hóa** điểm số của mình.
- **MIN**: muốn **tối thiểu hóa** điểm số của MAX (tức là đối thủ chơi tối ưu nhất).

Thuật toán giả định đối thủ luôn chơi hoàn hảo, rồi chọn nước đi cho kết quả **tệ nhất vẫn tốt nhất có thể**. Đây là lý do có tên "minimax" (minimize the maximum loss).

## Công thức

Giá trị của một trạng thái $s$:

$$
V(s) =
\begin{cases}
U(s) & \text{nếu } s \text{ là trạng thái kết thúc} \\[4pt]
\max\limits_{a \in A(s)} V\big(\text{Result}(s,a)\big) & \text{nếu đến lượt MAX} \\[4pt]
\min\limits_{a \in A(s)} V\big(\text{Result}(s,a)\big) & \text{nếu đến lượt MIN}
\end{cases}
$$

Trong đó:
- $U(s)$ là hàm hữu dụng (ví dụ $+1$ thắng, $0$ hòa, $-1$ thua),
- $A(s)$ là tập các nước đi hợp lệ tại $s$,
- $\text{Result}(s,a)$ là trạng thái sau khi đi nước $a$.

Nước đi tối ưu của MAX tại $s$ là:

$$
a^* = \arg\max_{a \in A(s)} V\big(\text{Result}(s,a)\big)
$$

## Ví dụ trên cây trò chơi

```
            MAX
          /  |  \
        MIN MIN MIN
        /\   /\   /\
       3 5  2 9  0 7
```

- Nút MIN thứ nhất: $\min(3,5)=3$
- Nút MIN thứ hai: $\min(2,9)=2$
- Nút MIN thứ ba: $\min(0,7)=0$
- Nút gốc MAX: $\max(3,2,0)=3$

MAX chọn nhánh thứ nhất, đảm bảo ít nhất được $3$ điểm dù MIN chơi tốt nhất.

## Mã giả

```python
def minimax(state, depth, is_max):
    if depth == 0 or is_terminal(state):
        return evaluate(state)
    if is_max:
        return max(minimax(child, depth - 1, False) for child in children(state))
    else:
        return min(minimax(child, depth - 1, True) for child in children(state))
```

## Độ phức tạp

Với hệ số phân nhánh $b$ và độ sâu $d$:

$$
T(n) = O(b^d), \qquad \text{bộ nhớ} = O(bd)
$$

Với cờ vua, $b \approx 35$, nên tìm kiếm đầy đủ là không khả thi. Vì vậy người ta dùng hai kỹ thuật:

1. **Giới hạn độ sâu + hàm đánh giá heuristic** $\text{eval}(s)$ để ước lượng giá trị khi chưa đến trạng thái kết thúc.
2. **Cắt tỉa Alpha-Beta** (xem bên dưới).

## Cắt tỉa Alpha-Beta

Alpha-Beta cho **cùng kết quả** với minimax nhưng bỏ qua các nhánh chắc chắn không ảnh hưởng đến quyết định:

- $\alpha$: giá trị tốt nhất mà MAX đã tìm được trên đường đi hiện tại.
- $\beta$: giá trị tốt nhất mà MIN đã tìm được trên đường đi hiện tại.
- Cắt nhánh khi $\alpha \ge \beta$.

Trong trường hợp tốt nhất (sắp xếp nước đi hợp lý), độ phức tạp giảm còn:

$$
O\!\left(b^{d/2}\right)
$$

tức là có thể tìm sâu gần gấp đôi trong cùng thời gian.

```python
def alphabeta(state, depth, alpha, beta, is_max):
    if depth == 0 or is_terminal(state):
        return evaluate(state)
    if is_max:
        value = float('-inf')
        for child in children(state):
            value = max(value, alphabeta(child, depth - 1, alpha, beta, False))
            alpha = max(alpha, value)
            if alpha >= beta:
                break
        return value
    else:
        value = float('inf')
        for child in children(state):
            value = min(value, alphabeta(child, depth - 1, alpha, beta, True))
            beta = min(beta, value)
            if alpha >= beta:
                break
        return value
```

## Lưu ý

- Chỉ áp dụng trực tiếp cho trò chơi **thông tin hoàn hảo** và **tổng bằng không**.
- Chất lượng phụ thuộc nhiều vào hàm đánh giá khi cắt ở độ sâu giới hạn.
- Biến thể: **Negamax** (viết gọn hơn nhờ $V_{\text{MIN}}(s) = -V_{\text{MAX}}(s)$), **Expectimax** (cho trò chơi có yếu tố ngẫu nhiên), **MCTS** (cho không gian tìm kiếm rất lớn như cờ vây).

Nếu bạn muốn, mình có thể viết code hoàn chỉnh cho tic-tac-toe hoặc giải thích kỹ hơn về Alpha-Beta.