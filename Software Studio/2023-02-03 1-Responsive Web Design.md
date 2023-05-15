- หลักๆ กำหนด breakpoint ทำแต่ละ layout
- set breakpoint

# Introduction

- viewport => viewable area of a browser
- RWD display web content ขึ้นอยู่กับ viewport
	- breakpoint เป็นจุดของความกว้าง ที่จะกำหนดว่าจะมีกี่ layout ที่ต่างกันตาม width ของ viewport (จอ) เตรียมไว้ล่วงหน้า
	- "Shrink to fit" concept

ex. ตอบสนองต่อ 3 breakpoint 
![[Pasted image 20230203094803.png|500]]

## Other than RWD

- AWD (Adaptive Web Design)
	- อย่างน้อย 6 layouts (5 breakpoints)
	- detect viewport -> breakpoints
	- design แต่ละ breakpoint ด้วย fix design ได้ แต่ละ layout
- FWD (Fluid Web Design)
	- เตรียม layout เดียว แต่ขนาดกำหนดด้วย % ต่อ viewport
	- ex. 3col 33.33%
- Fixed Design
	- fix pixel or absolute unit (inch, cm,...)
	- ทะลุจอ

## Related

- Relative unit (different from "absolute unit")
	- %
	- em = length relative to font size of the element  
	- rem = length relative to font size of the root element
- [CSS units and relative units](https://www.w3schools.com/cssref/css_units.asp)

## Image

- Display image which width related to viewport
	- max-width: 100%

# CSS media queries

กำหนด breakpoint

```css
@media screen and (min-width: nnnpx) { 
	/*style1*/
}  
@media screen and (min-width: ooopx) {
	/*style2*/
}
```
min-width อย่างน้อย/กว้างกว่า nnn px ขึ้นไป
max-width

>`@media` ไม่ใช่แค่จอ เป็นขนาด printer ก็ได้

## CSS media queries in link tags
แยก css file

```html
<link rel=“style sheet” type=“text/css” media=“screen” href=“s.css”>

<link rel=“style sheet” type=“text/css” media=“screen and (orientation: portrait)” href=“p-s.css”>
```

## Media queries with @import
-> Conditionally load style sheets into the existing style sheet

```html
@import url(“small.css”) screen and (max-width:320px);
```

## More Media Queries

- Basic Media Queries by W3School  
	- https://www.w3schools.com/css/css3_mediaqueries.asp

- CSS Variables and Media queries section in Everything you need to know about CSS variable by Emmanuel Ohans (ตัวอย่างการประยุกต์)
	- https://www.freecodecamp.org/news/everything-you-need-to-know-about-css-variables-c74d922ea855/

## Media queries for high-resolution device
-> target ไม่ได้อยู่ที่ความกว้าง-ยาวของจอ แต่อยู่ที่ความละเอียดความหนาแน่นของจุดภาพบนจอ

- @media (min-resolution: 2dppx)
	- 2dppx = 2 dots per pixel
	- 1dppx = 96dpi  
	- 192dpi  
	- 1 pixel = 1/96 inch
	- 1 point = 1/72 inch

ex. 4K จอทีวีเห็นได้ แต่แสดงบนมือถือ 4K ตัวจะเล็กลงมากก 



