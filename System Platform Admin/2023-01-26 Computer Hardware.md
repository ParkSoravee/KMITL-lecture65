- Hardware : ปูพื้นฐาน Computer/Server Componant 
- Environment : สภาพแวดล้อมที่ HW จะรันอยู่ตลอด 24hr. 7day/week

ซื้อคอมประกอบ
![[Pasted image 20230126093840.png]]

- RAM สำหรับ server พิเศษมี mode ECC : Error Correction Code
	ข้อมูลเก็บใน Flipflop สัญญาณไม่เสถียร Bit อาจจะเปลี่ยน เลยจำเป็นต้องมีวงจรคำนวนและกู้คืนข้อผิดพลาด ในแผงของ RAM เลย -> ECC RAM
- CPU ใน Server 
- GPU มี general purpose, special purpose เช่น การ์ดเร่งการเข้าและถอดรหัสลับ
- PSU : AC->DC

>[!Tip] สาเหตุที่ sysAdmin ต้องสนใจสเปค
>การอัพเกรดได้ หรือไม่ได้

>[!Question] Tesla(DC) vs Edison(AC) ??

ENV

![[Pasted image 20230126111256.png | 500]]
- Position
	- ไฟพอมั้ย
	- แดด
	- ภัยพิบัติ
- Security
	- Physical Security : ทุบประตู
	- .
- Electricity
	- มาจาก Position เลือกแหล่งที่มีคุณภาพไฟฟ้าดี
	- ไฟดับ ต้องมี UPS
	- หรือลงทุน power generator (เติมน้ำมันปั่นไดนาโม)
- HVAC : Heating, Ventilation, and Air Conditioning
	- ปรับอุณหภูมิ, ความชื้น, ฝุ่นควันอนุภาค
	- ไฟฟ้าสถิต เกิดจาก ความชื้นสัมพัทธ์ต่ำ (อุณหภูมิต่ำ)
		- ถ้าความชื้นสัมพัทธ์สูง สนิม 
	- บางครั้งไม่ใช้ HVAC ทั้งห้อง แต่เป็น HVAC ต่อท่อเข้าตู้ ไม่ได้ทำทั้งห้องให้เย็น (แต่ก็ไม่ร้อนเกินไป)
- Protection Alarm
	- ห้อง server นอกจาก thermometer (temperature), hygrometer (ความชื้น), water meter (ติดที่พื้น), fire alarm system เตือนไฟไหม้, smoke detector, heat detector, ยามเดินดูบ่อยๆ
	- ระบบดับเพลิง แต่ก็มีปัญหาไฟไหม้ ไม่ได้มีควันทุกครั้ง (แอลกอฮอล์) ไม่เห็นเปลวไฟ
	- กล่องโฟม กล่องกระดาษ พอติดตั้งเสร็จเอาออกไปให้หมด
	- Detection ไม่พอ ต้อง take action ให้ทันท่วงทีด้วย มีระบบ auto บางอย่าง มีสารดับเพลิงหลายรูปแบบ (ไว้ดับเพลิงตามประเภทการใช้งาน)
	- SCB Incident
		- มีเหตุการณ์ที่ห้อง data center ซ่อมบำรุงผิดพลาด ทำให้เกิดอุบัติเหตุคนตาย
		- ไม่ได้เกิดไฟไหม้ มีฝุ่นแกะ แต่มีก๊าซไล่ Oxygen ออกจากห้อง data center เป็นอุบัติเหตุ
		- ไม่ว่าจะไปไหน หา fire exit เสมอ

---

