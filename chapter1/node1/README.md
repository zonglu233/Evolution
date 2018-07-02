# HTML 基础课程

## 1. 实例

### 1.1 源码

```html
<!-- 这是 HTML 文件 -->
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Dobe工场</title>
    </head>
    <body>
        <h1>我的第一个标题</h1>
        <p>我的第一个段落。</p>
        <p>这是另外一个段落。</p>
    </body>
</html>
```

### 1.2 解析

- `<!-- 这是 HTML 文件 -->`

注释，浏览器不执行该语句

- `<!DOCTYPE html>`

声明该 HTML 为 HTML5 文档

- `<html>`

html元素是 HTML 页面的根元素

- `<head>`

head元素包含了文档的元（meta）数据

- `<meta>`

meta元素指定网页的描述，关键词，文件的最后修改时间，作者及其他元数据。

- `<title>`

title元素描述了文档的标题

- `<body>`

body元素包含了可见的页面内容

- `<h1>`

h1元素定义一个大标题

- `<p>`

p元素定义一个段落

### 1.3 可视化页面结构

上面是一个可视化的 HTML 页面结构：

![](images/1.png)

<div class='tips'>
<strong>Tips!</strong>
只有 &lt;body&gt; 区域 (白色部分) 才会在浏览器中显示。
</div>

## 2. 什么是 HTML？

HTML 是用来描述网页的一种语言。

- HTML 指的是超文本标记语言: HyperText Markup Language
- HTML 不是一种编程语言，而是一种标记语言
- 标记语言是一套标记标签 (markup tag)
- HTML 使用标记标签来描述网页
- HTML 文档包含了 HTML 标签及文本内容
- HTML 文档也叫做 web 页面
- 万维网联盟 (W3C) 制定 HTML 标准

## 3. HTML 组成

### 3.1 HTML 标签 (tag)

- HTML 标签是由尖括号包围的关键词，比如 `<html>`
- HTML 标签通常是成对出现的，比如 `<b>` 和 `</b>`
- 标签对中的第一个标签是开始标签，第二个标签是结束标签
- 开始和结束标签也被称为开放标签和闭合标签

### 3.2 HTML 元素 (element)

- HTML 元素以开始标签起始
- HTML 元素以结束标签终止
- 元素的内容是开始标签与结束标签之间的内容
- 某些 HTML 元素具有空内容（empty content）
- 空元素在开始标签中进行关闭（以开始标签的结束而结束）
- 大多数 HTML 元素可拥有属性

### 3.3 总结

很多人对元素和标签不理解，会混为一谈，其实只要看懂下面的公式：

<span class='label label-pill label-info'>
狗头 + 狗身 + 狗尾 = 狗<br/>开始标签 + 内容 + 结束标签 = 元素
</span>

![](images/2.gif)

也就是说元素由一个开始的标签和结束的标签组成，用来包含某些内容。

`<p>`这就是一个标签 (狗头)

`<p>这里是内容</p>` 这就是一个元素 (狗)

<div class='tips'>
<strong>Tips!</strong>
没有内容的 HTML 元素被称为空元素。空元素是在开始标签中关闭的。&lt;br&gt; 就是没有关闭标签的空元素 (&lt;br&gt; 标签定义换行) 。在 XHTML、XML 以及未来版本的 HTML 中，所有元素都必须被关闭。在开始标签中添加斜杠，比如 &lt;br/&gt;，是关闭空元素的正确方法，HTML、XHTML 和 XML 都接受这种方式。即使 &lt;br&gt;  在所有浏览器中都是有效的，但使用 &lt;br/&gt; 其实是更长远的保障。
</div>

## 4. HTML 网页运行原理

一个 HTML 文件，记事本打开是代码。浏览器打开，则是可视化页面。Why？

从我们在地址栏输入地址到看到页面，这个过程中都发生了什么？

### 4.1 文档对象模型 (Document Object Model)

文档对象模型 (Document Object Model，简称 DOM)，是 W3C 组织推荐的处理可扩展标志语言的标准编程接口。在网页上，组织页面 (或文档) 的对象被组织在一个树形结构中，用来表示文档中对象的标准模型就称为 DOM。

