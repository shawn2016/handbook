### 作业帮

1. 手写一个闭包
2. 闭包的作用和缺点

3. $.fn.extend与$.extend的区别

4. 说一下常用的es6语法

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
2. html5 新标签
3. 实现一个圆+三角形（css）
4. 实现一个动画波浪线（css3）
5. 基本数据类型
6. 写一个方法，输入120，输出02:00,输入121，输出02:01
7. dva
8. canvas的使用
9. vedio的使用，支持哪些格式，怎么监控vedio的卡顿
10. express require req.body req.param req.query
11. 怎么写一个中间件
12. nuxt.js
13. 前端优化有哪些？
14. 1,'1','',null.\[\],{}用true和false表示他们
15. 说一下内存泄露和垃圾回收机制
16. localstorage存入一个1，获取的时候返回是1，是什么类型？
17. localstorage，cookie，sessionstorage的区别
18. 怎么设置cookie的有效期
19. 上传文件做过吗？预览做过吗？怎么实现？
20. 1px 处理 安卓和ios的处理
21. 写一个手机号码的正则？
22. 手写一个不定宽盒子居中
23. flex使用过吗？怎么实现？怎么实现30%+40%+30%
24. es6有哪些东西？
25. 怎么让异步的函数变成同步的？



