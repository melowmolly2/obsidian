## Brute force
- Worst case: O(mn)
- Too slow!!!!!!!!!!!
![[Pasted image 20250429112605.png]]
## KMP
- Dùng thông tin từ các lần thử trước
- Tính trước cần nhảy lên bao nhiêu khi fail 
- Có thể tính trước nhảy bao nhiêu lần kể cả khi không biết T
![[Pasted image 20250429112839.png]]

## Implement
- Không bao giờ giảm `i` 
- Tính một bẳng f để nhảy 
- Làm điều này bằng cách so sánh P với chính nó ở mọi vị trí
![[Pasted image 20250429113058.png]]
![[Pasted image 20250429113105.png]]
![[Pasted image 20250429113133.png]]
![[Pasted image 20250429113152.png]]
![[Pasted image 20250429113157.png]]
![[Pasted image 20250429113215.png]]
## Performance
- Preprocess: O(m)
- 1 trong 3 trường hợp 
	- `t[i]=p[j]`: i tăng
	- `t[i]<>p[j]` và `j>0:` i-j tăng
	- `t[i]<>p[j]` và j=0: i tăng và j tăng
- Max 2N vòng
- Worst case: O(n+m)
  