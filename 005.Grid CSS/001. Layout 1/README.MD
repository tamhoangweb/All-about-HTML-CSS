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
