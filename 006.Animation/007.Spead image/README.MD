# Image

## HTML

1 section có 2 side

```
section
  .side#side1
  .side#side2
```

2side chứa image chiếm 100% chiều rộng, chiều cao

Dùng thuộc tính clip-path tạo polygon cho side1

Dùng thuộc tính clip-path tạo polygon cho side2 (lật ngược 2 điểm đầu và cuối của side1)

gán sự kiện scroll cho window: Khi user scroll xuống, thì polygon sẽ di chuyển sang 2 bên tạo cảm giác xé tấm hình.
