# CSS基础课程

## 1. 实例

### 1.1 源码
```css
/*这是 mystyle.css 文件*/
h1 {color:pink;font-size: larger;}
```
```html
<!-- 这是 HTML 文件 -->
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

- `<rel="stylesheet" type="text/css" href="mystyle.css">`

引入外部的样式表文件 mystyle.css，mystyle.css文件中定义了h1元素字体颜色为 pick，字体大小为大号

- `h1 {color:red;}`

h1元素中的字体颜色为 red

- `p {color:blue;}`

p元素中的字体颜色为 blue

- `#one {background-color: yellow;}`

id为 one 的元素背景色为 yellow

- `<p style="background-color:greenyellow;"></p>这是另外一个段落。</p>`

该p元素有 style 样式属性，样式定义其背景色为 greenyellow

## 2. 什么是 CSS？

上一章节讲到 HTML 元素 (`<p>xxx</p>`) 是狗，那么 CSS 就是给狗狗美颜的，让这只狗拥有好看的皮囊。

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

## 2. CSS基础及语法

CSS 规则由两个主要的部分构成：选择器，以及一条或多条声明。

![](images/grammar.png)

选择器通常是您需要改变样式的 HTML 元素。

每条声明由一个属性和一个值组成。

属性 (property) 是您希望设置的样式属性 (style attribute) 。每个属性有一个值。属性和值被冒号分开。属性与属性之间用分号隔开。

具体语法公式如下：

<span class='label label-pill label-info'>
选择器 { 属性1: 值1; 属性2: 值2; }
</span>

## 3. CSS选择器

### 3.1 概述

现在 HTML 文档中有三个 p 元素，分别表示三只狗。id 属性是相当于每只狗的编号，是唯一属性。class 属性表示狗的类名，显然，他们都属于 dog 这个类。
```html
<p id="dog001" class="dog">编号为001的狗</p>
<p id="dog002" class="dog">编号为002的狗</p>
<p id="dog003" class="dog">编号为003的狗</p>
```
现在需要完成两件事：

1. 把所有的“狗”字体颜色改为白色 (white)
2. 编号为002的“狗”字体大小改为 16pt

我们的 CSS 样式可以这样美颜：
```css
.dog { color: white; }
#dog002 { font-size: 16pt; }
```
`.dog`是一个 class 选择器，它表示选择所有 class 属性为 dog 的元素。

`#dog002`是一个 id 选择器，它表示选择 id 属性为 dog002 的元素，选择的元素是唯一的。

### 3.2 CSS选择器

除了上面讲到的 id 选择器和 class 选择器以外，CSS 还提供了各种不同的选择方案，用于选择你想要的元素。

下面是 CSS 提供一些常用的基本选择器。

*如需了解更多选择器，请访问：http://www.runoob.com/cssref/css-selectors.html*

