[[image:mkl-m11_UART_control_MP3_Player_module.jpg|thumb|400x400px|MKE-M11 UART control MP3 Player module|link=Special:FilePath/mkl-m11_UART_control_MP3_Player_module.jpg|alt=MKL-M11 UART control MP3 Player module]]
==Giới thiệu==
Mạch phát âm thanh MKE-M11 UART control MP3 Player module được sử dụng để phát âm thanh MP3 từ thẻ nhớ MicroSD, mạch có tích hợp Amply với công suất 2W đi kèm loa tương thích, mạch sử dụng giao tiếp UART nên dễ dàng kết nối và sử dụng với chỉ 2 chân giao tiếp TX và RX.

Mạch phát âm thanh MKE-M11 UART control MP3 Player module thuộc [[MakerEdu|hệ sinh thái phần cứng Robotics MakerEdu]] nên có thể sử dụng trực tiếp an toàn với các mạch điều khiển trung tâm ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....với chuẩn kết nối Connector XH2.54 thông dụng.
==Thông số kỹ thuật==
*Điện áp hoạt động: 5VDC
*Chuẩn giao tiếp: Digital UART
*Điện áp giao tiếp: TTL 3.3/5VDC
*Tích hợp Amply 2W đi kèm loa tương thích.
*Phát âm thanh MP3 từ thẻ nhớ MicroSD
*Sử dụng trực tiếp an toàn với các board mạch giao tiếp ở cả hai mức điện áp 3.3VDC và 5VDC như: Arduino, Raspberry Pi, Jetson Nano, Micro:bit,....
*Bổ sung thêm các thiết kế ổn định, chống nhiễu.
*Chuẩn kết nối:
**1 x Conector XH2.54 4Pins
**1 x Conector XH2.54 3Pins
**1 x Conector Domino 2P
*Thuộc hệ sinh thái phần cứng Robotics MakerEdu, tương thích tốt nhất khi sử dụng với các [[MakerEdu|mạch điều khiển trung tâm của MakerEdu và MakerEdu Shield.]]
==Kích thước==
[[File:FRAME_D2_DFP.JPG|alt=MKL-M11 UART control MP3 Player module dimension|none|thumb|400x400px|MKE-M11 UART control MP3 Player module dimension]]
==Các chân tín hiệu==
[[image:mkl-m11_UART_control_MP3_Player_module_back.jpg|thumb|400x400px|MKE-M11 UART control MP3 Player module back|link=Special:FilePath/mkl-m11_UART_control_MP3_Player_module_back.jpg|alt=MKL-M11 UART control MP3 Player module back]]
{| class="wikitable" border="1"
|-
!MKE-M11
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
|-
|Speaker
|Cổng kết nối loa (công suất tối đa 2W)
|-
|Line Out (R)
|Cổng kết nối đầu ra âm thanh Stereo bên phải (Right)
|-
|Line Out (L)
|Cổng kết nối đầu ra âm thanh Stereo bên trái (Left)
|-
|Line Out (G)
|Cổng kết nối đầu ra âm thanh Stereo tín hiệu Mass chung (GND)
|}
==Hướng dẫn sử dụng với phần mềm Arduino và Vietduino==

