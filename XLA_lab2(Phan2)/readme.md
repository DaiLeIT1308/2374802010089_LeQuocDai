
## 2. Phần bài tập

### **Bài tập 2: Viết chương trình tạo menu cho phép người dùng chọn các phương pháp biến đổi ảnh như sau:**

* **Fast Fourier Transform**
* **Butterworth Lowpass Filter**
* **Butterworth Highpass Filter**

Khi chạy cell (hoặc function **`fourier_menu()`**), thì chương trình sẽ hoạt động như sau:

* **Load ảnh** cần xử lý (ở đây sử dụng ảnh *`bird.png`*) và dùng `.convert("L")` để chuyển ảnh về dạng **grayscale**.

* Dùng `np.asarray()` để **chuyển ảnh thành mảng numpy** – giúp dễ dàng thao tác và biến đổi ảnh trong các bước tiếp theo.

* **Hiển thị menu lựa chọn**, cho phép người dùng chọn giữa các phương pháp xử lý trong miền tần số:

  * **1**: *Fast Fourier Transform*
  * **2**: *Butterworth Lowpass Filter*
  * **3**: *Butterworth Highpass Filter*
  * **Q**: *Thoát chương trình*

* Khi người dùng **chọn một phương pháp**, chương trình sẽ thực hiện các bước sau:

  * Áp dụng biến đổi tương ứng (gọi đúng hàm xử lý: **`fast_fourier_transform`**, **`butterworth_lowpass_filter`**, hoặc **`butterworth_highpass_filter`**).

  * Với bộ lọc Butterworth, người dùng có thể nhập thêm tham số như:

    * `d0`: *Cut-off radius*
    * `n`: *Order of filter*

* Sau khi xử lý xong, gọi hàm **`show_results()`** để hiển thị **ảnh gốc** và **ảnh sau biến đổi** song song cạnh nhau.

  ### **Bài tập 3: Viết chương trình chọn ngẫu nhiên các phương pháp biến đổi ảnh**

Khi chạy cell (hoặc gọi function **`random_transformation_menu()`**), chương trình sẽ hoạt động như sau:

* **Load ảnh** cần xử lý (ở đây sử dụng ảnh *`bird.png`*) và dùng `.convert("L")` để chuyển ảnh về dạng **grayscale**.

* Dùng **`np.asarray()`** để **chuyển ảnh thành mảng numpy** – giúp dễ dàng thao tác và biến đổi ảnh trong các bước tiếp theo.

* **Hiển thị menu lựa chọn**, cho phép người dùng chọn:

  * **`1`**: *Áp dụng phép biến đổi ảnh ngẫu nhiên*
  * **`Q`**: *Thoát chương trình*

---

###  Khi người dùng chọn **1**, chương trình sẽ:

1. **Chọn ngẫu nhiên một phương pháp xử lý ảnh trong miền tần số**, gồm:

   * *Fast Fourier Transform*
   * *Butterworth Lowpass Filter*
   * *Butterworth Highpass Filter*

2. Gọi đúng hàm tương ứng:

   * **`fast_fourier_transform(img_array)`**
   * **`lowpass_filter(img_array, d0, n)`**
   * **`butterworth_highpass_filter(img_array, d0, n)`**

3. Với các bộ lọc Butterworth, chương trình sẽ **tự sinh ngẫu nhiên tham số**:

   * **`d0`**: Cut-off radius, ngẫu nhiên trong khoảng từ `20` đến `60`
   * **`n`**: Order of filter, ngẫu nhiên từ `1` đến `3`

4. Cuối cùng, gọi hàm **`show_results()`** để hiển thị **ảnh gốc** và **ảnh đã xử lý** song song.