<table class="table-css-select">
    <tr>
        <th width="22%">选择器</th>
        <th width="17%">示例</th>
        <th width="56%">示例说明</th>
        <th>CSS</th>
    </tr>
    <tr>
        <td>.<i>class</i></td>
        <td>.intro</td>
        <td>选择所有class="intro"的元素</td>
        <td>1</td>
    </tr>
    <tr>
        <td>#<i>id</i></td>
        <td>#firstname</td>
        <td>选择所有id="firstname"的元素</td>
        <td>1</td>
    </tr>
    <tr>
        <td>*</td>
        <td class="code notranslate">*</td>
        <td>选择所有元素</td>
        <td>2</td>
    </tr>
    <tr>
        <td><i>element</i></td>
        <td>p</td>
        <td>选择所有&lt;p&gt;元素</td>
        <td>1</td>
    </tr>
    <tr>
        <td><i>element,element</i></td>
        <td>div,p</td>
        <td>选择所有&lt;div&gt;元素和&lt;p&gt;元素</td>
        <td>1</td>
    </tr>
    <tr>
        <td><i>element</i> <i>element</i></td>
        <td>div p</td>
        <td>选择&lt;div&gt;元素内的所有&lt;p&gt;元素</td>
        <td>1</td>
    </tr>
    <tr>
        <td><i>element</i>&gt;<i>element</i></td>
        <td>div&gt;p</td>
        <td>选择所有父级是 &lt;div&gt; 元素的 &lt;p&gt; 元素</td>
        <td>2</td>
    </tr>
    <tr>
        <td>[<i>attribute</i>=<i>value</i>]</td>
        <td>[target=-blank]</td>
        <td>选择所有使用target="-blank"的元素</td>
        <td>2</td>
    </tr>
    <tr>
        <td>:link</td>
        <td>a:link</td>
        <td>选择所有未访问链接</td>
        <td>1</td>
    </tr>
    <tr>
        <td>:visited</td>
        <td>a:visited</td>
        <td>选择所有访问过的链接</td>
        <td>1</td>
    </tr>
    <tr>
        <td>:active</td>
        <td>a:active</td>
        <td>选择活动链接</td>
        <td>1</td>
    </tr>
    <tr>
        <td>:hover</td>
        <td>a:hover</td>
        <td>选择鼠标在链接上面时</td>
        <td>1</td>
    </tr>
    <tr>
        <td>:focus</td>
        <td>input:focus</td>
        <td>选择具有焦点的输入元素</td>
        <td>2</td>
    </tr>
    <tr>
        <td>:first-child</td>
        <td>p:first-child</td>
        <td>指定只有当&lt;p&gt;元素是其父级的第一个子级的样式。</td>
        <td>2</td>
    </tr>
    <tr>
        <td>:before</td>
        <td>p:before</td>
        <td>在每个&lt;p&gt;元素之前插入内容</td>
        <td>2</td>
    </tr>
    <tr>
        <td>:after</td>
        <td>p:after</td>
        <td>在每个&lt;p&gt;元素之后插入内容</td>
        <td>2</td>
    </tr>
</table>

## 4. CSS 属性组

上节讲了如何选择“狗” (元素)，本节将介绍选择好“狗” (元素)后，做了简单的改变字体颜色和大小的“美颜”。本节将介绍除了字体颜色和大小外，还有哪些“美颜”功能。

HTML 页面上不同的内容有不同的“美颜”方式，比如，文字的“美颜”是调整颜色、大小等属性，图片的“美颜”是调整图片长款等属性。下面我们介绍一些常用的“美颜”属性组，以及其包含的属性用法。

### 4.1 颜色属性

- **color**

规定文本的字体颜色

属性值 | 描述
:--| :--
*color_name* | 规定颜色值为颜色名称的颜色（比如 red）
*hex_number* | 规定颜色值为十六进制值的颜色（比如 #ff0000）
*rgb_number* | 规定颜色值为 rgb 代码的颜色（比如 rgb(255,0,0)）
inherit | 规定应该从父元素继承颜色

*源码*
```html
<style>
    #color-1 { color:red; }
    #color-2 { color:#00ff00; }
    #color-3 { color:rgb(0,0,255); }
    #color-4 { color:inherit; }
</style>
<div id="color-1">这是 div1</div>
<div id="color-2">这是 div2</div>
<div id="color-3">
    这是 div3
    <div id="color-4">
        这是 div4
    </div>
</div>
```
*效果*
<div class="preview-code">
    <div id="color-1">这是 div1</div>
    <div id="color-2">这是 div2</div>
    <div id="color-3">
        这是 div3
        <div id="color-4">
            这是 div4
        </div>
    </div>
</div>

### 4.2 字体属性

- **font-family**

规定文本的字体系列

属性值 | 描述
:--| :--
family-name,generic-family | 用于某个元素的字体族名称或/及类族名称的一个优先表。默认值：取决于浏览器
inherit	| 规定应该从父元素继承字体系列

*源码*
```html
<style>
    #font-family-1 { font-family:"Times New Roman",Georgia,Serif; }
</style>
<div id="font-family-1">这是 div1</div>
```
*效果*
<div class="preview-code">
    <div id="font-family-1">这是 div1</div>
</div>

- **font-size**

规定文本的字体尺寸

