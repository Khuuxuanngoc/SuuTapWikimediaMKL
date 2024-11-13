==Giới thiệu==
[[image:makeredu_creator.jpg|thumb|400x400px|MakerEdu Creator|link=Special:FilePath/makeredu_creator.jpg|alt=]]
MakerEdu Creator mà mạch điều khiển trung tâm trong hệ sinh thái phần cứng Robotics MakerEdu với 3 chức năng chính:

# Chức năng lưu trữ và thực thi các lệnh lập trình qua Khối Vi Điều Khiển (Microcontroller Unit).
# Chức năng cấp nguồn, giao tiếp và điều khiển các mạch module chức năng ([[Template:MakerEdu Module|MakerEdu Module]]), cảm biến ([[Template:MakerEdu Sensor|MakerEdu Sensor)]] qua các cổng kết nối chuẩn XH2.54.
# Chức năng điều khiển 2 Động cơ DC, 2 Động cơ RC Servo qua Khối Công Suất (Power Unit).

Mạch MakerEdu Creator được thiết kế dựa trên nền tảng là mạch Arduino Uno nên hoàn toàn tương thích với các phần mềm:

* [https://www.arduino.cc/en/software Phần mềm Arduino (chọn Device là Arduino Uno).]
* [https://www.mblock.cc/en/download/ Phần mềm Mblock (chọn Device là MakerEdu Creator).]
* [https://thestempedia.com/product/pictoblox/ Phần mềm PictoBlox (Chọn Device là Arduino Uno).]

==Thông số kỹ thuật==
{| class="wikitable" cellpadding="1" cellspacing="1"
!Model
|MakerEdu Creator
|-
! scope="row" |Vi điều khiển
|ATmega328P-PU
|-
! scope="row" |Điện áp hoạt động
|5VDC từ cổng USB-C
|-
! scope="row" |Digital Port
| D10, D11, D12, D3+D2
|-
! scope="row" |Analog Port
|A1, A2, A3
|-
!I2C Port
|3 x I2C (SDA: A4 / SCL: A5)
|-
!Uart Port 
|1 x UART (RX: D0 / TX: D1)
|-
!RC Servo motor control Port
|D10, D11
|-
! rowspan="2" |DC motor control port
|Motor_A (Speed: D6 / Direction: D8, D9)
|-
|Motor_B (Speed: D5 / Direction: D4, D7)
|-
! scope="row" |Dòng DC đầu ra các chân I/O
| Max 20mA
|-
! scope="row" |Flash Memory
|32KB với 0.5 KB sử dụng cho bootloader
|-
! scope="row" |SRAM
|2KB
|-
! scope="row" |EEPROM
|1KB
|-
! scope="row" |Clock Speed
|16MHz
|-
! scope="row" |LED_BUILTIN
|D13
|-
!IC nạp chương trình và giao tiếp UART
|CH340
|-
!Cổng giao tiếp máy tính
|USB-C
|-
!Tương tích hệ điều hành
|Windows / MacOS / Linux
|}

==Kích thước==
[[File:makeredu_creator_dimension.JPG|alt=MakerEdu Creator dimension|none|thumb|400x400px|MakerEdu Creator dimension]]

==Các tính năng vượt trội ==
[[File:makeredu_creator_functions.jpg|alt=MakerEdu Creator Advance Function|thumb|400x400px|MakerEdu Creator Advance Function]]

# Mạch MakerEdu Creator thuộc [[Template:MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] với chuẩn kết nối connector XH2.54 chắc chắn, chống ngược và dễ dàng tháo lắp khi sử dụng với các mạch module chức năng ([[Template:MakerEdu Module|MakerEdu Module]]) và cảm biến ([[Template:MakerEdu Sensor|MakerEdu Sensor]]).
# Cấp nguồn qua cổng USB-C dễ dàng và an toàn, có thể sử dụng pin dự phòng (Power Bank), nguồn sạc điện thoại hoặc nguồn từ cổng USB máy tính để cấp nguồn cho mạch MakerEdu Creator.
# Tích hợp 2 cổng điều khiển 2 x Động cơ RC Servo.
# Tích hợp Driver điều khiển 2 x Động cơ DC.
# Vỏ Mica bảo vệ an toàn, tránh chập chạm.
# Tương thích với hầu hết các hệ điều hành Windows / MacOS / Linux và các phần mềm lập trình phổ biến: Arduino, Mblock, PictoBlox,...

==Các lưu ý==
[[File:81D96932-C445-4E34-B537-3D333488103D 1 201 a.jpg|alt=MakerEdu Creator connect with Motor|none|thumb|700x700px|MakerEdu Creator connect with Motor]]
'''1) Cấp nguồn'''

Mạch MakerEdu Creator sử dụng nguồn chính từ cổng USB-C để cấp nguồn 5VDC cho hệ thống hoạt động gồm bộ xử lý, cổng kết nối và động cơ. Các bạn có thể lựa chọn cấp nguồn từ cổng USB của máy tính, các loại nguồn cấp bằng cổng USB hoặc với các ứng dụng di động như robot có thể cấp nguồn bằng sạc dự phòng, loại sạc dự phòng khuyến nghị sử dụng:
*[https://hshop.vn/products/hop-sac-pin-du-phong-18650-diy-power-bank-case-3-cell Hộp sạc pin dự phòng 18650 DIY Power Bank Case 3 Cell]
'''2) Động cơ DC'''

Động cơ DC sử dụng phải là loại có thể hoạt động ở điện áp 5VDC, với dòng điện tiêu thụ tối đa 800mA, các loại động cơ khuyến nghị sử dụng:
*[https://hshop.vn/products/dong-co-dc-giamtoc-v1-1-48 Động cơ DC giảm tốc V1 Dual Shaft Plastic Geared TT Motor + bánh xe]
*[https://hshop.vn/products/bo-dong-co-dc-giam-toc-ga12-n20-kem-ga-bat-va-banh-xe-v1-34mm Bộ động cơ DC giảm tốc GA12 N20 kèm gá bắt và bánh xe V1 34mm]
*[https://hshop.vn/products/dong-co-bom-chim-mini-5vdc Động cơ bơm chìm Mini Water Pump 5VDC] ''(lưu ý với động cơ bơm cần phải cấp đúng chiều + và - không sẽ làm hỏng cấu trúc động cơ).''
'''3) Động cơ RC Servo'''

Động cơ RC Servo sử dụng phải là loại có thể hoạt động ở điện áp 5VDC, động cơ RC Servo sử dụng trực tiếp nguồn từ cổng USB-C của MakerEdu Creator nên khi sử dụng cần cấp nguồn với dòng điện đủ để động cơ có thể hoạt động bình thường, động cơ khuyến nghị sử dụng:
*[https://hshop.vn/products/dong-co-rc-servo-9g Động cơ RC Servo 9G]
*[https://hshop.vn/products/dong-co-rc-servo-mg90s Động cơ RC Servo MG90S]
== Hình ảnh sản phẩm ==
[[File:MakerEdu Creator front and back.jpg|alt=MakerEdu Creator front and back|none|thumb|1000x1000px|MakerEdu Creator front and back]]

==Hướng dẫn sử dụng với phần mềm Arduino ==

===Hướng dẫn sử dụng phần mềm Arduino cơ bản: ===
{{tongquanarduino}}

===Hướng dẫn kết nối và nạp chương trình mẫu cho '''''Mạch MakerEdu Creator''''' trên phần mềm Arduino:===
'''''<u>1) Kết nối máy tính:</u>''''' Kết nối '''''Mạch MakerEdu Creator''''' với máy tính bằng cáp USB-C sẽ thấy Led nguồn PWR trên mạch phát sáng.[[File:Connect MakerEdu Creator with Computer by USB-C cable.jpg|none|thumb|700x700px|alt=MakerEdu Creator connect with the computer|MakerEdu Creator connect with the computer]]'''<u>2) Cài đặt Driver:</u>''' '''''Mạch MakerEdu Creator'''''  là một mạch Arduino Uno Compatible (tương thích Arduino Uno) sử dụng '''''IC nạp chương trình và giao tiếp máy tính CH340,''''' các bạn có thể tham khảo [[Hướng dẫn cài đặt Driver cho các mạch sử dụng IC giao tiếp USB-UART CH34x|Hướng dẫn cài đặt Driver cho các mạch sử dụng IC giao tiếp USB-UART CH34x - MakerLab Wiki]].

'''<u>3) Cấu hình mạch trên phần mềm Arduino:</u>''' Để cấu hình mạch trên phần mềm Arduino chúng ta cần làm các bước sau:

*Thiết lập '''Board''' tại '''''Tools > Board > Arduino AVR Boards > Arduino Uno''''' và '''Port''' (cổng kết nối) cho mạch, nếu không xác định được cổng kết nối có thể ngắt kết nối mạch và kết nối lại đồng thời kiểm tra phần Port để thấy cổng kết nối mới của mạch xuất hiện:
[[File:Vietduino Uno Board and Port.jpg|alt=Vietduino Uno Board and Port|none|thumb|700x700px|MakerEdu Creator Board and Port]]
*Sau khi đã hoàn thành các thiết lập cơ bản bạn có thể nạp chương trình '''Blink''' sau vào mạch MakerEdu Creator trên phần mềm Arduino bằng cách nhấn vào nút '''Upload''' hoặc chọn '''''Sketch > Upload''''' sẽ thấy đèn Led L13 trên mạch chớp tắt 1 giây 1 lần:
<source lang="c++">/*
  Blink
  Turns an LED_BUILTIN on D13 of MakerEdu Creator for one second, then off for one second, repeatedly.
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
[[File:Upload Blink on Vietduino Uno.jpg|alt=Arduino Upload Blink on Vietduino Uno|none|thumb|700x700px|Arduino Upload Blink on MakerEdu Creator]]
== Hướng dẫn sử dụng với phần mềm mBlock ==

=== '''[[Hướng dẫn sử dụng phần mềm mBlock với mạch MakerEdu Creator]]:''' ===
{{tongquanmblock}}

=== Hướng dẫn kết nối và nạp chương trình cho '''''Mạch MakerEdu Creator''''' trên phần mềm Mblock: ===
'''''<u>1) Kết nối máy tính:</u>''''' Kết nối '''''Mạch MakerEdu Creator''''' với máy tính bằng cáp USB-C sẽ thấy Led nguồn PWR trên mạch phát sáng như ở phần hướng dẫn Arduino.

'''<u>''2) Cài đặt Driver và Cấu hình Device:''</u> Cài đặt Driver và cấu hình Mạch MakerEdu Creator trên phần mềm Mblock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn tại đây.]]'''

''<u>3) Nạp chương trình mẫu:</u>'' Nạp chương trình chớp tắt đèn Led L13 trên mạch MakerEdu Creator với phần mềm Mblock để kiểm tra hoạt động:
[[File:Mblock upload Blink on MakerEdu Creator.png|alt=Mblock upload Blink on MakerEdu Creator|none|thumb|700x700px|Mblock upload Blink on MakerEdu Creator]]

== Hướng dẫn sử dụng với phần mềm PictoBlox ==
'''''<u>1) Kết nối máy tính:</u>''''' Kết nối '''''Mạch MakerEdu Creator''''' với máy tính bằng cáp USB-C sẽ thấy Led nguồn PWR trên mạch phát sáng như ở phần hướng dẫn Arduino.

'''<u>''2) Cài đặt Driver:''</u> ''Mạch MakerEdu Creator''  là một mạch Arduino Uno Compatible (tương thích Arduino Uno) sử dụng ''IC nạp chương trình và giao tiếp máy tính CH340,'' các bạn có thể tham khảo [[Hướng dẫn cài đặt Driver cho các mạch sử dụng IC giao tiếp USB-UART CH34x|Hướng dẫn cài đặt Driver cho các mạch sử dụng IC giao tiếp USB-UART CH34x - MakerLab Wiki]].'''

''<u>3) Cấu hình mạch trên phần mềm PictoBlox:</u>''

Trên phần mềm PictoBlox, tại thanh công cụ chính chọn '''[Board]''', sau đó chọn mạch kết nối là '''Arduino Uno''' vì mạch MakerEdu Creator là một mạch Arduino Uno Compatible (tương thích Arduino Uno):
[[File:MakerEdu Creator board config PictoBlox.png|alt=MakerEdu Creator board config PictoBlox|none|thumb|700x700px|MakerEdu Creator board config PictoBlox]]
Sau đó tại thanh công cụ chính chọn cổng kết nối của MakerEdu Creator tại mục '''[Connect]''', cổng kết nối thường sẽ có tên là '''''usbserialxx (trên MacOS)''''' hoặc '''''COMxx (trên Windows)''''', nếu không xác định được cổng kết nối có thể ngắt kết nối mạch với máy tính và kết nối lại, quan sát phần cổng mới trước và sau khi kết nối để xác định, sau khi kết nối thành công biểu tương kết nối cạnh mục [Connect] sẽ thay đổi để báo hiệu:
[[File:MakerEdu Creator port config PictoBlox.png|alt=MakerEdu Creator port config PictoBlox|none|thumb|700x700px|MakerEdu Creator port config PictoBlox]]
''<u>3) Nạp chương trình mẫu:</u>'' Tại mục [Mode] trên thanh công cụ, chọn Tab [Upload], sau đó nhấp nút [Upload Code] để nạp chương trình chớp tắt đèn Led L13 trên mạch MakerEdu Creator giúp kiểm tra hoạt động:
[[File:PictoBlox upload Blink on MakerEdu Creator.png|alt=PictoBlox upload Blink on MakerEdu Creator|none|thumb|900x900px|PictoBlox upload Blink on MakerEdu Creator]]

==Nhà phân phối==
Có thể mua mạch MakerEdu Creator tại các nhà phân phối sau:

*[https://hshop.vn/products/mach-makeredu-creator-arduino-uno-compatible Hshop.vn - Điện tử & Robot.]
