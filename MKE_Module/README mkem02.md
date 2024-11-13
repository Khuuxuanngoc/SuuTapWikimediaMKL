[[image:mkl-m02_push_button_tact_switch_module.jpg|thumb|396x396px|MKE-M02 push button tact switch module|link=Special:FilePath/mkl-m02_push_button_tact_switch_module.jpg|alt=MKL-M02 push button tact switch module]]
==Giới thiệu==
Mạch nút nhấn MKE-M02 push button tact switch module sử dụng nút nhấn kích thước lớn giúp dễ dàng lắp đặt, thao tác, nút nhấn sử dụng trong loại là loại nhấn nhả (tact switch) thường được dùng để kích tín hiệu, nút nhấn có nắp chụp với nhiều màu sắc khác nhau để dễ phân biệt.

Mạch nút nhấn MKE-M02 push button tact switch module thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.
==Thông số kỹ thuật==
* Loại nút nhấn: nhấn nhả (tact switch)
* Điện áp hoạt động: 5VDC
* Chuẩn giao tiếp: Digital
* Điện áp giao tiếp: TTL 3.3/5VDC
* Có 4 phiên bản màu sắc: Xanh Lá, Xanh Dương, Vàng, Đỏ.
* Sử dụng trực tiếp an toàn với các board mạch giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
* Bổ sung thêm các thiết kế ổn định, chống nhiễu.
* Chuẩn kết nối: connector XH2.54 3Pins
* Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
{{Tr-Done
|name=Lưu ý:
|value=Khi '''nhấn''' nút, chân '''SIG''' sẽ xuất ra '''''0V'''''. Khi '''nhả''' nút, chân '''SIG''' sẽ xuất ra '''''3V3''''' !
}}
{{kxnKichThuocFrame_A
|name=MKL-M02 push button tact switch module dimension
}}
==Các chân tín hiệu==
[[image:mkl-m02_push_button_tact_switch_module_back.jpg|thumb|316x316px|MKE-M02 push button tact switch module back|link=Special:FilePath/mkl-m02_push_button_tact_switch_module_back.jpg|alt=MKL-M02 push button tact switch module back]]
{| class="wikitable" border="1"
|-
! MKE-M02
! Ghi chú
|-
| GND
| Chân cấp nguồn âm 0VDC
|-
| 5V
| Chân cấp nguồn dương 5VDC
|-
| SIG
| Chân tín hiệu Digital Out
|}
{| class="wikitable" border="1"
|-
!SIG (Digital Out)
!Trạng thái
|-
|TTL HIGH
|Hoạt động (On)
|-
|TTL LOW
| Không hoạt động (Off)
|}
==Hướng dẫn sử dụng với phần mềm Arduino và Vietduino==

===Phần cứng cần chuẩn bị:===
*Mạch nút nhấn MKE-M02 push button tact switch module
* [[Mạch Vietduino Uno (Arduino Uno Compatible)]]
* [[Mạch MakerEdu Shield for Vietduino]]
* Cáp USB để nạp chương trình và cấp nguồn

{{Tr-Info
|name=Lưu ý:
|value=Nếu không có mạch Vietduino Uno bạn vẫn có thể sử dụng mạch Vietduino Mega 2560, Arduino Uno, Arduino Mega 2560 hoặc các mạch phần cứng có cấu trúc các chân GPIO tương tự.
}}

=== Phần mềm cần chuẩn bị: ===
* Tải và cài đặt phần mềm Arduino theo [[Cách cài đặt phần mềm Arduino IDE|hướng dẫn.]]
* Tải và cài đặt Driver, cấu hình cho mạch Vietduino Uno trên phần mềm Arduino theo [[Cách cài đặt Driver và nạp chương trình cho mạch Arduino / Arduino Compatible|hướng dẫn.]]
* Tải và cài đặt [https://github.com/makerlabvn/mke-m02-push-button-tact-switch-module-lib bộ thư viện nút nhấn] theo [[Cách cài đặt các thư viện phần cứng Arduino Library|hướng dẫn.]]

=== Chương trình mẫu: ===
<source lang="c++">
// Thêm bộ thư viện Nút nhấn.
// Add the Button library.
#include <OneButton.h>

// Chọn chân Digital cho Nút nhấn.
// Select the Digital pin for Button.
#define BUTTON_PIN 11

// Khởi tạo "OneButton" cho Nút nhấn với cấu hình sau.
// Initialize "OneButton" for the Button with the following config.
OneButton btn = OneButton(
    BUTTON_PIN, // Cấu hình đây là chân Digital Input.
    true,       // Nút nhấn kích hoạt LOW.
    false       // Kích hoạt điện trở nội "Pull-Up".
);

// Lưu số lần thực hiện 1 Click vào nút.
// Save the number of times make 1 Click on the Button.
int value = 0;

void setup()
{
  // Khởi động kết nối Serial UART ở tốc độ 9600 để truyền dữ liệu lên máy tính.
  // Start the Serial UART connection at 9600 to transfer data to the computer.
  Serial.begin(9600);

  // Liên kết hàm "count" được gọi trên một sự kiện 1 Click.
  // Link the "count" function to be called on a single click event.
  btn.attachClick(count);
}

void loop()
{
  // Tiếp tục theo dõi Nút nhấn.
  // Keep watching the Button.
  btn.tick();
}

void count()
{
  // Ghi lại đây là 1 Click.
  // Record this is 1 Click.
  value++;

  // Truyền giá trị lên máy tính.
  // Transmit the value to the computer.
  Serial.print("Count: ");
  Serial.println(value);
}
</source>

=== Sơ đồ kết nối: ===
{| class="wikitable"
!MakerEdu Shield for Vietduino
!Arduino / Vietduino
!Devices
|-
|Port D11
|D11
|Mạch nút nhấn MKE-M02 push button tact switch module
|}

=== Các bước tiến hành: ===
#Kết nối mạch Vietduino Uno với mạch MakerEDU Shield for Vietduino.
#Kết nối Mạch Nút Nhấn MKE-M02 với mạch MakerEDU Shied for Vietduino qua '''Port D11'''.
#Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port).
#Nạp chương trình mẫu vào mạch Vietduino Uno.
#Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.

=== Kết quả: ===
...pic

==Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator==
===Phần cứng cần chuẩn bị:===
* Mạch nút nhấn MKE-M02 push button tact switch module
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Creator]] 
* Cáp USB để nạp chương trình và cấp nguồn
===Phần mềm cần chuẩn bị:===
*Tải và cài đặt phần mềm mBlock theo [[Giới thiệu và hướng dẫn cài đặt phần mềm mBlock|hướng dẫn.]]
*Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn]].
*Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm mBlock|hướng dẫn.]]
===Chương trình mẫu:===

