## exports 和 module.exports 的区别

`Node`里面的模块系统遵循的是`CommonJS`规范。

那问题又来了，什么是`CommonJS`规范呢？
由于`js`以前比较混乱，各写各的代码，没有一个模块的概念，而这个规范出来其实就是对模块的一个定义。

##### `CommonJS`定义的模块分为: 模块标识(`module`)、模块定义(`exports`) 、模块引用(`require`)

先解释 `exports` 和 `module.exports`
在一个node执行一个文件时，会给这个文件内生成一个 `exports`和`module`对象，
而`module`又有一个`exports`属性。他们之间的关系如下图，都指向一块{}内存区域。

```
exports = module.exports = {};
```

那下面我们来看看代码的吧。

```
//utils.js
let a = 100;

console.log(module.exports); //能打印出结果为：{}
console.log(exports); //能打印出结果为：{}

exports.a = 200; //这里辛苦劳作帮 module.exports 的内容给改成 {a : 200}

exports = '指向其他内存区'; //这里把exports的指向指走

//test.js

var a = require('/utils');
console.log(a) // 打印为 {a : 200} 
```

> 从上面可以看出，其实`require`导出的内容是`module.exports`的指向的内存块内容，并不是`exports`的。
> 简而言之，区分他们之间的区别就是 `exports` 只是 `module.exports`的引用，辅助后者添加内容用的。

用白话讲就是，`exports`只辅助`module.exports`操作内存中的数据，辛辛苦苦各种操作数据完，累得要死，结果到最后真正被`require`出去的内容还是`module.exports`的，真是好苦逼啊。

其实大家用内存块的概念去理解，就会很清楚了。

然后呢，为了避免糊涂，尽量都用 `module.exports` 导出，然后用`require`导入。

明白了上述例子后，我们只需知道三点就知道 exports 和 module.exports 的区别了：

1. module.exports 初始值为一个空对象 {}
2. exports 是指向的 module.exports 的引用
3. require\(\) 返回的是 module.exports 而不是 exports



