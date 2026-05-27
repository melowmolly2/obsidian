# Binary Heap
- Là cây phân dạng hoàn chỉnh
- Nút đỉnh có giá trị lớn hơn (hoặc nhỏ hơn) nút con
	- Max heap/Min heap
- **Được lưu trữ thực tế dưới dạng mảng**
## Thêm nút
1. Thêm nút mới vào cuối mảng
2. So sánh nút mới với nút cha, nếu thứ tự đảo ngược thì đổi chỗ
3. Lặp lại đổi chỗ cho đến heap đúng thứ tự
![[Pasted image 20250428212222.png]]
![[Pasted image 20250428212242.png]]
```
void swim(int a[], int k) {  
	while (k > 0 && a[k/2] < a[k]) {  
		swap(a, k/2, k);  
		k = k/2;  
	}  
}
```
## Xoá nút đỉnh
1. Loại bỏ nút đỉnh (lấy ra nút có giá trị max hoặc min)
2. **Chuyển nút cuối cùng đến đỉnh**, giảm kích thước heap
3. So sánh nút đỉnh với các nút con, nếu thứ tự đảo ngược thì đổi chỗ
	- Lặp lại việc đổi chỗ cho đến khi đúng thứ tự
![[Pasted image 20250428214506.png]]
![[Pasted image 20250428215324.png]]
```
//max heap
void sink(int index, int heapSize) {

        if(index<heapSize/2){

            int child= leftChild(index);

            if(child<heapSize-1

               &&array[child]<array[rightChild(index)])
				// lay nut con lon hon
                child++;

            if(array[index]>=array[child])return;

            swap(array[index],array[child]);

            sink(child,heapSize);

        }

        // TODO: Implement sink function

        // Compare with children and swap with larger child if needed

        // Continue until heap property is restored

    }
```
## Xoá nút bất kỳ
- Xoá nút `n` bất kỳ
- Thay thế `n` bằng nút cuối heap
- Thực hiện sink down với đỉnh `n` 
![[Pasted image 20250428220944.png]]
## Heapsort
- Là giải thuật sắp xếp ứng dụng tính chất của heap
- Xem mảng như một cây nhị phân hoàn chỉnh
- Sắp xếp mảng gồm 2 pha
	1. Tạo heap từ mảng bằng cách **vun đống từ dưới lên**
	2. Tạo mảng được sắp xếp bằng cách lần lượt lấy phần tử lớn nhất ra khỏi heap và đổi chỗ với phần tử cuối mảng
## Tạo heap: vun đống
- Vun đống cây con từ dưới lên, từ phải qua trái
- Tăng dần độ cao của cây
	- Các cây con của nó đã được vun đống
![[Pasted image 20250429111241.png]]
![[Pasted image 20250429111248.png]]
![[Pasted image 20250429111256.png]]
![[Pasted image 20250429111305.png]]
![[Pasted image 20250429111314.png]]
![[Pasted image 20250429111321.png]]
## Cài đặt
```
void sink(int index, int heapSize) {

        if(index<heapSize/2){

            int child= leftChild(index);

            if(child<heapSize-1

               &&array[child]<array[rightChild(index)])

                child++;

            if(array[index]>=array[child])return;

            swap(array[index],array[child]);

            sink(child,heapSize);

        }
    }
```
![[Pasted image 20250429111815.png]]
![[Pasted image 20250429111739.png]]
