[[image:mkl-m01_10mm_single_led_module1.jpg|thumb|400x400px|MKE-M01 10mm single led module|link=Special:FilePath/mkl-m01_10mm_single_led_module1.jpg|alt=MKL-M01 10mm single led module]]
==Giới thiệu==
Mạch led đơn MKE-M01 10mm single LED module sử dụng loại LED kích thước lớn 10mm giúp bạn dễ dàng ứng dụng trong các mô hình xe, trang trí,..., mạch gồm có 4 phiên bản với các màu sắc: Trắng, Xanh lá, Vàng, Đỏ.

Mạch led đơn MKE-M01 10mm single LED module thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.
==Thông số kỹ thuật==
*Điện áp hoạt động: 5VDC
*Chuẩn giao tiếp: Digital
*Điện áp giao tiếp: TTL 3.3VDC/5VDC
*Có 4 phiên bản màu sắc: Trắng , Xanh Lá, Vàng, Đỏ.
*Sử dụng LED kích thước 10mm.
* Tích hợp Transistor giúp giảm dòng tiêu thụ và bảo vệ các chân GPIO của mạch xử lý.
* Sử dụng trực tiếp an toàn với các board mạch giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
* Bổ sung thêm các thiết kế ổn định, chống nhiễu.
* Chuẩn kết nối: connector XH2.54 3Pins
* Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
{{kxnKichThuocFrame_A
|name=MKL-M01 10mm single LED module dimension
}}
==Các chân tín hiệu==
[[image:mkl-m01_10mm_single_led_module_back.jpg|thumb|400x400px|MKE-M01 10mm single led module back|link=Special:FilePath/mkl-m01_10mm_single_led_module_back.jpg|alt=MKL-M01 10mm single led module back]]
{| class="wikitable" border="1"
|-
!MKE-M01
!Ghi chú
|-
|GND
|Chân cấp nguồn âm 0VDC
|-
|5V
| Chân cấp nguồn dương 5VDC
|-
|SIG
|Chân tín hiệu Digital In
|}
{| class="wikitable" border="1"
|-
!SIG (Digital In)
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
*Mạch led đơn MKE-M01 10mm single LED module
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

=== Chương trình mẫu: ===
<source lang="c++">
// Chọn chân Digital điều khiển LED.
// Select the Digital pin to control LED.
#define LED_PIN 10

void setup()
{
  // Cấu hình đây là chân Digital Output.
  // Config this is Digital Output.
  pinMode(LED_PIN, OUTPUT);

  // Đảm bảo tắt LED khi mới khởi động.
  // Make sure to turn off the LED when starting.
  digitalWrite(LED_PIN, LOW);
}

void loop()
{
  // Bật LED trong 1s.
  // Turn on LED for 1 seconds.
  digitalWrite(LED_PIN, HIGH);
  delay(1000);

  // Tắt LED trong 1s.
  // Turn off LED for 1 seconds.
  digitalWrite(LED_PIN, LOW);
  delay(1000);
}
</source>

=== Sơ đồ kết nối: ===
{| class="wikitable"
!MakerEdu Shield for Vietduino
!Arduino / Vietduino
!Devices
|-
|Port D10
|D10
|Mạch led đơn MKE-M01 10mm single LED module
|}

=== Các bước tiến hành: ===
#Kết nối mạch Vietduino Uno với mạch MakerEDU Shield for Vietduino.
#Kết nối Mạch Led Đơn MKE-M01 với mạch MakerEDU Shied for Vietduino qua '''Port D10'''.
#Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port).
#Nạp chương trình mẫu vào mạch Vietduino Uno.
#Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.

=== Kết quả: ===
...pic

==Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator==
===Phần cứng cần chuẩn bị:===
* [[Mạch led đơn MKE-M01 10mm single LED module]]
* [[Mạch MakerEdu Creator]] 
* Cáp USB để nạp chương trình và cấp nguồn
===Phần mềm cần chuẩn bị:===
*Tải và cài đặt phần mềm mBlock theo [[Giới thiệu và hướng dẫn cài đặt phần mềm mBlock|hướng dẫn.]]
*Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn]].
*Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm mBlock|hướng dẫn.]]
===Chương trình mẫu:===

# Mạch MakerEdu Creator điều khiển LED bật 1s và tắt 1s liên tục, tạo hiệu ứng "Blink LED".

<u>'''Blocks'''</u>

