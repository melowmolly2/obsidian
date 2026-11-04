### **CHƯƠNG 0: SỐ PHỨC (COMPLEX NUMBERS)**

Chương 0 đóng vai trò là phần kiến thức đại số bổ trợ cốt lõi cho môn Đại số tuyến tính, giúp mở rộng tập số thực $\mathbb{R}$ lên tập số phức $\mathbb{C}$ nhằm phục vụ việc nghiên cứu phương trình đặc trưng, giá trị riêng phức và các phép biến đổi hình học trong các chương sau.

---

### **1. Khái niệm Số phức & Các phép toán Đại số**

#### **a. Định nghĩa số phức**

- **Số phức** là một số có dạng biểu diễn $z = a + bi$, trong đó $a$ và $b$ là các số thực, còn $i$ là đơn vị ảo thỏa mãn hệ thức $i^2 = -1$.
- $a$ được gọi là **phần thực** của $z$, ký hiệu là $\text{Re } z$; $b$ được gọi là **phần ảo** của $z$, ký hiệu là $\text{Im } z$.
- Hai số phức bằng nhau khi và chỉ khi phần thực của chúng bằng nhau và phần ảo của chúng bằng nhau.
- Tập hợp tất cả các số phức được ký hiệu là **$\mathbb{C}$**. Mỗi số thực $a$ được coi là một số phức đặc biệt dạng $a + 0i$.

#### **b. Các phép toán đại số cơ bản**

Cho hai số phức $z_1 = a + bi$ và $z_2 = c + di$:

- **Phép cộng:** Cộng phần thực với phần thực, phần ảo với phần ảo: $$(a + bi) + (c + di) = (a + c) + (b + d)i$$
- **Phép nhân:** Thực hiện bằng phép khai triển đại số thông thường và thay $i^2 = -1$: $$(a + bi)(c + di) = (ac - bd) + (ad + bc)i$$
- **Phép trừ:** Được định nghĩa qua phép cộng với số đối: $z_1 - z_2 = z_1 + (-1)z_2$.

#### **c. Số phức liên hợp và Mô-đun**

- **Số phức liên hợp** của $z = a + bi$ được ký hiệu là $\bar{z}$ (đọc là $z$ gạch), xác định bởi $\bar{z} = a - bi$.
- Tích $z\bar{z} = (a+bi)(a-bi) = a^2 + b^2$ luôn là một số thực không âm.
- **Mô-đun (giá trị tuyệt đối)** của số phức $z$ được ký hiệu là $|z|$, là căn bậc hai không âm của $z\bar{z}$: $$|z| = \sqrt{z\bar{z}} = \sqrt{a^2 + b^2}$$

#### **d. Tính chất của Liên hợp và Mô-đun**

Cho $w, z \in \mathbb{C}$ và $r \in \mathbb{R}$:

1. $\bar{z} = z \iff z \in \mathbb{R}$.
2. $\overline{w + z} = \bar{w} + \bar{z}$.
3. $\overline{wz} = \bar{w}\bar{z}$ (đặc biệt $\overline{rz} = r\bar{z}$).
4. $z\bar{z} = |z|^2 \ge 0$.
5. $|wz| = |w||z|$.
6. $|w + z| \le |w| + |z|$ (bất đẳng thức tam giác).

#### **e. Phép chia số phức và Số phức nghịch đảo**

- Khi $z \neq 0$ (tức $|z| > 0$), số phức $z$ có **nghịch đảo nhân tử** $z^{-1}$ hay $\frac{1}{z}$ được tính theo công thức: $$\frac{1}{z} = z^{-1} = \frac{\bar{z}}{|z|^2}$$
- **Phép chia hai số phức:** Để tính thương $\frac{w}{z}$, ta nhân cả tử số và mẫu số với liên hợp $\bar{z}$ của mẫu số nhằm triệt tiêu $i$ ở mẫu: $$\frac{w}{z} = w \left(\frac{1}{z}\right) = \frac{w\bar{z}}{|z|^2}$$

---

### **2. Biểu diễn Hình học của Số phức**

#### **a. Mặt phẳng phức $\mathbb{C}$**

- Mỗi số phức $z = a + bi$ tương ứng $1-1$ với một điểm có tọa độ $(a, b)$ trên mặt phẳng thực $\mathbb{R}^2$.
- **Trục thực (Real axis):** Trục hoành $Ox$, chứa các điểm $(a, 0)$ tương ứng với số thực $a$.
- **Trục ảo (Imaginary axis):** Trục tung $Oy$, chứa các điểm $(0, b)$ tương ứng với số thuần ảo $bi$.
- Điểm biểu diễn số phức liên hợp $\bar{z} = a - bi$ đối xứng với $z$ qua trục thực.
- Mô-đun $|z| = \sqrt{a^2 + b^2}$ chính là khoảng cách từ gốc tọa độ $(0,0)$ đến điểm biểu diễn $(a,b)$.

#### **b. Biểu diễn phép cộng vector & Sự khác biệt giữa $\mathbb{R}^2$ và $\mathbb{C}$**