下面是一个 DOM 树模型图：

![](images/1.gif)

下面是红楼梦家谱图：

![](images/2.png)

### 4.2 渲染引擎 (The Rendering Engine)

Web 浏览器 (如谷歌浏览器，Internet Explorer，Firefox，Safari) 读取 HTML 文件后，并不是直接显示的 HTML 标签，通过解析标签展示不同的页面效果，这些操作都归功于浏览器的渲染引擎。

渲染引擎是一种对 HTML 文档进行解析并将其显示在页面上的工具。它负责取得网页的内容 (HTML、XML、图象等等)、整理信息 (例如加入 CSS 等)，以及计算网页的显示方式然后会输出至显示器或打印机。

### 4.3 渲染引擎工作原理

- 构建 DOM 树

渲染引擎开始解析 HTML 文档，并将文档的标签转化为内容树中的 DOM 节点

- 构建 Render 树

渲染引擎解析外部 CSS 文件及 style 标签中的样式信息，这些样式信息以及 HTML 中的可见性指令将被用来构建另一棵树——Render 树。Render 树由一些包含有颜色和大小等属性的矩形组成，它们将被按照正确的顺序显示到屏幕上。

- 布局 Render 树

Render 树构建好了之后，将会执行布局过程，它将确定每个节点在屏幕上的确切坐标。

- 绘制 DOM 树

渲染引擎会遍历所有的 DOM 节点，并使用 UI 后端层绘制。

<div class='tips'>
<strong>Tips!</strong>
渲染过程是逐步完成的，为了更好的用户体验，渲染引擎将会尽可能早的将内容呈现到屏幕上，并不会等到所有的HTML都解析完成之后再去构建和布局Render树。而是解析完一部分内容就显示一部分内容，同时，可能还在通过网络下载其余内容。
</div>

### 4.4 主流浏览器的渲染引擎工作流程

- Webkit 工作流程

Safari 和 Chrome 都使用 Webkit，Webkit 是一款开源渲染引擎，它本来是为 Linux 平台研发的，后来由 Apple 移植到 Mac 及 Windows 上。

![](images/webkit.png)

- Gecko 工作流程

Firefox 使用 Geoko——Mozilla 自主研发的渲染引擎。

![](images/gecko.jpg)

- 总结

Webkit 和 Gecko 属于不同，但流程基本相同。 Gecko 将视觉化后的树称为“框架树”，Webkit 称为“渲染树”；对于元素的排放，Webkit 称为“布局 layout”，gecko 称为“重拍 reflow”；Gecko 在 html 解析和 DOM 树间添加了“内容槽”，用于生成 DOM 元素；将 DOM 树和样式信息构建渲染树的过程，Webkit 称为“附加”，Gecko 称为“框架结构”。

## 2. HTML 标签

`<p>这里是内容</p>` 表示小狗，如果一个 HTML 页面只有小狗一种动物，会显得很单调，而且有些事情小狗做不了，还应该有会飞的天鹅、会游泳的癞蛤蟆等其他动物。所以，万维网联盟 (W3C) 在指定 HTML 标准的时候，定义了丰富的标签元素供开发人员使用，并不断更新。

2014年10月29日，W3C宣布，新的 HTML 标准规范终于制定完成，也是 HTML 标准的第五次重大修改，所以我们习惯称之为 HTML 5.0。HTML 5.0 在它的前辈 HTML4.01 基础上，增加了一些标签元素，同时也废除了部分标签元素。

下面是 HTML 部分常用的标签元素。其中，打 * 标签表示使用不广泛使用或部分浏览器不兼容，了解即可。

<span class="new">New</span> - HTML5 新增标签

*参考链接：http://www.runoob.com/tags/ref-byfunc.html*

### 2.1 基础标签

