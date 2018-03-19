## 函数默认参数

之前我们不能直接为函数指定默认参数，因此很多时候为了保证传入的参数具备一个默认值，我们常常使用如下的方法：

```
function add(x, y) {
    var x = x || 20;
    var y = y || 30;
    return x + y;
}

console.log(add()); // 50
```

> 这种方式并不是没有缺点，比如当我传入一个x值为false，这个时候任然会取到默认值，就不是我们的本意了。

来看看ES6的默认值写法：

```
function add(x = 20, y = 30) {
    return x + y;
}

console.log(add());

```

在实际开发中给参数添加适当的默认值，可以让我们对函数的参数类型有一个直观的认知。

```
const ButtonGroupProps = {
    size: 'normal',
    className: 'xxxx-button-group',
    borderColor: '#333'
}

export default function ButtonGroup(props = ButtonGroupProps) {
    ... ...
}
```



