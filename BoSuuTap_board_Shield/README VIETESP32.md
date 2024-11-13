[[image:Vietduino Wifi BLE ESP32.jpg|thumb|472x472px|Vietduino Wifi BLE ESP32 Board|link=Special:FilePath/Vietduino Wifi BLE ESP32.jpg|alt=]]
==Giới thiệu==
'''''Mạch Vietduino Wifi BLE ESP32 (Arduino Compatible)''''' được nghiên cứu và và sản xuất bởi [https://www.makerlab.vn/ MakerLab.vn] dựa trên '''''Module Wifi BLE SoC ESP32 ESP-WROOM-32E''''' từ chính hãng '''''Espressif''''' với các ưu điểm vượt trội:
#Thiết kế với hình dạng và các chân tín hiệu được sắp xếp để có độ tương đồng về chức năng cao nhất với quy chuẩn Arduino. 
#'''S'''ử dụng mạch nguồn xung giảm áp với ưu điểm là hiệu suất chuyển đổi cao, toả nhiệt thấp, tiết kiệm năng lượng, dải điện áp đầu vào cấp cho mạch rộng từ 6~24VDC với dòng đầu ra lớn: 5VDC/Max 1500mA, 3.3VDC / Max 700mA.
#'''B'''ổ sung thêm các chân cấp nguồn POWER+ 5VDC giúp dễ dàng cấp nguồn cho nhiều thiết bị khác nhau.
#'''S'''ử dụng IC chuyển đổi USB-UART CH340 được nhập khẩu chính hãng cho độ ổn định và độ bền cao.
#Chức năng cách ly nguồn cổng USB tự động khi cấp nguồn ngoài từ chân Vin hoặc giắc DC giúp bảo vệ cổng USB máy tính của bạn an toàn hơn.
==Thông số kỹ thuật==
{| class="wikitable" cellpadding="1" cellspacing="1"
!Model
|'''''Mạch Vietduino Wifi BLE ESP32 (Arduino Compatible)''''' 
|-
! scope="row" |CPU and On­Chip Memory
|
* ESP32-D0WD-V3 embedded, Xtensa dual-core 32-bit LX6 microprocessor, up to 240 MHz
* 448 KB ROM
* 520 KB SRAM
* 16 KB SRAM in RTC
|-
! scope="row" |Power Supply
|Power Input:

* DC Plug: 6~24VDC, Current > 500mA
* USB-C: 5VDC, Current > 500mA

Power Output:

* 5VDC: Max 1500mA
* 3.3VDC: Max 700mA
|-
!Interface
|SD card, UART, SPI, SDIO, I2C, LED PWM, Motor PWM, I2S, IR, pulse counter, GPIO, capacitive touch sensor, ADC, DAC, Two-Wire Automotive Interface (TWAI®, compatible with ISO11898-1)
|-
!Wifi
|
* 802.11b/g/n
* Bit rate: 802.11n up to 150 Mbps
* A-MPDU and A-MSDU aggregation
* 0.4 µs guard interval support
* Center frequency range of operating channel: 2412 ~ 2484 MHz
|-
! scope="row" |Bluetooth
|
* Bluetooth V4.2 BR/EDR and Bluetooth LE specification
* Class-1, class-2 and class-3 transmitter
* AFH
* CVSD and SBC
|-
! scope="row" |Integrated Components on Module
|
* 40 MHz crystal oscillator
* 4MB (XXN4) / 16MB (XX0H28) SPI flash
|-
!Antenna
|PCB (WROOM-32E) / IPEX (WROOM-32UE)
|-
! scope="row" |Button
|Reset
|-
!Led
|TX / RX / IO18 
|-
!Programmer
|USB-UART CH340 Included
|-
!Packet
|Arduino Packet
|}
==Kích thước==
{{kxnImageDimension
|file=VietduinoUno_dimension.JPG
|name=Vietduino Wifi BLE ESP32 (Arduino Compatible)
}}

==Hình ảnh ==
[[File:Vietduino Wifi BLE ESP32 Front and Back.jpg|alt=Vietduino Wifi BLE ESP32 Front and Back|none|thumb|964x964px|Vietduino Wifi BLE ESP32 Front and Back]]

==Hướng dẫn sử dụng với phần mềm Arduino==

===Hướng dẫn sử dụng phần mềm Arduino cơ bản:===
{{tongquanarduino}}

===Hướng dẫn kết nối và nạp chương trình cho '''''Mạch Vietduino Wifi BLE ESP32''''' trên phần mềm Arduino:===
'''''<u>1) Kết nối máy tính:</u>''''' Kết nối '''''Mạch Vietduino Wifi BLE ESP32''''' với máy tính bằng cáp USB-C sẽ thấy Led nguồn PWR trên mạch phát sáng.
[[File:Vietduino ESP32 WROOM-32E connect with the computer.jpg|alt=Vietduino ESP32 WROOM-32E connect with the computer|none|thumb|700x700px|Vietduino ESP32 WROOM-32E connect with the computer]]

'''<u>2) Cài đặt Driver:</u>''' '''''Mạch Vietduino Wifi BLE ESP32'''''  mà một mạch Arduino Compatible (tương thích Arduino) sử dụng '''''IC nạp chương trình và giao tiếp máy tính CH340,''''' các bạn có thể tham khảo [[Hướng dẫn cài đặt Driver cho các mạch sử dụng IC giao tiếp USB-UART CH34x|Hướng dẫn cài đặt Driver cho các mạch sử dụng IC giao tiếp USB-UART CH34x - MakerLab Wiki]].

'''<u>3) Cấu hình mạch trên phần mềm Arduino:</u>''' Để cấu hình mạch trên phần mềm Arduino chúng ta cần làm các bước sau:

*Copy đường link sau và dán vào mục '''''File > Preferences > Additional boards manager URLs''''' (trên Windows) hoặc '''''Arduino IDE > Settings > Additional boards manager URLs (trên MacOS) sau đó nhấn OK:'''''
<source lang="c++">https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json</source>
[[File:Add URL Vietduino ESP32 Board on Arduino.png|alt=Add URL Vietduino ESP32 Board on Arduino|none|thumb|700x700px|Add URL Vietduino ESP32 Board on Arduino]]
*Tiếp theo chọn '''''Tools > Board > Boards Manager...''''', tìm từ khoá '''''ESP32''''' sẽ thấy mục "'''esp32''' by Espressif Systems", nhấn '''Install và chờ đợi cho đến khi cài đặt hoàn tất:'''
[[File:Install Vietduino ESP32 Board.png|alt=Install Vietduino ESP32 Board|none|thumb|700x700px|Install Vietduino ESP32 Board]]
*Sau khi cài đặt hoàn tất, tắt và khởi động lại phần mềm Arduino, sau đó thiết lập '''Board''' tại '''''Tools > Board > esp32 > ESP32 Dev Module''''' và '''Port''' (cổng kết nối) cho mạch, nếu không xác định được cổng kết nối có thể ngắt kết nối mạch và kết nối lại đồng thời kiểm tra phần Port để thấy cổng kết nối mới của mạch xuất hiện:
[[File:Vietduino ESP32 Board and Port.png|alt=Vietduino ESP32 Board and Port|none|thumb|700x700px|Vietduino ESP32 Board and Port]]
*Các thiết lập mặc định để nạp chương trình của mạch sẽ như hình dưới đây: 
{{Kxnwaring
|name=Lưu ý quan trọng!!!:
|value=- Upload Speed với hệ điều hành Windows có thể chọn 912600, với MacOS hoặc các hệ điều hành khác nếu có báo lỗi khi nạp chương trình chọn 115200.

- Flash Size nếu ký hiệu trên Module WROOM-32E là "XXN4" chọn 4MB, nếu ký hiệu là "XX0H28" chọn 16MB.
}}
[[File:Vietduino ESP32 Board Default Configuration.png|alt=Vietduino ESP32 Board Default Configuration|none|thumb|700x700px|Vietduino ESP32 Board Default Configuration]]
*Sau khi đã hoàn thành các thiết lập cơ bản bạn có thể nạp chương trình '''Blink''' sau vào mạch để test bằng cách nhấn vào nút '''Upload''' hoặc chọn '''''Sketch > Upload''''' sẽ thấy Led được kết nối với chân IO18 trên mạch chớp tắt 1 giây 1 lần:
<source lang="c++">/*
  Blink
  Turns an LED_BUILTIN on IO18 of Vietduino ESP32 for one second, then off for one second, repeatedly.
*/
// the setup function runs once when you press reset or power the board
void setup() {
  // initialize digital pin LED_BUILTIN on IO18 as an output.
  pinMode(18, OUTPUT);
}

// the loop function runs over and over again forever
void loop() {
  digitalWrite(18, HIGH);  // turn the LED on (HIGH is the voltage level)
  delay(1000);                      // wait for a second
  digitalWrite(18, LOW);   // turn the LED off by making the voltage LOW
  delay(1000);                      // wait for a second
}</source>
[[File:Upload Blink on Vietduino ESP32.png|alt=Upload Blink on Vietduino ESP32|none|thumb|700x700px|Upload Blink on Vietduino ESP32]]

==Nhà phân phối==
Có thể mua '''''Mạch Vietduino Wifi BLE ESP32''''' tại các nhà phân phối sau:

*[https://hshop.vn/products/mach-vietduino-wifi-ble-esp32-arduino-compatible Hshop.vn - Điện tử & Robot.]
