---
title: html学习笔记
date: 2023-10-27 11:19:40
tags: 
    - note
    - html
categories: learn
sticky: 300
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






