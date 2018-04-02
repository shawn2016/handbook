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
Person\(\)也是一个函数，那么Person\(\)函数也会有prototype属性，即Person.prototype。

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
person.height;    // 输出176
```

同理在Employee.prototype上定义的属性和方法，也可以被Employee类的实例使用。  
咱们的目的是让Employee的实例能够访问name属性和sayHello\(\)方法，如果没有Person\(\)构造函数，咱们是这么做的：

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

既然Person\(\)构造函数已经定义了name和sayHello\(\)，我们就不必这么做了。  
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

现在我们就可以访问emp.name和emp.sayHello\(\)方法了。

![](https://images2015.cnblogs.com/blog/341820/201606/341820-20160610071723355-1789598776.png)

在Chrome控制台，使用instanceof操作符，可以看到emp对象现在已经是Person类的实例了。

![](https://images2015.cnblogs.com/blog/341820/201606/341820-20160610071724355-791458085.png)

### 这是如何实现的？

* Employee.prototype是一个引用类型，它指向一个Person类的一个实例person。
* person对象恰恰是有name属性和sayHello\(\)方法的，访问Employee.prototype就像访问person对象一样。
* 访问emp.name和emp.sayHello\(\)时，实际访问的是Employee.prototype.name和Employee.prototype.sayHello\(\)，最终访问的是person.name和person.sayHello\(\)。

如果你对这段代码还是有所疑惑，你可以这么理解：

```
var person = new Person();
Employee.prototype.name = person.name;
Employee.prototype.sayHello = person.sayHello;
```

由于person对象在后面完全没有用到，以上这两行代码可以合并为一行

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

Employee.prototype = new Person();
var emp = new Employee('keepfool@xxx.com');
```

下面这幅图概括了实现Employee继承Person的过程：

![](https://images2015.cnblogs.com/blog/341820/201606/341820-20160610071725355-1020928779.png)

**name和sayHello\(\)不是Employee类的自有属性和方法，它来源于Employee.prototype。**

而Employee.prototype指向一个Person的实例，这个实例是能够访问name和sayHello\(\)的。

![](https://images2015.cnblogs.com/blog/341820/201606/341820-20160610071726402-523240670.png)

## 原型继承的本质

**JavaScript的原型继承的本质：将构造函数的原型对象指向由另外一个构造函数创建的实例。**

这行代码`Employee.prototype = new Person()`描述的就是这个意思。  
现在我们可以说**Employee\(\)构造函数继承了Person\(\)构造函数。**

用一句话概括这个继承实现的过程：

Employee\(\)构造函数的原型引用了一个由Person\(\)构造函数创建的实例，从而建立了Employee\(\)和Person\(\)的继承关系。

# 再谈constructor

## 对象的constructor属性

上一篇文章有提到过，**每个对象都有constructor属性，constructor属性应该指向对象的构造函。**  
例如：Person实例的constructor属性是指向Person\(\)构造函数的。

```
var person = new Person();
```

![](https://images2015.cnblogs.com/blog/341820/201606/341820-20160610071728668-419878531.png)

在未设置Employee.prototype时，emp对象的构造函数原本也是指向Employee\(\)构造函数的。

![](https://images2015.cnblogs.com/blog/341820/201606/341820-20160610071729527-1326466155.png)

当设置了`Employee.prototype = new Person();`时，emp对象的构造函数却指向了Person\(\)构造函数。

![](https://images2015.cnblogs.com/blog/341820/201606/341820-20160610071730496-329429816.png)

无形之中，emp.constructor被改写了。  
emp对象看起来不像是Employee\(\)构造函数创建的，而是Person\(\)构造函数创建的。

这不是我们期望的，我们希望emp对象看起来也是由Employee\(\)构造函数创建的，即emp.constructor应该是指向Employee\(\)构造函数的。  
要解决这个问题，我们先弄清楚对象的constructor属性是从哪儿来的，知道它是从哪儿来的就知道为什么emp.constructor被改写了。

  
constructor属性的来源

**当我们没有改写构造函数的原型对象时，constructor属性是构造函数原型对象的自有属性。  
**例如：Person\(\)构造函数的原型没有改写，constructor是Person.prototype的自有属性。

![](https://images2015.cnblogs.com/blog/341820/201606/341820-20160610071732027-2077474323.png)

**当我们改写了构造函数的原型对象后，constructor属性就不是构造函数原型对象的自有属性了。**

例如：Employee\(\)构造函数的原型被改写后，constructor就不是Person.prototype的自有属性了。

![](https://images2015.cnblogs.com/blog/341820/201606/341820-20160610071732902-1904980252.png)

Employee.prototype的constructor属性是指向Person\(\)构造函数的。

![](https://images2015.cnblogs.com/blog/341820/201606/341820-20160610071733761-1166814882.png)

这说明：**当对象被创建时，对象本身没有constructor属性，而是来源于创建对象的构造函数的原型对象。**

即当我们访问emp.constructor时，实际访问的是Employee.prototype.constructor，Employee.prototype.constructor实际引用的是Person\(\)构造函数，person.constructor引用是Person\(\)构造函数，Person\(\)构造函数实际上是Person.prototype.constructor。

这个关系有点乱，我们可以用以下式子来表示这个关系：

```
emp.constructor = person.constructor = Employee.prototype.constructor = Person = Person.prototype.constructor
```

**它们最终都指向Person.prototype.constructor！**

## 改写原型对象的constructor

弄清楚了对象的constructor属性的来弄去脉，上述问题就好解决了。  
解决办法就是让**Employee.prototype.constructor指向Employee\(\)构造函数。**

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

![](https://images2015.cnblogs.com/blog/341820/201606/341820-20160610071734636-2097881172.png)

如果你还是不能理解关键的这行代码：

```
Employee.prototype.constructor = Employee;
```

你可以尝试从C\#的角度去理解，在C\#中Employee类的实例肯定是由Employee类的构造函数创建出来的。

