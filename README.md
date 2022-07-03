# การใช้ปัญญาประดิษฐ์เพื่อคัดแยกประเภทภาพสแกนของเอกสารทางการแพทย์
## Contents
* [วัตถุประสงค์](#วัตถุประสงค์)
* [วิธีการทดลอง](#วิธีการทดลอง)
* [การประเมินผล](#การประเมินผล)
### **วัตถุประสงค์**

เพื่อสร้าง AI มาคัดแยกภาพสแกนของเอกสารทางการแพทย์ 

### **วิธีการทดลอง**

1. เตรียมข้อมูล : 
![image](https://user-images.githubusercontent.com/76510467/177020796-13066aeb-5755-4b79-bda8-11ba07d1ee51.png)
  -  1.1 เตรียมเอกสารสแกน พร้อมทั้งชนิดของประเภทเอกสาร ซึ่งใน projectนี้ แบ่งเป็น 4 ประเภท คือ 
     - 1) ผลการตรวจพยาธิวิทยา 
     - 2) ผลการตรวจทางรังสีวิทยา 
     - 3) ผลตรวจทางห้องปฎิบัติการ  
     - 4) เอกสารอื่นๆ
  - 1.2 นำเอกสารผ่าน OCR tool เพื่อแปลงตัวอักษรในภาพให้กลายเป็นตัวอักษร (text)ที่สามารถประมวลผลต่อได้ ซึ่งในโครงการนี้ใช้ library ของ https://pypi.org/project/pytesseract/ ตัวอย่างวิธีการใช้งานมีในไฟล์ https://github.com/ekapob-sang/Scanned-document-classification/blob/a6a370f1e0ef661e151b34eb269a44981e7e1860/svm_plot.png
  - 1.3 ทำการตัดคำ ( Tokenization ) , เอาคำทั่วๆไป (ซึ่งไม่สำคัญออก เช่น the , a , on ) , เอาสัญลักษณ์และตัวเลขออก, ลดรูปขแ
องคำ ( stemmatization เพื่อลดความหลากหลายของคำ เช่น lying , lies เมื่อลดรูปแล้วเท่ากับคำว่า lie เหมือนกัน) และปรับคำให้เป็นตัวพิมพ์เล็กทั้งหมด โดยมีตัวอย่าง code ตามรูป
2. สร้างโมเดล




### **Model **
Multiclass classification 



### Author
	นายแพทย์เอกภพ แสงอริยวนิช พ.บ., วว.โสต ศอ นาสิก วิทยา
	กลุ่มงานโสต ศอ นาสิก และ กลุ่มงานดิจิทัลทางการแพทย์ สถาบันมะเร็งแห่งชาติ 
	Email : ekapobkks@gmail.com
	ปัจจุบันเป็น Ph.D student สาขาวิชา Data Science for Healthcare and Clinical Informatics
        ของ Department of Clinical Epidemiology & Biostatistics
	Faculty of Medicine, Ramathibodi Hospital, Mahidol University

 

