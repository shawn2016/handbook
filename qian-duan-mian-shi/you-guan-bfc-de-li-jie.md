### BFC的理解

BFC用来格式化块级盒子

BFC: 提供一个环境，html元素会在这个环境中按照一定的规则进行布局。

ex: 例如浮动元素会形成bfc,浮动元素内部子元素主要受该浮动元素影响，但是两个浮动元素互相不影响。

这个可以理解为一个独立容器，里边规则不会影响到外边。

那么什么情况下会生成bfc呢：

1、浮动元素，float除none以外的值

2、绝对定位，position\(absolite,fixed\)

3、dispaly = inline-blocks\|table-cells\|table-captions

4、overflow除visible以外的值

作用：

1、可以阻止元素被浮动元素覆盖

2、包含浮动元素

3、如果属于同一个bfc的两个元素上下margin会发生重叠，但如果两个元素属于两个不同的bfc那么margin就不会发生重叠

