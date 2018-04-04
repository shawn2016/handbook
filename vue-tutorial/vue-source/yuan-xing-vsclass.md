原文链接：[https://segmentfault.com/a/1190000003798438\#articleHeader12](https://segmentfault.com/a/1190000003798438#articleHeader12)

类实现：

    class User {
      constructor(firstName, lastName) {
        this.firstName = firstName
        this.lastName = lastName
      }

      fullName() {
        return `${this.firstName} ${this.lastName}`
      }
    }

    let user = new User('David', 'Chen')
    user.fullName()  // David Chen

原型实现方式：

```
function User(firstName, lastName) {
  this.firstName = firstName
  this.lastName = lastName
}

User.prototype.fullName = function() {
  return '' + this.firstName + this.lastName
}
```

ES6 并没有改变 JavaScript 基于原型的本质，只是在此之上提供了一些语法糖。`class` 就是其中之一。其他的还有 `extends`，`super` 和 `static` 。它们大多数都可以转换成等价的 ES5 语法。

我们来看看另一个继承的例子：

```
class Child extends Parent {
  constructor(firstName, lastName, age) {
    super(firstName, lastName)
    this.age = age
  }
}
```

其基本等价于：

```
function Child(firstName, lastName, age) {
  Parent.call(this, firstName, lastName)
  this.age = age
}

Child.prototype = Object.create(Parent.prototype)
Child.constructor = Child
```

无疑上面的例子更加直观，代码组织更加清晰。这也是加入新语法的目的。不过虽然新语法的本质还是基于原型的，但新加入的概念或多或少会引起一些连带的影响。

### extends 继承内建类的能力

因为语言内部设计原因，我们没有办法自定义一个类来继承 JavaScript 的内建类的。继承类往往会有各种问题。ES6 的 `extends` 的最大的卖点，就是不仅可以继承自定义类，还可以继承 JavaScript 的内建类，比如这样：

```
class MyArray extends Array {
}
```

这种方式可以让开发者继承内建类的功能创造出符合自己想要的类。所有 Array 已有的属性和方法都会对继承类生效。这确实是个不错的诱惑，也是继承最大的吸引力。

但现实总是悲催的。`extends` 内建类会引发一些奇怪的问题，很多属性和方法没办法在继承类中正常工作。举个例子：

```
var a = new Array(1, 2, 3)
a.length  // 3

var b = new MyArray(1, 2, 3)
b.length  // 0
```

如果说语法糖可以用 Babel.js 这种 transpiler 去编译成 ES5 解决 ，扩充的 API 可以用 polyfill 解决，但是这种内建类的继承机制显然是需要浏览器支持的。而目前唯一支持这个特性的浏览器是………… Microsoft Edge 。

好在这并不是什么致命的问题。大多数此类需求都可以用封装类去解决，无非是多写一点 wrapper API 而已。而且个人认为封装和组合反而是比继承更灵活的解决方案。

