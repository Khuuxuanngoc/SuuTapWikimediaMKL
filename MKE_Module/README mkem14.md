[[image:mkl-m14_ir_remote_control_receiver_module.jpg|thumb|302x302px|MKE-M14 VS1838 IR remote control receiver module|link=Special:FilePath/mkl-m14_ir_remote_control_receiver_module.jpg]]
==Giới thiệu==
Mạch thu hồng ngoại MKE-M14 VS1838 IR remote control receiver module được sử dụng để nhận tín hiệu hồng ngoại từ các nút nhấn của remote (điều khiển từ xa), có thể được sử dụng để điều khiển robot, bật tắt đèn hoặc các ứng dụng điều khiển từ xa bằng hồng ngoại.

Mạch thu hồng ngoại MKE-M14 VS1838 IR remote control receiver module thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.
==Thông số kỹ thuật==
*Mắt hồng ngoại sử dụng: [https://www.mediafire.com/file/mw4tgqtz8au4cqa/&#x5B;Hshop.vn&#x5D;+VS1838+Datasheet.pdf/file VS1838]
*Điện áp hoạt động: 5VDC
*Chuẩn giao tiếp: Digital
* Điện áp giao tiếp: TTL 3.3VDC/5VDC
* Nhận tín hiệu hồng ngoại từ các nút nhấn của remote (điều khiển từ xa).
* Sử dụng trực tiếp an toàn với các board mạch giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
* Bổ sung thêm các thiết kế ổn định, chống nhiễu.
* Chuẩn kết nối: connector XH2.54 3Pins
* Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
{{kxnKichThuocFrame_A
|name=MKL-M14 VS1838 IR remote control receiver module dimension
}}
==Các chân tín hiệu==
[[image:mkl-m14_ir_remote_control_receiver_module_back.jpg|thumb|293x293px|MKE-M14 VS1838 IR remote control receiver module back|link=Special:FilePath/mkl-m14_ir_remote_control_receiver_module_back.jpg]]
{| class="wikitable" border="1"
|-
!MKE-M14
!Ghi chú
|-
|GND
|Chân cấp nguồn âm 0VDC
|-
|5V
| Chân cấp nguồn dương 5VDC
|-
|SIG
|Chân tín hiệu Digital In
|}
==Hướng dẫn sử dụng với phần mềm Arduino và Vietduino==

===Phần cứng cần chuẩn bị:===
*[[Mạch thu hồng ngoại MKE-M14 VS1838 IR remote control receiver module]]
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
* Tải và cài đặt [https://github.com/makerlabvn/mke-m14-IR-remote-control-receiver-module-lib bộ thư viện IR1838] theo [[Cách cài đặt các thư viện phần cứng Arduino Library|hướng dẫn.]]

=== Chương trình mẫu: ===
<source lang="c++">
// Thêm bộ thư viện IR1838.
// Add the IR1838 library.
#include <IRremote.h>

// Chọn chân đọc IR1838.
// Select the pin to read the IR1838.
#define IR_PIN 11

// Lưu giá trị "command" của tín hiệu IR.
// Store the "command" value of the IR signal.
long commandIR = 0;

void setup()
{
  // Khởi động kết nối Serial UART ở tốc độ 9600 để truyền dữ liệu lên máy tính.
  // Start the Serial UART connection at 9600 to transfer data to the computer.
  Serial.begin(9600);

  // Khởi động thư viện.
  // Start up the library.
  IrReceiver.begin(IR_PIN);
}

void loop()
{
  // Kiểm tra IR1838 xem có nhận được tín hiệu IR nào không?
  // Check IR1838 to see if an IR signal is received?
  if (IrReceiver.decode())
  {
    IrReceiver.resume();
    if (IrReceiver.decodedIRData.protocol == UNKNOWN)
    {
      commandIR = -1;
    }
    else
    {
      commandIR = IrReceiver.decodedIRData.command;
    }
  }
  else
  {
    commandIR = 0;
  }

  // Nếu phát hiện tín hiệu IR sẽ cho in giá trị lên màn hình máy tính.
  // If IR signal is detected, the value will be printed on the computer screen.
  if (commandIR != 0)
  {
    Serial.print("Command: ");
    Serial.println(commandIR);
  }
}
</source>

=== Sơ đồ kết nối: ===
{| class="wikitable"
!MakerEdu Shield for Vietduino
! style="text-align:left;" |Arduino/Vietduino
!Devices
|-
|Port D11
|D11
|Mạch Thu Hồng Ngoại MKE-M14 VS1838 IR Remote Control Receiver Module
|}

=== Các bước tiến hành: ===
#Kết nối mạch Vietduino Uno với mạch MakerEDU Shield for Vietduino.
#Kết nối Mạch Thu Hồng Ngoại MKE-M14 với mạch MakerEDU Shied for Vietduino qua '''Port D11'''.
#Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port).
#Nạp chương trình mẫu vào mạch Vietduino Uno.
#Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.

=== Kết quả: ===
...pic

==Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator==
===Phần cứng cần chuẩn bị:===
* [[Mạch thu hồng ngoại MKE-M14 VS1838 IR remote control receiver module]]
* [[Mạch hiển thị MKE-M07 LCD1602 I2C module]]
* [[Mạch MakerEdu Creator]] 
* Cáp USB để nạp chương trình và cấp nguồn
===Phần mềm cần chuẩn bị:===
*Tải và cài đặt phần mềm mBlock theo [[Giới thiệu và hướng dẫn cài đặt phần mềm mBlock|hướng dẫn.]]
*Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn]].
*Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm mBlock|hướng dẫn.]]
===Chương trình mẫu:===

