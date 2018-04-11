### 作业帮

1. 手写一个闭包

```
coding：

JavaScript 闭包好处是什么？为什么用到闭包？
一、变量的作用域
要理解闭包，首先必须理解Javascript特殊的变量作用域。
变量的作用域无非就是两种：全局变量和局部变量。
Javascript语言的特殊之处，就在于函数内部可以直接读取全局变量。

二、如何从外部读取局部变量？
出于种种原因，我们有时候需要得到函数内的局部变量。但是，前面已经说过了，正常情况下，这是办不到的，只有通过变通方法才能实现。
那就是在函数的内部，再定义一个函数。

三、闭包的概念
各种专业文献上的“闭包”（closure）定义非常抽象，很难看懂。我的理解是，闭包就是能够读取其他函数内部变量的函数。
由于在Javascript语言中，只有函数内部的子函数才能读取局部变量，因此可以把闭包简单理解成“定义在一个函数内部的函数”。
所以，在本质上，闭包就是将函数内部和函数外部连接起来的一座桥梁。

四、闭包的用途
闭包可以用在许多地方。它的最大用处有两个，一个是前面提到的可以读取函数内部的变量，另一个就是让这些变量的值始终保持在内存中。
```

1. 闭包的作用和缺点
2. vue中keep-alive
3. $.fn.extend与$.extend的区别
4. vue中a={data:{b:1}},b发生变化时watch可以监听到吗？怎么做才可以监听到。
5. 说一下常用的es6语法

```
1.变量声明const和let
2.模板字符串
3.函数
  函数默认参数
  箭头函数
4.拓展的对象功能
5.更方便的数据访问--解构
6.Spread Operator 展开运算符
7.import 和 export
8. Promise
9.Generators
```

1. 改变this的所有方法

```
call
apply
bind
箭头函数
```

1. var与let const的区别

```
使用var声明的变量，其作用域为该语句所在的函数内，且存在变量提升现象；
使用let声明的变量，其作用域为该语句所在的代码块内，不存在变量提升；
使用const声明的是常量，在后面出现的代码中不能再修改该常量的值。
```

1. 说一下原型和原型链，手写一个原型继承

```
JavaScript 原型，原型链 ? 有什么特点？
原型：
每个对象都会在其内部初始化一个属性，就是prototype(原型)。
原型链：
当我们访问一个对象的属性时，如果这个对象内部不存在这个属性，那么他就会去prototype里找这个属性，这个prototype又会有自己的prototype，于是就这样一直找下去，也就是我们平时所说的原型链的概念。
特点：
JavaScript对象是通过引用来传递的，我们创建的每个新对象实体中并没有一份属于自己的原型副本。当我们修改原型时，与之相关的对象也会继承这一改变。

  当我们需要一个属性的时，Javascript引擎会先看当前对象中是否有这个属性， 如果没有的话，就会查找他的Prototype对象是否有这个属性，如此递推下去，一直检索到 Object 内建对象。
```

```
var o = {};

function Person() {
    this.name = 'keefool';
    this.sayHello = function() {
        return 'Hello, I am ' + this.name;
    }
}
function Employee(email) {
    this.email = email;
}

Employee.prototype = new Person();
Employee.prototype.constructor = Employee;

var emp = new Employee('keepfool@xxx.com');
```

1. 平时用到了那些算法，说一下有哪些，并可以手写出来
2. vue中methods和computer的区别.
3. 怎么监听一个对象内部属性变化？
4. 这样很好性能，可以怎么优化？

```
http://www.jb51.net/article/120073.htm
watch和computed各自处理的数据关系场景不同
1.watch擅长处理的场景：一个数据影响多个数据
2.computed擅长处理的场景：一个数据受多个数据影响
```

