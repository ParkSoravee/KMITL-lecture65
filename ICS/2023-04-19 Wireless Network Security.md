
30 min late

---

# Physical layer

## 802.11

802.11a bandwidth 20MHz
802.11n bandwidth 20/40MHz แลกด้วยช่องสัญญาณลดลง flexible ลดลง
802.11ac 20/40/80/160/160(80+80)MHz เพิ่ม flexible มากขึ้น fix ได้เลยว่าจะใช้อันไหน มี guardband เป็นมาตรฐานให้. พอ bw เยอะ ทำให้มีโอกาสโดนรบกวนสูง (ปจบ. ม. ลดจาก 80 มาใช้ 40MHz กันรบกวน)

>guardband เป็นช่องสัญญาณว่างคั่น ไม่ให้ไปชนกันช่องอื่น

## Channel

2.4GHz : b, g, ac
5GHz : a, n, ac

2.4 GHz
![[Pasted image 20230419100626.png]]

### สิ่งที่ต้อง concern
**1. ช่องสัญญาณ**
แบ่งได้ 14 CH แต่ใช้ได้ไม่หมด ใช้ได้มากสุด 3 CH 1, 6, 11, 14(โดนกวนอยู่นิดนึง)
ex. พท เดียวกัน router ch1, access point ch6 ถ้า ch ชนกัน speed ตก
cover range ของ 2.4GHz กว้าง ถ้าใช้ anthena จะบีบความกว้างได้
เสาสัญญาณ anthena กระจายได้แบบ
- กระป๋อง 30องศา แนวตั้ง แต่แนวนอน 360 รอบตัว
- แตงโม 360องศา นอนตั้ง
- เก็บมุมห้อง
- cover ห้องสี่เหลี่ยม

802.11ac ตัวอุปกรณ์ฉลาด จะเลือกช่องที่ไม่ซ้ำ

wifi 6 : 6GHz
แต่ข้อจำกัด
ความถี่สูง รบกวนสูงตาม
ระยะทางไม่ไกล
แต่ได้ bw เยอะ

เวลาเลือก tech ต้องเลือกว่า
1. เอา bw เท่าไร
2. พื้นที่ ถ้าต้องการกว้างไปความถี่ต่ำ 2.4GHz แต่ ch มีให้เลือกน้อย
bw สูงจะกินช่องสัญญาณเยอะ จะมีช่องน้อย

ความแรง ความเข้มสัญญาณที่เหมาะสม > -50 dBm
ถ้าน้อยกว่า -30dBm แจ๋วเลย
< -80 แย่มาก เปิดอะไรไม่ขึ้น

>Wifi analyzer โปรแกรมโหลดจาก Microsoft Store ดูความแรงสัญญาณ ดูว่าแถวนี้ใช้ CH ไหนบ้าง

access point เดียวกัน ใช้ ch เดียวกัน คนละ ssid จะไม่ชนกัน มันจะไปแยกข้างในเอง

1. CH ไม่ชน ชาวบ้าน
2. ความเข้มสัญญาณต้องดีด้วย

simulator เวลาวางแผนติดตั้ง wifi อุปกรณ์ network แต่ละที่
![[Pasted image 20230419103014.png|600]]
จำลองการใช้ ch1 ทั้งหมด มีพท. โดนรบกวน มีปัญหาแน่นอน

สิ่งที่อยากได้ แบบนี้
![[Pasted image 20230419103259.png]]
แบบนี้ ch 1,2 ซ้อนกันแน่นอน (3ใน4)
![[Pasted image 20230419100626.png|400]]

แบบนี้โอเค พท. ที่ overlaped กันต้องเป็น ch ที่ไม่ซ้อนกันแน่นอน
![[Pasted image 20230419103347.png]]
เดินจาก ch1 ไป ch11 จะมีการ hand off เปลี่ยนไปจับ ตัวดีๆ หน่อยจะไม่กระทบ layer บนๆ

![[Pasted image 20230419103531.png]]
แต่ห้องประชุม ซ้ายกลาง จะชนหน่อยๆ