属性值 | 描述
:--| :--
xx-small<br />x-small<br />small<br />medium<br />large<br />x-large<br />xx-large | 绝对字体大小。把字体的尺寸设置为不同的尺寸，从 xx-small 到 xx-large，每种尺寸比前一种大20%。通常情况下，small 为 12px。默认值是 medium
smaller<br />larger	| 相对字体大小。把 font-size 设置为比父元素更小或更大的尺寸
px | 把 font-size 设置为一个固定的值（比如，16px）
em/% | 把 font-size 设置为基于父元素的一个百分比值，1em = 100%
inherit	规定应该从父元素继承字体尺寸

*源码*
```html
<style>
    #font-size-1 { font-size:xx-small; }
    #font-size-2 { font-size:18px; }
    #font-size-3 { font-size:1.5em; }
    #font-size-4 { font-size:inherit; }
</style>
<div>标准字体</div>
<div id="font-size-1">这是 div1</div>
<div id="font-size-2">这是 div2</div>
<div id="font-size-3">
    这是 div3
    <div id="font-size-4">
        这是 div4
    </div>
</div>
```
*效果*
<div class="preview-code">
    <div>标准字体</div>
    <div id="font-size-1">这是 div1</div>
    <div id="font-size-2">这是 div2</div>
    <div id="font-size-3">
        这是 div3
        <div id="font-size-4">
            这是 div4
        </div>
    </div>
</div>

- **font-weight**

规定字体粗细

属性值 | 描述
:--| :--
normal | 默认值。定义标准的字符。
bold | 定义粗体字符。
bolder | 定义更粗的字符。
lighter | 定义更细的字符。
100~900 | 定义由粗到细的字符。400 等同于 normal，而 700 等同于 bold。
inherit	| 规定应该从父元素继承字体的粗细。

*源码*
```html
<style>
    #font-weight-1 { font-weight:lighter; }
    #font-weight-2 { font-weight:bold; }
    #font-weight-3 { font-weight:900; }
    #font-weight-4 { font-weight:inherit; }
</style>
<div>标准字体</div>
<div id="font-weight-1">这是 div1</div>
<div id="font-weight-2">这是 div2</div>
<div id="font-weight-3">
    这是 div3
    <div id="font-weight-4">
        这是 div4
    </div>
</div>
```
*效果*
<div class="preview-code">
    <div>标准字体</div>
    <div id="font-weight-1">这是 div1</div>
    <div id="font-weight-2">这是 div2</div>
    <div id="font-weight-3">
        这是 div3
        <div id="font-weight-4">
            这是 div4
        </div>
    </div>
</div>


### 4.3 背景属性

- **background-color**

background-color属性设置一个元素的背景颜色。

元素的背景是元素的总大小，包括填充和边界（但不包括边距）。

属性值 | 描述
:--| :--
*color* | 指定背景颜色，同 color 属性的值相同
transparent | 指定背景颜色应该是透明的。这是默认
inherit | 指定背景颜色，应该从父元素继承

*源码*
```html
<style>
    #background-color-1 { background-color:lighter; }
    #background-color-2 { background-color:transparent; }
    #background-color-3 { background-color:yellow; }
    #background-color-4 { background-color:inherit; }
</style>
<div id="background-color-1">这是 div1</div>
<div id="background-color-2">这是 div2</div>
<div id="background-color-3">
    这是 div3
    <div id="background-color-4">
        这是 div4
    </div>
</div>
```
*效果*
<div class="preview-code">
    <div id="background-color-1">这是 div1</div>
    <div id="background-color-2">这是 div2</div>
    <div id="background-color-3">
        这是 div3
        <div id="background-color-4">
            这是 div4
        </div>
    </div>
</div>

- **background-image**

background-image属性设置一个元素的背景图像。

元素的背景是元素的总大小，包括填充和边界（但不包括边距）。

默认情况下，background-image放置在元素的左上角，并重复垂直和水平方向。

属性值 | 描述
:--| :--
url('URL') | 图像的URL
none | 无图像背景会显示。这是默认
inherit | 指定背景图像应该从父元素继承

