# Set和Map数据结构

### Set

ES6提供了新的数据结构Set。类似于数组，只不过其成员值都是唯一的，没有重复的值。

Set结构接收一个数组作为参数，用来初始化。

```
var items = new Set([1, 2, 3, 4, 5, 5, 5]);

items.size 
// 5
```

**向Set加入值的时候，不会发生类型转换。这意味着，在Set中5和”5”是两个不同的值。**

**Set结构有以下属性：**

* Set.prototype.constructor: 构造函数，默认就是Set函数。
* set.prototype.size : 返回Set的成员总数。

**Set结构有以下方法：**

* add\(value\) : 添加某个值。
* delete\(value\) : 删除某个值。
* has\(value\) : 返回一个布尔值，表示该值是否为Set的成员。
* clear\(\) : 清除所有成员。



Array.from方法可以将Set结构转换为数组。

这也提供了一种除去数组中重复元素的方法。

### Map

Js对象本质上是键值对的集合。但是只能使用字符串充当键。这在一定程度上给我们的使用带来很大的限制。

而ES6正是为了解决这个问题才提供了Map结构。它类似与对象，也是键值对集合，但是”键”的范围不限于字符串，对象也可以当作键。

```
var m = new Map();
o = {p: "hello world"};

m.set(o, "content");
console.log( m.get(o) );  // content
```

Map函数可接收一个数组进行初始化。

```
var map = new Map([["name", "小明"], ["title", "Author"]]);

map.size //2
map.has("name"); //true
map.get("name"); //小明
map.has("title"); //true
map.get("title"); //Author
```

注意：只有针对同一个对象的引用，Map结构才将其视作同一个键。这一点要非常小心才行。















