#   CSS 语法
##  CSS 实例
CSS 规则由两个主要部分构成：选择器，以及一或多条声明：
```css
h1 {
    color: blue;
    font-size: 12px;
}
```

选择器通常是我需要改变的 HTML 元素。

每条声明都由一个属性和一个值组成。

## CSS Id 和 Class
### Id 选择器
用 id 选择器可以标有特定 id 的 HTML 元素指定特定的样式
```html
<div id="para1">red</div>
```
```css
#para1
{
    text-align: center;
    color: red;
}
```

### Class 选择器
class 选择器用于描述一组元素的样式，class 选择器可以在多个元素中使用，而 id 选择器只能在单一元素中使用。
```html
<div class="center">center</div>
```
```css
.center
{
    text-align: center;
    color: blue;
}
```
上面的 css 代码表明，所有拥有 center 类的 html 元素均为居中

你也可以指定特定的 html 元素使用 class
```css
p.center
{
    text-align: center;
}
```
上面的代码表明，所有的 p 元素使用 class="center" 让该元素的文本居中

## CSS 创建
### 如何插入样式表
插入样式表的方法有三种：

#### 外部样式表
当样式需要应用于很多页面时，使用外部样式表。
```html
<head>
    <link rel="stylesheet" type="text/css" href="index.css">
</head>
```
浏览器会从文件 mystyle.css 中读到样式声明，并根据它来格式文档。

#### 内部样式表
当单个文档需要特殊的样式时，就应该使用内部样式表。我可以使用 style 标签在文档头部定义内部样式表， 如
```html
<head>
    <style>
        hr {
            color:sienna;
        }

        p {
            margin-left: 20px;
        }

        body {
            background-image: url("images/back40.gif");
        }
    </style>
</head>
```

#### 多重样式
如果某些属性在不同的样式表中被同样的选择器定义，那么属性值将从更具体的样式表中被继承过来
如：
外部样式表具有针对 h3 选择器的三个属性：
```css
h3
{
    color: red;
    text-align: left;
    font-size:8pt;
}
```
而内部样式表具有针对 h3 选择器的两个属性：
```css
h3
{
    text-align: right;
    font-size: 20pt;
}
```
如果具有内部样式表的这个页面同时于外部样式表链接，那么 h3 得到的样式是：
```css
h3
{
    color: red;
    text-align: right;
    font-size:20pt;
}
```

#### 多重样式优先级
内联 > 内部 > 外部 > 浏览器默认样式