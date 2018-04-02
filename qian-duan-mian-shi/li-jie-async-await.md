# 理解 async/await

`async`函数是`Generator`函数的语法糖。

想较于 Generator，`Async` 函数的改进在于下面四点：

* **内置执行器**。Generator 函数的执行必须依靠执行器，而 `Aysnc` 函数自带执行器，调用方式跟普通函数的调用一样 
* **更好的语义**。`async` 和 `await` 相较于 `*` 和 `yield` 更加语义化 
* **更广的适用性**。`co` 模块约定，`yield` 命令后面只能是 Thunk 函数或 Promise对象。而 `async` 函数的 `await`命令后面则可以是 Promise 或者 原始类型的值（Number，string，boolean，但这时等同于同步操作） 
* **返回值是 Promise**。`async` 函数返回值是 Promise 对象，比 Generator 函数返回的 Iterator 对象方便，可以直接使用 `then()` 方法进行调用

async用于定义一个异步函数，该函数返回一个Promise。

### async函数的异常

```
let sayHi = async functionsayHi(){
    throw new Error('出错了');
}
sayHi().then(result=> {
  console.log(result);
}).catch(err=> {
    console.log(err.message);   //出错了
});

```

await等待的虽然是promise对象，但不必写`.then(..)`，直接可以得到返回值。

既然`.then(..)`不用写了，那么`.catch(..)`也不用写，可以直接用标准的`try catch`语法捕捉错误。

await看起来就像是同步代码，所以可以理所当然的写在`for`循环里，不必担心以往需要`闭包`才能解决的问题。

值得注意的是，`await`必须在`async函数的上下文中`的。

