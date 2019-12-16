# BFC浅析

## BFC 是什么？

首先，BFC（block formatting context），中文直译：块格式化上下文。BFC的概念，无论是在W3C CSS2.1[官方文档](https://link.jianshu.com?t=https://www.w3.org/TR/CSS21/visuren.html#block-formatting)，还是在[MDN文档](https://link.jianshu.com?t=https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Block_formatting_context)中，都是十分难读懂的。再翻阅了大量博客后，首先必须了解，[视觉格式化模型](https://link.jianshu.com?t=https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Visual_formatting_model)这个概念：

> CSS 视觉格式化模型(*visual formatting model)*是用来处理文档并将它显示在视觉媒体上的机制。这是 CSS 的一个基础概念。 视觉格式化模型根据 CSS 盒模型为文档的每个元素生成 0，1 或多个盒。
>
> - 盒尺寸：明确指定，受限或没有指定
> - 盒类型：行内(inline), 行内级别(inline-level), 原子行内级别(atomic inline-level), 块(block)盒；
> -  [定位方案(positioning scheme)](https://link.jianshu.com?t=https://developer.mozilla.org/en-US/docs/CSS/Box_positioning_scheme): 常规流，浮动或绝对定位；
> - 树中的其它元素: 它的子代与同代；
> -  [视口(viewport)](https://link.jianshu.com?t=https://developer.mozilla.org/en-US/docs/CSS/viewport) 尺寸与位置；
> - 内含图片的固定尺寸；
> - 其它信息。
>
> CSS 视觉格式化模型的一部分工作是从文档元素生成盒。生成的盒拥有不同类型，并对视觉格式化模型的处理产生影响。生成盒的类型取决于 CSS 属性 [`display`](https://link.jianshu.com?t=https://developer.mozilla.org/zh-CN/docs/Web/CSS/display) 。
>
> —— [MDN - 视觉格式化模型](https://link.jianshu.com?t=https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Visual_formatting_model)

对于这个概念，可以简单理解为，页面文档在浏览器（视觉媒体）上的显示，是通过一定的模型构建的，就如同我们在word中写文章时，可以进行排版一样，这些模型就是帮助我们在浏览器中构建网页内容的排版。那么页面中的元素，就会根据这些模型生成一个个的盒子，这就是我们页面中的最基本的单位。

### BFC基本描述

> **块格式化上下文（block formatting context）** 是Web页面的可视CSS渲染的一部分。它是块盒子的布局发生及浮动体彼此交互的区域。
>
> ——[MDN - 块格式化上下文](https://link.jianshu.com?t=https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Block_formatting_context)

再看到MDN对于BFC的描述，可以理解为页面中的块盒（block boxes）所使用的的渲染模型就是BFC，当元素满足一定条件时，我们称之为触发了BFC，使其满足这个渲染模型的规范。

那么问题来了，什么是块盒（block boxes）？

### 块盒（block boxes）

> #### 块级元素与块盒(Block-level elements and block boxes)
>
> 当元素的 CSS 属性  [`display`](https://link.jianshu.com?t=https://developer.mozilla.org/zh-CN/docs/Web/CSS/display) 为 `block`, `list-item` 或 `table 时，它是块级元素` *block-level* 。块级元素（比如<p>)视觉上呈现为块，竖直排列。
>
> **块级盒**参与([块格式化上下文 block formatting context](https://link.jianshu.com?t=https://developer.mozilla.org/en-US/docs/CSS/block_formatting_context))。每个块级元素至少生成一个块级盒，称为主要块级盒(*principal block-level box*)。一些元素，比如<li>，生成额外的盒来放置项目符号，不过多数元素只生成一个主要块级盒。
>
> 主要块级盒将包含后代元素生成的盒以及生成的内容。它也是可以使用([定位方案 positioning scheme](https://link.jianshu.com?t=https://developer.mozilla.org/en-US/docs/CSS/Positioning_scheme))的盒。
>
> ![venn_blocks](E:\笔记\images\venn_blocks.png)
>
> 一个块级盒可能也是一个块容器盒。块容器盒(*block container box)* 只包含其它块级盒，或生成一个行内[格式化上下文(inline formatting context)](https://link.jianshu.com?t=https://developer.mozilla.org/en-US/docs/CSS/Inline_formatting_context)，由此只包含行内盒。注意块级盒与块容器盒概念不同。 前者描述元素跟它的父元素与兄弟元素之间的表现，后者描述元素跟它的后代之间的影响。有些块级盒，比如表格，不是块容器盒。相反，一些块容器盒，比如非替换行内块及非替换表格单元格，不是块级盒。
>
> 同时是块容器盒的块级盒称为块盒(*block boxes)。（*译注：块级盒与块盒名字相近，注意分别-）
>
> —— [MDN - 视觉格式化模型](https://link.jianshu.com?t=https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Visual_formatting_model)

根据MDN文档，这里我整理了关于盒子的三个概念：

1. Block-level boxes

   > **块级盒（Block-level boxes）**指由块级元素构成的盒子，每个块级元素至少会生成一个盒子，我们称其为主块级盒子。块级盒描述块级元素跟它的父元素和兄弟元素的表现。

2. Block containing boxes

   > **块容器盒（Block containing boxes）**指只包含其他块级盒的盒子，或指生成行内格式化上下文（inline fomatting context）的盒子，由此生成的盒子只包含行内盒（inline boxes）。其描述了元素与后代之间的影响。

3. Block boxes

   > **块盒（Block boxes）**指既是块级盒，又是块容器盒的盒子。

总的来看，块盒属于一个复杂概念的集合，当一个盒子既包含块级盒又包含块级容器的概念时，它就是一个块盒。其中，包含了块级元素与父亲、兄弟、子代关系的描述和影响，还涉及了其他视觉格式化的内容。因此，BFC可以说是一种CSS 渲染的表现形式。

对于BFC，我们还需要了解其特性及触发条件：

### BFC特性&创建条件

特性：

> 1. 内部的Box会在垂直方向，从顶部开始一个接一个地放置。
> 2. Box垂直方向的距离由margin决定。属于同一个BFC的两个相邻Box的margin会发生叠加
> 3. 每个元素的margin box的左边，与包含块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此。
> 4. BFC的区域不会与float box叠加。
> 5. BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素，反之亦然。
> 6. 计算BFC的高度时，浮动元素也参与计算。
>
> ——《[CSS之BFC详解](https://link.jianshu.com?t=http://www.html-js.com/article/1866) 》

创建条件：

> 块格式化上下文由以下之一创建：
>
> - 根元素或其它包含它的元素
> - 浮动 (元素的 [`float`](https://link.jianshu.com?t=https://developer.mozilla.org/zh-CN/docs/Web/CSS/float) 不是 `none`)
> - 绝对定位的元素 (元素具有 [`position`](https://link.jianshu.com?t=https://developer.mozilla.org/zh-CN/docs/Web/CSS/position) 为 `absolute` 或 `fixed`)
> - 内联块 inline-blocks (元素具有 [`display`](https://link.jianshu.com?t=https://developer.mozilla.org/zh-CN/docs/Web/CSS/display)`: inline-block`)
> - 表格单元格 (元素具有 [`display`](https://link.jianshu.com?t=https://developer.mozilla.org/zh-CN/docs/Web/CSS/display)`: table-cell，HTML表格单元格默认属性`)
> - 表格标题 (元素具有 [`display`](https://link.jianshu.com?t=https://developer.mozilla.org/zh-CN/docs/Web/CSS/display)`: table-caption`, HTML表格标题默认属性)
> - 块元素具有[`overflow`](https://link.jianshu.com?t=https://developer.mozilla.org/zh-CN/docs/Web/CSS/overflow) ，且值不是 `visible` 
> -  [`display`](https://link.jianshu.com?t=https://developer.mozilla.org/zh-CN/docs/Web/CSS/display):`flow-root` 
>
> ——[MDN - 块格式化上下文](https://link.jianshu.com?t=https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Block_formatting_context)

## BFC 可以用来做什么？

#### 1. 解决margin重叠的问题

根据BFC的特性，同一个BFC下的两个相邻的盒子会出现垂直margin重叠的问题，这个问题会影响我们对页面布局的控制，通常我们可以为其中一个盒子添加一个父元素，并使其触发BFC，即可解决这个问题：

![4655331-e826e7f44840bc9b](E:\笔记\images\4655331-e826e7f44840bc9b.webp)



margin重叠

### 2. 浮动带来的布局问题

根据前面其他作者总结的BFC特性的第三条和第四条，我们知道在同一个BFC下即使有元素浮动，BFC下元素的最左边边缘总是会与包含它的盒子左边相接触，那么就会出现浮动元素遮盖了其他元素的情况。BFC还有一条重要特性：BFC的区域不会与float box 重叠。试想，在一个BFC，如果存在一个float元素，和一个div，浮动元素会遮盖住div，此时，如果给这个div构建一个新的BFC，由于BFC特性，内外不相互影响，此时div会被float元素挤开。

比如下面这个例子，绿色盒子会因为浮动遮盖住红色的盒子，但由于两个盒子都在同一个BFC（body元素）下，根据BFC特性，红色盒子会与包含块相接，此时只要让红色盒子触发BFC，我们为红色盒子添加一个触发BFC的条件overflow:hidden，此时红色盒子由于BFC的特性隔离开绿色，这样我们就可以通过float元素的方式实现两栏布局。

![4655331-0bd6c330da5d0fa7](E:\笔记\images\4655331-0bd6c330da5d0fa7.webp)

布局问题

### 3. 清除浮动

这里就要说到我们常见的浮动元素引起的高度坍塌的问题。由于浮动特性，浮动元素会脱离父元素，我们是否可以通过触发BFC来解决高度坍塌的问题呢？

根据特性的第6条，在触发BFC后，这个盒子的高度将包含浮动元素的高度，在计算时，浮动元素会参与高度计算，我们可以理解为，当一个父元素中包含了浮动元素，而浮动元素超出了父元素，此时我们为父元素创建BFC，那么浮动元素就会包裹进这个BFC解决了父元素中高度塌陷的问题。

如下面的例子，`div.parent`包含了两个`div.child`，而两个div由于赋予了`float:left`使其浮动，导致了`div.parent`高度的坍塌，此时我们给`div.parent`添加一个`overflow:hidden`属性值，使`div.parent`触发BFC，由于BFC下的盒子会包含浮动元素的高度，因此盒子就被撑了起来，高度塌陷的问题也就得到了解决。

![4655331-c23159f5bbe3408f](E:\笔记\images\4655331-c23159f5bbe3408f.webp)



清除浮动

除了上面的清除浮动用到了BFC的一些特性外，还有一些其他的清除浮动的技巧，这里就不再做深入讨论。

## 其他

在学习BFC过程中，主要借鉴了一些博客文章及MDN的说明，由于自己的书面表达能力有限，这篇文章主要用于记录学习BFC的过程，如有表述不清的地方还请见谅。

此外，为了补充疏漏的地方，增加W3C官方文档的阅读。不过官方文档中BFC及相关概念大多为描述，没有非常确切的定性，所以这里只放出来作为参考。由于自己的英语水平有限，如有描述不当的地方，请以W3C CSS官方文档为准。

### BFC(block formatting context)的官方描述

我们来看看W3C  CSS2.1文档中关于[BFC](https://link.jianshu.com?t=https://www.w3.org/TR/CSS21/visuren.html#block-formatting)是怎么说的：

> Floats, absolutely positioned elements, block containers (such as inline-blocks, table-cells, and table-captions) that are not block boxes, and block boxes with 'overflow' other than 'visible' (except when that value has been propagated to the viewport) establish new block formatting contexts for their contents.
>
> In a block formatting context, boxes are laid out one after the other, vertically, beginning at the top of a containing block. The vertical distance between two sibling boxes is determined by the ['margin'](https://link.jianshu.com?t=https://www.w3.org/TR/CSS21/box.html#propdef-margin) properties. Vertical margins between adjacent block-level boxes in a block formatting context [collapse](https://link.jianshu.com?t=https://www.w3.org/TR/CSS21/box.html#collapsing-margins).
>
> In a block formatting context, each box's left outer edge touches the left edge of the containing block (for right-to-left formatting, right edges touch). This is true even in the presence of floats (although a box's *line boxes* may shrink due to the floats), unless the box establishes a new block formatting context (in which case the box itself [*may* become narrower](https://link.jianshu.com?t=https://www.w3.org/TR/CSS21/visuren.html#bfc-next-to-float) due to the floats).

简单的人肉+谷歌翻译：

> 浮动元素、绝对定位元素、块容器（比如 inline-blocks,table-cells,table-captions）及`overflow`值不为`visable`（除非该值已被传到视口）的块盒（block boxes），都会为其内容建立新的块格式化上下文（BFC）。
>
> 在一个BFC中，盒子将会垂直的从包含块(containing block)的顶部一个接一个的向下布置，兄弟元素之间的垂直距离将由`margin`属性确定。在BFC中，两个相邻的块级盒子（block-level boxes）之间的垂直边距（vertical margins）将会坍塌。
>
> 在一个BFC中，每个盒子的左外边缘会接触包容块的左边缘（对于从右往左的格式，则相反）。即便是在浮动`floats`情况下也是如此（尽管盒子的线框可能由于浮动而收缩），除非盒子建立了一个新的BFC（这种情况下，盒子自身可能会因为浮动变得更窄）。

### 格式化上下文（formatting context）

[CSS 2.1 - 9.4 Normal flow](https://link.jianshu.com?t=https://www.w3.org/TR/CSS21/visuren.html#normal-flow)

> Boxes in the normal flow belong to a [formatting context](https://link.jianshu.com?t=undefined), which may be block or inline, but not both simultaneously.
>
> [Block-level](https://link.jianshu.com?t=https://www.w3.org/TR/CSS21/visuren.html#block-level) boxes participate in a [block formatting](https://link.jianshu.com?t=https://www.w3.org/TR/CSS21/visuren.html#block-formatting) context. [Inline-level boxes](https://link.jianshu.com?t=https://www.w3.org/TR/CSS21/visuren.html#inline-level) participate in an [inline formatting](https://link.jianshu.com?t=https://www.w3.org/TR/CSS21/visuren.html#inline-formatting) context.

简单的人肉+谷歌翻译：

> 正常流中属于格式化上下文的盒子，可以是块或者内联，但不能同时存在。块级盒参与块级格式化上下文，行内级参与行级格式上下文。

### 包含块(containing block)

[CSS 2.1](https://link.jianshu.com?t=https://www.w3.org/TR/CSS2/visuren.html#containing-block) W3C 文档：

> In CSS 2.1, many box positions and sizes are calculated with respect to the edges of a rectangular box called a containing block. In general, generated boxes act as containing blocks for descendant boxes; we say that a box "establishes" the containing block for its descendants. The phrase "a box's containing block" means "the containing block in which the box lives," not the one it generates.
>
> Each box is given a position with respect to its containing block, but it is not confined by this containing block; it may [overflow](https://link.jianshu.com?t=https://www.w3.org/TR/CSS2/visufx.html#overflow).

简单的人肉+谷歌翻译：

> 在 CSS2.1中，许多盒子的定位（positions）和尺寸（size）被用来计算相对于矩形盒子的边缘，这种矩形盒子我们称其为包容块（containing block）。通常，生成的盒子将作为后代盒子的包含块，我们称其一个盒子为其后代**建立（establishes）**包容块。“一个盒子的包容块（a box's containning block）“指”这个盒子所在的包容块“，而不是指这个盒子产生的块。

### 块级盒子（block-level boxes）

> Block-level elements are those elements of the source document that are formatted visually as blocks (e.g., paragraphs). The following values of the ['display'](https://link.jianshu.com?t=https://www.w3.org/TR/CSS2/visuren.html#propdef-display) property make an element block-level: 'block', 'list-item', and 'table'.
>
> Block-level boxes are boxes that participate in a [block formatting context.](https://link.jianshu.com?t=https://www.w3.org/TR/CSS2/visuren.html#block-formatting) Each block-level element generates a [principal block-level box](https://link.jianshu.com?t=undefined) that contains descendant boxes and generated content and is also the box involved in any positioning scheme. Some block-level elements may generate additional boxes in addition to the principal box: 'list-item' elements. These additional boxes are placed with respect to the principal box.
>
> Except for table boxes, which are described in a later chapter, and replaced elements, a block-level box is also a block container box. A block container box either contains only block-level boxes or establishes an inline formatting context and thus contains only inline-level boxes. Not all block container boxes are block-level boxes: non-replaced inline blocks and non-replaced table cells are block containers but not block-level boxes. Block-level boxes that are also block containers are called block boxes.
>
> The three terms "block-level box," "block container box," and "block box" are sometimes abbreviated as "block" where unambiguous.

简单的人肉+谷歌翻译：

> 块级元素是源文档中作为块被视觉格式化的元素（比如：paragraphs）。`display`属性作为元素块级的表示，其值有`block`、`list-item`，`table`。
>
> 块级元素是参与BFC的盒子。每一个块级元素会生成一个主要块级元素盒（*principal block-level box*），盒中包含后代盒子和生成的内容，同时这个盒也包含任意定位方案。除了主块级元素盒外，一些块级元素也可能产生额外的盒子，比如：`list-item`元素。这些额外的盒子会被放置在相对主盒的地方。
>
> 除了后面章节描述的表格盒（table boxes）和替换元素外，块级元素盒（block-level box）同时也是一个块容器盒（block container box）。块容器盒要么只包块级盒，或建立内联格式化上下文（inline formatting）的情况下只包含内联级盒子（inline-level boxes）。并非所有块容器盒都是块级盒，不包含内联盒子和表单cell（table cell）的是块容器（block container），而不是块级盒（block-level boxes）。既是块级盒（block-level boxes）同时也是块容器（block container）的称为块盒（block boxes）。
>
> 块级盒（block-level block），块容器盒（block container box），块盒（block box）这三个术语有时会缩写为明确的：块（block）

参考：

1. [CSS之BFC详解](https://link.jianshu.com?t=http://www.html-js.com/article/1866)
2. [W3C CSS2.1 spec 9 Visual formatting model](https://link.jianshu.com?t=https://www.w3.org/TR/CSS21/visuren.html#block-formatting)
3. [扒一下W3C规范里的BFC和IFC](https://link.jianshu.com?t=https://segmentfault.com/a/1190000004246731)







文章来源网络,个人学习!