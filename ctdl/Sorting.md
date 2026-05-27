# Sắp xếp chọn (selection sort)
- Duyệt mảng, tìm phần tử bé nhất 
- Đổi chỗ với phần tử đầu tiên của mảng
- Lặp lại quá trình này với phần còn lại của mảng
-![[Pasted image 20250427210918.png]]
# Sắp xếp chèn (insertion sort)
- Duyệt từ phần tử đầu tiên
- Với phần tử kế tiếp, chèn nó vào vị trí thích hợp và lùi các phần tử sau đó 1 vị trí (dùng 1 vòng lặp swap 2 phần tử liên tiếp lùi)
- Lặp lại cho đến khi kết thúc
![[Pasted image 20250427211033.png]]
# Sắp xếp nổi bọt (Bubble sort)
- Duyệt từ vị trí đầu đến cuối, so sánh 2 số cạnh nhau, nếu ngược thứ tự thì đổi chỗ
- -> Phần tử lớn nhất sẽ bị "nổi lên" vị trí cuối cùng
- Lặp lại các bước với mảng còn lại 
![[Pasted image 20250427211612.png]]
# Sắp xếp trộn (merge sort)
- Nếu mảng có nhiều hơn một phần từ thì chia đôi mảng thành hai mảng A, B
- Sắp xếp 2 mảng A,B bằng merge sort
- Trộn 2 mảng A,B đã được sắp xếp (2 con trỏ)
![[Pasted image 20250427213621.png]]
# Natural merge sort
- Cải thiện hiệu quả bằng cách tận dụng các đoạn mảng đã có thứ tự
- Chia mảng dựa trên các đoạn mảng đã có thứ tự
- Lặp lại với các mảng con
![[Pasted image 20250427214050.png]]
# Quicksort
- Thuật toán hiệu quả nhất
- Dựa trên tiếp cận chia để trị 
- Khái niệm cơ bản: 
	- Chọn một giá trị chốt p (pivot)
	- Chia mảng thành 2 mảng con, một mảng gồm các phần tử nhỏ hơn (hoặc bằng p), mảng kia lớn hơn p
	- Đặt p vào vị trí giữa 2 mảng con
	- Lặp lại thuật toán với các mảng con
![[Pasted image 20250428151918.png]]
```
quicksort(list, left, right) {  
if (left < right) {  
	partition(list, left, right, j);  
	quicksort(list, left, j-1);  
	quicksort(list, j+1, right);  
	}  
}
```
# Quicksort: phân chia
- Tiếp cận dạng nôi bọt 
	- Duyệt từ trái sang phải tìm vị trí `i` giá trị > pivot và vị trí `j` sau đó giá trị $\le$ pivot, đổi chỗ hai phần tử
	- Cho `j` chạy từ `left` đến `right-1`, nếu `list[j]<pivot` 
		1. Đổi chỗ `list[i]` $\leftrightarrow$ `list[j];
		2. `i++;`
		3. Đổi chỗ `list[i]` $\leftrightarrow$ `list[right]` 
```
int pivot=arr[high];
int i=low-1;
	for(int j=low;j<=high-1; ++j){
		if(arr[j]<pivot){
			++i;
			swap(arr[i],arr[j]);
		}
	}
	swap(arr[i+1],arr[high]);
	return i+1;
```
![[Pasted image 20250428153239.png]]
- Tiếp cận duyệt từ hai đầu mảng
  1. Đặt `pivot=list[right]`
  2. Dùng 2 biến chỉ số `i=left` và `j=right-1`, trong khi `i<j`
	  1. tăng `i` until `list[i]>pivot;`
	  2. giảm `j` until `list[j]` $\le$ `pivot;`
  3. Đổi chỗ `list[i]` $\leftrightarrow$ `list[j]` và lặp lại bước 2
  4. Đổi chỗ `list[i]` $\leftrightarrow$ `list[right]`
![[Pasted image 20250428210705.png]]
