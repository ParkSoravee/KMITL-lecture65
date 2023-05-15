# Overview and current status of embedded systems

#todo/IT-entre 
- [ ] Speaking: เตรียมพูดการขาย selling (ไม่ใช่ marketing) ขายอะไรก็ได้ที่สามารถซื้อได้จริง ในราคาที่มาขาย ถ้าพูดแล้ว อ. อยากได้ ผ่าน

- What's Embedded system?
- What's Computer?
- What's Software?
- What's Software quality?
- What's Debugging?
- What's testing?

>[!Important] testing กับ debugging process คล้ายกัน แต่คอนเซปต่างกัน 
>Debugging -> Programmer ทำ prove ว่าโปรแกรมทำงานถูกต้อง
>Testing -> QA ทำ process มันทำงานไม่ถูกต้อง
>
>วัตถุประสงค์เดียวกัน เพื่อให้โปรแกรมทำงานถูกต้อง
>แต่การทดสอบต่างกัน คนทำคนละกลุ่มกัน
>ทั้งสองต้องมี test case

## Test cases

**Guild line : test case เทียบกับบรรทัดของโค้ด**
1 test case / 10 LOC
LOC: Line of code

ex
- Func A 200 LOC / 20 test cases

## Project management

**If Program A**
- 10 engr., 1 manager, 1 year project
- But 2 months delay (รู้ทีหลัง)

- 5 engr. add more
	- proj will be bigger delay, Why???

1. Educational problem : Engr. 5 คนที่ add มา ไม่รู้เรื่อง project
	- คนที่รู้ต้องมาสอนงาน คนทำงานน้อยลง
2. Communication complex
	- More people, more complex

>[!Danger] ข้อเสียของ brain strom เพราะคนทั้งห้องจะติข้อเสีย ไอเดียก็ตกไป เลยไม่มีใครกล้าเสนอไอเดีย 

**การประชุม**
- เพื่อการถ่ายทอด
- เพื่อการหาไอเดีย มาตัดสินใจ

![[Pasted image 20230123140240.png]]

example: what bugs?
![[Pasted image 20230123140612.png|500]]
6 year old??
6 ปี 3 เดือน ?
250 ปี ?? (ค่าเฉลี่ยเกินนน)
คิดปียังไง
ระบบเตือน ถ้าเตือน เตือนที่เท่าไร

อันนี้ req ลูกค้า แต่ไม่ใช่ software req
ต้องไปทำ sw req ยาวมากก

## Bug collected

วิธี manage bug ที่เจอ

- when detected
	- บันทึก
	- id number, symptom of the bug, who find out, when, seriousness

>ญี่ปุ่น เจอบัคเป็นการช่วยบริษัท มีการเก็บไว้ แก้ครั้งหน้าง่ายขึ้น
>ตะวันตก อินเดีย เจอแล้วแก้เลย ไม่มีใครรู้ อัพแพทช์บ่อยมาก

### Example of bug

- Banking system, data mismatch เงินใน db 2 อัน ไม่ตรงกัน
- Crash 1 system is ok
	- but difference systems is also crash cos that bug is TERRIBLE

>[!Important] การแก้ปัญหาในโลกจริง ไม่ตรงกับในการโค้ด มีหลายเรื่องที่ต้องคิด เรื่อง business ความเสียหาย

>[!Important] Realiability & Scalability เรื่องสำคัญในโลก tech

### program จะพร้อม release ได้เมื่อไร
- all case are tested
- ...
- ...
- ระบบรันไป ไม่มีปัญหา 48 ชม.

### Independant QA Engineer

- arond 8% of all engr.
- test
- product จะ launch ไม่ได้ ถ้าไม่ผ่าน
- ..

### The cost of the quality

ตัวอย่าง สมัยก่อน
มีเวลา 12 เดือน มี 10 dev ภาษา C 100,000 LOC
phase:
- requirement spec : 2 months
- designing : 3 months
- coding : 2 months
- debugging : 3 months
- testing QA : 2 months