| 标签           | 描述               |
| :------------- | :----------------- |
| `<!DOCTYPE>`   | 声明文档类型       |
| `<html>`       | 定义一个 HTML 文档 |
| `<title>`      | 为文档定义一个标题 |
| `<body>`       | 定义文档的主体     |
| `<h1> to <h6>` | 定义 HTML 标题     |
| `<p>`          | 定义一个段落       |
| `<br>`         | 定义简单的折行     |
| `<hr>`         | 定义水平线         |
| `<!--...-->`   | 定义一个注释       |

### 2.2 元信息标签

| 标签     | 描述                                   |
| :------- | :------------------------------------- |
| `<head>` | 定义关于文档的信息                     |
| `<meta>` | 定义关于 HTML 文档的元信息             |
| `<base>` | 定义页面中所有链接的默认地址或默认目标 |

### 2.3 样式/节标签

| 标签          | 描述                     |
| :------------ | :----------------------- |
| `<style>`     | 定义文档的样式信息       |
| `<div>`       | 定义文档中的块           |
| `<span>`      | 定义文档中的段落         |
| `<header>`    | 定义一个文档头部部分     |
| `<footer>`    | 定义一个文档底部         |
| `<section>`   | 定义了文档的某个区域     |
| `<article>`\* | 定义一个文章内容         |
| `<aside>`\*   | 定义其所处内容之外的内容 |

### 2.4 格式标签

| 标签                                 | 描述                       |
| :----------------------------------- | :------------------------- |
| `<b>`                                | 定义粗体文本               |
| `<i>`                                | 定义斜体文本               |
| `<u>`                                | 定义下划线文本             |
| `<del>`                              | 定义被删除文本             |
| `<s>`                                | 标记不再正确的文本         |
| `<small>`                            | 定义小号文本               |
| `<strong>`                           | 定义语气更为强烈的强调文本 |
| `<mark>`<span class="new">New</span> | 定义带有记号的文本         |
| `<pre>`\*                            | 定义预格式文本             |
| `<abbr>`\*                           | 定义一个缩写               |

### 2.5 图像标签

| 标签                                   | 描述                                                          |
| :------------------------------------- | :------------------------------------------------------------ |
| `<img>`                                | 定义图像                                                      |
| `<map>`                                | 定义图像映射                                                  |
| `<area>`                               | 定义图像地图内部的区域                                        |
| `<canvas>`<span class="new">New</span> | 通过脚本（通常是 JavaScript）来绘制图形（比如图表和其他图像） |
| `<figure>`\*                           | 用于对元素进行组合                                            |
| `<figcaption>`\*                       | 为 figure 提供图片说明                                        |

### 2.6 列表标签

| 标签   | 描述             |
| :----- | :--------------- |
| `<li>` | 定义一个列表项   |
| `<ul>` | 定义一个无序列表 |
| `<ol>` | 定义一个有序列表 |

### 2.7 表格标签

| 标签           | 描述                           |
| :------------- | :----------------------------- |
| `<table>`      | 定义一个表格                   |
| `<th>`         | 定义表格中的表头单元格         |
| `<tr>`         | 定义表格中的行                 |
| `<td>`         | 定义表格中的单元               |
| `<caption>`\*  | 定义表格标题                   |
| `<thead>`\*    | 定义表格中的表头内容           |
| `<tbody>`\*    | 定义表格中的主体内容           |
| `<tfoot>`\*    | 定义表格中的表注内容（脚注）   |
| `<col>`\*      | 定义表格中一个或多个列的属性值 |
| `<colgroup>`\* | 定义表格中供格式化的列组       |

### 2.8 链接标签

| 标签                                | 描述                     |
| :---------------------------------- | :----------------------- |
| `<a>`                               | 定义一个链接             |
| `<link>`                            | 定义文档与外部资源的关系 |
| `<nav>`<span class="new">New</span> | 定义导航链接             |

### 2.9 表单标签

