JavaScript诞生已经有20多年了，我们一直使用的用来循环一个数组的方法是这样的：

```
for (var index = 0; index < myArray.length; index++) {
console.log(myArray[index]);
}
```

自从JavaScript5起，我们开始可以使用内置的**forEach**方法：

```
myArray.forEach(function (value) {
console.log(value);
});
```

写法简单了许多，但也有短处：你不能中断循环\(使用语句或使用语句。

**for-in循环**

实际是为循环”enumerable“对象而设计的：

```
var obj = {a:1, b:2, c:3};
for (var prop in obj) {
console.log("obj." + prop + " = " + obj[prop]);
}
// 输出:
// "obj.a = 1"
// "obj.b = 2"
// "obj.c = 3"
```

你也可以用它来循环一个数组：

```
for (var index in myArray) { // 不推荐这样
console.log(myArray[index]);
}
```

不推荐用for-in来循环一个数组，因为，不像对象，数组的 index 跟普通的对象属性不一样，是重要的数值序列指标。

总之， for – in 是用来循环带有字符串key的对象的方法。

**for-of循环**

JavaScript6里引入了一种新的循环方法，它就是for-of循环，它既比传统的for循环简洁，同时弥补了forEach和for-in循环的短板

可以遍历：

1. 字符串
2. 数组
3. enumerable属性的对象
4. dom对象
5. Map
6. Set

```
let iterable = new Set([1, 1, 2, 2, 3, 3]);
for (let value of iterable) {
console.log(value);
}
// 1
// 2
// 3
```

1. generators

```
function* fibonacci() { // a generator function
let [prev, curr] = [0, 1];
while (true) {
[prev, curr] = [curr, prev + curr];
yield curr;
}
}
for (let n of fibonacci()) {
console.log(n);
// truncate the sequence at 1000
if (n >= 1000) {
break;
}
}
```



