# BTC Exchange Rates

[https://github.com/mihawktheone/WEB_PROJECT.git]  
เป็น Web Application ในการแสดงอัตราการแลกเปลี่ยนต่อ 1 BTC เป็นแต่ละ สกุลเงิน Digital ต่างๆ  
ข้อมูลแสดงรายวันและแสดงกราฟย้อนหลังจากวันปัจจุบันไป 30 วัน เพื่อเห็นแนวโน้ม  
โดย  API ที่ใช้จะเป็นสรุปย้อนหลังในแต่ละวัน โดยจะไม่มีการ update แบบ Real-Time ทันที  

[http://18.142.218.90:80/]  
  
<img width="900" alt="WEB_PROJECT2" src="https://github.com/user-attachments/assets/175dade5-9461-42cc-b6ad-042b8037b7da">

<img width="900" alt="WEB_FLOW" src="https://github.com/user-attachments/assets/b5797f4e-1166-4724-93e4-3368c8b13975">

  
  
## 1.หลักการพัฒนา

### Front-end ใช้ Bun Vite+React Javascript 
  Bun เป็น runtime ที่มีประสิทธิภาพสูงมาก ทำให้ขั้นตอนการติดตั้งและการ build เร็วขึ้น ซึ่งช่วยลดเวลาในการพัฒนาลงได้
Vite และ React การตั้งค่าเริ่มต้นโปรเจกต์มีความรวดเร็ว และการติดตั้งรวมถึงการตั้งค่าพื้นฐานก็ไม่ซับซ้อน ทำให้เริ่มต้นพัฒนาได้ทันทีโดยไม่ต้องตั้งค่า config เยอะ
Vite ใช้ ES Modules เป็นหลัก ซึ่งเข้ากันได้ดีกับโครงสร้างการทำงานแบบใหม่ใน JavaScript ทำให้การนำเข้าและจัดการโมดูลมีความเป็นระเบียบและใช้งานได้ง่ายกว่า

### Database ใช้ PostgreSQL
  PostgreSQL มีฟีเจอร์ JSONB ทำให้สามารถจัดเก็บและจัดการข้อมูล JSON ได้อย่างมีประสิทธิภาพ 
  เหมาะกับการพัฒนาแอปพลิเคชันที่ต้องการการจัดเก็บข้อมูลแบบกึ่งโครงสร้าง (Semi-structured data) และใช้งานร่วมกับ NoSQL ได้ในบางกรณี ทำให้มีความยืดหยุ่นสูง

### Back-end ใช้ Bun Express
  Express เป็นเฟรมเวิร์กที่เบาและมีความยืดหยุ่นสูง ซึ่งช่วยให้สามารถตั้งค่าและจัดการเส้นทาง (routes) ได้อย่างง่ายดาย 
  ทำให้เหมาะสำหรับการพัฒนา API และเว็บเซิร์ฟเวอร์ การทำงานร่วมกับ Express ใน Bun ทำให้สามารถใช้ประโยชน์จาก Middleware ต่างๆ ที่มีอยู่แล้วใน Express 
  และสามารถขยายระบบเพิ่มเติมได้ตามความต้องการ
<br>
<br>
<br>
## 2.API ที่สำคัญ
ดึงข้อมูลอัตราแลกเปลี่ยนสกุลเงิน Digital ประจำวันต่อ 1BTC จาก  
[https://cdn.jsdelivr.net/npm/@fawazahmed0/currency-api@latest/v1/currencies/btc.json]  
  
ซึ่งจะแสดงวันที่ล่าสุด และการดึงข้อมูลย้อนหลังจะเปลี่ยนช่วงวันที่จาก  
[https://cdn.jsdelivr.net/npm/@fawazahmed0/currency-api@2024-10-01/v1/currencies/btc.json]  
  
<br>
<br>
<br>
## 3.วิธี Deploy
CurrencyExchangeProject/<br>
&nbsp;│<br>
&nbsp;|─ front-end(CurrencyExchange)/<br>
&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|── Dockerfile  # Front-end Dockerfile<br>
&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|── ...&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Other front-end files<br>
&nbsp;│<br>
&nbsp;|─ back-end(backend)/<br>
&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|── Dockerfile  # back-end Dockerfile<br>
&nbsp;│&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|── ...&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;# Other back-end files<br>
&nbsp;│<br>
&nbsp;|─ docker-compose.yml<br>
<br>
<br>
<br>
ใช้ Dockerfile และ docker-compose  
ทั้งใน Front-end และ Back-end จะมี Dockerfile สำหรับ run  
และมี docker-compose.yml ในการ build ทั้ง Back-end และ Front-end  
  
การทดสอบ Deploy ที่เครื่อง  
ทำการติดตั้ง docker และ docker-compose ก่อนการใช้งาน  
  
ทำการดึงไฟล์ทั้งหมดจาก github
``` bash 
git clone https://github.com/mihawktheone/WEB_PROJECT.git
```

ทำการ Build 
``` bash
docker-compose up -d --build หรือ docker-compose up
```

กรณี down
``` bash
docker-compose down
```
<br> 
<br> 
<br> 
ข้อมูลนี้เป็นส่วนหนึ่งของ<br>
รายวิชาวิศวกรรมเว็บและคลาวด์ หลักสูตรวิศวกรรมศาสตรมหาบัณฑิต<br> 
วิทยาลัยวิศวกรรมศาสตร์และเทคโนโลยี<br>
มหาวิทยาลัยธุรกิจบัณฑิตย์<br>
<br>
ผู้จัดทำ<br>
66130502 นายปฏิวัติ สบายยิ่ง<br>
<br>
<a href="https://cite.dpu.ac.th/ResumeDean.html"> อาจารย์ที่ปรึกษา ผศ.ดร.ชัยพร เขมะภาตะพันธ์</a>


![logo-cite-edit](https://github.com/user-attachments/assets/352a53c0-341f-4d4a-afa8-d3d67340ef70)

