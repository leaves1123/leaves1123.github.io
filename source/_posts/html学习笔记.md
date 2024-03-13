---
title: html学习笔记
date: 2023-10-27 11:19:40
tags: 
    - note
    - html
categories: learn
sticky: 1
---

<h1 align="center">HTML部分</h1>

## HTML是什么？

>html(Hyper Text Markup Language), 超文本标签语言, 语言内容由标签组成, 标签通常成对出现, 比如&lt;a&gt;&lt;/a>, 少数是单标签, 主要用于搭建网络框架, 通常与css和javascript联用

注意: 对于成对的标签, 其是不可以交叉的, 比如:
```html
<!--False-->                    <!--True-->
<head>                          <head>
    <title>                         <title>
    </head>                          </title>
</title>                        </head>
```
<!--more-->

## 常用的标签(基础)

```html
标题标签(六级标题)               粗线标签
<h1></h1> - <h6></h6>          <strong></strong> or <b></b>

段落标签
(段落与段落之间有较大空隙)        斜体标签
<p></p>                        <i></i>

换行标签                        下划线标签
<br>                           <u></u>

水平线标签
<hr width="px or %">

区块标签(无具体含义, 只是划分了一个区域, 注意与别的标签的联动用法)
<div></div> 一行只能有一个, 大区块
<span></span> 一行能有多个, 小区块

图片标签
<img src="图像url" alt="图片显示错误时提示文字" title:"鼠标悬停时提示文字"
width="" height="" border="" border-radius=""> 相对路径+绝对路径+网页路径, 
src为必须属性, 属性与属性之间以空格分隔

链接标签
<a href="跳转目标url(相+绝+网页)" target="窗口弹出方式(#为空链接)" title="鼠标悬停时提示文字">文本 or 图像</a>

锚点链接
<a href="#name">text</a> --> <h id="name">text</h>

注释
<!--  -->

特殊字符
不换行空格: &nbsp;   <: &lt;      >: &gt;

...
有些样式也可以通过css控制
```

## 常用的标签(一般)

### 表格
显示数据, 结构如下(实际上用得少, 考虑使用css)
```html
       对齐  单元格内容与单元格间距 单元格间距
<table align="" cellpadding="" cellspacing="" width="" height="" border="">
    <tr> <!--<tr>表示一行-->
        <td></td> or <th></th> <!--<td>是普通单元格; <th是表头单元格, 用于首行, 加粗居中效果>-->
    </tr>
</table>
```
表格还可以分为表头`<thead>`和表体`<tbody>`

### 合并单元格

<table width="50%" align="center">
    <tr>
        <td>跨行合并</td>
        <td>rowspan</td>
    </tr>
    <tr>
        <td>跨列合并</td>
        <td>colspan</td>
    </tr>
</table>

### 列表
多使用无序列表, 后面用css
<table align="center">
    <tr>
        <td>无序列表</td>
        <td>&lt;ul></td>
    </tr>
    <tr>
        <td>有序列表</td>
        <td>&lt;ol></td>
    </tr>
    <tr>
        <td>自定义列表</td>
        <td>&lt;dl></td>
    </tr>
</table>

语法:
```html
无序列表                有序列表              自定义列表(用于名词解释)
<ul>                   <ol>                 <dl>
    <li>内容1</li>        <li>内容1</li>        <dt>名词</dt>
    <li>内容2</li>        <li>内容2</li>        <dd>解释1</dd>
    <li>内容3</li>        <li>内容3</li>        <dd>解释2</dd>
</ul>                  </ol>                </dl>
```

### 表单
收集信息; 表单域`<form>`+表单控件(元素)+提示信息
```html
<form action="url" method="提交方式(post or get)" name="表单域名称">
    +元素
</form>
```

表单常用元素:
`<input>`

```html
<input type=""> <!--单标签-->
```
![type_value](input_attribution.png "type value")

标签`<label>`
```html
<input type="radio" name="key" id="id"> <!--元素的id需和text的id相同-->
    <label for="id">text</label>
效果: 单击text即相当于单击元素
```

下拉列表`<select>`
```html
<select>
    <option>选项1</option>
    <option>选项2</option>
    <option>选项3</option>
</select>
```

文本域`<textarea>`<br>
~一个更大的文本框~

```html
<textarea rows="3" cols="20"> <!--占据3行20字符-->
    text
</textarea>
```
以上基本不会使用(难看), 使用css