| 标签                                       | 描述                                             |
| :----------------------------------------- | :----------------------------------------------- |
| `<form>`                                   | 定义一个 HTML 表单，用于用户输入                 |
| `<input>`                                  | 定义一个输入控件                                 |
| `<textarea>`                               | 定义多行的文本输入控件                           |
| `<button>`                                 | 定义按钮                                         |
| `<select>`                                 | 定义选择列表（下拉列表）                         |
| `<option>`                                 | 定义选择列表中的选项                             |
| `<label>`                                  | 定义 input 元素的标注                            |
| `<fieldset>`\*                             | 定义围绕表单中元素的边框                         |
| `<legend>`\*                               | 定义 fieldset 元素的标题                         |
| `<datalist>`\*<span class="new">New</span> | 规定了 input 元素可能的选项列表【Safari 不支持】 |
| `<keygen>`\*<span class="new">New</span>   | 规定用于表单的密钥对生成器字段【IE 不支持】      |
| `<output>`\*<span class="new">New</span>   | 定义一个计算的结果【IE 不支持】                  |

### 2.10 媒体标签

| 标签                                   | 描述                                            |
| :------------------------------------- | :---------------------------------------------- |
| `<audio>`<span class="new">New</span>  | 定义声音，比如音乐或其他音频流                  |
| `<video>`<span class="new">New</span>  | 定义一个音频或者视频                            |
| `<source>`<span class="new">New</span> | 定义媒体元素 (`<video>` 和 `<audio>`)的媒体资源 |

### 2.11 框架标签

| 标签         | 描述         |
| :----------- | :----------- |
| `<iframe>`\* | 定义内联框架 |

### 2.12 程序标签

| 标签                                    | 描述                                                 |
| :-------------------------------------- | :--------------------------------------------------- |
| `<script>`                              | 定义客户端脚本                                       |
| `<noscript>`\*                          | 定义针对不支持客户端脚本的用户的替代内容             |
| `<embed>`\*<span class="new">New</span> | 定义了一个容器，用来嵌入外部应用或者互动程序（插件） |
| `<object>`\*                            | 定义嵌入的对象                                       |
| `<param>`\*                             | 定义对象的参数                                       |

## 3. 元素属性

### 3.1 概述

`<p>这里是内容</p>` 表示小狗，那么这只小狗名字叫什么？它的毛色是什么样的？它是什么品种？这些都是这只小狗的属性，通过这些属性我们能了解这只小狗的相关信息。比如,我们这样写：
```
<狗 名字=小明，毛色=白色，品种=泰迪 是否纯种=是> LLLL </狗>
```
通过上面的表达，我们很容易看得出，这只小狗名字叫小明，是一只白色的纯种泰迪狗。

同样，HTML 元素也拥有属性。属性提供了有关 HTML 元素的更多的信息。

属性总是以名称/值对的形式出现，比如：name="value"。

属性总是在 HTML 元素的开始标签中规定。

### 3.2 全局属性

每个动物都都属于一个科，比如小狗是犬科，天鹅是鸭科，癞蛤蟆是蛙科动物。“科”这个属性就是每个动物共有的。

同样，虽然每个 HTML 元素属性不一样，但也有一些共有的属性，这些共有属性就是全局属性。

下面是 HTML 元素的共有属性。部分常用的标签元素，带星 * 标签表示使用不广泛使用或部分浏览器不兼容，了解即可。

<span class="new">New</span> - HTML5 新增属性

| 属性                                        | 描述                                     |
| :------------------------------------------ | :--------------------------------------- |
| id                                          | 规定元素的唯一                           |
| class                                       | 规定元素的类名（classname）              |
| style                                       | 规定元素的行内样式（inline style）       |
| data-\*<span class="new">New</span>         | 用于存储页面的自定义数据                 |
| hidden<span class="new">New</span>          | 属性规定对元素进行隐藏                   |
| draggable<span class="new">New</span>       | 指定某个元素是否可以拖动                 |
| contenteditable<span class="new">New</span> | 规定是否可编辑元素的内容                 |
| tabindex                                    | 设置元素的 Tab 键控制次序                |
| accesskey                                   | 设置访问元素的键盘快捷键                 |
| title                                       | 规定元素的额外信息（可在工具提示中显示） |
| spellcheck<span class="new">New</span>      | 检测元素是否拼写错误                     |
| dir                                         | 设置元素中内容的文本方向                 |
| lang                                        | 设置元素中内容的语言代码                 |

