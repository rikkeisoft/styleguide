# HTML/CSS Style Guide
Based on [Google HTML/CSS Style Guide]
(https://google.github.io/styleguide/htmlcssguide.xml)

### Quy tắc về style chung
#### Protocol
Khi nhúng resource từ trang bên ngoài, nếu resource tồn tại với cả 2 protocol `https:` & `http:` thì:
- Không dùng `http:`. Chỉ dùng `https:`.
- Có thể lược bỏ protocol (`http:`, `https:`) để trình duyệt tự động detect protocol của resource, tránh được vấn đề về "mixed-content".

*Tham khảo:* [MDN](https://developer.mozilla.org/en-US/docs/Security/MixedContent/How_to_fix_website_with_mixed_content)

```html
<!-- Not recommended -->
<script src="http://www.google.com/js/gweb/analytics/autotrack.js"></script>

<!-- Recommended -->
<script src="https://www.google.com/js/gweb/analytics/autotrack.js"></script>
<!-- or -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```

```css
/* Not recommended */
.example {
  background: url(http://www.google.com/images/example);
}

/* Recommended */
.example {
  background: url(https://www.google.com/images/example);
}
/* or */
.example {
  background: url(//www.google.com/images/example);
}
```

### Quy tắc về format chung
#### Indentation
Sử dụng 2 dấu cách cho mỗi mức. Không sử dụng tab hoặc kết hợp tab và dấu cách
cho indentation.

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
Sử dụng dạng chữ thường. Áp dụng đối với: tên HTML element, attribute,
giá trị của attribute (trừ `text/CDATA`), CSS selector, property và giá trị của
property (trừ trường hợp string).

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

#### Trailing Whitespace
Xoá bỏ các khoảng trắng thừa cuối dòng.

```html
<!-- Not recommended -->
<p>What?_ 

<!-- Recommended -->
<p>Yes please.
```

### Quy tắc về meta chung
#### Encoding
Sử dụng UTF-8 (no BOM). Chỉ định encoding cho các file HTML bằng `<meta charset="utf-8">`.
Không chỉ định encoding cho các file style sheet vì chúng mặc nhiên dùng UTF-8.

#### Comment
Viết comment nếu thấy cần thiết (tuỳ thuộc vào mức độ phức tạp của dự án).

#### Đánh dấu Todo
Đánh dấu việc cần làm (todo) với keyword `TODO`   
Có thể thêm username, email trong ngoặc: `TODO(username <email>)`   
Thêm nội dung cần làm sau dấu hai chấm: `TODO: action item`

```html
{# TODO(john.doe): revisit centering #}
<center>Test</center>

<!-- TODO: remove optional tags -->
<ul>
  <li>Apples</li>
  <li>Oranges</li>
</ul>
```

### Quy tắc về HTML style
#### Document Type
Sử dụng HTML5 cho tất cả các file HTML: `<!doctype html>`.   
Không sử dụng XHTML.   
Không đóng các void element, ví dụ: không viết `<br />`, hãy viết `<br>`.

Các void elements:   
`area, base, br, col, command, embed, hr, img, input, keygen, link, meta, param, source, track, wbr`

#### HTML Validity
Viết code HTML đúng chuẩn nếu có thể.
Có thể sử dụng [W3C Markup Validation Service](http://validator.w3.org/) để validate.

#### Semantic (ngữ nghĩa)
Sử dụng các element đúng với mục đích mà chúng được tạo ra.   
Ví dụ: các heading element (h1, h2, h3, ...) cho các mức tiêu đề, `p` cho đoạn văn,
`a` cho anchor (điểm neo).

```html
<!-- Not recommended -->
<div onclick="goToRecommendations();">All recommendations</div>

<!-- Recommended -->
<a href="recommendations/">All recommendations</a>
```

#### Thuộc tính alt
Thêm nội dung thay thế vào thuộc tính `alt` cho các đối tượng image, video, canvas, ...

```html
<!-- Not recommended -->
<img src="spreadsheet.png">

<!-- Recommended -->
<img src="spreadsheet.png" alt="Spreadsheet screenshot.">
```

#### Tham chiếu thực thể (Entity Reference)
Không cần thiết phải sử dụng các tham chiếu thực thể như `&mdash;`, `&rdquo;` hay `&#x263a;`
miễn là các file và các editor đều dùng thống nhất encoding là UTF-8.

```html
<!-- Not recommended -->
The currency symbol for the Euro is &ldquo;&eur;&rdquo;.

<!-- Recommended -->
The currency symbol for the Euro is “€”.
```

#### Thuộc tính type
Bỏ thuộc tính `type` đối với các file style sheet (nếu là file CSS) và script
(nếu là file javascript). Mặc định, HTML5 áp dụng `text/css` và `text/javascript`
cho file CSS và javascript.

```html
<!-- Not recommended -->
<link rel="stylesheet" href="//www.google.com/css/maia.css" type="text/css">

<!-- Recommended -->
<link rel="stylesheet" href="//www.google.com/css/maia.css">

<!-- Not recommended -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js" type="text/javascript"></script>

<!-- Recommended -->
<script src="//www.google.com/js/gweb/analytics/autotrack.js"></script>
```

### Quy tắc format HTML
#### Format thông thường
Sử dụng một dòng mới cho mỗi block element, list hoặc table, lùi đầu dòng cho mỗi element con.
(Nếu gặp vấn đề về khoảng trắng giữa các list item thì có thể cho nhiều `li` element cùng một dòng)

```html
<blockquote>
  <p><em>Space</em>, the final frontier.</p>
</blockquote>

<ul>
  <li>Moe</li>
  <li>Larry</li>
  <li>Curly</li>
</ul>

<table>
  <thead>
    <tr>
      <th scope="col">Income</th>
      <th scope="col">Taxes</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>$ 5.00</td>
      <td>$ 4.50</td>
    </tr>
  </tbody>
</table>
```

#### Dấu nháy kép
Sử dụng dấu nháy kép (`""`) bao quanh giá trị của attribute, không sử dụng dấu nháy đơn (`''`).

```html
<!-- Not recommended -->
<a class='maia-button maia-button-secondary'>Sign in</a>

<!-- Recommended -->
<a class="maia-button maia-button-secondary">Sign in</a>
```

### CSS Style Rules
#### CSS Validity
Viết CSS đúng chuẩn nếu có thể.
Có thể sử dụng [W3C CSS Validation Service](http://jigsaw.w3.org/css-validator/) để validate.

#### Đặt tên ID và class
Tránh đặt tên ID, class tối nghĩa (vd: #abc) hoặc mô tả hình thức của element (vd: .button-green).   
Hãy đặt tên sao cho nó thể hiện được mục đích/ý nghĩa của element: #login, .video, ...

Đặt tên ID và class sao cho ngắn gọn nhưng phải dễ hiểu.

```css
/* Not recommended */
#navigation {}
.atr {}

/* Recommended */
#nav {}
.author {}
```

#### Type Selector
Tránh dùng tên element kết hợp với ID, class nếu không cần thiết.   
Tránh dùng selector lồng nhau nếu không cần thiết (ảnh hưởng tới performance).

```css
/* Not recommended */
ul#example {}
div.error {}
ul .list-item {}

/* Recommended */
#example {}
.error {}
.list-item {}
```

#### Thuộc tính dạng viết tắt
Sử dụng cách viết tắt cho thuộc tính khi có thể.

```css
/* Not recommended */
border-top-style: none;
font-family: palatino, georgia, serif;
font-size: 100%;
line-height: 1.6;
padding-bottom: 2em;
padding-left: 1em;
padding-right: 1em;
padding-top: 0;

/* Recommended */
border-top: 0;
font: 100%/1.6 palatino, georgia, serif;
padding: 0 1em 2em;
```

#### Bỏ đơn vị sau giá trị 0
Bỏ đơn vị sau giá trị 0 (trừ trường hợp bắt buộc).

```css
/* Recommended */
margin: 0;
padding: 0;
```

#### Bỏ chữ số 0 dẫn đầu
Bỏ chữ số 0 dẫn đầu khi giá trị nằm trong khoảng -1 đến 1

```css
font-size: .8em;
```

#### Ký hiệu hexa
Đối với mã màu, sử dụng số hexa 3 ký tự nếu có thể.

```css
/* Not recommended */
color: #eebbcc;

/* Recommended */
color: #ebc;
```

#### Prefix
Với các dự án lớn hoặc có thể được nhúng trong dự án khác, hãy thêm prefix (namespace), theo sau bởi `-`, cho ID và class.

```css
.adw-help {} /* AdWords */
#maia-note {} /* Maia */
```

#### Chia tách các từ trong tên ID, class
Dùng dấu `-` để chia tách các từ trong tên ID, class.

```css
/* Not recommended: không chia tách các từ “demo” và “image” */
.demoimage {}

/* Not recommended: dùng dấu _ chứ không phải - */
.error_status {}

/* Recommended */
#video-id {}
.ads-sample {}
```

#### Hacks
Tránh sử dụng các CSS hack, hãy cố tìm cách khác trước.

### CSS Formatting Rules
#### Thứ tự khai báo
Khai báo theo thứ tự alphabet không tính các vendor-specific prefix. Chỉ xét
vendor-specific prefix khi sắp xếp nhiều vendor-specific prefix cho cùng 1 thuộc tính,
ví dụ: xếp prefix `-moz` trước `-webkit`.

```css
background: fuchsia;
border: 1px solid;
-moz-border-radius: 4px;
-webkit-border-radius: 4px;
border-radius: 4px;
color: black;
text-align: center;
text-indent: 2em;
```

#### Block Content Indentation
Lùi đầu dòng đối với các khối nội dung lồng nhau.

```css
@media screen, projection {

  html {
    background: #fff;
    color: #444;
  }

}
```

#### Dùng dấu ; sau mỗi khai báo

```css
/* Not recommended */
.test {
  display: block;
  height: 100px
}

/* Recommended */
.test {
  display: block;
  height: 100px;
}
```

#### Dùng 1 dấu cách giữa tên thuộc tính và giá trị
Luôn dùng 1 dấu cách giữa tên thuộc tính và giá trị (sau dấu `:`).

```css
/* Not recommended */
h3 {
  font-weight:bold;
}

/* Recommended */
h3 {
  font-weight: bold;
}
```

#### Phân cách các selector, khối khai báo
Mỗi selector và thuộc tính nằm trên 1 dòng riêng.   
Sử dụng 1 dấu cách giữa selector cuối cùng và dấu `{` bắt đầu khối khai báo.   
Dấu `{` nằm trên cùng 1 dòng với selector cuối cùng.   

```css
/* Not recommended: missing space */
#video{
  margin-top: 1em;
}

/* Not recommended: unnecessary line break */
#video
{
  margin-top: 1em;
}

/* Not recommended */
a:focus, a:active {
  position: relative; top: 1px;
}

/* Recommended */
h1,
h2,
h3 {
  font-weight: normal;
  line-height: 1.2;
}
```

#### Phân cách các rule
Các rule cách nhau 1 dòng trống.

```css
html {
  background: #fff;
}

body {
  margin: auto;
  width: 50%;
}
```

#### Sử dụng dấu nháy đơn (`''`)
Sử dụng dấu nháy đơn (`''`) thay cho dấu nháy kép (`""`) đối với attribute selector
và giá trị của thuộc tính. Không dùng dấu nháy đối với giá trị URL (`url()`).   
Ngoại lệ: dùng dấu nháy kép (`""`) cho giá trị [`@charset`]
(http://www.w3.org/TR/CSS21/syndata.html#charset)

```css
/* Not recommended */
@import url("//www.google.com/css/maia.css");

html {
  font-family: "open sans", arial, sans-serif;
}

/* Recommended */
@import url(//www.google.com/css/maia.css);

html {
  font-family: 'open sans', arial, sans-serif;
}
```
