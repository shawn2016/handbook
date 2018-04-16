## exports 和 module.exports 的区别

明白了上述例子后，我们只需知道三点就知道 exports 和 module.exports 的区别了：

1. module.exports 初始值为一个空对象 {}
2. exports 是指向的 module.exports 的引用
3. require\(\) 返回的是 module.exports 而不是 exports



