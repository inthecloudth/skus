โดยทั่วไป ผู้ใช้สามารถเปลี่ยน password ของตัวเองได้ถ้าเขาทราบ password เก่า (old password)

แต่ถ้าไม่ทราบ password เก่า เขาสามารถใช้ SSPR เข้าไป reset password ของตัวเองได้ แต่เขาต้องถูก authenticate ด้วยวิธีอื่นๆ ก่อน เช่น SMS text, mobile app, หรือ email เป็นต้น

## 1. Configure Pilot SSPR

เลือก group ที่จะ pilot SSPR ก่อน

[![alt text](<../assets/screenshots/1.5.1 password reset.jpg>)](<../assets/screenshots/1.5.1 password reset.jpg>)

เช่น G IT

[![alt text](<../assets/screenshots/1.5.2 pilot sspr.jpg>)](<../assets/screenshots/1.5.2 pilot sspr.jpg>)

## 2. Review default SSPR settings

ต่อมาเรามาดู default setting ของ SSPR กันครับ

1\. Authentication methods

SSPR จะขอให้ user ทำ authenticadtion ด้วย method ใด method หนึ่ง จะเป็น email หรือ SMS text ก็ได้ ก่อนที่จะอนุญาตให้ผู้ใช้ตั้ง password ใหม่ของตัวเอง

[![alt text](<../assets/screenshots/1.5.3 sspr authentication methods.jpg>)](<../assets/screenshots/1.5.3 sspr authentication methods.jpg>)

2\. Registration

ในการ sign in ครั้งถัดไป user ที่ถูก enable SSPR จะถูกระบบบังคับให้ register ข้อมูลที่จำเป็นสำหรับทำ SSPR เช่น ให้ระบุเบอร์โทรศัพท์ที่จะให้ SSPR ส่ง SMS text ไปหา

[![alt text](<../assets/screenshots/1.5.4 sspr registration.jpg>)](<../assets/screenshots/1.5.4 sspr registration.jpg>)

3\. Notification

ให้แจ้ง user เมื่อ password ถูก reset

[![alt text](<../assets/screenshots/1.5.5 sspr notifications.jpg>)](<../assets/screenshots/1.5.5 sspr notifications.jpg>)

4\. On-premises integration

ยังไม่มีการ enable password writeback กลับไปยัง on-premises AD DS

[![alt text](<../assets/screenshots/1.5.6 sspr onprem integration.jpg>)](<../assets/screenshots/1.5.6 sspr onprem integration.jpg>)

ตอนนี้ SSPR พร้อมใช้งานกับ pilot user  แล้ว ในหัวข้อถัดไปเรามาทดสอบกันต่อครับ

## 3. Test user registration

1\. ลอง sign out user1

[![alt text](<../assets/screenshots/1.5.7 user1 sign out.jpg>)](<../assets/screenshots/1.5.7 user1 sign out.jpg>)

แล้ว sign in ใหม่

[![alt text](<../assets/screenshots/1.5.8 user1 sign in again.jpg>)](<../assets/screenshots/1.5.8 user1 sign in again.jpg>)

2\. ระบบจะขอให้เราทำ registration

[![alt text](<../assets/screenshots/1.5.9 user1 sign in again 2.jpg>)](<../assets/screenshots/1.5.9 user1 sign in again 2.jpg>)

กรอกเบอร์โทรศัพท์ของ user1 ที่จะใช้รับ SMS text (ให้ระบุเบอร์โทรของเรา)

แล้วทำขั้นตอนต่างๆ ต่อไปเรื่อยๆ จนเสร็จ

[![alt text](<../assets/screenshots/1.5.10 sspr user1 registeration 1.jpg>)](<../assets/screenshots/1.5.10 sspr user1 registeration 1.jpg>)

[![alt text](<../assets/screenshots/1.5.11 sspr user1 registeration 2.jpg>)](<../assets/screenshots/1.5.11 sspr user1 registeration 2.jpg>)

ตอนนี้เรา register ข้อมุลที่ระบบขอเรียบร้อยแล้ว

