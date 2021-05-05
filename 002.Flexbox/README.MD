# Flexbox 
## 1.navbar layout
item con 1: menu

item con 2: đăng nhập

Dàn hàng ngang + tràn đều sang 2 bên trái phải 

SCSS cho div container
```scss
.nav {
  display: flex;
  justify-content: space-between;
}
```

## 2. Form layout
Thuộc tính giúp item con chiếm tối đa khoảng trống còn lại của flex cha.
```scss
flex: 1;
```

## 3. Column layout 
Chia độ rộng của các columns bằng thuộc tính flex.

Giá trị của flex càng lớn thì độ rộng chiếm càng nhiều.

## 4. Card layout 
Các cards chiếm độ rộng bằng nhau, và có khoảng cách ở giữa các cards

Dùng thuộc tính justify-content cho flex cha 

Dùng thuộc tính flex-basis cho các flex con

```scss
div.container{
  display: flex;
  justify-content: space-around;
}

div.card {
  /* tổng độ rộng chiếm của div cha là 90%, còn 10% là tạo khoảng cách giữa các item */
  flex-basis: 30%;
}
```

## 5. Căn giữa theo cả 2 trục XY (giữa màn hình)
Div con muốn center theo cả 2 trục XY, chỉ cần thuộc tính margin có giá trị là auto 
```scss
.center-item{
  margin: auto;
}
```

## 6. Chart Layout
Chart container phải có thuộc tính chiều cao (height: 320px).

Chart container phải có thuộc tính display:flex. 

Item có chiều cao = với giá trị %

```scss
.chart-item{
  /* percent là biến nội bộ của chart-item, được tạo ở html */
  height: var(--percent)
}
```

Để giữa các chart item, có khoảng cách thì dùng thuộc tính justify-content

Để dồn hết các item, nằm ở cạnh dưới của container thì dùng thuộc tính align-item
```scss
.chart-container {
  height: 320px;
  display: flex;
  justify-content: space-around;
  align-items: flex-end;
}
```

## 7. tạo animation cho chart item
Tạo rule @keyframe cho chiều cao của chart item sẽ hiển thị từ từ trong 3 giây.
```scss
@keyframe growth {
  from {
    height: 0;
  }
  to {
    height: var(--percent);
  }
}
```
Dùng @keyframe bằng thuộc tính animation
```scss
.chart-item{
  /* thời gian chạy từ from đến to là 2 giây */
  animation: growth 2s ease-in;
}
```

## 8. Layout dùng 2 lần flex
Flex cho div cha 

Flex cho div con (có 2 item bên trong)

Dùng thuộc tính flex: 1 để chia đều độ rộng 
```scss
.item{
  flex: 1;
}
```

Dùng thuộc tính flex-direction để đảo vị trí 2 item;
```scss
.container {
  display: flex;
  flex-direction: row-reverse;
}
```