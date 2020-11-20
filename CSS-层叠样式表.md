# CSS-层叠样式表

* CSS 指层叠样式表 (**C**ascading **S**tyle **S**heets)
* 样式定义**如何显示** HTML 元素
* 样式通常存储在**样式表**中
* 把样式添加到 HTML 4.0 中，是为了**解决内容与表现分离的问题**
* **外部样式表**可以极大提高工作效率
* 外部样式表通常存储在 **CSS 文件**中
* 多个样式定义可**层叠**为一个

## 语法规则

CSS 规则由两个主要的部分构成：选择器，以及一条或多条声明

选择器通常是您需要改变样式的 HTML 元素。

每条声明由一个属性和一个值组成。

属性（property）是您希望设置的样式属性（style attribute）。每个属性有一个值。属性和值被冒号分开。

``` HTML
p {
color:red;
text-align:center;/*居中*/
}
/*这是个注释*/
```

## Id和Class选择器

### Id选择器

id 选择器可以为标有特定 id 的 HTML 元素指定特定的样式。

HTML元素以id属性来设置id选择器, CSS 中 id 选择器以 "#" 来定义。

``` HTML
<style>
    #para1 {
        text-align: center;
        color: red;
    }
</style>
<p id="para1">Hello World!</p>
<p>这个段落不受该样式的影响。</p>
```

### Class选择器

class 选择器用于描述一组元素的样式，class 选择器有别于id选择器，class可以在多个元素中使用。class 选择器在HTML中以class属性表示, 在 CSS 中，类选择器以一个点"."号显示

``` HTML
<style>
    .center {
        text-align: center;
    }
</style>
<h1 class="center">标题居中</h1>
```

你也可以指定特定的HTML元素使用class。

在以下实例中, 所有的 p 元素使用 class="center" 让该元素的文本居中:

 `p.center {text-align:center;}`

## CSS创建样式表

* 外部样式表(External style sheet)
* 内部样式表(Internal style sheet)
* 内联样式(Inline style)

### 外部样式表

当样式需要应用于很多页面时，外部样式表将是理想的选择。在使用外部样式表的情况下，你可以通过改变一个文件来改变整个站点的外观。每个页面使用 `<link>` 标签链接到样式表。 `<link>` 标签在（文档的）头部：

``` HTML
<head>
    <link rel="stylesheet" type="text/css" href="mystyle.css">
</head>
```

浏览器会从文件 mystyle.css 中读到样式声明，并根据它来格式文档。

外部样式表可以在任何文本编辑器中进行编辑。文件不能包含任何的 html 标签。样式表应该以 .css 扩展名进行保存。下面是一个样式表文件的例子：

``` HTML
hr {color:sienna;}
p {margin-left:20px;}
body {background-image:url("/images/back40.gif");}
/*不要在属性值与单位之间留有空格*/
```

### 内部样式表

单个文档需要特殊的样式，使用 `<style>` 标签在文档头部定义内部样式表

``` HTML
<head>
    1<style>
        hr {
            color: sienna;
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

### 内联样式

由于要将表现和内容混杂在一起，内联样式会损失掉样式表的许多优势，当样式仅需要在一个元素上应用一次时。要使用内联样式，你需要在相关的标签内使用样式（style）属性。Style 属性可以包含任何 CSS 属性。

 `<p style="color:sienna;margin-left:20px">这是一个段落。</p>`

* 内联样式相当于是一个局部修饰变量
* 内部样式表相当于是一个全部变量

### 多重样式及其优先级

* 就近原则：离代码块越近，优先级别越高

  **内联样式）Inline style > （内部样式）Internal style sheet >（外部样式）External style sheet > 浏览器默认样式**

  **注意：** *如果外部样式放在内部样式的后面，则外部样式将覆盖内部样式。

  [和优先级相关的知识](https://www.runoob.com/w3cnote/css-style-priority.html)

* 多重样式的继承和覆盖

  相同的属性按照优先级别进行覆盖

  不同的属性直接继承到和属性

## background

* background-color
* background-image
* background-repeat
* background-attachment
* background-position

### 简写属性

为了简化这些属性的代码，我们可以将这些属性合并在同一个属性中.

背景颜色的简写属性为 "background":

 `body {background:#ffffff url('img_tree.png') no-repeat right top;}`

## 文本

![image-20200722180911088](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20200722180911088.png)

## 字体

### 字形