*源码*
```html
<style>
    #background-image-1 { background-image:url(../images/bgimage.png); }
    #background-image-2 { background-image:none; }
    #background-image-3 { background-image:url(../images/bgimage.png); }
    #background-image-4 { background-image:inherit; }
</style>
<div id="background-image-1">这是 div1</div>
<div id="background-image-2">这是 div2</div>
<div id="background-image-3">
    这是 div3
    <div id="background-image-4">
        这是 div4
    </div>
</div>
```
*效果*
<div class="preview-code">
    <div id="background-image-1">这是 div1</div>
    <div id="background-image-2">这是 div2</div>
    <div id="background-image-3">
        这是 div3
        <div id="background-image-4">
            这是 div4
        </div>
    </div>
</div>

- **background-position**

background-position属性设置背景图像的起始位置。

必须先指定background-image属性。

属性值 | 描述
:--| :--
left top<br />left center<br />left bottom<br />right top<br />right center<br />right bottom<br />center top<br />center center<br />center bottom | 如果仅指定一个关键字，其他值将会是"center"。<br />比如，横向（left,center,right），纵向（top,center,bottom）
x% y% | 第一个值是水平位置，第二个值是垂直。左上角是0％0％。右下角是100％100％。如果仅指定了一个值，其他值将是50％。 。默认值为：0％0％
xpos ypos | 第一个值是水平位置，第二个值是垂直。左上角是0。单位可以是像素（0px0px）或任何其他 CSS单位。如果仅指定了一个值，其他值将是50％。你可以混合使用％和positions
inherit | 指定background-position属性设置应该从父元素继承

- **background-repeat**

设置背景图像如何铺排填充。

必须先指定background-image属性。

属性值 | 描述
:--| :--
repeat | 背景图像将向垂直和水平方向重复。这是默认
repeat-x | 只有水平位置会重复背景图像
repeat-y | 只有垂直位置会重复背景图像
no-repeat | background-image不会重复
inherit | 指定background-repea属性设置应该从父元素继承

### 4.4 文本属性

- **text-align**

text-align属性指定元素文本的水平对齐方式。

属性值 | 描述
:--| :--
left | 把文本排列到左边。默认值：由浏览器决定。
right | 把文本排列到右边。
center | 把文本排列到中间。
justify | 实现两端对齐文本效果。
inherit | 规定应该从父元素继承 text-align 属性的值。

*源码*
```html
<style>
    #text-align-1 { text-align:right; }
    #text-align-2 { text-align:center; }
    #text-align-3 { text-align:justify; }
    #text-align-4 { text-align:inherit; }
</style>
<div>默认标准</div>
<div id="text-align-1">这是 div1</div>
<div id="text-align-2">这是 div2</div>
<div id="text-align-3">
    这是 div3
    <div id="text-align-4">
        这是 div4
    </div>
</div>
```
*效果*
<div class="preview-code">
    <div>默认标准</div>
    <div id="text-align-1">这是 div1</div>
    <div id="text-align-2">这是 div2</div>
    <div id="text-align-3">
        这是 div3
        <div id="text-align-4">
            这是 div4
        </div>
    </div>
</div>

- **line-height**

设置以百分比计的行高，即每一行的高度。

负值是不允许的。

属性值 | 描述
:--| :--
normal | 默认。设置合理的行间距。
*number* | 设置数字，此数字会与当前的字体尺寸相乘来设置行间距。
*length* | 设置固定的行间距。比如（line-height:20px;）
% | 基于当前字体尺寸的百分比行间距。
inherit | 规定应该从父元素继承 line-height 属性的值。

*源码*
```html
<style>
    #line-height-1 { line-height:2; }
    #line-height-2 { line-height:30px; }
    #line-height-3 { line-height:100%; }
    #line-height-4 { line-height:inherit; }
</style>
<div>默认标准</div>
<div id="line-height-1">DOBE工场</div>
<div id="line-height-2">DOBE工场</div>
<div id="line-height-3">
    DOBE工场
    <div id="line-height-4">
        DOBE工场
    </div>
</div>
```
*效果*
<div class="preview-code">
    <div>默认标准</div>
    <div id="line-height-1">DOBE工场</div>
    <div id="line-height-2">DOBE工场</div>
    <div id="line-height-3">
        DOBE工场
        <div id="line-height-4">
            DOBE工场
        </div>
    </div>
