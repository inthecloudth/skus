## 1. Create a new resource group

ลองสร้าง resource group ใหม่

![alt text](../assets/screenshots/module%2007/lab%203/image.png)

## 2. Move a VM to a new resoure group

1\. ลองย้าย VM และ resource ที่เกี่ยวข้อง (ที่ใช้ประกอบกันเป็น VM) ไปด้วย

![alt text](../assets/screenshots/module%2007/lab%203/image-1.png)

2\. เลือก resource group ปลายทาง

![alt text](../assets/screenshots/module%2007/lab%203/image-2.png)

3\. รอให้ระบบ validate เสร็จ แล้วจึงย้ายได้

แต่ให้เรากดปิดได้เลย ไม่ต้องย้ายก็ได้ครับ เพราะต้องใช้เวลารอ

![alt text](../assets/screenshots/module%2007/lab%203/image-3.png)

ซึ่งเราอาจจะดูตัวอย่างการย้ายจาก link นี้แทน

[https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/move-resource-group-and-subscription](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/move-resource-group-and-subscription)

4\. (Optional) แต่ถ้าเรารอ จนกดย้าย ก็จะได้ผลลัพธ์แบบนี้นะครับ

![alt text](../assets/screenshots/module%2007/lab%203/image-100.png)

![alt text](../assets/screenshots/module%2007/lab%203/image-101.png)

![alt text](../assets/screenshots/module%2007/lab%203/image-102.png)

![alt text](../assets/screenshots/module%2007/lab%203/image-200.png)

![alt text](../assets/screenshots/module%2007/lab%203/image-201.png)

และสำหรับการย้ายที่ยังอยู่ใน region เดิมแบบนี้ VM จะไม่ถูก shutdown หรือ restart ยังทำงานต่อไปได้เหมือนเดิม (สังเกตว่าหน้าจอเดิมยังเปิดค้างอยู่)

แต่หากเป็นการ move ข้าม region ตัว VM จะถูก shutdown นะครับ

[https://stackoverflow.com/questions/53146124/azure-resource-groups-moving-to-a-new-resource-group-is-there-any-downtime](https://stackoverflow.com/questions/53146124/azure-resource-groups-moving-to-a-new-resource-group-is-there-any-downtime)

![alt text](../assets/screenshots/module%2007/lab%203/image-202.png)

...