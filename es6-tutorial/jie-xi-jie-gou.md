## 解析结构

解析结构是一种全新的写法，我们只需要使用一个例子，大家就能够明白解析结构到底是怎么一回事儿。

```
// 首先有这么一个对象
const props = {
    className: 'tiger-button',
    loading: false,
    clicked: true,
    disabled: 'disabled'
}
```

当我们想要取得其中的2个值：loading与clicked时：

```
// es5
var loading = props.loading;
var clicked = props.clicked;

// es6
const { loading, clicked } = props;

// 给一个默认值，当props对象中找不到loading时，loading就等于该默认值
const { loading = false, clicked } = props;
```

是不是简单了许多？正是由于解析结构大大减少了代码量，因此它大受欢迎，在很多代码中它的影子随处可见。

```
// 比如
// section1 
import React, { Component } from 'react';

// section2
export { default } from './Button';

// section3
const { click, loading } = this.props;
const { isCheck } = this.state;

// more  任何获取对象属性值的场景都可以使用解析结构来减少我们的代码量
```

另外，数组也有属于自己的解析结构。

```
// es6
const arr = [1, 2, 3];
const [a, b, c] = arr;

// es5
var arr = [1, 2, 3];
var a = arr[0];
var b = arr[1];
var c = arr[2];
```

数组以序列号一一对应，这是一个有序的对应关系。  
而对象根据属性名一一对应，这是一个无序的对应关系。  
根据这个特性，使用解析结构从对象中获取属性值更加具有可用性。



