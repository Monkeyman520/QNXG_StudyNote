# HTML

## 基础标签

* 标题

  * 通过`<h1> - <h6>` 标签来定义

    `<h1>Heading_name</h1>`

* 段落 

  * 通过`<p>`标签定义

    `<p>Paragraph_name</p>`

* 链接

  * 通过标签 <a> 来定义

    `<a href="https://www.runoob.com">这是一个链接</a>`

    在 `href` 属性中指定链接的地址。

* 图像

  * 通过标签 `<img> `来定义

    `<img src="/images/logo.png" width="258" height="39" />`

    图像的名称和尺寸是以属性的形式提供的。

## 元素

* HTML 文档由 HTML 元素定义。

### 元素语法

- HTML 元素以**开始标签**起始
- HTML 元素以**结束标签**终止
- **元素的内容**是开始标签与结束标签之间的内容
- 某些 HTML 元素具有**空内容（empty content）**
- 空元素**在开始标签中进行关闭**（以开始标签的结束而结束）
- 大多数 HTML 元素可拥有**属性**
- 使用小写标签

### 元素嵌套

* 大多数 HTML 元素可以嵌套（HTML 元素可以包含其他 HTML 元素）。

  HTML 文档由相互嵌套的 HTML 元素构成。

### 元素内容

* `<p> `元素
  * 定义了 HTML 文档中的一个段落
* `<body>`元素
  * 定义了 HTML 文档的主体。
* `<html>`元素
  * 定义了整个 HTML 文档。

* 空元素
  * 没有内容的 HTML 元素被称为空元素。空元素是在开始标签中关闭的。`<br>` 就是没有关闭标签的空元素（`<br>` 标签定义换行）。
  * 在开始标签中添加斜杠，比如 `<br />`，是关闭空元素的正确方法

## 属性

* 属性是 HTML 元素提供的附加信息。

