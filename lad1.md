## การทดลองที่ 1 เรื่องการเขียนโปรแกรมเพื่อรันบนไมโครคอนโทรเลอร์ 

### วัตถุประสงค์
1. เพื่อทดสอบการใช้งานของอุปกรณ์ไมโครคอนโทรเลอร์ (ESP-01)


### อุปกรณ์ที่ใช้
1. ไมโครคอนโทรเลอร์ (ESP-01)
![Image](https://ae01.alicdn.com/kf/HTB1QMy2J9zqK1RjSZFpq6ykSXXac/ESP8266-ESP-01-ESP01-Serial-WIFI-3-3V-5V-Serial.jpg)
3. อุปกรณ์เชื่อมต่อแบบ USB
4. ซีเรียล


### ศึกษาข้อมูลเบื้องต้น
#### 01 run example
https://www.youtube.com/watch?v=NLIUsWLEpmg 

#### ESP-01
https://suppakorn_somnuk.gitbooks.io/esp8266/content/esp-01-and-esp-12e.html

#### PlatformIO
https://platformio.org/


### วิธีการทดลอง
1. เขียนโปรแกรมลงใน **visual studio code** โดยใช้ภาษา C
```C
#include <Arduino.h>

int cnt = 0;

void setup()
{
	Serial.begin(115200);
}

void loop()
{
	cnt++;
	Serial.printf("PATTANI :%d\n",cnt);
	delay(1000);
}


```
 
2. ต่ออุปกรณ์ USB เข้ากับซีเรียล
3. ต่อซีเรียลเข้ากับไมโครคอนโทรเลอร์
4. เปิด Command Prompt แล้วเข้าไปในโฟล์เดอร์ที่จะอัพโหลด เช่น ไดฟ์ D ไฟล์ ชื่อ test microcontroller
  พิมพ์ **d:** แล้วกด **Enter**
  พิมพ์ **cd test microcontroller** แล้วกด **Enter**
  จะแสดงโปรแกรมทั้งหมด 9 ตัว
    * 01_Serial-Monitor
    * 02_Scan-Wifi
    * 03_Output-Port
    * 04_Input-Port
    * 05_Wifi-Wed-Server
    * 06_Wifi-AP-Web-Server
    * 07_Wed-Server-OnOff
    * 08_MQTT-publish
    * 09_MQTT-subscript
* โดยการทดลองที่ 1 จะเป็นทดสอบไมโครคอนโทรเลอร์ จึงเรียกใช้ โปรแกรมที่โดยพิม **cd 01_Serial-Monitor** แล้วกด **Enter**
 สามารถเช็คโปรแกรมที่ใช้รันได้โดย พิมพ์ **vi src/main.cpp** แล้วกด **Enter**โดยจะแสดงโค้ดที่เขียนจากข้อที่ 1
5. สามารถเช็ค PlatformIO ได้ โดยพิมพ์ **vi platformio.ini** แล้วกด **Enter** จะแสดง
```
; IOT for KIDS
;
; By Dr.Choompol Boonmee
;

[env:exercise01]
platform = espressif8266
board = esp01_1m
framework = arduino
board_build.flash_mode = dout

upload_port = /dev/cu.usbserial-1420
;up;oad_port = COM3

monitor_port = /dev/cu.usbserial-1420
;monitor_port = COM3
monitor_speed = 115200
```
6. อัพโหลดโปรแกรม โดยพิมพ์ **pio run -t upload** แล้วกด **Enter** ในขณะที่รันโปรแกรมเพื่อให้ไมโครคอนโทรเลอร์รับโปกรแกรมใหม่เข้าไป ให้กดปุ่มดำค้าง แล้วกดปุ่มแดง 1 ครั้ง เพิ่มเป็นการรีเซต
7. เมื่อลงโปรแกรมเสร็จแล้ว พิมพ์ **pio device monitor** แล้วกด **Enter** เพื่อดูผลลัพท์โดยการแสดงผลจากคอมพิวเตอร์
8. สังเกต บันทึกผล และอธิปรายผล


### การบันทึกผลการทดลอง
เมื่อรันโปรแกรมเข้าไมโครคอนเลอร์ ไมโครคอนโทรเลอร์จะนับไปเรื่อยๆ


### อภิปรายผลการทดลอง
  จากการทดลอง พบว่า ไมโครคอนโทรเลอร์สามารถนับจำนวนครั้งได้ทุก 1 วิ แสดงว่าอุปกรณ์ไมโครคอนเลอร์ใช้งานได้เนื่องจากได้ทดสอบเขียนโปรแกรมให้นับเลขเพิ่มทุก ๆ 1 วินาที
  
  
### คำถามหลังการทดลอง
  * การทดสอบโดยการรันโปรแกรมนับเลขทุก ๆ วินาทีเข้าไปในไมโครคอนโทรเลอร์ สามารถเช็ตการใช้งานได้อย่างไร
  * สามารถใช้วิธีอื่นในการเช็คว่าไมโครคอนโทรเลอร์ยังใช้งานได้อยู่หรือไม่ พร้อมยกตัวอย่าง

## จบการทดลองที่ 1 เพียงเท่านั้น
### หากมีข้อผิดพลาดประการใดข้ออภัยมา ณ ที่นี้ด้วย
## :+1: :+1:  :+1:  :+1:  :+1:  
