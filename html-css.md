# HTML/CSS Style Guide
Based on [Google HTML/CSS Style Guide](https://google.github.io/styleguide/htmlcssguide.xml)

### Quy tắc chung về style
#### Protocol
Lược bỏ protocol (`http:`, `https:`) khi nhúng resource

```html
<!-- Not recommended -->
<script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>

<!-- Recommended -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```

```css
/* Not recommended */
.example {
  background: url(http://www.google.com/images/example);
}

/* Recommended */
.example {
  background: url(//www.google.com/images/example);
}
```

### Quy tắc chung về format
#### Indentation
Sử dụng 2 dấu cách cho mỗi mức. Không sử dụng tab hoặc kết hợp tab và dấu cách cho indentation.
```html
<ul>
  <li>Fantastic</li>
  <li>Great</li>
</ul>
```
```css
.example {
  color: blue;
}
```

#### Capitalization
Sử dụng dạng chữ thường. Áp dụng đối với: tên HTML element, attribute, giá trị của attribute (trừ `text/CDATA`), CSS selector, property và giá trị của property (trừ trường hợp string).
```html
<!-- Not recommended -->
<A HREF="/">Home</A>

<!-- Recommended -->
<img src="google.png" alt="Google">
```
```css
/* Not recommended */
color: #E5E5E5;

/* Recommended */
color: #e5e5e5;
```