===Phần cứng cần chuẩn bị:===
*Mạch phát âm thanh MKE-M11 UART control MP3 Player module
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
* Tải và cài đặt [https://github.com/makerlabvn/mke-m11-control-MP3-player-module-lib bộ thư viện MP3 Player] theo [[Cách cài đặt các thư viện phần cứng Arduino Library|hướng dẫn.]]

=== Chương trình mẫu: ===
<source lang="c++">
// Thêm bộ thư viện MP3 Player.
// Add the MP3 Player library.
#include "SoftwareSerial.h"
#include "DFRobotDFPlayerMini.h"

// Chọn chân cấu hình cho SoftwareSerial.
// Select the configuration pin for SoftwareSerial.
#define TX_PIN 12
#define RX_PIN 13

// Cấu hình chân kết nối tín hiệu cho MP3 Player.
// Configure the signal connection pins for the MP3 Player.
SoftwareSerial mySoftwareSerial(RX_PIN, TX_PIN);
DFRobotDFPlayerMini myDFPlayer;

/* ------------------------------------------------------------------------- */

// Đợi cho đến khi phát nhạc xong.
// Wait until the music play is done.
void waitFinishMusic()
{
  byte count = 0;
  bool wrongStack = false;
  bool timeOut = false;
  while (1)
  {
    if (myDFPlayer.available())
    {
      if (myDFPlayer.readType() == DFPlayerPlayFinished)
      {
        count++;
        if (count == 1)
        {
          break;
        }
      }
      else
      {
        if (myDFPlayer.readType() == WrongStack)
        {
          wrongStack = true;
        }
        else if (myDFPlayer.readType() == TimeOut)
        {
          timeOut = true;
        }
        //
        if (wrongStack && timeOut)
        {
          break;
        }
      }
    }
  }
}

/* ------------------------------------------------------------------------- */

void setup()
{
  // Khởi động kết nối Serial UART ở tốc độ 9600 để truyền dữ liệu lên máy tính.
  // Start the Serial UART connection at 9600 to transfer data to the computer.
  Serial.begin(9600);

  // Khởi động thư viện.
  // Start up the library.
  mySoftwareSerial.begin(9600);
  myDFPlayer.begin(mySoftwareSerial);

  // Cài đặt MP3 Player.
  // Install MP3 Player.
  myDFPlayer.volume(30);
  myDFPlayer.EQ(DFPLAYER_EQ_JAZZ);

  // Cho phát file số 1 đến hết bài.
  // Play file number 1 to the end.
  Serial.println("Play file 1 until done");
  myDFPlayer.playMp3Folder(1);
  waitFinishMusic();
}

void loop()
{
  // Cho phát bài nhạc kế tiếp đến hết bài.
  // Play the next song until the end of the song.
  Serial.print("Play next - ");
  myDFPlayer.next();
  waitFinishMusic();
  Serial.println("Done");
}
</source>

=== Sơ đồ kết nối: ===
{| class="wikitable"
!MakerEdu Shield for Vietduino
! style="text-align:left;" |Arduino/Vietduino
!Mạch Phát Âm Thanh MKE-M11 UART Control MP3 Player Module
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
#Kết nối Mạch Phát Âm Thanh MKE-M11 với mạch MakerEDU Shied for Vietduino qua '''D12,13'''.
#Kết nối mạch Vietduino Uno với máy tính bằng cáp USB và cấu hình mạch trên phần mềm Arduino (Board / Port).
#Nạp chương trình mẫu vào mạch Vietduino Uno.
#Nhấn nút Reset trên mạch Vietduino Uno hoặc mạch MakerEDU Shield for Vietduino để bắt đầu chạy chương trình.

=== Kết quả: ===
...pic

==Hướng dẫn sử dụng với phần mềm mBlock và MakerEdu Creator==
===Phần cứng cần chuẩn bị:===
* [[Mạch phát âm thanh MKE-M11 UART control MP3 Player module]]
* [[Mạch MakerEdu Creator]] 
* Cáp USB để nạp chương trình và cấp nguồn
===Phần mềm cần chuẩn bị:===
*Tải và cài đặt phần mềm mBlock theo [[Giới thiệu và hướng dẫn cài đặt phần mềm mBlock|hướng dẫn.]]
*Tải và cài đặt Driver, cấu hình cho Mạch MakerEdu Creator trên phần mềm mBlock theo [[Cách cài đặt Driver và Device cho mạch MakerEdu Creator trên phần mềm mBlock|hướng dẫn]].
*Tải và cài đặt Extension MakerEdu Hardware trên phần mềm Mblock theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm mBlock|hướng dẫn.]]
===Chương trình mẫu:===

# Trước khi phát nhạc, mạch MakerEdu Creator sẽ cài đặt Volume và EQ cho mạch phát.
# Sau đó cho phát bài nhạc đầu tiên là file 1.
# Đến khi phát xong, sẽ cho phát bài nhạc kế tiếp cho đến khi hết bài, và cho phát bài kế tiếp, cứ thế lặp lại...
# Bên cạnh, bạn cũng có thể xem thông tin MakerEdu Creator trả về qua các "Sprites" trên phần mềm mBlock.

<u>'''Blocks'''</u>

[[File:MBlock M11.PNG|border|700x700px]]

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEdu Creator
!Devices
|-
|Port D3+D2
|Mạch Phát Âm Thanh MKE-M11 UART Control MP3 Player Module
|}
===Các bước tiến hành:===
#Kết nối Mạch Phát Âm Thanh MKE-M11 với mạch MakerEdu Creator qua '''Port D3+D2'''.
#Kết nối mạch MakerEdu Creator với máy tính bằng cáp USB và cấu hình mạch trên phần mềm mBlock.
#Nạp chương trình mẫu vào mạch MakerEdu Creator.
#Nhấn nút Reset trên mạch MakerEdu Creator để bắt đầu chạy chương trình.
===Kết quả:===
...pic