### 3.3 源码示例
*源码*
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>常用标签示例</title>
	</head>
	<body>
		<div>
			<h1>格式标签</h1>
			<table>
				<tr>
					<th>标签</th>
					<th>说明</th>
					<th>示例</th>
				</tr>
				<tr>
					<td>&lt;b&gt;</td>
					<td>定义粗体文本</td>
					<td><b>DOBE工场</b></td>
				</tr>
				<tr>
					<td>&lt;i&gt;</td>
					<td>定义斜体文本</td>
					<td><i>DOBE工场</i></td>
				</tr>
				<tr>
					<td>&lt;u&gt;</td>
					<td>定义下划线文本</td>
					<td><u>DOBE工场</u></td>
				</tr>
				<tr>
					<td>&lt;del&gt;</td>
					<td>定义被删除文本</td>
					<td><del>DOBE工场</del></td>
				</tr>
				<tr>
					<td>&lt;s&gt;</td>
					<td>标记不再正确的文本</td>
					<td><s>DOBE工场</s></td>
				</tr>
				<tr>
					<td>&lt;small&gt;</td>
					<td>定义小号文本</td>
					<td><small>DOBE工场</small></td>
				</tr>
				<tr>
					<td>&lt;strong&gt;</td>
					<td>定义语气更为强烈的强调文本</td>
					<td><strong>DOBE工场</strong></td>
				</tr>
				<tr>
					<td>&lt;mark&gt;</td>
					<td>定义带有记号的文本</td>
					<td><mark>DOBE工场</mark></td>
				</tr>
			</table>
		</div>
		<hr />
		<div>
			<h1>图像标签</h1>
			<a href="http://www.runoob.com/try/try.php?filename=tryhtml_areamap">参考菜鸟示例</a>
		</div>
		<div>
			<h1>form表单及控件</h1>
			<div>
				<p>网站怎样与用户进行交互？答案是使用HTML表单(form)。表单是可以把浏览者输入的数据传送到服务器端，这样服务器端程序就可以处理表单传过来的数据。</p>
				<p>所有表单控件（文本框、文本域、按钮、单选框、复选框等）都必须放在  form 标签之间（否则用户输入的信息可提交不到服务器上哦！）。</p>
				<p>method:post/get的区别这一部分内容属于后端程序员考虑的问题。</p>
				<p>label标签不会向用户呈现任何特殊效果，它的作用是为鼠标用户改进了可用性。如果你在 label 标签内点击文本，就会触发此控件。就是说，当用户单击选中该label标签时，浏览器就会自动将焦点转到和标签相关的表单控件上（就自动选中和该label标签相关连的表单控件上）。 </p>
			</div>
			<form method="post" action="save.php"  style="border: dashed;padding: 6px;">
				<label for="username">姓名:</label>
				<input type="text" name="username" />
				<br /><br />
				<label>性别：</label>
				<label for="male">男</label>
				<input type="radio" name="gender" id="male" />
				<label for="female">女</label>
				<input type="radio" name="gender" id="female" />
				<br /><br />
				<label for="email">输入你的邮箱地址</label>
				<input type="email" id="email" placeholder="Enter email">
				<br /><br />
				你对什么运动感兴趣：
				<label for="run">慢跑</label>
				<input type="checkbox" name="sports" id="run">
				<label for="climb">登山</label>
				<input type="checkbox" name="sports" id="climb">
				<label for="basketball">篮球</label>
				<input type="checkbox" name="sports" id="basketball">
				<br /><br />
				<label>个人简介：</label><br>  
				<textarea cols="40" rows="10">在这里输入内容...</textarea><br>
				<br /><br />
				<label>爱好:</label>  
				<select>  
					<option value="看书" selected="selected">看书</option>  
					<option value="旅游">旅游</option>  
					<option value="运动">运动</option>  
					<option value="购物">购物</option>  
				</select> 
				<br /><br />
				<input type="submit" value="确定"  />  
				<input type="reset" value="重置"  />
			</form>
		</div>
	</body>