ch 1 5 9 13 : เป็น sulution ที่ดี
![[Pasted image 20230419103616.png]]

## Tools

- Wifi Analyzer (MS store)
- Vistumbler : ดูสัญญาณแต่ละตัวของ wifi ssid เอาไปประเมิณเครือข่ายที่ทำได้
	- Authentication
		- WPA2
			- Personal ตัว auth อยู่ในอุปกรณ์
			- Enterprise ตัว auth อยู่ใน server
		- Open ใช้ได้เลย ไม่ต้องใส่รหัส
		- Encryption ปลอดภัยได้อยู๋
	- RSSI : ความแรง
	- Channel ไหนใครใช้บ้าง
- Ekahau (ซื้อ 1 ล้านกว่าบาท) site survey and spectrum analyzer

## รู้จักศัพท์กี่คำ

![[Pasted image 20230419104911.png|500]]

อุปกรณ์ Ad hoc คุยกันเอง route เอง เปลืองไฟ
infrast. mode อุปกรณ์ network route ให้
broadcast ssid : อยู่ใน open network
CSMA/CA : collision avoidance ใช้คล้าย token ring บนอุปกรณ์ access point จัดการ token ให้เครื่อง a,b,c ฟังว่า carrier ว่าง ถึงจะส่ง
CSMA/CD : collision detection คือ voltage โดด ส่งชนกัน คนส่งกับอุปกรณ์เป็นตัว detect เกิด collision ก็จะ delay แล้วส่งใหม่

### Open Network
![[Pasted image 20230419105513.png|500]]
คือกระบวนการที่ access point ปล่อย ssid ออกมา ผ่าน **beacon** frame
node ที่จะเกาะสามารถขอ connect ได้ ส่ง ass req แนบ MAC Address ไป
acc เอา MAC ใส่ข้อมูล แล้วส่ง resp กลับไป 
plug ได้แล้ว แต่จะใช้งานได้ไหม??
ถ้าไม่มี auth ใช้ได้เลย (open system authentication)
ถ้ามีการทำ **MAC Address filtering** : filter ว่า mac address ไหน ให้ใช้ ไม่ให้ใช้
- แบบ allow list (ไม่เกิน 64) *ส่วนใหญ่ใช้*
- แบบ deny list

### Close Network
access point ปิดตัวเงียบ
![[Pasted image 20230419110043.png|500]]
จะใช้ต้องกรอกเอง probe ดูจะเจอ
ข้อดี secure มาก คนโจมตีไม่รู้ว่ามี access point
แต่ไม่ได้ปลอดภัยซะทีเดียว เพราะถ้ามีเครื่องนึง connect แล้วไปจับเครื่องนั้นจะเจอ ssid

## User Authentication

![[Pasted image 20230419110354.png|600]]
open network with open system auth -> free wifi ในเขต ชุมชน
ระวังมี proxy อยู่ ไม่ควรเชื่อม
มี auth อยู่

![[Pasted image 20230419110515.png]]
WEP ไม่ส่งรหัสผ่านกัน แต่ใช้ key (รหัสผ่าน)
challenge text เป็น random text ตัวนึง
เอา text encrypt ด้วย รหัสผ่าน แล้วส่ง ดูว่าตรงกันไหม
(share key ไม่ได้มีใช้เฉพาะ wifi)
![[Pasted image 20230419110801.png|500]]
WEP เป็นการเข้ารหัส (แบบหลวมๆ xor)
gen key ชุดนึง แล้วเอาไป xor กับ data ที่จะส่ง แล้วโยนไปปลายทาง
ปลายทาง gen key แล้ว ส่งมาเหมือนกัน

>กระบวนการเข้ารหัสอ่อนด้อย แต่เร็ว ใช้สมัยก่อน

![[Pasted image 20230419111154.png]]
CRC-32 เป็น integrity check ได้ ICV ออกมา
หั่น plain text เป็น block เข้า XOR
K(AB) : WEP key
ต้องใช้ IV (เลขสุ่ม หรือเลขไล่ ค่านึง) ใช้เป็น index ใน algo ใน PRNG
key ไม่ต้องส่ง เพราะรู้ 2 ฝั่งอยู่แล้ว

