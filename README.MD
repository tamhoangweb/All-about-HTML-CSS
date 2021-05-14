# All about CSS (update...)

## 1. Cách tổ chức 1 file CSS

Phân chia loại CSS

Có bảng đề mục loại CSS

Các CSS có chung đặc tính ghi gần nhau

Các CSS khác đặc tính ghi cách nhau 1 dòng

Ví dụ

```CSS
/* table of contens
1. global styles

2. typograhpy

3. components
   3.1 buttons
*/
```

```CSS
/* ================
   global styles
   ================ */

```

## 2. Các CSS nên dùng

```CSS
:focus{
  outline: none;
}

```

## 3. Cách selector element để CSS (tên gọi khác: CSS selectors)

### 1. Nhóm được chọn nhờ tự thân element đó

Dựa vào tên thẻ của element

```CSS
/* css cho element có thẻ tag là div hoặc span, hoặc h1, hoặc h2 */
div, span, h1, h2
```

Dựa vào thuộc tính class của element

```CSS
/* css cho element có class = "prevBtn" */
.prevBtn

/* css cho element không có class = "prevBtn" */
li:not(.green)

/* css cho element có 2 class = "prevBtn btn" */
.prevBtn.btn
```

Dựa vào thuộc tính id của element

```CSS
/* css cho element có id = "prevBtn" */
#formLogin
```

Dựa vào thuộc tính data-\*

```CSS
/* css cho element có thuộc tính data-red */
[data-red]

/* css cho element có thuộc tính data-red="true" */

[data-red="true"]

/* thuộc tính data-red có giá trị khởi đầu là chuỗi "12" */
[data-red^="12"]

/* thuộc tính data-red có giá trị kết thúc là chuỗi "12" */
[data-red$="12"]

/* thuộc tính data-red có giá trị chứa chuỗi "12" */
[data-red*="12"]
```

Dựa vào một số thuộc tính khác

```CSS
input:checked
input:required
input:disabled
```

Dựa vào các pseudo của element đó

```CSS
/* css cho element li khi li được mouse hover qua */
li:hover

/* css cho element input khi input được focus */
input:focus
```

### 2. Nhóm được chọn nhờ cha, anh em bà con

Dựa vào cha trực tiếp

```CSS
div > a

/* css cho element là element li và là con đầu tiên của element cha bất kỳ */
li:firts-child

li:last-child

/* css cho element là element li và là con thứ 3 của element cha bất kỳ */
li:nth-child(3)

/* css cho element là element li và là con thứ chẵn của element cha bất kỳ */
li:nth-child(2n)

/* css cho element là element li và là con thứ lẻ của element cha bất kỳ */
li:nth-child(2n - 1)

li:nth-last-child(2n-1)

/* css cho element là phải là element con có kiểu thẻ là span và là con đầu tiên theo kiểu thẻ span đó */
span:first-of-type

li:last-of-type
li:nth-last-of-type(2)
```

Dựa vào cha trực tiếp, hoặc cha xa xôi nhiều cấp

```CSS
div a

/* css cho thẻ span, mà phải có cha */
span:only-child
```

Dựa vào anh trực tiếp - ngay kế bên

```CSS
/* css cho thẻ li là em kế nhất của thẻ li.red */
li.red + li
```

Dựa vào anh trực tiếp hoặc xa xôi

```CSS
/* css cho tất cả các thẻ em của li.red */
li.red ~ li
```

## 4. CSS tricks

### 1.Tooltip

Các selectors sử dụng:

```css
[data-tooltip]

[data-tooltip]:hover::before
```

Các properties và value được sử dụng

