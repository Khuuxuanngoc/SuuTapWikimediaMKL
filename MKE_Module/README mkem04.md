[[image:mkl-m04_potentiometer_module.jpg|thumb|333x333px|MKE-M04 potentiometer module|link=Special:FilePath/mkl-m04_potentiometer_module.jpg|alt=MKL-M04 potentiometer module]]
==Giới thiệu==
Mạch biến trở MKE-M04 potentiometer module trả ra giá trị điện áp Analog tuyến tính với góc của trục xoay biến trở giúp bạn có thể ghi nhận và xử lý thông tin một cách chính xác nhất, ứng dụng trong các dạng điều khiển tăng giảm giá trị.

Mạch biến trở MKE-M04 potentiometer module thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.
==Thông số kỹ thuật==
* Điện áp hoạt động: 5VDC
*Chuẩn giao tiếp: Analog
* Điện áp giao tiếp: 0~3.3VDC
*Trả ra giá trị điện áp Analog tuyến tính với góc của trục xoay biến trở.
* Sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
* Bổ sung thêm các thiết kế ổn định, chống nhiễu.
* Chuẩn kết nối: connector XH2.54 3Pins
* Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
{{kxnKichThuocFrame_A
|name=MKL-M04 potentiometer module dimension
}}
==Các chân tín hiệu==
[[image:mkl-m04_potentiometer_module_back.jpg|thumb|313x313px|MKE-M04 potentiometer module back|link=Special:FilePath/mkl-m04_potentiometer_module_back.jpg|alt=MKL-M04 potentiometer module back]]
{| class="wikitable" border="1"
|-
!MKE-M04
!Ghi chú
|-
|GND
|Chân cấp nguồn âm 0VDC
|-
|5V
|Chân cấp nguồn dương 5VDC
|-
|SIG
|Chân tín hiệu ngõ ra Analog Out
|}
==Hướng dẫn sử dụng với phần mềm Arduino và Vietduino==

===Phần cứng cần chuẩn bị:===
*Mạch biến trở MKE-M04 potentiometer module
*[[Mạch led đơn MKE-M01 10mm single LED module]]
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
// Chọn chân Analog đọc Biến trở.
// Select the Analog pin to read the Potentiometer.
#define POT_PIN A1

// Số lần lấy mẫu.
// Number of sampling times.
#define SAMPLES 25

// Lưu giá trị Analog đọc từ Biến trở.
// Stores the Analog value read from the Potentiometer.
int valuePot;

// Lưu giá trị Analog lớn nhất đọc được từ Biến trở.
// Store the maximum Analog value read from the Potentiometer.
int maxPot = 676;

// Lưu giá trị (%) đổi từ giá trị Analog tương ứng.
// Store the value (%) converted from the corresponding Analog value.
int percentPot;

// Chọn chân Digital điều khiển LED.
// Select the Digital pin to control LED.
#define LED_PIN 10

// Lưu giá trị (~PWM) điều khiển LED.
// Save value (~PWM) control LED.
int lightLED;

void setup()
{
  // Khởi động kết nối Serial UART ở tốc độ 9600 để truyền dữ liệu lên máy tính.
  // Start the Serial UART connection at 9600 to transfer data to the computer.
  Serial.begin(9600);
}

void loop()
{
  /**
   * Các bước tính giá trị trung bình của cảm biến
   * 1. Xóa giá trị trong biến về 0
   * 2. Cộng tổng các mẫu đo lại
   * 3. Chia số mẫu để lấy giá trị trung bình
   */
  valuePot = 0;
  for (int i = 0; i < SAMPLES; i++)
  {
    valuePot += analogRead(POT_PIN);

    // Chờ 0,001s mới đo lại.
    // Wait 0,001s to measure again.
    delay(1);
  }
  valuePot = valuePot / SAMPLES;

  // Lưu nếu giá trị lớn nhất hiện tại được phát hiện.
  // Save if the current maximum value is detected.
  if (maxPot < valuePot)
  {
    maxPot = valuePot;
  }

  // Chuyển đổi sang thang đo (%).
  // Convert to scale (%).
  percentPot = map(valuePot, 0, maxPot, 0, 100);

  // Chuyển đổi sang thang đo (~PWM).
  // Conver to scale (~PWM).
  lightLED = map(percentPot, 0, 100, 0, 255);

  // Điều khiển độ sáng LED theo Biến trở.
  // Control LED brightness according to the Potentiometer.
  analogWrite(LED_PIN, lightLED);

  // Truyền giá trị đo được của cảm biến lên máy tính.
  // Transmit the measured value of the sensor to the computer.
  Serial.print(0);
  Serial.print(" ");
  Serial.print(100);
  Serial.print(" ");
  Serial.println(percentPot);

  // Chờ 0,025s.
  // Wait 0,025s.
  delay(25);
}
</source>

=== Sơ đồ kết nối: ===
{| class="wikitable"
!MakerEdu Shield for Vietduino
! style="text-align:left;" |Arduino/Vietduino
!Devices
|-
|Port A1
|A1
|Mạch Biến Trở MKE-M04 Potentiometer Module
|-
|Port D10
|D10
|Mạch Led Đơn MKE-M01 10mm Single LED Module
|}

=== Các bước tiến hành: ===
#Kết nối mạch Vietduino Uno với mạch MakerEDU Shield for Vietduino.
#Kết nối Mạch Biến Trở MKE-M04 với mạch MakerEDU Shied for Vietduino qua '''Port A1'''.
#Kết nối Mạch Led Đơn MKE-M01 với mạch MakerEDU Shied for Vietduino qua '''Port D10'''.
#Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port).
#Nạp chương trình mẫu vào mạch Vietduino Uno.
#Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.

