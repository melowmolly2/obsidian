# Cây nhị phân 
- Là cấu trúc dữ liẹu dựa trên liên kết các node
- Mỗi node có thể liên kết với các nút con 
- Cây nhị phân: chỉ có tối đa 2 nút con, là cấu trúc cây phổ biến 
## Cân bằng cây
- Điều chỉnh độ cao để cây cân bằng 
- Điều chỉnh thông qua phép "xoay cây"
	- Di chuyển cây con từ nhánh trái qua nhánh phải hoặc ngược lại 
	- Thay đổi nút đỉnh để đảm bảo tính chất của cây
![[Pasted image 20250426155636.png]]
Xoay trái: 
```
Node*y= x->right;

        Node* tmp=y->left;

        y->left=x;

        x->right=tmp;
        
return y;
```
Xoay phải:
```
 Node* x= y->left;

        Node * tmp= x->right;

        x->right=y;

        y->left=tmp;

return x; 
```
# Cây AVL
- Là cây BST cân bằng cao
	- Độ lệch tối đa 1
	- Mỗi nút chứa thêm thông tin để cân bằng cây (hệ số cân bằng)
- Với một cây AVL
	- Thêm bớt nút giống BST
	- Nếu cây mới mất cân bằng ($|\text{dộ lệch}|\ge 2$) thì thực hiện phép xoay cây để cân bằng cây
	- Thực hiên từ dưới lên với các cây con chứa nút thêm bớt
- Cây lêch trái: 
	- Cây con trái lệch trái: xoay phải cây trái
	- Cây con trái lệch phải: xoay trái cây trái, xoay phải cây gốc
- Cây lệch phải: 
	- Cây con phải lệch phải: xoay trái cây phải
	- Cây con phải lệch trái: xoay phải cây phải
- Thông tin cân bằng cây: 
	- Lưu độ cao của cây
- Lưu lại tổ tiên của nút được thêm/bớt
	- Để lần ngược tìm các nút cần xoay cây