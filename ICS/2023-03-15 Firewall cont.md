# ทวน

Firewall filter nw layer packet
routing to firewall

packet matching

- packet filtering - ip / port
- stateful - ตาม state ได้ (แพงกว่า 1-2 เท่า ของ packet filtering)
- proxy - เป็นตัวกลางฝั่ง client รับ connection แทน (แพงกว่า 5-6 เท่า)
- next gen - integrate กับ service อื่น

# cont

## ชนิดของ Firewall

### Application Proxy

app เชื่อมต่อมาที่ firewall ทำ 3way-handshake ที่ firewall
รับ connection แทน เช็คว่า connection ถูกต้องตาม policy
ถึงจะ connect ไป server ให้ (มี 3way-hs เหมือนเป็นตัวแทน)

>กันการโจมตีได้หลายแบบมาก ex. scan port , DoS, half connection 

FB_Messaging(or Bittorent) ขี่บน HTTP
HTTP ขี่บน TCP
TCP ขี่บน IP
เป็น stack

>[!Question] สมมติมีเงื่อนไขว่า ให้ใช้ Facebook แต่ไม่ให้ใช้ FB Messaging ใช้ firewall ไหนได้?
>หรือ ไม่ให้ใช้ Bit torent

![[Pasted image 20230315105004.png|350]]

กำหนด zone ก่อน 
![[Pasted image 20230315104056.png|500]]
![[Pasted image 20230315104435.png]]
![[Pasted image 20230315112050.png|500]]

![[Pasted image 20230315105206.png|400]]
junos:bittorrent


### Next Generation Firewall

app proxy base แค่ไป plug กับ service อื่นให้รู้จัก
ทำอะไรได้บ้างแล้วแต่รุ่นเลย

Classify traffic ว่าตรงกับ service ไหน
map ให้
![[Pasted image 20230315105231.png|500]]

ex. paloalto
![[Pasted image 20230315105248.png]]

profile คือทำ acrtion อะไรได้

#### Ac
![[Pasted image 20230315105431.png|500]]

ex. 
- port scan  x / / /
- Virus(script/ content base จากหน้า page) x x x x
- Virus(network base) กันได้

![[IMG_1594.jpeg]]

### Ac2
>ออกข้อสอบเก่า

เขียน policy
![[Pasted image 20230315111843.png|500]]
![[Pasted image 20230315111829.png|600]]

วิธีคือ อ่านแล้ว ลากเส้น
![[IMG_3453.jpeg|500]]


![[Recording 20230315113250.webm]]

## More examples

![[Pasted image 20230315113338.png|500]]
กันที่ R1 ตัวเดียวเลย

![[Pasted image 20230315113403.png|500]]
ใส่ policy ที่ R1 และ R4 กันทุกทาง

>ไปทางไหน อยู่ที่ default gateway ที่ set ในเครื่อง E (เราไม่รู้)

![[Pasted image 20230315113604.png|400]]
สมัย Firewall Bandwidth ต่ำ
- ทำตามลำดับ
- กฎไหนที่ match บ่อย ให้อยู่กฎแรกๆ ex. web, mail อันไหนไม่บ่อย ไว้ล่างๆ ex. ftp

สมัยนี้ (แก้ด้วยเงินได้)
- parallel process แบ่งงานให้ processor หลายๆ ตัว
- ลำดับไม่ค่อยมีผล

![[Pasted image 20230315113816.png|400]]
เมื่อก่อน ถ้าซ้ำจะทำงานช้า
สมัยนี้ ไม่ค่อยมีปัญหา ฉลาดขึ้น แจ้งว่ามีซ้ำ

## Firewall Zone

![[Pasted image 20230315113907.png|500]]

แยกเป็น 3 ระดับ (อยู่ที่ admin เจ้าหน้าที่ดูแล)
- untrust คือควบคุม user ไม่ได้ (ไม่รู้ว่าใครเข้ามา จัดการไม่ได้) เช่น web server, FTP, wifi network, student network เด็กภาคคอม/ IT/ Com-sci
- DMZ (demilitarized zone เขตปลอดทหาร) Zone คือครึ่งๆ 50/50 คนในก็ใช้ คนนอกก็ใช้ รู้ว่าใครทำอะไร ex. proxy(untrust/DMZ ก็ได้ อยู่ที่ trust แค่ไหน)
- trust คือรู้เลยว่า user คือใคร ใช้อะไรบ้าง (ex. ตึกอธิการ ใช้งานอินเตอร์เน็ตส่วนใหญ่, โหลดบิตไม่มี, เกมนิดหน่อย)

แต่ละ zone เอา firewall มากั้น แล้วเอา policy ใส่

>[!Tip] พอมี network เดิม แล้วเอา firewall ไปใส่ได้ ตาม zone

Q:
![[Pasted image 20230315114912.png|400]]
การจัดวาง มีเรื่อง traffic ด้วย (เกิดทีหลังจากที่ใช้ไปสักพักแล้ว monitor) (ไม่ใช่ประเด็นปัญหาใหญ่)
มุ่งเน้นให้ผ่าน firewall จำนวนตัวน้อยสุด 

![[Pasted image 20230315115129.png|500]]
มีความเสี่ยง ถ้าใช้ multi-leg เช็คว่า trust/untrust zone ไม่ link กัน
security admin จะบอกว่าตรงไหน มี/ไม่มี policy

>Firewall ทำหน้าที่ router ในตัวได้