</div>

- **letter-spacing**

letter-spacing 属性增加或减少字符间的空白（字符间距）

属性值 | 描述
:--| :--
normal | 默认。规定字符间没有额外的空间。
*length* | 定义字符间的固定空间（允许使用负值）。
inherit | 规定应该从父元素继承 letter-spacing 属性的值。

*源码*
```html
<style>
    #letter-spacing-1 { letter-spacing:5px; }
    #letter-spacing-2 { letter-spacing:-5px; }
    #letter-spacing-3 { letter-spacing:10px; }
    #letter-spacing-4 { letter-spacing:inherit; }
</style>
<div>默认标准</div>
<div id="letter-spacing-1">DOBE工场</div>
<div id="letter-spacing-2">DOBE工场</div>
<div id="letter-spacing-3">
    DOBE工场
    <div id="letter-spacing-4">
        DOBE工场
    </div>
</div>
```
*效果*
<div class="preview-code">
    <div>DOBE工场</div>
    <div id="letter-spacing-1">DOBE工场</div>
    <div id="letter-spacing-2">DOBE工场</div>
    <div id="letter-spacing-3">
        DOBE工场
        <div id="letter-spacing-4">
            DOBE工场
        </div>
    </div>
</div>

- **text-indent**

text-indent 属性规定文本块中首行文本的缩进。

负值是允许的。如果值是负数，将第一行左缩进。

属性值 | 描述
:--| :--
*length* | 定义固定的缩进。默认值：0。
% | 定义基于父元素宽度的百分比的缩进。
inherit | 规定应该从父元素继承 text-indent 属性的值。

*源码*
```html
<style>
    #text-indent-1 { text-indent:5px; }
    #text-indent-2 { text-indent:50%; }
    #text-indent-3 { text-indent:10px; }
    #text-indent-4 { text-indent:inherit; }
</style>
<div>默认标准</div>
<div id="text-indent-1">DOBE工场</div>
<div id="text-indent-2">DOBE工场</div>
<div id="text-indent-3">
    DOBE工场
    <div id="text-indent-4">
        DOBE工场
    </div>
</div>
```
*效果*
<div class="preview-code">
    <div>默认标准</div>
    <div id="text-indent-1">DOBE工场</div>
    <div id="text-indent-2">DOBE工场</div>
    <div id="text-indent-3">
        DOBE工场
        <div id="text-indent-4">
            DOBE工场
        </div>
    </div>
</div>

### 4.5 边框属性

- **border-style**

border-style属性设置一个元素的四个边框的样式。

此属性可以有一到四个值。四个值赋值分别是：上-右-下-左 的顺时针方式。

属性值 | 描述
:--| :--
none | 定义无边框。
hidden | 与 "none" 相同。不过应用于表时除外，对于表，hidden 用于解决边框冲突。
dotted | 定义点状边框。在大多数浏览器中呈现为实线。
dashed | 定义虚线。在大多数浏览器中呈现为实线。
solid | 定义实线。
double | 定义双线。双线的宽度等于 border-width 的值。
groove | 定义 3D 凹槽边框。其效果取决于 border-color 的值。
ridge | 定义 3D 垄状边框。其效果取决于 border-color 的值。
inset | 定义 3D inset 边框。其效果取决于 border-color 的值。
outset | 定义 3D outset 边框。其效果取决于 border-color 的值。
inherit | 规定应该从父元素继承边框样式。

*源码*
```html
<style>
    #border-style-1 {
        border-style:dotted dashed solid double;
        height: 100px;
        width: 200px;
        }
</style>
<div id="border-style-1">DOBE工场</div>
```
*效果*
<div class="preview-code">
    <div id="border-style-1">DOBE工场</div>
</div>

- **border-width**

border-width属性设置一个元素的四个边框的宽度。

此属性可以有一到四个值。

属性值 | 描述
:--| :--
thin | 定义细的边框。
medium | 默认。定义中等的边框。
thick | 定义粗的边框。
*length* | 允许您自定义边框的宽度。
inherit | 规定应该从父元素继承边框宽度。

