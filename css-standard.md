# CSS开发规范

### 1 命名

#### [强制] 组成元素

- 命名必须由单词、中划线或数字组成。
  
- 不允许使用拼音（约定俗成的除外，如：youku,baidu），尤其是缩写的拼音、拼音和英文混合。
  
  示例：
  
  ``` css
  /** good **/
  .detail{
    display: none;
  }
  .news-list{
    display: block;
  }
  
  /** bad **/
  .xiangqing{
    display: none;
  }
  .new_list{
    display: block;
  }
  ```



#### [建议] 前缀规范

|  前缀  | 说明                    | 示例          |
| :--: | :-------------------- | :---------- |
| xx-  | 业务模块命名方式，前缀表示该业务模块的名称 | anker-table |
| ui-  | 组件命名方式                | ui-selector |
| js-  | 所有用于纯交互的命名，不涉及任何样式规则。 | js-switch   |

### 2 书写格式

- 选择器与大括号之间保留一个空格；
- 所有规则需换行；
- 多组选择器之间需换行；
- 属性为 `0`，则不需要加单位；
- 颜色值建议用 `16进制值` 去表示；
- `>` 、`+` 、`~` 选择器的两边各保留一个空格。

示例：

``` css
.anker {
  display: block;
}

h1,
h2,
h3 {
  margin: 0;
  background-color: #FFFFFF;
}

div > p {
  font-size: 12px;
}

```



### 3 通用

#### [建议] 尽量不使用 `!important` 声明。

#### [建议] 尽量不使用import引入css文件。

#### [建议] 尽量不使用内联样式，应将其抽离出来放入css文件中。

#### [建议] 将 `z-index` 进行分层，对文档流外绝对定位的元素的视觉层级关系进行管理。

#### [强制] 页面文字大小应不小于 `12px` 。

解释：chrome浏览器最小字体为12px。

#### [强制] 禁止使用 `Expression` 。

#### [建议] 在可以使用缩写的情况下，尽量使用属性缩写。

``` css
/* good */
.post {
    font: 12px/1.5 arial, sans-serif;
}

/* bad */
.post {
    font-family: arial, sans-serif;
    font-size: 12px;
    line-height: 1.5;
}
```



### 4、注释

普通注释（单行）

``` css
/* 普通注释 */
```

区块注释

``` css
/**
 * 区块注释
 */
```