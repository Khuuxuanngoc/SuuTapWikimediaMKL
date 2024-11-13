[[image:mkl-m10_I2C_motor_control_module.jpg|thumb|400x400px|MKE-M10 I2C motor control module|link=Special:FilePath/mkl-m10_I2C_motor_control_module.jpg|alt=MKL-M10 I2C motor control module]]
==Giới thiệu==
Mạch điều khiển động cơ MKE-M10 I2C motor control module được sử dụng để điều khiển cùng lúc 2 x động cơ DC và 2 x động cơ RC Servo trong các ứng dụng điều khiển robot, xe tự hành, mạch sử dụng giao tiếp I2C nên dễ dàng kết nối và sử dụng với chỉ 2 chân giao tiếp I2C là SDA (data) và SCL (clock).

Mạch điều khiển động cơ MKE-M10 I2C motor control module thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] với chuẩn kết nối connector XH2.54, cảm biến có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm giao tiếp ở cả hai mức điện áp 3.3VDC / 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
{{Kxnwaring
|name= Cảnh báo:
|value=Nếu sử dụng động cơ RC Servo 5VDC công suất lớn có thể gây sụt áp, quá tải, chạy không ổn định, Quý Khách cần mua thêm [[Mạch cấp nguồn bổ sung MKE-M12 5VDC 5A power supply module]] với khả năng cấp nguồn 5VDC với dòng điện cung cấp tối đa lên đến 5A cho cổng POWER+.
}}
==Thông số kỹ thuật==
* Điện áp cấp cho mạch hoạt động: nguồn 5VDC từ cổng POWER+ (IN)
*Điện áp cấp cho động cơ hoạt động VM (V_Motor): nguồn VIN 6~12VDC từ cổng POWER+ (IN)
*Dòng cấp tối đa cho mỗi động cơ: 1.2A
*Chuẩn giao tiếp: Digital I2C
* Các chân giao tiếp: SDA (Serial Data) / SCL (Serial Clock)
*Điện áp giao tiếp: TTL 3.3/5VDC
*Địa chỉ I2C: 64~68 địa chỉ (có thể cài đặt hoặc thay đổi trong code)
*Điều khiển được 2 động cơ DC và 2 động cơ RC Servo cùng lúc.
* Sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
* Bổ sung thêm các thiết kế ổn định, chống nhiễu.
*Chuẩn kết nối:
**2 x Conector XH2.54 4Pins (cổng I2C và POWER+ (IN))
**2 x Conector Domino 2P (MotorA và MotorB)
**2 x Male Header 3P 2.54mm (RC Servo S1 và S2)
*Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
==Kích thước==
[[File:FRAME_Edu_Motor_V3.JPG|alt=MKL-M10 I2C motor control module dimension|none|thumb|400x400px|MKE-M10 I2C motor control module dimension]]
==Các chân tín hiệu==
[[image:mkl-m10_I2C_motor_control_module_back.jpg|thumb|400x400px|MKE-M10 I2C motor control module back|link=Special:FilePath/mkl-m10_I2C_motor_control_module_back.jpg|alt=MKL-M10 I2C motor control module back]]
{| class="wikitable" border="1"
|-
!MKE-M10 / Cổng tín hiệu I2C
!Ghi chú
|-
|GND
|Chân cấp nguồn âm 0VDC
|-
|NC
| Không kết nối (not connect)
|-
|SDA
|Chân tín hiệu I2C Serial Data
|-
|SCL
|Chân tín hiệu I2C Serial Clock
|}
{| class="wikitable" border="1"
|-
!MKE-M10 / Cổng cấp nguồn Power+ (IN)
!Ghi chú
|-
|GND
|Chân cấp nguồn âm 0VDC
|-
|VM (6~12V)
|Chân cấp nguồn 6~12VDC cho động cơ hoạt động
(lấy từ nguồn VIN của cổng POWER+)
|-
|5V
|Chân nguồn 5VDC cấp cho mạch hoạt động
(lấy từ nguồn 5VDC của cổng POWER+)
|-
|NC
|Không kết nối (not connect)
|}
{| class="wikitable" border="1"
|-
!MKE-M10 / Cổng kết nối động cơ
!Ghi chú
|-
|MotorA
|Cổng kết nối động cơ DC A
|-
| MotorB
|Cổng kết nối động cơ DC B
|-
|S1, +, -
|Cổng kết nối động cơ RC Servo S1 (điện áp hoạt động lấy từ nguồn 5VDC của cổng POWER+)
|-
|S2, +, -
|Cổng kết nối động cơ RC Servo S1 (điện áp hoạt động lấy từ nguồn 5VDC của cổng POWER+)
|}
==Hướng dẫn sử dụng với phần mềm Arduino và Vietduino==
===Cài đặt thư viện cho Arduino IDE:===
* Tham khảo [[Cách cài đặt các thư viện phần cứng Arduino Library]] để cài đặt hoặc cập nhật phiên bản thư viện mới nhất.
Tên thư viện sử dụng trong Arduino IDE: '''Makerlabvn_I2C_Motor_Driver'''
[[File:Makerlabvn_I2C_motor_driver_1_install_lib.JPG|alt=Makerlabvn_I2C_motor_driver_1_install_lib|none|thumb|700x700px|Makerlabvn_I2C_motor_driver_1_install_lib]]
* Upload chương trình mẫu: MKL-M10_I2C_motor_control_module_Speed_Direction
[[File:Makerlabvn_I2C_motor_driver_2_Example.JPG|alt=Makerlabvn_I2C_motor_driver_2_Example|none|thumb|700x700px|Makerlabvn_I2C_motor_driver_2_Example]]
<source lang="C++">
// M10_I2C_motor_control_module_Speed_Direction.ino

