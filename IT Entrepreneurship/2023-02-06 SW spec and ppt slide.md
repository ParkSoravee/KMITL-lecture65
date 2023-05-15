## เฉลยการบ้าน

- Functional
	- ใช้งานยังไง
	- ทำอะไรได้
- Reliability
	- เกิดปัญหา ทำงานต่อไป
	- ex. ไฟไหม้ครัว พ่อครัวขาด 
- Usability
	- ใช้ง่าย GUI
	- ร้านสวย
	- เมนูอ่านง่าย
	- ติดแอร์ส่วนกิน
- Eff (Performance)
	- ประสิทธิภาพ ที่ลงทุนไป
	- ex. ทำอาหารได้มีประสิทธิภาพ อาหารอร่อย ติดแอร์ครัว
- Maintainability
	- ปรับเปลี่ยน เพิ่มเมนู
	- ex. 
- Portability
	- ย้ายที่ขาย เปลี่ยนสัญญา

# Requirement specification

เอกสารที่ user บอกว่าอยากได้อะไร
business analysys คุยกับลูกค้า

เมื่อก่อน waterfall model

Engr. สร้างสิ่งซ้ำๆ เดิมๆ ให้ได้คุณภาพประสิทธิภาพเหมือนเดิม
เปรียบเป็น menu หรือ สูตรอาหาร ที่บอกว่าต้องใส่อะไรบ้าง
-> Development process

## Goal of software engineering

- Quicker -> Schedule
- Better -> Quality
- Cheaper -> Cost

QCD
- Quality (คุมยากสุด)
- Cost (คุมง่ายสุด)
- Delivery

## CMM

- American Standard for development process
- Capability Maturity Model -> จาก Carnegie melon University
บอกว่า ...

Lv1: ทั้งบริษัท ไม่มี development ไม่มี design, อยู่ในหัวหมด
(บ. ขนาดเล็ก) co-founder ทำทุกอย่าง

Lv2: บ. เขียน development process บาง project เป็นภาษาอังกฤษ

Lv3: เขียน development ทุกโปรเจค

Lv4: Engr ในโปรเจคมีความสามารถวัดประสิทธิภาพของ process ได้

Lv5: คนของ บ guild proj ให้ทำงานได้ดีกว่าเดิมได้

### CMM level in U.S. and India

CMM in the real world

CMM พูดเฉพาะ process
แต่ไม่ได้บอกว่า players good or not

>CCM Level 5 อย่าเพิ่งเชื่อ ต้องดูก่อนงาน

ต่างกับญี่ปุ่น
- เปรียบร้านอาหาร CMM lv5 ละเอียดยิบ แต่ใช้คนที่ไม่เคยทำอาหาร ดีมั้ย? ไม่
- ร้าน lv1 ไม่มีสูตรอาหาร แต่มีเชฟเก่ง สูตรอยู่ในหัว -> อร่อย
เหตุผลว่าทำไมร้าน local อร่อย

>Process ไม่ใช่ทุกสิ่งทุกอย่าง ตั้งต้นจากคนก่อน


ทำไม project fail
	req ไม่เคยนิ่ง วิธีแก้คือ
- แยก phase
- เอา req ที่นิ่งทำก่อน

3 อย่างที่ต้องดู
- priority : เราไม่สามารถสร้าง sw ตรงทั้งหมดลูกค้าได้ เลือกอัน must be ก่อน แล้ว should be แล้วค่อย desire
	- ex. reg : 
		- must be login, เด็กเลือกวิชาได้ | 
		- should be : ขึ้นตาราง
		- desired : ขึ้นค่าเฉลี่ย predict ให้จากเดือนที่แล้ว

20% modules = 80% functions

## ต้นทุนพัฒนาระบบ

8% req
5% design
7% coding
5% debugging
7% testing
60% Maintenance (phase ถัดไปด้วย)

**types of maintenance**
20% bug fix
60% เพิ่ม feature
20% adaptive อัพเกรด ios

