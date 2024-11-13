[[image:vietduino_uno.jpg|thumb|450x450px|Vietduino Uno Board|link=Special:FilePath/vietduino_uno.jpg|alt=]]
==Giới thiệu==
'''''Mạch Vietduino Uno (Arduino Uno Compatible)''''' được nghiên cứu và và sản xuất bởi [https://www.makerlab.vn/ MakerLab.vn] dựa trên nguyên mẫu là mạch Arduino Uno với các ưu điểm vượt trội:
#Thiết kế tương thích hoàn toàn về hình dạng, chuẩn chân tín hiệu và cách sử dụng với Arduino Uno.
#'''S'''ử dụng mạch nguồn xung giảm áp với ưu điểm là hiệu suất chuyển đổi cao, toả nhiệt thấp, tiết kiệm năng lượng, dải điện áp đầu vào cấp cho mạch rộng từ 6~24VDC với dòng đầu ra lớn: 5VDC/Max 1500mA, 3.3VDC / Max 700mA.
#'''B'''ổ sung thêm các chân cấp nguồn POWER+ 5VDC giúp dễ dàng cấp nguồn cho nhiều thiết bị khác nhau.
#'''S'''ử dụng IC chuyển đổi USB-UART CH340 được nhập khẩu chính hãng cho độ ổn định và độ bền cao.
#Chức năng cách ly nguồn cổng USB tự động khi cấp nguồn ngoài từ chân Vin hoặc giắc DC giúp bảo vệ cổng USB máy tính của bạn an toàn hơn.
==Thông số kỹ thuật==
{| class="wikitable" cellpadding="1" cellspacing="1"
!Model
|Vietduino Uno (Arduino Uno Compatible)
|-
! scope="row" |Vi điều khiển
|ATmega328P-PU
|-
! scope="row" |Điện áp hoạt động
|5VDC
|-
! scope="row" |Điện áp đầu vào VIN
|6~24VDC
|-
! scope="row" |Digital I/O 
|14 chân (với 6 chân có chức năng PWM)
|-
! scope="row" |PWM Digital I/O
| 6 chân (D3, D5, D6, D9, D10, D11)
|-
! scope="row" |Analog Input
|6 chân (A0~A5)
|-
! scope="row" |Dòng DC đầu ra các chân I/O
|Max 20mA
|-
! scope="row" |Dòng DC đầu ra chân 3V3 
|Max 700mA
|-
!Dòng DC đầu ra chân 5V
| Max 1500mA 
|-
! scope="row" |Flash Memory 
|32KB với 0.5 KB sử dụng cho bootloader
|-
! scope="row" | SRAM
|2KB
|-
! scope="row" | EEPROM
|1KB
|-
! scope="row" |Clock Speed
| 16MHz
|-
! scope="row" |LED_BUILTIN
|D13
|-
!IC nạp chương trình và giao tiếp UART
|CH340
|-
!Cổng giao tiếp máy tính
|USB-B hoặc USB-C
|-
!Kích thước
| 68.6 x 53.34mm 
|}

==Kích thước==
[[File:VietduinoUno_dimension.JPG|alt=Vietduino Uno dimension|none|thumb|400x400px|Vietduino Uno dimension]]

==Các phiên bản Vietduino Uno==
===Phiên bản sử dụng cổng USB-B===
[[File:Vietduino Uno USB-B front and back.jpg|alt=Vietduino Uno USB-B front and back|none|thumb|964x964px|Vietduino Uno USB-B front and back]]

===Phiên bản sử dụng cổng USB-C===
[[File:Vietduino Uno USB-C.jpg|alt=Vietduino Uno USB-C front and back|none|thumb|964x964px|Vietduino Uno USB-C front and back]]

==Hướng dẫn sử dụng với phần mềm Arduino==

===Hướng dẫn sử dụng phần mềm Arduino cơ bản:===
{{tongquanarduino}}

===Hướng dẫn kết nối và nạp chương trình cho '''''Mạch Vietduino Uno''''' trên phần mềm Arduino:===
'''''<u>1) Kết nối máy tính:</u>''''' Kết nối '''''Mạch Vietduino Uno''''' với máy tính bằng cáp USB sẽ thấy Led nguồn ON trên mạch phát sáng:
[[File:Vietduino Uno connect with Computer.jpeg|alt=Vietduino Uno connect with the computer|none|thumb|700x700px|Vietduino Uno connect with the computer]]

'''<u>2) Cài đặt Driver:</u>''' '''''Mạch Vietduino Uno'''''  mà một mạch Arduino Uno Compatible (tương thích Arduino Uno) sử dụng '''''IC nạp chương trình và giao tiếp máy tính CH340,''''' các bạn có thể tham khảo [[Hướng dẫn cài đặt Driver cho các mạch sử dụng IC giao tiếp USB-UART CH34x|Hướng dẫn cài đặt Driver cho các mạch sử dụng IC giao tiếp USB-UART CH34x - MakerLab Wiki]].

'''<u>3) Cấu hình mạch trên phần mềm Arduino:</u>''' Để cấu hình mạch trên phần mềm Arduino chúng ta cần làm các bước sau:

*Thiết lập '''Board''' tại '''''Tools > Board > Arduino AVR Boards > Arduino Uno''''' và '''''Port''''' (cổng kết nối) cho mạch, nếu không xác định được cổng kết nối có thể ngắt kết nối mạch và kết nối lại đồng thời kiểm tra phần Port để thấy cổng kết nối mới của mạch xuất hiện:
[[File:Vietduino Uno Board and Port.jpg|alt=Vietduino Uno Board and Port|none|thumb|700x700px|Vietduino Uno Board and Port]]
*Sau khi đã hoàn thành các thiết lập cơ bản bạn có thể nạp chương trình '''Blink''' sau vào mạch để test bằng cách nhấn vào nút '''Upload''' hoặc chọn '''''Sketch > Upload''''' sẽ thấy Led được kết nối với chân D13 trên mạch chớp tắt 1 giây 1 lần:
<source lang="c++">/*
  Blink
  Turns an LED_BUILTIN on D13 of Vietduino Uno for one second, then off for one second, repeatedly.
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
[[File:Upload Blink on Vietduino Uno.jpg|alt=Upload Blink on Vietduino Uno|none|thumb|700x700px|Upload Blink on Vietduino Uno]]

==Nhà phân phối==
Có thể mua mạch Vietduino Uno tại các nhà phân phối sau:
*'''Hshop.vn - Điện tử & Robot:''' [https://hshop.vn/products/vietduino-uno Vietduino Uno USB-B] | [https://hshop.vn/products/mach-vietduino-uno-usb-c-arduino-uno-compatible Vietduino Uno USB-C]