*源码*
```html
<style>
    #border-width-1 {
        border-style:solid;
        border-width:thin medium thick 10px;
        height: 100px;
        width: 200px;
        }
</style>
<div id="border-width-1">DOBE工场</div>
```
*效果*
<div class="preview-code">
    <div id="border-width-1">DOBE工场</div>
</div>

- **border-color**

border-color属性设置一个元素的四个边框颜色。

此属性可以有一到四个值。

属性值 | 描述
:--| :--
*color* | 指定背景颜色
transparent | 指定边框的颜色应该是透明的。这是默认
inherit | 指定边框的颜色，应该从父元素继承

*源码*
```html
<style>
    #border-color-1 {
        border-style:solid;
        border-color:red blue;
        height: 100px;
        width: 200px;
        }
</style>
<div id="border-color-1">DOBE工场</div>
```
*效果*
<div class="preview-code">
    <div id="border-color-1">DOBE工场</div>
</div>

- **border**

缩写边框属性设置在一个声明中所有的边框属性。

可以设置的属性分别（按顺序）：border-width, border-style,和border-color.

如果上述值缺少一个没有关系，例如border：＃FF0000;是允许的。

属性值 | 描述
:--| :--
*border-width* | 指定边框的宽度
*border-style* | 指定边框的样式
*border-color* | 指定边框的颜色
inherit	指定应该从父元素继承border属性值

*源码*
```html
<style>
    .border { margin: 10px; }
    #border-1 { border:5px solid red; }
    #border-2 { border:solid red; }
    #border-3 { border:5px red; }
</style>
<div id="border-1">DOBE工场</div>
```
*效果*
<div class="preview-code">
    <div id="border-1" class="border">DOBE工场</div>
    <div id="border-2" class="border">DOBE工场</div>
    <div id="border-3" class="border">DOBE工场</div>
</div>

- **outline**

outline（轮廓）是绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用。

outline简写属性在一个声明中设置所有的轮廓属性。

可以设置的属性分别是（按顺序）：outline-color, outline-style, outline-width

如果不设置其中的某个值，也不会出问题，比如 outline:solid #ff0000; 也是允许的。

属性值 | 描述
:--| :--
*outline-color* | 规定边框的颜色。
*outline-style* | 规定边框的样式。
*outline-width* | 规定边框的宽度。
inherit	规定应该从父元素继承 outline 属性的设置。

*源码*
```html
<style>
    #outline-1 { border:1px solid red; outline:green dotted thick; }
</style>
<div id="border-1">DOBE工场</div>
```
*效果*
<div class="preview-code">
    <div id="outline-1">DOBE工场</div>
</div>

### 4.6 列表属性

- **list-style-type**

list-style-type 属性设置列表项标记的类型。

属性值 | 描述
:--| :--
none | 无标记。
disc | 默认。标记是实心圆。
circle | 标记是空心圆。
square | 标记是实心方块。
decimal | 标记是数字。
decimal-leading-zero | 0开头的数字标记。(01, 02, 03, 等。)
lower-roman | 小写罗马数字(i, ii, iii, iv, v, 等。)
upper-roman | 大写罗马数字(I, II, III, IV, V, 等。)
lower-alpha | 小写英文字母The marker is lower-alpha (a, b, c, d, e, 等。)
upper-alpha | 大写英文字母The marker is upper-alpha (A, B, C, D, E, 等。)
lower-greek | 小写希腊字母(alpha, beta, gamma, 等。)
lower-latin | 小写拉丁字母(a, b, c, d, e, 等。)
upper-latin | 大写拉丁字母(A, B, C, D, E, 等。)
hebrew | 传统的希伯来编号方式
armenian | 传统的亚美尼亚编号方式
georgian | 传统的乔治亚编号方式(an, ban, gan, 等。)
cjk-ideographic | 简单的表意数字
hiragana | 标记是：a, i, u, e, o, ka, ki, 等。（日文片假名）
katakana | 标记是：A, I, U, E, O, KA, KI, 等。（日文片假名）
hiragana-iroha | 标记是：i, ro, ha, ni, ho, he, to, 等。（日文片假名）
katakana-iroha | 标记是：I, RO, HA, NI, HO, HE, TO, 等。（日文片假名）

