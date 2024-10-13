Azure disk encryption (ADE) ใช้ Key Vault เก็บ BitLocker encryption key (secret) ที่ใช้เข้ารหัส disk

ดังนั้น เราสร้าง Key Vault กันก่อนนะครับ

## 1. Create a Key Vault

1\. สร้าง Key Vault

![alt text](../assets/screenshots/module%2007/lab%202/image.png)

![alt text](../assets/screenshots/module%2007/lab%202/image-1.png)

2\. Enable "Azure Disk Encryption for volume encryption" เพื่อให้ key vault รองรับ ADE

![alt text](../assets/screenshots/module%2007/lab%202/image-2.png)

3\. อนุญาตให้ VM ที่อยู่ใน subnet ที่ต้องการเข้าถึง Key Vault ได้

แต่ต้อง enable virtual service network endpoint ของ Key Vault ก่อน

![alt text](../assets/screenshots/module%2007/lab%202/image-3.png)

แล้วกด Add เพื่อเพิ่ม subnet ของ VM เข้าไป

![alt text](../assets/screenshots/module%2007/lab%202/image-4.png)

Enable "Allow trusted Microsoft service to bypass this firewall" ด้วย

![alt text](../assets/screenshots/module%2007/lab%202/image-5.png)

แล้วกด Create

![alt text](../assets/screenshots/module%2007/lab%202/image-6.png)

4\. ตอนนี้เราได้ Key Vault แล้ว

![alt text](../assets/screenshots/module%2007/lab%202/image-7.png)

## 2. Enable Azure Disk Encryption (ADE)

1\. เริ่ม enable disk encryption

![alt text](../assets/screenshots/module%2007/lab%202/image-25.png)

Encrypt ทั้ง OS และ data disks เลย

แล้วเลือก Key Vault ที่จะใช้เก็บ BitLocker encryption key (secret) ของเรา

แต่ตอนนี้เรายังไม่มี Key encryption key (KEK) จึงต้องสร้างก่อน

![alt text](../assets/screenshots/module%2007/lab%202/image-8.png)

ตั้งชื่อ KEK อะไรก็ได้

> Key encryption key (KEK) เอาไว้ protect หรือ wrap BitLocker encryption key หรือ BEK (secret) ไว้อีกชั้นนึง

![alt text](../assets/screenshots/module%2007/lab%202/image-9.png)

Save

![alt text](../assets/screenshots/module%2007/lab%202/image-10.png)

![alt text](../assets/screenshots/module%2007/lab%202/image-11.png)

## 3. Review the results

### 3.1 Review BitLocker status

1\. ตอนนี้ VM disk ถูก encrypt ด้วย ADE แล้ว

![alt text](../assets/screenshots/module%2007/lab%202/image-12.png)

2\. ลองดู drive ว่าถูก encrypt แล้ว

หรือดู status ของ BitLocker ได้ด้วย manage-bde -status

![alt text](../assets/screenshots/module%2007/lab%202/image-13.png)

2\. หรือกดดู status ของ BitLocker ได้ที่ตรงนี้ครับ

![alt text](../assets/screenshots/module%2007/lab%202/image-23.png)

![alt text](../assets/screenshots/module%2007/lab%202/image-24.png)

### 3.2 Review keys

#### 3.2.1 Assign RBAC

1\. ตอนนี้เรามองไม่เห็น KEK เพราะไม่มี permission

![alt text](../assets/screenshots/module%2007/lab%202/image-14.png)

2\. ให้สิทธิ์ Key Vault Administrator ตัวเองก่อน

![alt text](../assets/screenshots/module%2007/lab%202/image-15.png)

3\. ตอนนี้มีสิทธิ์แล้ว แต่ Key Vault ถูก disable public access ไว้ จึงยังไม่เห็น key

![alt text](../assets/screenshots/module%2007/lab%202/image-16.png)

#### 3.2.2 Firewall

1\. เพิ่ม IP address ของ laptop เราเข้าไปที่ firewall

ใช้ what is my ip เพื่อหา public IP ของ laptop เรา

![alt text](../assets/screenshots/module%2007/lab%202/image-17.png)

แล้วเพิ่ม public IP ของ laptop เราเข้าที่ firewall ของ Key Vault

![alt text](../assets/screenshots/module%2007/lab%202/image-18.png)

2\. ตอนนี้เราเห็น KEK แล้ว

![alt text](../assets/screenshots/module%2007/lab%202/image-19.png)

#### 3.2.3 View keys

1\. k1 คือ Key encryption key (KEK) ที่ใช้ protect หรือ wrap BitLocker encryption key หรือ BEK (secret) อีกชั้นนึง

![alt text](../assets/screenshots/module%2007/lab%202/image-19.png)

2\. ฺซึ่ง BitLocker encryption key นี้ถูกนำไปใช้ในการ encrypt VM disk

![alt text](../assets/screenshots/module%2007/lab%202/image-20.png)

![alt text](../assets/screenshots/module%2007/lab%202/image-21.png)

กด tags เพื่อดูว่า BEK นี้ ใช้ encrypt drive C อยู่

> Drive D ถูกตั้งไว้ให้ถูก unlock โดยอัตโนมัติ หาก drive C ถูก decrypt ได้ด้วย BEK นี้

![alt text](../assets/screenshots/module%2007/lab%202/image-22.png)

## Ref.

- [https://learn.microsoft.com/en-us/azure/virtual-machines/windows/disk-encryption-portal-quickstart](https://learn.microsoft.com/en-us/azure/virtual-machines/windows/disk-encryption-portal-quickstart)

...