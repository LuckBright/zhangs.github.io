---
categories:
- 前端基础
date: '2022-10-24T05:58:00.000Z'
showToc: true
tags:
- 前端基础
title: 测试自动化

---



## HTML && CSS

### HTML5 新特性、语义化

1. **概念**：

  HTML5的语义化指的是`合理正确的使用语义化的标签来创建页面结构`。【正确的标签做正确的事】

1. **语义化标签**：

  header nav main article section aside footer

1. **语义化的优点**:

  - 在`没CSS样式的情况下，页面整体也会呈现很好的结构效果`

  - `代码结构清晰`，易于阅读，

  - `利于开发和维护` 方便其他设备解析（如屏幕阅读器）根据语义渲染网页。

  - `有利于搜索引擎优化（SEO）`，搜索引擎爬虫会根据不同的标签来赋予不同的权重

### HTML5新特性有哪些

- 语义化标签

- 音视频处理API(audio,video)

- canvas / webGL

- 拖拽释放(Drag and drop) API

- history API

- requestAnimationFrame

- 地理位置(Geolocation)API

- webSocket

- web存储 localStorage、SessionStorage

- 表单控件，calendar、date、time、email、url、search

### CSS 选择器及优先级

**选择器**

- id选择器(#myid)

- 类选择器(.myclass)

- 属性选择器(a[rel="external"])

- 伪类选择器(a:hover, li:nth-child)

- 标签选择器(div, h1,p)

- 相邻选择器（h1 + p）

- 子选择器(ul > li)

- 后代选择器(li a)

- 通配符选择器(*)

**优先级：**

- `!important`

- 内联样式（1000）

- ID选择器（0100）

- 类选择器/属性选择器/伪类选择器（0010）

- 元素选择器/伪元素选择器（0001）

- 关系选择器/通配符选择器（0000）

带!important 标记的样式属性优先级最高； 样式表的来源相同时：
`!important > 行内样式>ID选择器 > 类选择器 > 标签 > 通配符 > 继承 > 浏览器默认属性`

### 渐进增强与优雅降级的理解及区别

**渐进增强（Progressive Enhancement）：**
一开始就针对低版本浏览器进行构建页面，完成基本的功能，然后再针对高级浏览器进行效果、交互、追加功能达到更好的体验。

**优雅降级（Graceful Degradation）：**
一开始就构建站点的完整功能，然后针对浏览器测试和修复。比如一开始使用 CSS3 的特性构建了一个应用，然后逐步针对各大浏览器进行 hack 使其可以在低版本浏览器上正常浏览。
**两者区别**
1、广义：
其实要定义一个基准线，在此之上的增强叫做渐进增强，在此之下的兼容叫优雅降级
2、狭义：
渐进增强一般说的是使用CSS3技术，在不影响老浏览器的正常显示与使用情形下来增强体验，而优雅降级则是体现html标签的语义，以便在js/css的加载失败/被禁用时，也不影响用户的相应功能。

```plain text
/* 例子 */
.transition { /*渐进增强写法*/
  -webkit-transition: all .5s;
     -moz-transition: all .5s;
       -o-transition: all .5s;
          transition: all .5s;
}
.transition { /*优雅降级写法*/
          transition: all .5s;
       -o-transition: all .5s;
     -moz-transition: all .5s;
  -webkit-transition: all .5s;
}


```

### 常见的兼容性问题

1. 不同浏览器的标签默认的margin和padding不一样。*{margin:0;padding:0;}

1. IE6双边距bug：块属性标签float后，又有横行的margin情况下，在IE6显示margin比设置的大。hack：display:inline;将其转化为行内属性。

1. 设置较小高度标签（一般小于10px），在IE6，IE7中高度超出自己设置高度。hack：给超出高度的标签设置overflow:hidden;或者设置行高line-height 小于你设置的高度。

1. Chrome 中文界面下默认会将小于 12px 的文本强制按照 12px 显示,可通过加入 CSS 属性 -webkit-text-size-adjust: none; 解决。

1. 超链接访问过后hover样式就不出现了，被点击访问过的超链接样式不再具有hover和active了。解决方法是改变CSS属性的排列顺序:L-V-H-A ( love hate ): a:link {} a:visited {} a:hover {} a:active {}

### CSS3新特性

- 过渡

```plain text
/*所有属性从原始值到制定值的一个过渡，运动曲线ease,运动时间0.5秒*/
transition：all,.5s

```

- 动画

```plain text
//animation：动画名称，一个周期花费时间，运动曲线（默认ease），动画延迟（默认0），播放次数（默认1），是否反向播放动画（默认normal），是否暂停动画（默认running）
/*执行一次logo2-line动画，运动时间2秒，运动曲线为 linear*/
animation: logo2-line 2s linear;

```

- 形状转换

```plain text
//transform:适用于2D或3D转换的元素
//transform-origin：转换元素的位置（围绕那个点进行转换）。默认(x,y,z)：(50%,50%,0)
transform:translate(30px,30px);
transform:rotate(30deg);
transform:scale(.8);

```

- 选择器:nth-of-type()

- 阴影
文字阴影: text-shadow: 2px 2px 2px #000;(水平阴影，垂直阴影，模糊距离，阴影颜色) 盒子阴影: box-shadow: 10px 10px 5px #999

- 边框 border-image: url(border.png);

- 背景

- 文字

- 渐变

- Filter（滤镜）

- 弹性布局、栅格布局、多列布局

- 媒体查询

### position 属性的值有哪些及其区别

**固定定位 fixed**： 元素的位置相对于浏览器窗口是固定位置，即使窗口是滚动的它也不会移动。Fixed 定 位使元素的位置与文档流无关，因此不占据空间。 Fixed 定位的元素和其他元素重叠。

**相对定位 relative**： 如果对一个元素进行相对定位，它将出现在它所在的位置上。然后，可以通过设置垂直 或水平位置，让这个元素“相对于”它的起点进行移动。 在使用相对定位时，无论是 否进行移动，元素仍然占据原来的空间。因此，移动元素会导致它覆盖其它框。

**绝对定位 absolute**： 绝对定位的元素的位置相对于最近的已定位父元素，如果元素没有已定位的父元素，那 么它的位置相对于。absolute 定位使元素的位置与文档流无关，因此不占据空间。 absolute 定位的元素和其他元素重叠。

**粘性定位 sticky**： 元素先按照普通文档流定位，然后相对于该元素在流中的 flow root（BFC）和 containing block（最近的块级祖先元素）定位。而后，元素定位表现为在跨越特定阈值前为相对定 位，之后为固定定位。

**默认定位 Static**： 默认值。没有定位，元素出现在正常的流中（忽略 top, bottom, left, right 或者 z-index 声 明）。 inherit: 规定应该从父元素继承 position 属性的值。

### box-sizing属性

box-sizing 规定两个并排的带边框的框，语法为 box-sizing：content-box/border-box/inherit

**content-box**：宽度和高度分别应用到元素的内容框，在宽度和高度之外绘制元素的内边距和边框。【标准盒子模型】

**border-box**：为元素设定的宽度和高度决定了元素的边框盒。【IE 盒子模型】

**inherit**：继承父元素的 box-sizing 值。

### CSS 盒子模型

CSS 盒模型本质上是一个盒子，它包括：边距，边框，填充和实际内容。CSS 中的盒子模型包括 IE 盒子模型和标准的 W3C 盒子模型。\
在标准的盒子模型中，`width 指 content 部分的宽度`。\
在 IE 盒子模型中，`width 表示 content+padding+border 这三个部分的宽度`。

故在计算盒子的宽度时存在差异：

**标准盒模型：** 一个块的总宽度 = width+margin(左右)+padding(左右)+border(左右)

**怪异盒模型：** 一个块的总宽度 = width+margin（左右）（既 width 已经包含了 padding 和 border 值）

### BFC（块级格式上下文）

**BFC的概念**

`BFC` 是 `Block Formatting Context `的缩写，即块级格式化上下文。`BFC`是CSS布局的一个概念，是一个独立的渲染区域，规定了内部box如何布局， 并且这个区域的子元素不会影响到外面的元素，其中比较重要的布局规则有内部 box 垂直放置，计算 BFC 的高度的时候，浮动元素也参与计算。

**BFC的原理布局规则**

- 内部的Box会在`垂直方向`，一个接一个地放置

- Box`垂直方向的距离由margin决定`。属于同一个BFC的两个相邻Box的margin会发生重叠

- 每个元素的margin box的左边， 与包含块border box的左边相接触(对于从左往右的格式化，否则相反

- BFC的区域`不会与float box重叠`

- BFC是一个独立容器，容器里面的`子元素不会影响到外面的元素`

- 计算BFC的高度时，`浮动元素也参与计算高度`

- 元素的类型和`display属性，决定了这个Box的类型`。不同类型的Box会参与不同的`Formatting Context`。

**如何创建BFC？**

- 根元素，即HTML元素

- float的值不为none

- position为absolute或fixed

- display的值为inline-block、table-cell、table-caption

- overflow的值不为visible

**BFC的使用场景**

- 去除边距重叠现象

- 清除浮动（让父元素的高度包含子浮动元素）

- 避免某元素被浮动元素覆盖

- 避免多列布局由于宽度计算四舍五入而自动换行

### 让一个元素水平垂直居中