- HTML 元素可以设置**属性**
- 属性可以在元素中添加**附加信息**
- 属性一般描述于**开始标签**
- 属性总是以名称/值对的形式出现，**比如：name="value"**。
- 属性值应该始终被包括在引号内，若属性值本身就含有双引号，那么必须使用单引号。
-  [HTML 标签参考手册](https://www.runoob.com/tags/html-reference.html)
  - `<a herf="https://www.runoob.com/tags/html-reference.html">这是html的属性手册</a>`

## 标题

### 标题（Heading）

通过 <h1> - <h6> 标签进行定义的。

`<h1> 定义最大的标题。 <h6> 定义最小的标题。`

* 浏览器会自动地在标题的前后添加空行。

### 水平线

* `<hr>` 标签在 HTML 页面中创建水平线。

  hr 元素可用于分隔内容。

### 注释

`<!-- 这是一个注释 -->`

**注释:** 开始括号之后（左边的括号）需要紧跟一个叹号，结束括号之前（右边的括号）不需要。

### 段落

段落是通过 <p> 标签定义的。

**注意：**浏览器会自动地在段落的前后添加空行。（`</p>` 是块级元素）

### 折行

在不产生一个新段落的情况下进行换行（新行），使用 `<br> `标签

`<p>这个<br>段落<br>演示了分行的效果</p>`

## 文本格式化

### HTML格式化标签

* HTML 使用标签 <b>("bold") 与 <i>("italic") 对输出的文本进行格式, 如：**粗体** or *斜体*
* **通常标签` <strong>` 替换加粗标签` <b> `来使用,` <em>` 替换 `<i>`标签使用**
* `<strong>` 或者` <em>`意味着你要呈现的文本是重要的，所以要突出显示
* <a herf="https://www.runoob.com/html/html-formatting.html">格式化标签</a>

## 链接

HTML使用标签` <a>`来设置超文本链接。

超链接可以是一个字，一个词，或者一组词，也可以是一幅图像，您可以点击这些内容来跳转到新的文档或者当前文档中的某个部分。

当把鼠标指针移动到网页中的某个链接上时，箭头会变为一只小手。

在标签`<a> `中使用了`href`属性来描述链接的地址。

默认情况下，链接将以以下形式出现在浏览器中：

- 一个未访问过的链接显示为蓝色字体并带有下划线。
- 访问过的链接显示为紫色并带有下划线。
- 点击链接时，链接显示为红色并带有下划线。

> 注意：如果为这些超链接设置了` CSS `样式，展示样式会根据` CSS` 的设定而显示。

* `<a href="url">链接文本</a>`    `href` 属性描述了链接的目标。

### target属性

* 使用 target 属性，你可以定义被链接的文档在何处显示
  * `<a href="https://www.runoob.com/" target="_blank" rel="noopener noreferrer">访问菜鸟教程!</a>`   <!---打开新的标签页--->

### id属性

d属性可用于创建在一个HTML文档书签标记。

**提示:** 书签是不以任何特殊的方式显示，在HTML文档中是不显示的，所以对于读者来说是隐藏的。

在HTML文档中插入ID:

`<a id="tips">有用的提示部分</a>`

在HTML文档中创建一个链接到"有用的提示部分(id="tips"）"：

`<a href="#tips">访问有用的提示部分</a>`

或者，从另一个页面创建一个链接到"有用的提示部分(id="tips"）"：

`<a href="https://www.runoob.com/html/html-links.html#tips">访问有用的提示部分</a>`

## HTML `<head>`

[`<title> `- 定义了HTML文档的标题](https://www.runoob.com/try/try.php?filename=tryhtml_title)
使用 <title> 标签定义HTML文档的标题

[`<base>` - 定义了所有链接的URL](https://www.runoob.com/try/try.php?filename=tryhtml_base)
使用 <base> 定义页面中所有链接默认的链接目标地址。

<meta> - 提供了HTML文档的meta标记使用 <meta> 元素来描述HTML文档的描述，关键词，作者，字符集等。

### `<head>`元素

`<head>` 元素包含了所有的头部标签元素。在 `<head>`元素中你可以插入脚本（scripts）, 样式文件`（CSS）`，及各种meta信息。

可以添加在头部区域的元素标签为: `<title>`,` <style>`,` <meta>`, `<link>`, `<script>`, `<noscript>` 和 `<base>`。

#### `<title>`

`<title>` 标签定义了不同文档的标题。

`<title> `在` HTML/XHTML` 文档中是必须的。

`<title> `元素:

- 定义了浏览器工具栏的标题
- 当网页添加到收藏夹时，显示在收藏夹中的标题
- 显示在搜索引擎结果页面的标题

#### `<base>`

<base> 标签描述了基本的链接地址/链接目标，该标签作为HTML文档中所有的链接标签的默认链接

<head>
<base href="http://www.runoob.com/images/" target="_blank">
</head>

#### `<link>`

<link> 标签定义了文档与外部资源之间的关系。

<link> 标签通常用于链接到样式表:

```html
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```

#### `<style>`

`<style> 标签定义了HTML文档的样式文件引用地址.`


在<style> 元素中你也可以直接添加样式来渲染 HTML 文档:

```html
<head>
<style type="text/css">
body {background-color:yellow}
p {color:blue}
</style>
</head>
```

#### `<meta>`

meta标签描述了一些基本的元数据。

`<meta> 标签提供了元数据.元数据也不显示在页面上，但会被浏览器解析。`

META 元素通常用于指定网页的描述，关键词，文件的最后修改时间，作者，和其他元数据。

元数据可以使用于浏览器（如何显示内容或重新加载页面），搜索引擎（关键词），或其他Web服务。

`<meta> 一般放置于 <head> 区域`

每30秒钟刷新当前页面:

```html
<meta http-equiv="refresh" content="30">
```

## 样式-`CSS`

`CSS` 是为了更好的渲染HTML元素而引入的.

`CSS `可以通过以下方式添加到HTML中:

- 内联样式- 在HTML元素中使用"style" **属性**
- 内部样式表 -在HTML文档头部 <head> 区域使用<style> **元素** 来包含`CSS`
- 外部引用 - 使用外部` CSS` **文件**

[CSS 教程](https://www.runoob.com/css/)

### 内联样式

当特殊的样式需要应用到个别元素时，就可以使用内联样式。 使用内联样式的方法是在相关的标签中使用样式属性。

```html
<p style="color:blue;margin-left:20px;">这是一个段落。</p>
```

#### 字体样式

使用font-family（字体），color（颜色），和font-size（字体大小）属性来定义字体的样式

#### 文本对齐方式

使用 text-align（文字对齐）属性指定文本的水平与垂直对齐方式

`<h1 style="text-align:center;">居中对齐的标题</h1> <p>这是一个段落。</p>`

文本对齐属性 text-align取代了旧标签` <center>`

#### 内部样式表

当单个文件需要特别样式时，就可以使用内部样式表。你可以在<head> 部分通过 <style>标签定义内部样式表：

```html
<head>
<style type="text/css">
body {background-color:yellow;}
p {color:blue;}
</style>
</head>
```

#### 外部样式表

当样式需要被应用到很多页面的时候，外部样式表将是理想的选择。使用外部样式表，可以通过更改一个文件来改变整个站点的外观。

```html
<head>
<link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```

## 图像

### 图像标签（` <img>`）和源属性（`Src`）

在 HTML 中，图像由<img> 标签定义。

<img> 是空标签，意思是说，它只包含属性，并且没有闭合标签。

要在页面上显示图像，你需要使用源属性（src）。src 指 "source"。源属性的值是图像的 URL 地址。

**定义图像的语法是：**

`<img src="url" alt="some_text">`

URL 指存储图像的位置。如果名为 `"pulpit.jpg"` 的图像位于 www.runoob.com 的 images 目录中，那么其 URL 为 [http://www.runoob.com/images/pulpit.jpg](https://www.runoob.com/images/pulpit.jpg)。

浏览器将图像显示在文档中图像标签出现的地方。如果你将图像标签置于两个段落之间，那么浏览器会首先显示第一个段落，然后显示图片，最后显示第二段。

### Alt属性

alt 属性用来为图像定义一串预备的可替换的文本。

替换文本属性的值是用户定义的。

`<img src="boat.gif" alt="Big Boat">`

### 设置图像的高度与宽度

height（高度） 与 width（宽度）属性用于设置图像的高度与宽度。

属性值默认单位为像素:

`<img src="pulpit.jpg" alt="Pulpit rock" width="304" height="228">`

**提示:** 指定图像的高度和宽度是一个很好的习惯。如果图像指定了高度宽度，页面加载时就会保留指定的尺寸。如果没有指定图片的大小，加载页面时有可能会破坏HTML页面的整体布局。

```
<map name="planetmap">
  <area shape="rect" coords="0,0,82,126" alt="Sun" href="sun.htm">
  <area shape="circle" coords="90,58,3" alt="Mercury" href="mercur.htm">
  <area shape="circle" coords="124,58,8" alt="Venus" href="venus.htm">
</map>
```

该段代码中的shape指的是点击区域的形状，`coords`指的应该是链接区域在图片中的坐标（像素为单位）

、矩形：(左上角顶点坐标为`(x1,y1)`，右下角顶点坐标为`(x2,y2)`

```
<area shape="rect" coords="x1,y1,x2,y2" href=url>
```

2、圆形：(圆心坐标为`(X1,y1)`，半径为r)

```
<area shape="circle" coords="x1,y1,r" href=url>
```

3、多边形：(各顶点坐标依次为`(x1,y1)`、`(x2,y2)`、`(x3,y3) `......)

```
<area shape="poly" coords="x1,y1,x2,y2 ......" href=url>
```

## 表格

表格由 `<table> `标签来定义。每个表格均有若干行（由` <tr>` 标签定义），每行被分割为若干单元格（由 `<td> `标签定义）。字母 `td` 指表格数据（table data），即数据单元格的内容。数据单元格可以包含文本、图片、列表、段落、表单、水平线、表格等等。

<table border="1">     <tr>         <td>row 1, cell 1</td>         <td>row 1, cell 2</td>     </tr>     <tr>         <td>row 2, cell 1</td>         <td>row 2, cell 2</td>     </tr> </table>

### 表格和边框属性

如果不定义边框属性，表格将不显示边框。

<table border="1">     <tr>         <td>Row 1, cell 1</td>         <td>Row 1, cell 2</td>     </tr> </table>

### 表头

表格的表头使用 <th> 标签进行定义。

<table border="1">     <tr>         <th>Header 1</th>         <th>Header 2</th>     </tr>     <tr>         <td>row 1, cell 1</td>         <td>row 1, cell 2</td>     </tr>     <tr>         <td>row 2, cell 1</td>         <td>row 2, cell 2</td>     </tr> </table>

* 更多参见 <a herf="https://www.runoob.com/html/html-tables.html">菜鸟教程——HTML表格</a>

## 列表

### 无序列表

无序列表是一个项目的列表，此列项目使用粗体圆点（典型的小黑圆圈）进行标记。

无序列表使用` <ul> `标签。

<ul>
<li>Coffee</li>
<li>Milk</li>
</ul>

### 有序列表

同样，有序列表也是一列项目，列表项目使用数字进行标记。 有序列表始于 `<ol>` 标签。每个列表项始于 `<li>` 标签。

列表项使用数字来标记。

<ol>
<li>Coffee</li>
<li>Milk</li>
</ol>

### 自定义列表

自定义列表不仅仅是一列项目，而是项目及其注释的组合。

自定义列表以` <dl>` 标签开始。每个自定义列表项以 `<dt> `开始。每个自定义列表项的定义以 `<dd>` 开始。

<dl>
<dt>Coffee</dt>
<dd>- black hot drink</dd>
<dt>Milk</dt>
<dd>- white cold drink</dd>
</dl>

* 更多内容参见<a herf="https://www.runoob.com/html/html-lists.html">菜鸟教程——列表</a>

## 区块

HTML 可以通过` <div> `和 `<span>`将元素组合起来。

大多数 HTML 元素被定义为**块级元素**或**内联元素**。

* **块级元素**在浏览器显示时，通常会以新行来开始（和结束）。例: <h1>, <p>, <ul>, <table>

* **内联元素**在显示时通常不会以新行开始。例: <b>, <td>, <a>, <img>

### `<div>`

HTML` <div>` 元素是**块级元素**，它可用于组合其他 HTML 元素的容器。

`<div>` 元素没有特定的含义。除此之外，由于它属于块级元素，浏览器会在其前后显示折行。

如果与` CSS` 一同使用，`<div>` 元素可用于对大的内容块设置样式属性。

`<div>` 元素的另一个常见的用途是文档布局。它取代了使用表格定义布局的老式方法。使用 `<table>` 元素进行文档布局不是表格的正确用法。`<table>` 元素的作用是显示表格化的数据。

### `<span>`

HTML` <span> `元素是内联元素，可用作文本的容器

`<span>` 元素也没有特定的含义。

当与` CSS `一同使用时，`<span> `元素可用于为部分文本设置样式属性。

## 布局

### `<div>`布局

div 元素是用于分组 HTML 元素的块级元素。

### `<table>`布局

使用 HTML` <table> `标签是创建布局的一种简单的方式。

大多数站点可以使用` <div>` 或者 `<table>` 元素来创建多列。`CSS `用于对元素进行定位，或者为页面创建背景以及色彩丰富的外观。

* 详情参见 <a herf="https://www.runoob.com/html/html-layouts.html">HTML布局</a>

## 表单和输入

HTML 表单用于收集不同类型的用户输入。

### 表单

表单是一个包含表单元素的区域。

表单元素是允许用户在表单中输入内容,比如：文本域(`textarea`)、下拉列表、单选框(radio-buttons)、复选框(`checkboxes`)等等。

表单使用表单标签` <form>` 来设置