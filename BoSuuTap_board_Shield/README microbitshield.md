[[image:microbit_makeredu_shield.jpg|thumb|427x427px|Micro:bit MakerEDU Shield Board|link=Special:FilePath/microbit_makeredu_shield.jpg|alt=]]
==Giới thiệu==
Mạch MakerEdu Shield for Micro:bit là một bo mạch trung gian giúp bạn kết nối Micro:bit với các mạch trong hệ sinh thái phần cứng Robotics MakerEdu. Sau khi đã kết nối, Micro:bit sẽ trở thành mạch điều khiển trung tâm trong hệ sinh thái phần cứng Robotics MakerEdu với 3 chức năng chính: 

# Chức năng lưu trữ và thực thi các lệnh lập trình qua khối điều kiển là mạch Micro:bit (Controller Unit).
# Chức năng cấp nguồn, giao tiếp và điều khiển các mạch module chức năng [[Template:MakerEdu Module|MakerEdu Module]], cảm biến [[Template:MakerEdu Sensor|MakerEdu Sensor]] qua các cổng kết nối chuẩn XH2.54.
# Chức năng điều khiển 2 Động cơ DC, 2 Động cơ RC Servo qua Khối Công Suất (Power Unit) trên mạch MakerEdu Shield for Micro:bit.
Mạch MakerEdu Shield for Micro:bit được thiết kế để có thể tương thích tốt nhất với phiên bản Micro:bit V2 và các phiên bản có thiết kế tương tự.

==Thông số kỹ thuật==
{| class="wikitable" cellpadding="1" cellspacing="1"
!Model
|MakerEdu Shield for Micro:bit
|-
!Tương thích
|Tương thích tốt nhất với Micro:bit V2 hoặc các phiên bản có thiết kế tương tự.
|-
! scope="row" |Chuẩn Connector kết nối
|XH2.54 3Pins / 4Pins
|-
! scope="row" |Nguồn đầu vào
| 5VDC từ cổng Micro USB trên mạch.
|-
! scope="row" |Cổng Digital I/O đơn
| 6 cổng: [P0], [P1], [P2], [P13], [P14], [P15]
|-
!Cổng Digital I/O đôi
|2 cổng: [P0+P1], [P2+P8]
|-
! scope="row" |Cổng Analog Input
|2 cổng: [P0], [P1], [P2]
|-
!Cổng giao tiếp I2C
|2 cổng: [I2C]
|-
! scope="row" |Cổng điều khiển RC Servo
| 2 cổng: [P0], [P12]
|-
!Cổng điều khiển động cơ DC
|2 cổng: [Motor_A], [Motor_B]
|-
!Cổng kết nối mở rộng (kẹp cá sấu, jack bắp chuối)
|4 cổng: [P0], [P1], [P2], [GND]
|}

==Kích thước==
[[File:MicroBit_Shield_1_0.JPG|alt=Micro:bit MakerEDU Shield dimension|none|thumb|400x400px|Micro:bit MakerEDU Shield dimension]]

==Hình ảnh sản phẩm ==
[[File:CD060E81.jpg|alt=MakerEdu Shield for Micro:bit Front and Back|center|thumb|1000x1000px|MakerEdu Shield for Micro:bit Front and Back]]

==Các tính năng vượt trội==
[[File:microbit_makeredu_shield_function.jpg|thumb|MakerEdu Shield for Micro:bit Advance Function|link=Special:FilePath/Microbit_makeredu_shield_function.jpg|alt=MakerEdu Shield for Micro:bit Advance Function|449x449px]]

# Mạch MakerEdu Shield for Micro:bit là một bo mạch trung gian giúp bạn kết nối Micro:bit với các mạch trong [[Template:MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] với chuẩn kết nối connector XH2.54 chắc chắn, chống ngược và dễ dàng tháo lắp khi sử dụng với các mạch module chức năng [[Template:MakerEdu Module|MakerEdu Module]] và cảm biến [[Template:MakerEdu Sensor|MakerEdu Sensor]].
# Cấp nguồn qua cổng MicroUSB dễ dàng và an toàn, có thể sử dụng pin dự phòng (Power Bank), nguồn sạc điện thoại hoặc nguồn từ cổng USB máy tính để cấp nguồn cho mạch MakerEdu Shield for Micro:bit
# Tích hợp cổng điều khiển 2 x Động cơ RC Servo.
# Tích hợp cổng điều khiển 2 x Động cơ DC.
# Vỏ Mica bảo vệ an toàn, tránh chập chạm.
# Tích hợp các cổng kết nối mở rộng tương tự như Micro:bit dùng cho các ứng dụng cảm ứng chạm hoặc kết nối đơn giản.

