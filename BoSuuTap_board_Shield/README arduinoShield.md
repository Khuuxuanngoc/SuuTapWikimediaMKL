==Giới thiệu==
'''MakerEdu Shield for Vietduino''' được nghiên cứu và và sản xuất bởi [https://www.makerlab.vn/ MakerLab.vn] là một bo mạch trung gian chuẩn Arduino Shield, giúp bạn kết nối các mạch điều khiển trung tâm '''Arduino/Vietduino''' với các '''Module Chức Năng''' và '''Cảm Biến''' trong [[MakerEdu|''Hệ sinh thái phần cứng Robotics MakerEdu'']] qua cổng kết nối chuẩn XH2.54 giúp kết nối dễ dàng và chống ngược, sai các chân kết nối. 

Mạch MakerEdu Shield for Vietduino tương thích với các mạch điều khiển trung tâm sau: 

* Mạch Arduino Uno và các mạch có thiết kế tương tự
* Mạch Arduino Mega 2560 và các mạch có thiết kế tương tự
* [[Mạch Vietduino Uno (Arduino Uno Compatible)]]
* [[Mạch Vietduino Mega 2560 (Arduino Mega2560 Compatible)]]
* [[Mạch Vietduino Wifi BLE ESP32 (Arduino Compatible)]]
{{Tr-Info
|name=Lưu ý:
|value=Mạch MakerEdu Shield for Vietduino sẽ tương thích tốt nhất khi sử dụng với các mạch Vietduino giúp phát huy tối đa các chức năng của mạch.
}}[[File:Vietduino with MakerEdu robotics hardware.jpg|alt=1 trong 10 dự án: "Mô phỏng hệ thống giám sát môi trường trong nông nghiệp thông minh"|none|thumb|700x700px|Dự án "Mô phỏng hệ thống giám sát môi trường trong nông nghiệp thông minh" với module hiển thị LCD, cảm biến nhiệt độ độ ẩm, cảm biến ánh sáng, module còi báo động kết nối với Vietduino Uno qua MakerEdu Shield.]]
[[File:Arduino-DHT11-Humidity-and-Temperature.png|alt=Một dự án tương tự với cảm biến nhiệt độ độ ẩm và màn hình LCD nối bằng dây cắm đơn qua Breadboard.|none|thumb|700x700px|Một dự án tương tự với cảm biến nhiệt độ độ ẩm và màn hình LCD nối bằng dây cắm đơn qua Breadboard.]]

==Thông số kỹ thuật==
{| class="wikitable" cellpadding="1" cellspacing="1"
!Model
|MakerEdu Shield for Vietduino
|-
! scope="row" |Chuẩn kết nối với mạch điều khiển trung tâm
|Arduino Shield
|-
! scope="row" |Chuẩn Conector
|XH2.54 3Pins / 4Pins
|-
! scope="row" |Nguồn đầu vào
| VIN từ Domino hoặc VIN từ mạch điều khiển trung tâm
|-
! scope="row" |Cổng Digital I/O đơn
| 7 cổng: A1, A2, A3, D9, D10, D11 (Digital Signal-5V-GND)
|-
!Cổng Digital I/O đôi
|1 cổng: D12+D13 (D12-D13-5V-GND)
|-
! scope="row" |Cổng Analog Input
|3 cổng: A1, A2, A3 (Analog Signal-5V-GND)
|-
!Cổng giao tiếp I2C
|5 cổng (SCL-SDA-5V-GND)
|-
!Cổng giao tiếp UART
|1 cổng (TX-RX-5V-GND)
|-
! scope="row" |Cổng cấp nguồn đầu ra bổ sung POWER+
| 1 cổng Output (3V3-5V-VIN-GND)
|-
!Tích hợp
|Led nguồn, nút nhấn Reset
|}

==Kích thước==
[[File:EduShield.JPG|alt=MakerEDU Shield dimension|none|thumb|500x500px|MakerEdu Shield for Vietduino dimension]]

==Hình ảnh sản phẩm ==
[[File:arduino_makeredu_shield_front_back.jpg|alt=Arduino MakerEDU Shield Front and Back|center|thumb|700x700px|MakerEdu Shield for Vietduino Front and Back]]

==Hướng dẫn sử dụng==
[[File:Makeredu shield - function.jpg|alt=MakerEDU Shield Function|thumb|MakerEdu Shield for Vietduino Function]]

=== Các chức năng chính trên mạch ===
# '''''Nút nhấn Reset:''''' được nối với chân Reset (RST) của Arduino hoặc các bo mạch tương thích, sử dụng để khởi động lại (Reset) chương trình.
# ''Cổng cấp nguồn Domino:'' được nối với chân VIN của Arduino hoặc các bo mạch tương thích, sử dụng để cấp nguồn cho mạch hoạt động hoặc lấy áp từ chân VIN của Arduino cấp cho các mạch khác, lưu ý không cấp ngược nguồn âm (-) và dương (+) và không cấp quá điện áp quy định dưới đây:
#* Với các mạch Arduino sử dụng IC giảm áp LM1117 5VDC: điện áp VIN cấp từ 6~9VDC.
#* Với mạch Vietduino sử dụng nguồn xung giảm áp: điện áp VIN từ 6~24VDC.
# '''''Cổng giao tiếp I2C:''''' chuẩn cắm Conector XH2.54 4Pins (4 chân), được sử dụng để giao tiếp với cách bo mạch, module, cảm biến sử dụng giao tiếp I2C, thứ tự các chân tín hiệu: SCL-SDA-5V-GND, có tổng cộng 5 cổng I2C với các chân tín hiệu được nối song song (tương đương nhau).
# '''''Cổng Digital I/O đôi:''''' chuẩn cắm Conector XH2.54 4Pins (4 chân), được sử dụng để giao tiếp với các bo mạch, module, cảm biến với 2 chân Digital I/O là D12 và D13 như cảm biến siêu âm hoặc có thể sử dụng như cổng Software Serial UART, thứ tự các chân tín hiệu: D12-D13-5V-GND.
# '''''Cổng giao tiếp UART:''''' chuẩn cắm Conector XH2.54 4Pins (4 chân) được sử dụng để giao tiếp với cách bo mạch, module, cảm Biến sử dụng giao tiếp UART, thứ tự các chân tín hiệu: TX-RX-5V-GND.
# '''''Cổng Digital I/O đơn:''''' chuẩn cắm Conector XH2.54 3Pins (3 chân), được sử dụng để giao tiếp với các bo mạch, module, cảm biến sử dụng tín hiệu Digital, thứ tự các chân tín hiệu: Digital I/O-5V-GND, có tổng cộng 3 cổng Digital I/O đơn được nối với các chân tín hiệu là: D9, D10, D11, thứ tự các chân tín hiệu: Digital Signal-5V-GND.
# '''''Cổng cấp nguồn đầu ra bổ sung POWER+:''''' là cổng OUTPUT (đầu ra), được sử dụng để cấp nguồn cho các bo mạch, module, cảm biến cần sử dụng thêm các tín hiệu nguồn cấp bổ sung như: mạch relay, mạch điều khiển động cơ,...,  thứ tự các chân tín hiệu: 3V3-5V-VIN-GND. 
# '''''Cầu phân áp VIN:''''' là cầu phân áp được nối với chân VIN, đầu ra của cầu phân áp sẽ trả ra giá trị là VOUT = VIN/5.7 được nối vào chân tín hiệu Analog A0 trên mạch, được sử dụng để đo giá trị của VIN trong các trường hợp: xác định mức pin, báo hiệu hết pin,... 
# '''''Cổng Analog Input:''''' chuẩn cắm Conector XH2.54 3Pins (3 chân), được sử dụng để giao tiếp với các bo mạch, module, cảm biến sử dụng tín hiệu Analog, thứ tự các chân tín hiệu: Analog Signal-5V-GND, có tổng cộng 3 cổng Analog Input được nối với các chân tín hiệu là: A1, A2, A3 (lưu ý đối với Arduino thì chân Analog còn có thể sử dụng như chân Digital nên cũng có thể sử dụng các cổng Analog Input này với chức năng như các cổng Digital I/O đơn). 
# '''''Đèn báo nguồn:''''' đèn sẽ sáng báo hiệu khi mạch MakerEdu Shield for Vietduino đã được cấp nguồn.

=== Cách kết nối ===

==== Kết nối MakerEdu Shield với Vietduino Uno: ====
[[File:Kết nối MakerEdu Shield với Vietduino Uno.jpg|alt=Kết nối MakerEdu Shield với Vietduino Uno|none|thumb|700x700px|Kết nối MakerEdu Shield với Vietduino Uno]]

=== Lưu ý khi kết nối: ===

# Cần cắm chặt và chính xác các chân kết nối của MakerEdu Shield với Vietduino.
# Đèn nguồn trên MakerEdu Shield sẽ phát sáng khi các chân được kết nối chặt, khớp và đúng thứ tự.

[[File:Lưu ý khi kết nối MakerEdu Shield với Vietduino.jpg|alt=Lưu ý khi kết nối MakerEdu Shield với Vietduino|none|thumb|700x700px|Lưu ý khi kết nối MakerEdu Shield với Vietduino]]
=='''[[Hướng dẫn sử dụng phần mềm Arduino với các mạch Vietduino + MakerEdu Shield for Vietduino]]'''==
{{arduinomakeredu}}
==Nhà phân phối==
Có thể mua mạch MakerEdu Shield for Vietduino tại các nhà phân phối sau:

* [https://hshop.vn/products/arduino-makeredu-shield Hshop.vn - Điện tử & Robot.]
