## 新的变量声明方式 let/const

与var不同，新的变量声明方式带来了一些不一样的特性，其中最重要的两个特性就是提供了块级作用域与不再具备变量提升。

通过2个简单的例子来说明这两点。

```
{
    let a = 20;
}

console.log(a);  // a is not defined
```

而这个简单的例子，会被编译为：

```
{
    let _a = 20;
}

console.log(a);  // a is not defined
// ES5
console.log(a);   // undefined
var a = 20;

// ES6
console.log(a); // a is not defined
let a = 20;
```



![](https://upload-images.jianshu.io/upload_images/599584-0bb3aa3c263aebf0.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

  


变量提升demo示例

当然，你的代码编译成为了ES5之后，仍然会存在变量提升，因此这一点只需要我们记住即可。在实际使用中，也需要尽量避免使用变量提升的特性带来的负面影响。只有在面试题中，才会对变量提升不停的滥用。

使用ES6，我们需要全面使用let/const替换var，那么什么时候用let，什么时候用const就成为了一个大家要熟练区分的一个知识点。

我们常常使用let来声明一个值会被改变的变量，而使用const来声明一个值不会被改变的变量，也可以称之为常量。

当值为基础数据类型时，那么这里的值，就是指值本身。  
而当值对应的为引用数据类型时，那么我这里说的值，则表示指向该对象的引用。这里需要注意，正因为该值为一个引用，只需要保证引用不变就可以，我们仍然可以改变该引用所指向的对象。

当我们试图改变const声明的变量时，则会报错。

写几个例子，大家可以仔细揣摩一下：

```
let a = null;
a = 20;
const obDev = {
    a: 20,
    b: 30
}

obDev.a = 30;

console.log(obDev); // Object {a: 30, b: 30}
const fn = function() {}
const a = obDev.a;
... ...
```

只要抓住上面我说的特性，那么在使用let/const时就会显得游刃有余。  
根据我自己的经验，使用const的场景要比使用let的场景多很多。

