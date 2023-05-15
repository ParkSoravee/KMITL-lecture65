# Javascript

เขียนได้ 3 ลักษณะ
- internal
- inline
- external javascript * 
	- html ขนาดเล็กลง
	- reuse
	- proxy cache
	- easy to maintain

tag script มีกี่ตัวก็ได้ วางไว้ตรงไหนก็ได้ แต่แนะนำให้วางไว้ท้าย tag body

## Variable

- var, let keyword
- case sensitive
- เก็บได้แทบทุกอย่าง ex. func

![[Pasted image 20230210093542.png|300]]

### var VS let

![[Pasted image 20230210093646.png|500]]

var x;
var x = 5;

let y = 5
let y อีกไม่ได้

ex. declare in loop
var -> global ใช้ได้ก่อนใน define ใน loop ด้วย
let -> local (available only in scope that declare)

var ประกาศไว้ท้าย แต่ต้นๆ ก็ใช้งานได้ด้วย (posting behavior)

## Nameless function

func ไม่มีชื่อ ใช้ครั้งเดียว inline
(inline ต้องระวัง อาจจะเกิด bug ภายหลัง)

```
function() {...};
```

![[Pasted image 20230210094421.png|600]]

## Operators

![[Pasted image 20230210094655.png|500]]

`==` ไม่คิด type
`===` type ต้องเหมือนกันด้วย

'10' `==` 10 True
'10' `===`  10 False

## Conditional Statements

![[Pasted image 20230210094958.png|400]]

## Event Handlers

- คนใช้กระทำอะไรบางอย่างในหน้าเว็บ ex. click button
- หน้าเว็บส่งไป js แล้วตอบสนอง

![[Pasted image 20230210095546.png|600]]

### Inline (not recommend)
![[Pasted image 20230210100103.png|600]]

### Internal
แยก tag `<script>`

### External
![[Pasted image 20230210100252.png|600]]

(DOM)
![[Pasted image 20230210100310.png|600]]
func ใน js ไม่ถูกเรียกใช้ 
แต่มี code นอก func ถูก exe เรียกใช้ให้ (เมื่อ script ถูกโหลด)

### Examples
![[Pasted image 20230210100713.png|500]]
text box lost focus จะเรียก onblur

![[Pasted image 20230210100757.png|500]]
![[Pasted image 20230210100824.png|500]]
validation
`return false` คือการ cancel event นั้น ไม่มีการ link ไป

![[Pasted image 20230210101322.png|500]]

![[Pasted image 20230210101359.png|500]]

![[Pasted image 20230210101426.png|500]]

## The Event object

ข้อมูลที่ดึงมาใช้ได้ กับ js
![[Pasted image 20230210101911.png|600]]
Event.pageX เทียบกับ window browser
Event.screenX เทียบกับ ทั้งหน้าจอ

Ref: https://www.elated.com/events-and-event-handlers/

## Web Workers

![[Pasted image 20230210102058.png|600]]
งานหนักตอน render หน้าเว็บ
มีบางเว็บที่เป็น CPU intensive script มี js เยอะ render ภาพเยอะ ใช้เวลานานนน ทำให้เว็บ not response

code ที่จะรันใน web worker ต้องแยกออกมาจาก html (external)
ต้องเป็นไฟล์ js แยกจาก js อันหลัก
เพื่อเลี่ยงการใช้ global var. (race condition)

**main worker**
- render html
- run script y ที่ผูก `<script>` กับ html
**web worker** ติดต่อกับ main worker เท่านั้น
- load script w

### Create Web Workers
![[Pasted image 20230210102124.png|500]]

### To receive message from worker
เพราะ web worker ต้องติดต่อ main worker ให้ run ใน HTML
![[Pasted image 20230210103153.png|500]]
>ใน main worker กรณีมี msg จาก web worker w ให้เรียก func นี้

### To send msg. out of the worker
เกิดจาก web worker เรียก postMessage
![[Pasted image 20230210103556.png|400]]
ใน main worker ก็จะเกิด event onmessage

### Sending msg. into worker
![[Pasted image 20230210103700.png|500]]

### To terminate the worker
![[Pasted image 20230210103921.png|300]]

### Conclusion
![[Pasted image 20230210103957.png|500]]
- main worker สร้าง web worker ได้หลายตัว
- web worker สร้าง sub web worker ได้หลายตัว

![[IMG_3869.jpeg]]

---

## Cookie

>- Cookie ของเก่า
>- Web storage ของใหม่

แปะใน header ของ http msg.
ทุกครั้งที่ req ไป server ต้องเอา cookie แปะไปด้วย

![[Pasted image 20230210104830.png|600]]

### Cookie attributes

ตั้งชื่อได้โดยอิสระ
value เป็นอะไรก็ได้ที่ server ต้องการส่งมา
แต่ก็มี standard attr
![[Pasted image 20230210104927.png|500]]

domain url กว้างง ex. ส่ง cookie ไปหา ม. วิศวะ อ่านได้ วิทยา อ่านได้
เลยมี path ที่กำหนดเจาะจงขึ้น (privacy/sec) specific path เลย
js เขียนให้อ่านค่า cookie ได้

### Create cookie

server เป็นฝั่งสร้าง cookie
(จุดประสงค์แรกใช้ identify client แต่ยุคใหม่ทำงานกับ cookie ได้ใน frontend)

![[Pasted image 20230210105352.png|500]]

### Read a Cookie
![[Pasted image 20230210105517.png|500]]

### Change value of a Cookie
![[Pasted image 20230210105541.png|500]]

### Delete a Cookie
![[Pasted image 20230210105605.png|500]]
ไม่มีทาง delete property ของ obj ได้ ให้ใช้ set expire เป็นวันที่ย้อนหลัง

## Web Storage

>cookie ผิดวัตถุประสงค์ ใช้ track ได้ (no privacy) เลยเกิด web storage ใน ==HTML5==
>ให้ไม่สามารถ track ได้

![[Pasted image 20230210105727.png|500]]

จะส่งกลับไป server จะยากขึ้น
- เปิด websocket ส่งผ่าน network (เว็บธรรมดาไม่เปิด socket)

เปิดลักษณะ per domain
ex. .kmitl.ac.th จะใช้ storage ร่วมกัน
ce เขียน วิทยา อ่านได้ เพราะอยู่ใน domain เดียวกัน

>Encrypt เพื่อให้หน่วยงานใน domain เดียวกันอ่านไม่ออก (security)

![[Pasted image 20230210110324.png|500]]
**Web storage มี 2 ลักษณะ**
- local storage เก็บข้อมูลถาวร จนกว่าจะ clear cache
- session storage อยู่จนกว่าปิด browser เหมาะกับข้อมูล sensitive

>[!warning] ต้องเช็คเว็บ browser ว่ารองรับหรือเปล่า

### Storing data in Web Storage
![[Pasted image 20230210110414.png|500]]

### Retrieving data from web storage
![[Pasted image 20230210110441.png|500]]

### Removing data from web storage
![[Pasted image 20230210110504.png|500]]

### sessionStorage Object
![[Pasted image 20230210110523.png|500]]
ใช้เหมือนกับ local storage ทุกอย่าง
แต่แค่ปิด browser แล้วข้อมูลหาย

---

ไม่มี exercise
แต่ไปดูคลิป URL:youtube.com/watch?v=PkZNo7MFNFg&t=65s
(เนื้อหามีสิทธิ์ไปออกข้อสอบ!!)

