# GRID

## Các thuộc tính dùng trong thẻ cha (container):

```css
display: grid;
```

### 1. chia layout theo chiều dọc (column)

```css
grid-template-columns: 1fr 1fr 1fr;
```

### 2. chia layout theo chiều ngang (row)

```css
grid-template-rows: 200px 400px 200px 200px;
```

### 3. Tạo các gap

#### gap column

```css
grid-column-gap: 10px;
```

#### gap row

```css
grid-row-gap: 10px;
```

### 4. Độ cao auto

```css
grid-auto-rows: 160px;
```

### 5. Tự động lấp đầy ô trống (grid spots trống)

```css
display: grid;
grid-auto-flow: dense;
```

### 6. Căn giữa tracks theo trục X: justify-content

```css
display: grid;
grid-template-columns: repeat(3, 100px);
justify-content: center;
```

### 7. Căn giữa items theo trục X: justify-items

Lưu ý: từng item con có thể tự căn giữa cho content của mình, bằng thuộc tính justify-self

## Các thuộc tính dùng trong thẻ con (item):

### Đường line trong grid

- Bắt đầu đếm từ 1 ở cạnh trái đầu tiên: column line
- Bắt đầu đếm từ 1 ở cạnh trên đầu tiên: row line
- Line cuối là: -1
- Các item có thể được sắp xếp vị trí hiển thị tùy ý theo 2 loại đường line này.

### Chỉ định số cột mà item chiếm lấy

item1 chiếm 2 cột, bắt đầu từ line số 1, kết thúc ở line số 3

```css
.item1 {
  grid-column: 1 / 3;
}
```

item2 chiếm từ line 3 đến line 7 => số cột chiếm là 4

```css
.item2 {
  grid-column: 3 / 7;
}
```

### Chỉ định số dòng mà item chiếm lấy

item2 chiếm từ row line 2 đến row line 4 => số dòng chiếm là 2

```css
.item2 {
  grid-row: 2 / 4;
}
```

## Các hàm có thể sử dụng

### 1. repeat(số lần lặp, đơn vị lặp)

VD: tạo 3 cột, mỗi cột chiếm 1 fr

```css
grid-template-columns: repeat(3, 1fr);
```

### 2. minmax(đơn vị min, đơn vị max)

VD: chiều cao của ô nhỏ nhất là 200px

```css
grid-template-rows: repeat(3, minmax(200px, auto));
```

## Các đơn vị và từ khóa có thể dùng

### 1. span

- span: mở rộng
  VD: item3 mở rộng 3 lần

```css
grid-column: span 3;
```

hoặc

```css
grid-colum: 1 / 4;
```

### 2. 80% + 20% != 8fr 2fr

100% + 20px thì tổng độ rộng của lưới sẽ tràn ra ngoài 20px

(8+2)fr + 20px thì tổng độ rộng của lưới vẫn được chia là 8phần và 2 phần nhưng ko bị tràn ra ngoài 20px

```css
grid-gap: 20px;
grid-template-columns: 8fr 2fr;
```

```css
grid-gap: 20px;
grid-template-columns: 80% 20%;
```

Kết luận: Nên dùng fr.