[[File:MBlock M01.PNG|border|474x474px]]

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEdu Creator
!Devices
|-
|Port D10
|Mạch Led Đơn MKE-M01 10mm Single LED Module
|}
===Các bước tiến hành:===
#Kết nối Mạch Led Đơn MKE-M01 với mạch MakerEdu Creator qua '''Port D10'''.
#Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
#Nạp chương trình mẫu vào mạch MakerEdu Creator.
#Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.
===Kết quả:===
...pic

==Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bit==

===Phần cứng cần chuẩn bị:===

* Mạch led đơn MKE-M01 10mm single LED module
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Shield for Micro:bit]]
* [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|Mạch Micro:Bit]]
* Cáp USB để nạp chương trình và cấp nguồn

===Phần mềm cần chuẩn bị:===
*Khởi động phần mềm MakeCode theo [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|hướng dẫn]].
*Cài đặt Extension MakerEdu Hardware trên MadeCode và tham khảo các khối chức năng theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm MakeCode|hướng dẫn]].
*Tham khảo cách kết nối và nạp chương trình cho Micro:bit [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên máy tính với phần mềm MakeCode|trên máy tính]] hoặc [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên điện thoại, máy tính bảng với phần mềm MakeCode|điện thoại, máy tính bảng.]]

===Chương trình mẫu:===

# Trên mạch Micro:Bit có sẵn 2 nút nhấn A và B cho bạn sử dụng.
# Trong chương trình này, khi nhấn nút A sẽ bật LED, nhấn nút B để tắt LED.
# Còn khi nhấn cả 2 nút A và B cùng lúc, sẽ làm "chớp tắt" LED với chu kỳ 0,5s.
# Micro:bit có gửi thông tin thao tác nút lên màn hình LCD để bạn theo dõi.

'''<u>Blocks</u> [ on start ]'''

[[File:MakeCode M01 1.PNG|border]]

'''<u>Blocks</u> [ forever ]'''

[[File:MakeCode M01 2.PNG|border]]

'''<u>Blocks</u> [ on button pressed ]'''

[[File:MakeCode M01 3.PNG|border]]

'''<u>Javascript</u>'''

<source lang="typescript">
// Cho biết trạng thái hoạt động hiện tại của LED
let statusLED = 0
// Cho biết chế độ hoạt động của LED là "bình thường" hay "chớp tắt"
let blink = 0

// Xóa toàn bộ nội dung trên LCD (nếu có)
lcd.clearScreen()
// Cho hiển thị tiêu đề trên LCD và tắt LED
lcd.displayText("LED: OFF", 1, 1)
pins.digitalWritePin(DigitalPin.P0, 0)

// Khi nhấn nút A, chỉ bật LED
input.onButtonPressed(Button.A, function () {
  lcd.displayText("ON   ", 6, 1)
  blink = 0
  statusLED = 1
})

// Khi nhấn nút B, chỉ tắt LED
input.onButtonPressed(Button.B, function () {
  lcd.displayText("OFF  ", 6, 1)
  blink = 0
  statusLED = 0
})

// Khi nhấn cùng lúc cả nút A+B, cho chớp tắt LED
input.onButtonPressed(Button.AB, function () {
  lcd.displayText("Blink", 6, 1)
  blink = 1
})

// Kiểm tra liên tục chế độ của LED để điều khiển
basic.forever(function () {
  if (blink == 1) {
    pins.digitalWritePin(DigitalPin.P0, 1)
    basic.pause(250)
    pins.digitalWritePin(DigitalPin.P0, 0)
    basic.pause(250)
  } else {
    if (statusLED == 1) {
      pins.digitalWritePin(DigitalPin.P0, 1)
    } else {
      pins.digitalWritePin(DigitalPin.P0, 0)
    }
  }
})
</source>

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEDU Shield for Micro:bit
!Devices
|-
|Port P0
|Mạch Led Đơn MKE-M01 10mm Single LED Module
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}

===Các bước tiến hành:===
#Kết nối Mạch Led Đơn MKE-M01 với mạch MakerEDU Shield For Micro:Bit qua '''Port P0'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEDU Shield For Micro:Bit qua '''Port I2C'''.
# Kết nối Micro:bit với mạch MakerEdu Shield for Micro:bit
# Nạp chương trình mẫu vào mạch Micro:Bit.
# Nhấn nút Reset trên mạch Micro:Bit để bắt đầu chạy chương trình.

===Kết quả:===
...pic

==Nhà phân phối==
Có thể mua Mạch led đơn MKE-M01 10mm single LED module tại các nhà phân phối sau:
* [https://hshop.vn/products/mach-led-don-mkl-m01-10mm-single-led-module Hshop.vn - Điện tử & Robot.]
[[Category:Modules]]
