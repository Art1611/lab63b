## การทดลองที่ 3 เรื่อง การเขียนโปรแกรมเอ้าพุทสัญญาณดิจิทัล

### วัตถุประสงค์
1. ศึกษาการรันโปรแกรมเข้าไมโครคอนโทรเลอร์แล้วนำเอ้าพุทสัญญาณไปเชื่อมต่อกับอุปกรณ์อื่น ๆ
2. ศึกษาการทำงานของตัวรีเลย์ (Relay)


### อุปกรณ์ที่ใช้
1. ไมโครคอนโทรเลอร์ (ESP-01)
2. อุปกรณ์เชื่อมต่อแบบ USB
3. ซีเรียล
4. Adapter
5. รีเลย์(Relay)

![image](https://user-images.githubusercontent.com/80879565/111870658-90b99000-89b8-11eb-9241-21e0e7a6a4dc.png)



### ศึกษาข้อมูลเบื้องต้น
#### 03 run example 3
https://www.youtube.com/watch?v=CCnN1WJsXQY

#### Relay
http://www.psptech.co.th/%E0%B8%A3%E0%B8%B5%E0%B9%80%E0%B8%A5%E0%B8%A2%E0%B9%8Crelay%E0%B8%84%E0%B8%B7%E0%B8%AD%E0%B8%AD%E0%B8%B0%E0%B9%84%E0%B8%A3-15696.page




### วิธีการทดลอง
1. เขียนโปรแกรมลงใน **visual studio code** โดยใช้ภาษา C
```C
#include <Arduino.h>
#include <ESP8266WiFi.h>

int cnt = 0;

void setup()
{
	Serial.begin(115200);
	pinMode(0, OUTPUT);
	Serial.println("\n\n\n");
}

void loop()
{
	cnt++;
	if(cnt % 2) {
		Serial.println("========== ON ==========="");
		digitalWrite(0, HIGH);
	} else {
		Serial.println("========== OFF ===========");
		digitalWrite(0, LOW);
	}
	delay(500);
}



```
 
2. ต่ออุปกรณ์ USB เข้ากับซีเรียล
3. ต่อซีเรียลเข้ากับ Adapter

![image](https://user-images.githubusercontent.com/80879565/111870346-ccebf100-89b6-11eb-90c0-80c958516e99.png)
![image](https://user-images.githubusercontent.com/80879565/111870380-f86edb80-89b6-11eb-87f9-6d601dec997c.png)


4. ต่อ Adapter เข้ากับไมโครคอนโทรเลอร์

![image](https://user-images.githubusercontent.com/80879565/111870405-23592f80-89b7-11eb-8f70-45200335134c.png)

5. เปิด Command Prompt แล้วเข้าไปในโฟล์เดอร์ที่จะอัพโหลด เช่น ไดฟ์ D ไฟล์ ชื่อ Output-Port
  พิมพ์ **d:** แล้วกด **Enter**
  พิมพ์ **cd Output-Port** แล้วกด **Enter**
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
* โดยการทดลองที่ 3 เป็นการนำเอ้าพุทของไมโครคอนโทรเลอร์ไปใช้งานต่อ จึงเรียกใช้ โปรแกรมที่โดยพิม **cd Output-Port** แล้วกด **Enter**
 สามารถเช็คโปรแกรมที่ใช้รันได้โดย พิมพ์ **vi src/main.cpp** แล้วกด **Enter**โดยจะแสดงโค้ดที่เขียนจากข้อที่ 1
6. อัพโหลดโปรแกรม โดยพิมพ์ **pio run -t upload** แล้วกด **Enter** ในขณะที่รันโปรแกรมเพื่อให้ไมโครคอนโทรเลอร์รับโปกรแกรมใหม่เข้าไป ให้กดปุ่มดำค้าง แล้วกดปุ่มแดง 1 ครั้ง เพิ่มเป็นการรีเซต
7. เมื่อลงโปรแกรมเสร็จแล้ว พิมพ์ **pio device monitor** แล้วกด **Enter** เพื่อดูผลลัพท์โดยการแสดงผลจากคอมพิวเตอร์ สามารถกดปุ่มสีแดงเพื่อรีเซต

![image](https://user-images.githubusercontent.com/80879565/111870517-d1fd7000-89b7-11eb-92f5-79ecfc70ef96.png)
![image](https://user-images.githubusercontent.com/80879565/111870527-e0e42280-89b7-11eb-89a8-0fadc24c4c73.png)

8. สังเกต บันทึกผล และอธิปรายผล
9. ถอดไมโครคอนโทรเลอร์แล้วนำมาต่อกับตัวรีเลย์

![image](https://user-images.githubusercontent.com/80879565/111870683-b181e580-89b8-11eb-80b4-b7570dd25c33.png)

10. นำตัวรีเลย์ต่อกับหัวชาตเพื่อจ่ายไฟไปให้รีเลย์ทำงาน

![image](https://user-images.githubusercontent.com/80879565/111870723-eee67300-89b8-11eb-8959-03ed5f2b81ca.png)
![image](https://user-images.githubusercontent.com/80879565/111870717-dfffc080-89b8-11eb-8907-951e2193f110.png)

11. สังเกต บันทึกผล และอธิปรายผล


### การบันทึกผลการทดลอง
   เมื่อรันโปรแกรมเข้าไปในไมโครคอนโทรเลอร์ Adapter ที่ต่อกับหลอดไฟสีขาว จะสว่าง ดับ ทุก ๆ 0.5 วินาที เมื่อดูคำสั่งในคอมจะเป็น ON OFF สลับกันไปมา



### อภิปรายผลการทดลอง
   จากการทดลอง พบว่า เมื่อรันโปรแกรมเข้าไปในไมโครคอนโทรเลอร์แล้ว สามารถนำไมโครคอนโทรเลอร์ไปเชื่อมต่อกับอุปกรณ์อื่น ๆ ได้ 
เช่น Relay โดยจากโค้ตโปรแกรมจะสั่งให้เปิด-ปิดสวิซ์ทุก ๆ 0.5 วินาที รีเลย์จะมีเสียงการสลับขาไป-มา ช่วงเปิด-ปิด และรีเลย์จะมีแสง สลับกับไม่มีแสง
  
### คำถามหลังการทดลอง
1. ทำไมต้องเสียบ Adapter ระหว่าง สาย USB กับไมโครคอนโทรเลอร์
2. อธิบายหลักการทำงานของ Relay
 
## จบการทดลองที่ 3 เพียงเท่านั้น
### หากมีข้อผิดพลาดประการใดข้ออภัยมา ณ ที่นี้ด้วย
## :+1: :+1:  :+1:  :+1:  :+1:  
