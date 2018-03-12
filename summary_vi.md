### Bouncing loader

`Creates a bouncing loader animation.`

Tạo hiệu ứng nảy khi tải trang.
#### HTML

```html
<div class="bouncing-loader">
  <div></div>
  <div></div>
  <div></div>
</div>
```

#### CSS

```css
@keyframes bouncing-loader {
  from {
    opacity: 1;
    transform: translateY(0);
  }
  to {
    opacity: 0.1;
    transform: translateY(-1rem);
  }
}
.bouncing-loader {
  display: flex;
  justify-content: center;
}
.bouncing-loader > div {
  width: 1rem;
  height: 1rem;
  margin: 3rem 0.2rem;
  background: #8385aa;
  border-radius: 50%;
  animation: bouncing-loader 0.6s infinite alternate;
}
.bouncing-loader > div:nth-child(2) {
  animation-delay: 0.2s;
}
.bouncing-loader > div:nth-child(3) {
  animation-delay: 0.4s;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__bouncing-loader">
  	<div></div>
    <div></div>
    <div></div>
  </div>
</div>

<style>
@keyframes bouncing-loader {
  from {
    opacity: 1;
    transform: translateY(0);
  }
  to {
    opacity: 0.1;
    transform: translateY(-1rem);
  }
}
.snippet-demo__bouncing-loader {
  display: flex;
  justify-content: center;
}
.snippet-demo__bouncing-loader > div {
  width: 1rem;
  height: 1rem;
  margin: 3rem 0.2rem;
  background: #8385aa;
  border-radius: 50%;
  animation: bouncing-loader 0.6s infinite alternate;
}
.snippet-demo__bouncing-loader > div:nth-child(2) {
  animation-delay: 0.2s;
}
.snippet-demo__bouncing-loader > div:nth-child(3) {
  animation-delay: 0.4s;
}
</style>

#### Giải thích

Ghi chú: `1rem` tương đương `16px`.

1. Ta sử dụng tag `@keyframes` để định nghĩa hiệu ứng có 2 trạng thái, khi thành phần thay đổi độ trong suốt `opacity` và nó được dịch chuyển lên trong mặt phẳng 2D thì sử dụng thuộc tính `transform: translateY()`.

2. `.bouncing-loader` là khối chứa các hình tròn có hiệu ứng nảy lên  và các hình tròn đó có sử dụng các thuộc tính`display: flex`
   và `justify-content: center` để cố định vị trí của chúng vào giữa ( theo chiều dọc ).

3. thành phần `.bouncing-loader > div`, tập trung vào 3 thẻ con `div` nằm trong class cha. Các `div`s được nhận chiều cao và chiều rộng của `1 rem`, sử dụng `border-radius: 50%` để biến chúng từ hình vuông thành hình tròn.

4. `margin: 3rem 0.2rem` chỉ định mỗi vòng tròn có khoảng cách trên / dưới là `3rem` và trái / phải là `0.2rem` để chúng không chạm nhau và có không gian trống.

5. `animation` là một thuộc tính viết tắt cho các thuộc tính hiệu ứng khác nhau: `animation-name`, `animation-duration`, `animation-iteration-count`, `animation-direction` được sử dụng.

6. `nth-child(n)` nhắm mục tiêu các phần tử đó là con thứ n của phần tử cha mẹ nó.

7. `animation-delay` được sử dụng trên `div` thứ 2 và 3 tương ứng, để các phần tử không kích hoạt các hiệu ứng cùng một lúc.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-animation

<!-- tags: animation -->
### Đặt lại Box-sizing

Đặt lại `Độ rộng` và `chiều cao` của box-model sao cho không bị ảnh hưởng bởi `padding` và `borders`.

#### CSS

```css
html {
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__box-sizing-reset">Demo</div>
</div>

<style>
.snippet-demo__box-sizing-reset {
  box-sizing: border-box;
  width: 200px;
  padding: 1.5em;
  color: #7983ff;
  font-family: sans-serif;
  background-color: white;
  border: 5px solid;
}
</style>

#### Giải thích

1. `box-sizing: border-box` làm cho việc bổ sung `padding` hoặc `border`s không bị ảnh hưởng bởi `chiều cao` hay `độ rộng` phần tử.
2. `box-sizing: inherit` làm cho một phần tử tuân theo quy tắc `box-sizing` của phần tử cha.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css3-boxsizing

<!-- tags: layout -->
### Clearfix

Đảm bảo 1 phần tử tự xóa con của nó.

###### Note: Điều này chỉ hữu ích khi bạn sử dụng float để xây dựng bố cục. Hãy xem xét sử dụng một phuơng pháp hiện đại như flexbox layout hoặc grid layout.

#### HTML

```html
<div class="clearfix">
  <div class="floated">float a</div>
  <div class="floated">float b</div>
  <div class="floated">float c</div>
</div>
```

#### CSS

```css
.clearfix::after {
  content: '';
  display: block;
  clear: both;
}

.floated {
  float: left;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__clearfix">
    <div class="snippet-demo__floated">float a</div>
    <div class="snippet-demo__floated">float b</div>
    <div class="snippet-demo__floated">float c</div>
  </div>
</div>

<style>
.snippet-demo__clearfix::after {
  content: '';
  display: block;
  clear: both;
}

.snippet-demo__floated {
  float: left;
}
</style>

#### Giải thích

1. `.clearfix::after` định danh một phần tử giả lập.
2. `content: ''` cho phép phần tử giả lập đó ảnh hưởng đến bố cục.
3. `clear: both` xác định rằng bên trái, bên phải hoặc cả hai bên của phần tử không thể được kề bên với các phần tử đã lưu trước đó trong cùng một ngữ cảnh định dạng khối.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">⚠️ Để đoạn mã này hoạt động đúng, bạn cần phải đảm bảo rằng không có phần tử con non-floating trong vùng chứa và không có các tall floats trước vùng chứa rõ ràng nhưng trong cùng một ngữ cảnh định dạng (ví dụ: các cột được thả nổi). (e.g. floated columns).</span>

<!-- tags: layout -->
### Tỉ lệ giữa chiều rộng và cao không thay đổi

Với một phần tử có chiều rộng biến đổi, nó sẽ đảm bảo chiều cao của nó vẫn tương xứng theo kiểu đáp ứng
(i.e., chiều rộng đến chiều cao của nó không thay đổi).

#### HTML

```html
<div class="constant-width-to-height-ratio"></div>
```

#### CSS

```css
.constant-width-to-height-ratio {
  background: #333;
  width: 50%;
}
.constant-width-to-height-ratio::before {
  content: '';
  display: block;
  padding-top: 100%;
  float: left;
}
.constant-width-to-height-ratio::after {
  content: '';
  display: block;
  clear: both;
}
```

#### Demo

Thay đổi kích thước cửa sổ trình duyệt của bạn để xem tỷ lệ phần tử vẫn giữ nguyên.

<div class="snippet-demo">
  <div class="snippet-demo__constant-width-to-height-ratio"></div>
</div>

<style>
.snippet-demo__constant-width-to-height-ratio {
  background: #333;
  width: 50%;
}
.snippet-demo__constant-width-to-height-ratio::before {
  content: '';
  display: block;
  padding-top: 100%;
  float: left;
}
.snippet-demo__constant-width-to-height-ratio::after {
  content: '';
  display: block;
  clear: both;
}
</style>

#### Giải thích

`padding-top` trên phần tử giả lập `::before` gây ra chiều cao của phần tử bằng một phần trăm chiều rộng của nó. `100%` do đó chiều cao của phần tử sẽ luôn luôn là `100%`,tạo ra một hình vuông đáp ứng.

Phương pháp này cũng cho phép nội dung được đặt bên trong phần tử bình thường.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">✅ No caveats.</span>

<!-- tags: layout -->
### Phân phối đều các phần tử con

Phân phối đều các phần tử con trong phần tử cha

#### HTML

```html
<div class="evenly-distributed-children">
  <p>Item1</p>
  <p>Item2</p>
  <p>Item3</p>
</div>
```

#### CSS

```css
.evenly-distributed-children {
  display: flex;
  justify-content: space-between;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__evenly-distributed-children">
    <p>Item1</p>
    <p>Item2</p>
    <p>Item3</p>
  </div>
</div>

<style>
.snippet-demo__evenly-distributed-children {
  display: flex;
  width: 100%;  
  justify-content: space-between;
}
</style>

#### Giải thích

1. `display: flex` kích hoạt flexbox.
2. `justify-content: space-between` phân bố đều các phần tử con theo chiều ngang. Mục đầu tiên được đặt ở cạnh trái, trong khi mục cuối cùng được đặt ở cạnh bên phải.

Cách khác, sử dụng `justify-content: space-around` để phân phối phần tử con với không gian xung quoanh chung chứ không phải giữa chúng.

#### Hỗ trợ trình duyệt
<span class="snippet__support-note">⚠️ Cần tiền tố để được hỗ trợ đầy đủ..</span>

* https://caniuse.com/#feat=flexbox

<!-- tags: layout -->
### Trung tâm flexbox

Theo chiều dọc và chiều dọc, phần tử con nằm trong phần tử gốc sử dụng `flexbox`.

#### HTML

```html
<div class="flexbox-centering">
  <div class="child">Centered content.</div>
</div>
```

#### CSS

```css
.flexbox-centering {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__flexbox-centering">
    <p class="snippet-demo__flexbox-centering__child">Centered content.</p>
  </div>
</div>

<style>
.snippet-demo__flexbox-centering {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 200px;
}
</style>

#### Giải thích

1. `display: flex` kích hoạt flexbox.
2. `justify-content: center` căn giữa theo chiều ngang.
3. `align-items: center` căn phần tử con giữa theo chiều dọc.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">⚠️ Cần tiền tố để hỗ trợ đầy đủ.</span>

* https://caniuse.com/#feat=flexbox

<!-- tags: layout -->
### Căn giữa grid

Căn giữa phần tử con theo chiều dọc và chiều ngang sử dụng `grid`.

#### HTML

```html
<div class="grid-centering">
  <div class="child">Centered content.</div>
</div>
```

#### CSS

```css
.grid-centering {
  display: grid;
  justify-content: center;
  align-items: center;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__grid-centering">
    <p class="snippet-demo__grid-centering__child">Centered content.</p>
  </div>
</div>

<style>
.snippet-demo__grid-centering {
  display: grid;
  justify-content: center;
  align-items: center;
  height: 200px;
}
</style>

#### Giải thích

1. `display: grid` kích hoạt grid.
2. `justify-content: center` căn giữa phần tử con theo chiều ngang.
3. `align-items: center` căn giữa phần tử con theo chiều dọc.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-grid

<!-- tags: layout -->
### Giao diện grid

Giao diện website cơ bản sử dụng `grid`.

#### HTML

```html
<div class="grid-layout">
  <div class="header">Header</div>
  <div class="sidebar">Sidebar</div>
  <div class="content">
    Content
    <br>
    Lorem ipsum dolor sit amet, consectetur adipisicing elit.
  </div>
  <div class="footer">Footer</div>
</div>
```

#### CSS

```css
.grid-layout {
  display: grid;
  grid-gap: 10px;
  grid-template-columns: repeat(3, 1fr);
  grid-template-areas:
    'sidebar header header'
    'sidebar content content'
    'sidebar footer  footer';
  color: white;
}
.grid-layout > div {
  background: #333;
  padding: 10px;
}
.sidebar {
  grid-area: sidebar;
}
.content {
  grid-area: content;
}
.header {
  grid-area: header;
}
.footer {
  grid-area: footer;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__grid-layout">
    <div class="box snippet-demo__grid-layout__header">Header</div>
    <div class="box snippet-demo__grid-layout__sidebar">Sidebar</div>
    <div class="box snippet-demo__grid-layout__content">Content
      <br> Lorem ipsum dolor sit amet, consectetur adipisicing elit.
    </div>
    <div class="box snippet-demo__grid-layout__footer">Footer</div>
  </div>
</div>

<style>
.snippet-demo__grid-layout {
  margin: 1em;
  display: grid;
  grid-gap: 10px;
  grid-template-columns: repeat(3, 1fr);
  grid-template-areas:
    "sidebar header header"
    "sidebar content content"
    "sidebar  footer  footer";
  background-color: #fff;
  color: white;
}
.snippet-demo__grid-layout > div {
  background: #333;
  padding: 10px;
}
.snippet-demo__grid-layout__sidebar {
    grid-area: sidebar;
}
.snippet-demo__grid-layout__content {
    grid-area: content;
}
.snippet-demo__grid-layout__header {
    grid-area: header;
}
.snippet-demo__grid-layout__footer {
    grid-area: footer;
}
</style>

#### Giải thích

1. `display: grid` kích hoạt grid.
2. `grid-gap: 10px` định nghĩa khoảng trắng giữa các phần tử.
3. `grid-template-columns: repeat(3, 1fr)` định nghĩa 3 cột cùng kích cỡ.
4. `grid-template-areas` định nghĩa tên của các khu vực grid.
5. `grid-area: sidebar` làm cho các phần tử sử dụng khu vực với tên là `sidebar`.

#### Trình duyệt hỗ trợ

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-grid

<!-- tags: layout -->
### Lược bỏ text

Nếu đoạn text dài hơn 1 dòng nó sẽ được lược bỏ bằng dấu 3 chấm `…`.

#### HTML

```html
<p class="truncate-text">If I exceed one line's width, I will be truncated.</p>
```

#### CSS

```css
.truncate-text {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  width: 200px;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__truncate-text">
    This text will be truncated if it exceeds 200px in width.
  </p>
</div>

<style>
.snippet-demo__truncate-text {
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  width: 200px;
  margin: 0;
}
</style>

#### Giải thích

1. `overflow: hidden` ngăn cho đoạn văn bản không bị tràn lên kích cỡ của nó
   (đối với 1 khối, 100% chiều rông và chiều cao tự động).
2. `white-space: nowrap` ngăn cho text vượt quá 1 hàng trong chiều cao.
3. `text-overflow: ellipsis` thay bằng dấu chấm lửng nếu đoạn text tràn ra ngoài kích cỡ.
4. `width: 200px;` đảm bảo rằng phần tử có một chiều, để biết khi nào có dấu chấm lửng

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">⚠️ Chỉ thực hiện với phần tử đơn dòng.</span>

* https://caniuse.com/#feat=text-overflow

<!-- tags: layout -->
### Vòng tròn

Tạo hình tròn với css thuần.

#### HTML

```html
<div class="circle"></div>
```

#### CSS

```css
.circle {
  border-radius: 50%;
  width: 2rem;
  height: 2rem;
  background: #333;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__circle"></div>
</div>

<style>
.snippet-demo__circle {
  border-radius: 50%;
  width: 2rem;
  height: 2rem;
  background: #333;
}
</style>

#### Giải thích

`border-radius: 50%` đường cong của một phần tử để tạo ra một vòng tròn.
                     
Vì một vòng tròn có cùng bán kính tại bất kỳ điểm nhất định, chiều rộng và chiều cao phải giống nhau. Các giá trị khác nhau sẽ tạo ra một hình elip.

#### Hỗ trợ trình duyệt

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=border-radius

<!-- tags: visual -->
### Tự tạo scrollbar

Tạo thanh scrollbar cho các tài liệu và các phần tử với scrollbar overflow, trên nền tảng webkit.

#### HTML

```html
<div class="custom-scrollbar">
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?</p>
</div>
```

#### CSS

```css
/* Document scrollbar */
::-webkit-scrollbar {
  width: 8px;
}

::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  border-radius: 10px;
}

::-webkit-scrollbar-thumb {
  border-radius: 10px;
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
}

/* Scrollable element */
.some-element::webkit-scrollbar {
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__custom-scrollbar">
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?
    </p>
    <p>
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?
    </p>
  </div>
</div>

<style>
.snippet-demo__custom-scrollbar {
  height: 100px;
  overflow: auto;
}

.snippet-demo__custom-scrollbar::-webkit-scrollbar {
  width: 8px;
}

.snippet-demo__custom-scrollbar::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  border-radius: 10px;
}

.snippet-demo__custom-scrollbar::-webkit-scrollbar-thumb {
  border-radius: 10px;
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
}
</style>

#### Explanation

1. `::-webkit-scrollbar` nhắm mục tiêu toàn bộ phần tử thanh cuộn.
2. `::-webkit-scrollbar-track` chỉ nhắm mục tiêu theo dõi thanh cuộn.
3. `::-webkit-scrollbar-thumb` nhắm mục tiêu thanh công cụ scollbar.

Có rất nhiều yếu tố giả khác mà bạn có thể sử dụng để tạo kiểu thanh cuộn. Để biết thêm thông tin, hãy ghé thăm [WebKit Blog](https://webkit.org/blog/363/styling-scrollbars/)

#### Browser support

<span class="snippet__support-note">⚠️ Scrollbar styling khổng có bất kỳ tiêu chuẩn đánh giá nào.</span>

* https://caniuse.com/#feat=css-scrollbar

<!-- tags: visual -->
### Lựa chọn văn bản tùy chọn

Thay đổi phong cách của văn bản tùy chọn

#### HTML

```html
<p class="custom-text-selection">Select some of this text.</p>
```

#### CSS

```css
::selection {
  background: aquamarine;
  color: black;
}
.custom-text-selection::selection {
  background: deeppink;
  color: white;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__custom-text-selection">Select some of this text.</p>
</div>

<style>
.snippet-demo__custom-text-selection::selection {
  background: deeppink;
  color: white;
}
.snippet-demo__custom-text-selection::-moz-selection {
  background: deeppink;
  color: white;
}
</style>

#### Explanation

`::selection` định nghĩa một bộ chọn giả trên một phần tử để định kiểu văn bản bên trong nó khi được chọn. Lưu ý rằng nếu bạn không kết hợp bất kỳ bộ chọn khác, phong cách của bạn sẽ được áp dụng ở cấp gốc tài liệu, cho bất kỳ phần tử có thể lựa chọn nào.

#### Browser support

<span class="snippet__support-note">⚠️ Yêu cầu tiền tố để được hỗ trợ đầy đủ và không thực sự trong bất kỳ đặc điểm kỹ thuật..</span>

* https://caniuse.com/#feat=css-selection

<!-- tags: visual -->
### Dynamic shadow

Tạo một cái bóng giống như `box-shadow` nhưng dựa trên màu sắc thành phần của phần tử đó.
    
#### HTML

```html
<div class="dynamic-shadow-parent">
  <div class="dynamic-shadow"></div>
</div>
```

#### CSS

```css
.dynamic-shadow-parent {
  position: relative;
  z-index: 1;
}
.dynamic-shadow {
  position: relative;
  width: 10rem;
  height: 10rem;
  background: linear-gradient(75deg, #6d78ff, #00ffb8);
}
.dynamic-shadow::after {
  content: '';
  width: 100%;
  height: 100%;
  position: absolute;
  background: inherit;
  top: 0.5rem;
  filter: blur(0.4rem);
  opacity: 0.7;
  z-index: -1;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__dynamic-shadow-parent">
    <div class="snippet-demo__dynamic-shadow"></div>
  </div>
</div>

<style>
.snippet-demo__dynamic-shadow-parent {
  position: relative;
  z-index: 1;
}
.snippet-demo__dynamic-shadow {
  position: relative;
  width: 10rem;
  height: 10rem;
  background: linear-gradient(75deg, #6d78ff, #00ffb8);
}
.snippet-demo__dynamic-shadow::after {
  content: '';
  position: absolute;
  width: 100%;
  height: 100%;
  background: inherit;
  top: 0.5rem;
  filter: blur(0.4rem);
  opacity: 0.7;
  z-index: -1;
}
</style>

#### Explanation

The snippet requires a somewhat complex case of stacking contexts to get right, such that the pseudo-element
will be positioned underneath the element itself while still being visible.

1. `position: relative` về cha mẹ thiết lập một ngữ cảnh định vị Cartesian cho các phần tử con.
2. `z-index: 1` Thiết lập một ngữ cảnh xếp chồng khác.
3. `position: relative` Trên phần tử con thiết lập một ngữ cảnh cho các phần tử giả lập.
4. `::after` định nghĩa 1 phần tử gỉa lập.
5. `position: absolute` lấy phần tử giả ra khỏi dòng chảy của tài liệu và định vị nó trong quan hệ với cha mẹ.
6. `width: 100%` và `height: 100%` kích cỡ các yếu tố giả để điền vào kích thước của cha mẹ, làm cho nó có kích thước bằng nhau.
7. `background: inherit` Làm cho các phần tử giả kế thừa các linear gradient được chỉ định trên các phần tử.
8. `top: 0.5rem` bù đắp phần tử giả giảm nhẹ từ cha mẹ của nó.
9. `filter: blur(0.4rem)` sẽ làm mờ phần tử giả tạo ra sự xuất hiện của một cái bóng bên dưới.
10. `opacity: 0.7` làm cho các phần tử giả mờ đi 1 phần.
11. `z-index: -1` đưa vị trí phần tử giả ra sau phần tử cha.

#### Browser support

<span class="snippet__support-note">⚠️ Requires prefixes for full support.</span>

* https://caniuse.com/#feat=css-filters

<!-- tags: visual -->
### Văn bản khắc

Tạo ra một hiệu ứng mà văn bản xuất hiện để được "khắc" hoặc khắc vào nền.

#### HTML

```html
<p class="etched-text">I appear etched into the background.</p>
```

#### CSS

```css
.etched-text {
  text-shadow: 0 2px white;
  font-size: 1.5rem;
  font-weight: bold;
  color: #b8bec5;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__etched-text">I appear etched into the background.</p>
</div>

<style>
.snippet-demo__etched-text {
  font-size: 1.5rem;
  font-weight: bold;
  color: #b8bec5;
  text-shadow: 0 2px 0 white;
}
</style>

#### Explanation

`text-shadow: 0 2px white` tạo ra shadow màu trắng nhô ra `0px` theo chiều ngang và `2px` theo chiều dọc
từ vị trí nguồn.

Màu nền phải tối hơn màu bóng để có thể hoạt động.

Màu văn bản nên hơi nhạt dần để làm cho nó trông giống như nó được khắc / khắc ra nền.

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-textshadow

<!-- tags: visual -->
### Văn bản Gradient

cho văn bản một màu gradient

#### HTML

```html
<p class="gradient-text">Gradient text</p>
```

#### CSS

```css
.gradient-text {
  background: -webkit-linear-gradient(pink, red);
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__gradient-text">
    Gradient text
  </p>
</div>

<style>
.snippet-demo__gradient-text {
  background: -webkit-linear-gradient(pink, red);
  -webkit-text-fill-color: transparent;
  -webkit-background-clip: text;
  font-size: 2rem;
  font-weight: bold;
  margin: 0;
}
</style>

#### Explanation

1. `background: -webkit-linear-gradient(...)` cho phần tử text màu gradient.
2. `webkit-text-fill-color: transparent` đổ vào đoạn text màu gradient.
3. `webkit-background-clip: text` clip nền với văn bản, điền vào các văn bản với nền gradient như màu sắc.

#### Browser support

<span class="snippet__support-note">⚠️ Uses non-standard properties.</span>

* https://caniuse.com/#feat=text-stroke

<!-- tags: visual -->
### đường viền hairline

Cung cấp cho một phần tử một đường viền bằng 1 pixel của thiết bị gốc có chiều rộng, có thể trông rất sắc nét và sắc nét.

#### HTML

```html
<div class="hairline-border">text</div>
```

#### CSS

```css
.hairline-border {
  box-shadow: 0 0 0 1px;
}

@media (min-resolution: 2dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.5px;
  }
}

@media (min-resolution: 3dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.33333333px;
  }
}

@media (min-resolution: 4dppx) {
  .hairline-border {
    box-shadow: 0 0 0 0.25px;
  }
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__hairline-border">Text with a hairline border around it.</p>
</div>

<style>
.snippet-demo__hairline-border {
  box-shadow: 0 0 0 1px;
}

@media (min-resolution: 2dppx) {
  .snippet-demo__hairline-border {
    box-shadow: 0 0 0 0.5px;
  }
}

@media (min-resolution: 3dppx) {
  .snippet-demo__hairline-border {
    box-shadow: 0 0 0 0.33333333px;
  }
}

@media (min-resolution: 4dppx) {
  .snippet-demo__hairline-border {
    box-shadow: 0 0 0 0.25px;
  }
}
</style>

#### Explanation

1. `box-shadow`, Khi sử dụng để lan rộng, sử dụng một border giả có thẻ  sử dụng subpixels\*.
2. sử dụng `@media (min-resolution: ...)` để check tỉ lệ pixel của thiết bị (`1dppx` equals 96 DPI),
  cài đặt độ lan rộng của `box-shadow` bằng `1 / dppx`.

#### Browser Support

<span class="snippet__support-note">⚠️ Cần cú pháp thay thế và kiểm tra các tác nhân người dùng JavaScript để được hỗ trợ đầy đủ..</span>

* https://caniuse.com/#feat=css-boxshadow
* https://caniuse.com/#feat=css-media-resolution

<hr>

\*Chrome không hỡ trợ giá trị subpixel  trên `border`. Safari cũng không hỗ trợ cho `box-shadow`. Firefox hỗ trợ cả 2.

<!-- tags: visual -->
### Thanh cuộn tràn gradient

Thêm gradient fading cho một phần tử tràn để biểu thị tốt hơn có nhiều nội dung cần được cuộn lại.

#### HTML

```html
<div class="overflow-scroll-gradient">
  <div class="overflow-scroll-gradient__scroller">
    Content to be scrolled
  </div>
</div>
```

#### CSS

```css
.overflow-scroll-gradient {
  position: relative;
}
.overflow-scroll-gradient::after {
  content: '';
  position: absolute;
  bottom: 0;
  width: 240px;
  height: 25px;
  background: linear-gradient(
    rgba(255, 255, 255, 0.001),
    white
  ); /* transparent keyword is broken in Safari */
  pointer-events: none;
}
.overflow-scroll-gradient__scroller {
  overflow-y: scroll;
  background: white;
  width: 240px;
  height: 200px;
  padding: 15px 0;
  line-height: 1.2;
  text-align: center;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__overflow-scroll-gradient">
    <div class="snippet-demo__overflow-scroll-gradient__scroller">
      Content to be scrolled
    </div>
  </div>
</div>

<style>
.snippet-demo__overflow-scroll-gradient {
  position: relative;
}
.snippet-demo__overflow-scroll-gradient::after {
  content: '';
  background: linear-gradient(rgba(255, 255, 255, 0.001), white);
  position: absolute;
  width: 240px;
  height: 25px;
  bottom: 0;
  pointer-events: none;
}
.snippet-demo__overflow-scroll-gradient__scroller {
  overflow-y: scroll;
  background: white;
  width: 240px;
  height: 200px;
  padding: 15px 0;
  line-height: 1.2;
  text-align: center;
}
</style>

<script>
document.querySelector('.snippet-demo__overflow-scroll-gradient__scroller').innerHTML = 'content '.repeat(100)
</script>

#### Explanation

1. `position: relative` trên phần tử cha thiết lập một ngữ cảnh định vị Cartesian cho nội dung của phần tử giả.
2. `::after` định nghĩa một phần tử giả.
3. `background-image: linear-gradient(...)` thêm một gradient tuyến tính mà fades từ minh bạch để trắng (từ trên xuống dưới).
4. `position: absolute` lấy phần tử giả ra khỏi dòng chảy của tài liệu và định vị nó trong quan hệ với cha mẹ.
5. `width: 240px` khớp với kích thước của phần tử cuộn (đó là một đứa trẻ của cha mẹ có yếu tố giả).
6. `height: 25px` là chiều cao cua phần tử giả fading , nên được giữ ở mức tương đối thấp.
7. `bottom: 0` vị trí của phần tử giả ở dưới phần tử cha.
8. `pointer-events: none` xác định rằng phần tử giả không thể là một mục tiêu của sự kiện chuột, cho phép văn bản đằng sau nó vẫn có thể được lựa chọn / tương tác.

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-gradients

<!-- tags: visual -->
### Gạch chân văn bản đẹp

Một sự thay thế đẹp hơn cho trang trí văn bản: nhấn mạnh nơi mà các dấu chấm chấm không gạch dưới. Natively được thực hiện như `text-decoration-skip-ink: auto`: tự động nhưng nó có kiểm soát ít hơn gạch dưới.

#### HTML

```html
<p class="pretty-text-underline">Pretty text underline without clipping descending letters.</p>
```

#### CSS

```css
.pretty-text-underline {
  font-family: Arial, sans-serif;
  display: inline;
  font-size: 18px;
  text-shadow: 1px 1px 0 #f5f6f9, -1px 1px 0 #f5f6f9, -1px -1px 0 #f5f6f9, 1px -1px 0 #f5f6f9;
  background-image: linear-gradient(90deg, currentColor 100%, transparent 100%);
  background-position: 0 0.98em;
  background-repeat: repeat-x;
  background-size: 1px 1px;
}
.pretty-text-underline::-moz-selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}
.pretty-text-underline::selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__pretty-text-underline">Pretty text underline without clipping descending letters.</p>
</div>

<style>
.snippet-demo__pretty-text-underline {
  font-family: Arial, sans-serif;
  display: inline;
  font-size: 18px !important;
  text-shadow: 1px 1px 0 #f5f6f9,
    -1px 1px 0 #f5f6f9,
    -1px -1px 0 #f5f6f9,
    1px -1px 0 #f5f6f9;
  background-image: linear-gradient(90deg, currentColor 100%, transparent 100%);
  background-position: 0 0.98em;
  background-repeat: repeat-x;
  background-size: 1px 1px;
}

.snippet-demo__pretty-text-underline::-moz-selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}

.snippet-demo__pretty-text-underline::selection {
  background-color: rgba(0, 150, 255, 0.3);
  text-shadow: none;
}
</style>

#### Explanation

1. `text-shadow: ...` có 4 giá trị với độ lệch bao phủ một vùng 4x4 px để đảm bảo đường gạch chân có một bóng "dày" bao phủ đường mà người nối đoạn clip. Sử dụng màu phù hợp với nền. Đối với một phông chữ lớn hơn, sử dụng một kích thước px lớn hơn.
2. `background-image: linear-gradient(...)` tạo một gradient 90 độ với màu sắc chữ hiện tại (`currentColor`).
3. The `background-*` các thuộc tính có kích thước gradient như 1x1px ở phía dưới và lặp lại nó dọc theo trục x.
4. The `::selection` bộ chọn giả đảm bảo bóng văn bản không ảnh hưởng đến việc lựa chọn văn bản.

#### Browser support

<span class="snippet__support-note">⚠️ Khoảng cách gạch dưới của văn bản phụ thuộc vào số liệu nội bộ của phông chữ, do đó bạn phải đảm bảo mọi người đều thấy cùng một phông chữ (tức là không có phông chữ hệ thống thay đổi dựa trên hệ điều hành).</span>

* https://caniuse.com/#feat=css-textshadow
* https://caniuse.com/#feat=css-gradients

<!-- tags: visual -->
### Đặt lại tất cả styles

Đặt lại toàn bộ styles về mặc định của một thuộc tính. Nó sẽ không ảnh hưởng đến thuộc tính `direction` và `unicode-bidi` .

#### HTML

```html
<div class="reset-all-styles">
  <h4>Title</h4>
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?</p>
</div>
```

#### CSS

```css
.reset-all-styles {
  all: initial;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__reset-all-styles">
    <h3>Title</h3>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?</p>
  </div>
</div>

<style>
.snippet-demo__reset-all-styles {
  all: initial;
}
</style>

#### Explanation

Tất cả các thuộc tính cho phép bạn thiết lập lại tất cả các kiểu (kế thừa hay không) thành các giá trị mặc định.

#### Browser support

<span class="snippet__support-note">⚠️ Trạng thái MS Edge đang được xem xét..</span>

* https://caniuse.com/#feat=css-all

<!-- tags: visual -->
### Hình dạng tách

Sử dụng một hình dạng SVG để tách hai khối khác nhau để tạo ra một hình ảnh thú vị hơn so với sự phân chia ngang theo tiêu chuẩn.       

#### HTML

```html
<div class="shape-separator"></div>
```

#### CSS

```css
.shape-separator {
  position: relative;
  height: 48px;
  background: #333;
}
.shape-separator::after {
  content: '';
  background-image: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiIHN0cm9rZS1taXRlcmxpbWl0PSIxLjQxNCI+PHBhdGggZD0iTTEyIDEybDEyIDEySDBsMTItMTJ6IiBmaWxsPSIjZmZmIi8+PC9zdmc+);
  position: absolute;
  width: 100%;
  height: 24px;
  bottom: 0;
}
```

#### Demo

<div class="snippet-demo is-distinct">
  <div class="snippet-demo__shape-separator"></div>
</div>

<style>
.snippet-demo__shape-separator {
  position: relative;
  height: 48px;
  margin: -0.75rem -1.25rem;
}
.snippet-demo__shape-separator::after {
  content: '';
  background-image: url(data:image/svg+xml;base64,PHN2ZyB2aWV3Qm94PSIwIDAgMjQgMjQiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgZmlsbC1ydWxlPSJldmVub2RkIiBjbGlwLXJ1bGU9ImV2ZW5vZGQiIHN0cm9rZS1saW5lam9pbj0icm91bmQiIHN0cm9rZS1taXRlcmxpbWl0PSIxLjQxNCI+PHBhdGggZD0iTTEyIDEybDEyIDEySDBsMTItMTJ6IiBmaWxsPSIjZmZmIi8+PC9zdmc+);
  position: absolute;
  width: 100%;
  height: 24px;
  bottom: 0;
}
</style>

#### Explanation

1. `position: relative` trên phần tử cha thiết lập một ngữ cảnh định vị Cartesian cho nội dung của phần tử giả.
2. `::after` định nghĩa một phần tử giả.
3. `background-image: url(...)` thêm hình SVG (hình tam giác 24x24 ở định dạng cơ sở64) làm hình nền của phần tử giả, lặp lại theo mặc định. Nó phải có màu sắc tương tự như khối đang được tách ra.
4. `position: absolute` takes the pseudo element out of the flow of the document and positions it in relation to the parent.
5. `width: 100%` đảm bảo phần tử trải dài toàn bộ chiều rộng của cha mẹ.
6. `height: 24px` giống chiều cao của shape.
7. `bottom: 0` vị trí dưới cùng của phần tử cha.

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=svg

<!-- tags: visual -->
### Ngăn xếp phông chữ hệ thống

Sử dụng phông chữ bản địa của hệ điều hành để có được cảm nhận gần giống với ứng dụng gốc.

#### HTML

```html
<p class="system-font-stack">This text uses the system font.</p>
```

#### CSS

```css
.system-font-stack {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu,
    Cantarell, 'Helvetica Neue', Helvetica, Arial, sans-serif;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__system-font-stack">This text uses the system font.</p>
</div>

<style>
.snippet-demo__system-font-stack {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", Helvetica, Arial, sans-serif;
}
</style>

#### Explanation

The browser looks for each successive font, preferring the first one if possible, and
falls back to the next if it cannot find the font (on the system or defined in CSS).

1. `-apple-system` ở San Francisco, được sử dụng trên iOS và macOS (tuy nhiên không có Chrome)
2. `BlinkMacSystemFont` ở San Francisco sử dụng trên macOS Chrome
3. `Segoe UI` sử dụng trên Windows 10
4. `Roboto` sử dụng trên Android
5. `Oxygen-Sans` được sử dụng trên GNU+Linux
6. `Ubuntu` được sử dụng trên Linux
7. `"Helvetica Neue"` và `Helvetica` được sử dụng trên macOS 10.10 và bên dưới (được bao bọc bởi dấu ngoặc kép bởi vì nó có một không gian)
9. `sans-serif` là phông chữ sans-serif dự phòng nếu không có phông chữ nào được hỗ trợ

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

<!-- tags: visual -->
### Hình tam giác

Tạo hình tam giác với css thuần.

#### HTML

```html
<div class="triangle"></div>
```

#### CSS

```css
.triangle {
  width: 0;
  height: 0;
  border-top: 20px solid #333;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__triangles">
    <div class="snippet-demo__triangle snippet-demo__triangle-1"></div>
    <div class="snippet-demo__triangle snippet-demo__triangle-2"></div>
    <div class="snippet-demo__triangle snippet-demo__triangle-3"></div>
    <div class="snippet-demo__triangle snippet-demo__triangle-4"></div>
    <div class="snippet-demo__triangle snippet-demo__triangle-5"></div>
  </div>
</div>

<style>
.snippet-demo__triangles {
  display: flex;
  align-items: center;
}

.snippet-demo__triangle {
  display: inline-block;
  width: 0;
  height: 0;
  margin-right: 0.25rem;
}

.snippet-demo__triangle-1 {
  border-top: 20px solid #333;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}

.snippet-demo__triangle-2 {
  border-bottom: 20px solid #333;
  border-left: 20px solid transparent;
  border-right: 20px solid transparent;
}

.snippet-demo__triangle-3 {
  border-left: 20px solid #333;
  border-top: 20px solid transparent;
  border-bottom: 20px solid transparent;
}

.snippet-demo__triangle-4 {
  border-right: 20px solid #333;
  border-top: 20px solid transparent;
  border-bottom: 20px solid transparent;
}

.snippet-demo__triangle-5 {
  border-top: 40px solid #333;
  border-left: 15px solid transparent;
  border-right: 15px solid transparent;
}
</style>

#### Explanation

[View this link for a detailed explanation.](https://stackoverflow.com/q/7073484)

Màu của đường viền là màu của tam giác. Phía đỉnh điểm tam giác tương ứng với điểm đối diện thuộc tính `border-*`. Ví dụ 1 màu ở trên `border-top`
mcó nghĩa là một mũi tên đi xuống.

sử dụng giá trị `px` để thay đổi tỷ lệ tam giác

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

<!-- tags: animation -->
### hiệu ứng gián đoạn hình donut

Tạo một donut spinner có thể sử dụng để  biểu thị việc tải nội dung.

#### HTML

```html
<div class="donut"></div>
```

#### CSS

```css
@keyframes donut-spin {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
.donut {
  display: inline-block;
  border: 4px solid rgba(0, 0, 0, 0.1);
  border-left-color: #7983ff;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  animation: donut-spin 1.2s linear infinite;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__donut-spinner"></div>
</div>

<style>
@keyframes snippet-demo__donut-spin {
    0% { transform: rotate(0deg); }
    100% { transform: rotate(360deg);}
}
.snippet-demo__donut-spinner {
  display: inline-block;
  border: 4px solid rgba(0, 0, 0, 0.1);
  border-left-color: #7983ff;
  border-radius: 50%;
  width: 30px;
  height: 30px;
  animation: snippet-demo__donut-spin 1.2s linear infinite;
}
</style>

#### Explanation

Sử dụng đường viền bán minh bạch cho toàn bộ phần tử, ngoại trừ một bên sẽ đóng vai trò là chỉ số tải cho bánh rán. Sử dụng hình ảnh động để xoay phần tử.

#### Browser support

<span class="snippet__support-note">⚠️ Requires prefixes for full support.</span>

* https://caniuse.com/#feat=css-animation
* https://caniuse.com/#feat=transforms2d

<!-- tags: animation -->
### Làm giảm bớt biến số

Các biến có thể được sử dụng lại cho các thuộc tính chức năng của quá trình chuyển đổi, thời gian, mạnh mẽ hơn sự dễ dàng cài sẵn, dễ dàng, thoải mái và dễ dàng ra vào.

#### HTML

```html
<div class="easing-variables"></div>
```

#### CSS

```css
:root {
  --ease-in-quad: cubic-bezier(0.55, 0.085, 0.68, 0.53);
  --ease-in-cubic: cubic-bezier(0.55, 0.055, 0.675, 0.19);
  --ease-in-quart: cubic-bezier(0.895, 0.03, 0.685, 0.22);
  --ease-in-quint: cubic-bezier(0.755, 0.05, 0.855, 0.06);
  --ease-in-expo: cubic-bezier(0.95, 0.05, 0.795, 0.035);
  --ease-in-circ: cubic-bezier(0.6, 0.04, 0.98, 0.335);

  --ease-out-quad: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --ease-out-cubic: cubic-bezier(0.215, 0.61, 0.355, 1);
  --ease-out-quart: cubic-bezier(0.165, 0.84, 0.44, 1);
  --ease-out-quint: cubic-bezier(0.23, 1, 0.32, 1);
  --ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);
  --ease-out-circ: cubic-bezier(0.075, 0.82, 0.165, 1);

  --ease-in-out-quad: cubic-bezier(0.455, 0.03, 0.515, 0.955);
  --ease-in-out-cubic: cubic-bezier(0.645, 0.045, 0.355, 1);
  --ease-in-out-quart: cubic-bezier(0.77, 0, 0.175, 1);
  --ease-in-out-quint: cubic-bezier(0.86, 0, 0.07, 1);
  --ease-in-out-expo: cubic-bezier(1, 0, 0, 1);
  --ease-in-out-circ: cubic-bezier(0.785, 0.135, 0.15, 0.86);
}

.easing-variables {
  width: 50px;
  height: 50px;
  background: #333;
  transition: transform 1s var(--ease-out-quart);
}

.easing-variables:hover {
  transform: rotate(45deg);
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__easing-variables">Hover</div>
</div>

<style>
:root {
  --ease-in-quad: cubic-bezier(0.55, 0.085, 0.68, 0.53);
  --ease-in-cubic: cubic-bezier(0.55, 0.055, 0.675, 0.19);
  --ease-in-quart: cubic-bezier(0.895, 0.03, 0.685, 0.22);
  --ease-in-quint: cubic-bezier(0.755, 0.05, 0.855, 0.06);
  --ease-in-expo: cubic-bezier(0.95, 0.05, 0.795, 0.035);
  --ease-in-circ: cubic-bezier(0.6, 0.04, 0.98, 0.335);

  --ease-out-quad: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --ease-out-cubic: cubic-bezier(0.215, 0.61, 0.355, 1);
  --ease-out-quart: cubic-bezier(0.165, 0.84, 0.44, 1);
  --ease-out-quint: cubic-bezier(0.23, 1, 0.32, 1);
  --ease-out-expo: cubic-bezier(0.19, 1, 0.22, 1);
  --ease-out-circ: cubic-bezier(0.075, 0.82, 0.165, 1);

  --ease-in-out-quad: cubic-bezier(0.455, 0.03, 0.515, 0.955);
  --ease-in-out-cubic: cubic-bezier(0.645, 0.045, 0.355, 1);
  --ease-in-out-quart: cubic-bezier(0.77, 0, 0.175, 1);
  --ease-in-out-quint: cubic-bezier(0.86, 0, 0.07, 1);
  --ease-in-out-expo: cubic-bezier(1, 0, 0, 1);
  --ease-in-out-circ: cubic-bezier(0.785, 0.135, 0.15, 0.86);
}

.snippet-demo__easing-variables {
  width: 75px;
  height: 75px;
  background: #333;
  color: white;
  font-size: 0.8rem;
  font-weight: bold;
  display: flex;
  justify-content: center;
  align-items: center;
  transition: transform 1s var(--ease-out-quart);
}

.snippet-demo__easing-variables:hover {
  transform: rotate(45deg);
}
</style>

#### Explanation

Các biến được định nghĩa trên toàn cầu trong`: root` CSS pseudo-class khớp với phần tử gốc của cây đại diện cho tài liệu. Trong HTML,`: root` đại diện cho phần tử <html> và giống với html của bộ chọn, ngoại trừ độ đặc hiệu của nó cao hơn.
#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: animation -->
### Hiệu ứng di chuột để gạch chân

Tạo hiệu ứng gạch chân khi text được hover vào.

<small>**Credit:** https://flatuicolors.com/</small>

#### HTML

```html
<p class="hover-underline-animation">Hover this text to see the effect!</p>
```

#### CSS

```css
.hover-underline-animation {
  display: inline-block;
  position: relative;
  color: #0087ca;
}
.hover-underline-animation::after {
  content: '';
  position: absolute;
  width: 100%;
  transform: scaleX(0);
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: #0087ca;
  transform-origin: bottom right;
  transition: transform 0.25s ease-out;
}
.hover-underline-animation:hover::after {
  transform: scaleX(1);
  transform-origin: bottom left;
}
```

#### Demo

<div class="snippet-demo">
  <p class="snippet-demo__hover-underline-animation">Hover this text to see the effect!</p>
</div>

<style>
.snippet-demo__hover-underline-animation {
  display: inline-block;
  position: relative;
  color: #0087ca;
}
.snippet-demo__hover-underline-animation::after {
  content: '';
  position: absolute;
  width: 100%;
  transform: scaleX(0);
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: #0087ca;
  transform-origin: bottom right;
  transition: transform 0.25s ease-out;
}
.snippet-demo__hover-underline-animation:hover::after {
  transform: scaleX(1);
  transform-origin: bottom left;
}
</style>

#### Explanation

1. `display: inline-block` makes the block `p` an `inline-block` to prevent the underline from
   spanning the entire parent width rather than just the content (text).
2. `position: relative` trên phần tử cha tham khảo thiết lập một bối cảnh định vị Cartesian cho con của nó
4. `position: absolute` takes the pseudo element out of the flow of the document and positions it in relation to the parent.
5. `width: 100%` đảm bảo phần tử trải dài toàn bộ chiều rộng của cha mẹ.
6. `transform: scaleX(0)` ban đầu vảy phần tử giả thành 0 vì vậy nó không có chiều rộng và không nhìn thấy được.
7. `bottom: 0` và `left: 0` vị trí của nó ở dưới và bên trái phần tử cha.
8. `transition: transform 0.25s ease-out` có nghĩa là điểm chuyển đổi neo được đặt ở góc dưới bên phải của khối.
9. `transform-origin: bottom right` có nghĩa là điểm chuyển đổi neo được đặt ở góc dưới bên phải của khối.
10. `:hover::after` then uses `scaleX(1)` để chuyển đổi chiều rộng đến 100%, sau đó thay đổi nguồn gốc chuyển đổi sang phía dưới cùng bên trái để điểm neo được đảo ngược, cho phép nó chuyển tiếp theo hướng khác khi lơ lửng.

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=transforms2d
* https://caniuse.com/#feat=css-transitions

<!-- tags: animation -->
### Vô hiệu hoá lựa chọn

làm cho nội dung không thể lựa chọn.

#### HTML

```html
<p>You can select me.</p>
<p class="unselectable">You can't select me!</p>
```

#### CSS

```css
.unselectable {
  user-select: none;
}
```

#### Demo

<div class="snippet-demo">
  <p>You can select me.</p>
  <p class="snippet-demo__disable-selection">You can't select me!</p>
</div>

<style>
.snippet-demo__disable-selection {
  user-select: none;
}
</style>

#### Explanation

`user-select: none` định danh một văn bản không thể lựa chọn.
#### Browser support

<span class="snippet__support-note">⚠️ Yêu cầu tiền tố để được hỗ trợ đầy đủ..</span>
<span class="snippet__support-note">⚠️ Đây không phải là phương pháp an toàn để ngăn người dùng sao chép nội dung.</span>

* https://caniuse.com/#feat=user-select-none

<!-- tags: interactivity -->
### Theo dõi gradient con trỏ chuột

Hiệu ứng di chuột, nơi gradient đi theo con trỏ chuột.

<small class="snippet__credit">**Credit:** [Tobias Reich](https://codepen.io/electerious/pen/MQrRxX)</small>

#### HTML

```html
<button class="mouse-cursor-gradient-tracking">
  <span>Hover me</span>
</button>
```

#### CSS

```css
.mouse-cursor-gradient-tracking {
  position: relative;
  background: #7983ff;
  padding: 0.5rem 1rem;
  font-size: 1.2rem;
  border: none;
  color: white;
  cursor: pointer;
  outline: none;
  overflow: hidden;
}

.mouse-cursor-gradient-tracking span {
  position: relative;
}

.mouse-cursor-gradient-tracking::before {
  --size: 0;
  content: '';
  position: absolute;
  left: var(--x);
  top: var(--y);
  width: var(--size);
  height: var(--size);
  background: radial-gradient(circle closest-side, pink, transparent);
  transform: translate(-50%, -50%);
  transition: width 0.2s ease, height 0.2s ease;
}

.mouse-cursor-gradient-tracking:hover::before {
  --size: 200px;
}
```

#### JavaScript

```js
var btn = document.querySelector('.mouse-cursor-gradient-tracking')
btn.onmousemove = function(e) {
  var x = e.pageX - btn.offsetLeft
  var y = e.pageY - btn.offsetTop
  btn.style.setProperty('--x', x + 'px')
  btn.style.setProperty('--y', y + 'px')
}
```

#### Demo

<div class="snippet-demo">
  <button class="snippet-demo__mouse-cursor-gradient-tracking">
    <span>Hover me</span>
  </button>
</div>

<style>
.snippet-demo__mouse-cursor-gradient-tracking {
  position: relative;
  background: #7983ff;
  padding: 0.5rem 1rem;
  font-size: 1.2rem;
  border: none;
  color: white;
  cursor: pointer;
  outline: none;
  overflow: hidden;
}

.snippet-demo__mouse-cursor-gradient-tracking span {
  position: relative;
}

.snippet-demo__mouse-cursor-gradient-tracking::before {
  --size: 0;
  content: '';
  position: absolute;
  left: var(--x);
  top: var(--y);
  width: var(--size);
  height: var(--size);
  background: radial-gradient(circle closest-side, aqua, rgba(0,255,255,0.0001));
  transform: translate(-50%, -50%);
  transition: width .2s ease, height .2s ease;
}

.snippet-demo__mouse-cursor-gradient-tracking:hover::before {
  --size: 200px;
}
</style>

<script>
(function () {
  var btn = document.querySelector('.snippet-demo__mouse-cursor-gradient-tracking')
  btn.onmousemove = function (e) {
    var x = e.pageX - btn.offsetLeft - btn.offsetParent.offsetLeft
    var y = e.pageY - btn.offsetTop - btn.offsetParent.offsetTop
    btn.style.setProperty('--x', x + 'px')
    btn.style.setProperty('--y', y + 'px')
  }
})()
</script>

#### Explanation

_TODO_

**Note!**

Nếu phần tử cha của phần tử có ngữ cảnh định vị (vị trí: tương đối), bạn cũng cần phải trừ đi các giá trị của nó.

```js
var x = e.pageX - btn.offsetLeft - btn.offsetParent.offsetLeft
var y = e.pageY - btn.offsetTop - btn.offsetParent.offsetTop
```

#### Browser support

<div class="snippet__requires-javascript">Requires JavaScript</div>
<span class="snippet__support-note">⚠️ Requires JavaScript.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: visual, interactivity -->
### Popout menu

Tiết lộ trình đơn bật lên tương tác trên di chuột.

#### HTML

```html
<div class="reference">
  <div class="popout-menu">
    Popout menu
  </div>
</div>
```

#### CSS

```css
.reference {
  position: relative;
}
.popout-menu {
  position: absolute;
  visibility: hidden;
  left: 100%;
}
.reference:hover > .popout-menu {
  visibility: visible;
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__reference">
    <div class="snippet-demo__popout-menu">
      Popout menu
    </div>
  </div>
</div>

<style>
.snippet-demo__reference {
  background: linear-gradient(135deg, #ff4c9f, #ff7b74);
  height: 75px;
  width: 75px;
  position: relative;
  will-change: transform;
}
.snippet-demo__popout-menu {
  position: absolute;
  visibility: hidden;
  left: 100%;
  background: #333;
  color: white;
  font-size: 0.9rem;
  padding: 0.4rem 0.8rem;
  width: 100px;
  text-align: center;
}
.snippet-demo__reference:hover > .snippet-demo__popout-menu {
  visibility: visible;
}
</style>

#### Explanation

1. `position: relative` trên phụ huynh tham khảo thiết lập một bối cảnh định vị Cartesian cho con của nó 
2. `position: absolute` đưa trình đơn bật lên ra khỏi dòng chảy của tài liệu và định vị nó trong quan hệ với cha mẹ.
3. `left: 100%` di chuyển menu popout 100% chiều ngang của cha mẹ từ bên trái.
4. `visibility: hidden` ẩn menu popout ban đầu và cho phép chuyển tiếp (unlike `display: none`).
5. `.reference:hover > .popout-menu` có nghĩa là khi `.reference` được hover vào, chọn con trực tiếp với một class `.popout-menu` và thay đổi `visibility` thành `visible`, trong đó hiển thị popout.

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

<!-- tags: interactivity -->
### Sibling fade

Fades ra các anh chị em của một item hovered.

#### HTML

```html
<div class="sibling-fade">
  <span>Item 1</span>
  <span>Item 2</span>
  <span>Item 3</span>
  <span>Item 4</span>
  <span>Item 5</span>
  <span>Item 6</span>
</div>
```

#### CSS

```css
span {
  padding: 0 1rem;
  transition: opacity 0.2s;
}

.sibling-fade:hover span:not(:hover) {
  opacity: 0.5;
}
```

#### Demo

<div class="snippet-demo">
  <nav class="snippet-demo__sibling-fade">
    <span>Item 1</span>
    <span>Item 2</span>
    <span>Item 3</span>
    <span>Item 4</span>
    <span>Item 5</span>
    <span>Item 6</span>
  </nav>
</div>

<style>
.snippet-demo__sibling-fade {
  cursor: default;
  line-height: 2;
  vertical-align: middle;
}

.snippet-demo__sibling-fade span {
  padding: 1rem;
  transition: opacity 0.2s;
}

.snippet-demo__sibling-fade:hover span:not(:hover) {
  opacity: 0.5;
}
</style>

#### Explanation

1. `transition: opacity 0.2s` chỉ định rằng thay đổi độ mờ đục sẽ được chuyển đổi trong khoảng 0.2 giây.
2. `.sibling-fade:hover span:not(:hover)` chỉ định rằng khi cha mẹ được hovered, chọn bất kỳ phần tử con `span`  nào mà hiện không được hovered và thay đổi độ mờ của họ để `0.5`.

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-sel3
* https://caniuse.com/#feat=css-transitions

<!-- tags: interactivity -->
### Custom variables

Các biến CSS chứa các giá trị cụ thể để được sử dụng lại trong suốt một tài liệu.

#### HTML

```html
<p class="custom-variables">CSS is awesome!</p>
```

#### CSS

```css
:root {
  --some-color: #da7800;
  --some-keyword: italic;
  --some-size: 1.25em;
  --some-complex-value: 1px 1px 2px whitesmoke, 0 0 1em slategray, 0 0 0.2em slategray;
}

.custom-variables {
  color: var(--some-color);
  font-size: var(--some-size);
  font-style: var(--some-keyword);
  text-shadow: var(--some-complex-value);
}
```

#### Demo

<div class="snippet-demo">
  <div class="snippet-demo__custom-variables">
    <p>CSS is awesome!</p>
  </div>
</div>

<style>
.snippet-demo__custom-variables {
  --some-color: #686868;
  --some-keyword: italic;
  --some-size: 1.25em;
  --some-complex-value: 1px 1px 2px whitesmoke, 0 0 1em slategray , 0 0 0.2em slategray;
}

.snippet-demo__custom-variables p {
  color: var(--some-color);
  font-size: var(--some-size);
  font-style: var(--some-keyword);
  text-shadow: var(--some-complex-value);
}
</style>

#### Explanation

Các biến được định nghĩa trên toàn cầu trong `:root` CSS giả lớp phù hợp với phần tử gốc của một cây đại diện cho tài liệu. Các biến cũng có thể được đưa vào bộ chọn nếu được xác định trong khối.
                                                     
Khai báo biến với `--variable-name:`.

Tái sử dụng các biến số trong toàn bộ tài liệu bằng cách sử dụng hàm `var(--variable-name)`.

#### Browser support

<span class="snippet__support-note">✅ No caveats.</span>

* https://caniuse.com/#feat=css-variables

<!-- tags: other -->
