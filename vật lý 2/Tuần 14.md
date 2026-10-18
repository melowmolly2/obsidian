# Lý thuyết cần nhớ tuần 14 (Chương 16 và 17)

## Hằng số cần thuộc

$$h = 6{,}626\times10^{-34}\ \text{J·s} = 4{,}136\times10^{-15}\ \text{eV·s},\qquad hc = 1240\ \text{eV·nm}$$

$$m_e = 9{,}11\times10^{-31}\ \text{kg},\quad m_p = 1{,}673\times10^{-27}\ \text{kg},\quad 1\ \text{eV}=1{,}602\times10^{-19}\ \text{J},\quad \hbar = \frac{h}{2\pi}$$

---

## Chương 16: Photon và tính chất hạt của ánh sáng

**1. Photon**

$$E = hf = \frac{hc}{\lambda},\qquad p = \frac{h}{\lambda} = \frac{E}{c}$$

Công suất $P$ phát ra ánh sáng đơn sắc thì số photon phát ra mỗi giây là:

$$\frac{N}{t} = \frac{P}{E} = \frac{P\lambda}{hc}$$

Tần số $f$ là đặc trưng của mỗi photon, còn số photon mỗi giây phụ thuộc công suất. Hai đại lượng này khác nhau (Bài 1c).

**2. Hiệu ứng quang điện**

$$hf = \phi + K_{\max},\qquad K_{\max} = eV_s = \tfrac12 m v_{\max}^2$$

$$f_0 = \frac{\phi}{h},\qquad \lambda_0 = \frac{hc}{\phi}\quad(\text{ngưỡng quang điện})$$

- $K_{\max}$ chỉ phụ thuộc tần số (bước sóng), không phụ thuộc cường độ.
- Cường độ chỉ quyết định số photon, tức số quang electron mỗi giây. Nếu mỗi photon bứt ra một electron thì số electron/s bằng số photon/s.
- Giảm công suất một nửa, giữ nguyên $\lambda$: số electron/s giảm một nửa.
- Giảm $\lambda$ một nửa, giữ nguyên công suất: năng lượng mỗi photon tăng gấp đôi nên số photon/s giảm một nửa, do đó số electron/s giảm một nửa (Bài 5c, 5d).

**3. Tia X: ống phát tia X**

$$\lambda_{\min} = \frac{hc}{eV}$$

**4. Tán xạ Compton**

$$\Delta\lambda = \lambda' - \lambda = \frac{h}{mc},(1-\cos\phi),\qquad \frac{h}{mc} = 2{,}426\ \text{pm}$$

Bảo toàn năng lượng: $\dfrac{hc}{\lambda} = \dfrac{hc}{\lambda'} + K_e$

Với electron có vận tốc lớn (Bài 6) phải dùng biểu thức tương đối tính:

$$K_e = (\gamma-1)mc^2,\qquad \gamma = \frac{1}{\sqrt{1-v^2/c^2}}$$

**5. Nguyên lý bất định Heisenberg**

$$\Delta x,\Delta p_x \ge \frac{\hbar}{2},\qquad \Delta E,\Delta t \ge \frac{\hbar}{2}$$

Với khe hẹp rộng $a$ (Bài 4):

- $\Delta y \approx a$ nên $\Delta p_y \ge \dfrac{\hbar}{2a}$.
- Góc lệch ước lượng: $\tan\theta \approx \dfrac{\Delta p_y}{p} = \dfrac{\Delta p_y,\lambda}{h}$.
- Bề rộng vân trung tâm: $w = 2L\tan\theta$.

---

## Chương 17: Tính chất sóng của hạt và mẫu Bohr

**1. Bước sóng de Broglie**

$$\lambda = \frac{h}{p} = \frac{h}{mv}\quad(v\ll c)$$

Với cùng vận tốc, hạt có khối lượng lớn hơn thì $\lambda$ nhỏ hơn: $\lambda \propto 1/m$ (Bài 1: $\lambda_p = \lambda_e \cdot m_e/m_p$). Với hạt có động năng $K$: $\lambda = \dfrac{h}{\sqrt{2mK}}$.

**2. Mẫu Bohr cho nguyên tử hydro**

$$E_n = -\frac{13{,}6\ \text{eV}}{n^2},\qquad r_n = n^2 a_0,\quad a_0 = 0{,}529\times10^{-10}\ \text{m}$$

Chuyển mức $n_i \to n_f$:

$$|\Delta E| = hf = \frac{hc}{\lambda},\qquad \frac{1}{\lambda} = R\left|\frac{1}{n_f^2} - \frac{1}{n_i^2}\right|,\quad R = 1{,}097\times10^{7}\ \text{m}^{-1}$$

Nguyên tử bất kỳ (Bài 2, 39.29):

- Hấp thụ photon: $E_{\text{sau}} = E_{\text{đầu}} + \dfrac{hc}{\lambda}$
- Phát xạ photon: $E_{\text{sau}} = E_{\text{đầu}} - \dfrac{hc}{\lambda}$

Khoảng cách giữa các mức khi $n$ lớn:

$$E_{n+1}-E_n = 13{,}6\left[\frac{1}{n^2}-\frac{1}{(n+1)^2}\right] = 13{,}6,\frac{2n+1}{n^2(n+1)^2};\xrightarrow{n\gg1};\frac{2,(13{,}6\ \text{eV})}{n^3}$$

> **Lưu ý:** đề Bài 2 (39.22b) ghi giới hạn là $\dfrac{13{,}6,\text{eV}}{n^3}$, nhưng khai triển đúng cho hệ số là $2\times13{,}6$ eV $/n^3$. Có vẻ đề bị thiếu hệ số 2, nên bạn nên kiểm tra lại với đề gốc hoặc thầy cô.

Khoảng cách giữa các mức năng lượng giảm khi $n$ tăng. Khoảng cách giữa các bán kính thì ngược lại:

$$r_{n+1}-r_n = (2n+1)a_0$$

nên nó tăng theo $n$.

**3. Bức xạ vật đen**

Định luật Wien:

$$\lambda_m T = 2{,}898\times10^{-3}\ \text{m·K},\qquad f = \frac{c}{\lambda_m}$$

Định luật Stefan–Boltzmann: $I = \sigma T^4$, với $\sigma = 5{,}67\times10^{-8}\ \text{W/(m}^2\text{K}^4)$.

Nhiệt độ càng cao thì đỉnh phổ càng dịch về phía bước sóng ngắn (Bài 4).

**4. Cường độ và số photon (Bài 3, chương 17)**

$$I = \frac{P}{A},\qquad A = \frac{\pi d^2}{4}$$

$$\text{Số photon/(đơn vị diện tích · xung)} = \frac{P,\tau}{E_{\text{photon}},A}$$

---

## Mẹo làm bài

- Đổi đơn vị trước: nm sang m, eV sang J (hoặc dùng $hc = 1240$ eV·nm cho nhanh).
- Bài quang điện thường đi theo chuỗi: $E_{\text{photon}} \to K_{\max} \to \phi$ hoặc $V_s$ $\to v$.
- Bài Compton: tìm $\lambda_{\min}$ từ $eV$ trước, rồi mới dùng $\Delta\lambda$.
- Bài 6 (38.36): dùng $K_e = (\gamma - 1)mc^2$ để tìm $\lambda$ từ $\lambda'$, rồi tìm $\phi$ từ công thức Compton.

Bạn muốn mình giải chi tiết bài nào không?