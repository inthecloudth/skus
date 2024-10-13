## 1. Delete VMs (If you encountered the subscription quota limit issues)

หากเราใช้ Azure subscription แบบ free trial อยู่ อาจจะเจอปัญหา quota limit ที่ทำให้เราสร้าง VM ใหม่เพิ่มไม่ได้

ดังนั้น ถ้า lab ก่อนหน้า เราไม่ใช้แล้ว เราก็ลบ resources ทั้งหมดใน resource group ออกไปเลยก็ได้ครับ

![alt text](../assets/screenshots/module%2007/lab%207/image.png)

![alt text](../assets/screenshots/module%2007/lab%207/image-1.png)

ซึ่งตอนนี้ resources ทั้งหมดถูกลบแล้ว

![alt text](../assets/screenshots/module%2007/lab%207/image-2.png)

## 2. Create a base image

เราจะใช้ image ที่มีอยู่แล้วใน Azure ไปสร้าง VM scale set เลยก็ได้

แต่ให้เราจินตนาการว่า เราจะสร้าง VM ใหม่ ติดตั้ง middle ware ติดตั้ง tool หรือ utility ต่างๆ ติดตั้ง app ที่จะนำไปให้บริการจะดีกว่า

จากนั้นก็ capture เป็น image ของบริษัทเรา แล้วนำไปใช้สร้าง VM scale set กันนะครับ

### 2.1 Create a new VM

1\. สร้าง VM ใหม่

![alt text](../assets/screenshots/module%2007/lab%207/image-3.png)

2\. Remote เข้า VM

![alt text](../assets/screenshots/module%2007/lab%207/image-4.png)

### 2.2 Install app and anything you want on the base VM

ติดตั้ง app ตามต้องการ เช่น IIS

![alt text](../assets/screenshots/module%2007/lab%207/image-5.png)

### 2.3 Capture the image

1\. จากนั้น sysprep เพื่อสร้างเครื่องต้นแบบ

![alt text](../assets/screenshots/module%2007/lab%207/image-6.png)

![alt text](../assets/screenshots/module%2007/lab%207/image-7.png)

เครื่องจะถูก shutdown

![alt text](../assets/screenshots/module%2007/lab%207/image-8.png)

2\. แล้วให้เรา capture image จาก VM ที่ sysprep แล้ว

![alt text](../assets/screenshots/module%2007/lab%207/image-9.png)

ถ้า capture image เสร็จแล้วให้ลบ VM ทิ้งเลย

แล้วกด Create new Target VM image definition

![alt text](../assets/screenshots/module%2007/lab%207/image-10.png)

3\. ตั้งชื่ออะไรก็ได้

![alt text](../assets/screenshots/module%2007/lab%207/image-11.png)

ตั้ง version number อะไรก็ได้

เลือก Default storage sku = Standard HDD LRS

![alt text](../assets/screenshots/module%2007/lab%207/image-12.png)

แล้ว Create

![alt text](../assets/screenshots/module%2007/lab%207/image-13.png)

4\. ตอนนี้เราได้ image สำหรับนำไปสร้าง VM scale set หลายๆ instance แล้วนะครับ

![alt text](../assets/screenshots/module%2007/lab%207/image-14.png)

## 3. Create a VMSS

### 3.1 Configure autoscaling condition

1\. สร้าง VM scale set

![alt text](../assets/screenshots/module%2007/lab%207/image-15.png)

เลือก Scaling mode = Autoscaling

แล้วกด Configure

![alt text](../assets/screenshots/module%2007/lab%207/image-16.png)

2\. Edit

![alt text](../assets/screenshots/module%2007/lab%207/image-17.png)

ตั้ง scaling condition

- Initial instance count = 1
- Instance limit
  - Minimum = 1
  - Maximum = 2
- Scale in
  - CPU threshold less than = 50
- Query duration
  - 5

Save

![alt text](../assets/screenshots/module%2007/lab%207/image-18.png)

Save

![alt text](../assets/screenshots/module%2007/lab%207/image-19.png)

