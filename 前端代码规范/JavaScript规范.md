#  JavaScript 规范

>JavaScript 是一个高级的、动态的、弱类型的解释性编程语言，被包含在 ECMAScript 的语言规范中。同 HTML 和 CSS 一样，它是万维网内容生产环节必不可少的三种技术之一，被大多数网站所使用，并且在不需要使用插件的情况下被所有现代的浏览器所支持。Javascript 基于原型并且把函数视为头等公民，因此是一种多范式的编程语言，支持面向对象，命令式以及函数式编程风格。它有一个可被用来操作文字，数组，日期以及正则表达式的 API，然而并不包含任何 I/O，因此像建网，存储或者图形工具之类的功能就需要依赖它所在的开发环境。

## 变量命名

标准变量采用驼峰式命名（除了对象的属性外，主要是考虑到cgi返回的数据）

* 'ID'在变量名中全大写
* 'URL'在变量名中全大写
* 'Android'在变量名中大写第一个字母
* 'iOS'在变量名中小写第一个，大写后两个字母
* 常量全大写，用下划线连接
* 构造函数，大写第一个字母

```js
var thisIsMyName;

var goodID;

var reportURL;

var AndroidVersion;

var iOSVersion;

var MAX_COUNT = 10;

function Person(name) {
    this.name = name;
}
```

## 变量声明

一个函数作用域中所有的变量声明尽量提到函数首部，用一个var声明，不允许出现两个连续的var声明，声明时如果没有值，则给该变量为对应类型的初始值

```js
function doSomethingWithItems(items) {
  // use one var
  var value = 0,
    myStr = "",
    myObj = null,
    myArr = [];
        
}
```

## 常量使用

代码中出现的地址、时间等字符串时等需要使用常量代替

```js
const HOME_PAGE_PATH = "/path/home";

location.href = HOME_PAGE_PATH;
```

## 数组、对象

对象属性名不需要加引号；

对象以缩进的形式书写，不要写在一行；

数组、对象最后不要有逗号。

```js
// not good
var a = {
  'b': 1
};

var a = {b: 1};

var a = {
  b: 1,
  c: 2,
};

// good
var a = {
  b: 1,
  c: 2
};
```

## null

适用场景：

  * 初始化一个将来可能被赋值为对象的变量
  * 与已经初始化的变量做比较
  * 作为一个参数为对象的函数的调用传参
  * 作为一个返回对象的函数的返回值
  
不适用场景：

  * 不要用null来判断函数调用时有无传参
  * 不要与未初始化的变量做比较

## undefined

永远不要直接使用undefined进行变量判断；

使用typeof和字符串'undefined'对变量进行判断。

```js
// not good
if (person === undefined) {
  ...
}

// good
if (typeof person === 'undefined') {
  ...
}
```

## 缩进

使用2个空格

```js
var x = 1,
  y = 1;

if (x < y) {
  x += 10;
} else {
  x += 1;
}
```

## 单行注释

双斜线后，必须跟一个空格；

缩进与下一行代码保持一致；

可位于一个代码行的末尾，与代码间隔一个空格。

```js
if (condition) {
  // if you made it here, then all security checks passed
  allowed();
}

var zhangsan = 'zhangsan'; // one space after code
```

## 多行注释

最少三行, '*'后跟一个空格，具体参照右边的写法；

建议在以下情况下使用：

  * 难于理解的代码段
  * 可能存在错误的代码段
  * 浏览器特殊的HACK代码
  * 业务逻辑强相关的代码

```js
/*
 * one space after '*'
 */
var x = 1;
```

## 引号

最外层统一使用双引号。

```js
// not good
var x = 'test';

// good
var y = "foo",
  z = "<div id="test"></div>";

```

## 逻辑分离

数据处理尽量与数据请求尽量分离，数据处理的逻辑应该封装为另一个函数来使用。

```js
// 数据请求
this.$axios
  .post(urls.MES_GET_CITY_LIST_URL,postData)
  .then(function(response) {
      var data = response.data;
         
      // 数据处理
      formatData(data);
  });

function formatData(data){
  // do something
}
```


## jshint

* 用'===', '!=='代替'==', '!='；
* for-in里一定要有hasOwnProperty的判断；
* 不要在内置对象的原型上添加方法，如Array, Date；
* 变量不要先使用后声明；
* 不要使用未声明的变量（全局变量需要加到.jshintrc文件的globals属性里面）；
* 数组中不要存在空元素；
* 对上下文this的引用只能使用'_this', 'that', 'self'其中一个来命名；