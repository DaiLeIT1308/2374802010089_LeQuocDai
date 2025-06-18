# GIẢI THÍCH CODE TRONG FILE [TUAN_2.ipynb](./TUAN_2.ipynb)

## 1. Phần thực hành trên lớp

### 1.1 Image inverse

##### Khi chạy `cell 2`, chương trình sẽ chạy như sau:

- Load ảnh cần xử lý, (ở đây lấy `bird.png` làm ví dụ), khi load kèm theo `.convert("L")` để chuyển ảnh về grayscale
- Chuyển đổi ảnh được load về dạng array để dễ dàng hơn cho các bước xử lý tiếp theo (bản chất ảnh là một ma trận các giá trị pixel, chuyển về array, là mỗi giá trị pixel thành dạng số mà chúng ta có thể tính toán và thay đổi)
- lấy `255` trừ đi giá trị pixel hiện có trong ảnh, điều này sẽ làm đảo ngược màu của ảnh | ví dụ: `255 - 0(giá trị pixel gốc)` thì pixel đen -> trắng
- chuyển đổi ảnh từ dạng array về lại ảnh bình thường và hiển thị hình ảnh mới đã được xử lý

### 1.2 Gamma correction

##### Khi chạy `cell 3`, chương trình sẽ chạy như sau:

- Load ảnh cần xử lý, (ở đây lấy `bird.png` làm ví dụ), khi load kèm theo `.convert("L")` để chuyển ảnh về grayscale
- Chuyển đổi ảnh sang dạng array... như đã nói ở trên
- Đặt giá trị Gamma mặc định là `0.5`, có thể thay đổi tùy thích
- Thực hiện chuyển đổi kiểu dữ liệu của các pixel sang `float` để thực hiện các phép toán chính xác
- Tìm giá trị pixel lớn nhất trong toàn bộ array thông qua `np.max()`
- Chuẩn hóa các giá trị pixel (normalize) về thang giá trị `[0,1]` để thuận tiện hơn cho việc xử lý, trong phần này sẽ `+1` vào mỗi pixel trước để tránh lỗi `divide by zero encountered`, đảm bảo giá trị dương
- Thực hiện phép toán biến đổi Gamma, lấy giá trị đã được `normalize` trước đó nhân với giá trị `gamma` đã đặt trước đó, có ý nghĩa như sau:
  - `Logarit` hóa ảnh để xử lý độ tương phản
  - chỉnh `Gamma` trong miền logarit
- Dùng hàm mũ `exp()` để đảo ngược phép log, đưa ảnh về miền ban đầu, sau đó nhân với `255` để đưa ảnh về dạng `8-bit`
- Chuyển đổi về `uint8`, đảm bảo các giá trị pixel trong khoảng `0-255` như ảnh bình thường
- hiển thị ảnh đã qua xử lý dưới dạng trắng đen, kết thúc chương trình

### 1.3 Log transformation

##### Khi chạy `cell 4`, chương trình sẽ chạy như sau:

- Load ảnh cần xử lý, (ở đây lấy `bird.png` làm ví dụ), khi load kèm theo `.convert("L")` để chuyển ảnh về grayscale
- Chuyển đổi ảnh sang dạng array... như đã nói ở trên
- Thực hiện chuyển đổi kiểu dữ liệu của các pixel sang `float` để thực hiện các phép toán chính xác
- Tìm giá trị pixel lớn nhất trong toàn bộ array thông qua `np.max()`
- Normalize sử dụng công thức nén dải rộng `(128*np.log(1+img1)) / np.log(1+max_value)` để tối ưu lại các pixel làm cho ảnh dễ nhìn hơn, có đảm bảo `+1` để tránh lỗi `divide by zero encountered`
- Thực hiện phép toán biến đổi Gamma, lấy giá trị đã được `normalize` trước đó nhân với giá trị `gamma` đã đặt trước đó (như đã giải thích ở trên), có đảm bảo để không bị lỗi `divide by zero encountered`
- Dùng hàm mũ `exp()` để đảo ngược phép log, đưa ảnh về miền ban đầu, sau đó nhân với `255` để đưa ảnh về dạng `8-bit`
- Chuyển đổi về `uint8`, đảm bảo các giá trị pixel trong khoảng `0-255` như ảnh bình thường
- hiển thị ảnh đã qua xử lý dưới dạng trắng đen, kết thúc chương trình

### 1.4 Histogram euqalization

##### Khi chạy `cell 5`, chương trình sẽ chạy như sau:

