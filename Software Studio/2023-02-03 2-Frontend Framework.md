# Bootstrap

framework เขียน rules ของ CSS ไว้แล้ว เราแค่เอาไปใช้ เขียนโครงสร้าง
- กำหนด class selection ไป map CSS rules กับ tag ที่ต้องการ format

- Frontend framework
	- CSS/JavaScript : JS ช่วย visual effect
- Supports building web pages/responsive web pages
	- Increase dev. Speed
	- Cross browser compatibility
- Current version: Bootstrap 5
	- Mobile first
- Was created at Twitter in 2010

## Setting up

- download manual จาก web มาใส่ใน webserver แล้วใช้ tag link เข้าไป
	- เก็บไว้ใน server เราเอง ควบคุม version ได้
	- ข้อเสีย มันอยู่ในเครื่อง เวลาโหลดหน้าเว็บ ไฟลืต้องถูกโหลดจาก server เราด้วย => เปลือง bandwidth (network)
- Package managers
	- npm install bootstrap or yarn add bootstrap
- CDN : Content Distributed Network
	- ประหยัด bandwidth ของเครื่อง server เรา
	- แต่ link เป็นของเจ้าของ CDN อาจมีเปลี่ยนได้ เราคุมไม่ได้
```html
<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.mi n.css" rel="stylesheet" integrity="sha384- EVSTQN3/azprG1Anm3QDgpJLIm9Nao0Yz1ztcQTwFspd3yD65VohhpuuCOmLASjC" crossorigin="anonymous">

<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/js/bootstrap.bund le.min.js" integrity="sha384- MrcW6ZMFYlzcLA8Nl+NtUVF0sA7MsXsP1UyJoMp4YLEuNSfAP+JcXn/tWtIaxVXM" crossorigin="anonymous"></script>
```
**Good Practice**
![[Pasted image 20230203102402.png]]
- ตามลำดับ style ถูกโหลดตั้งแต่ต้น ก่อนจะ render
- JS ควรอยู่ท้ายสุดของ HTML ไม่ควรอยู่ตรงหัวเพราะมันจะประเมินผล JS ก่อน render เสร็จ
	- render เสร็จแล้ว Visual effect ถึงจะทำงาน

# Layout

ทำ adaptive, responsive ได้ง่าย เพราะ framework กำหนดมาให้แล้ว

## Grid system

ต้องมี container
bt รับ container ได้ 3 แบบ
- `.container`
	- Max width at each breakpoint
- `.container-fluid`
	- 100% width at all breakpoint
- `.container-[breakpoint]`
	- 100% width until specific breakpoint

![[Pasted image 20230203102917.png]]
default - sm

Row , Column BT กำหนดให้แล้ว
- 12 columns per row
- 6 default responsive tiers
![[Pasted image 20230203103602.png]]

>[!Tip] เวลาเขียน html จะมี column กับ row

แบบ .col-
![[Pasted image 20230203103653.png]]
	.col-6 แสดงว่า div ตัวนี้กิน 6 column (ในทุก breakpoint)

![[Pasted image 20230203103929.png]]
	ครอง 6 col ถ้า viewport เป็น md
	ถ้า >= 768 เป็น container ขนาด 720px
	ถ้า < 768 เป็น 100%

### Auto layout
![[Pasted image 20230203104222.png]]

### Column wrapping
![[Pasted image 20230203104306.png]]

### Responsive layout
![[Pasted image 20230203104334.png]]

![[Pasted image 20230203104512.png]]

### Nested
![[Pasted image 20230203104603.png]]

## Flexbox

![[Pasted image 20230203105026.png|400]]
![[Pasted image 20230203105047.png|400]]
![[Pasted image 20230203105114.png|400]]
![[Pasted image 20230203105135.png|400]]
[Example](https://getbootstrap.com/docs/4.0/utilities/flex/)

## Display

- .d-inline  
- .d-inline-block
- .d-block
[Example](https://getbootstrap.com/docs/4.0/utilities/display/)
>- Hiding elements
>- Display in print
>	- ![[Pasted image 20230203111445.png]]

![[Pasted image 20230203111231.png]]

## Spacing

### Box Model
![[Pasted image 20230203111524.png|500]]

### Margin / padding
![[Pasted image 20230203111557.png|400]]

### Border
![[Pasted image 20230203111624.png|300]]

[Borders · Bootstrap (getbootstrap.com)](https://getbootstrap.com/docs/4.0/utilities/borders/)

## Sizing
![[Pasted image 20230203111804.png|300]]

## Typography

### Heading
![[Pasted image 20230203112147.png|400]]

### Paragraph
![[Pasted image 20230203112209.png|400]]
![[Pasted image 20230203112224.png|400]]
[Example](https://www.tutorialrepublic.com/twitter-bootstrap-4-tutorial/bootstrap-typography.php)

## Forms

[How to Create Form Layouts with Bootstrap 4 - Tutorial Republic](https://www.tutorialrepublic.com/twitter-bootstrap-4-tutorial/bootstrap-forms.php)

## Navigation

menu

[Bootstrap 4 Tabs and Pills Nav Component - Tutorial Republic](https://www.tutorialrepublic.com/twitter-bootstrap-4-tutorial/bootstrap-navs.php)

## References

- https://www.tutorialrepublic.com/twitter-bootstrap-tutorial/
- https://getbootstrap.com/docs/5.0/getting-started/introduction/
- https://www.w3schools.com/bootstrap5/index.php

---

# Activity

เขียน 1 page magazine จัด layout

**One page magazine**
1. เนื้อหา 7 เรื่อง (อาจสมมุติ หรือใช้ mock up เช่น Lorem ipsum...)
2. ใช้ bootstrap ในการกำหนด style เช่น
	1.  รองรับ RWD อย่างน้อย 1 breakpoint  
	2.  สร้าง nav-bar เพื่อใช้กระโดดไปยังแต่ละบทความ (เป็นเมนู)
	3.  Lay out ของเว็บ
	4.  อาจใช้กำหนด theme สีของเว็บทั้งหมด หรือกำหนดร่วมกับ CSS (BT มีสีน้อย)
3. ถ้ามีการกำหนด CSS เพิ่มเติมให้เขียนแบบ internal CSS
4. รูปประกอบให้ใช้เว็บฝากรูป แล้วนำ url จากเว็บฝากรูปมาใช้กับ tag เช่น `<img src="url จากเว็บฝากรูป">` เป็นต้น

ส่ง 1 ไฟล์ html only
