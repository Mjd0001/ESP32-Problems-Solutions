# ESP32-Problems-Solutions
عدد من المشاكل التي واجهتني أثناء استخدام ESP32 والحلول التي نجحت معي
## My ESP32 Board
هذا هو البورد الذي أستخدمه
![image](https://github.com/Mjd0001/ESP32-Problems-Solutions/assets/105239889/e2d3f895-9387-4c66-b384-15b7accc5f5a)
Board : ESP-WROOM-32
IDE name: Arduino IDE 2.1.0


## The Problems
### Unable to upload anything to the board
اذا كنت ما تقدر ترفع الكود للبورد فممكن يكون عندك أحد هالمشكلتين:

**المشكلة 1 : مشكلة في البورت COM**
عشان تعرف ان عندك هالمشكلة روح لإدارة الاجهزة 
View => show hidden devices
ثم شوف
 ports (COM &LPT)
 ![image](https://github.com/Mjd0001/ESP32-Problems-Solutions/assets/105239889/72dc7c62-bdea-4363-8ac5-c6661dc4e046)
![image](https://github.com/Mjd0001/ESP32-Problems-Solutions/assets/105239889/d942c1e0-ada2-4ffd-93a8-fbe148b40052)

اذا عندك هالمشكلة
حمل CP210x من هالرابط https://t.co/BstuNeHBGA 
الفيديو يوضح طريقة التنصيب: https://twitter.com/star_20811/status/1659320063772573696?s=20
ثم جرب توصل البورد وترفع الكود وراح يشتغل ان شاء الله

**المشكلة 2**
عدم القدرة على رفع اي كود للبورد رغم اختيار ال Port الصحيح و اسم البورد الصحيح، جربت على عدد من البوردات الاخرى وكان يعمل جيداً
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

**الحل**
بعض الـ Pins تعيق عملية رفع الكود، لست مختص ولا أعرف لماذا.
في حالتي قمت بازالة pin 2 وتم رفع الكود بنجاح و تم حل المشكلة.
لتفاصيل أكثر: https://github.com/espressif/arduino-esp32/issues/1497

### Compilation error SD.h

