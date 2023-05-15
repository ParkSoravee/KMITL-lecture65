# Hardware spec

Hardware ที่เขาขายกันในตลาด

>[!Question] ใช้คอมประกอบเป็น server ได้ไหม?
>เปิด 24ชม. 7 วัน 72สัปดาห์ ไม่ได้

Server จะออกแบบมาให้ บำรุงรักษา เปลี่ยนได้
โดยไม่ต้องปิดเครื่อง (business ต้องการ continuity) เครื่องปิด = เงินหาย

ex. server cpu
PA-RISC
DELL - ALPHA
SPARC

แต่ก่อน server ต้องใช้อุปกรณ์ภายในของเขา เลยเกิด -> PC-base server
Dell และอีกหลายเจ้า - เลือกได้ว่าจะเอา spec ยังไง รอ 3-5 วันทำการ จะส่งคอมให้

ลักษณะ Server
- Tower
- Rack

เลือกตู้ Rack
- เอากี่ u สูงเท่าไร
- ลึกเท่าไร

เครื่อง server
HW ถ้ามองแล้วแพงมาก เทียบกับราคา pc ปกติ
1 Year Warranty สำคัญ มี onsite service (อย่ามองข้ามการเอาเครื่องไปซ่อม)

### Management and Console

![[Pasted image 20230202103152.png]]
iDRAC9 (ชื่อของ DELL) - management module (MMU)
chip set พิเศษที่ติดไว้กับ mainboard
คอยสอดส่อง cpu, ram, network, storage โดยไม่ได้รบกวน OS หลัก
ต้องเชื่อมผ่าน network only

Management Port or
Control port or
Machine management unit or
Console port
config ออกแบบพวกนี้ ยังไงให้ security (ไม่ออกสอบ ให้หาเพิ่มเติมวิชาชีพ)

---

ครั้งหน้า OS