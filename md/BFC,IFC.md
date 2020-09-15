# BFC,IFC

## Box

[Box Model](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Box_Model)
[display](https://developer.mozilla.org/zh-CN/docs/Web/CSS/display)

`Box` 是 `CSS` 布局的对象和基本单位。元素的类型和 `display` 属性，决定了这个 `Box` 的类型。 不同类型的 `Box`，会参与不同的 `Formatting Context`（一个决定如何渲染文档的容器），因此`Box`内的元素会以不同的方式渲染。

`block-level box`:`display` 属性为 `block`, `list-item`, `table` 的元素，会生成 `block-level box`。并且参与 `block fomatting context`
`inline-level box`:`display` 属性为 `inline`, `inline-block`, `inline-table` 的元素，会生成 `inline-level box`。并且参与 `inline formatting context`
`run-in box`: `css3` 中才有，`display`:`run-in`。

## visual formatting model（视觉格式化模型）

[visual formatting model](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Visual_formatting_model)

CSS 视觉格式化模型（visual formatting model）是用来处理和在视觉媒体上显示文档时使用的计算规则。该模型是 CSS 的基础概念之一。

视觉格式化模型会根据CSS盒子模型将文档中的元素转换为一个个盒子，每个盒子的布局由以下因素决定：

* 盒子的尺寸：精确指定、由约束条件指定或没有指定
* 盒子的类型：行内盒子（inline）、行内级盒子（inline-level）、原子行内级盒子（atomic inline-level）、块盒子（block）
* 定位方案（positioning scheme）：普通流定位、浮动定位或绝对定位
* 文档树中的其它元素：即当前盒子的子元素或兄弟元素
* 视口尺寸与位置
* 所包含的图片的尺寸
* 其他的某些外部因素
该模型会根据盒子的包含块（containing block）的边界来渲染盒子。通常，盒子会创建一个包含其后代元素的包含块，但是盒子并不由包含块所限制，当盒子的布局跑到包含块的外面时称为溢出（overflow）。
盒子的生成是 CSS 视觉格式化模型的一部分，用于从文档元素生成盒子。盒子有不同的类型，不同类型的盒子的格式化方法也有所不同。盒子的类型取决于 CSS display 属性。

### 块级元素与块盒子

当元素的 display 为 block、list-item 或 table 时，该元素将成为块级元素。一个块级元素会被格式化成一个块（例如文章的一个段落），默认按照垂直方向依次排列。

每个块级盒子都会参与块格式化上下文（block formatting context）的创建，而每个块级元素都会至少生成一个块级盒子，即主块级盒子（principal block-level box）。有一些元素，比如列表项会生成额外的盒子来放置项目符号，而那些会生成列表项的元素可能会生成更多的盒子。不过，多数元素只生成一个主块级盒子。 

### 行内级元素和行内盒子

如果一个元素的 display 属性为 inline、inline-block 或 inline-table，则称该元素为行内级元素。显示时，它不会生成内容块，但是可以与其他行内级内容一起显示为多行。一个典型的例子是包含多种格式内容（如强调文本、图片等）的段落，就可以由行内级元素组成。

行内级元素会生成行内级盒子，该盒子同时会参与行内格式化上下文（inline formatting context）的创建。行内盒子既是行内级盒子，也是一个其内容会参与创建其容器的行内格式化上下文的盒子，比如所有具有 display:inline 样式的非替换盒子。如果一个行内级盒子的内容不参与行内格式化上下文的创建，则称其为原子行内级盒子。而通过替换行内级元素或 display 值为 inline-block 或 inline-table 的元素创建的盒子不会像行内盒子一样可以被拆分为多个盒子。

### 其他类型的盒子

* 行盒子
行盒子由行内格式化上下文创建，用来显示一行文本。在块盒子内部，行盒子总是从块盒子的一边延伸到另一边（译注：即占据整个块盒子的宽度）。当有浮动元素时，行盒子会从向左浮动的元素的右边缘延伸到向右浮动的元素的左边缘。

行盒子更多是以技术性目的而存在的，Web开发者通常不需要关心。
* Run-in 盒子
Run-in 盒子通过 display:run-in 来定义，它可以是块盒子，也可以是行内盒子，这取决于紧随其后的盒子的类型。Run-in 盒子可以用来在可能的情况下将标题嵌入文章的第一个段落中。
 
注意：Run-in 盒子已经在CSS 2.1的标准中移除了，但可能会在CSS 3中作为一个实验性的内容再次加入。因此最好不要将其用于正式项目。

* 由其他模型引入的盒子
除了行内格式化上下文和块格式化上下文之外，CSS还定义了几种内容模型，这些模型同样可以应用于元素。这些模型一般用来描述布局，它们可能会定义一些额外的盒子类型：
 
1. 表格内容模型可能会创建一个表格包装器盒子和一个表格盒子，以及多个其他盒子如表格标题盒子等
2. 多列内容模型可能会在容器盒子和内容之间创建多个列盒子
3. 实验性的网格内容模型或flex-box内容模型同样会创建一些其他种类的盒子

## Formatting context

[Formatting context](https://wiki.developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flow_Layout/Intro_to_formatting_contexts)

`Formatting context` 是 `W3C CSS2.1` 规范中的一个概念。它是页面中的一块渲染区域，并且有一套渲染规则，它决定了其子元素将如何定位，以及和其他元素的关系和相互作用。最常见的 `Formatting context` 有 `Block fomatting context` (简称`BFC`)和 `Inline formatting context` (简称`IFC`)。
`CSS2.1` 中只有 `BFC` 和 `IFC`, `CSS3` 中还增加了 `GFC` 和 `FFC`。

### Block formatting context(BFC)

[Block formatting context](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Block_formatting_context)

块格式化上下文（Block Formatting Context，BFC） 是Web页面的可视CSS渲染的一部分，是块盒子的布局过程发生的区域，也是浮动元素与其他元素交互的区域。

#### 创建块格式化上下文：

* 根元素（<html>）
* 浮动元素（元素的 float 不是 none）
* 绝对定位元素（元素的 position 为 absolute 或 fixed）
* 行内块元素（元素的 display 为 inline-block）
* 表格单元格（元素的 display 为 table-cell，HTML表格单元格默认为该值）
* 表格标题（元素的 display 为 table-caption，HTML表格标题默认为该值）
* 匿名表格单元格元素（元素的 display 为 table、table-row、 table-row-group、table-header-group、table-footer-group（分别是HTML table、row、tbody、thead、tfoot 的默认属性）或 inline-table）
* overflow 值不为 visible 的块元素
* display 值为 flow-root 的元素
* contain 值为 layout、content 或 paint 的元素
* 弹性元素（display 为 flex 或 inline-flex 元素的直接子元素）
* 网格元素（display 为 grid 或 inline-grid 元素的直接子元素）
* 多列容器（元素的 column-count 或 column-width 不为 auto，包括 column-count 为 1）
* column-span 为 all 的元素始终会创建一个新的BFC，即使该元素没有包裹在一个多列容器中（标准变更，Chrome bug）。

#### BFC的约束规则

* 内部的Box会在垂直方向上一个接一个的放置
*  同一个 BFC 下外边距会发生折叠(如果想要避免外边距的重叠，可以将其放在不同的 BFC 容器中)
* 垂直方向的距离有margin决定(属于同一个BFC的两个相邻Box的margin会发生重叠，与方向无关)
* 每个元素的margin box的左边， 与包含块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此
* BFC的区域不会与float的元素区域重叠(元素有部分被浮动元素所覆盖时，(但是文本信息不会被浮动元素所覆盖) 如果想避免元素被覆盖，可触元素的 BFC 特性)
* 计算BFC的高度时，浮动子元素也参与计算（清除浮动）
* BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面元素，反之亦然

块格式化上下文包含创建它的元素内部的所有内容.

块格式化上下文对浮动定位（参见 float）与清除浮动（参见 clear）都很重要。浮动定位和清除浮动时只会应用于同一个BFC内的元素。浮动不会影响其它BFC中元素的布局，而清除浮动只能清除同一BFC中在它前面的元素的浮动。外边距折叠（Margin collapsing）也只会发生在属于同一BFC的块级元素之间。

### Inline formatting context(IFC)

内联格式上下(Inline formatting context,IFC)文存在于其他格式上下文中，可以将其视为段落的上下文。段落创建了一个内联格式上下文，其中在文本中使用诸如<strong>、<a>或<span>元素等内容。