*源码*
```html
<style>
    #list-style-type-1 { list-style-type:circle;}
    #list-style-type-2 { list-style-type:upper-latin;}
</style>
<ul id="list-style-type-1">
    <li>Coffee</li>
    <li>Tea</li>
    <li>Coca Cola</li>
</ul>
<ol id="list-style-type-2">
  <li>Coffee</li>
  <li>Tea</li>
  <li>Coca Cola</li>
</ol>
```
*效果*
<div class="preview-code">
    <ul id="list-style-type-1">
        <li>Coffee</li>
        <li>Tea</li>
        <li>Coca Cola</li>
    </ul>
    <ol id="list-style-type-2">
        <li>Coffee</li>
        <li>Tea</li>
        <li>Coca Cola</li>
    </ol>
</div>

- **list-style-position**

list-style-position属性指示如何相对于对象的内容绘制列表项标记。

属性值 | 描述
:--| :--
inside | 列表项目标记放置在文本以内，且环绕文本根据标记对齐。
outside | 默认值。保持标记位于文本的左侧。列表项目标记放置在文本以外，且环绕文本不根据标记对齐。
inherit | 规定应该从父元素继承 list-style-position 属性的值。

*源码*
```html
<style>
    #list-style-position-1 { list-style-position:inside;}
    #list-style-position-2 { list-style-position:outside;}
</style>
<ul id="list-style-position-1">
    <li>Coffee</li>
    <li>Tea</li>
    <li>Coca Cola</li>
</ul>
<ul id="list-style-position-2">
  <li>Coffee</li>
  <li>Tea</li>
  <li>Coca Cola</li>
</ul>
```
*效果*
<div class="preview-code">
    <ul id="list-style-position-1">
        <li>Coffee</li>
        <li>Tea</li>
        <li>Coca Cola</li>
    </ul>
    <ul id="list-style-position-2">
        <li>Coffee</li>
        <li>Tea</li>
        <li>Coca Cola</li>
    </ul>
</div>

- **list-style-image**

list-style-image 属性使用图像来替换列表项的标记。

请始终规定一个 "list-style-type" 属性以防图像不可用。

属性值 | 描述
:--| :--
*URL* | 图像的路径。
none | 默认。无图形被显示。
inherit | 规定应该从父元素继承 list-style-image 属性的值。

*源码*
```html
<style>
    #list-style-image-1 { list-style-image:url(../images/tubiao.png);}
</style>
<ul id="list-style-image-1">
    <li>Coffee</li>
    <li>Tea</li>
    <li>Coca Cola</li>
</ul>
```
*效果*
<div class="preview-code">
    <ul id="list-style-image-1">
        <li>Coffee</li>
        <li>Tea</li>
        <li>Coca Cola</li>
    </ul>
</div>

- **list-style**

list-style 简写属性在一个声明中设置所有的列表属性。

可以设置的属性（按顺序）： list-style-type, list-style-position, list-style-image.

可以不设置其中的某个值，比如 "list-style:circle inside;" 也是允许的。未设置的属性会使用其默认值。

属性值 | 描述
:--| :--
*list-style-type* | 设置列表项标记的类型。
*list-style-position* | 设置在何处放置列表项标记。
*list-style-image* | 使用图像来替换列表项的标记。
*initial* | 将这个属性设置为默认值。
*inherit* | 规定应该从父元素继承 list-style 属性的值。

*源码*
```html
<style>
    #list-style-1 { list-style:square url(../images/tubiao.png);}
</style>
<ul id="list-style-1">
    <li>Coffee</li>
    <li>Tea</li>
    <li>Coca Cola</li>
</ul>
```
*效果*
<div class="preview-code">
    <ul id="list-style-1">
        <li>Coffee</li>
        <li>Tea</li>
        <li>Coca Cola</li>
    </ul>
</div>

## 盒子模型

## 块状元素与内联元素

## 浮动与清除浮动

## 定位

## 三角形

## 导航条

## CSS图像精灵

## 兼容性（CSS hack技巧与HTML注释语句）

## CSS整站规划