```css
/* lấy value của attribute data-tooltip để hiển thị chữ */
content: attr(data-tooltip)

/* dùng cho element cha, nhằm tạo khung neo cho các element con bên trong đặt vị trí */
position: relative

/* quy định vị trí chính xác của element con bên trong element cha đã được position relative */
position: absolute

/* độ rộng của element con = 100% độ rộng của element cha */
width: 100%

/* Khoảng cách với element cha, tính từ viền trên = 0 */
/*Lưu ý: chỉ dùng được khi element cha có position relative, và element con có position absolute */
top: 0

/* Dịch chuyển theo chiều dọc, tính từ vị trí hiển tại ngược lên trên 1 đoạn đúng bằng 100% chiều cao của chính nó */
transform: translateY(-100%)

/*Vừa dịch sang trái, vừa dịch chuyển lên trên */
transform: translate(-50%, -100%)

```

### 2. :is

Các selectors sử dụng:

```css
/* CSS cho các element là li, con của ul hoặc ol, và ol hoặc ul này là con của ul hoặc ol khác */
:is(ul, ol): is(ul, ol) li;
```

### 3. Tăng biến đếm trong CSS

#### Bài toán 1:

- Trong tài liệu html, có nhiều thẻ h2
- Mỗi thẻ h2 là 1 tiêu đề, chỉ chứa nội dung có nghĩa, không có đánh số đề mục.
- Dùng CSS để sao cho trước mỗi h2, sẽ được đánh số đề mục la mã tự động.

Bước 1: cài property counter-reset cho selector body

```css
body {
  counter-reset: heading;
}
```

Bước 2: cài property counter-increment cho selector h2::before

```css
h2::before {
   content: "Phần" counter(heading, upper-roman) ": "
   counter-increament: heading;
}
```

#### Bài toán 2: Dùng counters syntax thay đổi cách hiển thị số của order list

Mặc định order list hiển thị là

```html
1. First item 2. Second item 1. item 2. item
```

Đổi thành kiểu đề mục sách

```html
1. First item 2. Second item 1.1. item 2.1. item
```

Bước 1: tắt hiển thị số mặc định của list

```css
li {
  list-style: none;
}
```

Bước 2: cài property content mới cho selector li:before

```css
li:before {
  content: counters(outline, ".") ". ";
  counter-increment: outline;
}
```

### 4.Flexbox Gap

Property gap thường được dùng trong display flex. Tuy nhiên nhiều trình duyệt chưa hỗ trợ thuộc tính này, ví dụ: safari trên iOS.

Giải pháp thay thế là dùng margin với cách selector đặc biệt như sau:

```css
.flex {
  display: flex;
}
.flex > * {
  margin-right: 10px;
}

/* tắt margin của phần tử cuối cùng trong element cha flex */
.flex > *:last-child {
  margin-right: 0;
}
```

### 5.Value conic-gradient dùng để tạo màu

```css
background: conic-gradient(
  red 0.25turn,
  //từ 0 đến 25%
  blue 0.25turn 0.5turn,
  //từ 25% đến 50%
  green 0.5turn //từ 50% đến 100%
);
```

### 6. Tạo chữ transparent với background là hình ảnh. (Background Clip Text)

```css
background-image: url('water.jpg')
-webkit-background-clip: text
background-clip: text
color: transparent
```

### 7. Reset lại giá trị của toàn bộ các thuộc tính css của element. (The All Property)

```css
all: initial;
```

### 8. Sử dụng giá trị 9999px để tạo bo góc cho đường viên (Easy Pill Shaped Buttons)

Giúp bo góc đường viền mà không cần cài đặt chiều cao cho block.

```css
border-radius: 9999px;
```

### 9. Tạo ký tự ... khi đoạn văn dài quá độ rộng của khối (Text overflow Ellipsis)

```css
text-overflow: ellipsis
white-space: nowrap
overflow: hidden
```

## 5. Dùng query @supports để kiểm tra trình duyệt có hỗ trợ thuộc tính css hay không

Ví dụ:

- Nếu trình duyệt CÓ hỗ trợ property position có value là sticky thì element body, sẽ có màu nền là màu pink