### 3.2 Select the image

1\. กด See all images

![alt text](../assets/screenshots/module%2007/lab%207/image-20.png)

2\. เลือก image ที่เรา capture ไว้

![alt text](../assets/screenshots/module%2007/lab%207/image-21.png)

### 3.3 Enter other information & create the VMSS

1\. ใส่ข้อมูลอื่นๆ

แล้วกด Next ไปเรื่อยๆ (พร้อมรีวิวค่า default setting ต่างๆ ไปด้วย)

![alt text](../assets/screenshots/module%2007/lab%207/image-22.png)

![alt text](../assets/screenshots/module%2007/lab%207/image-23.png)

![alt text](../assets/screenshots/module%2007/lab%207/image-24.png)

![alt text](../assets/screenshots/module%2007/lab%207/image-25.png)

![alt text](../assets/screenshots/module%2007/lab%207/image-26.png)

![alt text](../assets/screenshots/module%2007/lab%207/image-27.png)

![alt text](../assets/screenshots/module%2007/lab%207/image-28.png)

![alt text](../assets/screenshots/module%2007/lab%207/image-29.png)

จน Create

![alt text](../assets/screenshots/module%2007/lab%207/image-30.png)

2\. ตอนนี้เราได้ VMSS แล้วนะครับ

![alt text](../assets/screenshots/module%2007/lab%207/image-31.png)

## 4. Test scale out

### 4.1 Review scaling contdition

VMSS ของเราเริ่มต้นที่ 1 instance

และถ้า CPU ใช้งานเกิน 80% ใน 5 นาที ระบบจะเพิ่ม VM ใน VMSS ให้เราอีก 1 เครื่อง

![alt text](../assets/screenshots/module%2007/lab%207/image-32.png)

### 4.2 Remote to the VM

1\. เปิด RDP ให้เรา remote เข้า VM ให้ได้ก่อน

![alt text](../assets/screenshots/module%2007/lab%207/image-33.png)

![alt text](../assets/screenshots/module%2007/lab%207/image-34.png)

![alt text](../assets/screenshots/module%2007/lab%207/image-35.png)

![alt text](../assets/screenshots/module%2007/lab%207/image-36.png)

2\. Remote เข้า VM

![alt text](../assets/screenshots/module%2007/lab%207/image-37.png)

3\. ลองเข้า [http://localhost](http://localhost) ว่านี่เป็น image ที่เราเคยเตรียมไว้จริงๆ

![alt text](../assets/screenshots/module%2007/lab%207/image-38.png)

### 4.3 Stress the CPU to be more than 80%

รัน CPU stress เพื่อให้ average CPU utilization มากกว่า 80%

Download CPU stress จาก

[https://learn.microsoft.com/en-us/sysinternals/downloads/cpustres](https://learn.microsoft.com/en-us/sysinternals/downloads/cpustres)

![alt text](../assets/screenshots/module%2007/lab%207/image-39.png)

![alt text](../assets/screenshots/module%2007/lab%207/image-40.png)

![alt text](../assets/screenshots/module%2007/lab%207/image-41.png)

![alt text](../assets/screenshots/module%2007/lab%207/image-42.png)

### 4.4 Review the scale out result

1\. รอจน VMSS scale out VM ให้เราอีก 1 instance

![alt text](../assets/screenshots/module%2007/lab%207/image-43.png)

![alt text](../assets/screenshots/module%2007/lab%207/image-44.png)

2\. ตอนนี้ scale out เป็น 2 instance แล้ว

![alt text](../assets/screenshots/module%2007/lab%207/image-45.png)

## 5. Test scale down

1\. ปิด CPU stress

![alt text](../assets/screenshots/module%2007/lab%207/image-46.png)

![alt text](../assets/screenshots/module%2007/lab%207/image-47.png)

2\. รอสักพัก VMSS จะ scale down เหลือ 1 node ครับ

![alt text](../assets/screenshots/module%2007/lab%207/image-48.png)

...