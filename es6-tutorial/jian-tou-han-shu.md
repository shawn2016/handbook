### 箭头函数

之前我说ES6颠覆了js的编码习惯，箭头函数的使用占了很大一部分。

首先是写法上的不同:

```
// es5
var fn = function(a, b) {
    return a + b;
}
// es6 箭头函数写法，当函数直接被return时，可以省略函数体的括号
const fn = (a, b) => a + b;

// es5
var foo = function() {
    var a = 20；
    var b = 30;
    return a + b;
}

// es6
const foo = () => {
   const a = 20;
   const b = 30;
   return a + b;
}
```

> 箭头函数可以替换函数表达式，但是不能替换函数声明

其次还有一个至关重要的一点，那就是箭头函数中，没有this。**如果你在箭头函数中使用了this，那么该this一定就是外层的this。**

**也正是因为箭头函数中没有this，**因此我们也就无从谈起用call/apply/bind来改变this指向。记住这个特性，能让你在react组件之间传值时少走无数弯路。

```
var person = {
    name: 'tom',
    getName: function() {
        return this.name;
    }
}

// 我们试图用ES6的写法来重构上面的对象
const person = {
    name: 'tom',
    getName: () => this.name
}

// 但是编译结果却是
var person = {
    name: 'tom',
    getName: function getName() {
        return undefined.name;
    }
};
```

> 在ES6中，会默认采用严格模式，因此this也不会自动指向window对象了，而箭头函数本身并没有this，因此this就只能是undefined，这一点，在使用的时候，一定要慎重慎重再慎重，不然踩了坑你都不知道自己错在哪！这种情况，如果你还想用this，就不要用使用箭头函数的写法。

```
// 可以稍做改动
const person = {
    name: 'tom',
    getName: function() {
        return setTimeout(() => this.name, 1000);
    }
}

// 编译之后变成
var person = {
    name: 'tom',
    getName: function getName() {
        var _this = this;  // 使用了我们在es5时常用的方式保存this引用

        return setTimeout(function () {
            return _this.name;
        }, 1000);
    }
};
```

先记住箭头函数的写法，并留意箭头函数中关于this的特殊性，更过实践与注意事项我们在封装react组件时再慢慢来感受。



