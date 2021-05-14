# Hiệu ứng Wavy circle

## HTML

```
body
  .loader
    span*15
```

## CSS

Định dạng cho body: full chiều cao màn hình, màu nền, và canh giữa màn hình item bên trong

```css
body {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  background: #89179e;
}
```

Định dạng cho item .loader

Định dạng chung cho thẻ span thành hình tròn và có animation, xếp chồng lên nhau

```css
.loader span {
  border-radius: 50%;
  border: 2px solid #fff;
  display: block;
  position: absolute;
}
```

Định dạng vị trí cho từng thẻ span theo thứ tự. Mỗi 1 thẻ span thu nhỏ +10px

```css
.loader span:nth-child(1) {
  top: 140px;
  left: 140px;
  right: 140px;
  bottom: 140px;
}
.loader span:nth-child(2) {
  top: 130px;
  left: 130px;
  right: 130px;
  bottom: 130px;
}
.loader span:nth-child(3) {
  top: 120px;
  left: 120px;
  right: 120px;
  bottom: 120px;
}
.loader span:nth-child(4) {
  top: 110px;
  left: 110px;
  right: 110px;
  bottom: 110px;
}
.loader span:nth-child(5) {
  top: 100px;
  left: 100px;
  right: 100px;
  bottom: 100px;
}
.loader span:nth-child(6) {
  top: 90px;
  left: 90px;
  right: 90px;
  bottom: 90px;
}
.loader span:nth-child(7) {
  top: 80px;
  left: 80px;
  right: 80px;
  bottom: 80px;
}
.loader span:nth-child(8) {
  top: 70px;
  left: 70px;
  right: 70px;
  bottom: 70px;
}
.loader span:nth-child(9) {
  top: 60px;
  left: 60px;
  right: 60px;
  bottom: 60px;
}
.loader span:nth-child(10) {
  top: 50px;
  left: 50px;
  right: 50px;
  bottom: 50px;
}
.loader span:nth-child(11) {
  top: 40px;
  left: 40px;
  right: 40px;
  bottom: 40px;
}
.loader span:nth-child(12) {
  top: 30px;
  left: 30px;
  right: 30px;
  bottom: 30px;
}
.loader span:nth-child(13) {
  top: 20px;
  left: 20px;
  right: 20px;
  bottom: 20px;
}
.loader span:nth-child(14) {
  top: 10px;
  left: 10px;
  right: 10px;
  bottom: 10px;
}
.loader span:nth-child(15) {
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}
```

Tạo không gian 3D cho .loader. mặt phẳng tạo góc 90 độ với màn hình, độ sâu là 500px

```css
.loader {
  transform-style: preserve-3d;
  transform: perspective(500px) rotateX(60deg);
}
```

Tạo rule @keyframes animate cho span, dịch chuyển span theo trục Z trong khoảng -100px đến 100px

```css
.loader span {
  animation: animate 3s ease-in-out infinite;
}
@keyframes animate {
  0%,
  100% {
    transform: translateZ(-100px);
  }
  50% {
    transform: translateZ(100px);
  }
}
```

Thêm delay thời gian thực hiện animation cho từng thẻ span. Mỗi thẻ span tăng dần 0.1s tính từ span 15 là 0 giây.
