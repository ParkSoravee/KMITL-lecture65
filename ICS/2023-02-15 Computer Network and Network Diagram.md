Online class

การประเมิน sec ต้องดู Network Diagram เป็น
sysAds เช่นกัน

## ทวน

![[Pasted image 20230310194253.png|600]]
![[Pasted image 20230310194237.png|500]]
ตอนแรกต้องดูก่อนว่า nw ID อันเดียวกันไหม
nw ID ได้จากการ and (&) ชุดแรก (ที่ A:)

ex. ping

Q: ถ้าเครื่อง A, B อยู่เครือข่ายเดียวกัน แล้ว A ping ไปยัง B เกิดการส่งข้อมูลขึ้นกี่ครั้ง ใช้ protocol อะไรบ้าง
Ans:
- จะคำนวนก่อนว่าอยู่ nw เดียวกันมั้ย
A ต้องมี 
IP : src, dst มี
MAC : SMAC มี, DMAC ไม่มี
ดังน้ันหา DMAC ก่อน -> ARP REQ ไปหาทั้ง nw
B ได้รับ -> ARP Reply -> A
A ส่ง ICMP Echo Request -> B
B ส่ง ICMP Echo Reply -> A
(เกิดขึ้นแค่ครั้งแรก ถ้าไม่รู้ MAC)
ครั้งต่อไป : MAC Address Buffer จะเก็บไว้ว่า IP ไหนมี MAC อะไร (มีเวลา expire)
`arp -a`

![[Pasted image 20230310195755.png|500]]

ตอบ 4 ครั้ง ARP 2, ICMP 2


Q: ในกรณีที่ A,B อยู่เครือข่ายติดกัน (มี router กั้น 1 ตัว) แล้ว A ping ไป B ไปกลับ 1 ครั้ง เกิดการส่งข้อมูลขึ้นกี่ครั้ง ใช้ protocol อะไรบ้าง
Ans:

L3: IP A -> IP B
L2: MAC A -> MAC Router

know IP Router(by static or dynamic (DHCP) when turn on A) but MAC Router ??
A: ARP req -> broadcast
R: ARP reply
A: ICMP Echo req
R: ส่งต่อไป B IPเดิม แต่ ==MAC เปลี่ยน== but dont know MAC B ?? (L3 router ไม่แตะ) ชำแหละ L2 ใหม่
B: ICMP Echo reply
R: ส่งต่อไป A เลย (ไม่ทำ ARP ละ)

ไปลองทำดู
![[Pasted image 20230311103332.png]]

## Network Diagram

Q: ถ้าไม่มี network diagram ผู้ดูแลระบบจะไม่สามารถดูแลระบบได้ จริงหรือไม่?
A: ทำได้ถ้ามัน simple

Q: Nw Diagram
A: ไม่หมด ต้องมีอย่างน้อย 2-3 diagram
1. Physical Newwork Diagram -> สายต่ออะไรบ้าง sw เชื่อม port ไหนๆ, VLAN, มองสิ่งที่ตาเห็น
	![[Pasted image 20230311103651.png|200]]
2. Logical Newwork Diagram -> nw ต่อกันยังไง routing มอง L3, Routing
	![[Pasted image 20230311103740.png|300]]
3. Service Network Diagram -> เอา logical มาเขียนต่อว่า service ไหนอยู่ตรงไหน

>วันนี้ดูแค่ 1,2

>[!Question] nw diagram ควรมีรายละเอียดของอะไรบ้าง

![[Pasted image 20230311104232.png|500]]

### Logical Network Diagram (L3+)

![[Pasted image 20230311104529.png|500]]

นิยาม เครือข่าย 1 Network 
1. กลุ่มของอุปกรณ์ที่มี nw id เดียวกัน
2. Broadcast domain ชุดเดียวกัน

logical เขียนวงกลมไว้เลยว่าอยู่ nw เดียวกัน

แต่ถ้าในมุม physical คอม 100เครือง ไม่สามารถต่อกับ sw ตัวเดียวได้
![[Pasted image 20230311105006.png|500]]

>sw ปกติ มี UDP 32 port, fiber 2 port

sever ปกติไม่ต่อ router โดยตรง จะผ่าน distribute sw

### Site Connection Diagram

![[Pasted image 20230311105032.png|500]]

ส่วนมากมีใน
- โรงงาน
- ธนาคาร

### Switch Network Diagram (L2-)
switch ต่อกันยังไง , VLAN

![[Pasted image 20230311105348.png|500]]

#### VLAN

สมมุติว่าใน บ.
![[Pasted image 20230311105848.png|500]]
แบบนี้ง่าย

แต่ถ้าแบ่งทีม อยากคง nw diagram เดิม
without VLAN
![[Pasted image 20230311110025.png|500]]
ลำบากมากก

ใช้ VLAN -> ใน sw กำหนด VLAN ให้มัน ว่า port ไหนเป็น VLAN เบอร์ไหน
ใน frame ของ traffic ที่วิ่ง 802.1Q แปะ vlan no. ใน packet ของเส้นที่วิ่งไป R
![[Pasted image 20230311110951.png|500]]
Router สร้าง Virtual interface ใน diagram เป็น 3 nw เหมือนเดิม (ซ้าย)

### Device Connection Diagram

![[Pasted image 20230311105615.png|600]]

ต้องมี excel sheet อีกอันบอกว่า
src. device | port | dst. device | port

**ตัวอย่าง network diagram หน่วยงานอื่นๆ** (physical)
![[Pasted image 20230311113021.png|600]]
จุดแดง คือตู้ node หลักของตึก
เส้นแดงคือ fiber

ex. physical
![[Pasted image 20230311113111.png|600]]
![[Pasted image 20230311113216.png|600]]
mark สี
![[Pasted image 20230311113240.png|600]]
เป็น physical ก็จริง แต่มีบอกว่าอยู่ network ไหน

ด่านทางหลวง
![[Pasted image 20230311113542.png]]

การทางพิเศษ
![[Pasted image 20230311113623.png]]

## โจทย์

ให้นักศึกษาใช้อุปกรณ์ที่ให้ทั้งหมด สร้าง Network Diagram ขององค์กรนี้
![[Pasted image 20230311113909.png|500]]
![[Pasted image 20230311114027.png|500]]
![[Pasted image 20230311114043.png|500]]
![[Pasted image 20230311114125.png|500]]
![[Pasted image 20230311114144.png|400]]

วาด A,B และ CD รวมกัน

physical อาคาร
logical วาด nw เป็นวง

แนะนำเขียน logical ก่อน

>ระวัง sw มี 32 port (ถ้าเกิน ต้องใช้ต่อกัน)

ex. แนะนำวาด logical ก่อน
![[Pasted image 20230311115311.png]]