![[Pasted image 20230315115513.png|600]]
ใช้ตัดฝั่ง untrust ออกด้วย sandwich
inside จะเป็น multi-leg อะไรก็ได้
เหมือนกรอง 2 ชั้น

**โดยทั่วไป เป็นแบบนี้**
ใน trust zone จะ link ยังไงก็ได้
![[Pasted image 20230315115703.png|600]]
layer ของ
- untrust
- DMZ
- trust

---

## Ac1

from chat-gpt
1.  SYN Flood Attacks: A type of denial-of-service (DoS) attack that involves sending a large number of SYN requests to a target server, overwhelming its ability to respond and causing a denial of service to legitimate users. All types of firewalls can detect and prevent this type of attack to some extent.
    
2.  IP Spoofing: A technique used by attackers to forge the source IP address in packets to hide their true identity and bypass access controls. Packet filtering and stateful inspection firewalls can block traffic from known spoofed IP addresses, but Application proxy and next-generation firewalls can provide more advanced detection and prevention capabilities.
    
3.  Denial-of-Service (DoS) attacks: An attack that floods a network or server with traffic or requests, rendering it unavailable to legitimate users. All types of firewalls can detect and prevent this type of attack to some extent.

	 Distributed Denial of Service (DDoS) Attacks: A variant of DoS attacks that involve using a large number of compromised systems to launch a coordinated attack on a target system. Next-generation firewalls can provide more advanced detection and prevention capabilities for this type of attack.
    
4.  Port Scanning: The process of systematically scanning a network for open ports and services in order to identify potential vulnerabilities. Packet filtering and stateful inspection firewalls can block traffic from known scanning IPs, while Application proxy and next-generation firewalls can provide more advanced detection and prevention capabilities.
    
5.  IP Fragmentation Attacks: A type of attack that exploits vulnerabilities in the way that IP packets are fragmented and reassembled in order to cause network disruption or bypass security controls. All types of firewalls can detect and prevent this type of attack to some extent.
    
6.  SQL Injection Attacks: An attack that exploits vulnerabilities in web applications that allow SQL commands to be executed on a database, often resulting in unauthorized access or modification of data. Application proxy and next-generation firewalls can provide more advanced detection and prevention capabilities for this type of attack.
    
7.  Cross-Site Scripting (XSS) Attacks: An attack that injects malicious scripts into a web page viewed by other users, often leading to unauthorized data access or manipulation. Application proxy and next-generation firewalls can provide more advanced detection and prevention capabilities for this type of attack.
    
8.  Malware Attacks: Malicious software that is designed to infiltrate a computer system, often with the goal of stealing data, disrupting operations, or causing damage. All types of firewalls can detect and prevent this type of attack to some extent.
    
9.  Insider Threats: Threats posed by individuals with authorized access to an organization's systems or data, who may intentionally or unintentionally cause harm. Application proxy and next-generation firewalls can provide more advanced detection and prevention capabilities for this type of attack.
    
10.  Data Exfiltration: The unauthorized transfer of data from an organization's systems or network to an external location, often for malicious purposes such as data theft or espionage. Application proxy and next-generation firewalls can provide more advanced detection and prevention capabilities for this type of attack.
    
11.  Ransomware: A type of malware that encrypts an organization's data and demands payment in exchange for the decryption key. All types of firewalls can detect and prevent this type of attack to some extent.
    
12.  Zero-day attacks: An attack that exploits previously unknown vulnerabilities in software or hardware before a patch or fix can be developed. Application proxy and next-generation firewalls can provide more advanced detection and prevention capabilities for this type of attack.
    
13.  Advanced Persistent Threats (APTs): A type of targeted attack that involves a prolonged and sophisticated intrusion into an organization's systems or network, often with the goal of stealing sensitive data. Application proxy and next-generation firewalls can provide more advanced detection and prevention capabilities for this type of attack.

14.  URL Spoofing: A type of attack that involves creating a fake website that appears to be legitimate, with the goal of tricking users into providing sensitive information. Application proxy and next-generation firewalls can provide more advanced detection and prevention capabilities for this type of attack.
    
15.  DNS Spoofing: A type of attack that involves redirecting network traffic from a legitimate website to a fake website, with the goal of stealing sensitive information. All types of firewalls can detect and prevent this type of attack to some extent.
    
16.  Man-in-the-Middle (MitM) Attacks: A type of attack that involves intercepting and manipulating network traffic between two parties, with the goal of stealing sensitive information or injecting malicious code. Application proxy and next-generation firewalls can provide more advanced detection and prevention capabilities for this type of attack.
    
17.  Application-layer Attacks: Attacks that exploit vulnerabilities in specific applications or protocols, often with the goal of stealing sensitive data or causing disruption. Application proxy and next-generation firewalls can provide more advanced detection and prevention capabilities for this type of attack.
    
18.  Brute Force Attacks: A type of attack that involves systematically trying a large number of password combinations in order to gain unauthorized access to a system or account. All types of firewalls can detect and prevent this type of attack to some extent.
    
19.  Cross-Site Request Forgery (CSRF) Attacks: A type of attack that exploits a web application's trust in a user's session to perform unauthorized actions on their behalf. Application proxy and next-generation firewalls can provide more advanced detection and prevention capabilities for this type of attack.
    
20.  Drive-by Downloads: A type of attack that involves infecting a user's computer with malware by exploiting vulnerabilities in their web browser or other software. Application proxy and next-generation firewalls can provide more advanced detection and prevention capabilities for this type of attack.

