[[image:mkl-m15_bluetooth_dual_mode_module.jpg|thumb|270x270px|MKE-M15 Bluetooth 3.0 SPP / BLE 4.2 Dual Mode module|link=Special:FilePath/mkl-m15_bluetooth_dual_mode_module.jpg]]
==Giới thiệu==
Mạch thu phát MKE-M15 Bluetooth 3.0 SPP / BLE 4.2 Dual Mode module được sử dụng để truyền nhận dữ liệu qua Bluetooth với các Máy Tính, Điện Thoại Smart Phone hỗ trợ Bluetooth 3.0 SPP và BLE 4.2, ở chế độ Bluetooth 3.0 SPP mạch có thể được sử dụng để thay thế các mạch Bluetooth HC-05/HC-06 với độ tương thích gần như hoàn toàn (có thể thay thế mà không cần chỉnh sửa code), với BLE 4.2 mạch có thể kết nối với hầu hết các Smartphone mới nhất hiện nay sử dụng hệ điều hành Android / IOS như: Iphone, Ipad,..., mạch sử dụng chuẩn giao tiếp UART, hỗ trợ bộ tập lệnh AT Commands rất dễ dàng để kết nối và sử dụng.

Mạch thu phát MKE-M15 Bluetooth 3.0 SPP / BLE 4.2 Dual Mode module thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.
==Thông số kỹ thuật==
*Module Bluetooth sử dụng: JDY-33
*Điện áp hoạt động: 5VDC
* Điện áp giao tiếp: TTL 3.3VDC/5VDC
* Chuẩn giao tiếp: Digital UART
*Baudrate Default: 9600, N, 8, 1
*Hỗ trợ cấu hình qua bộ tập lệnh AT Commands.
*Chuẩn kết nối Bluetooth: Bluetooth 3.0 SPP và BLE 4.2 (tương thích Máy Tính, Điện Thoại Smart Phone hỗ trợ Bluetooth 2.0 / 3.0 và 4.0)
*Tần số sóng: 2.4Ghz
*Khoảng cách truyền nhận tối đa: 30m
*Tương thích hệ điều hành: Windows / Android / IOS
* Sử dụng trực tiếp an toàn với các board mạch giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
* Bổ sung thêm các thiết kế ổn định, chống nhiễu.
* Chuẩn kết nối: Conector XH2.54 4Pins
* Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
==Bộ tập lệnh AT Commands==
Nếu muốn thay đổi các thiết lập mặc định (thường không cần thiết), bạn có thể sử dụng bộ tập lệnh cấu hình AT Commands để cấu hình lại cho Mạch thu phát MKE-M15 Bluetooth 3.0 SPP / BLE 4.2 Dual Mode module, tuy nhiên việc này cần sử dụng thêm mạch chuyển USB-UART hoặc lập trình qua Arduino, xin lưu ý thiết lập đúng '''Baudrate Default: 9600, N, 8, 1''' và sau các lệnh AT cần thêm '''\r\n''':
[[File:MKL-M15 Bluetooth Dual Mode.jpg|alt=Mạch thu phát MKE-M15 Bluetooth 3.0 SPP - BLE 4.2 Dual Mode module AT Commands|none|thumb|726x726px|Mạch thu phát MKE-M15 Bluetooth 3.0 SPP - BLE 4.2 Dual Mode module AT Commands]]
==Kích thước==
[[File:FRAME_D2_DFP.JPG|alt=MKL-M15 Bluetooth 3.0 SPP / BLE 4.2 Dual Mode module dimension|none|thumb|400x400px|MKE-M15 Bluetooth 3.0 SPP / BLE 4.2 Dual Mode module dimension]]
==Các chân tín hiệu==
[[image:mkl-m15_bluetooth_dual_mode_module_back.jpg|thumb|279x279px|MKE-M15 Bluetooth 3.0 SPP / BLE 4.2 Dual Mode module back|link=Special:FilePath/mkl-m15_bluetooth_dual_mode_module_back.jpg]]
{| class="wikitable" border="1"
|-
!MKE-M15
!Ghi chú
|-
|GND
|Chân cấp nguồn âm 0VDC
|-
|5V
|Chân cấp nguồn dương 5VDC
|-
|TX
|Chân truyền tín hiệu UART Transmitter
|-
|RX
| Chân nhận tín hiệu UART Receiver
|}
==Hướng dẫn sử dụng với phần mềm Arduino và Vietduino==

===Phần cứng cần chuẩn bị:===
*Mạch thu phát MKE-M15 Bluetooth 3.0 SPP / BLE 4.2 Dual Mode module
*[[Mạch Vietduino Uno (Arduino Uno Compatible)]]
*[[Mạch MakerEdu Shield for Vietduino]]
*Cáp USB để nạp chương trình và cấp nguồn

{{Tr-Info
|name=Lưu ý:
|value=Nếu không có mạch Vietduino Uno bạn vẫn có thể sử dụng mạch Vietduino Mega 2560, Arduino Uno, Arduino Mega 2560 hoặc các mạch phần cứng có cấu trúc các chân GPIO tương tự.
}}

