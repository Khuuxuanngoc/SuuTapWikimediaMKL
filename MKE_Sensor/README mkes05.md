[[image:mkl-s05_ntc_temperature_sensor.jpg|thumb|367x367px|MKE-S05 NTC temperature sensor|link=Special:FilePath/mkl-s05_ntc_temperature_sensor.jpg]]
==Giới thiệu==
Cảm biến nhiệt độ MKE-S05 NTC temperature sensor được sử dụng để đo nhiệt độ của môi trường bằng cảm biến nhiệt NTC, cảm biến trả ra giá trị điện áp Analog tuyến tính tương ứng với nhiệt độ môi trường giúp bạn có thể ghi nhận và xử lý thông tin một cách chính xác nhất, ngoài ra cảm biến còn được bổ sung các thiết kế ổn định, chống nhiễu.

Cảm biến nhiệt độ MKE-S05 NTC temperature sensor thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.
==Nguyên lý hoạt động==
Cảm biến sử dụng nhiệt điện trở NTC (Negative Temperature Coefficient) là loại có điện trở giảm khi nhiệt độ tăng, bằng cách đo giá trị điện trở thay đổi tuyến tính với nhiệt độ ta có thể nhận biết được nhiệt độ của môi trường, để chuyển giá trị điện trở của cảm biến thành điện áp để có thể đọc bằng bộ chuyển đổi ADC (Analog to Digital Converter) của mạch xử lý ta mắc mạch cầu phân áp như sau:
[[File:MLK-S05 NTC temperature sensor.jpg|alt=Sơ đồ mạch chuyển giá trị điện trở thành điện áp.|none|thumb|425x425px|Sơ đồ mạch chuyển giá trị điện trở thành điện áp.]]
'''Diễn giải các giá trị:'''
* VCC: điện áp cấp nguồn cho cảm biến.
*RS: Giá trị điện trở của nhiệt điện trở NTC
*R2: Điện trở tạo thành cấu trúc cầu phân áp với RS, có giá trị xác định theo khuyến nghị của nhà sản xuất.
* Vout: Điện áp đầu ra thay đổi theo giá trị của RS.
Ta thấy theo công thức trong hình giá trị Vout sẽ thay đổi theo giá trị của điện trở RS, mà RS sẽ thay đổi tuyến tính theo nhiệt độ của môi trường, khi đó dùng mạch xử lý để đo Vout ta xác định được nhiệt độ của môi trường tại thời điểm đo.
==Thông số kỹ thuật==
* Điện áp hoạt động: 5VDC
*Chuẩn giao tiếp: Analog
*Điện áp giao tiếp: 0~3.3VDC
*Đo nhiệt độ môi trường bằng nhiệt điện trở NTC (Negative Temperature Coefficient).
* Sử dụng trực tiếp an toàn với các board mạch giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
* Bổ sung thêm các thiết kế ổn định, chống nhiễu.
* Chuẩn kết nối: connector XH2.54 3Pins
* Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
{{kxnKichThuocFrame_A
|name=MKL-S05 NTC temperature sensor dimension
}}
==Các chân tín hiệu==
[[image:mkl-s05_ntc_temperature_sensor_back.jpg|thumb|367x367px|MKE-S05 NTC temperature sensor back|link=Special:FilePath/mkl-s05_ntc_temperature_sensor_back.jpg]]
{| class="wikitable" border="1"
|-
!MKE-S05
!Ghi chú
|-
|GND
|Chân cấp nguồn âm 0VDC
|-
|5V
|Chân cấp nguồn dương 5VDC
|-
|SIG
|Chân tín hiệu ngõ ra Analog 0~3.3VDC
|}
==Hướng dẫn sử dụng với phần mềm Arduino và Vietduino==

===Phần cứng cần chuẩn bị:===
*Cảm biến nhiệt độ MKE-S05 NTC temperature sensor
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
// Chọn chân Analog đọc cảm biến.
// Select the Analog pin to read the sensor.
#define SENSOR_PIN A1

// Các hằng số trong công thức NTC.
// Constants in math formula NTC.
#define A 0.001009249522
#define B 0.0002378405444
#define C 2.019202697e-7

// Lưu giá trị Analog đọc từ cảm biến.
// Stores the Analog value read from the sensor.
float value;

// Điện trở phân áp (1k Ohm) với NTC.
// Voltage divider resistor (1k Ohm) with NTC.
#define R 1000.0

// Lưu giá trị điện trở hiện tại của NTC.
// Store the current resistance value of the NTC.
float rNTC;

// Lưu giá trị Logarit tự nhiên của điện trở NTC.
// Store the Natural Logarithm of the NTC resistor.
float log_rNTC;

