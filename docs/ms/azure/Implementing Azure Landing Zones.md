จริงๆ แล้ว ในการทดลองใช้งาน Entra ID เราใช้แค่ชื่อ default tenant "your-tenant-name.onmicrosoft.com" ก็เพียงพอแล้ว

 แต่ถ้าเราอยากลองทำให้เหมือนจริง ก็อาจจะลองเพิ่ม custom domain เข้ามาใน Entra ID tenant ของเราได้
 
 จากนั้นก็ให้ user ใช้ username@domain.xxx แทน username@your-tenant-name.onmicrosoft.com ได้เลยครับ

## 1. Buy a domain

1\. ซื้อ domain ราคาถูก จากที่ไหนก็ได้

เลือกแค่ 1 ปี

[![alt text](<../assets/screenshots/1.6.1 buy the domain.jpg>)](<../assets/screenshots/1.6.1 buy the domain.jpg>)

ปิดทุก option ที่จะทำให้เราเสียเงินเพิ่ม

[![alt text](<../assets/screenshots/1.6.2 reduce cost.jpg>)](<../assets/screenshots/1.6.2 reduce cost.jpg>)

แล้วกดซื้อ

[![alt text](<../assets/screenshots/1.6.3 complete purchase.jpg>)](<../assets/screenshots/1.6.3 complete purchase.jpg>)

ตอนนี้เราได้ domain ที่จะนำไปเพิ่มลงใน tenant ของเราแล้ว

[![alt text](<../assets/screenshots/1.6.4 complete purchase 2.jpg>)](<../assets/screenshots/1.6.4 complete purchase 2.jpg>)

2\. อย่าลืมเข้ามาปิด auto renew ด้วยนะครับ

[![alt text](<../assets/screenshots/1.6.5 turn off auto renew.jpg>)](<../assets/screenshots/1.6.5 turn off auto renew.jpg>)

## 2. Add a custom domain

1\. ใน Azure portal เลือก Add custom domain

[![alt text](<../assets/screenshots/1.6.6 add a custom domain.jpg>)](<../assets/screenshots/1.6.6 add a custom domain.jpg>)

copy ข้อมูล txt record ที่ระบบ generate ให้

[![alt text](<../assets/screenshots/1.6.7 txt record info.jpg>)](<../assets/screenshots/1.6.7 txt record info.jpg>)

2\. แล้วนำข้อมูล TXT record ไปสร้างใน DNS zone ที่เราพึ่งจดทะเบียนไป

[![alt text](<../assets/screenshots/1.6.9 add txt record to dns.jpg>)](<../assets/screenshots/1.6.9 add txt record to dns.jpg>)

3\. จากนั้นกลับไปที่ Azure portal เพื่อ verify domain

รอสักครู่ แล้วค่อยกด verify หรืออาจลองกด verify หลายๆ ครั้งหน่อย จนสำเร็จ

[![alt text](<../assets/screenshots/1.6.10 verify domain.jpg>)](<../assets/screenshots/1.6.10 verify domain.jpg>)

4\. เลือก domain ใหม่

[![alt text](<../assets/screenshots/1.6.11 select new domain.jpg>)](<../assets/screenshots/1.6.11 select new domain.jpg>)

แล้วแล้ว Make primary

[![alt text](<../assets/screenshots/1.6.12 make primary.jpg>)](<../assets/screenshots/1.6.12 make primary.jpg>)

ตอนนี้ domain ใหม่เป็น primary domain แล้ว

[![alt text](<../assets/screenshots/1.6.13 verify the new domain is primary.jpg>)](<../assets/screenshots/1.6.13 verify the new domain is primary.jpg>)

## 3. Change users' UPN suffixes

1\. เปลี่ยน UPN suffix ของ user1

[![alt text](<../assets/screenshots/1.6.14 user1 properties.jpg>)](<../assets/screenshots/1.6.14 user1 properties.jpg>)

เลือก domain ใหม่ที่พึ่งเพิ่มเข้ามา

[![alt text](<../assets/screenshots/1.6.15 change upn user1.jpg>)](<../assets/screenshots/1.6.15 change upn user1.jpg>)

[![alt text](<../assets/screenshots/1.6.15 user1 changed.jpg>)](<../assets/screenshots/1.6.15 user1 changed.jpg>)

2\. เปลี่ยน UPN suffix ของ user2 และ user3

[![alt text](<../assets/screenshots/1.6.16 3 users changed.jpg>)](<../assets/screenshots/1.6.16 3 users changed.jpg>)

## 4. Test

1\. ลอง sign in ด้วย UPN เดิม เช่น user1@your-tenant-name.onmicrosoft.com

เราจะ sign in ไม่ได้

[![alt text](<../assets/screenshots/1.6.17 test the old upn.jpg>)](<../assets/screenshots/1.6.17 test the old upn.jpg>)

2\. ลอง sign in อีกครั้งด้วย UPN ใหม่ user1@domain.xxx

[![alt text](<../assets/screenshots/1.6.18 sign in with the new upn.jpg>)](<../assets/screenshots/1.6.18 sign in with the new upn.jpg>)

[![alt text](<../assets/screenshots/1.6.19 password.jpg>)](<../assets/screenshots/1.6.19 password.jpg>)

ตอนนี้ user สามารถ sign in ด้วย UPN ใหม่ได้แล้ว

[![alt text](<../assets/screenshots/1.6.20 verify signed in.jpg>)](<../assets/screenshots/1.6.20 verify signed in.jpg>)

...

[Learn In the Cloud](https://learninthecloud.co)