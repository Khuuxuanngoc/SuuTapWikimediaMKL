[[image:mkl-m08_lcd2004_i2c_module.jpg|thumb|400x400px|MKE-M08 LCD2004 I2C module|link=Special:FilePath/mkl-m08_lcd2004_i2c_module.jpg|alt=MKL-M08 LCD2004 I2C module]]
==Giới thiệu==
Mạch hiển thị MKE-M08 LCD2004 I2C module được sử dụng để hiển thị thông tin dưới dạng ký tự với khả năng hiển thị 4 dòng, mỗi dòng 20 ký tự, mạch được tích hợp sẵn bộ chuyển đổi giao tiếp I2C cho LCD nên có thể dễ dàng kết nối và sử dụng với chỉ 2 chân giao tiếp I2C là SDA (data) và SCL (clock).

Mạch hiển thị MKE-M08 LCD2004 I2C module thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.
==Thông số kỹ thuật==
* Điện áp hoạt động: 5VDC
*Chuẩn giao tiếp: Digital I2C
* Các chân giao tiếp: SDA (Serial Data) / SCL (Serial Clock)
*Điện áp giao tiếp: TTL 3.3/5VDC
*Loại LCD: LCD2004 (4 dòng, mỗi dòng 20 ký tự), [https://www.mediafire.com/file/uu94qlpjyaik0wq/%255BMakerLab.vn%255D_LCD2004_Datasheet.pdf/file datasheet.]
*IC chuyển giao tiếp LCD sang I2C: PCF8574T, [https://www.mediafire.com/file/trz2qjkn45epry9/&#x5B;MakerLab.vn&#x5D;+PCF8574_PCF8574A+datasheet.pdf/file datasheet.]
* Sử dụng trực tiếp an toàn với các board mạch giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
* Bổ sung thêm các thiết kế ổn định, chống nhiễu.
* Chuẩn kết nối: Conector XH2.54 4Pins
* Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
==Kích thước==
[[File:Module_MKL_M08_LCD2004.JPG|alt=MKL-M08 LCD2004 I2C module dimension|none|thumb|400x400px|MKE-M08 LCD2004 I2C module dimension]]
==Các chân tín hiệu ==
[[image:mkl-m08_lcd2004_i2c_module_back.jpg|thumb|400x400px|MKE-M08 LCD2004 I2C module back|link=Special:FilePath/mkl-m08_lcd2004_i2c_module_back.jpg|alt=MKL-M08 LCD2004 I2C module back]]
{| class="wikitable" border="1"
|-
!MKE-M08
! Ghi chú
|-
|GND
|Chân cấp nguồn âm 0VDC
|-
|5V
|Chân cấp nguồn dương 5VDC
|-
|SDA
| Chân tín hiệu I2C Serial Data
|-
|SCL
|Chân tín hiệu I2C Serial Clock
|-
|A0, A1, A2
|Chân thiết lập địa chỉ I2C
|-
|CONTRAST
|Biến trở chỉnh độ tương phản của màn hình
|}
==Hướng dẫn sử dụng với phần mềm Arduino và Vietduino==

===Phần cứng cần chuẩn bị:===
*[[Mạch hiển thị MKE-M08 LCD2004 I2C module]]
*[[Mạch Vietduino Uno (Arduino Uno Compatible)]]
* [[Mạch MakerEdu Shield for Vietduino]]
*Cáp USB để nạp chương trình và cấp nguồn

{{Tr-Info
|name=Lưu ý:
|value=Nếu không có mạch Vietduino Uno bạn vẫn có thể sử dụng mạch Vietduino Mega 2560, Arduino Uno, Arduino Mega 2560 hoặc các mạch phần cứng có cấu trúc các chân GPIO tương tự.
}}

=== Phần mềm cần chuẩn bị: ===
* Tải và cài đặt phần mềm Arduino theo [[Cách cài đặt phần mềm Arduino IDE|hướng dẫn.]]
* Tải và cài đặt Driver, cấu hình cho mạch Vietduino Uno trên phần mềm Arduino theo [[Cách cài đặt Driver và nạp chương trình cho mạch Arduino / Arduino Compatible|hướng dẫn.]]
* Tải và cài đặt [https://github.com/makerlabvn/mke-m0708-LCD-I2C-module-lib bộ thư viện LCD] theo [[Cách cài đặt các thư viện phần cứng Arduino Library|hướng dẫn.]]

=== Chương trình mẫu: ===
<source lang="c++">
// Thêm bộ thư viện LCD.
// Add the LCD library.
#include <LiquidCrystal_I2C.h>

// Khởi tạo "LiquidCrystal_I2C" cho màn hình LCD với cấu hình sau.
// Initialize "LiquidCrystal_I2C" for the monitor LCD with the following config.
LiquidCrystal_I2C lcd(
    0x27, // Cài đặt địa chỉ I2C là 0x27.
    20,   // With 20 columns.
    4     // With 4 rows.
);

// Lưu số đếm.
// Save the count.
int count = 0;

void setup()
{
  // Khởi động thư viện.
  // Start up the library.
  lcd.init();

  // Xóa màn hình, đảm bảo không còn nội dung cũ trước đó.
  // Clear the screen, making sure there is no old content left before.
  lcd.clear();

  // Bật đèn nền màn hình.
  // Turn on the screen backlight.
  lcd.backlight();

  // Tại vị trí cột 1 dòng 2, cho in nội dung...
  // At column 1, row 2, print the content...
  lcd.setCursor(0, 1);
  lcd.print("     LCD2004 I2C    ");

  // Tại vị trí cột 1 dòng 3, cho in nội dung...
  // At column 1, row 3, print the content...
  lcd.setCursor(0, 2);
  lcd.print("     MakerLab.vn    ");

  // Chờ 5s.
  // Wait 5s.
  delay(5000);

  // Xóa màn hình.
  // Clear the screen.
  lcd.clear();

  // Tại vị trí cột 1 dòng 1, cho in nội dung...
  // At column 1, row 1, print the content...
  lcd.setCursor(0, 0);
  lcd.print("Count:");
}

void loop()
{
  // Tăng số đếm lên 1 đơn vị.
  // Increase the count by 1 unit.
  count++;

  // Tại vị trí cột 8 dòng 1, cho in nội dung...
  // At column 8, row 1, print the content...
  lcd.setCursor(7, 0);
  lcd.print(count);

  // Đợi 1s để đếm tiếp.
  // Wait for 1s to count continue.
  delay(1000);
}
</source>

=== Sơ đồ kết nối: ===
{| class="wikitable"
!MakerEdu Shield for Vietduino
! style="text-align:left;" |Arduino/Vietduino
!Devices
|-
|Port I2C
|SDA / SCL
|Mạch Hiển Thị MKE-M08 LCD2004 I2C module
|}

=== Các bước tiến hành: ===
#Kết nối mạch Vietduino Uno với mạch MakerEDU Shield for Vietduino.
#Kết nối Mạch Hiển Thị MKE-M08 với mạch MakerEDU Shied for Vietduino qua '''Port I2C'''.
#Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port).
#Nạp chương trình mẫu vào mạch Vietduino Uno.
#Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.

=== Kết quả: ===
...pic

==Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator==
===Phần cứng cần chuẩn bị:===
* Mạch hiển thị MKE-M08 LCD2004 I2C module
* [[Mạch MakerEdu Creator]] 
* Cáp USB để nạp chương trình và cấp nguồn
===Phần mềm cần chuẩn bị:===
*Tải và cài đặt phần mềm mBlock theo [[Giới thiệu và hướng dẫn cài đặt phần mềm mBlock|hướng dẫn.]]
*Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn]].
*Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm mBlock|hướng dẫn.]]
===Chương trình mẫu:===