// Lưu giá trị nhiệt độ (°K) và (°C) của NTC.
// Store the temperature value (°K) and (°C) of NTC.
float tempK;
float tempC;

void setup()
{
  // Khởi động kết nối Serial UART ở tốc độ 9600 để truyền dữ liệu lên máy tính.
  // Start the Serial UART connection at 9600 to transfer data to the computer.
  Serial.begin(9600);
}

void loop()
{
  // Đọc giá trị Analog.
  // Read Analog value.
  value = analogRead(SENSOR_PIN);

  /**
   * Các bước tính nhiệt độ của NTC
   * 1. Tính giá trị Điện trở hiện tại của NTC dựa trên giá trị Analog
   * 2. Tính Logarit của giá trị Điện trở NTC
   * 3. Áp dụng công thức của NTC, tính ra nhiệt độ °K
   * 4. Chuyển đổi °K sang °C
   */
  rNTC = R / ((677.0 / value) - 1.0);
  log_rNTC = log(rNTC);
  tempK = (1.0 / (A + B * log_rNTC + C * log_rNTC * log_rNTC * log_rNTC));
  tempC = tempK - 273.15;

  // Truyền giá trị đo được của cảm biến lên máy tính.
  // Transmit the measured value of the sensor to the computer.
  Serial.print("Temperature in °C: ");
  Serial.println(tempC, 2);

  // Chờ 0,5s mới đo lại.
  // Wait 0,5s to measure again.
  delay(500);
}
</source>

=== Sơ đồ kết nối: ===
{| class="wikitable"
!MakerEdu Shield for Vietduino
!Arduino / Vietduino
!Devices
|-
|Port A1
|A1
|Cảm biến nhiệt độ MKE-S05 NTC temperature sensor
|}

=== Các bước tiến hành: ===
#Kết nối mạch Vietduino Uno với mạch MakerEDU Shield for Vietduino.
#Kết nối Cảm Biến Nhiệt Độ MKE-S05 với mạch MakerEDU Shied for Vietduino qua '''Port A1'''.
#Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port).
#Nạp chương trình mẫu vào mạch Vietduino Uno.
#Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.

=== Kết quả: ===

==Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator==
===Phần cứng cần chuẩn bị:===
* Cảm biến nhiệt độ MKE-S05 NTC temperature sensor
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Creator]] 
* Cáp USB để nạp chương trình và cấp nguồn
===Phần mềm cần chuẩn bị:===
*Tải và cài đặt phần mềm mBlock theo [[Giới thiệu và hướng dẫn cài đặt phần mềm mBlock|hướng dẫn.]]
*Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn]].
*Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm mBlock|hướng dẫn.]]
===Chương trình mẫu:===

# Mạch MakerEdu Creator đọc liên tục giá trị Analog từ cảm biến nhiệt độ NTC, với chu kỳ mỗi 0,5s.
# Từ giá trị Analog, mạch MakerEdu Creator thực hiện một số phép tính theo công thức của cảm biến, để tính ra giá trị nhiệt độ °C.
# Gửi thông tin giá trị lên màn hình LCD, dưới đơn vị (°C).

<u>'''Blocks'''</u>

[[File:MBlock S05.PNG|border|700x700px]]

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEdu Creator
!Devices
|-
|Port A1
|Cảm Biến Nhiệt Độ MKE-S05 NTC Temperature Sensor
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}
===Các bước tiến hành:===
#Kết nối Cảm Biến Nhiệt Độ MKE-S05 với mạch MakerEdu Creator qua '''Port A1'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEdu Creator qua '''Port I2C'''.
#Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
#Nạp chương trình mẫu vào mạch MakerEdu Creator.
#Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.
===Kết quả:===
==Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bit==

===Phần cứng cần chuẩn bị:===

* Cảm biến nhiệt độ MKE-S05 NTC temperature sensor
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Shield for Micro:bit]]
* Bo mạch Micro:Bit
* Cáp USB để nạp chương trình và cấp nguồn

===Phần mềm cần chuẩn bị:===
*Khởi động phần mềm MakeCode theo [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|hướng dẫn]].
*Cài đặt Extension MakerEdu Hardware trên MadeCode và tham khảo các khối chức năng theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm MakeCode|hướng dẫn]].
* Tham khảo cách kết nối và nạp chương trình cho Micro:bit [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên máy tính với phần mềm MakeCode|trên máy tính]] hoặc [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên điện thoại, máy tính bảng với phần mềm MakeCode|điện thoại, máy tính bảng.]]

===Chương trình mẫu:===