- Phép cộng hai số phức $z = a + bi$ và $w = c + di$ tương ứng chính xác với **phép cộng hai vector** $(a,b)$ và $(c,d)$ trong $\mathbb{R}^2$ theo quy tắc hình bình hành.
- **Khác biệt logic giữa $\mathbb{R}^2$ và $\mathbb{C}$:** Trong $\mathbb{R}^2$, ta chỉ nhân vector với một số thực (vô hướng); phép tích vô hướng hai vector cho ra số thực chứ không cho ra vector mới thuộc $\mathbb{R}^2$. Ngược lại, trong tập số phức $\mathbb{C}$, tích của hai số phức bất kỳ luôn cho ra một số phức thứ ba nằm trong chính $\mathbb{C}$.

---

### **3. Dạng Lượng giác (Tọa độ cực) & Biểu diễn Phép nhân/chia**

#### **a. Tọa độ cực và Argument**

- Cho số phức khác không $z = a + bi \neq 0$. Gọi $\varphi$ là góc giữa chiều dương của trục thực và tia nối gốc tọa độ tới điểm $(a,b)$ với $-\pi < \varphi \le \pi$.
- Góc $\varphi$ được gọi là **argument** của $z$, ký hiệu $\varphi = \arg z$.
- Theo công thức lượng giác: $$a = |z|\cos\varphi \quad \text{và} \quad b = |z|\sin\varphi$$
- Do đó, $z$ có **dạng lượng giác**: $$z = |z|(\cos\varphi + i\sin\varphi)$$

#### **b. Phép nhân và phép chia dạng lượng giác**

Cho $z = |z|(\cos\varphi + i\sin\varphi)$ và $w = |w|(\cos\vartheta + i\sin\vartheta)$:

- **Phép nhân:** Mô-đun của tích bằng tích hai mô-đun, argument của tích bằng tổng hai argument: $$wz = |w||z|[\cos(\vartheta + \varphi) + i\sin(\vartheta + \varphi)]$$
- **Phép chia:** Mô-đun của thương bằng thương hai mô-đun, argument của thương bằng hiệu hai argument: $$\frac{w}{z} = \frac{|w|}{|z|}[\cos(\vartheta - \varphi) + i\sin(\vartheta - \varphi)]$$

#### **c. Ý nghĩa hình học của phép nhân**

- Nhân một số phức $z$ bất kỳ với số phức $w = \cos\vartheta + i\sin\vartheta$ (có mô-đun bằng 1) tương đương với việc **xoay $z$ một góc $\vartheta$** quanh gốc tọa độ.
- Đặc biệt, đơn vị ảo $i$ có $|i| = 1$ và $\arg i = \pi/2$, nên **nhân một số phức với $i$ chính là xoay số phức đó đi một góc vuông $\pi/2$ rad ($90^\circ$)** ngược chiều kim đồng hồ.

---

### **4. Công thức Euler & Lũy thừa De Moivre**

#### **a. Công thức Euler & Dạng mũ cực**

- **Công thức Euler** thiết lập liên hệ giữa hàm mũ phức và hàm lượng giác: $$e^{i\varphi} = \cos\varphi + i\sin\varphi$$
- Nhờ đó, mọi số phức $z$ có mô-đun $r = |z|$ và argument $\varphi$ đều được viết dưới **dạng mũ cực** ngắn gọn: $$z = r e^{i\varphi}$$
- Cho $\varphi = \pi$, ta có $e^{i\pi} = \cos\pi + i\sin\pi = -1$, suy ra **đồng nhất thức Euler** nổi tiếng: $$e^{i\pi} + 1 = 0$$

#### **b. Định lý De Moivre (Lũy thừa bậc cao)**

Áp dụng công thức nhân dạng lượng giác liên tiếp cho $z = r(\cos\varphi + i\sin\varphi)$, với mọi số nguyên dương $k$, ta có **Định lý De Moivre**: $$z^k = r^k(\cos k\varphi + i\sin k\varphi)$$

---

### **5. Căn bậc $n$ của Số phức & Căn của Đơn vị**

#### **a. Căn bậc $n$ của số phức**

- Số phức $u$ được gọi là một **căn bậc $n$ phức** của $z$ nếu $u^n = z$ (tức $u^n - z = 0$).
- Theo định lý cơ bản của đại số, một số phức $z = r(\cos\varphi + i\sin\varphi) \neq 0$ có **đúng $n$ căn bậc $n$ phức phân biệt**, cho bởi công thức: $$u_k = \sqrt[n]{r} \left( \cos \frac{\varphi + 2k\pi}{n} + i\sin \frac{\varphi + 2k\pi}{n} \right) \quad (k = 0, 1, \dots, n-1)$$

#### **b. Căn của đơn vị (Roots of Unity)**

- Khi $z = 1 = \cos 0 + i\sin 0$, ta thu được $n$ **căn bậc $n$ của đơn vị**: $$u_k = \cos \frac{2k\pi}{n} + i\sin \frac{2k\pi}{n} \quad (k = 0, 1, \dots, n-1)$$
- Các điểm biểu diễn $n$ căn bậc $n$ này nằm trên đường tròn đơn vị và tạo thành các đỉnh của một **đa giác đều $n$ cạnh** nội tiếp đường tròn tâm tại gốc tọa độ.

---

🎯 **Bạn có muốn chúng ta cùng làm một số bài tập minh họa về Chương 0 (như tính lũy thừa bằng định lý De Moivre, tìm các căn của số phức hoặc giải phương trình trên tập số phức) không?**