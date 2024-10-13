เราจะลอง assign license ให้กับ user ใน Entra ID tenant ของเราดู แต่เราต้องสมัคร trail license อะไรก็ได้สักตัวนึงก่อน

ในตัวอย่างนี้เราจะสมัคร Entra ID P2 trial กันนะครับ

## 1. Sign up a sample license

1\. รีวิว Entra ID license

ตอนนี้เราใช้ Microsoft Entra ID Free อยู่

[![alt text](<../assets/screenshots/1.3.1 view licenses.jpg>)](<../assets/screenshots/1.3.1 view licenses.jpg>)

และยังไม่มี license อะไรให้ทดลองใช้งานเพิ่มเลย

[![alt text](<../assets/screenshots/1.3.2 all products.jpg>)](<../assets/screenshots/1.3.2 all products.jpg>)

2\. Activate Entra ID P2 trial license

เราอยากลองใช้ feature เหล่านี้อยู่แล้ว  ดังนั้นเราก็สมัคร Entra ID P2 ดู

[![alt text](<../assets/screenshots/1.3.3 try entra id p2.jpg>)](<../assets/screenshots/1.3.3 try entra id p2.jpg>)

กด Activate (ครั้งที่ 1)

[![alt text](<../assets/screenshots/1.3.4 activate entra id p2.jpg>)](<../assets/screenshots/1.3.4 activate entra id p2.jpg>)

Next

[![alt text](<../assets/screenshots/1.3.5 activate entra id p2 2.jpg>)](<../assets/screenshots/1.3.5 activate entra id p2 2.jpg>)

Sign in

[![alt text](<../assets/screenshots/1.3.6 activate entra id p2 3.jpg>)](<../assets/screenshots/1.3.6 activate entra id p2 3.jpg>)

3\. อาจจะมีการข้อข้อมูล และขั้นตอนอยู่พอสมควร แต่จะไม่มีการ charge ค่าใช้จ่ายจากเรา

เริ่มจากใส่ sold to address

[![alt text](<../assets/screenshots/1.3.7 continue sold to address.jpg>)](<../assets/screenshots/1.3.7 continue sold to address.jpg>)

[![alt text](<../assets/screenshots/1.3.8 edit address.jpg>)](<../assets/screenshots/1.3.8 edit address.jpg>)

[![alt text](<../assets/screenshots/1.3.9 enter sold to address.jpg>)](<../assets/screenshots/1.3.9 enter sold to address.jpg>)

[![alt text](<../assets/screenshots/1.3.10 use this address.jpg>)](<../assets/screenshots/1.3.10 use this address.jpg>)

[![alt text](<../assets/screenshots/1.3.11 sold to address completed.jpg>)](<../assets/screenshots/1.3.11 sold to address completed.jpg>)

ใส่ TIN registration number (ถ้าไม่รู้ว่าจะใส่เลขอะไร ก็ใส่เลขบัตรประจำตัวประชนเราดู)

[![alt text](<../assets/screenshots/1.3.12 enter tin and save.jpg>)](<../assets/screenshots/1.3.12 enter tin and save.jpg>)

[![alt text](<../assets/screenshots/1.3.13 enter tin completed.jpg>)](<../assets/screenshots/1.3.13 enter tin completed.jpg>)

4\. ลอง activate อีกรอบ (ครั้งที่ 2)

[![alt text](<../assets/screenshots/1.3.14 activate 2.jpg>)](<../assets/screenshots/1.3.14 activate 2.jpg>)

5\. ยังต้องเพิ่ม credit card payment method (แต่ระบบจะไม่มีการ charge ค่าใช้จ่ายใดๆ จากเรา)

[![alt text](<../assets/screenshots/1.3.15 continue to add credit card payment method.jpg>)](<../assets/screenshots/1.3.15 continue to add credit card payment method.jpg>)

[![alt text](<../assets/screenshots/1.3.16 add payment method.jpg>)](<../assets/screenshots/1.3.16 add payment method.jpg>)

[![alt text](<../assets/screenshots/1.3.17 add payment method 2.jpg>)](<../assets/screenshots/1.3.17 add payment method 2.jpg>)

[![alt text](<../assets/screenshots/1.3.18 use this address.jpg>)](<../assets/screenshots/1.3.18 use this address.jpg>)

[![alt text](<../assets/screenshots/1.3.19 close.jpg>)](<../assets/screenshots/1.3.19 close.jpg>)

ตอนนี้ payment method ถูกเพิ่มแล้ว

