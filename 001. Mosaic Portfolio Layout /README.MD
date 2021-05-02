# 001. Mosaic Portfolio Layout 
Số cột: 5

Số dòng: 6

Các loại khối item:
- Square
- Large Square 
- Small Square
- Tall
- Wide

## 1. Chuẩn bị HTML
```html
.sidebar
   .logo > Awesome <span> Portfolio </span>
   nav
     a.nav-item > Home
     a.nav-item > About
     a.nav-item.active > Portfolio
     a.nav-item > Contact

.main-content
   .portfolio
     .portfolio-item.square > one
     .portfolio-item.large-square > two
     .portfolio-item.square > three
     .portfolio-item.small-square > four
     .portfolio-item.tall > five
     .portfolio-item.wide > six
```