== Các lưu ý ==
[[File:BBB5D926-779D-40ED-80A6-6920F05DE9EC 1 201 a.jpg|alt=MakerEdu Shield for Micro:bit connect with Motor|none|thumb|700x700px|MakerEdu Shield for Micro:bit connect with Motor]]
'''1) Cấp nguồn'''

Các bạn bắt buộc phải cấp nguồn qua cổng MicroUSB của MakerEdu shield vì nguồn trên các cổng kết nối, động cơ và Micro:bit đều được lấy từ cổng này, khi đó nguồn chính của hệ thống sẽ là 5VDC, các bạn có thể lựa chọn cấp nguồn từ cổng USB của máy tính, các loại nguồn cấp bằng cổng USB hoặc với các ứng dụng di động như robot có thể cấp nguồn bằng sạc dự phòng, loại sạc dự phòng khuyến nghị sử dụng:

* [https://hshop.vn/products/hop-sac-pin-du-phong-18650-diy-power-bank-case-3-cell Hộp sạc pin dự phòng 18650 DIY Power Bank Case 3 Cell]

'''2) Động cơ DC'''

Động cơ DC sử dụng phải là loại có thể hoạt động ở điện áp 5VDC, với dòng điện tiêu thụ tối đa 800mA, các loại động cơ khuyến nghị sử dụng:

* [https://hshop.vn/products/dong-co-dc-giamtoc-v1-1-48 Động cơ DC giảm tốc V1 Dual Shaft Plastic Geared TT Motor + bánh xe]
* [https://hshop.vn/products/bo-dong-co-dc-giam-toc-ga12-n20-kem-ga-bat-va-banh-xe-v1-34mm Bộ động cơ DC giảm tốc GA12 N20 kèm gá bắt và bánh xe V1 34mm]
* [https://hshop.vn/products/dong-co-bom-chim-mini-5vdc Động cơ bơm chìm Mini Water Pump 5VDC] ''(lưu ý với động cơ bơm cần phải cấp đúng chiều + và - không sẽ làm hỏng cấu trúc động cơ).''

'''3) Động cơ RC Servo'''

Động cơ RC Servo sử dụng phải là loại có thể hoạt động ở điện áp 5VDC, động cơ RC Servo sử dụng trực tiếp nguồn từ cổng MicroUSB của MakerEdu Shield nên khi sử dụng cần cấp nguồn với dòng điện đủ để động cơ có thể hoạt động bình thường, động cơ khuyến nghị sử dụng:

* [https://hshop.vn/products/dong-co-rc-servo-9g Động cơ RC Servo 9G]
* [https://hshop.vn/products/dong-co-rc-servo-mg90s Động cơ RC Servo MG90S]

== Cách kết nối ==
Kết nối Micro:bit với MakerEdu Shield với biểu tượng logo màu vàng ở chính giữa của Micro:Bit hướng theo chiều ký hiệu trên MakerEdu Shield như hình:
[[File:A0AA0914-909B-419D-B238-ECFC12DB393A 1 201 a.jpg|alt=Kết nối Micro:bit và MakerEdu Shield theo chiều biểu tượng logo trên Shield.|none|thumb|700x700px|Kết nối chiều biểu tượng logo màu vàng của Micro:bit hướng theo chiều ký hiệu trên MakerEdu Shield.]]
Sau khi kết nối thành công, cấp nguồn vào cổng MicroUSB của MakerEdu Shield sẽ thấy đèn nguồn trên Micro:bit và MakerEdu Shield sáng như hình:
[[File:D5C10512-C9AB-472F-AA49-45807EA5AA25 1 201 a.jpg|alt=Đèn nguồn trên Micro:bit và MakerEdu Shield phát sáng báo hiệu kết nối thành công.|none|thumb|700x700px|Đèn nguồn trên Micro:bit và MakerEdu Shield phát sáng báo hiệu kết nối thành công.]]
=='''[[Hướng dẫn sử dụng phần mềm MakeCode với mạch Micro:bit + MakerEdu Shield for Micro:bit]]'''==
{{Tongquanmakecode}}
==Nhà phân phối==
Có thể mua Mạch Micro:bit MakerEDU Shield tại các nhà phân phối sau:

* [https://hshop.vn/products/mach-micro-bit-makeredu-shield Hshop.vn - Điện tử & Robot.]
