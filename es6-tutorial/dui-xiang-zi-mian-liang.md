## 对象字面量

ES6针对对象字面量做了许多简化语法的处理。

* 当属性与值的变量同名时。

```
const name = 'Jane';
const age = 20

// es6
const person = {
  name,
  age
}

// es5
var person = {
  name: name,
  age: age
};
```

那么这种方式在任何地方都可以使用，比如在一个模块对外提供接口时

```
const getName = () => person.name;
const getAge = () => person.age;

// commonJS的方式
module.exports = { getName, getAge }

// ES6 modules的方式
export default { getName, getAge  }
```

* 除了属性之外，对象字面量写法中的方法也可以有简写方式。

```
// es6
const person = {
  name,
  age,
  getName() { // 只要不使用箭头函数，this就还是我们熟悉的this
    return this.name
  }
}

// es5
var person = {
  name: name,
  age: age,
  getName: function getName() {
    return this.name;
  }
};
```

* 在对象字面量中可以使用中括号作为属性，表示属性也能是一个变量了。

```
const name = 'Jane';
const age = 20

const person = {
  [name]: true,
  [age]: true
}
```

在ant-design的源码实现中，就大量使用了这种方式来拼接当前元素的className，例如:

    let alertCls = classNames(prefixCls, {
          [`${prefixCls}-${type}`]: true,
          [`${prefixCls}-close`]: !this.state.closing,
          [`${prefixCls}-with-description`]: !!description,
          [`${prefixCls}-no-icon`]: !showIcon,
          [`${prefixCls}-banner`]: !!banner,
     }, className);

> ant-design是一个认可度非常高的UI组件库，官方使用react的方式进行了实现，除此之外，还有vue也有对应的实现，有兴趣的同学可以去他们的官网了解学习。[https://ant.design/index-cn](https://ant.design/index-cn)



