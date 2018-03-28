### css盒子模型

包含了content,padding,border,margin=

这些基本的比如比如哪儿是content大家都了解我就说了在设置width = 300px时代表的是content的宽度那么最终的宽度是content+padding+border+margin.

css外边距合并

刚才在bfc中提到，在一个bfc中，css外边距是会发生重叠的，解决方法就是放在两个bfc中。当我们使用盒模型的时候需要注意的是浏览器的兼容性，这个很好解决在html中声明 ，ul在mozilia默认有padding值，而在IE中只有margin有值

盒模型中我们常使用一个属性叫box-sizing,这会单独起一页，这也是面一经常出的问题

