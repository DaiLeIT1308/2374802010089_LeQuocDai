# Bài tập thêm.



## Bài 1: Tịnh tiến và hiệu ứng sóng cho quả kiwi
- Mục tiêu: Cắt ảnh quả kiwi, tịnh tiến sang phải 50 pixel và xuống dưới 30 pixel, sau đó áp dụng hiệu ứng sóng dựa trên hàm sin.
- Kỹ thuật sử dụng:
  - Tịnh tiến ảnh bằng `scipy.ndimage.shift`.
  - Tạo hiệu ứng sóng bằng `map_coordinates` và biến đổi tọa độ.
- Kết quả: Lưu ảnh ra file `kiwi_wave.jpg`.

## Bài 2: Gradient màu và nền trong suốt
- Mục tiêu: 
  - Đổi màu quả đu đủ theo gradient từ đỏ sang xanh lá.
  - Đổi màu quả dưa hấu theo gradient từ vàng sang tím.
  - Ghép hai ảnh đã đổi màu lên một nền trong suốt (RGBA).
- Kỹ thuật sử dụng:
  - Tạo gradient màu bằng `numpy.linspace`.
  - Ghép ảnh vào ảnh mới 4 kênh (RGBA).
- Kết quả: Lưu ảnh dưới dạng PNG có nền trong suốt, tên `fruits_gradient_combined.png`.

## Bài 3: Xoay và phản chiếu ảnh núi và thuyền
- Mục tiêu: 
  - Xoay ảnh núi và thuyền 45 độ (giữ nguyên kích thước).
  - Áp dụng phản chiếu dọc (vertical mirror).
  - Ghép hai ảnh lên cùng một canvas trắng.
- Kỹ thuật sử dụng:
  - `rotate` với `reshape=False`.
  - `np.flipud` để phản chiếu.
  - Ghép ảnh bằng cách tạo canvas trắng bằng `numpy.ones`.
- Kết quả: Lưu ảnh kết quả với tên `mountain_boat_mirror.jpg`.

## Bài 4: Phóng to và uốn cong ảnh ngôi chùa
- Mục tiêu: 
  - Cắt vùng ảnh ngôi chùa.
  - Phóng to ảnh lên 5 lần.
  - Áp dụng biến đổi hình học tự định nghĩa để tạo hiệu ứng "uốn cong".
- Kỹ thuật sử dụng:
  - `zoom` để phóng to.
  - `geometric_transform` với hàm định nghĩa tùy chỉnh.
- Kết quả: Lưu ảnh kết quả với tên `pagoda_warped.jpg`.

## Bài 5: Chương trình menu tương tác xử lý ảnh
- Mục tiêu: Tạo một chương trình tương tác cho phép người dùng chọn ảnh và áp dụng một trong các phép biến đổi sau:
  1. Tịnh tiến (nhập dx, dy).
  2. Xoay (nhập góc và chọn reshape).
  3. Phóng to hoặc thu nhỏ (nhập hệ số zoom).
  4. Làm mờ Gaussian (nhập sigma).
  5. Áp dụng hiệu ứng sóng (nhập biên độ).
- Kỹ thuật sử dụng:
  - `input()` để nhận tham số từ người dùng.
  - Giao diện dòng lệnh.
  - Biến đổi ảnh bằng các hàm từ `scipy.ndimage`.
- Kết quả: Hiển thị ảnh sau biến đổi. Người dùng có thể chỉnh sửa để lưu nếu cần.

## Yêu cầu thư mục và ảnh
- Thư mục `exercise/` cần chứa các ảnh gốc như:
  - `colorful-ripe-tropical-fruits.jpg`
  - `papaya.jpg`
  - `watermelon.jpg`
  - `quang_ninh.jpg`
  - `pagoda.jpg`
