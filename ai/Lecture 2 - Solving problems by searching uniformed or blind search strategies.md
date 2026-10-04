
# Bài toán tìm kiếm
Một bài toán tìm kiếm gồm 5 thành phần: 
- Trạng thái đầu (start state)
- Hành động (actions)
- Mô hình chuyển trạng thái (transition model): làm hành động $a$ ở trạng thái $s$ thì sang trạng thái nào. 
- Kiểm tra đích (goal test)
- Chi phí đường đi (path cost): tổng các chi phí bước đi, với $c(s,a,s')\ge 0$.
**Nghiệm** là một dãy hành động đưa trạng