
说明： Html 元素分为行级元素（label,span）和块级元素（div）

## display：block (块级元素表示)

特点：  
1. block元素会独占一行，多个block元素会各自新起一行。默认情况下，block元素宽度自动填满其父元素宽度。
2. block元素可以设置width,height属性。块级元素即使设置了宽度,仍然是独占一行。
3. block元素可以设置margin和padding属性。

## display:inline （行级元素表示）

特点：  
1. inline元素不会独占一行，多个相邻的行内元素会排列在同一行里，直到一行排列不下，才会新换一行，其宽度随元素的内容而变化。
2. inline元素设置width,height属性无效。
3. inline元素的margin和padding属性，水平方向的padding-left, padding-right, margin-left, margin-right都产生边距效果；但竖直方向的padding-top, padding-bottom, margin-top, margin-bottom不会产生边距效果。 

## display:inline-block 

特点：
1. 行级元素表示，但是可以设置 width，height

## display:none

说明：
1. 不显示，