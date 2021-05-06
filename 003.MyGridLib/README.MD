# Thư viện CSS: grid
Không phải là thuộc tính display: grid

Mà là tập hợp các class CSS giúp tạo hệ thống lưới cho giao diện website.

Mô tả bài toán:

Content của website nên được đặt trong một khung chứa, khung chứa này sẽ được căn giữa màn hình theo trục X (chiều ngang)

Mặc định độ rộng khung chứa content (grid): chiếm 100% chiều ngang màn hình.

Tuy nhiên, nếu màn hình quá lớn: thì tối đa content chỉ chiếm 1200px; Và căn giữa màn hình theo trục X (chiều ngang)

Ngược lại, khi màn hình quá nhỏ thì độ rộng tối đa của content phải được thu nhỏ lại cho hợp lý.

Do đó, sẽ có các điểm breakpoint như sau:

- Màn hình lớn.       : 1200px (screen: >1239 px)
- Màn hình trung bình : 984px ( 1024 < scrren <= 1239)
- Màn hình nhỏ        : 644px (740px < screen <= 1023>)
- Điện thoại di động. : 100% (mặc định)

Khoảng cách giữa các cột: 
- Margin trái phải: 4px => Row tương ứng sẽ có margin trái phải -4px
- Margin trái phải: 8px => Row tương ứng sẽ có margin trái phải -8px
- Margin trái phải: 12px => Row tương ứng sẽ có margin trái phải -12px

Các class cần css responsive:
```scss
.grid
.wide
.row
.col
.c-0 ... c-12
.m-0 ... m-12
.l-0 ... l-12
```

## 1. GRID

Toàn bộ content chia lưới, sẽ được đặt bên trong một thẻ có class là .grid

Mặc định grid sẽ có width là 100% 
```scss
.grid{
  width: 100%;
  display: block;
}
```
Html tương ứng là 
```html
div.grid
```
Còn việc thay đổi độ rộng của thẻ .grid này tùy theo độ rộng của trình duyệt, là do thẻ .grid này sẽ có thêm 1 class nữa là .wide.

Khi nào .grid đi cùng với .wide nghĩa là sẽ ưu tiên lấy giá trị thuộc tính width được quy định .wide

Html tương ứng khi đó là
```html
div.grid.wide
```
Tóm lại, nếu layout của website, yêu cầu không có full hết màn hình, thì sẽ dùng thêm class .wide
Ngược lại, không phân biệt pc hay mobile mà lúc nào cũng full màn hình hết, thì dùng 1 .grid.

## 2. WIDE
Độ rộng tối đa của hệ thông lưới là 1200px
```scss
.grid.wide{
   max-width: 1200px;
   margin: 0 auto
}
```
Độ rộng của hệ thống lưới khi ở màn hình lớn là 984px
```scss
@media (min-width: 1024px) and (max-width: 1239px) {
  .wide {
    width: 984px;
  }
}
```
Tới đây, nghĩa là màn hình mà lớn hơn 1239px thì wide sẽ là 984px

Màn hình mà còn lớn hơn cả 1240px thì wide sẽ là 1200px

Độ rộng của hệ thống lưới khi ở màn hình trung bình là 644px
```scss
@media (min-width: 740px) and (max-width: 1023px) {
  .wide {
    width: 644px;
  }
}
```
Tóm lại;

Wide  | 100%  | 644px  | 984px  | 1200px
------------- | ------------- | ------------- | ------------- | -------------
screen  | < 740px  | 741px -> 1023px  | 1024px - 1239px  | >= 1240px
Device  | Mobile  | Medium  | Large  | Largest

## 3. ROW và COLUMN
Mỗi 1 ô trong hệ thống lưới gọi là cell.

1 Cell sẽ được xác định bởi ROW và COLUMN.

Trong đó, ROW có nhiệm vụ bao ngoài tất cả COLUMN, để áp dụng thuộc tính display:flex, và COLUMN sẽ trở thành flex item của ROW.

COLUMN sẽ có các class tiền tố đi kèm, để tiến hành tạo CELL.

Ví dụ:
1 ROW và có 3 COLUMN, khi đó, HTML sẽ là 

```html
.grid.wide 
   .row
      .col c-3
```