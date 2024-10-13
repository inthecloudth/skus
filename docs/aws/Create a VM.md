## 1. Create an Azure VM

### 1.1 Create an Azure VM

1\. สร้าง Azure VM

- Resouce group = ชื่ออะไรก็ได้
- Virtual machine name = ชื่ออะไรก็ได้
- Image = Windows อะไรก็ได้
- Size = อะไรก็ได้ (RAM สัก 2-4 GB)
- ใช้ Azure Hybrid Benefit เพื่อให้ค่าใช้จ่ายถูกลง

แล้วกด Next

![alt text](../assets/screenshots/module%2007/lab%201/image.png)

2\. ระบบเลือก OS disk แบบ premium SSD ให้เรา

เราสร้าง VM ใน availability zone จึงถูกบังคับให้ใช้ managed disks (managed disk ดีแล้ว)

![alt text](../assets/screenshots/module%2007/lab%201/image-1.png)

3\. เรายังไม่มี virtual network ใน Azure

เราก็ให้เขาสร้าง virtual network รวมถึง subnet, public IP, network security group (NSG), และเปิด remote desktop จาก Internet ให้เราเลยนะครับ

> ของจริงควรตั้งชื่อ resource ให้เหมาะสมกว่านี้ และระวังเรื่อง RDP จาก internet อย่าเปิดให้เข้ามาจาก Any นะครับ

![alt text](../assets/screenshots/module%2007/lab%201/image-2.png)

4\. กด Next ไปเรื่อยๆ (แต่ลองรีวิวค่า default settings ต่างๆ ด้วยนะครับ)

![alt text](../assets/screenshots/module%2007/lab%201/image-3.png)

![alt text](../assets/screenshots/module%2007/lab%201/image-4.png)

![alt text](../assets/screenshots/module%2007/lab%201/image-5.png)

![alt text](../assets/screenshots/module%2007/lab%201/image-6.png)

5\. แล้ว Create

![alt text](../assets/screenshots/module%2007/lab%201/image-7.png)

### 1.2 Review related resources

1\. เมื่อ VM สร้างเสร็จแล้ว ลองกดเข้าไปรีวิวกันนะครับ

![alt text](../assets/screenshots/module%2007/lab%201/image-8.png)

ลองดูค่าต่างๆ ใน Overview

![alt text](../assets/screenshots/module%2007/lab%201/image-9.png)

2\. ลองกด resource group ที่ VM อยู่

![alt text](../assets/screenshots/module%2007/lab%201/image-10.png)

เราจะเห็น resource ถูกสร้างขึ้น 6 ตัว เพื่อประกอบมาเป็น VM เครื่องนี้

![alt text](../assets/screenshots/module%2007/lab%201/image-11.png)

### 1.3 Connect the VM

1\. ลอง remote เข้าไปใน VM

![alt text](../assets/screenshots/module%2007/lab%201/image-12.png)

![alt text](../assets/screenshots/module%2007/lab%201/image-13.png)

2\. VM ใช้ dynamic IP อยู่

และเนื่องจากเป็น resource ตัวแรกของ subnet จึงได้ IP address เริ่มที่เบอร์ที่ 4 (10.0.0.4)

ส่วน DNS ที่ได้รับจาก DHCP server ชี้ไปที่ IP ของ Azure DNS

![alt text](../assets/screenshots/module%2007/lab%201/image-15.png)

3\. ตอนนี้ VM มี 2 local drives คือ C: (OS disk) และ D: (temp disk)

> OS disk ถูกเก็บอยู่ใน storage account แต่ temp disk อยู่บน Hyper-V host ที่ VM รันอยู่ หาก VM ถูกย้ายไปรันบน Hyper-V host เครื่องอื่นๆ ตัว temp disk จะไม่ตามไปด้วย (ดังนั้น อย่าเก็บข้อมูลที่เราต้องการให้อยู่แบบถาวรลงบน temp disk นะครับ ให้เก็บลงใน OS disk หรือเพิ่ม data disk ลูกใหม่ แล้วเก็บลงใน data disk แทน)

![alt text](../assets/screenshots/module%2007/lab%201/image-14.png)

## 2. More about related resouces

### 2.1 All network resources

