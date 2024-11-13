[[image:mkl-s14_dht11_temperature_humidity_sensor.jpg|thumb|332x332px|MKE-S14 temperature and humidity sensor|link=Special:FilePath/mkl-s14_dht11_temperature_humidity_sensor.jpg|alt=MKL-S14 temperature and humidity sensor]]
==Giới thiệu==
Cảm biến độ ẩm nhiệt độ MKE-S14 DHT11 temperature and humidity sensor được sử dụng rất phổ biến hiện nay để đo độ ẩm và nhiệt độ của môi trường không khí, cảm biến sử dụng giao tiếp 1-Wire với chỉ duy nhất 1 dây tín hiệu Digital, Xin lưu ý chỉ sử dụng cảm biến trong môi trường độ ẩm thuần là hơi nước, các môi trường đặc biệt ủ kín như ủ tỏi đen, ủ yếm khí...sẽ sinh ra nấm và vi khuẩn bám lên bề mặt cảm biến làm hư hỏng cảm biến.

Cảm biến độ ẩm nhiệt độ MKE-S14 DHT11 temperature and humidity sensor thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.

== Thông số kỹ thuật ==
* Cảm biến sử dụng: DHT11 temperature and humidity sensor, [https://www.mediafire.com/file/xbr3gnj26f045lo/&#x5B;MakerLab.vn&#x5D;+DHT11_Datasheet.pdf/file datasheet.]
*Điện áp hoạt động: 5VDC
*Chuẩn giao tiếp: Digital 1-Wire
*Điện áp giao tiếp: TTL 3.3/5VDC
* Dòng sử dụng: 2.5mA max (khi truyền dữ liệu).
*Khoảng đo độ ẩm: 20 - 90% RH (sai số 5% RH)
* Khoảng đo nhiệt độ: 0-50°C (sai số 2°C).
*Tần số lấy mẫu tối đa: 1Hz (1 giây 1 lần)
* Sử dụng trực tiếp an toàn với các board mạch giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
* Bổ sung thêm các thiết kế ổn định, chống nhiễu.
* Chuẩn kết nối: connector XH2.54 3Pins
* Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
{{kxnKichThuocFrame_A
|name=MKL-S14 temperature and humidity sensor dimension
}}
==Các chân tín hiệu==
[[image:mkl-s14_dht11_temperature_humidity_sensor_back.jpg|thumb|310x310px|MKE-S14 temperature and humidity sensor back|link=Special:FilePath/mkl-s14_dht11_temperature_humidity_sensor_back.jpg|alt=MKL-S14 temperature and humidity sensor back]]
{| class="wikitable" border="1"
|-
!MKE-S14
!Ghi chú
|-
|GND
|Chân cấp nguồn âm 0VDC
|-
| 5V
|Chân cấp nguồn dương 5VDC
|-
|SIG
|Chân tín hiệu Digital 1-Wire
|}
==Hướng dẫn sử dụng với phần mềm Arduino và Vietduino==

===Phần cứng cần chuẩn bị:===
*Cảm biến độ ẩm nhiệt độ MKE-S14 DHT11 temperature and humidity sensor
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
* Tải và cài đặt bộ thư viện [https://github.com/makerlabvn/DHT-sensor-library DHT-sensor-library] theo [[Cách cài đặt các thư viện phần cứng Arduino Library|hướng dẫn.]]

=== Chương trình mẫu: ===
<source lang="c++">
// Thêm bộ thư viện cảm biến DHT11.
// Add the DHT11 sensor library.
#include "DHT.h"

// Chọn chân đọc cảm biến.
// Select the pin to read the sensor.
#define SIG_PIN 11

// Cấu hình chân kết nối tín hiệu cho cảm biến DHT11.
// Configure the signal connection pins for the DHT11 sensor.
DHT dht(SIG_PIN, DHT11);

void setup()
{
  // Khởi động kết nối Serial UART ở tốc độ 9600 để truyền dữ liệu lên máy tính.
  // Start the Serial UART connection at 9600 to transfer data to the computer.
  Serial.begin(9600);

  // Khởi động thư viện.
  // Start up the library.
  dht.begin();
}

void loop()
{
  // Transmit the measured distance of the ultrasonic sensor to the computer.
  // Truyền khoảng cách đo được của cảm biến siêu âm lên máy tính.
  Serial.print("Humidity: ");
  Serial.print(dht.readHumidity(), 2);
  Serial.print("% - Temperature: ");
  Serial.print(dht.readTemperature(), 2);
  Serial.println("°C");

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
|Port D11
|D11
|Cảm biến độ ẩm nhiệt độ MKE-S14 DHT11 temperature and humidity sensor
|}

=== Các bước tiến hành: ===
#Kết nối mạch Vietduino Uno với mạch MakerEDU Shield for Vietduino.
#Kết nối Cảm Biến Độ Ẩm Nhiệt Độ MKE-S14 với mạch MakerEDU Shied for Vietduino qua '''Port D11'''.
#Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port).
#Nạp chương trình mẫu vào mạch Vietduino Uno.
#Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.

=== Kết quả: ===
...pic

==Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator==
===Phần cứng cần chuẩn bị:===
* Cảm biến độ ẩm nhiệt độ MKE-S14 DHT11 temperature and humidity sensor
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Creator]] 
* Cáp USB để nạp chương trình và cấp nguồn
===Phần mềm cần chuẩn bị:===
*Tải và cài đặt phần mềm mBlock theo [[Giới thiệu và hướng dẫn cài đặt phần mềm mBlock|hướng dẫn.]]
*Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn]].
*Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm mBlock|hướng dẫn.]]
===Chương trình mẫu:===

