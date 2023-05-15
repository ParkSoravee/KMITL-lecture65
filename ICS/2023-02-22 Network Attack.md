
# Network Attack

ARP : หา MAC

Network attack อาศัย ip protocol เป็นการส่งข้อมูลไป สร้าง package ที่ผิดปกติ

- ภัยคุกคาม (Threats)
- ช่องโหว่ (Vulnerability) : คุณสมบัตินึงของระบบ ไม่มีใน spec คาดเดาไม่ได้จนกว่าจะเจอ
- การอาศัยช่องโหว่เพื่อโจมตีระบบ (Exploit) : ระบบต้องมีช่องโหว่ก่อน

ในเชิง system และ network

>[!Tip] ทวน 3-way-handshake
>ส่ง syn
>syn/ack กลับมาถ้า port เปิด
>sys ถ้า port ปิด

hacker ส่ง syn หาทุก port ว่าเปิดไหม อาศัยช่องโหว่ของ TCP State Machine

![[IMG_4142.jpeg|500]]

![[Pasted image 20230222101632.png|400]]

- Malware : ศูนย์เสียทรัพยากร ข้อมูล ให้มัน
- Rootkits : buffer oberflow ในการเปลี่ยนสิทธิ์ตัวเองให้เป็น root admin
- Spam : การส่ง email จำนวนเยอะๆ
- Worm : อาศัย nw เน้นกระจายตัว ไม่เน้นทำลาย
- Trojan : ไว้ใช้หลอก ex.โปรแกรมวาดรูปฟรี มีการ embed code เช่น key logger หรือดูว่ามี cookie ไปที่ไหนบ้าง
- Spyware : คล้าย trojan แต่ไม่มีหน้ากาก เป็น spyware เลย embed ไปใน sw ตัวอื่น ซ่อนตัวอยู่ใน comp sw อื่นๆ
- Ransomware : เรียกค่าไถ่ข้อมูล เข้ารหัสข้อมูล (ทั่วไปใช้ web browser บอกว่าต้องทำไง) น้อยครั้งที่ทำตามแล้วจะได้ key ในการกู้คืน
- Adware : ad popup มา เป็น sw ที่ใช้ฟรี เป็น adware หมดเลย ex. youtube ธรรมดา

Q: จะป้องกัน แก้ไข malware ยังไง??
- anti virus 
**กระบวนการ**
แบบ 1 **signature base** 
-> หา pattern ความผิดปกตินอก system เก็บไว้ในฐานข้อมูลของ anti virus
แต่ ! ไม่มีทางรู้ถ้า virus เกิดใหม่เมื่อวาน
เพราะมีกระบวนการถ้าเจอ virus ส่งไปแกะเป็น virus signature แล้วอัพเดทให้คนทั่วโลก (ถ้าจ่ายตังจะได้อัพเดทไว)

แบบ 2 **Anomally/Profile/Role Base**
-> ?
-> Firewall


ทั้ง 2 แบบ 
- ไม่มีทางได้ขอบของ system ได้ครบ
- นอก system ก็ไม่ครบ
มี IDS ถ้าอยู่นอก IDS แต่มันปกติ -> เป็น false positive
อยู่นอก system แต่อยู่ใน IDS -> false negative

>[!warning] Anti virus มีโอกาส Error แน่นอน
>จ่ายตังให้อัพเกรด signature ไวๆ

## Sniffer
-> โปรแกรมดักจับข้อมูลที่วิ่งมาในสาย

![[Pasted image 20230222103711.png|600]]

เงื่อนไขที่การ์ดจะรับ
- des mac เป็นของมัน
- เป็น broadcast
ถึงจะส่งไป layer ถัดไป

แต่ถ้าเปิด mode สำส่อน(...)
จะทำให้เราได้ข้อมูลของ nw แน่นอน ได้ข้อมูล broadcast ทั้งหมด

แต่ปัจจุบัน ถ้าใช้ hub ที่กระจายให้เครื่องอื่น sniffer ไว้ที่ hub จะได้ข้อมูลทั้งหมด
แต่ถ้า switch จะมี table จะไม่ได้ข้อมูลเลย
แต่ hacker ไป export กระบวนการนึงของ switch เพราะ switch เก็บได้จำกัด มันจะเปลี่ยนตัวเองเป็น hub -> admin ทำไง??

Q: จะป้องกัน / แก้ไข การดักจับข้อมูลต่างๆ ได้อย่างไร
- Confidentaility * เข้ารหัสข้อมูลก่อนรับ ส่ง ex. ssl, vpn
- Integrity

ใช้ sw กลุ่ม secure ex. secure shell (putty) เวลาเชื่อมไป server
web -> SSL
remote desktop -> VPN sw

## Global Attack Map
![[Pasted image 20230222104826.png|600]]

บอกว่ามีการส่ง package จากไหน ไปโจมตีจุดไหน
IP map กับ GPS แล้วทำแผนภาพ

