[[image:mkl-s06_sound_sensor.jpg|thumb|323x323px|MKE-S06 sound sensor|link=Special:FilePath/mkl-s06_sound_sensor.jpg|alt=]]
==Giới thiệu==
Cảm biến âm thanh MKE-S06 sound sensor được sử dụng để đo cường độ âm thanh của môi trường bằng Microphone tích hợp trên cảm biến, cảm biến trả ra giá trị điện áp Analog tuyến tính tương ứng với cường độ âm thanh giúp bạn có thể ghi nhận và xử lý thông tin một cách chính xác nhất, ngoài ra cảm biến còn được bổ sung các thiết kế ổn định, chống nhiễu.

Cảm biến âm thanh MKE-S06 sound sensor thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.
==Nguyên lý hoạt động==
Cảm biến sử dụng [[wikipedia:Electret_microphone|electret microphone]] là một loại microphone điện dung để thu nhận âm thanh và chuyển thành tín hiệu điện, tín hiệu này sau đó được xử lý và khuếch đại để có thể đọc được bằng bộ chuyển đổi ADC (Analog to Digital Converter) của mạch xử lý.
==Thông số kỹ thuật==
*Điện áp hoạt động: 5VDC
*Chuẩn giao tiếp: Analog
*Điện áp giao tiếp: 0~3.3VDC
*Đo cường độ âm thanh của môi trường bằng [[wikipedia:Electret_microphone|electret microphone]].
* Sử dụng trực tiếp an toàn với các board mạch giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
* Bổ sung thêm các thiết kế ổn định, chống nhiễu.
* Chuẩn kết nối: connector XH2.54 3Pins
* Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
{{kxnKichThuocFrame_A
|name=MKL-S06 sound sensor dimension
}}
==Các chân tín hiệu==
[[image:mkl-s06_sound_sensor_back.jpg|thumb|318x318px|MKE-S06 sound sensor back|link=Special:FilePath/mkl-s06_sound_sensor_back.jpg]]
{| class="wikitable" border="1"
|-
!MKE-S06
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
*Cảm biến âm thanh MKE-S06 sound sensor
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

// Số lần lấy mẫu.
// Number of sampling times.
#define SAMPLES 25

// Lưu giá trị Analog đọc từ cảm biến.
// Stores the Analog value read from the sensor.
float value;

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
  /**
   * Các bước tính giá trị trung bình của cảm biến
   * 1. Xóa giá trị trong biến về 0
   * 2. Cộng tổng các mẫu đo lại
   * 3. Chia số mẫu để lấy giá trị trung bình
   */
  value = 0;
  for (int i = 0; i < SAMPLES; i++)
  {
    value += analogRead(SENSOR_PIN);

    // Chờ 0,001s mới đo lại.
    // Wait 0,001s to measure again.
    delay(1);
  }
  value = value / SAMPLES;

  // Chuyển đổi sang thang đo (%).
  // Convert to scale (%).
  percent = map(value, 0, 676, -100, 100);

  // Truyền giá trị đo được của cảm biến lên máy tính.
  // Transmit the measured value of the sensor to the computer.
  Serial.print("Noise Detector in %: ");
  Serial.println(percent);
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
|Cảm biến âm thanh MKE-S06 sound sensor
|}

=== Các bước tiến hành: ===
#Kết nối mạch Vietduino Uno với mạch MakerEDU Shield for Vietduino.
#Kết nối Cảm Biến Âm Thanh MKE-S06 với mạch MakerEDU Shied for Vietduino qua '''Port A1'''.
#Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port).
#Nạp chương trình mẫu vào mạch Vietduino Uno.
#Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.

=== Kết quả: ===
==Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator==
===Phần cứng cần chuẩn bị:===
* Cảm biến âm thanh MKE-S06 sound sensor
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Creator]] 
* Cáp USB để nạp chương trình và cấp nguồn
===Phần mềm cần chuẩn bị:===
*Tải và cài đặt phần mềm mBlock theo [[Giới thiệu và hướng dẫn cài đặt phần mềm mBlock|hướng dẫn.]]
*Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn]].
*Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm mBlock|hướng dẫn.]]
===Chương trình mẫu:===

# Mạch MakerEdu Creator đọc liên tục giá trị Analog từ cảm biến âm thanh, với tần suất mỗi 0,001s (1ms).
# Cứ mỗi 25 lần đọc, mạch MakerEdu Creator tính ra giá trị trung bình trong khoảng đó, nghĩa là bạn sẽ có được 1 giá trị Analog ổn định sau mỗi 0,025s (25ms), điều này giúp mạch MakerEdu Creator luôn có được giá trị mới nhất, gần như tức thời từ cảm biến.
# Gửi thông tin giá trị lên màn hình LCD, dưới đơn vị (%) với chu kỳ mỗi 0,25s.

