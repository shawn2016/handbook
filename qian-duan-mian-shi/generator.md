#### generator



generator（生成器）是ES6标准引入的新的数据类型。一个generator看上去像一个函数，但可以返回多次。

```
function* foo(x) {
    yield x + 1;
    yield x + 2;
    return x + 3;
}
```

Generator 函数是一个普通函数，但是有两个特征:

一是，function关键字与函数名之间有一个星号；

二是，函数体内部使用yield语句，定义不同的内部状态



Generator函数的调用方法与普通函数一样，也是在函数名后面加上一对圆括号。不同的是，调用Generator函数后，该函数并不执行，返回的也不是函数运行结果，而是一个指向内部状态的指针对象，我们可以通过调用 next 方法，使得指针移向下一个状态



作用很多啊.

迭代器 iterator, infinite range, 可以暂停函数, lazy evaluation, 用来实现 async/await 啊, 棒棒哒.

async generator/iterator 更是秒.