[[image:mkl-m09_RTC_DS3231_real_time_clock_module.jpg|thumb|322x322px|MKE-M09 RTC DS1307 real time clock module|link=Special:FilePath/mkl-m09_RTC_DS3231_real_time_clock_module.jpg|alt=MKL-M09 RTC DS3231 real time clock module]]
==Giới thiệu==
Mạch thời gian thực MKE-M09 RTC DS1307 real time clock module được sử dụng để lấy dữ liệu về thời gian thực: giờ, phút, giây, thứ, ngày, tháng, năm trong các ứng dụng cần điều khiển và đồng bộ với thời gian thực tế, mạch sử dụng giao tiếp I2C nên dễ dàng kết nối và sử dụng với chỉ 2 chân giao tiếp I2C là SDA (data) và SCL (clock).

Mạch thời gian thực MKE-M09 RTC DS1307 real time clock module thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.
==Thông số kỹ thuật==
*Điện áp hoạt động: 5VDC
*Chuẩn giao tiếp: Digital I2C
*Các chân giao tiếp: SDA (Serial Data) / SCL (Serial Clock)
*Điện áp giao tiếp: TTL 3.3/5VDC
* IC thời gian thực: DS1307, [https://www.sparkfun.com/datasheets/Components/DS1307.pdf datasheet.]
*Tích hợp pin CR1220 lưu giữ thời gian khi không cấp nguồn.
* Sử dụng trực tiếp an toàn với các board mạch giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
* Bổ sung thêm các thiết kế ổn định, chống nhiễu.
* Chuẩn kết nối: Conector XH2.54 4Pins
* Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
{{kxnKichThuocFrame_A
|name=MKL-M09 RTC DS3231 real time clock module dimension
}}
==Các chân tín hiệu==
[[image:mkl-m09_RTC_DS3231_real_time_clock_module_back.jpg|thumb|309x309px|MKE-M09 RTC DS1307 real time clock module back|link=Special:FilePath/mkl-m09_RTC_DS3231_real_time_clock_module_back.jpg|alt=MKL-M09 RTC DS3231 real time clock module back]]
{| class="wikitable" border="1"
|-
!MKE-M09
!Ghi chú
|-
|GND
|Chân cấp nguồn âm 0VDC
|-
|5V
|Chân cấp nguồn dương 5VDC
|-
|SDA
|Chân tín hiệu Digital Data
|-
|SCL
|Chân tín hiệu Digital Clock
|}
==Hướng dẫn sử dụng với phần mềm Arduino và Vietduino==

===Phần cứng cần chuẩn bị:===
*Mạch thời gian thực MKE-M09 RTC DS1307 real time clock module
*[[Mạch Vietduino Uno (Arduino Uno Compatible)]]
* [[Mạch MakerEdu Shield for Vietduino]]
*Cáp USB để nạp chương trình và cấp nguồn

{{Tr-Info
|name=Lưu ý:
|value=Nếu không có mạch Vietduino Uno bạn vẫn có thể sử dụng mạch Vietduino Mega 2560, Arduino Uno, Arduino Mega 2560 hoặc các mạch phần cứng có cấu trúc các chân GPIO tương tự.
}}

=== Phần mềm cần chuẩn bị: ===
* Tải và cài đặt phần mềm Arduino theo [[Cách cài đặt phần mềm Arduino IDE|hướng dẫn.]]
* Tải và cài đặt Driver, cấu hình cho mạch Vietduino Uno trên phần mềm Arduino theo [[Cách cài đặt Driver và nạp chương trình cho mạch Arduino / Arduino Compatible|hướng dẫn.]]
* Tải và cài đặt [https://github.com/adafruit/RTClib bộ thư viện DS1307] theo [[Cách cài đặt các thư viện phần cứng Arduino Library|hướng dẫn.]]

=== Chương trình mẫu: ===
<source lang="c++">
// Thêm bộ thư viện DS1307.
// Add the DS1307 library.
#include "RTClib.h"

// Khởi tạo "RTC_DS1307".
// Initialize "RTC_DS1307".
RTC_DS1307 rtc;

// Lưu tên gọi của Thứ trong Tuần.
// Save the name of the Day of the Week.
char daysOfTheWeek[7][12] = {
    "Sun", // Chủ Nhật.
    "Mon", // Thứ 2.
    "Tue", // Thứ 3.
    "Wed", // Thứ 4.
    "Thu", // Thứ 5.
    "Fri", // Thứ 6.
    "Sat"  // Thứ 7.
};

void setup()
{
  // Khởi động kết nối Serial UART ở tốc độ 9600 để truyền dữ liệu lên máy tính.
  // Start the Serial UART connection at 9600 to transfer data to the computer.
  Serial.begin(9600);

  // Khởi động thư viện.
  // Start up the library.
  rtc.begin();
}

void loop()
{
  // Lấy toàn bộ dữ liệu thời gian hiện tại.
  // Get all current time data.
  DateTime now = rtc.now();

  // Truyền giá trị lên máy tính.
  // Transmit the value to the computer.
  Serial.print(daysOfTheWeek[now.dayOfTheWeek()]);
  Serial.print(", ");
  //
  Serial.print(now.day(), DEC);
  Serial.print("/");
  Serial.print(now.month(), DEC);
  Serial.print("/");
  Serial.print(now.year(), DEC);
  Serial.print(" - ");
  //
  Serial.print(now.hour(), DEC);
  Serial.print(":");
  Serial.print(now.minute(), DEC);
  Serial.print(":");
  Serial.print(now.second(), DEC);
  Serial.println();

  // Đợi 1s để cập nhập tiếp.
  // Wait 1s to update again.
  delay(1000);
}
</source>

=== Sơ đồ kết nối: ===
{| class="wikitable"
!MakerEdu Shield for Vietduino
! style="text-align:left;" |Arduino/Vietduino
!Devices
|-
|Port I2C
|SDA / SCL
|Mạch Thời Gian Thực MKE-M09 RTC DS1307 Real Time Clock Module
|}

=== Các bước tiến hành: ===
#Kết nối mạch Vietduino Uno với mạch MakerEDU Shield for Vietduino.
#Kết nối Mạch Thời Gian Thực MKE-M09 với mạch MakerEDU Shied for Vietduino qua '''Port I2C'''.
#Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port).
#Nạp chương trình mẫu vào mạch Vietduino Uno.
#Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.

=== Kết quả: ===
...pic

==Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator==
===Phần cứng cần chuẩn bị:===
* Mạch thời gian thực MKE-M09 RTC DS1307 real time clock module
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Creator]] 
* Cáp USB để nạp chương trình và cấp nguồn
===Phần mềm cần chuẩn bị:===
*Tải và cài đặt phần mềm mBlock theo [[Giới thiệu và hướng dẫn cài đặt phần mềm mBlock|hướng dẫn.]]
*Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn]].
*Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm mBlock|hướng dẫn.]]
===Chương trình mẫu:===