# Mạch MakerEdu Creator luôn liên tục kiểm tra có giá trị trả về từ mạch thu hồng ngoại không?
# Nếu mạch thu nhận được tín hiệu hồng ngoại từ bất kì Remote IR.
# MakerEdu Creator sẽ cho hiển thị phần thông tin "Command" của tín hiệu đó lên màn hình LCD.

<u>'''Blocks'''</u>

[[File:MBlock M14.PNG|border|700x700px]]

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEdu Creator
!Devices
|-
|Port D12
|Mạch Thu Hồng Ngoại MKE-M14 VS1838 IR Remote Control Receiver Module
|-
|Port I2C
|Mạch Hiển Thị MKE-M07 LCD1602 I2C Module
|}
===Các bước tiến hành:===
#Kết nối Mạch Thu Hồng Ngoại MKE-M14 với mạch MakerEdu Creator qua '''Port D12'''.
#Kết nối Mạch Hiển Thị MKE-M07 với mạch MakerEdu Creator qua '''Port I2C'''.
#Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
#Nạp chương trình mẫu vào mạch MakerEdu Creator.
#Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.
===Kết quả:===
...pic

==Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bit==

===Phần cứng cần chuẩn bị:===

* [[Mạch thu hồng ngoại MKE-M14 VS1838 IR remote control receiver module]]
* [[Mạch MakerEdu Shield for Micro:bit]]
* [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|Mạch Micro:Bit]]
* Cáp USB để nạp chương trình và cấp nguồn

===Phần mềm cần chuẩn bị:===
*Khởi động phần mềm MakeCode theo [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|hướng dẫn]].
*Cài đặt Extension MakerEdu Hardware trên MadeCode và tham khảo các khối chức năng theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm MakeCode|hướng dẫn]].
*Tham khảo cách kết nối và nạp chương trình cho Micro:bit [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên máy tính với phần mềm MakeCode|trên máy tính]] hoặc [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên điện thoại, máy tính bảng với phần mềm MakeCode|điện thoại, máy tính bảng.]]

===Chương trình mẫu:===

# Micro:bit luôn liên tục kiểm tra có giá trị trả về từ mạch thu hồng ngoại không?
# Nếu mạch thu nhận được tín hiệu hồng ngoại từ bất kì Remote IR.
# Micro:bit sẽ cho hiển thị mọi thông tin của tín hiệu đó qua giao thức UART.
# Bạn có thể xem thông tin Micro:bit trả về qua Serial Monitor (chọn đúng COM của Micro:bit và đặt Baudrate 115200).

<u>'''Blocks'''</u>

[[File:MakeCode_M14.png|border|frameless|1000x1000px]]

'''<u>Javascript</u>'''

<source lang="typescript">
/**
 * Code này giúp bạn biết được toàn bộ thông tin dạng văn bản
 * Nhận được từ mỗi nút bấm của Remote IR
 * Dưới dạng các giá trị HEX
 */

let dataIR = ""
basic.forever(function () {
  dataIR = ir1838.printValueIR(ir1838.PinKit.P0)
  if (dataIR != "NONE") {
    serial.writeString(dataIR)
    serial.writeLine("...")
  }
})
</source>

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEDU Shield
!Devices
|-
|Port P0
|Mạch Thu Hồng Ngoại MKE-M14 VS1838 IR Remote Control Receiver Module
|}

===Các bước tiến hành:===
#Kết nối Mạch Thu Hồng Ngoại MKE-M14 với mạch MakerEDU Shield For Micro:Bit qua '''Port P0'''.
#Gắn bo Micro:Bit lên mạch MakerEDU Shield.
# Kết nối Micro:bit với mạch MakerEdu Shield for Micro:bit
# Nạp chương trình mẫu vào mạch Micro:Bit.
# Nhấn nút Reset trên mạch Micro:Bit để bắt đầu chạy chương trình.

===Kết quả:===
...pic

==Nhà phân phối==
Có thể mua Mạch thu hồng ngoại MKE-M14 VS1838 IR remote control receiver module tại các nhà phân phối sau:
* [https://hshop.vn/products/mach-thu-hong-ngoai-mkl-m14-vs1838-ir-remote-control-receiver-module Hshop.vn - Điện tử & Robot.]
[[Category:Modules]]