# Mạch MakerEdu Creator hiển thị một số thông tin lên màn hình LCD khoảng 5s.
# Rồi bắt đầu cho chạy đếm số tăng dần cũng hiển thị trên LCD.

<u>'''Blocks'''</u>

[[File:MBlock M08.PNG|border|700x700px]]

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEdu Creator
!Devices
|-
|Port I2C
|Mạch Hiển Thị MKE-M08 LCD2004 I2C Module
|}
===Các bước tiến hành:===
#Kết nối Mạch Hiển Thị MKE-M08 với mạch MakerEdu Creator qua '''Port I2C'''.
#Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
#Nạp chương trình mẫu vào mạch MakerEdu Creator.
#Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.
===Kết quả:===
...pic

==Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bit==

===Phần cứng cần chuẩn bị:===

* [[Mạch hiển thị MKE-M08 LCD2004 I2C module]]
* [[Mạch MakerEdu Shield for Micro:bit]]
* [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|Mạch Micro:Bit]]
* Cáp USB để nạp chương trình và cấp nguồn

===Phần mềm cần chuẩn bị:===
*Khởi động phần mềm MakeCode theo [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|hướng dẫn]].
*Cài đặt Extension MakerEdu Hardware trên MadeCode và tham khảo các khối chức năng theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm MakeCode|hướng dẫn]].
*Tham khảo cách kết nối và nạp chương trình cho Micro:bit [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên máy tính với phần mềm MakeCode|trên máy tính]] hoặc [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên điện thoại, máy tính bảng với phần mềm MakeCode|điện thoại, máy tính bảng.]]

