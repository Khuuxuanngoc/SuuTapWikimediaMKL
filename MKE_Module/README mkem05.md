[[image:mkl-m05_optocoupler_relay_module.jpg|thumb|400x400px|MKE-M05 optocoupler relay module|link=Special:FilePath/mkl-m05_optocoupler_relay_module.jpg|alt=MKL-M05 optocoupler relay module]]
==Giới thiệu==
Mạch đóng ngắt tải MKE-M05 optocoupler relay module được sử dụng như một dạng công tắc 3 cực với ba tiếp điểm thường đóng (NC), thường mở (NO) và chân chung (COM) được điều khiển bằng tín hiệu từ mạch xử lý, mạch có thể đóng ngắt dòng điện, tín hiệu điện một chiều (DC) và xoay chiều (AC), mạch được thiết kế chống nhiễu và bảo vệ an toàn với Transistor, Diode và Opto cách ly.

Mạch đóng ngắt tải MKE-M05 optocoupler relay module thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.
==Nguyên lý hoạt động==
Relay hoạt động như một công tắc 3 cực có thể được sử dụng để đóng ngắt nguồn hoặc tín hiệu điện AC/DC, hoạt động đóng ngắt của Relay được điều khiển bởi chân tín hiệu của mạch xử lý, các chân tiếp điểm của Relay:
* NC: là viết tắt của chân tiếp điểm thường đóng (Normally Close), chân này sẽ luôn nối với chân chung (COM) khi chưa có tín hiệu kích của mạch xử lý hoặc khi Relay chưa hoạt động, khi có tín hiệu kích từ mạch xử lý thì chân (COM) sẽ ngắt kết nối với chân (NC) và chuyển sang nối với chân (NO).
* NO: là viết tắt của chân tiếp điểm thường mở (Normally Open), ngược lại với chân (NC) chân này sẽ không nối với chân (COM) khi chưa có tín hiệu kích của mạch xử lý hoặc khi Relay chưa hoạt động, khi có tín hiệu kích từ mạch xử lý thì chân (COM) sẽ ngắt kết nối với chân (NC) và chuyển sang nối với chân (NO).
* COM: là viết tắt của chân chung (Common), chân này có thể điều khiển bởi tín hiệu từ mạch xử lý để có thể nối hoặc ngắt với hai chân (NC) hoặc (NO), khi chưa có tín hiệu kích của mạch xử lý hoặc khi Relay chưa hoạt động thì chân (COM) luôn nối với chân (NC).
Dựa vào nguyên lý hoạt động của Relay ta có thể sử dụng cặp tiếp điểm (COM) / (NO) hoặc (COM) / (NC) đấu nối tiếp với tải hoặc tín hiệu điện AC/DC để có thể điều khiển đóng ngắt bằng mạch xử lý như hình:
[[File:How relay work.gif|alt=Nguyên lý hoạt động của Relay|none|thumb|420x420px|Nguyên lý hoạt động của Relay]]
==Thông số kỹ thuật==
*Điện áp hoạt động: 5VDC
*Chuẩn giao tiếp: Digital
*Điện áp giao tiếp: TTL 3.3VDC
*Loại Relay: SRD-05VDC-SL-C
*Công suất chịu tải của Relay:
**10A 250VAC / 10A 125VAC
**10A 30VDC / 10A 28VDC
*Tích` hợp Transistor, Diode và Opto cách ly bảo vệ an toàn, chống nhiễu.
* Sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
* Chuẩn kết nối: connector XH2.54 3Pins
* Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
{{kxnKichThuocFrame_C2
|name=MKL-M05 optocoupler relay module dimension
}}
==Các chân tín hiệu==
[[image:mkl-m05_optocoupler_relay_module_back.jpg|thumb|400x400px|MKE-M05 optocoupler relay module back|link=Special:FilePath/mkl-m05_optocoupler_relay_module_back.jpg|alt=MKL-M05 optocoupler relay module back]]
{| class="wikitable" border="1"
|-
!MKE-M05
!Ghi chú
|-
|GND
|Chân cấp nguồn âm 0VDC
|-
|5V
|Chân cấp nguồn dương 5VDC
|-
|SIG
|Chân tín hiệu Digital In
|-
|NC
|Cổng kết nối chân tiếp điểm thường đóng của Relay (Normally Close)
|-
|COM
|Cổng kết nối chân tiếp điểm chung của Relay (Common)
|-
|NO
|Cổng kết nối chân tiếp điểm thường mở của Relay (Normally Open)
|}
{| class="wikitable" border="1"
|-
!SIG (Digital In)
!Trạng thái
|-
|TTL HIGH
|Không hoạt động (Off)
|-
|TTL LOW
| Hoạt động (On)
|}
==Hướng dẫn sử dụng với phần mềm Arduino và Vietduino==

===Phần cứng cần chuẩn bị:===
*Mạch đóng ngắt tải MKE-M05 optocoupler relay module
*[[Mạch nút nhấn MKE-M02 push button tact switch module]]
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

// Chọn chân Digital điều khiển Relay.
// Select the Digital pin to control Relay.
#define RELAY_PIN 10

// Lưu trạng thái hiện tại của Relay (true = OFF Relay).
// Save the current state of the Relay (true = OFF Relay).
bool stateRelay = true;

void setup()
{
  // Khởi động kết nối Serial UART ở tốc độ 9600 để truyền dữ liệu lên máy tính.
  // Start the Serial UART connection at 9600 to transfer data to the computer.
  Serial.begin(9600);

  // Liên kết hàm "controlRelay" được gọi trên một sự kiện 1 Click.
  // Link the "controlRelay" function to be called on a single click event.
  btn.attachClick(controlRelay);

  // Cấu hình đây là chân Digital Output.
  // Config this is Digital Output.
  pinMode(RELAY_PIN, OUTPUT);

  // Đảm bảo tắt Relay khi mới khởi động.
  // Make sure to turn off the Relay when starting.
  digitalWrite(RELAY_PIN, stateRelay);
}

void loop()
{
  // Tiếp tục theo dõi Nút nhấn.
  // Keep watching the Button.
  btn.tick();
}

void controlRelay()
{
  // Đảo trạng thái Relay.
  // Invert the Relay state.
  stateRelay = !stateRelay;
  digitalWrite(RELAY_PIN, stateRelay);

  // Truyền giá trị lên máy tính.
  // Transmit the value to the computer.
  if (stateRelay)
  {
    Serial.println("Relay: OFF");
  }
  else
  {
    Serial.println("Relay: ON");
  }
}
</source>

=== Sơ đồ kết nối: ===
{| class="wikitable"
!MakerEdu Shield for Vietduino
! style="text-align:left;" |Arduino/Vietduino
!Devices
|-
|Port D10
|D10
|Mạch Đóng Ngắt Tải MKE-M05 Optocoupler Relay Module
|-
|Port D11
|D11
|Mạch Nút Nhấn MKE-M02 Push Button Tact Switch Module
|}

=== Các bước tiến hành: ===
#Kết nối mạch Vietduino Uno với mạch MakerEDU Shield for Vietduino.
#Kết nối Mạch Đóng Ngắt Tải MKE-M05 với mạch MakerEDU Shied for Vietduino qua '''Port D10'''.
#Kết nối Mạch Nút Nhấn MKE-M02 với mạch MakerEDU Shied for Vietduino qua '''Port D11'''.
#Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port).
#Nạp chương trình mẫu vào mạch Vietduino Uno.
#Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.

=== Kết quả: ===
...pic

==Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator==
===Phần cứng cần chuẩn bị:===
* Mạch đóng ngắt tải MKE-M05 optocoupler relay module
* [[Mạch nút nhấn MKE-M02 push button tact switch module]]
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Creator]] 
* Cáp USB để nạp chương trình và cấp nguồn
===Phần mềm cần chuẩn bị:===
*Tải và cài đặt phần mềm mBlock theo [[Giới thiệu và hướng dẫn cài đặt phần mềm mBlock|hướng dẫn.]]
*Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn]].
*Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm mBlock|hướng dẫn.]]
===Chương trình mẫu:===

# Mạch MakerEdu Creator sẽ chờ tín hiệu từ Nút nhấn, mỗi khi bạn nhấn 1 Click.
# Nó sẽ đảo ngược trạng thái của Relay, đang tắt thì mở và ngược lại.
# Trạng thái hiện tại của Relay sẽ được hiển thị trên màn hình LCD.

<u>'''Blocks'''</u>

[[File:MBlock M05.PNG|border|700x700px]]

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEdu Creator
!Devices
|-
|Port D10
|Mạch Đóng Ngắt Tải MKE-M05 Optocoupler Relay Module
|-
|Port D11
|Mạch Nút Nhấn MKE-M02 Push Button Tact Switch Module
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}
===Các bước tiến hành:===
#Kết nối Mạch Đóng Ngắt Tải MKE-M05 với mạch MakerEdu Creator qua '''Port D10'''.
#Kết nối Mạch Nút Nhấn MKE-M02 với mạch MakerEdu Creator qua '''Port D11'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEdu Creator qua '''Port I2C'''.
#Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
#Nạp chương trình mẫu vào mạch MakerEdu Creator.
#Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.
===Kết quả:===
...pic

==Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bit==

===Phần cứng cần chuẩn bị:===

* [[Mạch đóng ngắt tải MKE-M05 optocoupler relay module]]
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Shield for Micro:bit]]
* [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|Mạch Micro:Bit]]
* Cáp USB để nạp chương trình và cấp nguồn

===Phần mềm cần chuẩn bị:===
*Khởi động phần mềm MakeCode theo [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|hướng dẫn]].
*Cài đặt Extension MakerEdu Hardware trên MadeCode và tham khảo các khối chức năng theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm MakeCode|hướng dẫn]].
*Tham khảo cách kết nối và nạp chương trình cho Micro:bit [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên máy tính với phần mềm MakeCode|trên máy tính]] hoặc [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên điện thoại, máy tính bảng với phần mềm MakeCode|điện thoại, máy tính bảng.]]

===Chương trình mẫu:===

# Trên bo mạch Micro:Bit có sẵn 2 nút nhấn A và B cho bạn sử dụng.
# Trong chương trình này, khi nhấn nút A sẽ bật Relay, nhấn nút B để tắt Relay.
# Micro:bit có gửi thông tin thao tác nút lên màn hình LCD để bạn theo dõi.

'''<u>Blocks</u>'''

[[File:MakeCode M05.PNG|border]]

'''<u>Javascript</u>'''

<source lang="typescript">
// Xóa toàn bộ nội dung trên LCD (nếu có)
lcd.clearScreen()
// Cho hiển thị tiêu đề trên LCD và tắt Relay
lcd.displayText("Relay: OFF", 1, 1)
pins.digitalWritePin(DigitalPin.P0, 1)

// Khi nhấn nút A, Relay được bật
input.onButtonPressed(Button.A, function () {
  lcd.displayText("ON ", 8, 1)
  pins.digitalWritePin(DigitalPin.P0, 0)
})

// Khi nhấn nút B, Relay bị tắt
input.onButtonPressed(Button.B, function () {
  lcd.displayText("OFF", 8, 1)
  pins.digitalWritePin(DigitalPin.P0, 1)
})
</source>

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEDU Shield
!Devices
|-
|Port P0
|Mạch Đóng Ngắt Tải MKE-M05 Optocoupler Relay Module
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}

===Các bước tiến hành:===
#Kết nối Mạch Đóng Ngắt Tải MKE-M05 với mạch MakerEDU Shield For Micro:Bit qua '''Port P0'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEDU Shield For Micro:Bit qua '''Port I2C'''.
# Kết nối Micro:bit với mạch MakerEdu Shield for Micro:bit
# Nạp chương trình mẫu vào mạch Micro:Bit.
# Nhấn nút Reset trên mạch Micro:Bit để bắt đầu chạy chương trình.

===Kết quả:===
...pic

==Nhà phân phối==
Có thể mua Mạch đóng ngắt tải MKE-M05 optocoupler relay module tại các nhà phân phối sau:
* [https://hshop.vn/products/mach-dong-ngat-tai-mkl-m05-optocoupler-relay-module Hshop.vn - Điện tử & Robot.]
[[Category:Modules]]