# Micro:Bit đọc liên tục giá trị Analog từ cảm biến NTC, với chu kỳ mỗi 0,5s.
# Sau đó Micro:bit thực hiện các phép tính theo công thức của NTC, để tính ra giá trị nhiệt độ °K
# Cuối dùng Micro:bit sẽ đổi độ °K thành độ °C và cho hiển thị giá trị lên màn hình LCD.
# Đồng thời cũng gửi giá trị của NTC ở thang (%) qua cổng Serial, bạn có thể mở mục "Show Data (Device)" để xem trên máy tính.

'''<u>Blocks</u> [ on start ]'''

[[File:MakeCode S05 1.PNG|border|frameless|500x500px]]

'''<u>Blocks</u> [ forever ]'''

[[File:MakeCode S05 2.PNG|border|frameless|1000x1000px]]

{{Tr-Info
|name=Lưu ý:
|value=Để tính được giá trị nhiệt độ từ NTC, bạn sẽ cần dùng đến '''công thức toán Logarit'''.<br>Tiếc rằng, trong bộ khối của MakeCode không có tính năng này.<br>Cho nên bạn chỉ có thể sử dụng được qua tính năng có sẵn trong ngôn ngữ JavaScript.<br>Đơn giản là '''copy''' đoạn code dưới và '''paste''' vào mục JavaScript trên MakeCode.
}}

'''<u>Javascript</u>'''

<source lang="typescript">
/* Các hằng số trong công thức của NTC */
let A = 0.001009249522
let B = 0.0002378405444
let C = 2.019202697e-7

// Giá trị Analog của NTC
let analog_NTC
// Giá trị (%) của NTC
let percent_NTC

// Giá trị điện trở phân áp (1k Ohm) với NTC
let R = 1000
// Giá trị điện trở hiện tại của NTC
let rNTC
// Logarit tự nhiên của điện trở NTC
let log_rNTC

// Giá trị nhiệt độ °K của NTC
let tempK
// Giá trị nhiệt độ °C của NTC
let tempC

// Bật cổng Serial
serial.setBaudRate(BaudRate.BaudRate115200)

// Xóa toàn bộ nội dung trên LCD (nếu có)
lcd.clearScreen()

// Cho hiển thị tiêu đề trước
lcd.displayText("Temperature NTC", 1, 1)
lcd.displayText(lcd.displaySymbol(lcd.Symbols.sym02), 1, 2)

basic.forever(function () {
  // Đọc giá trị Analog của NTC và đổi ra thang (%)
  analog_NTC = pins.analogReadPin(AnalogPin.P0)
  percent_NTC = Math.round(Math.map(analog_NTC, 0, 1023, 100, 0))

  /**
   * Các bước tính nhiệt độ của NTC
   * 1. Tính giá trị Điện trở hiện tại của NTC dựa trên giá trị Analog
   * 2. Tính Logarit của giá trị Điện trở NTC
   * 3. Áp dụng công thức của NTC, tính ra nhiệt độ °K
   * 4. Chuyển đổi °K sang °C
   * 5. Lấy giá trị °C với 2 chữ số thập phân
   */
  rNTC = R / ((1024 / analog_NTC) - 1)
  log_rNTC = Math.log(rNTC)
  tempK = (1 / (A + B * log_rNTC + C * log_rNTC * log_rNTC * log_rNTC))
  tempC = tempK - 273.15
  tempC = Math.trunc(tempC * 100) / 100

  // Cho hiển thị giá trị nhiệt độ °C của NTC trên LCD sau tiêu đề
  lcd.displayText("" + tempC + lcd.displaySymbol(lcd.Symbols.sym07) + "C  ", 3, 2)

  // Gửi giá trị (%) của NTC lên Serial
  serial.writeLine("" + (percent_NTC))

  // Dừng 0.5s
  basic.pause(500)
})
</source>

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEDU Shield for Micro:bit
!Devices
|-
|Port P0
|Cảm biến Nhiệt Độ MKE-S05 NTC Temperature Sensor
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}

===Các bước tiến hành:===
#Kết nối Cảm biến Nhiệt Độ MKE-S05 với mạch MakerEDU Shield For Micro:Bit qua '''Port P0'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEDU Shield For Micro:Bit qua '''Port I2C'''.
# Kết nối Micro:bit với mạch MakerEdu Shield for Micro:bit
# Nạp chương trình mẫu vào mạch Micro:Bit.
# Nhấn nút Reset trên mạch Micro:Bit để bắt đầu chạy chương trình.

===Kết quả:===
==Nhà phân phối==
Có thể mua Cảm biến nhiệt độ MKE-S05 NTC temperature sensor tại các nhà phân phối sau:
* [https://hshop.vn/products/cam-bien-nhiet-do-mkl-s05-ntc-temperature-sensor Hshop.vn - Điện tử & Robot.]
[[Category:Sensor]]