===Chương trình mẫu:===

# Micro:Bit hiển thị một số thông tin lên màn hình LCD khoảng 5s.
# Rồi bắt đầu cho chạy đếm số tăng dần cũng hiển thị trên LCD.

<u>'''Blocks'''</u>

[[File:MakeCode_M08.png|border|frameless|1000x1000px]]

'''<u>Javascript</u>'''

<source lang="typescript">
// Xóa toàn bộ nội dung trên LCD (nếu có)
lcd.clearScreen()

// Cho hiển thị nội dung sau trên LCD
lcd.displayText("     LCD2004 I2C    ", 1, 2)
lcd.displayText("     MakerLab.vn    ", 1, 3)

// Dừng 5s để hiển thị, rồi xóa toàn bộ nội dung
basic.pause(5000)
lcd.clearScreen()

// Cho hiển thị tiêu đề "Đếm"
lcd.displayText("Count:", 1, 1)
// Tạo 1 biến lưu số đếm, bắt đầu từ số 0
let count = 0

basic.forever(function () {
  // Tăng giá trị số đếm lên 1 đơn vị
  count += 1
  // Hiển thị giá trị đó trên LCD sau tiêu đề "Đếm"
  lcd.displayText(convertToText(count), 8, 1)

  // Dừng 0.5s
  basic.pause(500)
})
</source>

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEDU Shield for Micro:bit
!Devices
|-
|Port I2C
|Mạch Hiển Thị MKE-M08 LCD2004 I2C Module
|}

===Các bước tiến hành:===
#Kết nối Mạch Hiển Thị MKE-M08 với mạch MakerEDU Shield For Micro:Bit qua '''Port I2C'''.
#Kết nối Micro:bit với mạch MakerEdu Shield for Micro:bit
#Nạp chương trình mẫu vào mạch Micro:Bit.
# Nhấn nút Reset trên mạch Micro:Bit để bắt đầu chạy chương trình.

===Kết quả:===
...pic

==Nhà phân phối==
Có thể mua Mạch hiển thị MKE-M08 LCD2004 I2C module tại các nhà phân phối sau:
* [https://hshop.vn/products/mach-hien-thi-mkl-m08-lcd2004-i2c-module Hshop.vn - Điện tử & Robot.]
[[Category:Modules]]
