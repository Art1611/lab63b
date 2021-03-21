## การทดลองที่ 6 เรื่อง การเขียนโปรแกรมสร้างไวไฟแอคเซสพอยต์ (Wifi AP)

### วัตถุประสงค์
1. เพื่อศึกษาการันโปรแกรมสร้างไวไฟของไมโครคอนโทรเลอร์


### อุปกรณ์ที่ใช้
1. ไมโครคอนโทรเลอร์ (ESP-01)
2. อุปกรณ์เชื่อมต่อแบบ USB
3. ซีเรียล


### ศึกษาข้อมูลเบื้องต้น
#### 06 run wiri AP
https://www.youtube.com/watch?v=T26DVHePlTs



### วิธีการทดลอง
1. เขียนโปรแกรมลงใน **visual studio code** โดยใช้ภาษา C
```C
#include <ESP8266WiFi.h>
#include <ESP8266WebServer.h>

const char* ssid = "TUENG-ESP-WIFI";
const char* password = "choompol";

IPAddress local_ip(192, 168, 1, 1);
IPAddress gateway(192, 168, 1, 1);
IPAddress subnet(255, 255, 255, 0);

ESP8266WebServer server(80);

int cnt = 0;

void setup(void){
	Serial.begin(115200);

	WiFi.softAP(ssid, password);
	WiFi.softAPConfig(local_ip, geteway, subnet);
	delay(100);

	server.onNotFound([]() {
		server.send(404, "text/plain", "Path Not Found");
	});

	server.on("/", []() {
		cnt++;
		String msg = "Hello cnt: ";
		msg += cnt;
		server.send(200, "text/plain",msg);
	});

	server.begin();
	Serial.println("HTTP server started");
}

void loop(void){
	server.handleClient();
}


```
 
2. ต่ออุปกรณ์ USB เข้ากับซีเรียล
3. ต่อซีเรียลเข้ากับไมโครคอนโทรเลอร์
4. เปิด Command Prompt แล้วเข้าไปในโฟล์เดอร์ที่จะอัพโหลด เช่น ไดฟ์ D ไฟล์ ชื่อ Wifi-AP-Web-Server
  พิมพ์ **d:** แล้วกด **Enter**
  พิมพ์ **cd Wifi-AP-Web-Server** แล้วกด **Enter**
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
* โดยการทดลองที่ 6 จะเป็นการไมโครคอนโทรเลอร์สร้างไวไฟ จึงเรียกใช้ โปรแกรมที่โดยพิม **cd 06_Wifi-AP-Web-Server** แล้วกด **Enter**
 สามารถเช็คโปรแกรมที่ใช้รันได้โดย พิมพ์ **vi src/main.cpp** แล้วกด **Enter**โดยจะแสดงโค้ดที่เขียนจากข้อที่ 1
5. อัพโหลดโปรแกรม โดยพิมพ์ **pio run -t upload** แล้วกด **Enter** ในขณะที่รันโปรแกรมเพื่อให้ไมโครคอนโทรเลอร์รับโปกรแกรมใหม่เข้าไป ให้กดปุ่มดำค้าง แล้วกดปุ่มแดง 1 ครั้ง เพิ่มเป็นการรีเซต
6. เมื่อลงโปรแกรมเสร็จแล้ว พิมพ์ **pio device monitor** แล้วกด **Enter** เพื่อดูผลลัพท์โดยการแสดงผลจากคอมพิวเตอร์ สามารถกดปุ่มสีแดงเพื่อรีเซต

![image](https://user-images.githubusercontent.com/80879565/111905215-1737a580-8a7d-11eb-9055-14b7e8e87867.png)

7. สังเกต บันทึกผล และอธิปรายผล


### การบันทึกผลการทดลอง
  สามารถใช้โปรแกรมรันเข้าไมโครคอนโทรเลอร์เพื่อสร้างเป็นไวไฟได้ โดยไวไฟ ชื่อ "TUENG-ESP-WIFI" และมีรหัส choompol โดยสามารถเช็คไวไฟจากการเชื่อมต่อกับโทรศัพท์


### อภิปรายผลการทดลอง
  จากการทดลอง พบว่า ไมโครคอนโทรเลอร์สามารถสร้างเป็นไวไฟเพื่อใช้งานได้
  
  
### คำถามหลังการทดลอง
  * ไวไฟที่สร้างจากไมโครคอนโทรเลอร์สามารถใช้งานได้หรือไม่ อย่างไร
   

## จบการทดลองที่ 6 เพียงเท่านั้น
### หากมีข้อผิดพลาดประการใดข้ออภัยมา ณ ที่นี้ด้วย
## :+1: :+1:  :+1:  :+1:  :+1:  

