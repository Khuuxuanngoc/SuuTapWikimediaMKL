[[image:mkl-m03_buzzer_module.jpg|thumb|400x400px|MKE-M03 buzzer module|link=Special:FilePath/mkl-m03_buzzer_module.jpg|alt=MKL-M03 buzzer module]]
==Giới thiệu==
Mạch còi báo MKE-M03 buzzer module được sử dụng để tạo ra các âm thanh báo hiệu trong các ứng dụng chống trộm, hồi tiếp, phản hồi bằng âm thanh.

Mạch còi báo MKE-M03 buzzer module thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.
==Thông số kỹ thuật==
* Điện áp hoạt động: 5VDC
*Chuẩn giao tiếp: Digital
*Điện áp giao tiếp: TTL 3.3VDC/5VDC
*Sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
*Bổ sung thêm các thiết kế ổn định, chống nhiễu.
*Chuẩn kết nối: connector XH2.54 3Pins
*Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
{{kxnKichThuocFrame_A
|name=MKL-M03 buzzer module dimension
}}
==Các chân tín hiệu==
[[image:mkl-m03_buzzer_module_back.jpg|thumb|400x400px|MKE-M03 buzzer module back|link=Special:FilePath/mkl-m03_buzzer_module_back.jpg|alt=MKL-M03 buzzer module back]]
{| class="wikitable" border="1"
|-
!MKE-M03
!Ghi chú
|-
|GND
|Chân cấp nguồn âm 0VDC
|-
| 5V
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
*Mạch còi báo MKE-M03 buzzer module
*[[Mạch Vietduino Uno (Arduino Uno Compatible)]]
*[[Mạch MakerEdu Shield for Vietduino]]
*Cáp USB để nạp chương trình và cấp nguồn

{{Tr-Info
|name=Lưu ý:
|value=Nếu không có mạch Vietduino Uno bạn vẫn có thể sử dụng mạch Vietduino Mega 2560, Arduino Uno, Arduino Mega 2560 hoặc các mạch phần cứng có cấu trúc các chân GPIO tương tự.
}}

=== Phần mềm cần chuẩn bị: ===
* Tải và cài đặt phần mềm Arduino theo [[Cách cài đặt phần mềm Arduino IDE|hướng dẫn.]]
* Tải và cài đặt Driver, cấu hình cho mạch Vietduino Uno trên phần mềm Arduino theo [[Cách cài đặt Driver và nạp chương trình cho mạch Arduino / Arduino Compatible|hướng dẫn.]]

=== Chương trình mẫu: ===
<source lang="c++">
// Chọn chân Digital điều khiển Còi.
// Select the Digital pin to control Buzzer.
#define BUZ_PIN 10

void setup()
{
  // Cấu hình đây là chân Digital Output.
  // Config this is Digital Output.
  pinMode(BUZ_PIN, OUTPUT);

  // Đảm bảo tắt Còi khi mới khởi động.
  // Make sure to turn off the Buzzer when starting.
  digitalWrite(BUZ_PIN, LOW);
}

void loop()
{
  // Bật Còi trong 0,5s.
  // Turn on Buzzer for 0,5 seconds.
  digitalWrite(BUZ_PIN, HIGH);
  delay(500);

  // Tắt Còi trong 0,5s.
  // Turn off Buzzer for 0,5 seconds.
  digitalWrite(BUZ_PIN, LOW);
  delay(500);
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
|Mạch còi báo MKE-M03 buzzer module
|}

=== Các bước tiến hành: ===
#Kết nối mạch Vietduino Uno với mạch MakerEDU Shield for Vietduino.
#Kết nối Mạch Còi Báo MKE-M03 với mạch MakerEDU Shied for Vietduino qua '''Port D10'''.
#Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port).
#Nạp chương trình mẫu vào mạch Vietduino Uno.
#Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.

=== Kết quả: ===
...pic

==Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator==
===Phần cứng cần chuẩn bị:===
* Mạch còi báo MKE-M03 buzzer module
* [[Mạch MakerEdu Creator]] 
* Cáp USB để nạp chương trình và cấp nguồn
===Phần mềm cần chuẩn bị:===
*Tải và cài đặt phần mềm mBlock theo [[Giới thiệu và hướng dẫn cài đặt phần mềm mBlock|hướng dẫn.]]
*Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn]].
*Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm mBlock|hướng dẫn.]]
===Chương trình mẫu:===

