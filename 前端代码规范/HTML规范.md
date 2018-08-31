#  HTML 规范

**超文本标记语言(HTML)**

>超文本标记语言，通常被称为 HTML，被用作创建网页的标准标记语言。网络浏览器可以读取 HTML 文件并且把它们渲染成可见或可听的网页。HTML 在语义上描述了一个网站的结构，并且隐含了其表现形式，因此是一种标记语言，而非程序语言。


**实用高于完美**

尽量遵循HTML标准和语义，但是不应该以浪费实用性作为代价；

任何时候都要用尽量小的复杂度和尽量少的标签来解决问题。

## 语法

* 缩进使用soft tab（2个空格）；
* 嵌套的节点应该缩进；
* 在属性上，使用双引号，不要使用单引号；
* 属性名全小写，用中划线做分隔符；
* 不要在自动闭合标签结尾处使用斜线（HTML5 规范 指出他们是可选的）；
* 不要忽略可选的关闭标签，例：</li>和</body>。

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Page title</title>
    </head>
    <body>
        <img src="images/company_logo.png" alt="Company">

        <h1 class="hello-world">Hello, world!</h1>
    </body>
</html>
```

## HTML5 doctype

在页面开头使用这个简单地 doctype 来启用标准模式，使其在每个浏览器中尽可能一致的展现；
虽然 doctype 不区分大小写，但是按照惯例，doctype 大写。

```html
<!DOCTYPE html>
<html>
    ...
</html>
``` 

## lang属性

根据HTML5规范：

> 应在html标签上加上lang属性。这会给语音工具和翻译工具帮助，告诉它们应当怎么去发音和翻译。

```html
<!DOCTYPE html>
<html lang="zh-cmn-Hans">
    ...
</html>
```

## 字符编码

通过声明一个明确的字符编码，让浏览器轻松、快速的确定适合网页内容的渲染方式，通常指定为'UTF-8'。

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
    </head>
    ...
</html>
```

## IE 兼容模式

IE 支持通过特定的 `<meta>` 标签来确定绘制当前页面所应该采用的 IE 版本。除非有强烈的特殊需求，否则最好是设置为 edge mode，从而通知 IE 采用其所支持的最新的模式。

```html
<!DOCTYPE html>
<html>
    <head>
        <meta http-equiv="X-UA-Compatible" content="IE=Edge">
    </head>
    ...
</html>
```

## 引入CSS, JS

根据HTML5规范, 通常在引入CSS和JS时不需要指明type，因为text/css和text/javascript分别是他们的默认值。

```html
<!-- External CSS -->
<link rel="stylesheet" href="code_guide.css">

<!-- In-document CSS -->
<style>
    ...
</style>

<!-- External JS -->
<script src="code_guide.js"></script>

<!-- In-document JS -->
<script>
    ...
</script>
```

## 属性顺序

属性应该按照特定的顺序出现以保证易读性；

* `class`
* `id`
* `name`
* `data-*`
* `src`、`for`、`type`、`href`、`value`、`max-length`、`max`、`min`、`pattern`
* `placeholder`、`title`、`alt`
* `aria-*`、`role`
* `required`、`readonly`、`disabled`

class是为高可复用组件设计的，所以应处在第一位；

id更加具体且应该尽量少使用，所以将它放在第二位。

```html
<a class="..." id="..." data-modal="toggle" href="#">Example link</a>

<input class="form-control" type="text">

<img src="..." alt="...">
```

## boolean 属性

 boolean 属性指不需要声明取值的属性， XHTML 需要每个属性声明取值，但是 HTML5 并不需要；

 > boolean属性的存在表示取值为true，不存在则表示取值为false。

```html
<input type="text" disabled>

<input type="checkbox" value="1" checked>

<select>
    <option value="1" selected>1</option>
</select>
```

## alt 与 title 属性

为了保证代码的平稳退化和页面语义化，alt 与 title 属性一定要赋予相应的值。

```html
  <img src="../" title="title" alt="test">
```

## 减少标签数量

在编写HTML代码时，需要尽量避免多余的父节点；很多时候，需要通过迭代和重构来使 HTML 变得更少。

```html
<!-- Not well -->
<span class="avatar">
    <img src="...">
</span>

<!-- Better -->
<img class="avatar" src="...">
```