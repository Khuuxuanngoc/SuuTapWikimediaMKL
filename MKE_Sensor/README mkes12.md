[[image:mkl-s12_rain_water_sensor.jpg|thumb|350x350px|MKE-S12 rain water sensor|link=Special:FilePath/mkl-s12_rain_water_sensor.jpg|alt=MKL-S12 rain water sensor]]
==Giới thiệu==
Cảm biến mưa MKE-S12 rain water sensor bao gồm một đầu dò (probe) và mạch chuyển đổi tín hiệu, cảm biến hoạt động theo nguyên lý cảm ứng điện dung nên đầu dò được phủ lớp sơn chống oxy hóa (không hở phần tiếp xúc kim loại như các loại sử dụng nguyên lý điện trở) cho độ bền cao, cảm biến trả ra giá trị điện áp Analog tương ứng với lượng nước lưu lại trên đầu dò giúp bạn có thể ghi nhận và xử lý thông tin một cách chính xác nhất, ngoài ra cảm biến còn được bổ sung các thiết kế ổn định, chống nhiễu.

Cảm biến mưa MKE-S12 rain water sensor thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.
==Nguyên lý hoạt động==
Cảm biến hoạt động theo nguyên lý cảm ứng điện dung để nhận biết lượng nước đọng trên đầu dò (probe), sau đó điện dung của đầu dò (probe) được đưa qua mạch chuyển đổi tín hiệu để chuyển thành tín hiệu điện có thể đọc được bằng bộ chuyển đổi ADC (Analog to Digital Converter) của mạch xử lý.
==Thông số kỹ thuật ==
*Điện áp hoạt động: 5VDC
* Chuẩn giao tiếp: Analog
*Điện áp giao tiếp: 0~3.3VDC
*Đo lượng nước lưu lại trên đầu dò theo nguyên lý cảm ứng điện dung và trả ra giá trị điện áp Analog tuyến tính tương ứng.
*Hoạt động theo nguyên lý cảm ứng điện dung nên đầu dò được phủ lớp sơn chống oxy hóa (không hở phần tiếp xúc kim loại như các loại sử dụng nguyên lý điện trở) cho độ bền cao.
*Sử dụng trực tiếp an toàn với các board mạch giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
* Bổ sung thêm các thiết kế ổn định, chống nhiễu.
* Chuẩn kết nối:
** 1 x Conector XH2.54 3Pins (cổng tín hiệu Analog)
** 1 x Conector XH2.54 2Pins (cổng kết nối đầu dò (Probe))
* Cáp đầu dò (Probe) dài 40cm.
* Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
{{kxnKichThuocFrame_A
|name=MKL-S12 rain water sensor dimension
}}
[[File:FRAME_Rain_Probe.JPG|alt=MKL-S12 rain water sensor probe dimension|none|thumb|400x400px|MKE-S12 rain water sensor probe dimension]]
==Các chân tín hiệu==
[[image:mkl-s12_rain_water_sensor_back.jpg|thumb|327x327px|MKE-S12 rain water sensor back|link=Special:FilePath/mkl-s12_rain_water_sensor_back.jpg|alt=MKL-S12 rain water sensor back]]
{| class="wikitable" border="1"
|-
!MKE-S12
!Ghi chú
|-
|GND
|Chân cấp nguồn âm 0VDC
|-
|5V
| Chân cấp nguồn dương 5VDC
|-
|SIG
|Chân tín hiệu ngõ ra Analog 0~3.3VDC
|-
|Probe
|Cổng kết nối đầu dò (Probe)
|}
==Hướng dẫn sử dụng với phần mềm Arduino và Vietduino==

===Phần cứng cần chuẩn bị:===
*Cảm biến mưa MKE-S12 rain water sensor
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

// Lưu giá trị Analog đọc từ cảm biến.
// Stores the Analog value read from the sensor.
int value;

// Lưu giá trị (%) đổi từ giá trị Analog tương ứng.
// Store the value (%) converted from the corresponding Analog value.
int percent;

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

  // Chuyển đổi sang thang đo (%).
  // Convert to scale (%).
  percent = map(value, 0, 676, 100, 0);

  // Truyền giá trị đo được của cảm biến lên máy tính.
  // Transmit the measured value of the sensor to the computer.
  Serial.print("Amount of Rain in %: ");
  Serial.println(percent);

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
|Cảm biến mưa MKE-S12 rain water sensor
|}

=== Các bước tiến hành: ===
#Kết nối mạch Vietduino Uno với mạch MakerEDU Shield for Vietduino.
#Kết nối Cảm Biến Mưa MKE-S12 với mạch MakerEDU Shied for Vietduino qua '''Port A1'''.
#Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port).
#Nạp chương trình mẫu vào mạch Vietduino Uno.
#Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.

