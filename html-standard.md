# HTML编码规范

### 1 标签

#### [强制] 标签名使用小写字母。

示例：

``` html
<!-- good -->
<p>oceanwing</p>

<!-- bad -->
<P>oceanwing</P>
```



#### [建议] 对于无需自闭合的标签，需要自闭合

解释：

常见的无需自闭合标签有input、br、img等。

示例：

``` html
<!-- good -->
<input type="text" name="title" />

<!-- bad -->
<input type="text" name="title">
```



#### [建议] 在 `CSS` 可以实现同等需求的情况下尽量不要使用表格布局。

解释：表格绘制需要多次，而其他的标签知需要一次。



#### [强制] `HTML` 标签的使用应该遵循标签的语义。

解释：

下面是常见标签语义

- p - 段落
- h1,h2,h3,h4,h5,h6 - 层级标题
- strong,em - 强调
- ins - 插入
- del - 删除
- abbr - 缩写
- code - 代码标识
- cite - 引述来源作品的标题
- q - 引用
- blockquote - 一段或长篇引用
- ul - 无序列表
- ol - 有序列表
- dl,dt,dd - 定义列表





### 2 属性

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

示例：

``` html
<div data-id="1"></div>
```

#### [建议] 非必须属性值，建议不添加属性值。

示例：

``` html
<!-- good -->
<input type="text" readonly />
<input type="text" disabled />

<!-- bad -->
<input type="text" readonly="readonly" />
<input type="text" disabled="disabled" />
```



### 3 通用

#### [建议] DOCTYPE，使用 `HTML5` 的 `doctype` 来启用标准模式，建议使用大写的 `DOCTYPE` 。

示例：

``` html
<!DOCTYPE html>
```

#### [建议] 启用IE Edge 模式。

示例：

``` html
<meta http-equiv="X-UA-Compatible" content="IE=Edge">
```



### 4  CSS和Javascript引入

#### [建议] 展示定义放置于 `CSS` 中，行为定义放置于外部 `Javascript` 中。

解释：

结构-样式-行为的代码分离，对于提高代码的可阅读性和维护性都有好处。

#### [建议] 在 `head` 中引入页面需要的所有 `CSS` 资源。

解释：

在页面的渲染过程中，新的css可能导致页面重拍和重绘，或者出现闪速的现象。

#### [建议] `javascript` 应当放到页面的末尾，或采取异步加载。

解释：

将js放在页面中间会阻断页面的渲染。



### 5 表单

#### [强制] 有文字标题的控件，必须使用 `label` 标签将其与标题相关联。

解释：

有两种方式：

1、将控件至于label标签内。

2、将label的for属性指向控件的ID。

示例：

``` html
<label><input type="checkbox" name="confirm" value="on"/> 我已同意上述条款</label>

<label for="username"></label><input type="checkbox" name="username" id="username"/>
```



### 6 模板

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



### 7 注释

代码块之间是注释标明和分隔开。

``` html
<!-- header start -->
<header>
	这是头部
  	....
</header>
<!-- header end -->

<!-- 内容区域 start -->
<section>
	内容区域
  	....
</section>
<!-- 内容区域 end -->

<!-- 页脚 start-->
<footer>
	页脚区域
  	....
</footer>
<!-- 页脚 end -->

<!-- 弹出框模板 start -->
<script id="tplDialog" type="text/html">
	<div>
    	...
    </div>
</script>
<!-- 弹出框模板 end -->
```