## ความยากของการทำ req spec
- ambiguous (doubt)
- incomplete มันยาก
- contradictory มันขัดกัน
- difficalt to understand ไม่เข้าใจ business flow/logic ของเขา

ex. 2 คนแผนกเดียวกัน business flow ต่างกัน

>SA, PM ต้องเข้าใจ business flow, business language

### ออกแบบ เขียน req เกมเป่ายิงฉุบ
เขียน req spec ของ sw ในการเล่น เป่ายิ้งฉุบ
เราเขียนระบบเกมเป่ายิ้งฉุบ
ทีมงาน dev ไม่เคยเล่นเกมนี้
สมมติเราเป็น SA
req spec ส่งให้ทีมงาน dev

- เกมนี้เล่นยังไง
- นิยาม ก้อนหิน กระดาษ กรรไกร

sw engr.

CASE = Computer Aid Software Engineering tool
tool ที่ทำให้ sw engr ง่ายขึ้น

software metric วัดได้
"If u can't mesure, you can't control"

วัดความซับซ้อน sw -> Cyclometic number
แทนสมการ

Software Metric วิธีการวัดบางสิ่งบางอย่างของ sw (ประสิทธิภาพ, ความซับซ้อน,... เพื่อควบคุม quality)
- Metric before the fact : ทำก่อน coding
- ... after

## Group exercise

#todo/IT-entre 
- [ ] group exercise สามเหลี่ยม ส่งเวลาเดิม

เขียน req spec ของ sw นี้มา ในกระดาษ / ipad แล้วอัพไฟล์ส่ง
ป้อนความยาวด้าน 3 ด้าน แล้วได้ผลลัพท์ว่าเป็น 3 เหลี่ยมอะไร
- ด้านไม่เท่า
- หน้าจั่ว
- ด้านเท่า
- มุมฉาก

**เขียน**
- sw spec
- ใช้เวลาเท่าไร
- ใช้คนกี่คน
- วัดผลลัพท์ยังไง
ขอแบบ detail of req spec


# Making PowerPoint Slides

guildline การทำ slide มีประเด็นไหนบ้างที่ต้อง concern

## Outline

- หน้า 1-2 บอกว่าเนื้อหาทั้งหมดมีประเด็นไหนบ้าง detail คืออะไร สร้างภาพใหญ่ก่อน
- ไล่ order ตามที่เขียนด้วย (อย่าให้ เอ๊ะ ในใจคนฟัง)
- ใส่เฉพาะ main point ของ slide

## Slide structure

- 1-2 slide ต่อนาที
- เขียนเฉพาะประเด็น keyword ใส่มา 4-5 bullet ต่อสไลด์
- ไม่เอาคำยาวๆ
- เป็นไปได้ โชว์ทีละ point ขึ้นมา
- ทำให้ผู้ฟังมีสมาธิกับการฟัง
- (แต่ดูสไตล์ด้วย บางคนชอบอ่านรวมๆ หลาย bullet)

- animation อย่าใช้ที่กวนสายตา ใช้แบบเดิมๆ อย่าเปลี่ยนบ่อย


## Font

- 18 อย่างน้อย ใช้ font มาตรฐาน

## Color

- ใช้สีที่มันเหมาะกับ backgroud
- ใส่สีให้คำเน้น นานๆ ใช้ที

## Background

- ใช้แบบเดิมๆ ซ้ำๆ
- เนื้อหาสำคัญ

## Graphs

- ใช้ graph อธิบาย แทน data เป็น table ได้
- ใส่ title ด้วย 

## Spelling and grammar

- ตรวจสอบเสมอ

## Conclusion

- สรุป ปิดประเด็น
- มนุษย์ จำประเด็นสุดท้ายได้
- ย้ำเตือนว่าเราคุยประเด็นไหนบ้าง
- อนาคตทำอะไรต่อ

- จบด้วย Q&A
- invite ให้เขาถามเรา

## Other

- เลขหน้า
- แถบล่าง
- ดูว่า present ให้ใคร


