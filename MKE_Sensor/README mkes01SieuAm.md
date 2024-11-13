[[image:mkl-us01_ultra_sonic_distance_sensor.jpg|thumb|419x419px|MKE-S01 Ultrasonic Distance Sensor|link=Special:FilePath/mkl-us01_ultra_sonic_distance_sensor.jpg|alt=]]
==Giới thiệu==
Cảm biến siêu âm MKE-S01 Ultrasonic Distance Sensor sử dụng sóng siêu âm để đo khoảng cách đến vật cản từ 3~200cm, cảm biến sử dụng IC xử lý, thạch anh chất lượng tốt cho độ bền, độ ổn định và độ chính xác cao, thích hợp để làm các loại robot tránh vật cản, chống trộm, đo khoảng cách,...

Cảm biến siêu âm MKE-S01 Ultrasonic Distance Sensor thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.
==Nguyên lý hoạt động==
Cảm biến siêu âm đo khoảng cách đến vật cản bằng cách phát sóng siêu âm từ mắt phát T (Transmitter) đến vật cản, sóng siêu âm khi đó sẽ bị phản xạ lại và truyền tới mắt thu R (Receiver), ghi nhận khoảng thời gian '''t''' quá trình này xảy ra bằng mạch xử lý kết hợp với vận tốc xác định của sóng siêu âm ta có thể tính được khoảng cách tương đối chính xác đến vật cản theo công thức: 

'''Khoảng cách đến vật cản L = (khoảng thời gian t * vận tốc sóng siêu âm) / 2'''
[[File:Ultrasonic sensor mke-s01 copy.jpg|alt=Minh họa sóng siêu âm từ phát phát T (Transmitter) đến vật cản bị phản xạ lại và truyền tới mắt thu R (Receiver).|none|thumb|500x500px|Minh họa sóng siêu âm từ phát phát T (Transmitter) đến vật cản bị phản xạ lại và truyền tới mắt thu R (Receiver).]]
Để tăng độ chính xác và giảm nhiễu, sóng siêu âm sẽ được mắt phát T (Transmitter) phát ra theo tần số chuyên biệt để không bị nhiễu với các loại sóng khác của môi trường, phương pháp đo khoảng cách bằng cảm biến siêu âm tương đối chính xác và ổn định, tuy nhiên vẫn có một nhược điểm của phương pháp này là phụ thuộc vào hình dạng của vật thể phản xạ, vật thể có bề mặt không phẳng sẽ làm ảnh hưởng đến độ phản xạ của sóng siêu âm dẫn đến kết quả đo kém chính xác.
==Thông số kỹ thuật==
*Điện áp hoạt động: 5VDC
*Chuẩn giao tiếp: Digital
*Điện áp giao tiếp: TTL 3.3VDC / 5VDC
*Dòng điện hoạt động: 65mA
*Tần số hoạt động: 40Khz
*Khoảng cách đo được: 3-200cm
*Góc quét: 15°
*Tín hiệu ngõ vào Trigger: 10μs TTL pulse
*Sử dụng trực tiếp an toàn với các board mạch giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
*Bổ sung thêm các thiết kế ổn định, chống nhiễu.
*Chuẩn kết nối: connector XH2.54 4Pins
*Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
== Kích thước==
[[File:Kt_ultrasonic.JPG|alt=MKL-US01 ultra sonic distance sensor dimension|none|thumb|400x400px|MKE-S01 Ultrasonic Distance Sensor dimension]]
==Các chân tín hiệu==
[[image:mkl-us01_ultra_sonic_distance_sensor_back.jpg|thumb|413x413px|MKE-S01 Ultrasonic Distance Sensor back|link=Special:FilePath/mkl-us01_ultra_sonic_distance_sensor_back.jpg|alt=]]
{| class="wikitable" border="1"
|-
!MKE-S01
!Ghi chú
|-
|GND
|Chân cấp nguồn âm 0VDC
|-
|5V
|Chân cấp nguồn dương 5VDC
|-
|TRIG
|Chân tín hiệu ngõ vào Trigger (Input: 3.3~5VDC)
|-
|ECHO
|Chân tín hiệu ngõ ra Echo (Output: 3.3VDC)
|-
|}
==Hướng dẫn sử dụng với phần mềm Arduino và Vietduino==
===Phần cứng cần chuẩn bị:===
*Cảm biến siêu âm MKE-S01 Ultrasonic Distance Sensor
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
* Tải và cài đặt [https://github.com/makerlabvn/mke-s01-ultrasonic-distance-sensor-lib bộ thư viện cảm biến siêu âm] theo [[Cách cài đặt các thư viện phần cứng Arduino Library|hướng dẫn.]]
=== Chương trình mẫu: ===
<source lang="c++">
// Thêm bộ thư viện cảm biến siêu âm.
// Add the ultrasonic sensor library.
#include <HCSR04.h>

// Chọn chân đọc cảm biến.
// Select the pin to read the sensor.
#define ECHO_PIN 12
#define TRIG_PIN 13

// Cấu hình chân kết nối tín hiệu cho cảm biến siêu âm.
// Configure the signal connection pins for the ultrasonic sensor.
HCSR04 ultra(TRIG_PIN, ECHO_PIN);

void setup()
{
  // Khởi động kết nối Serial UART ở tốc độ 9600 để truyền dữ liệu lên máy tính.
  // Start the Serial UART connection at 9600 to transfer data to the computer.
  Serial.begin(9600);
}

void loop()
{
  // Truyền khoảng cách đo được của cảm biến siêu âm lên máy tính.
  // Transmit the measured distance of the ultrasonic sensor to the computer.
  Serial.print("Distance in cm: ");
  Serial.println(ultra.dist());

  // Chờ 60ms mỗi lần đọc để tránh nhiễu tín hiệu.
  // Wait 60ms per read to avoid signal interference.
  delay(60);
}
</source>

=== Sơ đồ kết nối: ===
{| class="wikitable"
!MakerEdu Shield for Vietduino
! style="text-align:left;" |Arduino / Vietduino
!Cảm biến siêu âm MKE-S01 Ultrasonic Distance Sensor
|-
| rowspan="2" |Port D12,13
|D12
|ECHO
|-
|D13
|TRIG
|}
=== Các bước tiến hành: ===
#Kết nối  mạch Vietduino Uno với mạch MakerEDU Shield for Vietduino.
#Kết nối Cảm Biến Siêu Âm MKE-S01 với mạch MakerEDU Shied for Vietduino qua '''Port D12,13'''.
#Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port) theo [[Cách cài đặt Driver cho mạch Arduino / Arduino Compatible|hướng dẫn]].
#Nạp chương trình mẫu vào mạch Vietduino Uno.
#Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.
=== Kết quả: ===
Mở Serial Monitor trên phần mềm Arduino với tốc độ 9600 để thấy chương trình hoạt động:[[File:MKE-S01 Ultrasonic Distance Sensor.jpg|none|thumb|1100x1100px|Ultrasonic sensor transmits data to Arduino Serial Monitor]]

==Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator==
===Phần cứng cần chuẩn bị:===
* Cảm biến siêu âm MKE-S01 Ultrasonic Distance Sensor
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Creator]] 
* Cáp USB để nạp chương trình và cấp nguồn
===Phần mềm cần chuẩn bị:===
*Tải và cài đặt phần mềm mBlock theo [[Giới thiệu và hướng dẫn cài đặt phần mềm mBlock|hướng dẫn.]]
*Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn]].
*Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm mBlock|hướng dẫn.]]
===Chương trình mẫu:===