# Mạch MakerEdu Creator đọc liên tục giá trị từ cảm biến DHT11, với chu kỳ mỗi 0,5s.
# Gửi thông tin giá trị nhiệt độ (°C) và độ ẩm (%) lên màn hình LCD.

<u>'''Blocks'''</u>

[[File:MBlock S14.PNG|border|700x700px]]

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEdu Creator
!Devices
|-
|Port D11
|Cảm Biến Độ Ẩm Nhiệt Độ MKE-S14 DHT11 Temperature And Humidity Sensor
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}
===Các bước tiến hành:===
#Kết nối Cảm Biến Độ Ẩm Nhiệt Độ MKE-S14 với mạch MakerEdu Creator qua '''Port D11'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEdu Creator qua '''Port I2C'''.
#Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
#Nạp chương trình mẫu vào mạch MakerEdu Creator.
#Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.
===Kết quả:===
...pic

==Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bit==

===Phần cứng cần chuẩn bị:===

* [[Cảm biến độ ẩm nhiệt độ MKE-S14 DHT11 temperature and humidity sensor]]
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Shield for Micro:bit]]
* Bo mạch Micro:Bit
* Cáp USB để nạp chương trình và cấp nguồn

===Phần mềm cần chuẩn bị:===
*Khởi động phần mềm MakeCode theo [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|hướng dẫn]].
*Cài đặt Extension MakerEdu Hardware trên MadeCode và tham khảo các khối chức năng theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm MakeCode|hướng dẫn]].
*Tham khảo cách kết nối và nạp chương trình cho Micro:bit [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên máy tính với phần mềm MakeCode|trên máy tính]] hoặc [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên điện thoại, máy tính bảng với phần mềm MakeCode|điện thoại, máy tính bảng.]]

===Chương trình mẫu:===

# Micro:Bit đọc liên tục giá trị nhiệt độ (°C) và độ ẩm (%) trong môi trường từ cảm biến DHT11, với chu kỳ mỗi 0,5s.
# Hiển thị giá trị lên màn hình LCD.

<u>'''Blocks'''</u>

[[File:MakeCode_S14.png|border|frameless|1000x1000px]]

'''<u>Javascript</u>'''

<source lang="typescript">
// Xóa toàn bộ nội dung trên LCD (nếu có)
lcd.clearScreen()

// Cho hiển thị tiêu đề "Nhiệt độ"
lcd.displayText("Temp:", 1, 1)

// Cho hiển thị tiêu đề "Độ ẩm"
lcd.displayText("Humi:", 1, 2)

basic.forever(function () {
  // Đọc giá trị nhiệt độ hiện tại từ cảm biến DHT11, với đơn vị (°C)
  // Rồi cho hiển thị giá trị đó trên LCD sau tiêu đề "Nhiệt độ"
  lcd.displayText("" + dht11.readTemperature(dht11.TemperatureType.Celsius, dht11.PinKit.P0) + lcd.displaySymbol(lcd.Symbols.sym07) + "C   ", 7, 1)

  // Đọc giá trị độ ẩm hiện tại từ cảm biến DHT, với đơn vị (%)
  // Rồi cho hiển thị giá trị đó trên LCD sau tiêu đề "Độ ẩm"
  lcd.displayText("" + dht11.readHumidity(dht11.PinKit.P0) + "%   ", 7, 2)

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
|Cảm Biến Độ Ẩm Nhiệt Độ MKE-S14 DHT11 Temperature And Humidity Sensor
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}

===Các bước tiến hành:===
#Kết nối Cảm Biến Độ Ẩm Nhiệt Độ MKE-S14 với mạch MakerEDU Shield For Micro:Bit qua '''Port P0'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEDU Shield For Micro:Bit qua '''Port I2C'''.
# Kết nối Micro:bit với mạch MakerEdu Shield for Micro:bit
# Nạp chương trình mẫu vào mạch Micro:Bit.
# Nhấn nút Reset trên mạch Micro:Bit để bắt đầu chạy chương trình.

===Kết quả:===
...pic

==Nhà phân phối==
Có thể mua Cảm biến độ ẩm nhiệt độ MKE-S14 DHT11 temperature and humidity sensor tại các nhà phân phối sau:
* [https://hshop.vn/products/cam-bien-do-am-nhiet-do-mkl-s14-dht11-temperature-and-humidity-sensor Hshop.vn - Điện tử & Robot.]
[[Category:Sensor]]
