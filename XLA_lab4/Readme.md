
#  LAB 4: PHÂN VÙNG ẢNH 



## 1. Cài đặt thư viện

Cài đặt các thư viện cần thiết:

```bash
pip install opencv-python
````

---

## 2: Viết chương trình phân vùng ảnh

###  2.1: Phân vùng theo Histogram

* `2.1.1` **Otsu Thresholding** – Tự động tìm ngưỡng tối ưu.
* `2.1.2` **Adaptive Thresholding** – Phân ngưỡng cục bộ theo từng vùng ảnh.

###  2.2: Phân vùng theo Region (Watershed)

* Sử dụng kỹ thuật distance transform + erosion để xác định foreground và thực hiện watershed segmentation.

###  2.3: Biến đổi hình thái ảnh nhị phân (Morphology)

* `2.3.1` Dilation
* `2.3.2` Opening
* `2.3.3` Erosion
* `2.3.4` Closing

---

##  PHẦN BÀI TẬP

###  Bài 1 – LangBiang (Tịnh tiến + Otsu)

* Cắt vùng LangBiang trong `dalat.jpg`.
* Dịch sang phải 100px.
* Phân vùng bằng Otsu (ngưỡng \* 0.3).
*  Lưu thành `lang_biang.jpg`.

###  Bài 2 – Hồ Xuân Hương (Xoay + Adaptive Threshold)

* Cắt vùng Hồ Xuân Hương.
* Xoay 45 độ.
* Phân vùng với `threshold_local(... offset=60)`.
*  Lưu thành `ho_xuan_huong.jpg`.

###  Bài 3 – Quảng trường Lâm Viên (Coordinate Mapping + Binary Closing)

* Cắt vùng Quảng trường.
* Áp dụng ánh xạ tọa độ (ví dụ lật ngang).
* Thực hiện `binary_closing`.
*  Lưu thành `quan_truong_lam_vien.jpg`.

---

##  Bài 4 – Tạo Menu Xử lý Ảnh

###  Menu gồm:

```text
geometric_transformation
 ├── coordinate_mapping
 ├── Rotate
 ├── Scale
 └── Shift
segment
 ├── Adaptive_thresholding
 ├── Binary_dilation
 ├── Binary_erosion
 └── Otsu
```

###  Cách sử dụng chương trình:

* Chạy chương trình `main()`.
* Người dùng nhập **1 chức năng**, hoặc **kết hợp 2 chức năng** từ:

  * 1 thuộc `geometric_transformation`
  * 1 thuộc `segment`

###  Ví dụ nhập:

* `rotate`
* `coordinate_mapping`
* `rotate otsu`
* `scale adaptive_thresholding`

###  Kết quả:

* Ảnh sẽ được xử lý theo các thao tác người dùng nhập.
* Hiển thị trực quan bằng `matplotlib`.

---

##  Cấu trúc thư mục đề xuất

```bash
lab4/
├── exercise/
│   └── dalat.jpg
├── dil_img.gif
├── lab4_processing.py
├── README.md
```

