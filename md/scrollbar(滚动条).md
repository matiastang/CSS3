<!--
 * @Descripttion: 
 * @version: 
 * @Author: matias tang
 * @Date: 2020-09-24 16:49:59
 * @LastEditors: matias tang
 * @LastEditTime: 2020-09-24 16:51:08
-->
# scrollbar(滚动条)

[参考一](https://blog.csdn.net/github_36487770/article/details/78750589)
[参考二](https://www.cnblogs.com/ranyonsue/p/9487599.html)

```css
.activity-result-info-div::-webkit-scrollbar {
    /* 1 滚动条整体部分，其中的属性有width,height,background,border（就和一个块级元素一样）等。 */
    width: 10px;     /*高宽分别对应横竖滚动条的尺寸*/
    height: 1px;
}   
.activity-result-info-div::-webkit-scrollbar-button {
    /* 2 滚动条两端的按钮。可以用display:none让其不显示，也可以添加背景图片，颜色改变显示效果。 */

}
.activity-result-info-div::-webkit-scrollbar-track{
    /* 3  外层轨道。可以用display:none让其不显示，也可以添加背景图片，颜色改变显示效果。 */
    /* box-shadow: inset 0 0 5px rgba(0,0,0,0.2); */
    border-radius: 10px;
    background: rgba(237,237,237,1);
}
.activity-result-info-div::-webkit-scrollbar-track-piece {
    /* 4  内层轨道，滚动条中间部分（除去）。 */
}
.activity-result-info-div::-webkit-scrollbar-thumb {
    /* 5  滚动条里面可以拖动的那部分 */
    border-radius: 10px;
    box-shadow: inset 0 0 5px rgba(252,180,4,1);
    background: rgba(252,180,4,1);
}
.activity-result-info-div::-webkit-scrollbar-corner {
    /* 6  边角 */
}
.activity-result-info-div::-webkit-resizer {
    /* 7   定义右下角拖动块的样式 */
}
```