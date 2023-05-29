
# ESP32-Problems-Solutions
عدد من المشاكل التي واجهتني أثناء استخدام ESP32 والحلول التي نجحت معي
هذا هو البورد الذي أستخدمه
![image](https://github.com/Mjd0001/ESP32-Problems-Solutions/assets/105239889/e2d3f895-9387-4c66-b384-15b7accc5f5a)
Board : ESP-WROOM-32 <br>
IDE name: Arduino IDE 2.1.0 <br>

---
## ESP32 installation
لتشغيل البورد لأول مره اتبع الخطوات التالية:

Steps to Start Use ESP32:
1. Download Arduino IDE :https://www.arduino.cc/en/software
2.	Open Arduino IDE => File => Preferences => Paste this in "Additional Boards Manager URLs: https://dl.espressif.com/dl/package_esp32_index.json
3.	Tools => Board => Boards Manager => search "ESP32" then Install it.
4.	Connect ESP32 to the computer.
5.	Choose The Board: Tools => Board => ESP32 Arduino => WEMOS D1 MINI ESP32.
6.	To Test The ESP32: File => Examples => Basics => Blink 
7.	Upload the code
8.	Then the LED in the ESP32 will Blink, that's mean it's work well. 

--- 

## The Problems
### Unable to upload anything to the board
اذا كنت ما تقدر ترفع الكود للبورد فممكن يكون عندك أحد هالمشكلتين: <br>

**المشكلة 1 : مشكلة في البورت COM** <br>
عشان تعرف ان عندك هالمشكلة روح لإدارة الاجهزة 
View => show hidden devices
ثم شوف
 ports (COM &LPT)
 ![image](https://github.com/Mjd0001/ESP32-Problems-Solutions/assets/105239889/72dc7c62-bdea-4363-8ac5-c6661dc4e046)
![image](https://github.com/Mjd0001/ESP32-Problems-Solutions/assets/105239889/d942c1e0-ada2-4ffd-93a8-fbe148b40052)

اذا عندك هالمشكلة 
حمل CP210x من هالرابط https://t.co/BstuNeHBGA <br>
الفيديو يوضح طريقة التنصيب: https://twitter.com/star_20811/status/1659320063772573696?s=20 <br> 
ثم جرب توصل البورد وترفع الكود وراح يشتغل ان شاء الله <br>
<br> 
<br>
<br>
**المشكلة 2** <br>
عدم القدرة على رفع اي كود للبورد رغم اختيار ال Port الصحيح و اسم البورد الصحيح، جربت على عدد من البوردات الاخرى وكان يعمل جيداً <br>
رسالة الخطأ:
```
Sketch uses 197736 bytes (15%) of program storage space. Maximum is 1310720 bytes.
Global variables use 13084 bytes (3%) of dynamic memory, leaving 314596 bytes for local variables. Maximum is 327680 bytes.
esptool.py v3.0-dev
Serial port COM6
Connecting........_____....._____....._____....._____....._____....._____....._____

A fatal error occurred: Failed to connect to ESP32: Timed out waiting for packet header
Failed uploading: uploading error: exit status 2
```

**الحل** <br>
بعض الـ Pins تعيق عملية رفع الكود، لست مختص ولا أعرف لماذا. <br>
في حالتي قمت بازالة pin 2 وتم رفع الكود بنجاح و تم حل المشكلة. <br>
لتفاصيل أكثر: https://github.com/espressif/arduino-esp32/issues/1497

---
### Compilation error SD.h
عند  التحقق من الكود أو محاولة رفعه يظهر هذا الخطأ: <br>
```
#error Architecture or board not supported. ^ Multiple libraries were found for "SD.h" 
Used: C:\Users\MA\AppData\Local\Arduino15\libraries\SD 
Not used: C:\Users\MA\AppData\Local\Arduino15\packages\esp32\hardware\esp32\1.0.6\libraries\SD exit status 1 Compilation error: exit status 1
```
هناك حلول في الانترنت يقولون نحذف مجلد Arduino15 من المسار C:\Users\MA\AppData\Local\Arduino15\libraries\SD  <br>
لكن هذه الحلول لم تنجح وظهرت العديد من المشكلات الجديدة، الحل الانسب هو القيام بهذه الخطوات:

1. Select File > Preferences from the Arduino IDE menus.
2. Enter the following URL into the "Additional Boards Manager URLs" field:
https://raw.githubusercontent.com/espressif/arduino-esp32/gh-pages/package_esp32_index.json
:exclamation: If there are already Boards Manager URLs in the field, separate them with commas.
Click the OK button.
3. You will now see a "Downloading index: ..." notification at the bottom right corner of the IDE window. Wait for that notification to close.
4. Select Tools > Board > Boards Manager from the Arduino IDE menus to open the "Boards Manager" view in the left side panel.
Scroll down through the list of boards platforms until you see the "esp32 by Espressif Systems" entry. Hover the mouse pointer over that entry.
You will now see a version menu. Make sure "2.0.5" is shown as selected in the menu.
5. You will also see an "UPDATE" or "INSTALL" button at the bottom of the entry. Click the button.
6. Wait for the update to finish.<br>
اذا قمت بتنفيذ هذه الخطوات سيتم رفع الكود بنجاح ان شاء الله <br>
لتفاصيل أكثر حول المشكلة وأسبابها : https://forum.arduino.cc/t/compilation-error-arduino-2-0-sd-h/1045826/2