# Mạch MakerEdu Creator đọc liên tục giá trị thời gian từ mạch RTC DS1307, với chu kỳ mỗi 1s.
# Sau đó cho hiển thị các giá trị thời gian lên màn hình LCD, gồm: "Thứ, Ngày/Tháng/Năm" và "Giờ:Phút:Giây".

<u>'''Blocks'''</u>

[[File:MBlock M09.PNG|border|700x700px]]

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEdu Creator
!Devices
|-
|Port I2C
|Mạch Thời Gian Thực MKE-M09 RTC DS1307 Real Time Clock Module
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}
===Các bước tiến hành:===
#Kết nối Mạch Thời Gian Thực MKE-M09 với mạch MakerEdu Creator qua '''Port I2C'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEdu Creator qua '''Port I2C'''.
#Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
#Nạp chương trình mẫu vào mạch MakerEdu Creator.
#Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.
===Kết quả:===
...pic

==Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bit==

===Phần cứng cần chuẩn bị:===

*Mạch thời gian thực MKE-M09 RTC DS1307 real time clock module
*[[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
*[[Mạch MakerEdu Shield for Micro:bit]]
*[[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|Mạch Micro:Bit]]
* Cáp USB để nạp chương trình và cấp nguồn

===Phần mềm cần chuẩn bị:=== 
*Khởi động phần mềm MakeCode theo [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|hướng dẫn]].
*Cài đặt Extension MakerEdu Hardware trên MadeCode và tham khảo các khối chức năng theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm MakeCode|hướng dẫn]].
*Tham khảo cách kết nối và nạp chương trình cho Micro:bit [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên máy tính với phần mềm MakeCode|trên máy tính]] hoặc [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên điện thoại, máy tính bảng với phần mềm MakeCode|điện thoại, máy tính bảng.]]

===Chương trình mẫu: ===

# Micro:Bit đọc liên tục giá trị thời gian từ mạch RTC DS1307, với chu kỳ mỗi 1s.
# Sau đó cho hiển thị các giá trị thời gian lên màn hình LCD, gồm: "Thứ, Ngày/Tháng/Năm" và "Giờ:Phút:Giây".

<u>'''Blocks'''</u>

[[File:MakeCode_M09.png|border|frameless|1000x1000px]]

'''<u>Javascript</u>'''

<source lang="typescript">
// Xóa toàn bộ nội dung trên LCD (nếu có)
lcd.clearScreen()

basic.forever(function () {
  // Cho hiển thị thông tin LỊCH hiện tại trong RTC trên LCD
  // Là Thứ, Ngày, Tháng, Năm
  lcd.displayText(ds3231.getCalendar(), 1, 1)

  // Cho hiển thị tiếp thông tin THỜI GIAN hiện tại trong RTC trên LCD
  // Là Giờ, Phút, Giây
  lcd.displayText(ds3231.getTime(), 1, 2)

  // Dừng 1s
  basic.pause(1000)
})
</source>

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEDU Shield for Micro:bit
!Devices
|-
|Port I2C
|Mạch Thời Gian Thực MKE-M09 RTC DS1307 Real Time Clock Module
|-
| Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}

=== Các bước tiến hành:=== 
#Kết nối Mạch Thời Gian Thực MKE-M09 với mạch MakerEDU Shield For Micro:Bit qua '''Port I2C'''.
# Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEDU Shield For Micro:Bit qua '''Port I2C'''.
# Kết nối Micro:bit với mạch MakerEdu Shield for Micro:bit
# Nạp chương trình mẫu vào mạch Micro:Bit.
# Nhấn nút Reset trên mạch Micro:Bit để bắt đầu chạy chương trình.

===Kết quả:===
...pic

==Nhà phân phối==
Có thể mua Mạch thời gian thực MKE-M09 RTC DS1307 real time clock module tại các nhà phân phối sau:
*[https://hshop.vn/products/mach-thoi-gian-thuc-mkl-m09-rtc-ds3231-real-time-clock-module Hshop.vn - Điện tử & Robot.]
[[Category:Modules]]
