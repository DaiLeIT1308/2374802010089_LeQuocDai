# Giải thích Notebook `thi_thu.ipynb`

## Câu 1 : Cho ảnh có tên là a.jpg và thực hiện các yêu cầu.
Cell này thực hiện một chuỗi các phép biến đổi trên một ảnh duy nhất có tên `a.jpg`.

- **Mean Filter**: Áp dụng bộ lọc trung bình (làm mờ) với kernel 5x5 để làm mịn ảnh.
- **Edge Detection (Phát hiện biên)**:
  - Sử dụng thuật toán **Canny** để phát hiện các biên cạnh sắc nét.
  - Sử dụng bộ lọc **Sobel** để tính toán gradient và làm nổi bật các cạnh theo cả chiều ngang và dọc.
- **Random Color Change (Đổi màu ngẫu nhiên)**: Tách các kênh màu (Blue, Green, Red), xáo trộn thứ tự của chúng và kết hợp lại để tạo ra một ảnh có màu sắc ngẫu nhiên. Kết quả được lưu vào file `a_random_color.jpg`.
- **HSV Conversion (Chuyển đổi sang không gian màu HSV)**:
  - Chuyển ảnh từ không gian màu BGR sang HSV (Hue, Saturation, Value).
  - Tách riêng từng kênh H, S, V và lưu chúng thành các ảnh grayscale riêng biệt: `a_hue.jpg`, `a_saturation.jpg`, và `a_value.jpg`.

## Câu 2: Viết một chương trình Python sử dụng OpenCV để tạo menu động cho phép người dùng chọn các phương pháp biến đổi ảnh từ một danh sách mở rộng, áp dụng cho nhiều ảnh cùng lúc, và thực hiện các phân tích bổ sung.

Câu 2 là một chương trình có menu tương tác cho phép người dùng chọn và áp dụng các phép biến đổi khác nhau lên một loạt ảnh theo phím bấm tương ứng (`image1.jpg`, `image2.jpg`, `image3.jpg`).

- **Các phép biến đổi có sẵn**:
  - `i`: **Image Inverse** - Đảo ngược màu ảnh.
  - `g`: **Gamma Correction** - Hiệu chỉnh gamma với giá trị ngẫu nhiên.
  - `l`: **Log Transformation** - Biến đổi logarit.
  - `h`: **Histogram Equalization** - Cân bằng lược đồ xám.
  - `c`: **Contrast Stretching** - Giãn lược đồ tương phản.
  - `a`: **Adaptive Histogram Equalization (CLAHE)** - Cân bằng lược đồ xám thích ứng.
- **Hoạt động**: Sau khi người dùng chọn một tùy chọn, chương trình sẽ áp dụng phép biến đổi lên tất cả các ảnh, lưu kết quả ra các file riêng biệt (ví dụ: `output_gamma_1.jpg`), và hiển thị ảnh gốc cùng ảnh đã xử lý để so sánh.

## Câu 3: Viết một chương trình Python sử dụng OpenCV để xử lý ba ảnh: colorful-ripe-tropical-fruits.jpg, quang-ninh.jpg, và pagoda.jpg với các phương pháp biến đổi và tiền xử lý nâng cao.

Câu 3 chứa một tập hợp các hàm độc lập để thực hiện các yêu cầu xử lý ảnh cụ thể trên các file ảnh khác nhau.

- **Yêu cầu 1**: Tăng kích thước của ảnh `colorful-ripe-tropical-fruits.jpg` thêm 30 pixel cả chiều rộng và chiều cao.
- **Yêu cầu 2**: Xoay ảnh `quang_ninh.jpg` 45 độ theo chiều kim đồng hồ, sau đó lật ảnh theo chiều ngang.
- **Yêu cầu 3**: Tăng kích thước ảnh `pagoda.jpg` lên 5 lần, sau đó áp dụng bộ lọc **Gaussian Blur** 7x7 để làm mịn.
- **Yêu cầu 4**: Điều chỉnh độ sáng và độ tương phản của ảnh `pagoda.jpg` bằng cách sử dụng công thức `I_out = alpha * I_in + beta`.

tất cả các yêu cầu đều hiển thị ảnh gốc / ảnh đã xử lý bằng `plt.show()`