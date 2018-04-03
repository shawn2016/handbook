### 怎么理解es6箭头函数中的this，它和一般函数的this指向有什么区别呢？

[https://www.cnblogs.com/freelyflying/p/6978126.html](#)

**普通函数中的this:**

1. this总是代表它的直接调用者, 例如 obj.func ,那么func中的this就是obj
2. 在默认情况\(非严格模式下,未使用 'use strict'\),没找到直接调用者,则this指的是 window
3. 在严格模式下,没有直接调用者的函数中的this是 undefined
4. 使用call,apply,bind\(ES5新增\)绑定的,this指的是 绑定的对象

**箭头函数中的this**

默认指向在定义它时,它所处的对象,而不是执行时的对象, 定义它的时候,可能环境是window（即继承父级的this）;

### 同源策略

**同源策略**在web应用的安全模型中是一个重要概念。源就是{协议，主机，端口}

### 说一说移动端的布局。 flexible。

手机淘宝从2014年中开始，全面推行flexible设计。什么叫flexible呢？其实flexible就是responsive的低端形态和基础。

手机淘宝用JS来动态写meta标签，手机淘宝的flexible方案是综合运用rem和px两种单位+js设置scale和html字体。
我们可以在[GitHub](https://link.jianshu.com?t=https://github.com/amfe/lib-flexible)上找到这个项目，可以通过网上查阅资料了解更多。

### 说一说异步编程的方式有哪些

Javascript语言将任务的执行模式分成两种：同步（Synchronous）和异步（Asynchronous）。

"同步模式"：后一个任务等待前一个任务结束，然后再执行，程序的执行顺序与任务的排列顺序是一致的、同步的；

"异步模式"则完全不同，每一个任务有一个或多个回调函数（callback），前一个任务结束后，不是执行后一个任务，而是执行回调函数，后一个任务则是不等前一个任务结束就执行，所以程序的执行顺序与任务的排列顺序是不一致的、异步的。非常重要。在浏览器端，耗时很长的操作都应该异步执行，避免浏览器失去响应，最好的例子就是Ajax操作。在服务器端，"异步模式"甚至是唯一的模式，因为执行环境是单线程的，如果允许同步执行所有http请求，服务器性能会急剧下降，很快就会失去响应。

#### 有哪些方法实现"异步模式"编程

1. 回调函数：一般情况下，应用程序时常通过API调用库里所预先备好的函数。但是有些库函数却要求应用先传给它一个函数，好在合适的时候调用，以完成目标任务。这个被传入的、后又被调用的函数就称为回调函数。
2. 事件监听：另一种思路是采用事件驱动模式。任务的执行不取决于代码的顺序，而取决于某个事件是否发生。
3. 发布/订阅
4. Promise

### 你最喜欢的es6中的特性是什么，为什么。

1. const和let关键字
2. 数组助手函数
3. 箭号函数
4. class类
5. 模板字符串
6. 默认函数参数
7. Rest
8. 解构
9. Promise

###   有没有遇到过这样的问题： 一个有border的div，里面有一个图片，发现图片和下面的border有一定的空隙。

img与div（block类型元素）下边界有距离（或者叫缝隙、空隙）。

解决方案：

**法宝一：**给图片img标签display:block

**法宝二：**定义图片img标签vertical-align:bottom，vertical-align:middle，vertical-align:top。

 img{vertical-align:bottom;}  

至于HTML属性align="center"（对于图片浏览器会处理成align="middle"）的解决办法，就相当于vertical-align:middle; 所以道理也是一样的，只要vertical-align不取baseline，这个空隙就消失了。

 

**法宝三：**定义容器里的字体大小为0。

div { 
width:110px; 
border:1px solid #000000; 
font-size:0 
} 

 

**据说原因：**

图片文字等inline元素默认是和父级元素的baseline对齐的，而baseline又和父级底边有一定距离（这个距离和 font-size，font-family 相关），所以设置 vertical-align:top/bottom/text-top/text-bottom 都可以避免这种情况出现。而且不光li，其他的block元素中包含img也会有这个现象。

 

**相关说明**

1.ie的显示有几种模式，在html文档的开始部分声明<!DOCTYPE ....>

如果声明为strict模式，ie以w3c的方式显示文档，而w3c的标准里面<img />默认是一个inline的标签，除非自己显式的声明为 block

2.那个空隙是ie针对盒模型默认的line-height和font-size. 给img desplay:block;虽然能解决问题,但没从结构上来考虑.可谓治标不治本.

### 函数调用的方式有哪些。他们的区别是什么。

#### **方法调用模式**

当一个函数被保存为对象的一个属性时，我们称它为一个方法。当一个对象的方法被调用时，this被绑定到调用方法的对象。

```
var myObj = {
    name : "MT",
    setName : function(name){
        this.name = name;
    }
};
 
myObj.setName("哀木涕");
console.log(myObj.name);    //"哀木涕"
 
myObj.setName("小德");
console.log(myObj.name);    //小德
```

方法可以使用this访问自己所属的对象，所以它能从对象中取值或对对象进行修改。this和对象的绑定发生在方法调用的时候。这个“超级”延迟绑定(vary late binding)使得函数可以对this高度复用。通过this可以取得它们所属对象的上下文方法称为公共方法（public method）。

#### **函数调用模式**  

当一函数并非一个对象的属性时，那么它就是被当做一个函数来调用的:

以此模式调用函数时，this被绑定到全局对象。这是语言设计上的一个错误。倘若语言设计正确，那么当内部函数被调用时，this应该仍然绑定到外部函数的this变量。这个设计错误的后果就是方法不能利用内部函数来帮助它工作，因为内部函数的this被绑定了错误的值(全局对象)，所以不能共享该方法对对象的访问权。幸运的是，有一个很容易的解决方案：如果一个对象的方法定义了一个变量并将this赋值给它，那么内部函数就可以通过那个变量访问到外部方法调用的对象。按照约定，我们把那个变量命名为that:

```
myObj.changeName = function(){
    var that = this;    //解决方法
     
    var change = function(){
        that.name = "change" + that.name;
    }
     
    change();   //以函数的方式调用change;
}
 
//以方法的形式调用changeName。
myObj.changeName();
console.log(myObj.name);
```

#### **构造器调用模式**

JavaScript是一门基于原型继承的语言。这意味着对象可以直接从其他对象继承属性。该语言是无类型的。

　　如果在一个函数前面带上 new 关键字来调用，那么背地里将会创建一个连接到该函数的prototype成员的新对象，同时this会被绑定到那个新对象上。

　　new 前缀也会改变return 语句的行为,如果return 的值是对象，那么将会将这个对象返回，否则将返回默认创建的新对象。

```
//创建一个名为Person的构造器函数。它构造一个带有name属性的对象。
function Person(howName){
    this.name = howName;
}
 
Person.prototype.getName = function(){
    return this.name;
}
 
var person = new Person("MT");
console.log(person.getName());
```

　一个函数，如果创建的目的就是希望结合new前缀来调用，那它就被称为构造器函数。按照约定，它们保存在以大写格式命名的变量里。如果调用构造函数时没有在前面加上new ,可能会发生非常糟糕的事情，（这时将会以函数的方式调用，由于函数的方式调用this是全局对象，这时不会返回新对象，而是在全局对象上添加属性。）既没有编译时警告，，也没有运行时警告，所以大写约定非常重要。

#### **apply/call调用模式**

因为JavaScript是一门函数式的面向对象编程语言，所以函数可以拥有方法。

　　apply/call方法允许我们选择this的值。apply方法接受两个参数，第一个是要绑定的this的值，第二个参数是参数数组。call方法第一个参数是要绑定的this的值，后面紧跟的是相关的参数。

```
function setAge(age){
    this.age = age;
}
 
setAge.call(myObj, 23);
console.log(myObj.age);     //23
 
setAge.apply(myObj, [24]);
console.log(myObj.age);     //24
```

### 说一说原型链

https://www.cnblogs.com/zhengsongjun/p/7657608.html

#### **原型对象**

在javascript中，每当定义一个对象（函数也是对象），对象都会包含一些预定义的属性，其中每个函数对象都有一个prototype属性，这个属性指向函数的原型对象，所以反过来粗暴一点说，原型对象就是函数的prototype这个属性所指的对象，函数的对象的prototype的属性就是这个函数的原型对象。

```
Person.prototype = {
   name:  'Zaxlct',
   age: 28,
   job: 'Software Engineer',
   sayName: function() {
     alert(this.name);
   }
}
```

这就是原型对象，明白吗，然后我们给这个原型对象添加很多很多的属性和sayName这个方法，当然，他还有一个对象constructor

 默认情况下，所有的原型对象，都会自动获得一个constructor(构造函数)这个属性，这个属性是一个指针，指向prototype属性所在的函数Person!

**Person.prototype.constructor === Person**

### 几种保持登录状态的方式

https://www.cnblogs.com/-new/p/6960901.html