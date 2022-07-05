# การใช้ปัญญาประดิษฐ์เพื่อคัดแยกประเภทภาพสแกนของเอกสารทางการแพทย์
## Contents
* [วัตถุประสงค์](#วัตถุประสงค์)
* [วิธีการทดลอง](#วิธีการทดลอง)
* [การประเมินผล](#การประเมินผล)
* [Python code](#code)
### **วัตถุประสงค์**

เพื่อสร้าง AI มาคัดแยกภาพสแกนของเอกสารทางการแพทย์ 

### **วิธีการทดลอง**

#### 1. การเตรียมข้อมูล 
![image](https://user-images.githubusercontent.com/76510467/177020796-13066aeb-5755-4b79-bda8-11ba07d1ee51.png)

  1.1 เตรียมเอกสารสแกน พร้อมทั้งชนิดของประเภทเอกสาร ซึ่งใน projectนี้ แบ่งเป็น 4 ประเภท คือ 
  
     1 ผลการตรวจพยาธิวิทยา 
     
     2 ผลการตรวจทางรังสีวิทยา 
     
     3 ผลตรวจทางห้องปฎิบัติการ  
     
     4 เอกสารอื่นๆ
     
  1.2 นำเอกสารผ่าน OCR tool เพื่อแปลงตัวอักษรในภาพให้กลายเป็นตัวอักษร (text)ที่สามารถประมวลผลต่อได้ ซึ่งในโครงการนี้ใช้ library ของ https://pypi.org/project/pytesseract/ 
  
  1.3 ทำการตัดคำ ( Tokenization ) , เอาคำทั่วๆไป (ซึ่งไม่สำคัญออก เช่น the , a , on ) , เอาสัญลักษณ์และตัวเลขออก, ลดรูปขแ
องคำ ( stemmatization เพื่อลดความหลากหลายของคำ เช่น lying , lies เมื่อลดรูปแล้วเท่ากับคำว่า lie เหมือนกัน) และปรับคำให้เป็นตัวพิมพ์เล็กทั้งหมด 

#### 2. สร้างโมเดล
![image](https://user-images.githubusercontent.com/76510467/177083543-818ffb46-3f66-4043-b0ec-4b302c34aa8a.png)

 2.1 random split data (ให้มีสัดส่วนประเภทเอกสารเหมื่อน dataset) 80% สำหรับ train model และ 20% สำหรับ test model
 
 2.2 สร้าง vector representation เป็นตัวแทนข้อความในเอกสาร  โดยวิธี term frequency–inverse document frequency (TFI-DF) ซึ่งใช้หลักการว่า คำๆหนึ่งในเอกสาร มีความสำคัญแค่ไหน เมื่อเทียบกับ 
     คำทั้งหมดในชุดข้อมูล ดังนั้น ถ้าคำที่พบมากในเอกสารหนึ่งๆ แต่คำๆนั้น ก็ปรากฏในเอกสารอื่นๆเช่นกัน ค่าน้ำหนัก tfi-df ก็จะมีค่าน้อย
     
 2.3 Train model ในงานนี้แบบ Multiclass classification   โดยในการสร้างโมเดล เลือก traditional machine learning มาใช้ทดลอง 4 โมเดล ได้แก่ 
   1) Logistic regression (LG)
   2) Naive Bayes (NB)
   3) Random Forest ( RF )
   4) Support vector machine (SVM)
   
 โดยการหาค่า parameter ที่เหมาะสมของแต่ละโมเดลใช้วิธีการ cross validation ร่วมกับ Randomsearch และ Gridsearch
 
 2.4 เมื่อได้ model แล้ว นำ test data มาทดสอบกับโมเดล โดย test data ก็ต้องผ่าน tfi-df แบบเดียวกับ train data 
 
 ### **การประเมินผล**

 
   


### **Python code**
1. แปลง scanned doucmnet ให้เป็น text file

https://github.com/ekapob-sang/Scanned-document-classification/blob/main/code/ocr_to_text.ipynb

2. งานทดลอง





### Author
	นายแพทย์เอกภพ แสงอริยวนิช พ.บ., วว.โสต ศอ นาสิก วิทยา
	-กลุ่มงานโสต ศอ นาสิก และ กลุ่มงานดิจิทัลทางการแพทย์ สถาบันมะเร็งแห่งชาติ 
	-Email : ekapobkks@gmail.com
	-Ph.D student สาขาวิชา Data Science for Healthcare and Clinical Informatics, Department of Clinical Epidemiology & Biostatistics
	 ,Faculty of Medicine, Ramathibodi Hospital, Mahidol University

 

