[[image:mkl-s04_ir_infared_flame_sensor.jpg|thumb|401x401px|MKE-S04 IR infared flame sensor|link=Special:FilePath/mkl-s04_ir_infared_flame_sensor.jpg]]
==Giới thiệu==
Cảm biến lửa MKE-S04 IR infrared flame sensor được sử dụng để phát hiện lửa bằng tia hồng ngoại (IR-Infrared) phát ra trong ngọn lửa, thích hợp với các ứng dụng: xe chữa cháy tự hành, báo cháy,..., cảm biến cũng có thể sử dụng để đo cường độ tia hồng ngoại của môi trường.

Cảm biến lửa MKE-S04 IR infrared flame sensor trả ra giá trị điện áp Analog tuyến tính tương ứng với cường độ ánh sáng hồng ngoại (IR-Infrared) giúp bạn có thể ghi nhận và xử lý thông tin một cách chính xác nhất, ngoài ra cảm biến còn được bổ sung các thiết kế ổn định, chống nhiễu.

Cảm biến lửa MKE-S04 IR infrared flame sensor thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.
== Nguyên lý hoạt động==
Cảm biến sử dụng mắt thu hồng ngoại (IR-Infrared Diode) là một loại Photo Diode với khả năng nhận biết ánh sáng hồng ngoại của môi trường (không bị ảnh hưởng bởi các nguồn ánh sáng khác), từ đó có thể nhận biết được ánh sáng hồng ngoại phát ra từ ngọn lửa (các vật thể phát nhiệt thường sẽ phát ra tia hồng ngoại).
Khi mắt thu hồng ngoại (IR-Infrared) nhận biết được ánh sáng hồng ngoại từ ngọn lửa phát ra thì điện trở (độ dẫn điện) của mắt thu sẽ thay đổi theo cường độ của ánh sáng hồng ngoại, để chuyển giá trị điện trở thành điện áp để có thể đọc bằng bộ chuyển đổi ADC (Analog to Digital Converter) của mạch xử lý ta mắc mạch cầu phân áp như sau:
[[File:Mkl-s04 ir flame sensor.jpg|alt=Sơ đồ mạch chuyển giá trị điện trở thành điện áp.|none|thumb|426x426px|Sơ đồ mạch chuyển giá trị điện trở thành điện áp.]]

'''Diễn giải các giá trị:'''
*VCC: điện áp cấp nguồn cho cảm biến.
* RS: Giá trị điện trở của IR Diode.
* R2: Điện trở tạo thành cấu trúc cầu phân áp với RS, có giá trị xác định theo khuyến nghị của nhà sản xuất.
*Vout: Điện áp đầu ra thay đổi theo giá trị của RS.
Ta thấy theo công thức trong hình giá trị Vout sẽ thay đổi theo giá trị của điện trở RS, mà RS sẽ thay đổi theo cường độ ánh sáng hồng ngoại, khi đó dùng mạch xử lý để đo Vout ta xác định được cường độ ánh sáng hồng ngoại phát ra từ ngọn lửa tại thời điểm đo.
==Thông số kỹ thuật==
*Điện áp hoạt động: 5VDC
*Chuẩn giao tiếp: Analog
*Điện áp giao tiếp: 0~3.3VDC
* Phát hiện ánh sáng hồng ngoại từ ngọn lửa bằng mắt thu hồng ngoại (IR-Infrared Diode).
* Sử dụng trực tiếp an toàn với các board mạch giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
* Bổ sung thêm các thiết kế ổn định, chống nhiễu.
* Chuẩn kết nối: connector XH2.54 3Pins
* Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
{{kxnKichThuocFrame_A
|name=MKL-S04 IR infrared flame sensor dimension
}}
==Các chân tín hiệu==
[[image:mkl-s04_ir_infared_flame_sensor_back.jpg|thumb|393x393px|MKE-S04 IR infared flame sensor back|link=Special:FilePath/mkl-s04_ir_infared_flame_sensor_back.jpg]]
{| class="wikitable" border="1"
|-
!MKE-S04
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
*Cảm biến lửa MKE-S04 IR infrared flame sensor
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
  Serial.print("Flame Detection in %: ");
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
|Cảm biến lửa MKE-S04 IR infrared flame sensor
|}