ปัญหา(ปี 2002): IV ตรงกัน จะทำให้ invert หา key ได้
![[Pasted image 20230419111646.png|500]]

Wi-Fi : กลุ่มของผู้ใช้บริการ บ. ที่เกี่ยวกับ wireless network (802.11) ไม่ใช่ tech แต่เป็นกลุ่มคนกลุ่มคนนึงที่เกี่ยวข้อง เป็น tester แล้วให้ certificate IEEE 802.11
Wireless Network : เป็น tech

ซื้ออุปกรณ์มา cer มีเลข ไปเช็คกับ WiFi ได้

WEP IEEE 802.11 เป็นคนออก
WPA Wi-Fi เป็นคนออก
IEEE 802.11i ทำด้าน sec ที่ 802.11 ไม่มี

WPA ให้ Patch อัพเดท firmware ใหม่
WPA2 ต้องซื้อใหม่ เพราะ chip เปลี่ยน

![[Pasted image 20230419112741.png|600]]
Enterprise ไป auth กับ อุปกรณ์ 3rd party ได้
Personal auth ในอุปกรณ์

![[Pasted image 20230419113117.png|500]]

![[Pasted image 20230419112847.png|600]]
เอา data เข้ารหัส เพิ่มความยาว key โอกาสซ้ำน้อยลง
ไม่สามารถ reverse หา key ได้แล้ว

![[Pasted image 20230419113056.png|400]]
48 bit -> 280 trillion โอกาส IV ซ้ำน้อย
psudo .. gen เปลี่ยนตั้งชุด
patch firmware ได้

แต่ก็ไม่หมดทีเดียว TKIP ไม่ใช่เป็นที่ยอมรับ
แค่ gen key ยาวขึ้น แต่ใช้ processing power ต่ำอยู่

algo แข็งแกร่งสุดในโลก (ในตอนนั้น) คือ WPA2 -> AES
![[Pasted image 20230419113344.png|500]]
![[Pasted image 20230419113527.png|500]]

802.1X แบบ ม. proxy ขึ้นหน้าให้ login ก่อน

WPA2 sec เพิ่มขึ้น
- Confidentiality : AES
- Auth method : กระบวนการ auth แต่ละ access point จะมีการทำ auth ที่ server ด้วย
![[Pasted image 20230419113929.png|500]]
(ระบบ มหาลัย)

![[Pasted image 20230419114208.png|600]]

---

ใครเกี่ยวข้องกับ wireless sec บ้าง แล้วต้อง concern อะไรบ้าง แล้วแก้ยังไง
1. ผู้ใช้งานทั่วไป
- เลือกอุปกรณ์ที่เชื่อถือเท่านั้น : (man in the middle attack) access point แรงๆ open network/open system auth ตั้ง proxy ไว้ อุปกรณ์ auto เกาะ
	- ควร set เครื่องว่า ถ้าจะไปเกาะ nw ไหน ให้ถาม (set เลือกอันไหนเกาะอัตโนมัติบ้าง trust แค่บางอุปกรณ์)
- ไม่ใช้ nw ที่ sec ต่ำ
	- ใช้ WPA2 only!! (vpn กลายๆ อยู่ละ)
	- ทำ vpn ต้นทางไปปลายทาง

2. คนวางระบบ (internet บ้าน/องค์กร)
- ช่องสัญญาณห้ามชน
	- ex. floor นึงติดตั้ง 3 ตัวถึงจะ cover จะ set CH ยังไง
	- ตรงไหน สัญญาณขาดเอา atena ไปเติม

3. คนดูแลระบบ (Network admin)
- authentication
- ป้องกัน access point
	- ใครที่มาเสียบ lan ต้องไม่ให้ authen
	- 802.11i sec สูงสุด
	- 802.11i การเข้ารหัส AES ปลอดภัยสูงมาก

---

ไม่ว่า site ใหญ่เล็ก ใช้ WPA2 only! จบ

