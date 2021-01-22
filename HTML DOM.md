# HTML DOM

## 简介

HTML DOM 定义了访问和操作 HTML 文档的标准方法。

DOM 是 Document Object Model（文档对象模型）的缩写。

*HTML DOM 是关于如何获取、修改、添加或删除 HTML 元素的标准。*

## HTML DOM 节点

**在 HTML DOM 中，所有事物都是节点。DOM 是被视为节点树的 HTML。**

**HTML DOM Tree **

![HTML DOM Node Tree](https://www.w3school.com.cn/i/ct_htmltree.gif)

通过 HTML DOM，树中的所有节点均可通过 JavaScript 进行访问。所有 HTML 元素（节点）均可被修改，也可以创建或删除节点。

## 节点父、子和同胞

节点树中的节点彼此拥有层级关系。

父（parent）、子（child）和同胞（sibling）等术语用于描述这些关系。父节点拥有子节点。同级的子节点被称为同胞（兄弟或姐妹）。

- 在节点树中，顶端节点被称为根（root）
- 每个节点都有父节点、除了根（它没有父节点）
- 一个节点可拥有任意数量的子
- 同胞是拥有相同父节点的节点

下面的图片展示了节点树的一部分，以及节点之间的关系：

![DOM 节点关系](https://www.w3school.com.cn/i/dom_navigate.gif)

```html
<html>
  <head>
    <title>DOM 教程</title>
  </head>
  <body>
    <h1>DOM 第一课</h1>
    <p>Hello world!</p>
  </body>
</html>
```

从上面的 HTML 中：

- <html> 节点没有父节点；它是根节点
- <head> 和 <body> 的父节点是 <html> 节点
- 文本节点 "Hello world!" 的父节点是 <p> 节点

并且：

- <html> 节点拥有两个子节点：<head> 和 <body>
- <head> 节点拥有一个子节点：<title> 节点
- <title> 节点也拥有一个子节点：文本节点 "DOM 教程"
- <h1> 和 <p> 节点是同胞节点，同时也是 <body> 的子节点

并且：

- <head> 元素是 <html> 元素的首个子节点

- <body> 元素是 <html> 元素的最后一个子节点

- <h1> 元素是 <body> 元素的首个子节点

- <p> 元素是 <body> 元素的最后一个子节点

## HTML DOM 方法

方法是我们可以在节点（HTML元素）上执行的动作。

**编程接口**

可通过javascript 对HTML DOM 进行访问。

所以HTML 元素被定义为对象，而编程接口则是对象方法和对象属性。

方法是能够执行的动作（比如添加和修改元素）。

属性是能够获取或设置的值（比如节点的名称或内容）

* getElementById ( ) 方法

```javascript
var element = document.getElementById("intro");
```

HTML DOM  对象  - - - - - - - - 方法和属性

* getElementById(id) - 获取带有指定id 的节点（元素）
* appendChild(node) - 插入新的子节点（元素）
* removeChild（node）-  删除子节点（元素）

一些常用的 HTML DOM 属性：

- innerHTML - 节点（元素）的文本值
- parentNode - 节点（元素）的父节点
- childNodes - 节点（元素）的子节点
- attributes - 节点（元素）的属性节点

## HTML DOM 属性

**innerHTML属性**

​	获取元素内容的最简单方法是使用 innerHTML 属性。

​	innerHTML 属性对于获取或替换 HTML 元素的内容很有用

**nodeName属性**

​	nodeName属性规定节点的名称。

		* nodeName 是只读的
		* 元素节点的 nodeName 与标签名相同
* 属性节点的 nodeName 与属性名相同
* 文本节点的 nodeName 始终是 #text
* 文档节点的 nodeName 始终是 #document

**nodeValue属性**

​	nodeValue 属性规定节点的值。

- 元素节点的 nodeValue 是 undefined 或 null
- 文本节点的 nodeValue 是文本本身
- 属性节点的 nodeValue 是属性值

**获取元素的值**

```html
<html>
    <body>

        <p id="intro">Hello World!</p>

        <script type="text/javascript">
        x=document.getElementById("intro");
        document.write(x.firstChild.nodeValue);
        </script>

    </body>
</html>
```



**nodeType 属性**

## HTML DOM 访问

**访问HTML DOM - 查找HTML元素**

访问HTML元素（节点）

访问HTML元素等同于访问节点

访问HTML方式

* getElementById()

* getElementsByTagName()

* getElementsByClassName()

  **注释：**getElementsByClassName() 在 Internet Explorer 5,6,7,8 中无效

  

## HTML DOM - 修改

**修改HTML  =   改变元素、属性、样式和事件**

修改HTML元素

* 改变HTML内容
* 改变CSS样式
* 改变HTML属性
* 创建新的HTML元素
* 删除已有的HTML元素
* 改变事件（处理程序）

**创建HTML内容**

```javascript
document.getElementById("p1").innerHTML="New text!";
```

**改变HTML样式**

```javascript
document.getElementById("p2").style.color = "blue";
```

**创建新的HTML内容**

* appendChild（）

```javascript
var para=document.createElement("p");
var node=document.createTextNode("This is new.");
para.appendChild(node);

var element=document.getElementById("d1");
element.appendChild(para);
```

* insertBefore()

```javascript
var para=document.createElement("p");
var node=document.createTextNode("This is new.");
para.appendChild(node);

var element=document.getElementById("div1");
var child=document.getElementById("p1");
element.insertBefore(para,child);
```

**删除已有的HTML元素**

如需删除HTML元素，需清楚该元素的父元素：

```html
<div id="div1">
    <p id="p1">This is a paragraph.</p>
    <p id="p2">This is another paragraph.</p>
</div>
<script>
    var parent=document.getElementById("div1");
    var child=document.getElementById("p1");
    parent.removeChild(child);
</script>
```

**替换HTML元素**



## HTML DOM - 修改内容

**通过HTML DOM 、javascript 能够访问HTML文档的每个元素**

**使用事件**

HTML DOM 允许在事件发生时执行代码。

当HTML元素 “有事情发生” 时，浏览器就会生成事件：

* 在元素上点击
* 加载页面
* 改变输入字段

```html
<html>
	<body>

<script>
function ChangeBackground(){
	document.body.style.backgroundColor="lavender";
}
</script>

<input type="button" onclick="ChangeBackground()"
value="Change background color" />

	</body>
</html>
```



## HTML DOM 事件

HTML DOM 允许 Javas 对 HTML 事件作出反应。

**对事件做出反应**

```javascript
onclick = javascript
```

HTML 事件的例子：

- 当用户点击鼠标时
- 当网页已加载时
- 当图片已加载时
- 当鼠标移动到元素上时
- 当输入字段被改变时
- 当 HTML 表单被提交时
- 当用户触发按键时

**HTML 事件属性**



**HTML DOM - 导航**

通过 HTML DOM，您能够使用节点关系在节点树中导航。

**HTML DOM 节点列表**

getElementsByTagName（）方法返回节点列表。节点列表是一个节点数组。

```javascript
var x = document.getElementsByTagName("p");
var y = x[0];
var y = x[1];
```

**HTML DOM 节点列表长度**

length 属性定义节点列表中节点的数量。

```javascript
x=document.getElementsByTagName("p");
for (i=0;i<x.length;i++)
{
    document.write(x[i].innerHTML);
    document.write("<br />");
}
```

**导航节点关系**

有三个节点属性可供使用，parentNode、firstNode 以及lastNode。

```html
<html>
<body>

<p>Hello World!</p>
<div>
  <p>DOM 很有用!</p>
  <p>本例演示节点关系。</p>
</div>

</body>
</html>
```

- 首个 <p> 元素是 <body> 元素的首个子元素（firstChild）
- <div> 元素是 <body> 元素的最后一个子元素（lastChild）
- <body> 元素是首个 <p> 元素和 <div> 元素的父节点（parentNode）

**DOM 根节点**

* document.documentElement - 全部文档
* document.body - 文档的主题

```html
<html>
<body>

<p>Hello World!</p>
<div>
<p>DOM 很有用!</p>
<p>本例演示 <b>document.body</b> 属性。</p>
</div>

<script>
alert(document.body.innerHTML);
</script>

</body>
</html>
```

