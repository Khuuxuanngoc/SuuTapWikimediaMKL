[[image:mkl-m13_I2C_POWER_port_expander_module.jpg|thumb|400x400px|MKE-M13 I2C/POWER port expander module|link=Special:FilePath/mkl-m13_I2C_POWER_port_expander_module.jpg]]
==Giới thiệu==
Mạch mở rộng cổng kết nối MKE-M13 I2C/POWER port expander module thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] với chuẩn kết nối connector XH2.54 thông dụng giúp mở rộng thêm cổng kết nối nguồn POWER+ hoặc cổng I2C để có thể cấp nguồn và giao tiếp với nhiều thiết bị, mạch còn được thiết kế thêm cổng mở rộng dạng Domino để có thể kết nối linh hoạt.
==Thông số kỹ thuật==
* Cổng đầu vào INPUT:
** 1 x Conector XH2.54 4Pins
* Cổng đầu ra OUTPUT:
** 3 x Conector XH2.54 4Pins
** 1 x Conector Domino 4P
* Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
{{kxnKichThuocFrame_A
|name=MKL-M13 I2C/POWER port expander module dimension
}}
==Các chân tín hiệu==
[[image:mkl-m13_I2C_POWER_port_expander_module_back.jpg|thumb|400x400px|MKE-M13 I2C/POWER port expander module back|link=Special:FilePath/mkl-m13_I2C_POWER_port_expander_module_back.jpg]]
{| class="wikitable" border="1"
|-
! Sử dụng để mở rộng cổng POWER+
! Sử dụng để mở rộng cổng I2C
|-
| 3V3
| SCL
|-
| 5V
| SDA
|-
| VIN
| 5V
|-
|GND
|GND
|}
==Hướng dẫn sử dụng với MakerEdu Shield==
===Các phần cứng sử dụng:===
* Mạch mở rộng cổng kết nối MKE-M13 I2C/POWER port expander module
* [[Mạch Vietduino Uno (Arduino Uno Compatible)]]
* [[Mạch MakerEdu Shield for Vietduino]]
{{kxninfo
|name=Lưu ý:
|value=*Nếu không có mạch Vietduino Uno bạn vẫn có thể sử dụng mạch Vietduino Mega 2560, Arduino Uno, Arduino Mega 2560 hoặc các mạch phần cứng có cấu trúc các chân GPIO tương tự.
}}
===Các bước tiến hành:===
# Kết nối mạch MakerEdu Shield for Vietduino vào mạch Vietduino Uno.
# Kết nối cổng (INPUT) của Mạch mở rộng cổng kết nối MKE-M13 I2C/POWER port expander module vào cổng (POWER+ (Out)) hoặc cổng (I2C) trên mạch MakerEDU Shield for Vietduino để mở rộng thêm kết nối.
# Các cổng (OUTPUT) trên Mạch mở rộng cổng kết nối MKE-M13 I2C/POWER port expander module có các tín hiệu được nối song song với cổng (INPUT) nên sẽ có chức năng tương đương như cổng (INPUT) để có thể kết nối thêm nhiều thiết bị khác nhau.
==Nhà phân phối==
Có thể mua Mạch mở rộng cổng kết nối MKE-M13 I2C/POWER port expander module tại các nhà phân phối sau:
* [https://hshop.vn/products/mach-mo-rong-cong-ket-noi-mkl-m13-i2c-power-port-expander-module Hshop.vn - Điện tử & Robot.]
[[Category:Modules]]
