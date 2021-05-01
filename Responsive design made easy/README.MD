# Responsive design made easy
Nguyên tắc để resonpsive dễ dàng:
- Ở bản mobile: dùng flex-direction: column
- Ở bản desktop: dùng flex-direction: row
- Để các column có kích thước đều nhau đều = 100%
- Không dùng flex-gap để tạo khoảng cách giữa các column. 
- Image có max-width = 100%
## Các properties, và value sử dụng trong file css
```css
/* thẻ */
:root
.split > * + *

/* thuộc tính */
margin-inline
--clr-primary

flex-direction
flex-basis

/* value */
flex

/* hàm logic trong css */
var()
min()

/* đơn vị */
1.1325rem
1em
line-height: 1.6
max-width: 100%

```
## Đọc hiểu 1 bản thiết kế về các yếu tố 
1. Khối 
2. Màu nền 
3. Màu chữ 
4. Font chữ

## Lên file html chuẩn:
1. Dùng các thẻ có ý nghĩa + các thẻ nào có thẻ alt thì điền đầy đủ.
Ví dụ: 
```html
<header>
/* Mỗi trang html, chỉ có 1 thẻ h1, và ở trên cùng so với các thẻ heading khác. */
   <h1> Responsive layout don't have to be a struggle </h1>
<header>
```

2. Mỗi component sẽ được bao bởi 1 hoặc 2 thẻ:
  1 thẻ giúp canh lề 2 bên 
  1 thẻ giúp chia flex (nếu có dùng flex)
```html
<section>
  <h2> Quality Designs </h2>
  <div class="split">
     (div>p)*2
  </div>
</section>
```
3. Đặt tên các class đã được hình dung trước từ việc đọc hiểu bản thiết kế

    3.1 Class dùng để chia layout 

    3.2 Class dùng để style content private

    3.3 Class dùng để style utility

### Kết quả 
Bước 1: Lên các thẻ, và nội dung mockup
```html
header 
   p>lorem3
   h1 

section
   h2|"Quality Designs"
   .split
      div>p>lorem25
      div>p>lorem25

section 
   .split
      div
        h2|"Made custom for you"
        p>lorem25
      div
        img|alt=""
section
   .split
      div
        img|alt=""
      div
        h2|"Created with care"
        p>lorem25
```
Bước 2: Đặt tên class cho các thẻ từ sự đọc hiểu design ban đầu
1. Class dùng để chia layout
```html
div.split
```
2. Class dùng để style riêng cho element 
```html
header.bg-light
section.bg-dark
section.bg-primary
```
3. Class dùng để style chung cho element
```html
.text-center
```

## Lên file CSS
1. Các reset 
2. Các biến lưu trữ màu, và font 
3. Style cho thẻ body
4. Style cho các thẻ heading
5. Style cho các class màu nền và màu chữ trên màu nền đó
6. Style cho thẻ bao component.
7. Style cho các class công cụ
8. Style các khoảng cách giữa các element
9. Style cho image
10. Layout
11. Responsive: css cho màn hình desktop


### 1. Các reset 
```css
*,
*::before,
*::after{
  box-sizing: border-box
}

body,
h1, h2, h3,
p {
  margin: 0;
}
```

### 2. Các biến lưu trữ màu, và font 
Chia màu theo độ sáng

Chia font theo độ đậm, dày của font
```css
:root {
   --clr-primary-200: #F3EED9;
   --clr-primary-400: #824936;

   --clr-neutral-100: #FFF;
   --clr-neutral-900: #222C2A;

   --ff-primary: 'Roboto', sans-serif;
   --ff-accent: 'Playfair Display', serif;
}
```

### 3. Style cho thẻ body
Chính là style cho toàn bộ font căn bản của website.

Những nơi nào có font đặc biệt sẽ được định nghĩa sau.
```css
font-family: var(--ff-primary);
font-weight: 400;
/* 1rem = 16px; 1.3125 = 21px */
font-size: 1.3125rem;
line-height: 1.6;
```

### 4. Style cho các thẻ heading
File html dùng thẻ heading nào, thì style cho thẻ heading đó, không làm dư
```css
h1,
h2,
h3 {
  color: var(--clr-primary-400)
  font-family: var(--ff-accent);
  font-weight: 900;
  line-height: 1;
}
```

### 5. Style cho các class màu nền và màu chữ trên màu nền đó

1. Style cho màu nền và màu chữ cơ bản
```css
.bg-light { 
   background-color: var(--clr-primary-200); 
}

/* nền tối và chữ màu trắng */
.bg-primary { 
   background-color: var(--clr-primary-400); 
   color: var(--clr-neutral-100);
}
.bg-dark { 
   background-color: var(--clr-neutral-900); 
   color: var(--clr-neutral-100);
}
```
2. Style cho màu chữ tiêu đề theo class màu nền
```css
.bg-primary h2,
.bg-dark h2 {
   color: var(--clr-primary-200)
}
```
### 6. Style cho thẻ bao component:
Định nghĩa khoảng cách 2 bên lề 

Độ rộng của component: tối đa là 70.5rem, còn dưới 70.5 rem, thì = 90% của body. 


```css
header,
section{
  padding: 3rem 0;
}

.container {
  margin-inline: auto;
  width: min(90%, 70.5rem)
}
```

Thêm modifier cho class container, dùng cho trường hợp tiêu đề quá dài mà muốn 
```css
.container--narrow{
   max-width: 34rem;
}
```
### 7. Style cho các class công cụ
```css
.text-center{
   text-align: center
}
```

### 8. Style các khoảng cách giữa các element
Khoảng cách giữa các element thường rất đều nhau, mình sẽ style cho các element nào có chung khoảng cách.
```css
h2,
h3,
p {
  margin-bottom: 1em
}
```

### 9. Style cho image
```css
display: block
max-width: 100%
```
### 10. Layout 
```css
.split {
   display: flex;
   flex-direction: column;
}
```

### 11. Responsive: css cho màn hình desktop
Responsive cho element nào, thì viết @media ngay bên dưới đoạn css cho element đó.

1. Các column nằm ngang hàng nhau

2. Độ rộng các column bằng nhau

3. Khoảng cách giữa các column là 2em

4. Padding ở các section là 7rem, so với 4rem ở mobile
```css
@media (min-width: 40em) {
   .split {
      flex-direction: row;
   }
   /* để tất cả các column có độ rộng bằng nhau */
   .split > *{
      flex-basis: 100%;
   }
  /* tạo khoảng cách giữa các column */
  .split > * + * {
      margin-left: 2em
   }
}
```

```css
header,
section {
  padding: 4rem 0
}

@media (min-width: 40rem) {
   header,
   section {
       padding: 7rem 0
   }
}
```
