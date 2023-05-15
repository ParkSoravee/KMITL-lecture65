
## มาตรฐานการดูแลระบบ

>เพื่อที่จะทำให้

### COBIT
การทำงานเข้าไกล้เป้าหมาย
มุ่งเน้นเป้าหมาย แต่ไม่ได้บอก solution
![[Pasted image 20230329095016.png|500]]

### ITIL
มุ่งเน้นไปที่ library ต้องทำ 1,2,3,4 ให้ได้เป้าหมาย
เอา mission goal มาตั้ง core ก่อน (คล้าย business)
แล้วเป้าหมายนี้มี service อะไรบ้าง
![[Pasted image 20230329095141.png|500]]
ถ้าทำ 5 service นี้ได้จะดี ^^^ lifecycle
design -> implement

>ex. app ตู้ธนาคาร ทำ service transition ดีมาก
>ที่ต่อ network ได้ เวลาอัพเดทสั่งจากส่วนกลาง ไม่มีคนมาจิ้ม

เปลี่ยน อัพเกรดหรือเพิ่ม sw ยังให้ให้ไม่กระทบระบบเดิม -> change management (ธนาคารทำยาวมากๆ) (service transition)

ถ้าทำ service design ต้องทำให้ได้ข้างบน 4 ข้อ
- supplier management ใครบ้างที่ feed ของให้เรา
- service level ดีมากน้อยแค่ไหน (Service Level Agreement : SLA) ex. online 24/7 availability 99.99 (ปีนึงล่มได้ 1ชม.) *ต้องเขียนไว้ตอน design ระบบ สำคัญมาก*
- service catelog เป็นบอกว่า service มี module อะไรบ้าง
- ทำให้ server มี availibility

design structure
admin ดูเรื่อง load, monitor

ทำกระทั่ง service มัน deploy ลงไปได้
วงในทั้ง 3 อันเน้นที่การ monitor

process ที่ต้องทำคือวงนอก
report & measurement ต้องวัดผลให้ได้ มีการ improve เสมอ
CIO มองด้านใน
PM ดูแลก้อนเล็กๆ วงนอก
แรกๆ เราอาจจะเป็นส่วนนึงในวงนอก รวมถึงการปรับปรุง
ex. เพิ่ม server 3 ตัว ทำไง?, availibility ทำ dr side

### ISO 20000

ทำ 2 อันบนแล้ว มักเข้ามาเสียบตอนท้าย เป็นผู้ issue มาตรฐาน
เป็น standard

![[Pasted image 20230329100207.png|600]]
ถ้าอยากขอ cer ต้องทำตามนี้
ต้องเขียนกฎและให้คนในองค์กรทำตาม

มี guildline กว้างๆ iso 
ถ้าอยาก implement/ improve ไปดึงเอา COBIT, ITIL มา

### Summary

>admin เน้น ITIL
>COBIT เป็นก้อนใหญ่ไม่ได้บอกว่าทำอะไร ยังไง

ถ้าทำงานด้วยนี้ไม่จำเป็นต้องรู้ทั้งหมดของ ITIL
หนังสือที่บอกวงนอกของ ITIL แตกเป็นงานย่อยๆ ได้
![[Pasted image 20230329100541.png|600]]

ex. problem management - เช่นการเปิด ticket
งานของ IT System Management

- network management - config ระบบ network ได้
- storage - raid, allocate
- security - filter ได้ ป้องกัน ตรวจจับ incident ได้

>ดูว่าใบ tools ที่เตรียมมา ตอบโจทย์ด้านไหนของ IT System Management บ้าง


## System Monitoring

ex. 
- Solorwinds ใช้ที่ easypass
- Zabeix ดึงข้อมูลการใช้งานพื้นฐาน ไปดึงค่าใน server ไปเก็บเป็น system monitor report ได้

System Monitoring
ต้องขอสิทธิ์ หรือเปิด protocol ด้วย

Application
ต้องเอา agent ไปติดตั้ง หรือทำ remote เข้าเช็ค หรือเปิดหน้าเว็บเช็ค

Network
util ดูกราฟ
connectivity ดูว่า on/off อยู่ไหม ใช้ ping ได้

![[Pasted image 20230329103144.png|500]]
น้ำเงิน capability
เส้นแดง คือข้อมูลจริง

OS Load มีแถวรอตลอด (แบ่งงานมาแต่ละตัวๆ)
Disk หมายถึง I/O R/W 

คำถามคือระบบนี้เกิดเหตุอะไรขึ้น แล้วจะแก้ยังไง
- App กิน RAM เยอะเกิน Memory ไม่พอ แล้วทำไมถึงเกิด Disk เกิน เพราะเกิด SWAP (virtual memmory) แก้โดย
	- เพิ่ม RAM
	- ลด legacy ของ disk : เปลี่ยน HDD เป็น SSD
	- ซื้อเครื่องใหม่ (3-4 ปี แล้ว capacity ใช้ 80% เพราะตามบช มีอายุ 5 ปี)
- เกิดคอขวดที่ OS Load (ex. การขอ transcript มหาลัย ผอ. ต้องมาเซ็นทุกใบ เปลี่ยนเป็นภาพแทน) 

### ตัวอย่าง Tools

#### CACTI
ฟรี
ใช้ SNMP ไปดึงข้อมูล server
![[Pasted image 20230329104357.png|500]]
CPU Usage 
avg 49.5 ไม่เกิน 70 ถือว่า safe

buffer ใช้สำหรับ app , system ที่รันอยู่
cache รอให้ buffer ดึงไปใช้

![[Pasted image 20230329104722.png|500]]
load - cpu ทำงานหนักแค่ไหน (front counter)
>cpu load ต้องน้อยกว่า cpu core

