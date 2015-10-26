# HTML编码规范

[1 代码风格](#user-content-1-代码风格)

​	[1.1 命名](user-content-11-命名)

​	[1.2 标签](user-content-12标签)





## 1 代码风格

### 1.1 命名

#### **id命名：** `id`  全小写，单词之前用 `-` 分隔开。

#### **class命名：** `class` 全小写，单词之前用  `-` 分隔开。

#### **常量命名：** 全大小 ，单词之前用 `_` 分隔开。

#### **变量命名：** 小驼峰式命名。

#### 注：jquery对象赋值给变量时，变量前面加 `$` ，html模板赋值给变量时，变量前面加 `tpl`	 。

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

//bad
var ocean_erp_count = 20, //变量
	OCEANERPCOUNT = 20, //常量
    body = $(document.body), //jquery对象
    bodyHtml = document.body.innerHTML; //html模板
```



#### [建议] `id` 、 `class` 命名，在描述清楚的前提下尽可能的短。

``` html
<!-- good -->
<div id="nav"></div>

<!-- bad -->
<div id="navigation"></div>
```



### 1.2 标签

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



### 1.3 属性

#### [强制] 属性名称必须使用小写字母。

示例：

``` html
<!-- good -->
<table cellspacing="0"></table>

<!-- bad -->
<table cellSpacing="0"></table>
```



#### [建议] 自定义属性建议以 `XXX-` 为前缀，推荐使用 `data-` 。

解释：data-*的形式，所有主流浏览器都支持，而且可以通过jquery的data方法去获取。





## 2 通用

### 2.1 DOCTYPE

#### 使用 `HTML5` 的 `doctype` 来启用标准模式，建议使用大写的 `DOCTYPE` 。

示例：

``` html
<!DOCTYPE html>
```

#### [建议] 启用IE Edge 模式。

示例：

``` html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```



### 2.2  CSS和Javascript引入

#### [建议] 展示定义放置于 `CSS` 中，行为定义放置于外部 `Javascript` 中。

解释：

结构-样式-行为的代码分离，对于提高代码的可阅读性和维护性都有好处。

#### [建议] 在 `head` 中引入页面需要的所有 `CSS` 资源。

解释：

在页面的渲染过程中，新的css可能导致页面重拍和重绘，或者出现闪速的现象。

#### [建议] `javascript` 应当放到页面的末尾，或采取异步加载。

解释：

将js放在页面中间会阻断页面的渲染。



## 3 表单

### 3.1 控件标题 

#### [强制] 有文件标题的控件，必须使用 `label` 标签将其与标题相关联。

解释：

有两种方式：

1、将控件至于label标签内。

2、将label的for属性指向控件的ID。

示例：

``` html
<label><input type="checkbox" name="confirm" value="on"/> 我已同意上述条款</label>

<label for="username"></label><input type="checkbox" name="username" id="username"/>
```





## 4 模板中的html

#### [建议] 模板代码的缩进优先保证 `HTML` 代码的缩进规则。

示例：

``` html
<!-- good -->
{#if true}
<div>
  <ul>
    {#each list}
    <li>{{item}}</li>
    {/each}
  </ul>
</div>
{/if}

<!-- bad -->
{#if true}
	<div>
      <ul>
		{#each list}
        	<li>{{item}}</li>
        {/each}
      </ul> 
    </div>
{/if}
```