testing phase (3M)
- 100,000 LOC -> 10,000 test case (1k/ developer)
- 10 days to design 10K test case
- 10 days to check 1K test cases in code inspection
- 40 days to check 10K test cases in machine testing

### ถ้าจะสร้าง sw ให้ดี
มี 3 เรื่อง
- **Quality** -> ทำให้ดี * manage ยากสุด เพราะวัดยาก
- **Schedule** -> ทำให้เร็ว
- **Cost** -> ทำให้ถูก

### Engr. vs Science

- Engr : built something that really worth to use.
	- ต้องคิดต้นทุน ทุกเรื่อง
- Sci : Just possibility.
	- ความเป็นไปได้

Ex. น้ำทะเลเยอะมาก 10 ตัน สกัดเอาทองออกมา
- Engr : Don't worth enough -> so much cost
- Sci : Great new way of tech!

## Student VS Professional Programming

**Student program**
- No quality assurance/control เพราะคนออกแบบ พัฒนา ทดสอบ คนเดียวกัน
- Profitability: 1 LOC = 50 - 100 & 1 person-month = 1K LOC
	- student ไม่สนต้นทุน ว่ามันคุ้มไหม หรือทำกี่วัน เขียน for fun
- Estimation : ประเมินราคา กี่วัน ราคา คน person/month
- Project management : stu dont care
- Risk management : จัดการความเสี่ยง ex. back up, dev หาย
- Error cases : boundary, abnormal
- Reusability : เอา code เก่ามาใช้ซ้ำ แต่ไม่ modify
- GUI : UXUI
- Documentation : ไม่ทำ

## Resource usage

- 1 pregrammer = 1K LOC / month
- 1 line = 50$ - 100$
- 1 prog = 100,000 $ (Japan, US)
- 10-20 prog is ok

>[!Info] SW Engr/Embedded system
>ความสำคัญไม่ได้อยู่ที่การ coding (ใช้เด็กจบใหม่ได้) ที่สำคัญคือ requirement spec, Specification, Design.

## Popular models

### Waterfall model
- Adv : finish phase and go on
- DisAdv: เห็นงานทีตอนจบ

### Spiral model
- ข้อดี: ลูกค้าเห็นการทำงาน แก้ระหว่างทางได้
- ข้อเสีย: วาง arch รองรับระบบใหญ่ยาก for scale

## Software

เป็นสิ่งที่ complex สุดที่มนุษย์สร้าง
1. Software is HUGE! : ระบบเล็กๆ แต่จริงๆ ใหญ่
- พูดถึงสิ่งเดียวกัน มุมมองคนใช้ กับคนสร้าง ต่างกัน

- Mobile phone noKia -> 10M LOC
- Xerox multi function -> 100M LOC

2. SW มองไม่เห็น จับต้องไม่ได้
non-programmer คิดว่ามันสร้างง่าย

3. SW is easy to change เปลี่ยนง่ายมาก
แก้บรรทัดเดียวเปลี่ยนได้แล้ว คอมไพล์เร็ว
ไม่มีความมั่นคง มีบัคค่อยแก้

>[!Info] Software เป็นทั้ง ศาสตร์และศิลป์

4. Software has too much ...

## sw...

- Schedule ทำตาราง
- Cost ดูตัวเลข
	- ต้นทุนส่วนมากคือค่าแรง engr

## SW Quality

วัดยาก เพราะตอบไม่ได้ว่า sw ที่ดีคืออะไร
- Bug น้อย?? แต่ไม่ตอบโจทย์
- Bug free ยากมาก ใช้เวลายากมาก

ดูจาก ความพอใจลูกค้า ได้อยู่
ขึ้นกับ domain ด้วย product แต่ละอันมี domain quality ไม่เหมือนกัน
เช่น เครื่องมือแพทย์

>[!Important] ถ้าอะไรไม่พร้อม lanch บอกลูกค้าด้วยว่า beta release

