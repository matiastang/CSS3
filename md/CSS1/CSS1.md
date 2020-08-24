# CSS1

## white-space

[MDN white-space](https://developer.mozilla.org/zh-CN/docs/Web/CSS/white-space)

`white-space`属性出自`CSS1`用于指定如何处理容器中的空白字符。适用于块状元素，具有继承性，支持`IE 5.5+、Chrome、FireFox、Safari、Opera`等所有主流浏览器，其默认值为`normal`。

```css
/* Schlüsselwortwerte */
white-space: normal;
white-space: nowrap;
white-space: pre;
white-space: pre-wrap;
white-space: pre-line;

/* Globale Werte */
white-space: inherit;
white-space: initial;
white-space: unset;
```

| 值 | 描述 |
| - | - |
| normal | 默认，空白会被浏览器忽略。|
| pre | 空白会被浏览器保留，其行为类似HTML中的`<pre>`标签。|
| nowrap | 文本不会换行，文本会在同一行上继续，知道遇到`<br>`标签为止。|
| pre-wrap | 保留空白符序列，但是正常的进行换行。|
| pre-line | 合并空白符序列，但是保留换行符。|
| break-spaces | 与 pre-wrap的行为相同，除了：1. 任何保留的空白序列总是占用空间，包括在行尾。2. 每个保留的空格字符后都存在换行机会，包括空格字符之间。3.这样保留的空间占用空间而不会挂起，从而影响盒子的固有尺寸（最小内容大小和最大内容大小）。 |
| inherit | 规定应该从父元素继承white-space属性的值。|

注：所有浏览器都支持`white-space`属性。任何的版本的 `Internet Explorer （包括 IE8）`都不支持属性值 `inherit`。

可以设置`p`和`per`标签`white-space: pre-wrap;`来显示文本中的自动的换行。

## word-wrap(使用overflow-wrap替换)

[MDN white-space](https://developer.mozilla.org/zh-CN/docs/Web/CSS/white-space)

`word-wrap`属性用于指示Web浏览器是否可以在单词内进行换行。如果原本不可分割的文本对于其中包含的框而言太长，则必须防止溢出。

注意：`word-wrap Microsoft` 的原始（无前缀）专有扩展名  已在`CSS3`文本规范的当前草案中重命名`overflow-wrap`。`word-wrap`现在被视为`overflow-wrap`的“备用名称” 。`Google Chrome`和`Opera`的稳定版本支持新语法。

```css
/* Keyword values */
word-wrap: normal;
word-wrap: break-word;

/* Global values */
word-wrap: inherit;
word-wrap: initial;
word-wrap: unset;
```
| 值 | 描述 |
| - | - |
| normal | 只允许在断字点换行（浏览器保持默认处理）。|
| break-word | 在长单词或URL地址内部进行换行。|