</html>
```
<div class="preview-code">
    <div>
        <h1>格式标签</h1>
        <table>
            <tr>
                <th>标签</th>
                <th>说明</th>
                <th>示例</th>
            </tr>
            <tr>
                <td>&lt;b&gt;</td>
                <td>定义粗体文本</td>
                <td><b>DOBE工场</b></td>
            </tr>
            <tr>
                <td>&lt;i&gt;</td>
                <td>定义斜体文本</td>
                <td><i>DOBE工场</i></td>
            </tr>
            <tr>
                <td>&lt;u&gt;</td>
                <td>定义下划线文本</td>
                <td><u>DOBE工场</u></td>
            </tr>
            <tr>
                <td>&lt;del&gt;</td>
                <td>定义被删除文本</td>
                <td><del>DOBE工场</del></td>
            </tr>
            <tr>
                <td>&lt;s&gt;</td>
                <td>标记不再正确的文本</td>
                <td><s>DOBE工场</s></td>
            </tr>
            <tr>
                <td>&lt;small&gt;</td>
                <td>定义小号文本</td>
                <td><small>DOBE工场</small></td>
            </tr>
            <tr>
                <td>&lt;strong&gt;</td>
                <td>定义语气更为强烈的强调文本</td>
                <td><strong>DOBE工场</strong></td>
            </tr>
            <tr>
                <td>&lt;mark&gt;</td>
                <td>定义带有记号的文本</td>
                <td><mark>DOBE工场</mark></td>
            </tr>
        </table>
    </div>
    <hr />
	<div>
		<h1>图像标签</h1>
		<a href="http://www.runoob.com/try/try.php?filename=tryhtml_areamap">参考菜鸟示例</a>
	</div>
    <div>
        <h1>form表单及控件</h1>
        <div>
            <p>网站怎样与用户进行交互？答案是使用HTML表单(form)。表单是可以把浏览者输入的数据传送到服务器端，这样服务器端程序就可以处理表单传过来的数据。</p>
            <p>所有表单控件（文本框、文本域、按钮、单选框、复选框等）都必须放在  form 标签之间（否则用户输入的信息可提交不到服务器上哦！）。</p>
            <p>method:post/get的区别这一部分内容属于后端程序员考虑的问题。</p>
            <p>label标签不会向用户呈现任何特殊效果，它的作用是为鼠标用户改进了可用性。如果你在 label 标签内点击文本，就会触发此控件。就是说，当用户单击选中该label标签时，浏览器就会自动将焦点转到和标签相关的表单控件上（就自动选中和该label标签相关连的表单控件上）。 </p>
        </div>
        <form method="post" action="save.php"  style="border: dashed;padding: 6px;">
            <label for="username">姓名:</label>
            <input type="text" name="username" />
            <br /><br />
            <label>性别：</label>
            <label for="male">男</label>
            <input type="radio" name="gender" id="male" />
            <label for="female">女</label>
            <input type="radio" name="gender" id="female" />
            <br /><br />
            <label for="email">输入你的邮箱地址</label>
            <input type="email" id="email" placeholder="Enter email">
            <br /><br />
            你对什么运动感兴趣：
            <label for="run">慢跑</label>
            <input type="checkbox" name="sports" id="run">
            <label for="climb">登山</label>
            <input type="checkbox" name="sports" id="climb">
            <label for="basketball">篮球</label>
            <input type="checkbox" name="sports" id="basketball">
            <br /><br />
            <label>个人简介：</label><br>  
            <textarea cols="40" rows="10">在这里输入内容...</textarea><br>
            <br /><br />
            <label>爱好:</label>  
            <select>  
                <option value="看书" selected="selected">看书</option>  
                <option value="旅游">旅游</option>  
                <option value="运动">运动</option>  
                <option value="购物">购物</option>  
            </select> 
            <br /><br />
            <input type="submit" value="确定"  />  
            <input type="reset" value="重置"  />
        </form>
    </div>
</div>