# Mỗi khi bạn nhấn "1 Click" trên nút nhấn, mạch MakerEdu Creator sẽ đếm và hiển thị số lần bạn nhấn nút lên màn hình LCD.

<u>'''Blocks'''</u>

[[File:MBlock M02.PNG|border|700x700px]]

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEdu Creator
!Devices
|-
|Port D11
|Mạch Nút Nhấn MKE-M02 Push Button Tact Switch Module
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}
===Các bước tiến hành:===
#Kết nối Mạch Nút Nhấn MKE-M02 với mạch MakerEdu Creator qua '''Port D11'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEdu Creator qua '''Port I2C'''.
#Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
#Nạp chương trình mẫu vào mạch MakerEdu Creator.
#Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.
===Kết quả:===
...pic

==Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bit==

===Phần cứng cần chuẩn bị:===

* [[Mạch nút nhấn MKE-M02 push button tact switch module]]
* [[Mạch MakerEdu Shield for Micro:bit]]
* [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|Mạch Micro:Bit]]
* Cáp USB để nạp chương trình và cấp nguồn

===Phần mềm cần chuẩn bị:===
*Khởi động phần mềm MakeCode theo [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|hướng dẫn]].
*Cài đặt Extension MakerEdu Hardware trên MadeCode và tham khảo các khối chức năng theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm MakeCode|hướng dẫn]].
*Tham khảo cách kết nối và nạp chương trình cho Micro:bit [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên máy tính với phần mềm MakeCode|trên máy tính]] hoặc [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên điện thoại, máy tính bảng với phần mềm MakeCode|điện thoại, máy tính bảng.]]

===Chương trình mẫu:===

# Trên bo mạch Micro:Bit có sẵn bảng mạch 25 LED để sử dụng.
# Trong chương trình này, mỗi khi nhấn nút Micro:bit sẽ lấy ngẫu nhiên một số từ 1 đến 6, và cho hiển thị mặt "xúc xắc" tương ứng lên 25 LED kia.

'''<u>Blocks</u>'''

[[File:MakeCode M02.png|border]]

'''<u>Javascript</u>'''

<source lang="typescript">
// Giá trị của "xúc xắc"
let random = 0

// Khi nhấn nút (P0) sẽ đổ "xúc xắc"
input.onPinPressed(TouchPin.P0, function () {
  basic.showLeds(`
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        . . . . .
        `)
  // Lấy một số ngẫu nhiên trong khoảng 1 đến 6
  random = randint(1, 6)

  // Cho hiển thị mặt "xúc xắc" theo số tương ứng
  if (random == 1) {
    basic.showLeds(`
            . . . . .
            . . . . .
            . . # . .
            . . . . .
            . . . . .
            `)
  } else if (random == 2) {
    basic.showLeds(`
            . . # . .
            . . . . .
            . . . . .
            . . . . .
            . . # . .
            `)
  } else if (random == 3) {
    basic.showLeds(`
            . . . . #
            . . . . .
            . . # . .
            . . . . .
            # . . . .
            `)
  } else if (random == 4) {
    basic.showLeds(`
            # . . . #
            . . . . .
            . . . . .
            . . . . .
            # . . . #
            `)
  } else if (random == 5) {
    basic.showLeds(`
            # . . . #
            . . . . .
            . . # . .
            . . . . .
            # . . . #
            `)
  } else if (random == 6) {
    basic.showLeds(`
            # . . . #
            . . . . .
            # . . . #
            . . . . .
            # . . . #
            `)
  }
})
</source>

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEDU Shield for Micro:bit
!Devices
|-
|Port P0
|Mạch Nút Nhấn MKE-M02 Push Button Tact Switch Module
|}

===Các bước tiến hành:===
#Kết nối Mạch Nút Nhấn MKE-M02 với mạch MakerEDU Shield For Micro:Bit qua '''Port P0'''.
#Gắn bo Micro:Bit lên mạch MakerEDU Shield.
# Kết nối Micro:bit với mạch MakerEdu Shield for Micro:bit
# Nạp chương trình mẫu vào mạch Micro:Bit.
# Nhấn nút Reset trên mạch Micro:Bit để bắt đầu chạy chương trình.

===Kết quả:===
...pic

==Nhà phân phối==
Có thể mua Mạch nút nhấn MKE-M02 push button tact switch module tại các nhà phân phối sau:
* [https://hshop.vn/products/mach-nut-nhan-mkl-m02-push-button-tact-switch-module Hshop.vn - Điện tử & Robot.]
[[Category:Modules]]
