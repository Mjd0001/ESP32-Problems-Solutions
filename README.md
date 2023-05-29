# ESP32-Problems-Solutions
عدد من المشاكل التي واجهتني أثناء استخدام ESP32 والحلول التي نجحت معي
## My ESP32 Board
هذا هو البورد الذي أستخدمه
![image](https://github.com/Mjd0001/ESP32-Problems-Solutions/assets/105239889/e2d3f895-9387-4c66-b384-15b7accc5f5a)
Board : ESP-WROOM-32
IDE name: Arduino IDE 2.1.0


## The Problems
### Unable to upload anything to the board
**وصف المشكلة:**
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