1. 跨域常用有哪些，nginx用过吗？反向代理知道吗？
2. node使用过吗
3. bigpipe呢？
4. git、svn的区别
5. 说一下git add/git commit/git push的动作都干什么了？
6. 特殊要求，线上代码有问题，需要立马回滚，怎么做？
7. 一个文件需要输入和压缩或者编译后需要怎么做？（webpack）
8. plugins是干嘛的，有哪些常用的插件。
9. 怎么去掉字符串的重复项[https://blog.csdn.net/admin\_yi/article/details/54925440](https://blog.csdn.net/admin_yi/article/details/54925440) split+正则

```
var a="aaAAcRfR";
a = a.replace(/(.)(?=.*\1)/g,"")
alert(a)
```

1. 数组去重有哪些方法？
2. 手写出一个100个不重复随机有效的时间数组（20180401）
3. 网页怎么优化
4. react优化在那几个生命周期当中

```
React的优化是基于shouldComponentUpdate的，该生命周期默认返回true，所以一旦prop或state有任何变化，都会引起重新render。
```

1. foreach、map、fifter、reduce的用法和区别

```
forEach() 方法对数组的每一个元素执行一次提供的函数。

map() 方法创建一个新数组，其结果是该数组都执行一次函数，原函数保持不变。

filter() 方法使指定函数测试数组的每一个元素，并放回一个通过元素的新数组。

reduce() 方法使数组中的前项和后项经过某种计算，并累计最终值

some() 方法测试该数组有元素通过了指定函数的测试，如果有返回true，否则，返回false。

every() 方法测试该数组是否全部通过指定函数测试，全部通过返回true，否则，返回false。

forEach 遍历数组
var arr = ["a", "b", "c"];
arr.forEach(function(element,index) {
    console.log(element,index);      
});

map 返回新数组，为当前元素加字符串m
var arr = ["a", "b", "c"];

arr.map(function(element,index) {
    return element += "m";
});

// 将给定数组的元素转成整数

["1", "2", "3"].map(parseInt);         // [1, NaN, NaN]
// 等价于
["1", "2", "3"].map(function(value,index,array){
    return parseInt(value,index);
});
parseInt(3,1);                         // NaN   parseInt(string, radix) 函数将给定的字符串以指定基数解析成为整数。

filter 返回大于10的元素
// 12, 130, 44
var arr = [12, 5, 8, 130, 44];
arr.filter(function(value){
    return value>10
});
// 等价于
arr.filter((value)=>value>10);

 var result = arr.reduce(function(prev,next){
   return prev+next
 })
some 判断当前数组有元素大于10的元素
var arr = [12, 5, 8, 130, 44];
arr.some(function(value){                  // true
    return value>10
});

every 判断当前数组所有元素是否都大于10
var arr = [12, 5, 8, 130, 44];
arr.every(function(value){                 // false
    return value>10
});
```

1. vue-router的实现原理看了吗？两种模式怎么设置
2. promise解决了什么问题?
3. vue nexttick知道吗？
4. Async await 用过吗？怎么使用？
5. 怎么解决express的回调

### 唯乐屋

1. 手写一个东升日落的效果
2. vue-router的实现原理
3. 字符串转数组，数组转字符串的方法（三种方法）
4. less、sass有哪些东西
5. 说一下变量提升？
6. es6有哪些东西？

### 好未来公司

#### 一面：

1. amd，cmd,common,es6模块规范
2. html5 新标签有哪些？
3. 实现一个圆+三角形（css）
4. 实现一个动画波浪线（css3）
5. 基本数据类型
6. 写一个方法，输入120，输出02:00,输入121，输出02:01
7. dva
8. promise是解决什么问题
9. canvas的使用
10. vedio的使用，支持哪些格式，怎么监控vedio的卡顿
11. express require req.body req.param req.query
12. 怎么写一个中间件
13. nuxt.js
14. 前端优化有哪些？
15. 1,'1','',null.\[\],{}用true和false表示他们
16. 说一下内存泄露和垃圾回收机制
17. localstorage存入一个1，获取的时候返回是1，是什么类型？
18. localstorage，cookie，sessionstorage的区别
19. 怎么设置cookie的有效期
20. 上传文件做过吗？预览做过吗？怎么实现？
21. 1px 处理 安卓和ios的处理
22. 写一个手机号码的正则？
23. 手写一个不定宽盒子居中？
24. flex使用过吗？怎么实现三等分？怎么实现30%+40%+30%
25. es6有哪些东西？
26. a,b分别输出的是什么？


```
(function(){
var a=b=1
})()
console.log(a)
console.log(b)

拆分一下就是 var a=b;b=1;
省略var 就是代表声明的是全局变量
```

1. 怎么让异步的函数变成同步的？
2. react native 安卓与ios
3. ios怎么取消点按选中的效果
4. webpack的一些配置有哪些？
5. 说一下loader和plugins的区别
6. Ie8
7. antd
8. ionic
9. 实现继承有哪些方法？说一下
10. react生命周期有哪些？
11. vue的生命周期有哪些？
12. react&vue的区别