# Mạch MakerEdu Creator đọc liên tục giá trị từ cảm biến siêu âm, với chu kỳ mỗi 0,5s.
# Gửi thông tin giá trị lên màn hình LCD, dưới đơn vị (cm).

<u>'''Blocks'''</u>

[[File:MBlock S01.PNG|border|700x700px]]

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEdu Creator
!Devices
|-
|Port D3+D2
|Cảm Biến Siêu Âm MKE-S01 Ultrasonic Distance Sensor
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}
===Các bước tiến hành:===
#Kết nối Cảm Biến Siêu Âm MKE-S01 với mạch MakerEdu Creator qua '''Port D3+D2'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEdu Creator qua '''Port I2C'''.
#Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
#Nạp chương trình mẫu vào mạch MakerEdu Creator.
#Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.
===Kết quả:===
==Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bit==

===Phần cứng cần chuẩn bị:===

* Cảm biến siêu âm MKE-S01 Ultrasonic Distance Sensor
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Shield for Micro:bit]]
* Bo mạch Micro:Bit
* Cáp USB để nạp chương trình và cấp nguồn

===Phần mềm cần chuẩn bị:===
*Khởi động phần mềm MakeCode theo [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|hướng dẫn]].
*Cài đặt Extension MakerEdu Hardware trên MadeCode và tham khảo các khối chức năng theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm MakeCode|hướng dẫn]].
*Tham khảo cách kết nối và nạp chương trình cho Micro:bit [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên máy tính với phần mềm MakeCode|trên máy tính]] hoặc [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên điện thoại, máy tính bảng với phần mềm MakeCode|điện thoại, máy tính bảng.]]

===Chương trình mẫu:===

* Micro:Bit đọc liên tục giá trị khoảng cách từ cảm biến siêu âm, với chu kỳ mỗi 0,5s.
* Sau đó cho hiển thị giá trị lên màn hình LCD, với đơn vị (cm).

<u>'''Blocks'''</u>

[[File:MakeCode_S01.png|border|frameless|1000x1000px]]

'''<u>Javascript</u>'''

<source lang="typescript">
// Xóa toàn bộ nội dung trên LCD (nếu có)
lcd.clearScreen()

// Cho hiển thị tiêu đề "Khoảng cách"
lcd.displayText("Dist:", 1, 1)

basic.forever(function () {
  // Đọc giá trị khoảng cách hiện tại từ cảm biến siêu âm, với đơn vị (cm)
  // Rồi cho hiển thị giá trị đó trên LCD sau tiêu đề "Khoảng cách"
  lcd.displayText("" + ultraSonic.readDistance(ultraSonic.PingUnit.Centimeters, ultraSonic.PinKit.Port1) + " cm   ", 7, 1)

  // Dừng 0.5s
  basic.pause(500)
})
</source>

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEDU Shield for Micro:bit
!Devices
|-
|Port P2+P8
|Cảm Biến Siêu Âm MKE-S01 Ultrasonic Distance Sensor
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}

===Các bước tiến hành:===
#Kết nối Cảm Biến Siêu Âm MKE-S01 với mạch MakerEDU Shield For Micro:Bit qua '''Port P2+P8'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEDU Shield For Micro:Bit qua '''Port I2C'''.
#Kết nối Micro:bit với mạch MakerEdu Shield for Micro:bit
#Nạp chương trình mẫu vào mạch Micro:Bit.
#Nhấn nút Reset trên mạch Micro:Bit để bắt đầu chạy chương trình.

===Kết quả:===
==Nhà phân phối==
Có thể mua Cảm biến siêu âm MKE-S01 ultra sonic distance sensor tại các nhà phân phối sau:
*[https://hshop.vn/products/cam-bien-sieu-am-mke-s01-ultrasonic-distance-sensor Hshop.vn - Điện tử & Robot.]
[[Category:Sensor]]
