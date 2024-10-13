## 1. Before resize

1\. ลองดูว่า VM ของเรา รันอยู่บน Hyper-V host ที่ชื่อว่าอะไร

Get-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Virtual Machine\Guest\Parameters"  | Select-Object HostName

![alt text](../assets/screenshots/module%2007/lab%204/image.png)

2\. ลองสร้าง file ทิ้งไว้ใน

C:

![alt text](../assets/screenshots/module%2007/lab%204/image-1.png)

D:

![alt text](../assets/screenshots/module%2007/lab%204/image-2.png)

## 2. Change VM size

1\. เปลี่ยน size ของ VM

![alt text](../assets/screenshots/module%2007/lab%204/image-3.png)

VM จะถูก restart

![alt text](../assets/screenshots/module%2007/lab%204/image-4.png)

2\. ตอนนี้ VM ของเราใช้ size ใหม่แล้ว

![alt text](../assets/screenshots/module%2007/lab%204/image-5.png)

## 3. After resize

1\. ลองดูว่าข้อมุลใน drive C ยังอยู่

![alt text](../assets/screenshots/module%2007/lab%204/image-6.png)

![alt text](../assets/screenshots/module%2007/lab%204/image-7.png)

แต่ข้อมูลใน drive D หายไป

![alt text](../assets/screenshots/module%2007/lab%204/image-8.png)

เพราะ VM ถูกย้ายไปที่ Hyper-V host ใหม่แล้วนั่นเองครับ

Get-ItemProperty -Path "HKLM:\SOFTWARE\Microsoft\Virtual Machine\Guest\Parameters"  | Select-Object HostName

![alt text](../assets/screenshots/module%2007/lab%204/image-9.png)

## Ref.

- [https://techcommunity.microsoft.com/t5/itops-talk-blog/find-the-hostname-of-a-hyper-v-vm/ba-p/2074171](https://techcommunity.microsoft.com/t5/itops-talk-blog/find-the-hostname-of-a-hyper-v-vm/ba-p/2074171)

...