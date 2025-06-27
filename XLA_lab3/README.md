
#  BÀI THỰC HÀNH 3: BIẾN ĐỔI HÌNH HỌC 

##  Mục tiêu:
- Thực hiện các phép biến đổi hình học cơ bản: tịnh tiến, xoay, phóng to, thu nhỏ.
- Áp dụng biến đổi ánh xạ tọa độ (coordinate mapping) và hiệu ứng sóng.
- Tách và xử lý các đối tượng cụ thể trong ảnh.
- Viết chương trình xử lý ảnh với giao diện dòng lệnh đơn giản.

---

##  1. Viết trương trình biến đổi ảnh

### 1.1. Chọn đối tượng trong ảnh
- Đọc ảnh `fruit.jpg`, cắt một vùng (cam) và lưu thành `orange.jpg`.

### 1.2. Tịnh tiến đơn 
- Dùng `nd.shift` để tịnh tiến ảnh đầu vào 100 pixel dọc, 25 pixel ngang.

### 1.3. Thay đổi kích thước ảnh
- Dùng `nd.zoom` để phóng to, thu nhỏ hoặc biến đổi riêng từng chiều.

### 1.4. Xoay ảnh
- Sử dụng `nd.rotate` để xoay ảnh với/không reshape.

### 1.5. Dilation và Erosion
- Thao tác trên ảnh nhị phân (hoặc ảnh xám float): Dilation mặc định và nhiều lần.

### 1.6. Coordinate Mapping
- Biến đổi ảnh bằng ánh xạ tọa độ nhiễu ngẫu nhiên (hiệu ứng dạng "nhiễu").

### 1.7. Biến đổi hình học tự định nghĩa
- Hàm `GeoFun`: biến đổi ảnh theo hàm cosine (hiệu ứng sóng nhẹ).

---

##  2. PHẦN BÀI TẬP

###  Bài 1: Tịnh tiến quả kiwi
- Ảnh: `colorful-ripe-tropical-fruits.jpg`
- Cắt chính xác quả kiwi tại tọa độ `[300:480, 920:1080]`.
- Tịnh tiến 30 pixels sang phải.
- Lưu kết quả thành `kiwi_translated.jpg`.

###  Bài 2: Đổi màu đu đủ và dưa hấu
- Dưa hấu tại `[200:650, 1200:1600]`
- Đu đủ tại `[600:850, 100:420]`
- Đổi màu đu đủ bằng đảo kênh RGB: `[:, :, ::-1]`
- Làm sáng dưa hấu bằng cộng thêm 50 và `np.clip`.
- Lưu: `papaya_colored.jpg`, `watermelon_colored.jpg`.

###  Bài 3: Xoay ngọn núi và con thuyền
- Ảnh: `quang_ninh.jpg`
- Cắt vùng:  
  - Núi: `[0:330, 410:700]`  
  - Thuyền: `[420:580, 500:700]`
- Xoay mỗi vùng 45 độ.
- Lưu: `ngon_nui.jpg`, `con_thuyen.jpg`.

###  Bài 4: Phóng to ảnh ngôi chùa 5 lần
- Ảnh: `pagoda.jpg`
- Cắt vùng chùa `[130:210, 0:600]`
- Phóng to bằng `nd.zoom(..., (5, 5, 1))`
- Lưu: `pagoda_zoom_5_lan.jpg`

---

##  3. BÀI 5  MENU XỬ LÝ ẢNH

###  Chức năng:
Chương trình tạo menu tương tác với 5 lựa chọn:

| Phím | Chức năng            |
|------|-----------------------|
| T    | Tịnh tiến             |
| X    | Xoay ảnh              |
| P    | Phóng to              |
| H    | Thu nhỏ               |
| C    | Coordinate Mapping    |

###  Cách sử dụng:
- Chạy chương trình, chọn ảnh từ thư mục `exercise`.
- Nhập phím tương ứng với phép biến đổi.
- Nhập các tham số cần thiết (góc xoay, hệ số zoom, tịnh tiến...).
- Kết quả hiển thị ngay sau đó.