snapshot 1 นาที แล้วทำ avg 1,5,15min
เวลาดู ดูเฉพาะ avg 1min พอ
cpu 2 ตัวสามารถทำงานได้

traffic มีอะไรผิดปกติบ้าง?
เส้นสีน้ำเงินที่กระโดด อาจจะมี script บางอย่างรัน ไปหาให้เจอว่า script ปกติหรือผิดปกติ

![[Pasted image 20230329105251.png|500]]
DB ส่วนใหญ่ทำงานที่ Memory
จะทำที่ disk เมื่อ commit data
ดังนั้นมอง IO R/W สูงไหม ถ้าสูงแปลว่ามี force commit บ่อย
ดูเส้นแดง

### Solar wind

ตัวหลักราคาไม่แพง แต่ส่วนเสริมแพง
![[Pasted image 20230329105409.png|600]]
![[Pasted image 20230329105456.png|600]]

![[Pasted image 20230329105615.png|600]]
มีอะไรผิดปกติไหม? ไม่มี แต่ละอันไม่เกิน
แต่มี spike เป็นช่วงๆ มีรอบประมาณ 4 ชม.
สอดคล้องกับ RAM (ภาพด้านล่าง)

![[Pasted image 20230329105710.png|600]]
แสดงว่ามี program บางอย่างทำงานเป็นช่วงๆ

ที่ด่าน มี pc ตัวนึงแสดงเงินที่เหลือ แล้วโยนไปด่าน
แล้วทุก 4 ชม. ส่งไป HQ และดึงข้อมูลกลับมาเก็บไว้ที่ด่าน
(เพราะ req ให้หน้ด่านทำงานได้ แม้ HQ จะล่ม)

DB เป็น App ตัวนึง
![[Pasted image 20230329110056.png|600]]
ระบบนี้จะไม่สามารถทำงานได้อีกทีวันไหน?
32GB จะ down อีก 2-3 วันแน่ๆ ต้อง reboot ใหม่
ปัญหาจริงๆ คือ เขียนด้วย java แล้วเขียน ... ได้ไม่ดี
java สร้าง vm มา take RAM แล้วไม่คืน
เจอโดยไปดูใน RAM ว่าโปรแกรมอะไรใช้เยอะ

ปรับปรุงโดย
- ปรับ version 
- down ทุกๆ กี่วัน - ทุกๆ 2 สัปดาห์ (ช่วงไหน load น้อยๆ ก็ down) ระบบ reboot กี่นาที? down ได้ไม่กระทบหน้าด่าน

![[Pasted image 20230329110524.png|600]]
เช็คว่าระบบไหน down บ้าง

## Intrusion Prevention System

โดยทั่วไปจะมีการตัดการเชื่อมต่อให้ได้ด้วย เป็น firewall ได้ (แต่ในภาวะผิดปกติ)
- Network-based IPS - ติดตั้ง sw, rt
- Host-based IPS - ติดตั้งที่ pc

detect กับ alert แต่ทำอะไรไม่ได้
ex. SNORT เป็น pattern matching

### IPS Detection Method
รูปแบบการทำงาน
- Signature-Based Detection : Pattern Matching ex. SNORT
	- ทำ pattern ของ app layer ไว้ กำหนด monitor port อะไร service อะไร
	- ex. mail server ตั้งไว้ที่ port 25 ใส่กฎลงไป
- Statistical Anomaly-Based Detection : Count and set Threashou ไว้
	- ex. DNS นาทีละ 10req IPS จะรับให้แล้วนับ ถ้าเจอว่าต้นทางเครื่องนี้มา 300req -> anormaly แล้วตัดการเชื่อมต่อ (admin เป็นคนตั้ง)
	- อะไรก็ตามที่นับตัวเลขได้ จับได้หมด
- Stateful Protocol Analysis Detection : set state

>IPS เก่งกว่า firewall นิดนึง แต่ take cpu

![[Pasted image 20230329111443.png]]

**StoneGate Deployment IDS mode**
IPS เหมือน police ซ่อน ไม่แสดงตัว
ทำหน้าที่คล้าย switch ping ไม่เจอ มี port น้อย
monitor traffic ที่ผ่าน ถ้าผิดปกติก็ drop ทิ้ง
ข้อดีคือหาไม่เจอแน่ๆ ไม่รู้ว่ามี IPS อยู่

**IPS mode**
มี mirror port (span port)
ใช้ switch ต้องมีช่อง traffic ที่เข้าออกทุก port จะเข้ามา IPS ด้วย
ข้อเสียคือแค่ alert ทำอะไรไม่ได้
จึงเป็นชุด ขายทั้ง solution IPS+Switch ให้ IPS สั่ง Switch ไปตัดการเชื่อมต่อ

cisco SPAN port ตั้งได้ว่า port ที่เท่าไรๆ ส่งออกไป spamport ด้วย
(ตั้งได้ว่า SPAN port จะเป็น port ไหน) และสามารถดึง Virtual port ได้ด้วย

>SPAN vs Mirror port
>SPAN ดีกว่า
>- ผู้พัฒนาไม่ต้องทำ port เพิ่ม
>- port แต่ละอัน bandwidth มีกี่ port แสดงว่า mirror ใช้ UDP ไม่ได้ต้อง Fiber
>- SPAN กำหนดเป็น secment ได้ flexible มากกว่า

![[Pasted image 20230329112205.png|500]]
มูลค่าเท่าไร
ลิส 5 การโจมตีที่อุปกรณ์ทั้งหมด ไม่สามารถจัดการ ตรวจสอบการโจมตีได้
ของในมือกันอะไรได้ ไม่ได้















