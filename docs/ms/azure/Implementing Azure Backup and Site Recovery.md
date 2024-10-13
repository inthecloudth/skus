จริงๆ แล้ว ทุกคนน่าจะมี user account ใน Entra ID tenant ของบริษัทตัวเองอยู่แล้ว แต่เราอาจจะไม่มีสิทธิ์มากพอที่จะไปลองเล่นอะไรก็ได้ หรือ ถ้าเราทำอะไรไม่ระวังก็อาจจะทำให้ tenant ของบริษัทเสียหายได้

ดังนั้น เพื่อความปลอดภัย เราสร้าง Entra ID tenant ใหม่ของเราเอง เพื่อใช้ทดลองใช้งานจะดีกว่านะครับ

> หากเรายังไม่มี account ใดๆ เลย ก็สามารถสร้าง Entra ID tenant ตามนี้ได้ครับ [Quickstart: Create a new tenant in Microsoft Entra ID](https://learn.microsoft.com/th-th/entra/fundamentals/create-new-tenant)

## 1. Create a new Microsoft Entra ID tenant

1\. เข้า Azure portal ([https://portal.azure.com](https://portal.azure.com))

ไปที่ Microsoft Entra ID

[![alt text](<../assets/screenshots/1.0 search entra id.jpg>)](<../assets/screenshots/1.0 search entra id.jpg>)

Manage tenants

[![alt text](<../assets/screenshots/1.0 manage tenants.jpg>)](<../assets/screenshots/1.0 manage tenants.jpg>)

Create

[![alt text](<../assets/screenshots/1.0 create.jpg>)](<../assets/screenshots/1.0 create.jpg>)

2\. เลือก Microsoft Entra ID

[![alt text](<../assets/screenshots/1.0 choose entra id.jpg>)](<../assets/screenshots/1.0 choose entra id.jpg>)

ชื่อ tenant จะอยู่ใน format your-tenant-name.onmicrosoft.com ให้เราตั้งชื่อ tenant ของเรา และใช้ Location = Thailand นะครับ

[![alt text](<../assets/screenshots/1.0 enter tenant name.jpg>)](<../assets/screenshots/1.0 enter tenant name.jpg>)

กด Create แล้วรอสักครู่จน tenant สร้างเสร็จ จากนั้นกด link เพื่อเข้า Entra ID tenant ใหม่ของเรา

[![alt text](<../assets/screenshots/1.0 create tenant.jpg>)](<../assets/screenshots/1.0 create tenant.jpg>)

3\. ตอนนี้เราได้ Entra ID tenant แล้วนะครับ

[![alt text](<../assets/screenshots/1.0 result.jpg>)](<../assets/screenshots/1.0 result.jpg>)

## 2. Create a user and assign Global Administrator role

1\. สร้าง user ใหม่

[![alt text](<../assets/screenshots/11 create user.jpg>)](<../assets/screenshots/11 create user.jpg>)

ระบุ user principal name (UPN) ของ account ใหม่

> หมายเหตุ: Copy password เอาไว้ใช้ หรือจะตั้งใหม่เองก็ได้ครับ

[![alt text](<../assets/screenshots/11 name the user 3.jpg>)](<../assets/screenshots/11 name the user 3.jpg>)

Next

[![alt text](<../assets/screenshots/11 properties 3.jpg>)](<../assets/screenshots/11 properties 3.jpg>)

2\. Assign Global Administrator role

[![alt text](<../assets/screenshots/11 assign global admin role.jpg>)](<../assets/screenshots/11 assign global admin role.jpg>)

แล้วกด Create

[![alt text](<../assets/screenshots/11 verify and create.jpg>)](<../assets/screenshots/11 verify and create.jpg>)

3\. เข้าไปดูผลลัพธ์ที่ Users

[![alt text](<../assets/screenshots/11 review the result.jpg>)](<../assets/screenshots/11 review the result.jpg>)

เมื่อเราได้ global administrator ใหม่ของ Entra ID tenant ใหม่แล้ว เราก็ Sign out ได้เลย

[![alt text](<../assets/screenshots/11 sign out.jpg>)](<../assets/screenshots/11 sign out.jpg>)

## 3. Sign in with a new global adminsitrator

1\. Sign in เข้า [https://portal.azure.com](https://portal.azure.com) ด้วย global administrator คนใหม่

[![alt text](<../assets/screenshots/10 re-sign in again.jpg>)](<../assets/screenshots/10 re-sign in again.jpg>)

ใส่ password ที่ copy เก็บไว้

[![alt text](<../assets/screenshots/10 enter password.jpg>)](<../assets/screenshots/10 enter password.jpg>)

ตั้ง password ใหม่

[![alt text](<../assets/screenshots/10 update password.jpg>)](<../assets/screenshots/10 update password.jpg>)

2\. กด Cancel หรือ Get started

[![alt text](<../assets/screenshots/10 cancel.jpg>)](<../assets/screenshots/10 cancel.jpg>)

ปิด Quickstart Center หรือลองรีวิวดู

[![alt text](<../assets/screenshots/10 close.jpg>)](<../assets/screenshots/10 close.jpg>)

ตอนนี้ global administrator คนใหม่ sign in เข้ามาที่ Entra ID tenant ใหม่เรียบร้อยแล้ว

[![alt text](<../assets/screenshots/10 azure dashboard.jpg>)](<../assets/screenshots/10 azure dashboard.jpg>)

ต่อจากนี้ ถ้าเราอยากทดลองอะไรก็ทำได้หมดเลยครับ

...

[Learn In the Cloud](https://learninthecloud.co)