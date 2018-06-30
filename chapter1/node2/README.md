# CSS基础课程

## 1. 实例

### 1.1 源码
```css
h1 {color:pink;font-size: larger;}
```
```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Dobe工场</title>
        <link rel="stylesheet" type="text/css" href="mystyle.css">
        <style type="text/css">
            h1 {color:red;}
            p {color:blue;}
            #one {background-color: yellow;}
        </style>
    </head>
    <body>
        <h1>我的第一个标题</h1>
        <p id="one">我的第一个段落。</p>
        <p style="background-color:greenyellow;">这是另外一个段落。</p>
    </body>
</html>
```

### 1.2 解析

- &lt;rel="stylesheet" type="text/css" href="mystyle.css"&gt;

引入外部的样式表文件 mystyle.css，mystyle.css文件中定义了h1元素字体颜色为 pick，字体大小为大号

- h1 {color:red;}

h1元素中的字体颜色为 red

- p {color:blue;}

p元素中的字体颜色为 blue

- #one {background-color: yellow;}

id为 one 的元素背景色为 yellow

- &lt;p style="background-color:greenyellow;"&gt;这是另外一个段落。&lt;/p&gt;

该p元素有 style 样式属性，样式定义其背景色为 greenyellow

## 2. 什么是 CSS？

上一章节讲到 HTML 元素 (`<p>xxx</p>`) 是狗，那么 CSS 就是让这只狗拥有一个好看的皮囊，给这只小狗化妆的。

![](images/hashiqi.png)

### 2.1 定义
CSS 指层叠样式表 (Cascading Style Sheets)，是一种用来表现 HTML 或 XML 等文件样式的计算机语言。

- 样式定义如何显示 HTML 元素
- 样式通常存储在样式表中
- 是为了解决内容与表现分离的问题
- 多个样式定义可层叠为一

### 2.2 样式表与层叠

#### 样式表

- 外部样式表 (External style sheet)

当样式需要应用于很多页面时，外部样式表将是理想的选择。在使用外部样式表的情况下，你可以通过改变一个文件来改变整个站点的外观。每个页面使用 `<link>` 标签链接到样式表。 `<link>` 标签在（文档的）头部：
```html
<head>
    <link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```
浏览器会从文件 mystyle.css 中读到样式声明，并根据它来格式文档。

- 内部样式表 (Internal style sheet)

当单个文档需要特殊的样式时，就应该使用内部样式表。你可以使用 `<style>` 标签在文档头部定义内部样式表，就像这样:
```html
<head>
    <style type="text/css">
        h1 {color:red;}
        p {color:blue;}
        #one {background-color: yellow;}
    </style>
</head>
```

- 内联样式 (Inline style)

由于要将表现和内容混杂在一起，内联样式会损失掉样式表的许多优势。请慎用这种方法，例如当样式仅需要在一个元素上应用一次时。

要使用内联样式，你需要在相关的标签内使用样式（style）属性。Style 属性可以包含任何 CSS 属性。本例展示如何改变段落的颜色和左外边距：
```html
<p style="background-color:greenyellow;">这是另外一个段落。</p>
```

#### 层叠

- 多重样式

如果某些属性在不同的样式表中被同样的选择器定义，那么属性值将从更具体的样式表中被继承过来。 

例如，外部样式表拥有针对 h1 选择器的属性：
```css
h1 {
    color:pink;
    font-size: larger;
    }
```
而内部样式表拥有针对 h1 选择器的属性：
```css
h1 {
    color:red;
    }
```
假如拥有内部样式表的这个页面同时与外部样式表链接，那么 h1 得到的样式是：
```css
h1 {
    color:red;
    font-size: larger;
    }
```

- 多重样式优先级

式表允许以多种方式规定样式信息。样式可以规定在单个的 HTML 元素中，在 HTML 页的头元素中，或在一个外部的 CSS 文件中。甚至可以在同一个 HTML 文档内部引用多个外部样式表。

一般情况下，优先级公式如下：

<span class='label label-pill label-info'>
内联样式 > 内部样式 > 外部样式 > 浏览器默认样式
</span>

## CSS基础及语法

## CSS格式化文本及段落

## CSS与颜色、背景及图像的使用

## 使用CSS格式化列表

## a标签

## 使用CSS美化标签

## CSS选择器

## 盒子模型

## 块状元素与内联元素

## 浮动与清除浮动

## 定位

## 三角形

## 导航条

## CSS图像精灵

## 兼容性（CSS hack技巧与HTML注释语句）

## CSS整站规划