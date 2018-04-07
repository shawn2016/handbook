### 请问老师new Object\(\)和Object.create\(\)两者有何异同？

```
 // Demo
var a = new Object();  // 创建一个对象，没有父类哦
var b = Object.create(a.prototype);  // b 继承了a的原型
```



Object.create() 是E5的一个新特性哦，其实可以理解为继承一个对象，create方法有两个参数

一个是要继承的对象的原型，如果没有就传null，第二个参数是对象的属性描述符，这些都是E5才有的~

第一种：
var a = {x:1};
var b = Object.create(a);
console.log(b);//输出：{};
console.log(b.__proto__);//输出：{x:1}
第二种：
如果用 b =new object(a)
connsole.log(b);//输出：{x:1}
congsole.log(b.__proto__);//输出：{}

所以 var b = Object.create(a.prototype); // b 继承了a的原型
这个说法是错误的，应该是b.__proto__=== a.prototype,严格等于
结论：b的原型指向a的prototype属性

\#3