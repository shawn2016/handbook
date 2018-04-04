### 原文链接：[https://segmentfault.com/a/1190000006599500](https://segmentfault.com/a/1190000006599500) {#articleHeader0}

### [http://hcysun.me/2017/03/03/Vue%E6%BA%90%E7%A0%81%E5%AD%A6%E4%B9%A0](http://hcysun.me/2017/03/03/Vue%E6%BA%90%E7%A0%81%E5%AD%A6%E4%B9%A0) {#articleHeader0}

### 几种实现双向绑定的做法 {#articleHeader0}

目前几种主流的mvc\(vm\)框架都实现了单向数据绑定，而我所理解的双向数据绑定无非就是在单向绑定的基础上给可输入元素（input、textare等）添加了change\(input\)事件，来动态修改model和 view，并没有多高深。所以无需太过介怀是实现的单向或双向绑定。

实现数据绑定的做法有大致如下几种：

> 发布者-订阅者模式（backbone.js）
>
> 脏值检查（angular.js）
>
> 数据劫持（vue.js）

**发布者-订阅者模式:**一般通过sub, pub的方式实现数据和视图的绑定监听，更新数据方式通常做法是`vm.set('property', value)`，这里有篇文章讲的比较详细，有兴趣可点[这里](http://www.html-js.com/article/Study-of-twoway-data-binding-JavaScript-talk-about-JavaScript-every-day)

这种方式现在毕竟太low了，我们更希望通过`vm.property = value`这种方式更新数据，同时自动更新视图，于是有了下面两种方式

**脏值检查:**angular.js 是通过脏值检测的方式比对数据是否有变更，来决定是否更新视图，最简单的方式就是通过`setInterval()`定时轮询检测数据变动，当然Google不会这么low，angular只有在指定的事件触发时进入脏值检测，大致如下：

* DOM事件，譬如用户输入文本，点击按钮等。\( ng-click \)

* XHR响应事件 \( $http \)

* 浏览器Location变更事件 \( $location \)

* Timer事件\( $timeout , $interval \)

* 执行 $digest\(\) 或 $apply\(\)

**数据劫持:**vue.js 则是采用数据劫持结合发布者-订阅者模式的方式，通过`Object.defineProperty()`来劫持各个属性的`setter`，`getter`，在数据变动时发布消息给订阅者，触发相应的监听回调。

