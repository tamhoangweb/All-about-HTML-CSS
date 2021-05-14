# Hexagon

## Tạo hình lục giác

### Cách 1: Dùng border

### Cách 2: Dùng thuộc tính css clip-path

https://bennettfeely.com/clippy

```css
clip-path: polygon(25% 0%, 75% 0%, 100% 50%, 75% 100%, 25% 100%, 0% 50%);
```

## Tạo hiệu ứng đổi màu

Bước 1: tạo 1 thẻ container chứa hình hexagon

Bước 2: Tạo thuộc tính animation cho thẻ container

```css
.container {
  animation: animate 4s linear infinite;
}
```

Bước 3: Tạo keyframe cho thuộc tính animation

Hiệu ứng chuyển màu dùng thuộc tính filter

```css
@keyframes animate {
  0% {
    filter: hue-rotate(0deg);
  }
  100% {
    filter: hue-rotate(360deg);
  }
}
```

Lưu ý: để màu đẹp => đổi background color của hình lục giác #0F0

## Mouse hover => hexagon đổi màu

### 1. Tạo nhiều hexagon xếp thành hình tổ ong

#### Bước 1: Tạo thêm thẻ row

```
.container
  .row
    .hexagon*16
```

#### Bước 2: Bỏ thuộc tính display flex ở body

```css
body {
  background: #000;
}
```

#### Bước 3: Tạo css cho thẻ .container

```css
.container {
  height: 100vh;
  overflow: hidden;
}
```

#### Bước 4: Tạo css cho thẻ .row

```css
.row {
  display: inline-flex;
  margin-top: -32px;
  margin-left: -50px;
}
.row:nth-child(even) {
  margin-left: 1px;
}
```

#### Bước 5: Chỉnh lại css cho thẻ .hexagon

Đổi màu nền

```css
.hexagon2 {
  margin: 1px;
  width: 100px;
  height: 110px;
  background: #111;
  clip-path: polygon(50% 0%, 100% 25%, 100% 75%, 50% 100%, 0% 75%, 0% 25%);
}
```

### 2. Tạo một nửa - kiểu thiếu sáng cho hexagon

Cho thẻ .hexagon2 có position relative

```css
.hexagon2 {
  position: relative;
}
```

Cho thẻ pseudo .hexagon2:before có bg chiếu sáng

```css
.hexagon2:before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 50%;
  height: 100%;
  pointer-events: none;
  background: rgba(255, 255, 255, 0.02);
}
```

### 3. Tạo hiệu ứng khi hover qua hexagon

Gắn thuộc tính transition là 2s cho hexagon

```css
.hexagon2 {
  transition: 2s;
}
```

Khi hover qua hexagon, thì hexagon đổi màu background

```css
.hexagon2:hover {
  background: #0f0;
}
```

Tăng thời gian mất đi hiệu ứng hover, bằng cách thêm thuộc tính transition là 0s

```css
.hexagon2:hover {
  transition: 0s;
}
```