==Hướng dẫn sử dụng với phần mềm MakeCode và Micro:bit==

===Phần cứng cần chuẩn bị:===

* Mạch phát âm thanh MKE-M11 UART control MP3 Player module
* [[Mạch MakerEdu Shield for Micro:bit]]
* [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|Mạch Micro:Bit]]
* Cáp USB để nạp chương trình và cấp nguồn

===Phần mềm cần chuẩn bị:===
*Khởi động phần mềm MakeCode theo [[Giới thiệu về mạch Micro:bit và phần mềm MakeCode|hướng dẫn]].
*Cài đặt Extension MakerEdu Hardware trên MadeCode và tham khảo các khối chức năng theo [[Cách cài đặt Extension và giới thiệu các khối lệnh cho phần cứng MakerEdu trên phần mềm MakeCode|hướng dẫn]].
*Tham khảo cách kết nối và nạp chương trình cho Micro:bit [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên máy tính với phần mềm MakeCode|trên máy tính]] hoặc [[Cách kết nối và nạp chương trình cho mạch Micro:bit trên điện thoại, máy tính bảng với phần mềm MakeCode|điện thoại, máy tính bảng.]]

===Chương trình mẫu:===

# Trước khi phát nhạc, Micro:bit sẽ cài đặt Volume và EQ cho mạch phát.
# Sau đó cho phát bài nhạc đầu tiên là file 1.
# Đến khi phát xong, sẽ cho phát bài nhạc kế tiếp cho đến khi hết bài, và cho phát bài kế tiếp, cứ thế lặp lại...
# Bên cạnh, bạn cũng có thể xem thông tin Micro:bit trả về qua Serial Monitor (chọn đúng COM của Micro:bit và đặt Baudrate 115200).

<u>'''Blocks'''</u>

[[File:MakeCode_M11.png|border|frameless|1000x1000px]]

'''<u>Javascript</u>'''

<source lang="typescript">
// Đặt mức âm lượng là 30 (mức cao nhất)
mp3Player.setVolume(30)
// Đặt EQ là nhạc Jazz
mp3Player.setEQ(mp3Player.EQ.Jazz)

// Lấy thông tin hiện đang cài đặt trong bộ phát nhạc
// Và gửi thông tin đó lên cổng UART
serial.writeString(mp3Player.getInfo())
serial.writeLine("...")

// Dừng 3s
basic.pause(3000)

// Gửi thông tin dưới đây lên cổng UART
serial.writeLine("Play file 1 until done")
// Phát nhạc file 1 cho đến khi hết bài
mp3Player.playFileUntilDone(1)

basic.forever(function () {
  // Gửi thông tin dưới đây lên cổng UART
  serial.writeLine("Play Next")
  // Phát bài tiếp theo cho đến khi hết bài
  mp3Player.playUntilDone(mp3Player.PlayWhat.Next)
})
</source>

===Sơ đồ kết nối:===
{| class="wikitable"
! style="text-align:left;" |MakerEDU Shield for Micro:bit
!Devices
|-
|Port P2+P8
|Mạch Phát Âm Thanh MKE-M11 UART Control MP3 Player Module
|}

===Các bước tiến hành:===
#Kết nối Mạch Phát Âm Thanh MKE-M11 với mạch MakerEDU Shield For Micro:Bit qua '''Port P2+P8'''.
#Gắn bo Micro:Bit lên mạch MakerEDU Shield.
#Kết nối Micro:bit với mạch MakerEdu Shield for Micro:bit
#Nạp chương trình mẫu vào mạch Micro:Bit.
#Nhấn nút Reset trên mạch Micro:Bit để bắt đầu chạy chương trình.

===Kết quả:===
...pic

==Nhà phân phối==
Có thể mua Mạch phát âm thanh MKE-M11 UART control MP3 Player module tại các nhà phân phối sau:
* [https://hshop.vn/products/mach-phat-am-thanh-mkl-m11-uart-control-mp3-player-module Hshop.vn - Điện tử & Robot.]
[[Category:Modules]]
