# Flexbox Landing page easy

## Tiêu đề h1 ấn tượng

```scss
h1 {
  font-size: 5em;
  color: $green;
  text-transform: uppercase;
  letter-spacing: 15px;
  outline: 3px solid $white;
  outline-offset: 0.25em;
  display: inline-block;
  margin: 0.25em 0 0.5em;
  span {
    font-weight: 300;
  }
}
```

## Background blend mode đẹp

```scss
.hero {
  background-color: #444;
  background-image: url(//unsplash.it/1000/600);
  background-blend-mode: multiply;
  background-size: cover;
  height: 100vh;
  padding: 1em;
  color: $white;
}
```

## Căn giữa toàn bộ banner của khung nhìn hero

```scss
.hero {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
```

## Căn giữa 3 khối đều nhau của sales-points

```scss
.sales-points {
  display: flex;
}
```

## Tạo khoảng cách giữa 3 khối

```scss
.sale-point {
  flex-basis: 30%;
}

.sales-points {
  display: flex;
  justify-content: space-between;
}
```

## Khi màn hình desktop thì flex-direction là row (chia làm 3 phần nằm ngang). Khi màn hình mobile thì flex-direction là column (Mỗi sales-point là 1 dòng)

```scss
.sales-points {
  flex-direction: column;
}
@media (min-width: 40rem) {
  .sales-points {
    flex-direction: row;
  }
}
```

## Cho phần cta chiếm 50%, và nằm bên phải

```scss
.cta {
  display: flex;
  justify-content: flex-end;
}
.cta-text {
  flex-basis: 50%;
}
```

## Khi màn hình mobile, thì cta chiếm 100%

```scss
.cta-text {
  @media (min-width: 40rem) {
    flex-basis: 50%;
  }
}
```
