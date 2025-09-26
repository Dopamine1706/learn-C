---

## 1. Bảng Ký hiệu Chuyển đổi Cơ bản (Conversion Specifiers)

| Ký hiệu | Kiểu dữ liệu | Mô tả | Ví dụ `printf` |
| :--- | :--- | :--- | :--- |
| **`%c`** | `char` | Một ký tự đơn. | `printf("%c", 'A');` |
| **`%s`** | `char*` | Một chuỗi ký tự (kết thúc bằng null). | `printf("%s", "Hello");` |
| **`%d`** hoặc **`%i`** | `int` | Số nguyên thập phân (có dấu). | `printf("%d", 123);` |
| **`%u`** | `unsigned int` | Số nguyên không dấu thập phân. | `printf("%u", 40000U);` |
| **`%o`** | `int` | Số nguyên hệ bát phân (Octal). | `printf("%o", 8);` |
| **`%x`** | `int` | Số nguyên hệ thập lục phân (Hexadecimal), dùng chữ thường. | `printf("%x", 255);` |
| **`%X`** | `int` | Số nguyên hệ thập lục phân, dùng chữ hoa. | `printf("%X", 255);` |
| **`%f`** | `double` | Số thực dấu phẩy động (dạng thập phân). **Lưu ý: Dùng `%f` cho cả `float` và `double` trong `printf`**. | `printf("%f", 3.14);` |
| **`%e`** hoặc **`%E`** | `double` | Số thực dấu phẩy động, dạng khoa học. | `printf("%e", 12.3);` |
| **`%g`** hoặc **`%G`** | `double` | Chọn dạng ngắn hơn giữa `%f` và `%e`. | |
| **`%p`** | `void*` | Địa chỉ bộ nhớ (con trỏ). | `printf("%p", &var);` |
| **`%%`** | (Không có) | In ra ký tự dấu phần trăm (`%`). | `printf("100%%");` |

---

## 2. Bảng Ký hiệu Thay đổi Chiều dài (Length Modifiers)

| Ký hiệu | Ký hiệu Chuyển đổi (ví dụ) | Kiểu dữ liệu tương ứng | Mô tả |
| :--- | :--- | :--- | :--- |
| **`l`** (chữ L thường) | `%ld`, `%lu` | `long int`, `unsigned long int` | Dùng cho `long` integers. |
| **`ll`** | `%lld`, `%llu` | `long long int`, `unsigned long long int` | Dùng cho `long long` integers (từ C99). |
| **`h`** | `%hd`, `%hu` | `short int`, `unsigned short int` | Dùng cho `short` integers. |
| **`L`** (chữ L hoa) | `%Lf`, `%Le`, `%Lg` | **`long double`** | Dùng cho kiểu `long double`. |
| **`z`** | `%zd`, `%zu` | `size_t` | Dùng cho kiểu `size_t` (thường là kích thước mảng/đối tượng). |

---

## 3. Bảng Cờ Định dạng (Flags)

Các cờ được đặt ngay sau dấu `%` và trước độ rộng.

| Cờ | Mô tả | Ví dụ | Kết quả |
| :--- | :--- | :--- | :--- |
| **`-`** | Căn trái giá trị (mặc định là căn phải). | `printf("|%-5d|", 10);` | `|10   |` |
| **`+`** | Luôn hiển thị dấu (`+` hoặc `-`) cho các số có dấu. | `printf("%+d", 10);` | `+10` |
| **`(khoảng trắng)`** | Nếu số không âm, hiển thị một khoảng trắng thay vì dấu `+`. | `printf("% d", 10);` | ` 10` |
| **`#`** | Dùng cho các dạng thay thế: thêm `0x` cho hệ 16 (`%x`), `0` cho hệ 8 (`%o`). | `printf("%#x", 10);` | `0xa` |
| **`0`** | Đệm bằng số 0 thay vì khoảng trắng, khi sử dụng độ rộng. | `printf("%05d", 10);` | `00010` |

---

## Tóm tắt Định dạng `scanf` (Đọc Dữ liệu)

Đây là các ký hiệu quan trọng nhất cho hàm `scanf`. **Lưu ý: Chúng khác với `printf`!**

| Ký hiệu `scanf` | Kiểu dữ liệu tương ứng | Mô tả |
| :--- | :--- | :--- |
| **`%f`** | `float` | Đọc giá trị kiểu `float`. |
| **`%lf`** | `double` | **Phải dùng** để đọc giá trị kiểu `double`. |
| **`%Lf`** | `long double` | Đọc giá trị kiểu `long double`. |
| **`%s`** | `char*` | Đọc chuỗi ký tự (dừng khi gặp khoảng trắng). |
| **`%d`**, **`%ld`**, **`%lld`** | `int`, `long`, `long long` | Đọc các kiểu số nguyên tương ứng. |
### B. Độ Rộng (Width)

Chỉ định số ký tự tối thiểu sẽ được in.

| Ví dụ | Mô tả |
| :--- | :--- |
| **`%5d`** | Độ rộng tối thiểu 5 ký tự (căn phải). |
| **`%-10s`** | Độ rộng tối thiểu 10 ký tự (căn trái). |

### C. Độ Chính xác (Precision)

Ý nghĩa khác nhau tùy thuộc vào kiểu dữ liệu:

| Kiểu | Ví dụ | Mô tả |
| :--- | :--- | :--- |
| **Số thực (`%f`)** | **`%.3f`** | Số lượng chữ số sau dấu thập phân (ví dụ: 3). |
| **Số nguyên (`%d`)** | **`%.5d`** | Số lượng chữ số tối thiểu (đệm bằng số 0 ở đầu). |
| **Chuỗi (`%s`)** | **`%.5s`** | Số lượng ký tự tối đa sẽ được in ra từ chuỗi. |


