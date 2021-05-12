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