```css
@supports (position: sticky) {
  body {
    background-color: pink;
  }
}
```

- Nếu trình duyệt KHÔNG CÓ hỗ trợ property position có value là sticky thì element body, sẽ có màu nền là màu pink

```css
@supports not (position: sticky) {
  body {
    background-color: pink;
  }
}
```

- Nếu trình duyệt có hỗ trợ property position có value là sticky, VÀ position có value là relative thì element body, sẽ có màu nền là màu pink

```css
@supports (position: sticky) and (position: relative) {
  body {
    background-color: pink;
  }
}
```

- Nếu trình duyệt có hỗ trợ property position có value là sticky, HOẶC position có value là relative thì element body, sẽ có màu nền là màu pink

```css
@supports (position: sticky) or (position: relative) {
  body {
    background-color: pink;
  }
}
```

## 6. Dùng query @media để CSS cho màn hình nằm ngang

```css
@media (orientation: landscape) {
}
```

## 7. CSS Animation

Bối cảnh 1:

- Có 1 block cha
- Bên trong block cha có 1 block con
- Khi hover qua block cha thì block con chuyển động.

Nguyên tắc:

- Thuộc tính transition sẽ được đặt ở block con
- Thuộc tính "chuyển động" sẽ được đặt ở block con khi block cha được hover

```css
block-con {
   thuộc tính transition
}
block-cha:hover block-con{
  thuộc tính chuyển động
}
```

- Trường hợp chuyển động sau 1 khoảng thời gian user vào website, không phải dựa vào việc block cha được hover thì:

```css
/* Đối với thuộc tính transition, sẽ dùng transition-delay */
transition-delay: 2s;
```

```css
/* Đối với thuộc tính animation, sẽ dùng animation-delay */
animation-delay: 2s;
```

- Thuộc tính transition tạo ra cảm giác chuyển động mượt mà, hoặc va đập, tốc độ nhanh chậm ...
- Thuộc tính chuyển động, bao gồm tất cả các thuộc tính css, khiến cho block con thay đổi vị trí, màu, kích thước... Tóm lại là các thuộc tính khiến cho block-con đổi từ kiểu css này sang kiểu css khác Ví dụ:

1. margin
2. padding
3. left, top, right, bottom
4. transform
5. animation
   ...

- Trong đó, thuộc tính animation là tổng hợp của nhiều thuộc tính chuyển động khác. Do đó, nó phải được tạo ra bằng rule keyframes.

```css
block-cha:hover block-con {
  animation: left-to-right 1s ease-in;
}
@keyframe left-to-right {
  100% {
    transform: translateX(100%);
  }
}
```

### 1. Các value của thuộc tính animation

- name : là tên khi tạo rule @keyframe
- duration : Thời gian hoàn thành chuyển động 1 lần
- delay : Thời gian trì hoãn trước khi chạy (có cho phép dùng số âm)
- iteration-count : Số lần chạy, hoặc chạy vô tận
- direction : hướng chuyển động
- timing-function : linear, ease, ease-in, ease-out, ease-in-out
- fill-mode. : có bị giật về vị trí ban đầu sau khi thực hiện chuyển động hay ko

### 2. Các rule @keyframe

- Thuộc tính animation phải chỉ ra Khoảng thời gian thực hiện xong chuyển động.
- @keyframe sẽ dựa vào khoảng thời gian này, mà tiến hành thay đổi hiệu ứng.

```css
@keyframe example {
  0% {
    background-color: red;
  }
  25% {
    background-color: yellow;
  }
  50% {
    background-color: blue;
  }
  100% {
    background-color: green;
  }
}
```

### 3. Khi hover qua block-cha thì, block-con ngưng chuyển động.

- Chuyển thuộc tính animation lên làm thuộc tính mặc định của block-con
- Dùng thuộc tính animation-play-state

