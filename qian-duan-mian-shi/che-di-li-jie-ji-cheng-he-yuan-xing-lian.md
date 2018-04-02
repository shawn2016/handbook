## 彻底理解继承和原型链

### 继承的目的

##### 实现继承的目的是什么？当然是让子类能够使用基类的属性和方法。

在JavaScript中定义两个构造函数Person\(\)和Employee\(\)，为了方便理解和讲解，我们可以将它们理解为Person类和Employee类。  
以下内容提到的Person类、Employee类，和Person\(\)构造函数、Employee\(\)构造函数是一个意思。

```
function Person() {
    this.name = 'keefool';
    this.sayHello = function() {
        return 'Hello, I am ' + this.name;
    }
}

function Employee(email) {
    this.email = email;
}

var person = new Person();
var emp = new Employee('keepfool@xxx.com');
```

目前Person\(\)和Employee\(\)构造函数是两个彼此独立的存在，它们没有任何关系。  
所以由Employee\(\)构造函数创建的实例emp，肯定是访问不到Person的name属性和sayHello\(\)方法的。

![](https://images2015.cnblogs.com/blog/341820/201606/341820-20160610071721402-246699741.png)

使用instanceof操作符同样可以确定emp是Employee类的实例，而不是Person类的实例。

![](https://images2015.cnblogs.com/blog/341820/201606/341820-20160610071722433-1387947998.png)

### 实现继承

**通过原型实现继承。**

当我们定义函数时，JavaScript会自动的为函数分配一个prototype属性。
Person()也是一个函数，那么Person()函数也会有prototype属性，即Person.prototype。

```
function Person() {
    this.name = 'keefool';
    this.sayHello = function() {
        return 'Hello, I am ' + this.name;
    }
}	

// 定义了函数后，JavaScript自动地为Person()函数分配了一个prototype属性
// Person.prototype = {};
```

我们可以在Person.prototype上定义一些属性和方法，这些属性和方法是可以被Person的实例使用的。

```
function Person() {
    this.name = 'keefool';
    this.sayHello = function() {
        return 'Hello, I am ' + this.name;
    }
}

Person.prototype.height = 176;

var person = new Person();
// 访问Person.prototype上定义的属性
person.height;	// 输出176
```

同理在Employee.prototype上定义的属性和方法，也可以被Employee类的实例使用。
咱们的目的是让Employee的实例能够访问name属性和sayHello()方法，如果没有Person()构造函数，咱们是这么做的：

```
function Employee(email) {
    this.email = email;
}
Employee.prototype = {
    name : 'keefool',
    sayHello = function() {
        return 'Hello, I am ' + this.name;
    }
}
```

既然Person()构造函数已经定义了name和sayHello()，我们就不必这么做了。
怎么做呢？**让Employee.prototype指向一个Person类的实例。**

```
function Person() {
    this.name = 'keefool';
    this.sayHello = function() {
        return 'Hello, I am ' + this.name;
    }
}
function Employee(email) {
    this.email = email;
}

var person = new Person(); 
Employee.prototype = person;

var emp = new Employee('keepfool@xxx.com');
```