{{Tr-Done
|name=Tip:
|value=Bạn có thể mở '''Serial Plotter''' để xem đồ thị trực quan hơn cách mạch Biến trở phản hồi về.
}}

=== Kết quả: ===
...pic

==Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator==
===Phần cứng cần chuẩn bị:===
* Mạch biến trở MKE-M04 potentiometer module
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Creator]]
* Động cơ RC Servo
* Cáp USB để nạp chương trình và cấp nguồn
===Phần mềm cần chuẩn bị:===
*Tải và cài đặt phần mềm mBlock theo [[Giới thiệu và hướng dẫn cài đặt phần mềm mBlock|hướng dẫn.]]
*Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn]].
*Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm mBlock|hướng dẫn.]]
===Chương trình mẫu:===

# Mạch MakerEdu Creator đọc liên tục giá trị Analog từ Biến trở, sau đó chuyển đổi giá trị này sang thang (độ °) tương ứng để điều khiển Servo.
# Nó cũng gửi các giá trị này lên màn hình LCD để bạn theo dõi.

<u>'''Blocks'''</u>

[[File:MBlock M04.PNG|border|700x700px]]

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEdu Creator
!Devices
|-
|Port A1
|Mạch Biến Trở MKE-M04 Potentiometer Module
|-
|Port D10
|Động cơ RC Servo
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}
===Các bước tiến hành:===
#Kết nối Mạch Biến Trở MKE-M04 với mạch MakerEdu Creator qua '''Port A1'''.
#Kết nối Động Cơ RC Servo với mạch MakerEdu Creator qua '''Port D10'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEdu Creator qua '''Port I2C'''.
#Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
#Nạp chương trình mẫu vào mạch MakerEdu Creator.
#Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.
===Kết quả:===
...pic

==Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bit==

===Phần cứng cần chuẩn bị:===

* [[Mạch biến trở MKE-M04 potentiometer module]]
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Shield for Micro:bit]]
* [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|Mạch Micro:Bit]]
* Động cơ RC Servo
* Cáp USB để nạp chương trình và cấp nguồn

===Phần mềm cần chuẩn bị:===
*Khởi động phần mềm MakeCode theo [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|hướng dẫn]].
*Cài đặt Extension MakerEdu Hardware trên MadeCode và tham khảo các khối chức năng theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm MakeCode|hướng dẫn]].
*Tham khảo cách kết nối và nạp chương trình cho Micro:bit [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên máy tính với phần mềm MakeCode|trên máy tính]] hoặc [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên điện thoại, máy tính bảng với phần mềm MakeCode|điện thoại, máy tính bảng.]]

===Chương trình mẫu:===

# Micro:bit đọc liên tục giá trị Analog từ Biến trở. Sau đó chuyển đổi giá trị này sang thang (độ °) tương ứng để điều khiển Servo.
# Micro:bit cũng gửi các giá trị này lên màn hình LCD để bạn theo dõi.

'''<u>Blocks</u>'''

[[File:MakeCode M04.PNG|border]]

'''<u>Javascript</u>'''

<source lang="typescript">
// Giá trị góc điều khiển Servo
let angle = 0
// Giá trị Biến trở đọc được
let pot = 0

// Xóa toàn bộ nội dung trên LCD (nếu có)
lcd.clearScreen()
// Cho hiển thị tiêu đề trên LCD
lcd.displayText("Pot  :", 1, 1)
lcd.displayText("Servo:", 1, 2)

basic.forever(function () {
  // Đọc giá trị Biến trở
  pot = pins.analogReadPin(AnalogPin.P0)
  // Chuyển đổi giá trị trên sang Góc tương ứng
  angle = Math.round(Math.map(pot, 0, 1023, 0, 180))

  // Hiển thị giá trị Biến trở lên LCD
  lcd.displayText("" + pot + "   ", 8, 1)
  // Hiển thị giá trị Góc lên LCD
  lcd.displayText("" + angle + lcd.displaySymbol(lcd.Symbols.sym07) + "  ", 8, 2)

  // Điều khiển Servo với giá trị Góc
  pins.servoWritePin(AnalogPin.P12, angle)

  // Dừng 0.01s
  basic.pause(10)
})
</source>

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEDU Shield for Micro:bit
!Devices
|-
|Port P0
|Mạch Biến Trở MKE-M04 Potentiometer Module
|-
|Port P12
|Động Cơ RC Servo
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}

===Các bước tiến hành:===
#Kết nối Mạch Biến Trở MKE-M04 với mạch MakerEDU Shield For Micro:Bit qua '''Port P0'''.
#Kết nối Động Cơ RC Servo với mạch MakerEDU Shield For Micro:Bit qua '''Port P12'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEDU Shield For Micro:Bit qua '''Port I2C'''.
# Kết nối Micro:bit với mạch MakerEdu Shield for Micro:bit
# Nạp chương trình mẫu vào mạch Micro:Bit.
# Nhấn nút Reset trên mạch Micro:Bit để bắt đầu chạy chương trình.

===Kết quả:===
...pic

==Nhà phân phối==
Có thể mua Mạch biến trở MKE-M04 potentiometer module tại các nhà phân phối sau:
* [https://hshop.vn/products/mach-bien-tro-mkl-m04-potentiometer-module Hshop.vn - Điện tử & Robot.]
[[Category:Modules]]
