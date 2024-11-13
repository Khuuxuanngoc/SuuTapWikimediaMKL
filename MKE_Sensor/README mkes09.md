[[image:mkl-s08_mq2_gas_sensor.jpg|thumb|315x315px|MKE-S09 MQ-135 Air Quality Sensor|link=Special:FilePath/mkl-s08_mq2_gas_sensor.jpg.jpg|alt=MKL-S09 MQ-135 Air Quality Sensor]]
==Giới thiệu==
Cảm biến chất lượng không khí MKE-S09 MQ-135 Air Quality Sensor được sử dụng để đo nồng độ các khí: NH3,NOx, alcohol, Benzene, khói,CO2 ,...giúp bạn xác định được chất lượng không khí của môi trường, cảm biến trả ra giá trị điện áp Analog tuyến tính tương ứng với nồng độ các khí đo được trong không khí giúp bạn có thể ghi nhận và xử lý thông tin một cách chính xác nhất, ngoài ra cảm biến còn được bổ sung các thiết kế ổn định, chống nhiễu.

Cảm biến chất lượng không khí MKE-S09 MQ-135 Air Quality Sensor thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.
==Nguyên lý hoạt động==
Cảm biến chất lượng không khí MKE-S09 MQ-135 Air Quality Sensor được thiết kế dựa trên cảm biến MQ-135 là một loại Chemiresistors (tạm dịch là điện trở hóa học), để tham khảo nguyên lý hoạt động của cảm biến xin tham bảo bài viết: [[Cấu tạo và nguyên lý hoạt dộng của các loại cảm biến MQ]].
==Thông số kỹ thuật==
* Cảm biến chính: MQ-135 Air Quality Sensor, [https://www.mediafire.com/file/wjysxvpfaz9rn5i/&#x5B;MakerLab.vn&#x5D;+MQ-135+Datasheet.pdf/file Datasheet].
* Đo nồng độ các khí: NH3,NOx, alcohol, Benzene, khói,CO2 ,...giúp bạn xác định được chất lượng không khí của môi trường.
* Điện áp hoạt động: 5VDC
* Chuẩn giao tiếp: Analog
* Điện áp giao tiếp: 0~3.3VDC
* Sử dụng trực tiếp an toàn với các board mạch giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
* Bổ sung thêm các thiết kế ổn định, chống nhiễu.
* Chuẩn kết nối: connector XH2.54 3Pins
* Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
==Kích thước==
[[File:MLK-MQ Sensor Dimension.jpg|alt=MKL-S09 MQ-135 Air Quality Sensor dimension|none|thumb|400x400px|MKE-S09 MQ-135 Air Quality Sensor dimension]]
==Các chân tín hiệu==
[[image:mkl_mq_sensor_back.jpg|thumb|325x325px|MKE-S09 MQ-135 Air Quality Sensor back|link=Special:FilePath/mkl_mq_sensor_back.jpg|alt=MKL-S09 MQ-135 Air Quality Sensor back]]
{| class="wikitable" border="1"
|-
! MKE-S09
! Ghi chú
|-
| GND
| Chân cấp nguồn âm 0VDC
|-
| 5V
| Chân cấp nguồn dương 5VDC
|-
| SIG
| Chân tín hiệu ngõ ra Analog 0~3.3VDC
|}
==Hướng dẫn sử dụng với phần mềm Arduino và Vietduino==

===Phần cứng cần chuẩn bị:===
*Cảm biến chất lượng không khí MKE-S09 MQ-135 Air Quality Sensor
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

// Thời gian đợi cảm biến khởi động (s).
// Time to wait for the sensor to start (s).
#define TIME_WAIT 60

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

  // Thời gian còn lại để cảm biến khởi động.
  // Remaining time for the sensor to start.
  for (int i = TIME_WAIT; i > 0; i--)
  {
    Serial.print("Pls, wait in ");
    Serial.print(i);
    Serial.println("s");

    delay(1000);
  }
}

void loop()
{
  // Đọc giá trị Analog.
  // Read Analog value.
  value = analogRead(SENSOR_PIN);

  // Chuyển đổi sang thang đo (%).
  // Convert to scale (%).
  percent = map(value, 0, 676, 0, 100);

  // Truyền giá trị đo được của cảm biến lên máy tính.
  // Transmit the measured value of the sensor to the computer.
  Serial.print("Air Quality in %: ");
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
|Cảm biến chất lượng không khí MKE-S09 MQ-135 Air Quality Sensor
|}

=== Các bước tiến hành: ===
#Kết nối mạch Vietduino Uno với mạch MakerEDU Shield for Vietduino.
#Kết nối Cảm Biến Chất Lượng Không Khí MKE-S09 với mạch MakerEDU Shied for Vietduino qua '''Port A1'''.
#Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port).
#Nạp chương trình mẫu vào mạch Vietduino Uno.
#Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.

=== Kết quả: ===
...pic

==Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator==
===Phần cứng cần chuẩn bị:===
* [[Cảm biến chất lượng không khí MKE-S09 MQ-135 Air Quality Sensor]]
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Creator]] 
* Cáp USB để nạp chương trình và cấp nguồn
===Phần mềm cần chuẩn bị:===
*Tải và cài đặt phần mềm mBlock theo [[Giới thiệu và hướng dẫn cài đặt phần mềm mBlock|hướng dẫn.]]
*Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn]].
*Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm mBlock|hướng dẫn.]]
===Chương trình mẫu:===