อ่านข้อมูลในสาย แล้วมาแสดงผล
![[Pasted image 20230222105216.png|600]]

## DoS

![[Pasted image 20230222110537.png|200]]

- Smurf attack ขยายจำนวน package??
- Ping Of Death : set ping package ใหญ่ๆ
- Ping Flood : เน้นจำนวน
- Teardrop ส่ง package ไป ประกอบปลายทางไม่ได้
- Fraggle

![[Pasted image 20230222110747.png|500]]

Q: จะป้องกัน / แก้ไข DoS ยังไง?
- Firewall
- Load balance
- Proxy : re-locate DoS ให้ drop หรือไปที่อื่น
ส่วนใหญ่เว็บดังๆ จะโดนเยอะ

## N-Map
อันตรายสุดด
![[Pasted image 20230222110900.png|500]]
exploit nw protocol เพื่อหา information ของระบบเครือข่าย

มี mode ต่างๆ เอาไว้หลบ firewall
![[Pasted image 20230222111019.png|500]]
แต่ละแบบทำงานยังไง?
ปกติ ส่ง syn ไปสแกน แต่ firewall มีการกำหนดโควต้า หรือปิดไม่ให้ syn ภายนอกส่งเข้าไปในเครือข่าย

- TCP Connection scan ทำ 3 way-handshake ได้ banner ออกมา(เว็บชื่ออะไร)
	- ข้อเสียคือต้องเปิดเผยตัว ip src
- Fin scan: set flag fin ไปด้วย ให้หลุด firewall ทำเหมือนเครือข่ายภายในทำ 3-way hs แล้วจะส่ง info จากภายนอก แล้วภายนอกส่ง fin กลับมา
	- port เปิด จะส่ง fin/ack กลับ
	- port ปิด จะส่ง reset กลับ
	- ไม่รู้แบนเนอร์แต่รู้ว่า port ไหนเปิด

Q: ป้องกัน
- Firewall

## Exploit

![[Pasted image 20230222112923.png|600]]
buffer overflow

เปลี่ยนสิทธิ์ได้
รันโค้ดจาก id=500 -> id=0 (root)
โยน buffer ไปชุดนึง พร้อมโค้ดเพื่อเปลี่ยนสิทธิ์ตัวเอง

แต่ต้องเข้าใจโปรแกรมนั้นพอสมควร ไม่ก็เอา tool มาใช้
แต่โค้ดได้โหลดมายังทำงานไม่ได้ ต้องแก้บางอย่าง (community ป้องกัน)

Q: แก้
- upgrade software

## TCP/IP Hijacking

Connection id
TCP -> seq/ack no.
แทรก data เข้าไปใน stream ของ TCP/IP ได้

![[Pasted image 20230222113338.png|500]]

web  -> HTTP sesion ID หาจาก sniffer
![[Pasted image 20230222113354.png|500]]

personal web proxy
หยุดไม่ให้ส่งไป server เราแก้ไขก่อน แล้วค่อยกดส่ง

>Web เก็บข้อมูล มี 4 แบบ
>- URL *ทำ session hijack ง่าย แต่ไม่ปลอดภัย* แต่แก้ไขให้กำหนดเวลา expire ได้ (กันมาเปิดทีหลัง) JS keep alive
>- Cookie
>- var in webpage
>- var in server *most secure*

Q: ป้องกัน แก้ไข session hijack ยังไง
- Set expire time (1-2 min)

## Rogue Access Point

![[Pasted image 20230222114258.png|500]]
access point โยน beacon frame ออกมาบอก user ตลอดเวลา
ถ้า lock เข้าไปไม่ได้
แต่ถ้าเครื่องเจอ access point ที่สัญญาณแรง ความเข้มสูงสุด จะเลือกไปเกาะก่อน

Rogue Access Point มาตั้ง เป็น open ไม่ต้องใส่รหัส ต่อ internet ให้ด้วย
- สัญญาณแรงมาก
- เปิด open
- set proxy เชื่อมเข้ามาจะ set เข้า proxy ก่อน

>personal hostpot คนอื่นเกาะมาไม่ใช้รหัส อันตราย

วิธีแก้
ตั้ง device ว่าจะ prefer wifi ตัวไหน auto ไว้

## Summary

Exploit -> การหาประโยชน์จากสิ่งที่มีอยู่
ex. TCP 3way-handshake ดีมาก แต่ทำให้ FIN Scan ได้

>ดูว่าการโจมตีแต่ละแบบ ใช้กลไกอะไรในการ exploit

CIA, CIA, DIR

Access point แก้ได้ด้วย authen
Sniffer แก้ด้วย confidential
Hijack แก้ด้วย integrity gen hash ชื่อกับ score ส่งไปด้วย ให้ไปเทียบกับ algo เดิมใน server ถ้าเหมือนกัน = match

>Exploit ได้หมด แต่เอา security concept ไปจับ

---