## Schedule delay

ถ้า sw เสร็จไม่ได้ตาม schedule ถ้าไม่เลื่อน deadline ต้องลด function

## IsO 9126
define มาตรฐานในการทำด้าน SW

1. Functionality
2. ...

#todo/IT-entre
- [x] (ส่ง nextweek) ในแต่ละหัวข้อของ ISO 9126 ถ้าเป็นการเปิดร้านอาหารที่ดี จะเขียนยังไง
เขียนใส่ A4 

week หน้า บ่าย 2-3 มี บ. อื่นมาพูดว่า ช่วง covid ทำไร


# การโน้มน้าวจิตใจ (Convince)

ฝึกโดยใช้หัวข้อทาง IT มาพูดคุยกัน

#todo/IT-entre 
- [x] (ส่ง nextweek) 3 คน present ให้เพื่อนฟัง ออกมา convince ให้เพื่อนและ อ. เห็นด้วย

--- 

13.00-14.00 convince
14.00-15.00 บ. มาพูด
15.00-16.00 convince

---

## iOS better than android

notion

### **Usability → Park**

-   ใช้งานยาวๆ apple claim 6 ปี ได้ iOS รุ่นใหม่ๆ
-   ถ้าใช้ face id ความง่ายในการใช้งาน ใส่หน้ากาก ใส่แว่น ยังใช้ได้
-   ใช้ง่าย android เด่นด้านความยืดหยุ่นของตัวระบบปรับแต่งได้มาก แต่ iOS หน้าตาเหมือนกันทุกรุ่น เปลี่ยนเครื่องก็ยังรู้สึกเหมือนเดิม simple to use ระบบง่ายมาก ไม่ซับซ้อน
-   เลือกซื้อ ง่ายไม่ต้องคิดมาก รุ่นให้เลือกน้อย ไม่ต้องเปรียบเทียบความต่างอะไรมาก มั่นใจได้ว่าจะเป็นมือถือที่ดีแน่นอน วัสดุพรีเมี่ยม สเปคภายในประสิทธิภาพสูง สิ่งที่ต้องคิดคือราคาเท่านั้น
-   ความทนทาน อึด ทนกระแทก จอ **Ceramic Shield**, กันน้ำ กันฝุ่น
-   จักรวาล Ecosystem โคตรแกร่ง ส่วนมากใช้ ipad ด้วยจะดีมาก ตัวอย่าง ทุกอย่างเชื่อมต่อกันได้อย่างลงตัว ลื่นไหล ไร้รอยต่อ
    -   airdrop
    -   copy paste
    -   มีคนโทรเข้ามา รับสายคุย สนทนาผ่าน ipad
    -   apple watch ปลดล็อค iphone , air pod เชื่อมต่อง่ายโคตร
    -   mac ใช้ iphone เป็นกล้องได้ (ใครใช้ mac อยู่บ้าง)
-   trade in เปลี่ยนเครื่อง บริการย้ายข้อมูลมีความปลอดภัยมาก android → iPhone, iPhone → iPhone

### Customer service → Park

-   apple care รับประกันที่ติดกับเครื่องมาอยู่แล้ว 1 ปี / apple care+ แพง (สำหรับผมไม่ค่อยจำเป็น) แต่ได้บริการดีสุดๆ มีศูนย์มาตรฐานทั่วประเทศ
    -   customer support ออนไลน์ ผู้เชี่ยวชาญ
-   จะเห็นว่าหลังๆ สัดส่วน คนรอบตัว ใช้ iphone เยอะขึ้นเมื่อเทียบกับเมื่อก่อน
-   สรุป
-   ราคาแพง เปิดใจทดลอง ความสามารถ ความเร็ว ความปลอดภัย โทรศัพท์ที่จะอยู่กับเราไปนาน คุ้มค่าที่จะลงทุนมากก

