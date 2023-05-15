online class
# Firewall and Policy 

firewall เป็น hw / sw
track การทำงานที่ชั้น nw layer or other
firewall บางตัวทำงานได้ถึง app layer

เป็นตัวคัดกรองว่าข้อมูล ปกติ/ผิดปกติ
func. prevent -> detect -> respond

detect จาก pattern, content, 
response -> drop packet

## ทวน Network

Datalink Layer:
	IEEE 802.3 : Src MAC address, dst MAC address
Network Layer :
	IP : src IP, dst IP, ID, offset, Fragment Flag
	ICMP : Type, Code
Transport Layer:
	TCP : Src Port, Dst Port, Seq number, Ack number, windows size, Flag (tcp state machine) ex. syn,ack,reset,fin
	UDP : Src Port, Dst Port
Application Layer :
	HTTP

>คนที่มา config firewall ต้องเข้าใจ header ต่างๆ ของแต่ละ protocol

Q: การบุกรุก การโจมตี ทางเครือข่ายมีอะไรบ้าง มีลักษณะ header field ยังไงบ้าง

![[Pasted image 20230301101915.png]]
เขียนแบบนี้ได้ set firewall ได้

## Firewall

Firewall = Network Filtering
Network -> Data ที่ flow อยู่ใน nw เป็นหลัก

1. ป้องกันภัยคุกคาม : ใส่ pattern ของการโจมตีแล้วสั่งให้มัน deny ex. pattern NMAP ไม่ให้ผ่าน
2. กำหนดนโยบายการเชื่อมต่อ : nw A -> nw B ได้มั้ย?

ภัยคุกคาม
บางอัน capture packet มาบอกได้เลยว่าผิดปกติ
แต่อีกแบบถ้าขนอุปกรณ์ผลิตยาบ้าไป (firewall เก่งๆ จำ packet ไว้ได้)

![[Pasted image 20230301103000.png|500]]
ต้องดู data sheet : keyword -> Filtering , Access control

Management sw ทำ MAC addr filtering ได้ (firewall(ไม่สากล) ใน datalink)
L3 Switch มี package filtering อนุญาตให้ packet วิ่งผ่านหรือเปล่า

![[Pasted image 20230301103227.png|600]]

### switch based
sw base or appliance base ดูจาก จำนวน port
sw base - UTP port เยอะๆ  เกือบ 32 port
- มาจาก บ. ที่ทำ switch มาก่อน
ถ้า sw routing ได้ -> L3 sw
'+ filtering ทำ VLAN ได้

sw base ดู data sheet ว่า
- เป็น L3 ?
- filtering, access control
- policy
ข้อดี
- เร็ว (เพราะเกิดจาก switch)
- port เยอะ
ข้อเสีย
- policy ไม่ซับซ้อน

### appliance based
- port น้อย 4-8 port
- มาจากบริษัททำ controller, board มาก่อน (ไม่ได้ทำ sw มาก่อนแน่นอน)
- เอา linux มาใส่ แล้ว custom kernel ให้ support Network operation ให้ไว
- ทำ device interface network ใส่ไป
- เป็น controller : forwadding rate, bandwidth ไม่สูงมาก
- เป็น OS : sw base ตั้ง policy ซับซ้อนได้
- link ระบบอื่นๆ ได้

Firewall Bandwidth < Network Bandwidth
- sw based ความเร็วเยอะกว่า กินขาด
- ถ้าต้องการตรวจสอบ policy ซับซ้อน ใส่ role ไป link app อื่นเยอะๆ appliance ทำได้

![[Pasted image 20230301104632.png|400]]
firewall ดู 3 layer แล้วบอกว่าให้ผ่าน/ไม่ผ่าน


ในเครื่องคอม -> Host based firewall
- ป้องกัน จับ virus ได้บางส่วน (ไม่เยอะ) ตอนมันกระจายตัว แต่ไม่ได้เป็น antivirus (file system) firewall ได้เฉพาะ communication เช่น ปิด port นั้นนี้
- ex. เซ็ตไม่ตอบ ping
- shared drive แต่ปิดไม่ให้คนอื่นมา discovery

Q: Firewall ป้องกันภัยคุกคามอะไรได้ ไม่ได้
ทาง nw ที่มี pattern เกี่ยวข้องกับ header protocol
nw, transport layer เท่านั้น (ไปถึง app layer มั้ย ขึ้นอยู่กับ firewall)
ไม่เกี่ยวกับ content ใน app layer

