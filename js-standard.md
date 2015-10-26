# Javascript编码规范

[1 命名](#user-content-1-命名)

[2 标签](#user-content-2-标签)

[3 属性](#user-content-3-属性)

[4 变量](#user-content-4-变量)

[5 命名](#user-content-5-方法)

[6 对象](#user-content-6-对象)

[7 属性](#user-content-7-属性)



## 1 命名

#### **id命名：** `id`  全小写，单词之前用 `-` 分隔开。

#### **class命名：** `class` 全小写，单词之前用  `-` 分隔开。

#### **方法命名：** 小驼峰式命名（构造函数为大驼峰式命名、私有方法以 `_` 开头的小驼峰式）。

#### **常量命名：** 全大小 ，单词之前用 `_` 分隔开。

#### **变量命名：** 小驼峰式命名。

注：jquery对象赋值给变量时，变量前面加 `$` ，html模板赋值给变量时，变量前面加 `tpl` 。



示例：

``` html
<!-- good --> 
<div id="ocean-erp"></div>
<div class="ocean-erp"></div>

<!-- bad -->
<div id="oceanerp"></div>
<div class="oceanerp"></div>
```

``` javascript
//good
var oceanErpCount = 20, //变量
   	OCEAN_ERP_COUNT = 20, //常量
	$body = $(document.body), //jquery对象
    tplBody = document.body.innerHTML; //html模板

var getAllPerson = function(){ //普通方法命名
  //...
};

var Person = function(){ //构造方法命名
  //...
}

var _init = function(){ //私有方法命名
  //..
}

//bad
var ocean_erp_count = 20, //变量
	OCEANERPCOUNT = 20, //常量
    body = $(document.body), //jquery对象
    bodyHtml = document.body.innerHTML; //html模板

var get_all_person = function(){//普通方法命名
  //...
}

var person = function(){ //构造方法命名
  //...
}

var init = function(){ //私有方法命名
  //...
}
```

#### [建议] `id` 、 `class` 命名，在描述清楚的前提下尽可能的短。

``` html
<!-- good -->
<div id="nav"></div>

<!-- bad -->
<div id="navigation"></div>
```



## 2 标签

#### 标签名使用小写字母。

示例：

``` html
<!-- good -->
<p>oceanwing</p>

<!-- bad -->
<P>oceanwing</P>
```

#### 对于无需自闭合的标签，需要自闭合

解释：

常见的无需自闭合标签有input、br、img等。

示例：

``` html
<!-- good -->
<input type="text" name="title" />

<!-- bad -->
<input type="text" name="title" />
```

#### [建议] 在 `CSS` 可以实现同等需求的情况下尽量不要使用表格布局。

解释：表格绘制需要多次，而其他的标签知需要一次。



## 3 属性

#### [强制] 属性名称必须使用小写字母。

示例：

``` html
<!-- good -->
<table cellspacing="0"></table>

<!-- bad -->
<table cellSpacing="0"></table>
```

#### [建议] 自定义属性建议以 `XXX-` 为前缀，推荐使用 `data-*` 。

解释：data-*的形式，所有主流浏览器都支持，而且可以通过jquery的data方法去获取。



## 4 变量

#### [强制] 变量使用前必须用 `var` 进行定义。

#### [建议] 变量的声明应该代码块或者函数的头部，运算符前后各留一个空格。

``` javascript
//good 
var i = 0,
    j = 0;

//bad
var i=0;
j = 0;
```

#### [建议] 变量声明时适当的加些前后缀表示变量的类型。

``` javascript
var $body = $(document.body); //jquery对象
var tplBody = document.body.innerHTML;//模板对象
var personArray = []; //数组对象
var personObj = {  //json对象
  "name": "oceanwing",
  "age": "10"
}
```

#### [强制] 通过闭包的方式去尽可能的减少全局变量。

解释：避免全局变量泛滥和污染。

``` javascript
//good
!(function(){
  var i = 0,
      flag = true;
})();

//bad
var i = 0,
    flag = true;
```



## 5 方法

#### [建议] 一个函数的长度控制在 `50`行以内，函数参数控制在 `6` 个以内。

#### [建议] js文件或者js方法中，使用 `use strict` (严格模式)。

参考链接：http://www.ruanyifeng.com/blog/2013/01/javascript_strict_mode.html

#### [强制] 如若js方法体内容过多，则将方法体的内容逻辑抽离成一个或者多个方法。

解释：便于理解和维护。

``` javascript
//bad
var joinAnker = function(){
  //第一行
  //...
  //第N行
}

//good
var joinAnker = function(){
  //...
  sendResume();
  //...
  passInterview();
  //...
  report();
  //...
}

```



#### [建议] 使用 `数组` 或 `+` 拼接字符串

示例：

``` javascript
//使用数组拼接字符串
var str = [
  	//推荐换行开始并缩进开始第一个字符串，对齐代码，方便阅读。
  	"<ul>",
  		"<li>第一项</li>",
   		"<li>第二项</li>",
  	"</ul>"
].join("");

//使用 + 拼接字符串
var str2 = ""//建议第一个为空字符串，第二个换行开始并缩进开始，对齐代码，方便阅读
	+ "<ul>",
    +    "<li>第一项</li>",
    +    "<li>第二项</li>",
    + "</ul>";

```

#### [建议] 复杂的数据和试图字符串的转换过程，选用一种模板引擎。

解释：使用模板引擎有如下好处。

1. 在开发过程中专注于数据，将视图生成的过程由另外一个层级维护，使程序逻辑结构更清晰。
2. 优秀的模板引擎，通过模板编译技术和高质量的编译产物，能获得比手工拼接字符串更高的性能。



#### if语句的规范

* if判断条件换行时，运算符必须在新行的行首。
  
* if判断相等尽可能的使用类型严格的 `===` 。仅当判断null或undefined时，使用 `== null`
  
  解释：使用 `===` 可以避免等于判断中隐式的类型转换
  
* if不能省略大括号。
  
* 尽可能的使用简洁的表达式

``` javascript
//good 
if(oceaingwing.erp === anker.erp
   && oceanwing == anker){
  //...
  return true;
}
if(!name){
  //...
}


//bad
if(oceanwing.erp == anker.erp &&
  oceanwing == anker){
  //...
  return true;
}

if(name === ""){
  //...
}

if(true)
  anker();
```



#### jquery事件绑定

* 动态生成的结构，建议用事件委托的方式去绑定事件
* 给元素绑定事件，应通过ID或者class去绑定，class不能用通用的样式class

``` javascript
//good
$("#container").on("click", "#submit", function(){
	//...  
});
$("#container").append("<input type='button' id='submit'/>");

//bad
$(".left").on("click", function(){
  //...
});
```



## 6 对象

#### [强制] 使用对象字面量 `{}` 创建新的 `Object`

示例：

``` javascript
//good
var obj = {};

//bad 
var obj = new Object();
```

#### [建议] 属性访问时，尽量用 `.` 。

解释：

属性名符合 Identifier 的要求，就可以通过 `.` 来访问，否则就只能通过 `[expr]` 方式访问。

#### [建议] `for in` 遍历对象时,使用 `hasOwnProperty` 过滤掉原型中的属性。

示例：

``` javascript
var newInfo = {};
for(var key in info){
  if(info.hasOwnProperty(key)){
    newInfo[key] = info[key];
  }
}
```



#### [建议] 使用数组字面量 `[]` 创建新的数组，除非想要创建指定长度的数组。

示例：

``` javascript
//good 
var arr = [];

//bad 
var arr = new Array();
```



#### [建议] 自定义面向对象时，属性在构造方法中定义，方法在原型中定义。

解释：原型对象的成员被所有实例共享，能节约内存占用。

``` javascript
function TextNode(value, engine){
  this.value = value;
  this.engine = engine;
}

TextNode.prototype.clone = function(){
  return this;
}
```





## 7 注释

#### 【文件注释】包含文件用途、创建人、时间。

``` javascript
/**
 * owp里程碑业务代码
 * Created by flybear on 15/10/25
 */
```

#### 【方法注释】包含方法说明、参数说明、返回值说明。

``` javascript
/**
 * 获得随机Id
 * @param {string} prefix Id前缀
 * @returns {string} 返回带指定前缀的新Id
 */
function getId(prefix){
  return prefix + (new Date()).getTime();
}

```

#### 【声明类属性注释】包含属性说明、类型、默认值。

``` javascript
var Test = function(){
  /**
  * 设置当前页
  * @type number
  * @default 1
  */
  this.currentPage = 1;
}
```

#### 【点击事件注释】 包含方法说明。

``` javascript
$(".input").on("click", function(){//输入框点击事件
  //....
}).on("blur", function(){//输入框失去焦点事件
  //...
});
```



#### 【其他注释】

``` javascript
/**
* =================================================================
* 如果某段代码有功能未实现或者有待改善，必须添加TODO标记，TODO前后应留一个空格
* =================================================================
*/
/**
 * 数据统计
 * @param {string} 产品Id
 * @returns {string} 返回计算结果对象
 */
function calculate(id){
  //.....
  // TODO 导出数据统计文档，下个版本实现。
  //....
  return resultObj;
}

/**
* =================================================================
* 如果在其他同事写的js文件中添加修改内容，则修改的部分需要加上自己的名字，以及修改目的
* =================================================================
*/
/**
 * owp里程碑业务代码
 * Created by oceanwing on 15/10/25
 */
function calculate(id){
  //.....
  // 添加导出数据统计文档功能,add by flybear start.
  // ......
  // add by flybear end.
  //....
  return resultObj;
}


```