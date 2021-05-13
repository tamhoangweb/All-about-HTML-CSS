# Layout Grid

Chia layout nhanh với thuộc tính display: grid

## Cài đặt thuộc tính grid cho body

```scss
body {
  display: grid;
  grid-template-rows: 10em 50vh auto 10em;
  grid-template-columns: 1fr 5fr 2fr 1fr;
  grid-template-areas:
    "header header header header"
    "hero hero hero hero"
    ". main sidebar ."
    "footer footer footer footer";
}
```

hoặc, cách viết tắt

```scss
body {
  display: grid;
  grid-template:
    "header header header header" 10em
    "hero hero hero hero" 50vh
    ". main sidebar ." auto
    "footer footer footer footer" 10em / 1fr 5fr 2fr 1fr;
}
```

Cài đặt minmax cho cột thứ 2 (main) và cột thứ 3 (sidebar)

```scss
body {
  display: grid;
  grid-template:
    "header header header header" 10em
    "hero hero hero hero" 50vh
    ". main sidebar ." auto
    "footer footer footer footer" 10em / 1fr minmax(30em, 5fr) minmax(15em, 2fr) 1fr;
}
```

## Cài đặt thuộc tính grid-area cho các item

```scss
header {
  grid-area: header;
}
.hero {
  grid-area: hero;
}
main {
  grid-area: main;
}
aside {
  grid-area: sidebar;
}
footer {
  grid-area: footer;
}
```

## CSS cho header, footer

Các thuộc tính:

- Màu nền
- Màu chữ
- Căn giữa các phần tử theo chiều ngang + dọc

```scss
header,
footer {
  background-color: $black;
  color: $yellow;
  display: flex;
  justify-content: center;
  align-items: center;
}
```

Chỉnh font cho header-title, footer-title:

```scss
.header-title,
.footer-title {
  @include font-alt($font-size: $fs-h2, $color: $yellow);
}
```

## CSS cho hero

Các thuộc tính:

- hình nền
- căn giữa các item theo chiều dọc và chiều ngang
- Chỉnh font và màu cho hero-title, và hero-subtitle

```scss
.hero {
  grid-area: hero;
  background-image: url("https://s3-us-west-2.amazonaws.com/s.cdpn.io/308367/gridarea-hero-bg.jpg");
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.hero-title {
  @include font-alt($fs-xl);
  margin: 0;
}
.hero-subtitle {
  @include font-base($font-size: $fs-h2, $color: $white);
  margin: 0;
}
```

## CSS cho sidebar

Các thuộc tính:

- Màu nền $dark-gray
- Khoảng cách 2 bên

## Grid layout cho card tin tức

### 1. Đặt tên cho các grid item

```scss
.card-img {
  grid-area: img;
}
.card-title {
  grid-area: title;
}
.card-content {
  grid-area: content;
}
```

### 2. Định grid layout cho grid container

```scss
.card {
  display: grid;
  grid-template-columns: 1fr 3fr;
  grid-template-rows: min-content auto;
  grid-template-areas:
    "img title"
    "img content";
}
```

HOẶC viết tắt:

```scss
.card {
  display: grid;
  grid-template:
    "img title" min-content
    "img content" auto / 1fr 3fr;
}
```

### 3. CSS thêm cho card container

```

```