/* ----------------------------------------------------- */

#include "Makerlabvn_I2C_Motor_Driver.h"

Makerlabvn_I2C_Motor_Driver myDriver(0);

unsigned long timeDelay = 2000; //2000ms 

void setup()
{
    // put your setup code here, to run once:
    myDriver.begin();
}

void loop()
{
    myDriver.writeS1(45);
    myDriver.writeS2(135);
    myDriver.writeMA(1, 50);
    myDriver.writeMB(1, 50);
    delay(timeDelay);

    myDriver.writeS1(90);
    myDriver.writeS2(90);
    myDriver.writeMA(1, 0);
    myDriver.writeMB(1, 0);
    delay(timeDelay);

    myDriver.writeS1(135);
    myDriver.writeS2(45);
    myDriver.writeMA(0, 100);
    myDriver.writeMB(0, 100);
    delay(timeDelay);

    myDriver.writeS1(0);
    myDriver.writeS2(0);
    myDriver.writeMA(0, 0);
    myDriver.writeMB(0, 0);
    delay(timeDelay);
}
</source>
===Các phần cứng sử dụng:===
* Mạch điều khiển động cơ MKE-M10 I2C motor control module
* [[Mạch Vietduino Uno (Arduino Uno Compatible)]]
* [[Mạch MakerEdu Shield for Vietduino]]
* Nguồn 9V 2A để cấp nguồn cho hệ thống.
* Cáp USB upload code
* 2 x Motor RC Servo 9G
* 2 x Motor giảm tốc V1
{{kxninfo
|name=Lưu ý:
|value=Nếu không có mạch Vietduino Uno bạn vẫn có thể sử dụng mạch Vietduino Mega 2560, Arduino Uno, Arduino Mega 2560 hoặc các mạch phần cứng có cấu trúc các chân GPIO tương tự.
}}

{| class="wikitable"
! style="text-align:left;" |Arduino/Vietduino
!Mạch điều khiển động cơ MKE-M10 I2C motor control module
|-
|GND
| GND
|-
|5V
|5V
|-
|SDA
|SDA
|-
|SCL
|SCL
|-
|VIN
|VM
|}
===Kết nối phần cứng:===
[[File:Makerlabvn_I2C_motor_driver_3_Wiring.JPG|alt=Makerlabvn_I2C_motor_driver_3_Wiring|none|thumb|700x700px|Makerlabvn_I2C_motor_driver_3_Wiring]]

===Video Demo:===

==Nhà phân phối==
Có thể mua Mạch điều khiển động cơ MKE-M10 I2C motor control module tại các nhà phân phối sau:
* [https://hshop.vn/products/mach-dieu-khien-dong-co-mkl-m10-i2c-motor-control-module Hshop.vn - Điện tử & Robot.]
[[Category:Modules]]
