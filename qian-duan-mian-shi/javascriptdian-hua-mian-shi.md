

```
typeof 返回值有哪些？
number, boolean, string, undefined, object, function，symbol
```



区分对象和数组的方法

```
Object.prototype.toString.call(o)=='[object Array]'
```

```
var ary = [1,23,4];
function isArray(o){
return Object.prototype.toString.call(o)=='[object Array]';
}
console.log(isArray(ary));
```

```
一个数组里用很多元素，如何快速把这个数组清空
 const len = obj.length
        obj.length = 0
        obj = Array.from({ length: len })
```



