## 1. Deploy VMs to availability sets

### 1.1 Create availability sets for web servers & database servers

1\. สร้าง web-as availability set

![alt text](../assets/screenshots/module%2007/lab%206/image.png)

![alt text](../assets/screenshots/module%2007/lab%206/image-1.png)

![alt text](../assets/screenshots/module%2007/lab%206/image-2.png)

2\. สร้าง db-as availability set

![alt text](../assets/screenshots/module%2007/lab%206/image-3.png)

3\. ตอนนี้เรามี 2 availability sets แล้ว

![alt text](../assets/screenshots/module%2007/lab%206/image-4.png)

### 1.2 Deploy VMs to availability sets

1\. สร้าง VM web1 ลงใน web-as

![alt text](../assets/screenshots/module%2007/lab%206/image-5.png)

2\. สร้าง VM web2 ลงใน web-as

![alt text](../assets/screenshots/module%2007/lab%206/image-6.png)

3\. สร้าง VM web3 ลงใน web-as

![alt text](../assets/screenshots/module%2007/lab%206/image-7.png)

4\. ตอนนี้เรามี 3 VMs ใน availability set เดียวกันแล้ว (web-as)

![alt text](../assets/screenshots/module%2007/lab%206/image-8.png)

5\. ซึ่งจะเห็นว่า web1, web2, และ web3 ที่อยู่ใน availability set เดียวกัน ถูกสร้างลงบน rack คนละตู้ (fault domain 0 และ 1)

และถูกกระจายให้อยู่คนละ update domain ด้วย

![alt text](../assets/screenshots/module%2007/lab%206/image-9.png)

## 2. Deploy VMs to availability zones

ลองดูว่าเราสามารถสร้าง VM ลงบน availability zone ที่ต้องการได้

แต่ให้เรา cancel ไป ไม่ต้องทำก็ได้ครับ

![alt text](../assets/screenshots/module%2007/lab%206/image-10.png)

...