=== Phần mềm cần chuẩn bị: ===
* Tải và cài đặt phần mềm Arduino theo [[Cách cài đặt phần mềm Arduino IDE|hướng dẫn.]]
* Tải và cài đặt Driver, cấu hình cho mạch Vietduino Uno trên phần mềm Arduino theo [[Cách cài đặt Driver và nạp chương trình cho mạch Arduino / Arduino Compatible|hướng dẫn.]]
* Tải và cài đặt [https://github.com/makerlabvn/mke-m15-bluetooth-dabble-module-lib bộ thư viện Dabble] (sử dụng App Dabble điều khiển bo Arduino qua Bluetooth) theo [[Cách cài đặt các thư viện phần cứng Arduino Library|hướng dẫn.]]

=== Chương trình mẫu: ===
<source lang="c++">
// Thêm bộ thư viện GamePad Dabble.
// Add the GamePad Dabble library.
#define CUSTOM_SETTINGS
#define INCLUDE_GAMEPAD_MODULE
#include <Dabble.h>

// Chọn chân cấu hình cho mô-đun Bluetooth.
// Select the configuration pin for the Bluetooth module.
#define TX_PIN 12
#define RX_PIN 13

void setup()
{
  // Khởi động kết nối Serial UART ở tốc độ 9600 để truyền dữ liệu lên máy tính.
  // Start the Serial UART connection at 9600 to transfer data to the computer.
  Serial.begin(9600);

  // Khởi động thư viện và cấu hình các chân kết nối.
  // Start the library and configure the pins.
  Dabble.begin(115200, RX_PIN, TX_PIN);
}

void loop()
{
  /**
   * Hàm này được sử dụng để làm mới dữ liệu thu được từ điện thoại thông minh.
   * Do đó, việc gọi hàm này là bắt buộc để nhận dữ liệu chính xác từ điện thoại di động của bạn.
   */
  Dabble.processInput();

  // Truyền tên nút bấm từ điện thoại lên máy tính.
  // Transfer button names from phone to computer.
  if (GamePad.isUpPressed())
  {
    Serial.println("UP");
  }
  if (GamePad.isDownPressed())
  {
    Serial.println("DOWN");
  }
  if (GamePad.isLeftPressed())
  {
    Serial.println("LEFT");
  }
  if (GamePad.isRightPressed())
  {
    Serial.println("RIGHT");
  }

  // Chờ 0,05s mới kiểm tra lại.
  // Wait 0,05s to check again.
  delay(50);
}
</source>

=== Sơ đồ kết nối: ===
{| class="wikitable"
!MakerEdu Shield for Vietduino
! style="text-align:left;" |Arduino/Vietduino
!Mạch Thu Phát MKE-M15 Bluetooth 3.0 SPP / BLE 4.2 Dual Mode Module
|-
| rowspan="2" |Port D12,13
|D12 (TX)
|RX
|-
|D13 (RX)
|TX
|}

=== Các bước tiến hành: ===
#Kết nối mạch Vietduino Uno với mạch MakerEDU Shield for Vietduino.
#Kết nối Mạch Thu Phát Bluetooth MKE-M15 với mạch MakerEDU Shied for Vietduino qua '''Port D12,13'''.
#Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port).
#Nạp chương trình mẫu vào mạch Vietduino Uno.
#Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.

=== Kết quả: ===
...pic

==Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator==
===Phần cứng cần chuẩn bị:===
* Mạch thu phát MKE-M15 Bluetooth 3.0 SPP / BLE 4.2 Dual Mode module
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Creator]] 
* Cáp USB để nạp chương trình và cấp nguồn
===Phần mềm cần chuẩn bị:===
*Tải và cài đặt phần mềm mBlock theo [[Giới thiệu và hướng dẫn cài đặt phần mềm mBlock|hướng dẫn.]]
*Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn]].
*Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm mBlock|hướng dẫn.]]
===Chương trình mẫu:===

# Sau khi bạn đã mở app Dabble, vào giao diện Control và kết nối Bluetooth thành công.
# Mỗi khi bạn bấm các nút mũi tên hướng trên điện thoại, tín hiệu sẽ được gửi về mạch MakerEdu Creator qua Bluetooth.
# Mạch MakerEdu Creator sẽ cho hiển thị tên nút nhấn tương ứng, gồm UP/DOWN/LEFT/RIGHT lên màn hình LCD.

<u>'''Blocks'''</u>

[[File:MBlock M15.PNG|border|700x700px]]

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEdu Creator
!Devices
|-
|Port UART
|Mạch Thu Phát MKE-M15 Bluetooth 3.0 SPP / BLE 4.2 Dual Mode Module
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}
===Các bước tiến hành:===
#Kết nối Mạch Thu Phát Bluetooth MKE-M15 với mạch MakerEdu Creator qua '''Port UART'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEdu Creator qua '''Port I2C'''.
#Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
#Nạp chương trình mẫu vào mạch MakerEdu Creator.
#Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.
===Kết quả:===
...pic

== Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bit ==
{{Tr-Info
|name=Lưu ý:
|value=Mạch Micro:bit có tích hợp sẵn Bluetooth trên mạch nên sẽ không cần sử dụng thêm mạch Bluetooth MKE-M15, tham khảo các khối lệnh cho Bluetooth của Micro:bit [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm MakeCode|tại đây.]]
}}

==Nhà phân phối==
Có thể mua Mạch thu phát MKE-M15 Bluetooth 3.0 SPP / BLE 4.2 Dual Mode module tại các nhà phân phối sau:
* [https://hshop.vn/products/mach-thu-phat-mke-m15-bluetooth-3-0-spp-ble-4-2-dual-mode-module Hshop.vn - Điện tử & Robot.]
[[Category:Modules]]
