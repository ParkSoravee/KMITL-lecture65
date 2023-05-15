
>[!Info] Class เรียนนี้ ทำเว็บง่ายๆ ให้ back ไปถึงข้อมูลให้ front render และ unit test backend/frontend และไป analyst ใน Jenkin -> SonarQube แล้วไป integrate automate test
>- Front: react
>- Back: java(spring-boot)
>- QA : automate - robot framework (python)

พี่เอ - tech lead
พี่แบงค์ - backend dev / fullstack
พี่มิ้น - frontend
พี่กานต์ - automate tester

Quality Assurance - รับประกันว่าสิ่งนั้น มันได้คุณภาพจริงๆ

QA / Tester ความหมายใกล้เคียงกัน (ในโลกจริง role ไม่ต่างกันในบางที่)
ทดสอบระบบ และหาจุดบกพร่อง คอยดูว่า app ทำงานได้ถูกต้อง มีประสิทธิภาพหรือเปล่า

**ความแตกต่าง**
**QA** - ทำหน้าที่ test ระบบ หาบัค หาจุดบกพร่อง unexpected case, bypass, รหัสง่าย ก็ขึ้นกับชั่วโมงบิน ประสบการณ์
**Tester** - คนวาง strategy ทำยังไงให้ case พวกนี้ไม่เกิด

![[Pasted image 20230124091458.png]]

- Setting the check point - ฉันจะทำอะไรมันบ้าง ex. ใส่ตัวเลข, ใส่ตัวอักษร
- Measure Change Impact สิ่งที่เราจะทำ(test) มันสร้างผลกระทบอะไรบ้าง ทำให้ระบบไหนพังหรือเปล่า
- Having Multiple Testing Strategy การ test แบ่งได้หลาย strategy -> ex. fundimental, optional หรือทำ automate testing
- * Maintaining Records and Reports : ทำ record, report สิ่งหรือ case ที่เกิดขึ้นแล้ว ไม่ควรเกิดขึ้นอีก ถ้าเกิดต้องไปดู sw แล้ว
- Managing Good Relations : tester, QA ต้อง deal กับลูกค้า, กับ dev ด้วย ให้รู้สึกไม่กดดันเกินไป หรือ ต่อรองลูกค้า (ex. อยากได้งานไวขึ้น คุณยอมรับความเสี่ยงตรงนี้ได้ไหม)
- SQA Management Plan : Software Quality Assurance ต้องนั่ง plan ระยะยาว จะทำยังไงต่อ รูปแบบไหน strategy ยังไง เป็นตัวมาครอบตัวอื่น

>[!Note] Software Crisis
>Crisis -> ปรากฏการณ์ / วิกฤตการณ์ (แง่ลบ) -> sw ที่สร้างมา ไม่ได้มี quality (สมัยก่อน)
>
>ทำ sw ต้องใช้ cost & time
>สิ่งที่ขาดไม่ได้คือ quality

>[!Important] UI TESTS ทุกอย่าง element, pixel ต้องตรง กับที่ทำไว้

![[Pasted image 20230124093700.png|500]]

More integration and slower and expensive
- UI TESTS
- INTEGRATION TESTS
- UNIT TESTS
More isolation and faster and cheaper

>[!Question] ทำไงให้ dev ทำ unit test
>ขึ้นอยู่กับ culture บ. ด้วย
>มีแนวคิด TDD: Test Driving Development : เขียน test ก่อน แล้วไป dev
>DEV ต้องทำ unit test

>[!Tip] จะรู้ได้ไงว่า test ครบหรือเปล่า
>Technical Leads & จะมี tool: SonarQube ที่มาช่วย detection ว่า test ครบหรือเปล่า แต่คนที่เขียน rule คือคน ว่า test เขียนแบบนี้ผ่านไหม อยู่ที่ประสบการณ์ในการเขียน rule (แต่มี standard template อยู่)

## QA is important as same as Developer

QA ต้องรู้เบื้องต้น หรือ อนาคตอาจต้องเจอ
- ระบบล่ม
- ทำ rate limit
- ระบบมีหลาย micro-service
- Dev แก้ feature ซื้อของ แต่ดันเจอปัญหากับ feature เลือกสินค้า

>[!Tip] QA vs Tester
>QA หา bug
>Tester วางแพลน

>[!Info] Micro-service เป็นดาบสองคม ถ้าแต่ละตัวเชื่อมต่อกันหมด เสีย time request คนที่รู้ business เป็นคนวางแผน

## ทำไมงาน QA ถึงน่าสนใจ

- เจอการทดสอบระบบ หลากหลาย Tech stack
- Automation test มีให้ทำเยอะ
- Technical dept และ Bug มีมาก
- ได้เรียนรู้โลกผ่าน business req และ dev process
	- ต้องเข้าใจ req ลูกค้า เนื้องาน ยิ่งกว่า dev
	- ลูกค้า จะถาม tester ไม่ถาม dev, เทสถึงไหนแล้ว
- ต้องตรวจงาน dev ก่อนไปถึงลูกค้า

### Roles of Tester

- Manual Tester : ใช้มือกด จนกว่าจะผ่าน
- Automation Tester : เขียน bot มาเทสซ้ำๆ หลายๆ รอบ
- Penetester : security

>[!Tip] Automate test
>step 0: delete clear data ออกก่อน

>[!Tip] test web ง่ายๆ ใช้ extension: Selenium IDE

---

>[!Note] Agile
>- fast feedback
>- transparent ทุกคนทำงานเห็นภาพเดียวกัน

ชื่อ test ตั้งชื่อให้ คนอื่นใครก็ตามที่มาอ่านเทสเราแล้วเข้าใจ โดยที่ไม่ต้องดูโค้ด
3 keyword จากหลังไปหน้า
- given สิ่งที่ให้ไป
- when เมื่อไร
- then ให้อะไรออกมา

ex. shoud_return_information_dto_when_call_get_fund_information_given_correlation_id_and_fund_code_request_body


>[!Note]
>Enterprise ส่วนมาก นิยมใช้ backend -> Java(spring-boot), C#

>[!Info] Pair Programming
>คน drive(เขียนโค้ด) กับ follow(นั่งข้างๆ เข้าใจว่า code ทำอะไร)
>มีสลับตำแหน่งกัน ตลอดๆ
>(ต่างกับ Solo programming)

---

next lesson: workflow ของการใช้ git ในการทำงานจริง

>git-cherry-pick ใช้บ่อยทำงานจริง

#todo/testing
- [ ] ลง react, spring boot ให้เรียบร้อย

