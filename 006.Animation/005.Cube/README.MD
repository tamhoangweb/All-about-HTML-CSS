# Cube

## Cách tạo khối 3D

là 3 thẻ có thuộc tính clip-path tương ứng là các mặt khác nhau của hình hộp.

thẻ thứ 2 cạnh bên, có thêm 1 pseudo before nằm đè lên và màu sạm đi, tạo cảm giác thiếu sáng.

### Các bước làm

#### HTML

```
body
  .container
    .row
      .cube
        span*3
```

#### CSS

Reset css, và cho body chiếm hết chiều cao màn hình trình duyệt, đồng thời display flex, để căn giữa cube.

```css
body {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #ffeb3b;
}
```

Để các mặt của cube nằm chồng lên nhau, thì thẻ cha của nó phải có position là relative, và bản thân nó phải có position là absolute

```css
.cube {
  position: relative;
  width: 150px;
  height: 150px;
}
.cube span {
  position: absolute;
  top: 0;
  left: 0;
  display: block;
  width: 100%;
  height: 100%;
  background-color: #fff;
}
```

Tạo clip-path cho từng mặt của cube

```css
.cube span:nth-child(1) {
  clip-path: polygon(50% 0%, 100% 25%, 50% 50%, 0 25%);
}
.cube span:nth-child(2) {
  clip-path: polygon(0% 75%, 50% 100%, 50% 50%, 0 25%);
}
.cube span:nth-child(3) {
  clip-path: polygon(100% 75%, 50% 100%, 50% 50%, 100% 25%);
}
```

Tạo màu sậm cho những mặt thiếu sáng bằng pseudo before

```css
.cube span:nth-child(2):before {
  content: "";
  display: block;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.1);
}

.cube span:nth-child(3):before {
  content: "";
  display: block;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
}
```

## Cách tạo nhiều khối 3D tràn đầy màn hình

### HTML

```
Một dãy cube nằm ngang
(.cube>span*3)*12
```

### CSS

Cho thẻ body full chiều cao

```css
body {
  min-height: 100vh;
}
```

Cho thẻ .container full màn hình, và ẩn những pixel dư.

```css
.container {
  position: relative;
  height: 100vh;
  overflow: hidden;
}
```

Cho các cube nằm thành hàng ngang:

- .row có display flex thì các item bên trong sễ xếp ngang.

```css
.row {
  position: relative;
  display: inline-flex;
}
```

Copy 1 row thành nhiều row

```
Dãy thứ 2
(.cube>span*3)*12
....

```

Cho từng dãy cube xếp chồng và xem kẽ nhau một chút bằng thuộc tính margin-top và margin-left giá trị âm

```css
.row {
  position: relative;
  display: inline-flex;
  margin-top: -45px;
}
.row:nth-child(even) {
  margin-top: -45px;
  margin-left: -75px;
}
```

## Hiệu ứng khi hover khối cube sẽ đổi màu và có cảm giác nối đuôi nhau

Để tạo cảm giác đổi màu nối đuôi nhau cần cài thuộc tính transition ở cả 2 selector( selector mặc định, và selector khi hover qua)

```css
/* selector mặc định */
.cube span {
  position: absolute;
  top: 0;
  left: 0;
  display: block;
  width: 100%;
  height: 100%;
  background-color: #fff;
  transition: 2s;
}
/* selector hover */
.cube:hover span {
  transition: 0s;
  background-color: #03a9f4;
}
```

Tạo thêm animation đổi màu kiểu hue-rotate

```css
.cube span {
  animation: animate 10s linear infinite;
}
@keyframes animate {
  0% {
    filter: hue-rotate(0deg);
  }
  100% {
    filter: hue-rotate(360deg);
  }
}
```
