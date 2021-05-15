# 7 Styles Box Shadow

## HTML

Tạo ra 1 thẻ cha container

Có 7 thẻ con .box

Mỗi thẻ con có thêm class shadow1 đến shadow7

## CSS

Reset css

Body full chiều cao và center content.

```css
body {
  display: flex;
  justify-content: center;
  align-items: center;

  min-height: 100vh;
  background-color: #2ec194;
}
```

.Container hiển thị flex theo cột.

```css
.container {
  display: flex;
  flex-direction: column;
}
```

Từng .box có chiều rộng, chiều cao, margin trên dưới, màu nền trắng, và center content.

```css
.container .box {
  position: relative;
  width: 300px;
  height: 200px;
  margin: 40px 0;
  background-color: #fff;

  font-size: 2.5em;
  display: flex;
  justify-content: center;
  align-items: center;
}
```

Công thức box-shadow

```
box-shadow: x y blur color_rgba
```

Nếu chỉ cài đặt giá trị x,y và màu rgba đổ bóng thì bóng sẽ đặc, như 1 hình vẽ. Nên có thêm chỉ số blur để làm nhòe nhẹ nhẹ mới có cảm giác là bóng đổ.

### Shadow 1: tạo cảm giác nổi lên trên mặt phẳng body

### Shadow 2: tạo cảm giác trang vở sắp được lật ở góc bên phải

Dùng pseudo before

```css
.shadow2 {
  content: "";
  position: absolute;
  bottom: 10px;
  left: 10%;
  width: 90%;
  height: 50px;
  background-color: rgba(0, 0, 0, 0.3);
  transform-origin: left;
  transform: skewY(5deg);
  z-index: -1;
}
```

### Shadow 3:tạo cảm giác trang vở sắp được lật ở 2 bên trái, phải

### Shadow 4: tạo cảm giác hình nổi lên có bóng ở bên dưới

Dùng pseudo before tạo ra 1 hình eclip ở bên dưới hình chính.

```css
.box.shadow4:before {
  content: "";
  position: absolute;
  bottom: -50px;
  left: 5%;

  width: 90%;
  height: 20px;

  filter: blur(10px);
  background-color: rgba(0, 0, 0, 0.3);
  border-radius: 50%;

  z-index: -1;
}
```

### Shadow 5: Tạo cảm giác có độ sâu phía sau

Dùng pseudo before tạo 1 hình phụ ở phía sau, và filter blur tạo cảm giác đó là bóng đổ.

```css
.box.shadow5:before {
  content: "";
  position: absolute;
  bottom: -15%;
  left: 5%;

  width: 90%;
  height: 90%;

  filter: blur(10px);
  background-color: rgba(0, 0, 0, 0.3);

  z-index: -1;
}
```

### Shadow 6: Dùng 1 cặp giá trị box shadow để tạo cảm giác đó là nút bấm

Giá trị 1: tạo hình bóng đổ cạnh trái trên

Giá trị 2: tạo hình bóng đổ cạnh dưới phải

```css
.box.shadow6 {
  background-color: #2ec194;
  border-radius: 15px;
  box-shadow: -15px -15px 15px rgba(255, 255, 255, 0.2), 15px 15px 15px rgba(0, 0, 0, 0.1);
}
```

### Shadow 7: Dùng 2 cặp giá trị box shadow để tạo cảm giác nút bấm bị ẩn vào trong

```css
.box.shadow7 {
  background-color: #2ec194;
  border-radius: 15px;
  box-shadow: -15px -15px 15px rgba(255, 255, 255, 0.2), 15px 15px 15px rgba(0, 0, 0, 0.1),
    inset -5px -5px 5px rgba(255, 255, 255, 0.2), inset 5px 5px 5px rgba(0, 0, 0, 0.1);
}
```
