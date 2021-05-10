# Tạo Header dễ dàng với Flexbox và thuộc tính margin

1. HTML

```
header
  nav.nav
    ul.nav__list
      li > a > {Home}
      li > a > {About}
      li > a > {Blog}
      li > a > {Pricing}
      li > a > {Contact}
      li > a > {Login}
      li > a > {Sign up}
```

2. CSS

```
header {
  display: flex
}
```

```
nav__list{
  display: flex
}
```

```
header {
  display: block
}
```