Q: Firewall ควบคุมการเชื่อมต่อ จาก A -> B ได้หรือไม่
![[Pasted image 20230301105703.png|600]]
ไม่ได้
เพราะ Firewall จะทำกับ traffic ที่วิ่งผ่านมันเท่านั้น

Q: จาก A -> D ได้หรือไม่
ทำได้

Q: Firewall policy ถูกพัฒนาขึ้นก่อนหรือหลังภัยคุกคาม?

firewall กันได้ 60-70%
มูลค่า firewall ขึ้นอยู่กับ องค์กร

องค์กร ถ้าโดนโจมตี เสียมูลค่าเท่าไร (เก็บข้อมูลไว้เยอะๆ มูลค่าที่ล่ม กระทบกับรายรับยอดเท่านี้ๆ)
firewall 1 ตัว อยู่ใน 5 ปี มีค่า license รายปี

เอาที่บันทึก x 5 ปี ใส่ไปในราคา firewall
คืนทุกภายในกี่ปี (ส่วนมาก 2 ปี)

## ชนิดของ Firewall

4 types
![[Pasted image 20230301110852.png|300]]

stateful inspection มีขายเกรื่อนตลาด
next gen องค์กรใหญ่

### การกำหนดกฎของ Firewall

- **Allow All / Deny Some** : (filtering) Usability ทั่วไป ง่ายในการใช้งาน default allow all แล้วค่อยมาปิดทีละอัน (Plug-and-play)

- * **Deny All / Allow Some** : (more secure) 

>CISCO L3 Switch ถ้าปกติ จะเป็น allow all
>ถ้า set filter บางอย่าง มันจะ deny all อัตโนมัติ

>**default** กฎ deny any:any (src ไป dst ใดๆ ก็ตาม จะ deny)

### Packet Filtering Firewall
![[Pasted image 20230301112321.png|500]]
- Zone -> Zone
- มองแค่ header
- ex. nw A -> B ได้ A -> C ได้ แต่ B -> C ไม่ได้
- แรกเริ่ม network layer : เห็น src/dst IP เท่านั้น แต่ตอนนี้ src/dst port ได้
- ไม่ให้เข้าเว็บนี้ได้

![[Pasted image 20230301112127.png|500]]
>เพิ่มเติมในภาพ (รวมเป็น 3 ข้อ)
>Src.ABC:Any -> Dst.DEF:Any Allow
>Any:Any -> Any:Any deny (เป็น default เขียน/ไม่เขียนก็ได้ แต่แนะนำให้เขียน)

ไล่ deny ก่อน แล้วค่อย allow แล้วปิดด้วย deny all

>[!Warning] เมื่อไรที่กฎตัวแรกใส่ไป firewall (ส่วนมาก) จะเปลี่ยนเป็น any any - any any deny (deny all)
>ถ้าจะให้เชื่อมได้ ต้องใส่ Src.ABC:Any -> Dst.DEF:Any Allow

>[!Important] ออกสอบ ในข้อสอบ port ใส่ variable ได้
>port ต้นทาง สุ่มโดยไม่อยู่ใน 0-1024 (\* คือ port any) 
>defalut DB port : 3306

ip ใส่เป็น range ได้ -> subnet mask/ wildcard (ดูใน manual อีกที)
161.246.4.0/24

>[!Note] กฎมันทำงานบนลองล่าง อันไหนไม่เข้า = drop ทิ้ง

### Stateful Inspection Policy
อีกเทคนิคในการจัดการ policy

![[Pasted image 20230301112256.png|400]]
- เพิ่มเติม มี follow state ของแต่ละ protocol ได้
- ดูพฤติกรรมว่าจะทำอะไรต่อ ex. ให้ลองเชื่อมต่อก่อน แล้วค่อย block

>[!Summary] อยาก Apply กฎนี้ใน state ไหนได้เลย
>มุ่งเน้นที่ connection มากกว่า packet

![[Pasted image 20230301112624.png|500]]
- Packet filtering ทำไม่ได้ เพราะถ้าตัดไป มันมีการเปลี่ยนไป port 80 (ถ้าปิด 5121)
- admin ไม่ควรปิด 80 อยู่แล้ว
- ดังนั้นจึง ใช้ stateful allow 5121 ก่อน track ว่าถ้า cli connected (3way-handshake) กับ game server แล้วนับ 2 นาทีแล้วตัด deny (established state)
- src ip * dst ip เป็น server, state: tcp connected deny

**TCP State** (Connection Oriented)
![[Pasted image 20230315102846.png|400]]

cli ขอปิดก่อน ex. STP, Telnet, remote terminal
server ขอปิดก่อน ex. http (ส่งข้อมูลครบแล้ว)

>ต่อคาบหน้า


