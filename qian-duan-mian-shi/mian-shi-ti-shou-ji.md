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



  