- Load ảnh cần xử lý, (ở đây lấy `bird.png` làm ví dụ), khi load kèm theo `.convert("L")` để chuyển ảnh về grayscale
- Chuyển đổi ảnh sang dạng array... như đã nói ở trên
- Dùng `iml.flatten()` chuyển mảng từ dạng nhiều chiều `[1, 2], [3, 4]` về 1 chiều `[1,2,3,4]` để tiện cho việc ánh xạ giá pixel.
- tính toán histogram của ảnh bằng hàm `np.histogram()`
- tính toán hàm phân phối tích lũy (CDF) của histogram bằng hàm `np.cumsum()`
- chuẩn hóa CDF để giá trị pixel trong khoảng `0-255`
- ánh xạ giá trị pixel của ảnh gốc đến giá trị pixel đã được chuẩn hóa
- hiển thị ảnh đã qua xử lý dưới dạng trắng đen, kết thúc chương trình

### 1.5 Contrast stretching

##### Khi chạy `cell 6`, chương trình sẽ chạy như sau:

- Load ảnh cần xử lý, (ở đây lấy `bird.png` làm ví dụ), khi load kèm theo `.convert("L")` để chuyển ảnh về grayscale
- Chuyển đổi ảnh sang dạng array... như đã nói ở trên
- Tìm giá trị pixel lớn nhất trong toàn bộ array thông qua `np.max()` và nhỏ nhất bằng `np.min()`
- chuyển đổi về `float` để thực hiện các phép toán chính xác
- kéo giãn độ tương phản của ảnh bằng công thức `255 * (img - min) / (max - min)`
- chuyển đổi ảnh từ `array` sau xử lý thành ảnh bình thường
- hiển thị ảnh đã qua xử lý , kết thúc chương trình

### 1.6 Biến đổi Fourier

##### Khi chạy `cell 7`, chương trình sẽ chạy như sau:

- Load ảnh cần xử lý, (ở đây lấy `bird.png` làm ví dụ), khi load kèm theo `.convert("L")` để chuyển ảnh về grayscale
- Chuyển đổi ảnh sang dạng array. Nhưng dùng `np.asarray` thay vì `np.asanyarray` để đảm bảo đầu vào cho các hàm `fft`
- `ftt2` là phép biến đổi Fourier 2 chiều (ảnh thành miền tần số)
- `fftshift` để đưa thành phần có miền tần số thấp về trung tâm, cao ra rìa
- Tạo bộ lọc BLFF **(Butterworth Lowpass Filter)** có kích thước bằng ảnh nhằm mục đích giữ lại tần số thấp và làm mờ tần số cao, giúp giữ lại các đặc trưng sắc nét, mịn của ảnh, với mỗi pixel, tính khoảng cách đến tâm ảnh (`r`), nếu `r > d_0`(bán kính cắt) thì giảm bớt cường độ của pixel và áp dụng bộ lọc
- biến đổi Fourier ngược lại về miền ảnh bằng `ifft2`
- chuyển đổi về dạng `float`, bởi vì sau khi xử lý ảnh không còn dạng `uint8` mà có thể là `[2516.78007157 2261.37380907....`, sau đó chuyển về ảnh bình thường bằng `np.abs`
- hiển thị ảnh đã qua xử lý, kết thúc chương trình

## 2. Phần bài tập

### Bài tập 1: Viết chương trình biến đổi ảnh dựa theo những cách biến đổi đã học (image inverse, gamma, log, histogram, contrast)

khi chạy cell ( hoặc function `image_transformation()` ), thì nó sẽ chạy như sau:

- Load ảnh cần xử lý, (ở đây lấy `bird.png` làm ví dụ), khi load kèm theo `.convert("L")` để chuyển ảnh về grayscale

- Chuyển đổi ảnh được load về dạng array để dễ dàng hơn cho các bước xử lý tiếp theo (bản chất ảnh là một ma trận các giá trị pixel, chuyển về array, là mỗi giá trị pixel thành dạng số mà chúng ta có thể tính toán và thay đổi)

- Cho người dùng chọn phương pháp biến đổi ảnh | `.upper()` để không phân biệt input hoa/thường

- tạo các vòng lặp `if` có chứa các phương thức để biến đổi ảnh với từng phím tương ứng:

  - I : đảo ngược màu hình ảnh (Image inverse)
  - G : Gamma correction
  - L : Log transformation
  - H : Histogram equalization
  - C : Constant stretching

- Khi xử lý ảnh xong thì sẽ gọi thêm `show_result()` để hiển thị ra ảnh gốc / ảnh đã xử lý trên cùng một frame
