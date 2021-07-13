#   Bootstrap CSS 概览
##  移动设备优先

为了让 Bootstrap 开发的网站对移动设备更加友好，确保适当的绘制和触屏缩放，需要在一个网站的 head 之中添加 veiwport meta 标签
```html
<meta name="viewport" content="width=device-width, initial-scale=1.8"> 
```

如果网站会被带有不同屏幕分辨率的设备浏览，那么将它设置为 device-width 可以确保它能正常的显示在不同的设备上。

initial-scale=1.0 确保网页在加载时，不会有任何的缩放。

在移动设备浏览器上，通过为 viewport meta 标签添加 user-scalable=no 可以禁用其缩放功能。

通常我们会同时使用 maximum-scale=1.0 与 user-scalable=no 一起使用。这样在禁用缩放功能后，用户只能滚动屏幕，就能让网站更像原生应用的感觉。

```html
<meta name="viewport" content="width=device-width, 
                                     initial-scale=1.0, 
                                     maximum-scale=1.0, 
                                     user-scalable=no">
```

##  响应式图像

```html
<img src="..." class="img-responsive" alt="响应式图像">
```

来看看这个 class 的 css 属性
```css
.img-responsive {
    display : block; 
    /*表明相关图像呈现为块级元素*/
    height : auto; 
    /* 相关元素的高度取决于浏览器 */
    max-width : 100%;
    /* 设定 max-width 为100% 会重写任何通过 width 属性指定的宽度。这让图片对响应式布局的支持更友好。 */
}
```
## 避免跨浏览器的不一致
Bootstrap 使用 Normalize 来建立跨浏览器的一致性

Normalize.css 是一个很小的 css 文件，在 HTML 元素的默认样式中提供了更好的跨浏览器一致性

## 容器(Container)
```html
<div class="container">
...
</div>
```

Bootstrap 3 的 container class 用于包裹页面上的内容。
```css
.container {
    padding-right: 15px;
    padding-left: 15px;
    margin-right: auto;
    margin-left: auto;
}
```

通过上面的代码，把 container 的左右外边距交给浏览器决定。由于内边距是固定宽度，默认情况下容器是不可嵌套的。
```css
.container:before,
.container:after {
    display: table;
    content: " ";
}
```
这会产生伪元素，设置 display 为 table ，会创建一个匿名的 table-cell 和一个新的块格式化上下文。:before 伪元素防止上边距崩塌， :after 伪元素清除浮动。

如果 conteneditable 属性出现在 HTML 中，由于一些Opera bug, 围绕上述元素创建一个空格。这可以通过使用 content "" 来修复。
```css
.container:after {
    clear: both;
}
```
它创建了一个伪元素，并确保了所有的容器包含所有的浮动元素。

Bootstrap 3 CSS 又一个申请响应的媒体查询，在不同的媒体查询阈值范围内都为 container 设置了 max-width，用以匹配网格系统。
```css
@media (min-width: 768px) {
    .container :
    width: 750px;
}
```