=== Các bước tiến hành: ===
#Kết nối mạch Vietduino Uno với mạch MakerEDU Shield for Vietduino.
#Kết nối Cảm Biến Lửa MKE-S04 với mạch MakerEDU Shied for Vietduino qua '''Port A1'''.
#Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port).
#Nạp chương trình mẫu vào mạch Vietduino Uno.
#Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.
=== Kết quả: ===
==Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator==
===Phần cứng cần chuẩn bị:===
* Cảm biến lửa MKE-S04 IR infrared flame sensor
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Creator]] 
* Cáp USB để nạp chương trình và cấp nguồn
===Phần mềm cần chuẩn bị:===
*Tải và cài đặt phần mềm mBlock theo [[Giới thiệu và hướng dẫn cài đặt phần mềm mBlock|hướng dẫn.]]
*Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn]].
*Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm mBlock|hướng dẫn.]]
===Chương trình mẫu:===

# Mạch MakerEdu Creator đọc liên tục giá trị Analog từ cảm biến lửa, với chu kỳ mỗi 0,5s.
# Gửi thông tin giá trị lên màn hình LCD, dưới đơn vị (%).

<u>'''Blocks'''</u>

[[File:MBlock S04.PNG|border|700x700px]]

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEdu Creator
!Devices
|-
|Port A1
|Cảm Biến Lửa MKE-S04 IR Infrared Flame Sensor
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}
===Các bước tiến hành:===
#Kết nối Cảm Biến Lửa MKE-S04 với mạch MakerEdu Creator qua '''Port A1'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEdu Creator qua '''Port I2C'''.
#Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
#Nạp chương trình mẫu vào mạch MakerEdu Creator.
#Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.
===Kết quả:===
==Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bit ==

===Phần cứng cần chuẩn bị:===

* Cảm biến lửa MKE-S04 IR infrared flame sensor
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Shield for Micro:bit]]
* Bo mạch Micro:Bit
* Cáp USB để nạp chương trình và cấp nguồn

===Phần mềm cần chuẩn bị:===
*Khởi động phần mềm MakeCode theo [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|hướng dẫn]].
*Cài đặt Extension MakerEdu Hardware trên MadeCode và tham khảo các khối chức năng theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm MakeCode|hướng dẫn]].
*Tham khảo cách kết nối và nạp chương trình cho Micro:bit [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên máy tính với phần mềm MakeCode|trên máy tính]] hoặc [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên điện thoại, máy tính bảng với phần mềm MakeCode|điện thoại, máy tính bảng.]]

===Chương trình mẫu:===

# Micro:Bit đọc liên tục giá trị Analog từ cảm biến lửa, với chu kỳ mỗi 0,5s.
# Sau đó Micro:Bit đổi giá trị sang thang (%) tương ứng, để hiển thị lên LCD.
# Micro:Bit cũng gửi giá trị đó qua cổng Serial, bạn có thể mở mục "Show Data (Device)" để xem trên máy tính.

<u>'''Blocks'''</u>

[[File:MakeCode_S04.png|border|frameless|1000x1000px]]

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
lcd.displayText("Flame Detector", 1, 1)
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
|Cảm Biến Lửa MKE-S04 IR Infrared Flame Sensor
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}

===Các bước tiến hành:===
#Kết nối Cảm Biến Lửa MKE-S04 với mạch MakerEDU Shield For Micro:Bit qua '''Port P0'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEDU Shield For Micro:Bit qua '''Port I2C'''.
# Kết nối Micro:bit với mạch MakerEdu Shield for Micro:bit
# Nạp chương trình mẫu vào mạch Micro:Bit.
# Nhấn nút Reset trên mạch Micro:Bit để bắt đầu chạy chương trình.

===Kết quả:===
==Nhà phân phối==
Có thể mua Cảm biến lửa MKE-S04 IR infrared flame sensor tại các nhà phân phối sau:
* [https://hshop.vn/products/cam-bien-lua-mkl-s04-ir-infrared-flame-sensor Hshop.vn - Điện tử & Robot.]
[[Category:Sensor]]