=== Kết quả: ===
...pic

==Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator==
===Phần cứng cần chuẩn bị:===
* Cảm biến mưa MKE-S12 rain water sensor
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Creator]] 
* Cáp USB để nạp chương trình và cấp nguồn
===Phần mềm cần chuẩn bị:===
*Tải và cài đặt phần mềm mBlock theo [[Giới thiệu và hướng dẫn cài đặt phần mềm mBlock|hướng dẫn.]]
*Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn]].
*Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm mBlock|hướng dẫn.]]
===Chương trình mẫu:===

# Mạch MakerEdu Creator đọc liên tục giá trị Analog từ cảm biến mưa, với chu kỳ mỗi 0,5s.
# Gửi thông tin giá trị lên màn hình LCD, dưới đơn vị (%).

<u>'''Blocks'''</u>

[[File:MBlock S12.PNG|border|700x700px]]

<u>'''Link Code mBlock:'''</u> Example Code.

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEdu Creator
!Devices
|-
|Port A1
|Cảm Biến Mưa MKE-S12 Rain Water Sensor
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}
===Các bước tiến hành:===
#Kết nối Cảm Biến Mưa MKE-S12 với mạch MakerEdu Creator qua '''Port A1'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEdu Creator qua '''Port I2C'''.
#Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
#Nạp chương trình mẫu vào mạch MakerEdu Creator.
#Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.
===Kết quả:===
...pic

==Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bit==

===Phần cứng cần chuẩn bị:===

* Cảm biến mưa MKE-S12 rain water sensor
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Shield for Micro:bit]]
* Bo mạch Micro:Bit
* Cáp USB để nạp chương trình và cấp nguồn

===Phần mềm cần chuẩn bị:===
*Khởi động phần mềm MakeCode theo [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|hướng dẫn]].
*Cài đặt Extension MakerEdu Hardware trên MadeCode và tham khảo các khối chức năng theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm MakeCode|hướng dẫn]].
*Tham khảo cách kết nối và nạp chương trình cho Micro:bit [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên máy tính với phần mềm MakeCode|trên máy tính]] hoặc [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên điện thoại, máy tính bảng với phần mềm MakeCode|điện thoại, máy tính bảng.]]

===Chương trình mẫu:===

# Micro:Bit đọc liên tục giá trị Analog từ cảm biến mưa, với chu kỳ mỗi 0,5s.
# Sau đó Micro:Bit đổi giá trị sang thang (%) tương ứng, để hiển thị lên LCD.
# Micro:Bit cũng gửi giá trị đó qua cổng Serial, bạn có thể mở mục "Show Data (Device)" để xem trên máy tính.

<u>'''Blocks'''</u>

[[File:MakeCode S12.PNG|border|frameless|700x700px]]

'''<u>Javascript</u>'''

<source lang="typescript">
// Giá trị Analog của cảm biến
let dataAnalog = 0
// Giá trị (%) của cảm biến
let dataPercent = 0

// Bật cổng Serial
serial.setBaudRate(BaudRate.BaudRate115200)

// Xóa toàn bộ nội dung trên LCD (nếu có)
lcd.clearScreen()

// Cho hiển thị tiêu đề trước
lcd.displayText("Amount of Rain", 1, 1)
lcd.displayText(lcd.displaySymbol(lcd.Symbols.sym02), 1, 2)

basic.forever(function () {
  // Đọc giá trị Analog của cảm biến và đổi ra thang (%)
  dataAnalog = pins.analogReadPin(AnalogPin.P0)
  dataPercent = Math.round(Math.map(dataAnalog, 0, 1023, 100, 0))

  // Cho hiển thị giá trị (%) của cảm biến trên LCD
  lcd.displayText("" + dataPercent + "%  ", 3, 2)

  // Gửi giá trị (%) của cảm biến lên Serial
  serial.writeLine("" + (dataPercent))

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
|Cảm Biến Mưa MKE-S12 Rain Water Sensor
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}

===Các bước tiến hành:===
#Kết nối Cảm Biến Mưa MKE-S12 với mạch MakerEDU Shield For Micro:Bit qua '''Port P0'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEDU Shield For Micro:Bit qua '''Port I2C'''.
# Kết nối Micro:bit với mạch MakerEdu Shield for Micro:bit
# Nạp chương trình mẫu vào mạch Micro:Bit.
# Nhấn nút Reset trên mạch Micro:Bit để bắt đầu chạy chương trình.

===Kết quả:===
...pic

==Nhà phân phối==
Có thể mua Cảm biến mưa MKE-S12 rain water sensor tại các nhà phân phối sau:
* [https://hshop.vn/products/cam-bien-mua-mkl-s12-rain-water-sensor Hshop.vn - Điện tử & Robot.]
[[Category:Sensor]]