```css
block-con {
  animation: left-to-right 1s ease-in forwards infinite alternate;
}

block-cha:hover block-con {
  animation-play-state: paused;
}
```

## 8. CSS Animation Performance

### 1. Nếu chuyển động lên xuống, hãy dùng transform: translateY thay cho margin

### 2. Nếu biến mất, hãy dùng opacity.

## 9. Thuộc tính CSS ít dùng nhưng hay

### 1. Resizable

```css
/* Dùng chuột kéo mở rộng khối theo chiều ngang */
resize: horizontal
resize: both
overflow: hidden

/* giới hạn phạm vi mở rộng khối */
min-width: 200px
width: 300px
max-width: 400px
```

### 2. Aspect Ratio

```css
aspect-ratio: 16 / 9
aspect-ratio: 1 / 1
/* cài đặt độ rộng mặc định */
width: 100px
```

### 3. Scroll padding Top

Cài đặt khoảng cách mặc định giữa scroll khi click vào anchor với viền trên của trình duyệt.

```css
:root {
  --header-height: 50px
  scroll-padding-top: calc(var(--header-height) + 10px);
  scroll-behavior: smooth;
}
```

## 10. Flexbox design patterns

Chỉ dùng display: flex; mà không cần dùng @media query

1. Các column có độ rộng bằng nhau
2. Các column có độ rộng khác nhau
3. Column content và column sidebar

### 1. Các column có độ rộng bằng nhau

```css
/* Đối với block cha */
.container {
  display: flex;
}
/* Đối với các block con cấp 1 bên trong */
.container > * {
  flex-basis: 100%;
}
```

### 2. Các column có độ rộng khác nhau

Khi div container còn đủ chỗ:

- Mỗi div con có độ rộng ít nhất là 10em
- Tất cả column nằm dàn ngang

Khi div container không còn đủ chỗ:

- Các column rớt xuống hàng dưới
- Và chiếm đủ 100% độ rộng div container

```css
/* Đối với block cha */
.container {
  display: flex;
  flex-wrap: wrap;
}
/* Đối với các block con cấp 1 bên trong */
.container > * {
  /*
   flex-growth: 1
   flex-shrink: 1
   flex-basis: 10em
   */
  flex: 1 1 10em;
}
```

### 3. Column content và column sidebar

```css
/* Đối với block cha */
.container {
  display: flex;
  flex-wrap: wrap;
}
/* Đối với block content */
.container > *:nth-child(1) {
  /*
   flex-growth: 1
   flex-shrink: 1
   flex-basis: 70%
   */
  flex: 1 1 70%;
  /* 25ch = 25 * 8px */
  min-width: 25 ch;
}
/* Đối với block sidebar */
.container > *:nth-child(2) {
  flex: 1 1 30%;
  min-width: 15 ch;
}
```

## 11. Các pseudo css

### Đổi màu chữ khi quét khối (text selection color)

```scss
::selection {
  background-color: #73248b;
}
```

## 12. Đơn vị đo trong CSS

Giá trị font-size mặc định của các trình duyệt là 16px

### 1. REM

Rem: khi font size của trình duyệt thay đổi, thì giá trị cơ bản 1 rem thay đổi.

VD:
User zoom trình duyệt lên 200%, thì giá trị font-size của thẻ html sẽ tăng lên 200%

=> Rem = Rem \* 2

### 2. EM

Khi cài đặt thuộc tính font-size cho chính nó, hoặc element cha gần nhất, thì giá trị cơ bản của 1 em thay đổi.

Khi dùng @media query, người ta thường dùng đơn vị em

### 3. PX

Nếu user zoom màn hình trình duyệt lên 200% để nhìn thấy rõ chữ, thì với đơn vị px, nó vẫn giữa nguyên kích thước.

Cho nên, người ta hay dùng đơn vị rem hoặc em.

### 4. VW = view port width

Thường dùng trong responsive hình full màn hình từ trái qua phải

### 5. VH = view port height