---
ในแต่ละหัวข้อของ ISO 9126 ถ้าเป็นการเปิดร้านอาหารที่ดี จะเขียนยังไง
เขียนใส่ A4 
- สถานที่
- อาหาร เมนู
- พนักงานเสิร์ฟ
- พ่อครัว

1. Functionality
	- ร้านต้องเสิร์ฟอาหารถูกโต๊ะ ถูกคน และถูกต้องตามที่ลูกค้าสั่ง 
	- เมื่อมีการ custom menu เช่น ไม่ใส่ผัก ก็ต้องไม่ใส่ผัก
	- อาหารต้องตรงปก หรือใกล้เคียงกับภาพในเมนูที่สุด
	- บรรกาศในร้านอาหารดูดี ปลอดภัย
2. Reliability
	- มีการลงประวัติการสั่งอาหารของลูกค้าไว้ในระบบ ถ้ามีการเสิร์ฟอาหารผิดพลาดสามารถเสิร์ฟใหม่ได้ทันที
	- มีระบบคิวในการทำอาหาร และสามารถแทรกคิวได้กรณีทำอาหารผิด
	- มีอุปกรณ์ จาน ช้อน ส้อม เครื่องปรุง ไว้ให้ลูกค้า
	- มีการสำรองวัตถุดิบ เผื่อไว้กรณีที่เป็นช่วงเทศกาล หรือมีลูกค้าเข้ามาเยอะกว่าปกติ
	- มีที่นั่งให้ลูกค้ารอคิว หากร้านเต็ม
3. Usability
	- มีเครื่องปรุง เครื่องเคียง อุปกรณ์ช้อนส้อม ต้องเตรียมพร้อมไว้ให้ลูกค้าเสมอ
	- พนักงานประจำจำนวนเพียงพอ และยืนในจุดที่ มองเห็นครอบคลุมพื้นที่ เพื่อให้บริการได้ทั่วถึง กรณีลูกค้าจะเรียกสั่งอาหาร หรือขอความช่วยเหลือ
	- มีเมนูแนะนำ
	- เทรนพนักงานเสิร์ฟในการให้คำแนะนำเมนูกับลูกค้า
4. Efficiency
	- มีพ่อครัว ในจำนวนที่เหมาะสมกับปริมาณลูกค้า ไม่เยอะหรือน้อยเกินไป ที่จะทำให้ลูกค้าไม่รอนาน
	- มีพนักงานเสิร์ฟในจำนวนที่เหมาะสมกับพื้นที่ และปริมาณลูกค้า
	- มีการเทรนพนักงานเสิร์ฟเรื่องความรวดเร็วในการเก็บโต๊ะ หรือให้บริการลูกค้า
	- มีการคำนวน stock วัตถุดิบที่ใช้ทำอาหาร และ predict สั่งของมาให้พอดีกับปริมาณลูกค้า
5. Maintainability
	- มีสูตร และเทคนิคการทำอาหารคงที่ มีการบันทึก เปลี่ยนแปลงได้ แต่ต้องเทรนพ่อครัวอยู่เสมอ เมื่อเปลี่ยนพ่อครัวก็สามารถทำให้อาหารรสชาติเดิมได้
	- มีกฎกติกาของพนักงานเสิร์ฟ มีการเทรนเป็นประจำ เพื่อให้พนักงานใหม่และเก่าให้บริการตามมาตรฐานของร้าน
6. Portability (ถ้าต้องย้ายร้าน หรือขยายเฟรนไชส์)
	- เลือกอุปกรณ์ครัว และโต๊ะ เก้าอี้ ที่สามารถเคลื่อนย้าย จัดใหม่หรือเปลี่ยนที่ได้และยังคงรักษาคุณภาพ บรรยากาศของร้านได้ดี
	- อุปกรณ์ครัว และโต๊ะ เก้าอี้ ต้องซื้อจากร้านที่มีความน่าเชื่อถือ ที่จะสามารถผลิตให้เราได้เมื่อเราต้องการ
	- แหล่งซื้อวัตถุดิบต้องสามารถหาที่อื่นที่แทนได้