[![alt text](<../assets/screenshots/1.5.12 sspr user1 registeration 3.jpg>)](<../assets/screenshots/1.5.12 sspr user1 registeration 3.jpg>)

[![alt text](<../assets/screenshots/1.5.13 sspr user1 registeration 4.jpg>)](<../assets/screenshots/1.5.13 sspr user1 registeration 4.jpg>)

3\. sign in อีกครั้ง

[![alt text](<../assets/screenshots/1.5.14 sign in again.jpg>)](<../assets/screenshots/1.5.14 sign in again.jpg>)

[![alt text](<../assets/screenshots/1.5.15 sign in again.jpg>)](<../assets/screenshots/1.5.15 sign in again.jpg>)

4\. แล้ว sign out

[![alt text](<../assets/screenshots/1.5.16 sign out.jpg>)](<../assets/screenshots/1.5.16 sign out.jpg>)

จากนั้น เราไปลองทดสอบ reset password ของ user1 ผ่าน SSPR กันครับ

## 4. Test password reset

1\. ลอง sign in ด้วย user1 แต่ไม่ต้องใส่ password

ให้เรากด forgot my password แทน

[![alt text](<../assets/screenshots/1.5.17 forgot password.jpg>)](<../assets/screenshots/1.5.17 forgot password.jpg>)

2\. แล้วเริ่มกระบวณการ reset password

[![alt text](<../assets/screenshots/1.5.18 forgot password 2.jpg>)](<../assets/screenshots/1.5.18 forgot password 2.jpg>)

[![alt text](<../assets/screenshots/1.5.19 forgot password 3.jpg>)](<../assets/screenshots/1.5.19 forgot password 3.jpg>)

[![alt text](<../assets/screenshots/1.5.20 forgot password 4.jpg>)](<../assets/screenshots/1.5.20 forgot password 4.jpg>)

ตั้ง password ใหม่ (แต่ password policy ใน Entra ID อาจทำให้ตั้งยากหน่อย)

[![alt text](<../assets/screenshots/1.5.21 set new password.jpg>)](<../assets/screenshots/1.5.21 set new password.jpg>)

[![alt text](<../assets/screenshots/1.5.22 set new password success.jpg>)](<../assets/screenshots/1.5.22 set new password success.jpg>)

3\. สุดท้ายลอง sign in อีกครั้งด้วย password ใหม่

[![alt text](<../assets/screenshots/1.5.22 sign in with new password 1.jpg>)](<../assets/screenshots/1.5.22 sign in with new password 1.jpg>)

[![alt text](<../assets/screenshots/1.5.23 sign in with new password 2.jpg>)](<../assets/screenshots/1.5.23 sign in with new password 2.jpg>)

[![alt text](<../assets/screenshots/1.5.24 sign in with new password 3.jpg>)](<../assets/screenshots/1.5.24 sign in with new password 3.jpg>)

ตอนนี้ user1 sign in ด้วย password ใหม่ได้เรียบร้อยแล้ว

[![alt text](<../assets/screenshots/1.5.25 sign in with new password success.jpg>)](<../assets/screenshots/1.5.25 sign in with new password success.jpg>)

## 5. Verify logs

1\. ในฐานะ admin

เราลองหา activity Reset password (self-service) จาก audit log ดู

[![alt text](<../assets/screenshots/1.5.26 admin verify 1.jpg>)](<../assets/screenshots/1.5.26 admin verify 1.jpg>)

ลองดูข้อมูลอื่นๆ เพิ่มเติม

[![alt text](<../assets/screenshots/1.5.27 admin verify 2.jpg>)](<../assets/screenshots/1.5.27 admin verify 2.jpg>)

2\. ลองเปิด user properties

แล้วลองดูค่า Last password change date time เป็นต้น

[![alt text](<../assets/screenshots/1.5.28 admin verify 3.jpg>)](<../assets/screenshots/1.5.28 admin verify 3.jpg>)

...

[Learn In the Cloud](https://learninthecloud.co)
