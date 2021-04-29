# Các thẻ HTML trông khó nhưng mà có sẵn
## 1. Danh sách thẻ trong form 
Bộ thẻ tạo khung form
```html
form > fieldset > legend
```

Bộ thẻ tạo danh sách dữ liệu cho input:
- Không giới hạn số dòng dữ liệu
- Có sẵn tính năng: khi gõ 1 ký tự bất kỳ sẽ hiển thị gợi ý dữ liệu.
```html
<input list="color-list" type="text">
<datalist id = "color-list">
   <option value="Red">
   <option value="Yellow">
<datalist>
```

Thẻ input tạo ra bảng màu cho user chọn
```html
<input type="color" >
```

Thẻ input tạo ra bảng chọn thời gian
```html
<input type="time" >
```

Bộ thẻ tạo ra thanh tiến trình khi upload file
```html
<div>
   <progress value="50" max="100">50</progress> %
</div>
```

## 2. Open graph: làm chủ cách hiển thị khi chia sẻ đường link website lên các trạng mạng xã hội
Bộ các property của thẻ meta
```html
property="og:site_name"
property="og:url"
property="og:title"
property="og:image"
property="og:image:width"
property="og:image:height"
property="og:description"
property="og:type"
property="og:video:url"
```
## 3. thẻ thu nhỏ xuống dưới sub, thẻ thu nhỏ lên trên sup

## 4. Bộ thẻ picture giúp responsive hình
Cùng 1 vị trí trên website, hiển thị 1 tấm hình với điều kiện:
- Khi màn hình > 900px thì load hình 1
- Khi màn hình <= 900px thì load hình 2 
- Nếu trình duyệt hỗ trợ loại hình .webp thì load hình webp
```html
<picture>
  <source srcset="hinh.webp" type="image/webp">
  <source srcset="hinh1.png" media="(min-width: 900px)" >
  
  <img src="hinh2.png">
</picture>
```
## 5. Template
Tạo ra 1 đoạn mã html bên trong thẻ template
```html
<template>
   <h2> Tiêu đề 2</h2>
</template>
```
Trình duyệt mặc định sẽ không hiển thị đoạn html này.
Dùng javascript để hiển thị đoạn html này.
```javascript
const template = document.querySelector('template')
const content = template.content.cloneNode(true)
document.body.append(content)
```