# Mạch MakerEdu Creator điều khiển Còi bật tắt liên tục với chu kỳ 1s.

<u>'''Blocks'''</u>

[[File:MBlock M03.PNG|border|474x474px]]

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEdu Creator
!Devices
|-
|Port D10
|Mạch Còi Báo MKE-M03 Buzzer Module
|}
===Các bước tiến hành:===
#Kết nối Mạch Còi Báo MKE-M03 với mạch MakerEdu Creator qua '''Port D10'''.
#Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
#Nạp chương trình mẫu vào mạch MakerEdu Creator.
#Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.
===Kết quả:===
...pic

==Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bitPhần cứng cần chuẩn bị:==

* Mạch còi báo MKE-M03 buzzer module
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
# Trong chương trình này, khi nhấn nút A còi được phép bật, nhấn nút B để tắt còi.
# Khi còi được phép bật, nó sẽ bật tắt liên tục với chu kỳ 1s để tạo âm thanh tick...tick...
# Micro:bit có gửi thông tin thao tác nút lên màn hình LCD để bạn theo dõi.
# Micro:Bit cũng gửi giá trị đó qua cổng Serial, bạn có thể mở mục "Show Data (Device)" để xem trên máy tính.

'''<u>Blocks</u> [ on start ]'''

[[File:MakeCode M03 1.PNG|border]]

'''<u>Blocks</u> [ every (ms) ]'''

[[File:MakeCode M03 2.PNG|border]]

'''<u>Blocks</u> [ on button pressed ]'''

[[File:MakeCode M03 3.PNG|border]]

'''<u>Javascript</u>'''

<source lang="typescript">
// Cho biết trạng thái hoạt động hiện tại của còi
let statusBuzz = 0
// Cho biết chế độ còi đang bật hay tắt
let modeBuzz = 0

// Xóa toàn bộ nội dung trên LCD (nếu có)
lcd.clearScreen()
// Cho hiển thị tiêu đề trên LCD và tắt còi
lcd.displayText("Buzzer: OFF", 1, 1)
pins.digitalWritePin(DigitalPin.P0, 0)

// Khi nhấn nút A, còi được phép bật
input.onButtonPressed(Button.A, function () {
  modeBuzz = 1
  lcd.displayText("ON ", 9, 1)
})

// Khi nhấn nút B, còi bị tắt
input.onButtonPressed(Button.B, function () {
  modeBuzz = 0
  lcd.displayText("OFF", 9, 1)
})

// Mỗi 0.5s sẽ đảo trạng thái còi, nếu còi được bật
loops.everyInterval(500, function () {
  if (modeBuzz == 1) {
    if (statusBuzz == 0) {
      statusBuzz = 1
    } else {
      statusBuzz = 0
    }
    pins.digitalWritePin(DigitalPin.P0, statusBuzz)
  } else {
    pins.digitalWritePin(DigitalPin.P0, 0)
  }
})
</source>

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEDU Shield for Micro:bit
!Devices
|-
|Port P0
|Mạch Còi Báo MKE-M03 Buzzer Module
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}

===Các bước tiến hành:===
#Kết nối Mạch Còi Báo MKE-M03 với mạch MakerEDU Shield For Micro:Bit qua '''Port P0'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEDU Shield For Micro:Bit qua '''Port I2C'''.
# Kết nối Micro:bit với mạch MakerEdu Shield for Micro:bit
# Nạp chương trình mẫu vào mạch Micro:Bit.
# Nhấn nút Reset trên mạch Micro:Bit để bắt đầu chạy chương trình.

===Kết quả:===
...pic

==Nhà phân phối==
Có thể mua Mạch còi báo MKE-M03 buzzer module tại các nhà phân phối sau:
* [https://hshop.vn/products/mach-coi-bao-mkl-m03-buzzer-module Hshop.vn - Điện tử & Robot.]
[[Category:Modules]]