[![alt text](<../assets/screenshots/1.3.20 add the payment method completed.jpg>)](<../assets/screenshots/1.3.20 add the payment method completed.jpg>)

5\. ลอง activate อีกครั้ง (ครั้งที่ 3)

[![alt text](<../assets/screenshots/1.3.21 activate 3.jpg>)](<../assets/screenshots/1.3.21 activate 3.jpg>)

Try now

[![alt text](<../assets/screenshots/1.3.22 try now.jpg>)](<../assets/screenshots/1.3.22 try now.jpg>)

Continue

[![alt text](<../assets/screenshots/1.3.23 continue.jpg>)](<../assets/screenshots/1.3.23 continue.jpg>)

ในที่สุด เราก็ได้ license แล้ว

[![alt text](<../assets/screenshots/1.3.24 got the entra id p2 license.jpg>)](<../assets/screenshots/1.3.24 got the entra id p2 license.jpg>)

ลองดูใน Azure portal อีกที่นึง

[![alt text](<../assets/screenshots/1.3.25 view the license in azure portal.jpg>)](<../assets/screenshots/1.3.25 view the license in azure portal.jpg>)

## 2. Create a new dynamic user group

1\. สร้าง dynamic user group

เช่น ชื่อ G HR

[![alt text](<../assets/screenshots/1.3.26 new group.jpg>)](<../assets/screenshots/1.3.26 new group.jpg>)

2\. เลือก membership type = Dynamic User

และ Add dynamic query

[![alt text](<../assets/screenshots/1.3.27 dynamic group.jpg>)](<../assets/screenshots/1.3.27 dynamic group.jpg>)

ให้ user ทุกคนที่อยู่ใน department = HR เป็นสมาชิกของ group นี้

[![alt text](<../assets/screenshots/1.3.28 dynamic user rule.jpg>)](<../assets/screenshots/1.3.28 dynamic user rule.jpg>)

Create

[![alt text](<../assets/screenshots/1.3.29 create dynamic group.jpg>)](<../assets/screenshots/1.3.29 create dynamic group.jpg>)

ตอนนี้ dynamic group ถูกสร้างเรียบร้อยแล้ว

[![alt text](<../assets/screenshots/1.3.30 review the dynamic group.jpg>)](<../assets/screenshots/1.3.30 review the dynamic group.jpg>)

3\. รอสักครู่ก็จะเห็น user ของแผนก HR ปรากฏเป็นสมาชิก dynamic user group ใหม่นี้

[![alt text](<../assets/screenshots/1.3.31 review the dynamic group 2.jpg>)](<../assets/screenshots/1.3.31 review the dynamic group 2.jpg>)

[![alt text](<../assets/screenshots/1.3.32 review members.jpg>)](<../assets/screenshots/1.3.32 review members.jpg>)

ตอนนี้เรามี dynamic group แล้ว ดังนั้นเราลองไปใช้ประโยชน์จาก dynamic user group กันครับ

## 3. Group-based licensing

เราจะลองใช้ประโยชน์จาก dynamic user group เพื่อให้ user ในแผนก HR ถูก assign license โดยอัตโนมัติผ่าน group-based licensing feature

1\. ไปที่ dynamic group ที่สร้างขึ้นก่อนหน้านี้

แล้ว assign license

[![alt text](<../assets/screenshots/1.3.33 assign license to group.jpg>)](<../assets/screenshots/1.3.33 assign license to group.jpg>)

เลือก Entra ID P2 (ตอนนี้เรามี license นี้อยู่ตัวเดียว)

[![alt text](<../assets/screenshots/1.3.34 select the license.jpg>)](<../assets/screenshots/1.3.34 select the license.jpg>)

[![alt text](<../assets/screenshots/1.3.35 verify the licesne is assigned to the group.jpg>)](<../assets/screenshots/1.3.35 verify the licesne is assigned to the group.jpg>)

2\. ลองตรวจสอบ user ที่อยู่ใน dynamic user group ที่เรา assign license ใส่ group ไว้

ตอนนี้ user ถูก assign license อัตโนมัติแล้วนะครับ

[![testing](<../assets/screenshots/1.3.36 review the license for the users.jpg>)](<../assets/screenshots/1.3.36 review the license for the users.jpg>)

ใน Microsoft 365 admin center ก็จะเห็นว่า user ใน group ทุกคนถูก assign license แล้วเช่นกัน

[![alt text](<../assets/screenshots/1.3.37 review the license in 365.jpg>)](<../assets/screenshots/1.3.37 review the license in 365.jpg>)

...

[Learn In the Cloud](https://learninthecloud.co)