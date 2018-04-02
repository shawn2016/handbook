# 用原生js实现一个new方法

首先写一个父类方法\(包含参数name,age\)：

```
function Person(name,age){
    this.name = name;
    this.age = age;
}
```

new一个Person的实例p1做研究对比

```
var p1 = new Person("Richard", 22);
//此时p1包含name、age属性，同时p1的__proto__指向Person的prototype
p1.name;//Richard
p1.age;//22
```

自定义一个New函数：

```
//通过分析原生的new方法可以看出，在new一个函数的时候，
// 会返回一个func同时在这个func里面会返回一个对象Object，
// 这个对象包含父类func的属性以及隐藏的__proto__
function New(f) {
    //返回一个func
    return function () {
        var o = {"__proto__": f.prototype};
        f.apply(o, arguments);//继承父类的属性

        return o; //返回一个Object
    }
}
```

通过自定义New方法创建一个实例对象p2:

```
var p2 = New(Person)("Jack",25);
p2.name;//Jack
p2.age;//25
```

此时p2 instanceof Person 返回的是true；

```
Person.prototype.gender ="male";
p1.gender//male
p2.gender//male
```

