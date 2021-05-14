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

Bước 1: Tạo thêm thẻ row

```
.container
  .row
    .hexagon*10
```

Bước 2: bỏ thuộc tính display flex ở body

Bước 3: Tạo điểm neo là thẻ container

```css
.container {
  position: relative;
  height: 100vh;
  overflow: hidden;
}
```
