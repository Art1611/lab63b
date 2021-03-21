## การทดลองที่ 5 เรื่อง การเขียนโปรแกรมเชื่อมต่อไวไฟและเว็บเซอร์เวอร์

### วัตถุประสงค์
1. ศึกษาการใช้ไมโครคอนโทรเลอร์สร้างเว็บเซอร์เวอร์จากไวไฟ


### อุปกรณ์ที่ใช้
1. ไมโครคอนโทรเลอร์ (ESP-01)
2. อุปกรณ์เชื่อมต่อแบบ USB
3. ซีเรียล


### ศึกษาข้อมูลเบื้องต้น
#### 05 run wifi
https://www.youtube.com/watch?v=VX-QNQcO-b4



### วิธีการทดลอง
1. เขียนโปรแกรมลงใน **visual studio code** โดยใช้ภาษา C
```C
#include <ESP8266WiFi.h>
//#include <WiFiClient.h>
#include <ESP8266WebServer.h>

const char* ssid = "HI_BMFWIFI_2.4G";
const char* password = "0819110933";

ESP8266WebServer server(80);

int cnt = 0;

void setup(void){
	Serial.begin(115200);

	WiFi.mode(WIFI_STA);
	WiFi.begin(ssid, password);
	while (WiFi.status() != WL_CONNECTED) {
		delay(500);
		Serial.print(".");
	}
	Serial.print("\n\nIP address: ");
	Serial.println(WiFi.localIP());

	server.onNotFound([]() {
		server.send(404, "text/plain", "Path Not Found");
	});

	server.on("/", []() {
		cnt++;
		Strind msg = "Hello cnt: ";
		msg += cnt;
		server.send(200, "text/plain", msg);
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
4. เปิด Command Prompt แล้วเข้าไปในโฟล์เดอร์ที่จะอัพโหลด เช่น ไดฟ์ D ไฟล์ ชื่อ Wifi-Wed-Server
  พิมพ์ **d:** แล้วกด **Enter**
  พิมพ์ **cd Wifi-Wed-Server** แล้วกด **Enter**
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
* โดยการทดลองที่ 5 จะเป็นทดสอบไมโครคอนโทรเลอร์ จึงเรียกใช้ โปรแกรมที่โดยพิม **cd 05_Wifi-Wed-Server** แล้วกด **Enter**
 สามารถเช็คโปรแกรมที่ใช้รันได้โดย พิมพ์ **vi src/main.cpp** แล้วกด **Enter**โดยจะแสดงโค้ดที่เขียนจากข้อที่ 1
5. อัพโหลดโปรแกรม โดยพิมพ์ **pio run -t upload** แล้วกด **Enter** ในขณะที่รันโปรแกรมเพื่อให้ไมโครคอนโทรเลอร์รับโปกรแกรมใหม่เข้าไป ให้กดปุ่มดำค้าง แล้วกดปุ่มแดง 1 ครั้ง เพิ่มเป็นการรีเซต



### การบันทึกผลการทดลอง
###เนื่องจากลิปมีปัญหา


### อภิปรายผลการทดลอง
###เนื่องจากลิปมีปัญหา
  
  
### คำถามหลังการทดลอง
###เนื่องจากลิปมีปัญหา

## จบการทดลองที่ 5 เพียงเท่านั้น
### หากมีข้อผิดพลาดประการใดข้ออภัยมา ณ ที่นี้ด้วย
## :+1: :+1:  :+1:  :+1:  :+1:  
