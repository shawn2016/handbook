## class

ES6为我们创建对象提供了新的语法糖，这就是Class语法。如果你对ES5中面向对象的方式比较熟悉的话，Class掌握起来也是非常迅速的，因为除了写法的不同，它并不会增加新的难以理解的知识点。我们先利用一个简单的例子来看看写法的不同。

```
// ES5
// 构造函数
function Person(name, age) {
  this.name = name;
  this.age = age;
}

// 原型方法
Person.prototype.getName = function() {
  return this.name
}

// ES6
class Person {
  constructor(name, age) {  // 构造函数
    this.name = name;
    this.age = age;
  }

  getName() {  // 原型方法
    return this.name
  }
}
```

> babel会将ES6的写法编译成为利用Object.defineProperty实现的方式，这个方法的具体用处大家可以在《JavaScript高级编程3》中学习了解，包括get，set，等都有详细的说明

除此之外，我们还需要特别注意在实际使用中的几种写法方式的不同，在下面的例子注释中，我说明了他们分别对应的ES5中的含义。

```
class Person {
  constructor(name, age) {  // 构造函数
    this.name = name;
    this.age = age;
  }

  getName() {   // 这种写法表示将方法添加到原型中
    return this.name
  }

  static a = 20;  // 等同于 Person.a = 20

  c = 20;   // 表示在构造函数中添加属性 在构造函数中等同于 this.c = 20

// 箭头函数的写法表示在构造函数中添加方法，在构造函数中等同于this.getAge = function() {}
  getAge = () => this.age   

}
```

箭头函数需要注意的仍然是this的指向问题，因为箭头函数this指向不能被改变的特性，因此在react组件中常常利用这个特性来在不同的组件进行传值会更加方便。

* 继承 extends

相比ES5，ES6的继承就要简单很多，我们直接来看一个例子。

```
class 
Person {
  constructor(name, age) {
    
this.name = name;
    
this.age = age;
  }

  getName() {
    
return 
this.name
  }
}


// Student类继承Person类

class 
Student 
extends 
Person {
  constructor(name, age, gender, classes) {
    
super(name, age);
    
this.gender = gender;
    
this.classes = classes;
  }

  getGender() {
    
return 
this.gender;
  }
}
```

我们只需要一个extends关键字，就可以实现继承了，不用像ES5那样去担心构造函数继承和原型继承，除此之外，我们还需要关注一个叫做`super`的方法。

在继承的构造函数中，我们必须如上面的例子那么调用一次super方法，它表示构造函数的继承，与ES5中利用call/apply继承构造函数是一样的功能。

```
// 构造函数中
// es6 
super(name, age);

// es5
Person.call(this);
```

> super还可以直接调用父级的原型方法，`super.getName`，但是我自己从来没这样用过，也就不扩展说了。

继承在react中有大量的使用场景，许多组件都利用继承来创建。

```
import React, { Component } from 'react';

class App extends Component {

  defaultProps = {}
  state = {}
  componentWillMount() {}
  componentDidMount() {}

  btnClick = e => {}

  render() {}
}

```

只要根据我们上面所学到的知识，明确的知道哪些属性方法是放在构造函数中，哪些属性方法是放到了原型中，那么我们自己在编写react组件的时候就要简单和清晰很多。

其实只要我们ES5面向对象的知识足够扎实，ES6和react掌握起来也没有太多的难度，所有的学习难点，并不在ES6这些不同的语法糖上，而在于ES5中的原理，因此我在前面分享ES5的核心知识的时候，很多读者老爷都迫不及待的希望我能够更多的说一说ES6的知识。其实我们都没有必要那么着急，只要前面10多篇文章的知识足够扎实，这篇文章所涉及到的常用的ES6知识，最多花30分钟也就掌握了。这些写法上的不同并不会造成大家理解上的困难，只需要有一个熟悉过程就行了。所以大家的重点，还是要回归到基础上来。

