## 彻底理解继承和原型链

### 继承的目的

在JavaScript中定义两个构造函数Person()和Employee()，为了方便理解和讲解，我们可以将它们理解为Person类和Employee类。
以下内容提到的Person类、Employee类，和Person()构造函数、Employee()构造函数是一个意思。

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

目前Person()和Employee()构造函数是两个彼此独立的存在，它们没有任何关系。
所以由Employee()构造函数创建的实例emp，肯定是访问不到Person的name属性和sayHello()方法的。

