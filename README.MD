# Cách tổ chức 1 file CSS 
Phân chia loại CSS 

Có bảng đề mục loại CSS

## Ví dụ 
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

## Các CSS nên dùng 
```CSS
:focus{
  outline: none;
}

```

# Cách cách selector element để CSS (tên gọi khác: CSS selectors)
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

Dựa vào thuộc tính data-*
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

# CSS tricks 
## 1.Tooltip
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

## 2. :is
Các selectors sử dụng: 
```css
/* CSS cho các element là li, con của ul hoặc ol, và ol hoặc ul này là con của ul hoặc ol khác */
:is(ul, ol) :is(ul, ol) li
```

## 3. Tăng biến đếm trong CSS
### Bài toán 1:
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

### Bài toán 2: Dùng counters syntax thay đổi cách hiển thị số của order list 
Mặc định order list hiển thị là 
```html
1. First item
2. Second item
   1. item
   2. item
```
Đổi thành kiểu đề mục sách
```html
1. First item
2. Second item
   1.1. item
   2.1. item
```
Bước 1: tắt hiển thị số mặc định của list
```css
li { 
  list-style: none
}
```

Bước 2: cài property content mới cho selector li:before
```css
li:before { 
  content: counters(outline, '.') ". ";
  counter-increment: outline;
}
```

## 4.Flexbox Gap
Property gap thường được dùng trong display flex. Tuy nhiên nhiều trình duyệt chưa hỗ trợ thuộc tính này, ví dụ: safari trên iOS.

Giải pháp thay thế là dùng margin với cách selector đặc biệt như sau:
```css
.flex {
   display: flex
}
.flex > * {
   margin-right: 10px;
}

/* tắt margin của phần tử cuối cùng trong element cha flex */
.flex > *:last-child {
   margin-right: 0;
}
```

## 5.Value conic-gradient dùng để tạo màu

```css
background: conic-gradient(
   red .25turn,         //từ 0 đến 25%
   blue .25turn .5turn, //từ 25% đến 50%
   green .5turn         //từ 50% đến 100%
);
```