#  LAB 5: XÁC ĐỊNH ĐỐI TƯỢNG TRONG ẢNH

### 2 VIẾT CHƯƠNG TRÌNH GÁN NHÃN ẢNH
### 2.1  Gắn nhãn ảnh 

**Mục đích**: Xác định và gắn nhãn các đối tượng riêng biệt trong ảnh nhị phân.

**Kỹ thuật sử dụng**:

* `threshold_otsu()` – Phân ngưỡng ảnh xám.
* `label()` – Gắn nhãn vùng liên thông.
* `regionprops()` – Vẽ bounding box.

**Kết quả**: Hiển thị ảnh với các hộp bao quanh (màu đen) mỗi đối tượng.

---

### 2.2  Dò cạnh theo chiều dọc

**Mục đích**: Phát hiện sự thay đổi theo trục dọc.

**Kỹ thuật sử dụng**:

* Dùng `nd.shift()` để dịch ảnh.
* Trừ ảnh gốc với ảnh đã dịch → làm nổi bật viền.

**Kết quả**: Ảnh thể hiện các biên dọc rõ nét.

---

### 2.3  Dò cạnh bằng Sobel Filter

**Mục đích**: Xác định cạnh bằng đạo hàm theo trục X và Y.

**Kỹ thuật sử dụng**:

* `nd.sobel(image, axis=0)` và `axis=1`
* Kết hợp biên X và Y bằng công thức:

  ```python
  edges = np.hypot(grad_x, grad_y)
  ```

**Kết quả**: Hiển thị bản đồ cạnh sắc nét.

---

### 2.4 Xác định góc của đối tượng

**Mục đích**: Tìm điểm góc (corner points) – nơi có biến đổi mạnh theo nhiều hướng.

**Kỹ thuật sử dụng**:

* Đạo hàm theo `sobel`.
* Áp dụng công thức Harris:

    R=det(M)−α⋅(trace(M))^2
**Kết quả**: Hiển thị bản đồ góc (điểm R lớn thể hiện góc rõ).

---
### 2.5	Dò tìm hình dạng cụ thể trong ảnh với Hough Transform
### 2.5.1	Dò tìm đường thẳng trong ảnh

**Mục đích**: Tìm đường thẳng trong ảnh.

**Kỹ thuật sử dụng**:

* Biến đổi không gian ảnh thành (r, θ).
* Tạo ảnh không gian Hough để tích lũy.

**Kết quả**: Hiển thị không gian Hough với các điểm sáng biểu thị đường thẳng.

---

### 2.5.2	Dò tìm đường tròn trong ảnh

**Mục đích**: Phát hiện đặc trưng hình tròn trong ảnh.

**Kỹ thuật sử dụng**:

* Dùng `corner_harris()` → điểm góc.
* Suy luận đặc trưng tròn từ phân bố góc.

**Kết quả**: Ảnh với các điểm phản hồi Harris quanh hình tròn.

---

### 2.6	Image matching

**Mục đích**: So sánh sự tương đồng giữa hai ảnh.

**Kỹ thuật sử dụng**:

* Dò điểm góc bằng `corner_harris`.
* Trích mô tả từ vùng lân cận quanh mỗi điểm.
* So khớp bằng khoảng cách Euclidean (`cdist`).

**Kết quả**: Hiển thị 2 ảnh ghép đôi, nối các điểm khớp bằng đường màu đỏ.

---
