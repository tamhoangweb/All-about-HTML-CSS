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

## Cách cách selector element để CSS (tên gọi khác: CSS selectors)
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

