[[image:vietduino_mega_2560.jpg|thumb|500x500px|Vietduino Mega 2560 Board|link=Special:FilePath/vietduino_mega_2560.jpg|alt=]]
==Giới thiệu==
'''''Mạch Vietduino Mega 2560 (Arduino Mega 2560 Compatible)''''' được nghiên cứu và và sản xuất bởi [https://www.makerlab.vn/ MakerLab.vn] dựa trên nguyên mẫu là mạch Arduino Mega 2560 với các ưu điểm vượt trội:
# Thiết kế tương thích hoàn toàn về hình dạng, chuẩn chân tín hiệu và cách sử dụng với Arduino Mega 2560.
#'''S'''ử dụng mạch nguồn xung giảm áp với ưu điểm là hiệu suất chuyển đổi cao, toả nhiệt thấp, tiết kiệm năng lượng, dải điện áp đầu vào cấp cho mạch rộng từ 6~24VDC với dòng đầu ra lớn: 5VDC/Max 1500mA, 3.3VDC / Max 700mA.
#'''B'''ổ sung thêm các chân cấp nguồn POWER+ 5VDC giúp dễ dàng cấp nguồn cho nhiều thiết bị khác nhau.
#'''S'''ử dụng IC chuyển đổi USB-UART CH340 được nhập khẩu chính hãng cho độ ổn định và độ bền cao.
#Chức năng cách ly nguồn cổng USB tự động khi cấp nguồn ngoài từ chân Vin hoặc giắc DC giúp bảo vệ cổng USB máy tính của bạn an toàn hơn.
==Thông số kỹ thuật==
{| class="wikitable" cellpadding="1" cellspacing="1"
!Model
|Mạch Vietduino Mega 2560 (Arduino Mega 2560 Compatible)
|-
! scope="row" |Vi điều khiển
|ATMEGA2560-16AU
|-
! scope="row" |Điện áp hoạt động
|5VDC
|-
! scope="row" |Điện áp đầu vào VIN
|6~24VDC
|-
! scope="row" |Digital I/O
|54 chân (D0-D53)
|-
! scope="row" |PWM Digital I/O
|15 chân (D2-D13, D44-D46)
|-
! scope="row" | Analog Input
| 16 chân (A0-A15)
|-
! scope="row" |Dòng DC đầu ra các chân I/O
|20mA
|-
! scope="row" |Dòng DC đầu ra chân 3V3
| Max 700mA
|-
!Dòng DC đầu ra chân 5V
|Max 1500mA
|-
! scope="row" |Flash Memory
|256KB of which 8 KB used by bootloader
|-
! scope="row" |SRAM
|8KB
|-
! scope="row" | EEPROM
|4KB
|-
! scope="row" |Clock Speed
|16MHz
|-
! scope="row" |LED_BUILTIN
|D13
|-
!BUTTON_BUILTIN
|S8 (D8)
|-
!IC nạp chương trình và giao tiếp UART
|CP2102
|-
! Cổng giao tiếp máy tính
|USB-B 
|-
!Kích thước
|101.6 x 53.35mm 
|}
==Kích thước==
[[File:VietduinoMega2560_dimension.JPG|alt=Vietduino Mega 2560 dimension|none|thumb|500x500px|Vietduino Mega 2560 dimension]]

== Hình ảnh sản phẩm ==
[[image:vietduino_mega_2560.jpg|thumb|700x700px|Vietduino Mega 2560 Front|link=Special:FilePath/vietduino_mega_2560.jpg|alt=Vietduino Mega 2560 Front|none]]
[[File:Vietduino Mega 2560 Back.jpg|alt=Vietduino Mega 2560 Back|none|thumb|700x700px|Vietduino Mega 2560 Back]]

==Hướng dẫn sử dụng với phần mềm Arduino==

===Hướng dẫn sử dụng phần mềm Arduino cơ bản:===
{{tongquanarduino}}

===Hướng dẫn kết nối và nạp chương trình cho '''''Mạch Vietduino Mega 2560''''' trên phần mềm Arduino:===
'''''<u>1) Kết nối máy tính:</u>''''' Kết nối '''''Mạch Vietduino Mega 2560''''' với máy tính bằng cáp USB sẽ thấy Led nguồn PWR trên mạch phát sáng.

'''<u>2) Cài đặt Driver:</u>''' '''''Mạch Vietduino Mega 2560'''''  mà một mạch Arduino Mega 2560 Compatible (tương thích Arduino Mega 2560) sử dụng '''''IC nạp chương trình và giao tiếp máy tính CP2102,''''' các bạn có thể tham khảo [[Hướng dẫn cài đặt Driver cho các mạch sử dụng IC giao tiếp USB-UART CP210x|Hướng dẫn cài đặt Driver cho các mạch sử dụng IC giao tiếp USB-UART CP210x - MakerLab Wiki]].

'''<u>3) Cấu hình mạch trên phần mềm Arduino:</u>''' Để cấu hình mạch trên phần mềm Arduino chúng ta cần làm các bước sau:

*Thiết lập '''Board''' tại '''''Tools > Board > Arduino AVR Boards > Arduino Mega or Mega 2560''''' và '''''Port''''' (cổng kết nối) cho mạch, nếu không xác định được cổng kết nối có thể ngắt kết nối mạch và kết nối lại đồng thời kiểm tra phần Port để thấy cổng kết nối mới của mạch xuất hiện:
[[File:Vietduino Mega 2560 Board and Port.jpg|alt=Vietduino Mega 2560 Board and Port|none|thumb|700x700px|Vietduino Mega 2560 Board and Port]]
*Sau khi đã hoàn thành các thiết lập cơ bản bạn có thể nạp chương trình '''Blink''' sau vào mạch để test bằng cách nhấn vào nút '''Upload''' hoặc chọn '''''Sketch > Upload''''' sẽ thấy Led được kết nối với chân D13 trên mạch chớp tắt 1 giây 1 lần:
<source lang="c++">/*
  Blink
  Turns an LED_BUILTIN on D13 of Vietduino Mega 2560 for one second, then off for one second, repeatedly.
*/
// the setup function runs once when you press reset or power the board
void setup() {
  // initialize digital pin LED_BUILTIN on D13 as an output.
  pinMode(13, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(13, HIGH);  // turn the LED on (HIGH is the voltage level)
  delay(1000);                      // wait for a second
  digitalWrite(13, LOW);   // turn the LED off by making the voltage LOW
  delay(1000);                      // wait for a second
}</source>
[[File:Upload Blink on Vietduino Mega 2560.jpg|alt=Upload Blink on Vietduino Mega 2560|none|thumb|700x700px|Upload Blink on Vietduino Mega 2560]]

==Nhà phân phối ==
Có thể mua '''''Mạch Vietduino Mega 2560''''' tại các nhà phân phối sau:
* [https://hshop.vn/products/vietduino-mega-2560-aruduino-mega-2560-compatible Hshop.vn - Điện tử & Robot.]