<u>'''Blocks'''</u>

[[File:MBlock S06.PNG|border|700x700px]]

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEdu Creator
!Devices
|-
|Port A1
|Cảm Biến Âm Thanh MKE-S06 Sound Sensor
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}
===Các bước tiến hành:===
#Kết nối Cảm Biến Âm Thanh MKE-S06 với mạch MakerEdu Creator qua '''Port A1'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEdu Creator qua '''Port I2C'''.
#Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
#Nạp chương trình mẫu vào mạch MakerEdu Creator.
#Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.
===Kết quả:===
...pic

==Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bit==

===Phần cứng cần chuẩn bị:===

* [[Cảm biến âm thanh MKE-S06 sound sensor]]
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Shield for Micro:bit]]
* Bo mạch Micro:Bit
* Cáp USB để nạp chương trình và cấp nguồn

===Phần mềm cần chuẩn bị:===
*Khởi động phần mềm MakeCode theo [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|hướng dẫn]].
*Cài đặt Extension MakerEdu Hardware trên MadeCode và tham khảo các khối chức năng theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm MakeCode|hướng dẫn]].
* Tham khảo cách kết nối và nạp chương trình cho Micro:bit [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên máy tính với phần mềm MakeCode|trên máy tính]] hoặc [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên điện thoại, máy tính bảng với phần mềm MakeCode|điện thoại, máy tính bảng.]]

===Chương trình mẫu:===

# Micro:Bit đọc liên tục giá trị Analog từ cảm biến âm thanh, đọc tầm 25 lần để tính giá trị trung bình cộng.
# Sau đó Micro:Bit đổi giá trị sang thang (%) tương ứng, để gửi giá trị đó qua cổng Serial. Toàn bộ quá trình này được thực hiện lại với chu kỳ mỗi 0,025s.
# Bạn có thể mở mục "Show Data (Device)" để xem trên máy tính. Bên cạnh, khoảng mỗi 0,5s Micro:Bit cũng gửi giá trị (%) hiện tại lên LCD.

'''<u>Blocks</u> [ on start ]'''

[[File:MakeCode_S06_1.png|border|frameless|1000x1000px]]

'''<u>Blocks</u> [ forever ]'''

[[File:MakeCode_S06_2.png|border|frameless|1000x1000px]]

'''<u>Blocks</u> [ every (ms) ]'''

[[File:MakeCode_S06_3.png|border|frameless|1000x1000px]]

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
lcd.displayText("Noise Detector", 1, 1)
lcd.displayText(lcd.displaySymbol(lcd.Symbols.sym02), 1, 2)

// Cho hiển thị giá trị (%) của cảm biến trên LCD, với tần suất 0.5s
loops.everyInterval(500, function () {
  lcd.displayText("" + dataPercent + "%  ", 3, 2)
})

basic.forever(function () {
  // Đọc giá trị Analog 25 lần, lấy trung bình cộng
  dataAnalog = 0
  for (let index = 0; index < 25; index++) {
    dataAnalog += pins.analogReadPin(AnalogPin.P0)
    basic.pause(1)
  }
  dataAnalog = dataAnalog / 25

  // Đọc giá trị Analog của cảm biến và đổi ra thang (%)
  dataPercent = Math.round(Math.map(dataAnalog, 0, 1023, -100, 100))
  // Gửi giá trị (%) của cảm biến lên Serial
  serial.writeLine("" + (dataPercent))

  // Dừng 0.025s
  basic.pause(25)
})
</source>

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEDU Shield for Micro:bit
!Devices
|-
|Port P0
|Cảm Biến Âm Thanh MKE-S06 Sound Sensor
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}

===Các bước tiến hành:===
#Kết nối Cảm Biến Âm Thanh MKE-S06 với mạch MakerEDU Shield For Micro:Bit qua '''Port P0'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEDU Shield For Micro:Bit qua '''Port I2C'''.
# Kết nối Micro:bit với mạch MakerEdu Shield for Micro:bit
# Nạp chương trình mẫu vào mạch Micro:Bit.
# Nhấn nút Reset trên mạch Micro:Bit để bắt đầu chạy chương trình.

===Kết quả:===
==Nhà phân phối==
Có thể mua Cảm biến âm thanh MKE-S06 sound sensor tại các nhà phân phối sau:
* [https://hshop.vn/products/cam-bien-am-thanh-mkl-s06-sound-sensor Hshop.vn - Điện tử & Robot.]
[[Category:Sensor]]
