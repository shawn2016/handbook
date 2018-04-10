## 1. Array.from()

Array.from方法用于将两类对象转为真正的数组：类数组的对象（ array-like object ）和可遍历（ iterable ）的对象（包括 ES6 新增的[数据结构](http://lib.csdn.net/base/datastructure) Set 和Map ）

```
let arrayLike = {  
　　'0': 'a',  
　　'1': 'b',  
　　'2': 'c',  
　　length: 3  
};  
// ES5 的写法  
var arr1 = [].slice.call(arrayLike); // ['a', 'b', 'c']  
// ES6 的写法  
let arr2 = Array.from(arrayLike); // ['a', 'b', 'c']  
  
// NodeList 对象  
let ps = document.querySelectorAll('p');  
Array.from(ps).forEach(function (p) {  
　　console.log(p);  
});  
// arguments 对象  
function foo() {  
var args = Array.from(arguments);  
// ...  
}  

//字符串转换为字符数组str.split('')  
Array.from('hello')  // ['h', 'e', 'l', 'l', 'o']  
let namesSet = new Set(['a', 'b'])  
Array.from(namesSet) // ['a', 'b']  
  
Array.from({ length: 3 });  // [ undefined, undefined, undefined ] 
```

对于还没有部署该方法的浏览器，可以用Array.prototype.slice方法替代：

```
const toArray = (() =>
  Array.from ? Array.from : obj => [].slice.call(obj)
)();
```

Array.from还可以接受第二个参数，作用类似于数组的map方法，用来对每个元素进行处理，将处理后的值放入返回的数组。

```
Array.from(arrayLike, x => x * x);  
//  等同于  
Array.from(arrayLike).map(x => x * x);  
Array.from([1, 2, 3], (x) => x * x)  
// [1, 4, 9]  
```

```
//Array.from回调函数
var arr1 = Array.from([1,2,3], function(item){
    return item*item;
});
var arr2 = Array.from([1,2,3]).map(function(item){
    return item*item;
});
var arr3 = Array.from([1,2,3], (item) => item*item);

console.log(arr1); //[ 1, 4, 9 ]
console.log(arr2); //[ 1, 4, 9 ]
console.log(arr3); //[ 1, 4, 9 ]
```

值得提醒的是，扩展运算符（...）也可以将某些数据结构转为数组。

```
// arguments 对象  
function foo() {  
　　var args = [...arguments];  
}  
// NodeList 对象  
[...document.querySelectorAll('div')]  
```

## 2. Array.of()

Array.of方法用于将一组值，转换为数组。Array.of总是返回参数值组成的数组。如果没有参数，就返回一个空数组。

Array.of基本上可以用来替代Array()或new Array()，并且不存在由于参数不同而导致的重载。它的行为非常统一。

这个方法的主要目的，是弥补数组构造函数Array()的不足。因为参数个数的不同，会导致Array()的行为有差异

```
Array() // []  
Array(3) // [, , ,]  
Array(3, 11, 8) // [3, 11, 8]  
  
Array.of() // []  
Array.of(3) // [3]  
Array.of(3, 11, 8) // [3,11,8]  
  
Array.of(3).length // 1   
Array.of(undefined) // [undefined]  
Array.of(1) // [1]  
Array.of(1, 2) // [1, 2]  
```

Array.of方法可以用下面的代码模拟实现：

```
function ArrayOf(){
  return [].slice.call(arguments);
}
```

## 3. find() 和 findIndex()

数组实例的find方法，用于找出第一个符合条件的数组成员。它的参数是一个回调函数，所有数组成员依次执行该回调函数，直到找出第一个返回值为true的成员，然后返回该成员。如果没有符合条件的成员，则返回undefined。

```
[1, 4, -5, 10].find((n) => n < 0)  
// -5  
[1, 5, 10, 15].find(function(value, index, arr) {  
    return value > 9;  
}) // 10  
```

　　上面代码中，find方法的回调函数可以接受三个参数，依次为**当前的值、当前的位置和原数组**。
数组实例的findIndex方法的用法与find方法非常类似，返回第一个符合条件的数组成员的位置，如果所有成员都不符合条件，则返回-1。

```
[1, 5, 10, 15].findIndex(function(value, index, arr) {  
    return value > 9;  
}) // 2  
```

这两个方法都可以接受第二个参数，用来**绑定回调函数的this对象**。
另外，这两个方法都可以发现NaN，弥补了数组的IndexOf方法的不足。

```
[NaN].indexOf(NaN)  
// -1  
[NaN].findIndex(y => Object.is(NaN, y))  
// 0  
```

## 4. fill()

fill()方法使用给定值，填充一个数组。

```
['a', 'b', 'c'].fill(7)  
// [7, 7, 7]  
new Array(3).fill(7)  
// [7, 7, 7]  
['a', 'b', 'c'].fill(7, 1, 2)  
// ['a', 7, 'c']  
```

　　上面代码表明，fill方法用于空数组的初始化非常方便。数组中已有的元素，会被全部抹去。
fill()方法还可以接受第二个和第三个参数，用于指定填充的起始位置和结束位置

```
['a', 'b', 'c'].fill(7, 1, 2)
// ['a', 7, 'c']
```

## 5. entries() ， keys() 和 values()

ES6 提供三个新的方法 —— entries()，keys()和values() —— 用于遍历数组。它们都返回一个遍历器对象，可以用**for...of循环**进行遍历，唯一的区别是**keys()是对键名的遍历、values()是对键值的遍历，entries()是对键值对的遍历。**

```
for (let index of ['a', 'b'].keys()) {  
    console.log(index);  
}  
// 0  
// 1  
for (let elem of ['a', 'b'].values()) {  
    console.log(elem);  
}  
// 'a'  
// 'b'  
for (let [index, elem] of ['a', 'b'].entries()) {  
    console.log(index, elem);  
}  
// 0 "a"  
// 1 "b"  
```

如果不使用for...of循环，可以手动调用遍历器对象的**next方法**，进行遍历。

```
let letter = ['a', 'b', 'c'];  
let entries = letter.entries();  
console.log(entries.next().value); // [0, 'a']  
console.log(entries.next().value); // [1, 'b']  
console.log(entries.next().value); // [2, 'c']  
```

## 6. includes()

ES5中，我们常用数组的indexOf方法，检查是否包含某个值。**indexOf方法有两个缺点**，一是不够语义化，它的含义是找到参数值的第一个出现位置，所以要去比较是否不等于 -1 ，表达起来不够直观。二是，它内部使用严格相当运算符（ === ）进行判断，这会导致对NaN的误判。

```
[NaN].indexOf(NaN)  
// -1  
includes使用的是不一样的判断算法，就没有这个问题。  
[NaN].includes(NaN)  
// true 
```

Array.prototype.includes方法返回一个**布尔值**，表示某个数组是否包含给定的值，与字符串的includes方法类似。该方法属于 ES7 ，但 Babel 转码器已经支持。

```
[1, 2, 3].includes(2); // true  
[1, 2, 3].includes(4); // false  
[1, 2, NaN].includes(NaN); // true  
```

该方法的**第二个参数表示搜索的起始位置**，默认为 0 。如果第二个参数为负数，则表示倒数的位置，如果这时它大于数组长度（比如第二个参数为 -4 ，但数组长度为 3 ），则会重置为从 0 开始。

```
[1, 2, 3].includes(3, 3); // false  
[1, 2, 3].includes(3, -1); // true  
```

下面代码用来检查当前环境是否支持该方法，如果不支持，部署一个简易的替代版本。

```
const contains = (() =>  
Array.prototype.includes  
    ? (arr, value) => arr.includes(value)  
    : (arr, value) => arr.some(el => el === value)  
)();  

contains(["foo", "bar"], "baz"); // => false  
```

另外， Map 和 Set 数据结构有一个has方法，需要注意与includes区分。
Map 结构的has方法，是用来查找**键名**的，比如Map.prototype.has(key)、WeakMap.prototype.has(key)、Reflect.has(target, propertyKey)。
Set 结构的has方法，是用来查找**值**的，比如Set.prototype.has(value)、WeakSet.prototype.has(value)。

## 7. 数组的空位

数组的空位指，数组的某一个位置没有任何值。比如，Array构造函数返回的数组都是空位。

注意，空位不是undefined，一个位置的值等于undefined，依然是有值的。空位是没有任何值，in运算符可以说明这一点。

```
0 in [undefined, undefined, undefined] // true
0 in [, , ,] // false
```

　　上面代码说明，第一个数组的 0 号位置是有值的，第二个数组的 0 号位置没有值。

ES5 对空位的处理，已经很不一致了，大多数情况下会忽略空位。
　　forEach() ,  filter() ,  every() 和some()都会跳过空位。
　　map()会跳过空位，但会保留这个值
　　join()和toString()会将空位视为undefined，而undefined和null会被处理成空字符串。

```
// forEach方法
[,'a'].forEach((x,i) => console.log(i)); // 1

// filter方法
['a',,'b'].filter(x => true) // ['a','b']

// every方法
[,'a'].every(x => x==='a') // true

// some方法
[,'a'].some(x => x !== 'a') // false

// map方法
[,'a'].map(x => 1) // [,1]

// join方法
[,'a',undefined,null].join('#') // "#a##"

// toString方法
[,'a',undefined,null].toString() // ",a,,"
```

ES6则是明确将空位转为undefined。

```
//Array.from方法会将数组的空位，转为undefined，也就是说，这个方法不会忽略空位。  
Array.from(['a',,'b'])  // [ "a", undefined, "b" ]  

//扩展运算符（...）也会将空位转为undefined。  
[...['a',,'b']]  // [ "a", undefined, "b" ]  

//copyWithin()会连空位一起拷贝。  
[,'a','b',,].copyWithin(2,0) // [,"a",,"a"]  

//fill()会将空位视为正常的数组位置。  
new Array(3).fill('a') // ["a","a","a"]  

//for...of循环也会遍历空位。  
let arr = [, ,];  
for (let i of arr) {  
    console.log(1);  
}  
// 1  
// 1  
//上面代码中，数组arr有两个空位，for...of并没有忽略它们。如果改成map方法遍历，空位是会跳过的。  

//entries()、keys()、values()、find()和findIndex()会将空位处理成undefined。  
// entries()  
[...[,'a'].entries()] // [[0,undefined], [1,"a"]]  
// keys()  
[...[,'a'].keys()] // [0,1]  
// values()  
[...[,'a'].values()] // [undefined,"a"]  
// find()  
[,'a'].find(x => true) // undefined  
// findIndex()  
[,'a'].findIndex(x => true) // 0  
//由于空位的处理规则非常不统一，所以建议避免出现空位。
```