## 查阅相关文档
[W3C](https://www.w3school.com.cn/)
[MDN](https://developer.mozilla.org/zh-CN/)

<hr>


<h1 align="center">CSS部分</h1>

## css是什么?
>CSS(Cascading Style Sheets, 层叠样式表), 用于设置html样式, 一个样式表中可以放置多个属性(层叠);

## 基本语法格式
写在`head`中
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Documents</title>

    <style>
        /* 不需要调用 */
        name(标签选择器):{
            相应的属性1: ;
            相应的属性2: ;
        } 

        /* 标签中使用class调用 */
        .name(类选择器):{
            相应的属性1: ;
            相应的属性2: ;

        /* 与类选择器类似, 但是只能用一次 */
        #name(id选择器):{
            相应的属性1: ;
            相应的属性2: ;
        } 
        
        /* 不常用, 清除内外边距 */
        *(通配符选择器):{
            margin: 0;
            padding: 0;
        } 

    </style>

</head>
<body>
    ...
</body>
```
`类选择器`可以单独设置每一个标签(即便标签的类型是一样的))的样式, 只要它的名字不一样

## 常用属性
### 字体
<table>
    <tr align="center">
        <th>属性</th>
        <th>用于</th>
        <th>单位</th>
    </tr>
    <tr align="center">
        <td>font-size</td>
        <td>字体大小</td>
        <td>px</td>
    </tr>
    <tr align="center">
        <td>font-weight</td>
        <td>字体粗细</td>
        <td>none</td>
    </tr>
    <tr align="center">
        <td>font-style</td>
        <td>字体类型</td>
        <td>none</td>
    </tr>
</table>

上述字体属性可以综合写
`body{font: font-style font-weight font-size/line-height font-family}`

注意: 

+ 顺序不能颠倒
+ 不同属性之间空格隔开
+ 必须保留`font-size & font-family`

### 文本
|      属性       |   用于   | 单位  |
| :-------------: | :------: | :---: |
|      color      | 文本颜色 | none  |
|   text-align    | 文本对齐 | none  |
|   text-align    | 文本对齐 | none  |
| text-decoration | 文本修饰 | none  |
|   text-indent   | 文本缩进 | px/em |
|   line-height   |  行间距  |  px   |
|   line-height   |  行间距  |  px   |

<div>注:</div>

+ `text-decoration`主要用于设置下划线`underline` `none`
+ `em`是相对单位, 为当前元素中一个字符的像素大小
+ 上间距+文本高度+下间距 = 行间距

## 样式表分类
+ 行内样式表
写在标签内
`<div style="color: ;font-size: ;"></div>`
不常用

+ 内部样式表
即上面的语法格式

+ 外部样式表
所有样式写在外部.css文件中, 再导入html文件中
`<link rel="stylesheet" href="path/to/css">`

## chrome调试工具
![](chrome_debug.png)

## emmet语法
+ `div`+`tab键` = `<div></div>`
+ `div*3`+`tab键` = 3个`div`标签
+ 父子级关系`>`
```html
ul>li -> 
<ul>
    <li></li>
</ul>
```
+ 兄弟关系`+`
```html
div+p ->
<div></div>
<p></p>
```
- 如果生成带有类名或者id名字的，  直接写  .demo  或者  #two   tab 键就可以了
- 如果生成的div 类名是有顺序的， 可以用 自增符号  $ 
- 如果想要在生成的标签内部写内容可以用  {}  表示

## 复合选择器

>多个基础选择器 = 复合选择器

### 后代选择器
![后代选择器](后代选择器.png)

### 子选择器
```html
元素1 > 元素2 {样式声明}
```
+ 中间用`>`隔开
+ 只能选择所有最靠近元素1的元素2

### 并集选择器

```html
元素1, 元素2 {样式声明}
```
+ 中间用`,`隔开
+ 多个标签共同配置样式

### 伪类选择器

>用于添加特殊效果, 用`:`表示, 比如`:hover`

#### 链接伪类选择器

```html
a { 
    color: gray;
}

/* 设置鼠标经过时链接改变颜色 */
a:hover { 
    color: red;
}
```
+ a:link     没有点击时的链接
+ a:visited  点击过的链接
+ a:hover    鼠标经过时的链接
+ a:cative   正在按下但是还没有弹起时的链接

>顺序说明: `:link-:visited-:hover-:active`

#### focus伪类选择器
```html
/* 设置光标在表单元素上时颜色为黄色 */
input:focus {
    background-color:yellow;
}
```
### 总结
![复合选择器总结](复合选择器总结.png)

## css显示模式

>即标签以什么方式进行显示, 例如`div`独占一行, `span`在一行中可以存在多个

### 元素显示模式分类
+ 块元素
  + 自己独占一行
  + 高度+宽度+内外边距
  + 内部可以放其它行内或块元素
  + 文字类元素内不能放块元素
```html
<h1>~<h6> <p> <div> <ul> <ol> <li>
```
+ 行内元素
  + 元素在同一行, 一行可显示多个
  + 无高度, 宽度设置
  + 只能容纳文本或其它行内元素

```html
<a> <strong> <b> <em> <i> <del> <s> <ins> <u> <span>
```
+ 行内块元素
  + 与相邻行内元素在一行上, 中间有空白缝隙 
  + 一行有多个(行内元素)
  + 可以控制高度, 宽度, 内外边距(块级元素)

```html
<img> <input> <td>
```

### 总结
![元素显示模式总结](元素显示模式总结.png)

## 显示模式转换
|          语法          |      结果      |
| :--------------------: | :------------: |
|    `dispaly:block`     |   转为块元素   |
|    `dispaly:inline`    |  转为行内元素  |
| `dispaly:inline-block` | 转为行内块元素 |

## 文字垂直居中显示

文字的`行高` = `盒子高度`

## css背景

>添加背景样式, 如颜色 图片等

+ 背景颜色

```html
background-color:颜色值;  /* 默认是transparent */
```
+ 背景图片

```html
background-image: none | url(); /* 默认是none */
```

+ 背景平铺

```html
background-repeat: repeat | no-repeat | repeat-x | repeat-y;
```
![背景平铺](背景平铺总结.png)

+ 背景图片位置
  + 参数可以是精确数值也可以是方位名词
  + 精确数值时`x`和`y`的位置必须为前左后右
  + 方位名词时可不考虑顺序
  + 只设置其中一个, 另一个位置必居中对齐

```html
background-position: x y;
```

+ 背景图片固定
  + `scroll`: 背景图像随对象内容滚动
  + `fixed`: 固定

```html
background-attachment: scroll | fixed
```

+ 与背景相关的复合写法

>约定顺序: `背景颜色 背景图片地址 背景平铺 背景图像滚动 背景图片位置;`

```html
background: transparent url() repeat fixed top
```

+ 背景色半透明
```html
background: rgba(0,0,0,.3)
```

### 总结

![背景总结](背景总结.png)

## CSS三大特性
+ 层叠性: 就近原则, 解决样式冲突问题
+ 继承性: 子标签会继承父标签的某些样式，如文本颜色和字号
+ 优先级: 
  + 选择器相同，则执行层叠性
  + 选择器不同，则根据选择器权重执行

![选择器优先级](选择器优先级.png)
> 左边的数字`>`右边, 且没有进位, 多种选择器权重可以`叠加`

## 盒子模型

### 网页布局

网页布局过程:

1. 先准备好相关的网页元素, 网页元素基本都是盒子 Box
2. 利用 CSS 设置好盒子样式, 然后摆放到相应位置
3. 往盒子里面装内容

### 盒子模型组成(box)

![盒子模型组成](盒子模型组成.png)

## 边框(border)

由三个部分组成:

+ 边框宽度, 单位是px
+ 边框样式, none || solid || dashed || dotted
+ 边框颜色

```css
border : border-width || border-style || border-color;
```

```css
border: 1px solid red; /* 简写 */
border-top: 1px solid red; /* 只设置上边框样式, 其余类似 */
border-collapse: collapse; /* 相邻边框合并在一起 */
```
> 边框会影响盒子的实际大小

解决:
+ 设置边框大小值为0
+ 重新设置box的宽度 | 高度
  + `width/height-border-width`

## 边距

### 内边距

> `padding`用于设置内边距, 为边框与内容之间的距离

![内边距语法](内边距语法.png)

![内边距语法2](内边距语法2.png)

> 当`box`设置了宽度和高度时, 添加`padding`会使得`box`变大

解决:
+ 可以让盒子适应图片也可以让图片适应盒子

### 外边距

> `margin`用于设置外边距, 控制盒子与盒子之间的距离

![外边距属性](外边距属性.png)

让块级元素水平居中
+ `box`必须有`width`
+ `box`的左右外边距为`auto`

```css
margin-left: auto; margin-right: auto;
margin: auto; margin:0 auto /* 常用 */
```

> 以上方法是让块级元素水平居中, 行内元素或者行内块元素水平居中给其父元素添加 `text-align:center` 即可

### 外边距合并

+ `上下相邻`的块元素, 只设置一个`box`的`margin`即可
+ `嵌套关系`的块元素
  + 可以为父元素定义上边框
  + 可以为父元素定义上内边距
  + 可以为父元素添加 `overflow:hidden`

### 清除内外边距

> 布局前, 首先要清除下网页元素的内外边距

```css
* {
    padding: 0;
    margin: 0;
}
```
> 行内元素为了照顾兼容性`(?)`, 尽量只设置左右内外边距, 不要设置上下内外边距; 但是转换为块级和行内块元素就可以了

## 其它样式

### 圆角边框

`border-radius`用于设置元素的外边框圆角

```css
border-radius: length;
```
~值越大弧度越明显~

+ `length`可以是数值也可以是百分比
+ 格式为`上右下左`
+ 也可以分开写
    + border-top-left-radius
    + border-top-right-radius
    + border-bottom-right-radius
    + border-bottom-left-radius

### 盒子阴影

```css
box-shadow: h-shadow v-shadow blur spread color inset;
```
![盒子阴影](盒子阴影.png '盒子阴影')

### 文字阴影

```css
text-shadow: h-shadow v-shadow blur color;
```
![文字阴影](文字阴影.png '文字阴影')

## 浮动

> 用于一行上显示多个盒子, 且默认盒子与盒子之间没有空隙, 布局用; 标准流父元素排上下, 内部浮动子元素排左右

```css
选择器{
    float: none | left | right;
}
```

+ ![浮动特性](浮动特性.png '浮动特性')
+ 浮动的元素会一行内显示并且元素顶部对齐
+ 浮动的元素会具有行内块元素的特性
    + 大小根据内容决定
    + 一个元素浮动, 兄弟元素也要浮动
+ 有时需要清除浮动
    + ![浮动影响](浮动影响.png '浮动影响')

```css
选择器{
    clear: left | right | both;
}
```
推荐的方法为父级添加after伪元素

```css
.clearfix:after {  
    content: ""; 
    display: block; 
    height: 0; 
    clear: both; 
    visibility: hidden;  
} 
.clearfix {  /* IE6、7 专有 */ 
    *zoom: 1;
}   
```
或者给父级添加双伪元素
```css
.clearfix:before,.clearfix:after {
    content:"";
    display:table; 
}
.clearfix:after {
    clear:both;
}
.clearfix {
    *zoom:1;
}   
```
~一般用这个~
> 如果父盒子本身有高度, 则不需要清除浮动

## ps切图
> ps+cutterman

[cutterman](http://www.cutterman.cn/zh/cutterman)为`ps`中的插件

## CSS书写属性

> 一般遵循以下顺序

1. **布局定位属性**：display / position / float / clear / visibility / overflow（建议 display 第一个写，毕竟关系到模式）
2. **自身属性**：width / height / margin / padding / border / background
3. **文本属性**：color / font / text-decoration / text-align / vertical-align / white- space / break-word
4. **其他属性（CSS3）**：content / cursor / border-radius / box-shadow / text-shadow / background:linear-gradient …

e.g.
```css
.jdc {
    display: block;
    position: relative;
    float: left;
    width: 100px;
    height: 100px;
    margin: 0 10px;
    padding: 20px 0;
    font-family: Arial, 'Helvetica Neue', Helvetica, sans-serif;
    color: #333;
    background: rgba(0,0,0,.5);
    border-radius: 10px;
} 
```

## 页面布局整体思路

1. 必须确定页面的版心, 即可视区域
2. 分析页面中的行模块以及每个行模块的列模块
3. 一行中的列模块经常浮动布局, 先确定每个列的大小, 再确定列的位置(e.g. float: left)
4. 先结构, 后样式
5. coding之前先在脑海中搭建好结构

<b>这个例子还需要再练习一遍</b>


## 定位(position)

### 为什么要使用定位
```markdown
定位可用于让盒子自由的在某个盒子内移动位置或者固定在屏幕中的某个位置, 且可以压住其它盒子(浮动的效果)
```

### 定位的组成
定位 = 定位模式+边偏移

+ 定位模式: 用于指定一个元素在文档中的定位方式(如**相对和绝对**)
+ 边偏移: 决定该元素的最终位置(如**top, left...**)

一般情况下, 有定位的地方必有边偏移

#### 定位模式(position)

```css
选择器 {
    position: 属性值;
}
```

| 值 | 语义 | 说明 |
| -- | -- | -- |
| `static` | 静态定位 | 几乎不用 | 
| `relative` | 相对定位 | 相对于<u>自己原来的位置</u>, 保留位置|
| `absolute` | 绝对定位 | 相对于<u>祖先元素</u>的位置, 不保留位置|
| `fixed` | 固定定位 | 固定于<u>浏览器可视区位置</u> |

注意:
+ 对于`绝对定位`
    + 没有祖先元素或者祖先元素没有定位的情况下, 以浏览器为基准进行定位
    + 如果祖先元素有定位, 则以最近一级的有定位的祖先元素为参考点移动位置
    + 绝对定位不保留位置(脱标)
+ 对于`固定定位`
    + 以浏览器的可视窗口为参考点移动元素(不随滚动条滚动)
    + 不保留原来的位置
+ `子绝父相`
    + 指子盒子元素相对定位, 父盒子元素绝对定位
    + 用于设置一个大盒子中嵌套一个不占位置的子盒子
    + 当父元素不需要保留位置的时候, 可演变为`子绝父绝`

### 定位的一个常用应用
让盒子贴着版心右侧区域移动
1. 具有固定定位属性的盒子`left: 50%`
2. 再使其`margin-left: 版心宽度/2`

### 堆叠顺序(z-index)
> 定位布局时, 盒子可能会发生重叠的情况, 此时可用**z-index**来调整前后次序

语法
```css
选择器 {
    z-index: 1'
}
```

特点: 
+ 整数(包括0), 数值越大, 盒子越靠上
+ 如果每个盒子的`z-index`值相同, 则按照书写顺序来排
+ 无单位
+ 用于**相对定位&绝对定位&固定定位**

### 定位的拓展

+ 设置了`绝对定位&固定定位`的盒子设置水平居中的方式
    1. `left: 50%`
    2. `margin-left: -(本身宽度的一半)`
+ 对于行内元素盒子, 添加`浮动`, `固定定位`或`绝对定位`, 则不用转换即可直接设置宽度和高度
+ 添加浮动或定位, 则不会有*垂直外边距合并*的问题了
+ 绝对定位的元素会压住下面标准流的所有元素, 而浮动的元素会压住盒子, 但不会压住文字

## 元素的显示与隐藏

`display`

语法:

```css
display: attribute;
```

|attribute|explain|
|--|--|
|none|隐藏对象, 之后不再占有位置|
|block|转换位块级元素的同时显示元素|

`visibility`

语法:
```css
visibility: attribute;
```

|attribute|explain|
|--|--|
|hidden|隐藏对象, 继续占有位置|
|visible|显示元素|

`overflow`

```markdown
用于指定内容溢出元素时, 会发生什么
```

|attribute|explain|
|--|--|
|visible|不剪切内容也不添加滚动条|
|hidden|超出部分隐藏|
|scroll|始终显示滚动条|
|auto|超出时才显示滚动条|

## 精灵图
`目的: `为了提高网页加载的速度
`原理: `将小图片整合成一张大图片, 后续只需调整精灵图的位置即可

`使用核心:`
+ 调整位置使用background-position
+ 一般调整的坐标值都是负数, 这是因为相对于浏览器的坐标是向右为正, 向下为正
+ 每个小图片的位置需要精确测量

## 字体图标(iconfont)
> 一般网页中的小图标都是字体图标, 展示的是图标, 本质属于字体

+ 可以改变颜色; 产生阴影效果; 透明效果; 旋转等
+ 主要针对的是图标部分

### 字体图标的下载
+ **icomoon:**http://icomoon.io
+ **ali:**http://www.iconfont.cn/

### 字体图标的使用
+ 网站上下载->解压->**fonts**文件夹放到页面的根目录下
+ css样式中全局声明字体

```css
@font-face {
    font-family: 'icomoon';
    src:  url('fonts/icomoon.eot?7kkyc2');
    src:  url('fonts/icomoon.eot?7kkyc2#iefix') format('embedded-opentype'),
        url('fonts/icomoon.ttf?7kkyc2') format('truetype'),
        url('fonts/icomoon.woff?7kkyc2') format('woff'),
        url('fonts/icomoon.svg?7kkyc2#icomoon') format('svg');
    font-weight: normal;
    font-style: normal;
}
```
+ 标签内添加小图标
+ 给标签定义字体
```css
span {
    font-family: "icomoon";
}
```

`注意: `font-family须一致

+ 字体图标的追加: 在网站上上传`selection.json`, 再重新下载即可

## css三角
`做法原理: `盒子的宽度和高度设置为0, 边框设置得大一些, 能够产生三角的形状, 两个盒子进行拼凑则有可能可以得到一个梯形的形状

## css用户界面样式
+ 鼠标样式
```css
li {
    cursor: pointer; /* 小手的意思 */
}
```
+ 轮廓线
```css
input {
 	outline: none; /* 去掉默认的蓝色边框 */
}
```
+ 防止拖曳文本域(resize)
```css
textarea{ 
 	resize: none;
}
```

## vertical-align属性应用
> 用于设置图片/表单和文字的垂直对齐方式(只针对于行内元素/行内块元素)

`语法`
```css
vertical-align : baseline | top | middle | bottom 
```

### 解决图片底部默认空白缝隙问题
1. `vertical-align:middle | top| bottom`

2. 把元素转为块级元素

## 溢出的文字省略号显示
```css
  /*1. 先强制一行内显示文本*/
   white-space: nowrap;  （ 默认 normal 自动换行）
   
  /*2. 超出的部分隐藏*/
   overflow: hidden;
   
  /*3. 文字用省略号替代超出的部分*/
   text-overflow: ellipsis;
```

## HTML5新特性

### 新增加一些语义化标签
|标签|说明|
|--|--|
|\<header>|头部标签|
|\<nav>|导航栏标签|
|\<article>|内容标签|
|\<section>|定义文档某个区域|
|\<aside>|侧边栏标签|
|\<footer>|尾部标签|

### 多媒体标签

`1. 视频标签`
> 一般使用.mp4格式

语法:
```html
<video src="media/mi.mp4"></video>
```

常用属性
|属性|值|说明|
|--|--|--|
|autoplay|autoplay|自动播放|
|width|pixels|宽度|
|height|pixels|高度|
|loop|loop|循环播放|
|src|url|播放源|
|myted|muted|静音播放|

**示例代码**

```html
<video src="media/mi.mp4" autoplay="autoplay" muted="muted"  loop="loop" poster="media/mi9.jpg"></video>
```

`2. 音频标签`
> 一般使用.mp3格式

语法:
```html
<audio src="media/music.mp3"></audio>
```

常用属性

|属性|值|描述|
|--|--|--|
|autoplay|autoplay|自动播放|
|controls|controls|显示播放按钮|
|loop|loop|循环播放|
|src|url|路径|

**示例代码**

```html
<audio src="media/music.mp3" autoplay="autoplay" controls="controls"></audio>
```

### 新增表单元素

语法:
```html
<input type="xxx"/>
```
常见的输入类型
```markdown
text password radio checkbox button file hidden submit reset image
```

## CSS3新特性

### 属性选择器
> 即根据标签中的属性来选择元素

**示例代码**

```css
 /* 只选择 type =text 文本框的input 选取出来 */
input[type=text] {
    color: pink;
}
/* 选择首先是div 然后 具有class属性 并且属性值 必须是 icon开头的这些元素 */
div[class^=icon] {
    color: red;
}
/* 选择首先是section 然后 具有class属性 并且属性值 必须是 data结尾的这些元素 */
section[class$=data] {
    color: blue;
}
```
`注: 权重为10`

### 结构伪类选择器

> 一般用于根据父级选择器选择里面的子元素, 更多的选取规则可网上查阅

**示例代码**

```html
 <style>
    ul li:first-child{
      background-color: red;
    }
  </style>

  <ul>
    <li>列表项一</li>
    <li>列表项二</li>
    <li>列表项三</li>
    <li>列表项四</li>
  </ul>
```

注意:
+ `nth-child(n)`: 只有排序
+ `nth-of-type(n)`: 先考虑元素类型再排序


### 伪元素选择器

> 可以用于CSS创建新标签元素设置样式, 但并不是HTML标签, 因此称作`伪元素`

|选择符|简介|
|--|--|
|::before|在元素的前面插入内容|
|::after|在元素的后面插入内容|

**示例代码**

```html
<style>
    div {
        width: 200px;
        height: 200px;
        background-color: pink;
    }
    /* div::before 权重是2 */
    div::before {
        /* 这个content是必须要写的 */
        content: '我';
    }
    div::after {
        content: '小猪佩奇';
    }
</style>
<body>
    <div>
        是
    </div>
</body>
```

注意:
+ before 和 after 创建一个元素，但是属于行内元素
+ 语法：`element::before {}`
+ before 和 after 必须有 `content` 属性 
+ before 在父元素内容的前面创建元素，after 在父元素内容的后面插入元素
  伪元素选择器和标签选择器一样，权重为`1`

应用场景一: `字体图标`

**示例代码**

```html
<head>
    ...
    <style>
        @font-face {
            font-family: 'icomoon';
            src: url('fonts/icomoon.eot?1lv3na');
            src: url('fonts/icomoon.eot?1lv3na#iefix') format('embedded-opentype'),
                url('fonts/icomoon.ttf?1lv3na') format('truetype'),
                url('fonts/icomoon.woff?1lv3na') format('woff'),
                url('fonts/icomoon.svg?1lv3na#icomoon') format('svg');
            font-weight: normal;
            font-style: normal;
            font-display: block;
        }
        div {
            position: relative;
            width: 200px;
            height: 35px;
            border: 1px solid red;
        }

        div::after {
            position: absolute;
            top: 10px;
            right: 10px;
            font-family: 'icomoon';
            /* content: ''; */
            content: '\e91e';
            color: red;
            font-size: 18px;
        }
    </style>
</head>
<body>
    <div></div>
</body>
```

应用场景二: `设置遮罩层`

**示例代码**

```html
<head>
    ...
    <style>
        .tudou {
            position: relative;
            width: 444px;
            height: 320px;
            background-color: pink;
            margin: 30px auto;
        }

        .tudou img {
            width: 100%;
            height: 100%;
        }

        .tudou::before {
            content: '';
            /* 隐藏遮罩层 */
            display: none;
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, .4) url(images/arr.png) no-repeat center;
        }

        /* 当我们鼠标经过了 土豆这个盒子，就让里面before遮罩层显示出来 */
        .tudou:hover::before {
            /* 而是显示元素 */
            display: block;
        }
    </style>
</head>

<body>
    <div class="tudou">
        <img src="images/tudou.jpg" alt="">
    </div>
    <div class="tudou">
        <img src="images/tudou.jpg" alt="">
    </div>
    <div class="tudou">
        <img src="images/tudou.jpg" alt="">
    </div>
    <div class="tudou">
        <img src="images/tudou.jpg" alt="">
    </div>
</body>
```

应用场景三: `清除浮动`

### 盒子模型

|属性: 值|说明|
|--|--|
|box-sizing: content-box|盒子大小为width+padding+border|
|box-sizing: border-box|盒子大小为width|

注: 当设置`box-sizing: border-box`时, padding和border在不超出宽度的情况下不会撑大盒子

### 其它特性

+ 图片变模糊

**语法:**

```css
filter:   函数(); -->  例如： filter: blur(5px);  -->  blur模糊处理  数值越大越模糊
```

+ 计算盒子宽度

**语法:**
语法：

```css
width: calc(100% - 80px);
```

+ 过渡
> 一个状态过渡到另一个状态, 动态效果
**语法:**

```css
transition: 要过渡的属性  花费时间  运动曲线  何时开始;
```
**示例代码**
> 添加一个动态的progress bar
```html
<head>
    ...
    <style>
        .bar {
            width: 150px;
            height: 15px;
            border: 1px solid red;
            border-radius: 7px;
            padding: 1px;
        }
        .bar_in {
            width: 50%;
            height: 100%;
            background-color: red;
            /* 谁做过渡给谁加 */
            transition: all .7s;
        }
        .bar:hover .bar_in {
            width: 100%;
        }
    </style>
</head>
<body>
    <div class="bar">
        <div class="bar_in"></div>
    </div>
</body>
```