# Trước khi bắt đầu, mạch MakerEdu Creator sẽ đợi 1 phút, để cảm biến có thời gian khởi động làm nóng.
# Sau đó, mạch MakerEdu Creator đọc liên tục giá trị Analog từ cảm biến chất lượng không khí, với chu kỳ mỗi 0,5s.
# Gửi thông tin giá trị lên màn hình LCD, dưới đơn vị (%).

<u>'''Blocks'''</u>

[[File:MBlock S09.PNG|border|700x700px]]

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEdu Creator
!Devices
|-
|Port A1
|Cảm Biến Chất Lượng Không Khí MKE-S09 MQ-135 Air Quality Sensor
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}
===Các bước tiến hành:===
#Kết nối Cảm Biến Chất Lượng Không Khí MKE-S09 với mạch MakerEdu Creator qua '''Port A1'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEdu Creator qua '''Port I2C'''.
#Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
#Nạp chương trình mẫu vào mạch MakerEdu Creator.
#Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.
===Kết quả:===
...pic

==Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bit==

===Phần cứng cần chuẩn bị:===

* Cảm biến chất lượng không khí MKE-S09 MQ-135 Air Quality Sensor
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Shield for Micro:bit]]
* Bo mạch Micro:Bit
* Cáp USB để nạp chương trình và cấp nguồn

===Phần mềm cần chuẩn bị:===
*Khởi động phần mềm MakeCode theo [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|hướng dẫn]].
*Cài đặt Extension MakerEdu Hardware trên MadeCode và tham khảo các khối chức năng theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm MakeCode|hướng dẫn]].
*Tham khảo cách kết nối và nạp chương trình cho Micro:bit [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên máy tính với phần mềm MakeCode|trên máy tính]] hoặc [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên điện thoại, máy tính bảng với phần mềm MakeCode|điện thoại, máy tính bảng.]]

===Chương trình mẫu:===

# Khi mới khởi động, Micro:Bit sẽ đợi khoảng 1 phút, để cho cảm biến có thời gian làm nóng.
# Sau đó, Micro:bit đọc liên tục giá trị Analog từ cảm biến khí chất lượng không khí, với chu kỳ mỗi 0,01s.
# Rồi đổi giá trị sang thang (%) tương ứng, để gửi giá trị đó qua cổng Serial.
# Bạn có thể mở mục "Show Data (Device)" để xem trên máy tính.
# Bên cạnh Micro:bit cũng gửi giá trị (%) lên màn hình LCD, với tần suất thấp hơn mỗi 0,5s.

'''<u>Blocks</u> [ on start ]'''

[[File:MakeCode_S09_1.PNG|border|frameless|1000x1000px]]

'''<u>Blocks</u> [ every (ms) ] & [ forever ]'''

[[File:MakeCode_S09_2.PNG|border|frameless|1000x1000px]]

{{Tr-Done
|name=Tip:
|value=Các dòng cảm biến MQ này khi để ở môi trường không khí bên ngoài một thời gian lâu không hoạt động.<br>Phần lõi cảm biến sẽ bị '''oxy hóa''', dẫn đến việc đọc giá trị bị sai lệch.<br>Khi gặp trường hợp này, các bạn cần cấp nguồn cho cảm biến hoạt động liên tục (nên khoảng hơn 5 phút hơn), để cảm biến tự làm nóng hồi phục dần độ chính xác.
}}

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

// Cho đếm ngược (60s), chờ cảm biến làm nóng xong
let wait = 60
lcd.displayText("Pls, wait in", 1, 1)
for (let index = 0; index < 60; index++) {
  // Cho hiển thị tiêu đề trước
  lcd.displayText("" + wait + "s ", 14, 1)
  basic.pause(1000)
  wait += -1
}

// Xóa toàn bộ nội dung trên LCD
lcd.clearScreen()
// Cho hiển thị tiêu đề trước
lcd.displayText("Air Quality", 1, 1)
lcd.displayText("[MQ135] " + lcd.displaySymbol(lcd.Symbols.sym02), 1, 2)

// Cho hiển thị giá trị (%) của cảm biến trên LCD mỗi 0.5s
loops.everyInterval(500, function () {
  lcd.displayText("" + dataPercent + "%  ", 11, 2)
})

basic.forever(function () {
  // Đọc giá trị Analog của cảm biến và đổi ra thang (%)
  dataAnalog = pins.analogReadPin(AnalogPin.P0)
  dataPercent = Math.round(Math.map(dataAnalog, 0, 1023, 0, 100))

  // Gửi giá trị (%) của cảm biến lên Serial
  serial.writeLine("" + (dataPercent))

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
|Cảm Biến Chất Lượng Không Khí MKE-S09 MQ-135 Air Quality Sensor
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}

===Các bước tiến hành:===
#Kết nối Cảm Biến Chất Lượng Không Khí MKE-S09 với mạch MakerEDU Shield For Micro:Bit qua '''Port P0'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEDU Shield For Micro:Bit qua '''Port I2C'''.
# Kết nối Micro:bit với mạch MakerEdu Shield for Micro:bit
# Nạp chương trình mẫu vào mạch Micro:Bit.
# Nhấn nút Reset trên mạch Micro:Bit để bắt đầu chạy chương trình.

===Kết quả:===
...pic

==Nhà phân phối==
Có thể mua Cảm biến chất lượng không khí MKE-S09 MQ-135 Air Quality Sensor tại các nhà phân phối sau:
* [https://hshop.vn/products/cam-bien-chat-luong-khong-khi-mkl-s09-mq-135-air-quality-sensor Hshop.vn - Điện tử & Robot.]
[[Category:Sensor]]
