# CSS3

## overflow-wrap

[MDN overflow-wrap](https://developer.mozilla.org/zh-CN/docs/Web/CSS/word-wrap)

`overflow-wrap` 是用来说明当一个不能被分开的字符串太长而不能填充其包裹盒时，为防止其溢出，浏览器是否允许这样的单词中断换行。

```css
/* Keyword values */
overflow-wrap: normal;
overflow-wrap: break-word;

/* Global values */
overflow-wrap: inherit;
overflow-wrap: initial;
overflow-wrap: unset;
```
| 值 | 描述 |
| - | - |
| normal | 行只能在正常的单词断点处中断。（例如两个单词之间的空格）。|
| break-word | 表示如果行内没有多余的地方容纳该单词到结尾，则那些正常的不能被分割的单词会被强制分割换行。|