Resouces ทางด้าน network ของ VM เครื่องนี้ มี 4 ตัว

- Public IP
- Network security group (NSG)
- Virtual network
- Network interface

![alt text](../assets/screenshots/module%2007/lab%201/image-17.png)

มีค่าดังนี้

![alt text](../assets/screenshots/module%2007/lab%201/image-18.png)

ซึ่งเราค่อยๆ ไล่ดูกันนะครับ

#### 2.1.1 Public IP

1\. Public IP

![alt text](../assets/screenshots/module%2007/lab%201/image-19.png)

ผูกเข้ากับ network interface และ vm1

![alt text](../assets/screenshots/module%2007/lab%201/image-24.png)

2\. Public IP ถูก assign แบบ static

![alt text](../assets/screenshots/module%2007/lab%201/image-25.png)

#### 2.1.2 Network Security Group (NSG)

1\. ที่ NSG

![alt text](../assets/screenshots/module%2007/lab%201/image-20.png)

Remote desktop จาก Internet ถูก Allow อยู่

มี source = Any

![alt text](../assets/screenshots/module%2007/lab%201/image-26.png)

เราสามารถแก้ไข หรือ เพิ่ม/ลด rule ได้

![alt text](../assets/screenshots/module%2007/lab%201/image-27.png)

2\. NSG apply ไปที่ network interface เพื่อ allow หรือ deny network traffic ตามที่เรากำหนด

![alt text](../assets/screenshots/module%2007/lab%201/image-28.png)

3\. ตอนนี้ NSG ยังไม่ได้ apply ที่ระดับ subnet

![alt text](../assets/screenshots/module%2007/lab%201/image-29.png)

#### 2.1.3 VNet

1\. รีวิว virtual network

![alt text](../assets/screenshots/module%2007/lab%201/image-21.png)

มี 1 subnet ถูกสร้างขึ้นมา

Address space = 10.0.0.0/24

![alt text](../assets/screenshots/module%2007/lab%201/image-31.png)

2\. 10.0.0.0/24 เป็น subnet ภายใต้ virtual network 10.0.0.0/16

![alt text](../assets/screenshots/module%2007/lab%201/image-32.png)

3\. ตอนนี้มี network interface 1 ใบ เกาะอยู่ใน virtual network นี้แล้ว

ซึ่งก็คือ network interface ของ vm1 (IP 10.0.0.4)

![alt text](../assets/screenshots/module%2007/lab%201/image-33.png)

4\. Virtual network วงนี้ assign Azure DNS ผ่าน DHCP ให้กับ DHCP client (IP ของ Azure DNS คือ 168.63.129.16)

![alt text](../assets/screenshots/module%2007/lab%201/image-34.png)

#### 2.1.4 Network interface

1\. รีวิว network interface

![alt text](../assets/screenshots/module%2007/lab%201/image-22.png)

Network interface ใบนี้มี public IP assign อยู่

Network interface ใบนี้ถูกใช้โดย vm1

![alt text](../assets/screenshots/module%2007/lab%201/image-35.png)

2\. ดู IP configurations เพิ่มเติม

![alt text](../assets/screenshots/module%2007/lab%201/image-36.png)

ตอนนี้ network interface ใช้ private IP แบบ dynamic อยู่

และมี public IP ผูกเข้าหาด้วย

![alt text](../assets/screenshots/module%2007/lab%201/image-37.png)

### 2.2 Disks

รีวิว disks

![alt text](../assets/screenshots/module%2007/lab%201/image-38.png)

VM ใช้ OS disk แบบ premium SSD

ยังไม่มี data disk

![alt text](../assets/screenshots/module%2007/lab%201/image-39.png)

### 2.3 VM

แล้วลองรีวิวข้อมูลทั่วไปของ VM ดู

![alt text](../assets/screenshots/module%2007/lab%201/image-40.png)

ลองตอบคำถามเกี่ยวกับ VM เครื่องนี้ดูนะครับ

- Public IP = ?
- Private IP = ?
- Computer name = ?
- OS = ?
- VM size = ?
- มี RAM เท่าไหร่?
- อยู่ใน virtual network และ subnet ชื่อว่าอะไร?

![alt text](../assets/screenshots/module%2007/lab%201/image-41.png)

...