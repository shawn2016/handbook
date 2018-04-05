

* `CSS`伪类用于向某些选择器添加特殊的效果。
* css伪元素用于将特殊的效果添加到某些选择器。

## 伪类种类 {#articleHeader0}

### ![](http://segmentfault.com/img/bVcccn) 

### 伪元素种类

![](http://segmentfault.com/img/bVccco)

## 区别 {#articleHeader2}

这里用伪类 `:first-child` 和伪元素 `:first-letter` 来进行比较。

```
p>i:first-child {color: red}
<p>
    <i>first</i>
    <i>second</i>
</p>

```

![img](http://segmentfault.com/img/bVcccr) //伪类 `:first-child` 添加样式到第一个子元素
如果我们不使用伪类，而希望达到上述效果，可以这样做：

```
.first-child {color: red}
<p>
    <i class="first-child">first</i>
    <i>second</i>
</p>

```

即我们给第一个子元素添加一个类，然后定义这个类的样式。那么我们接着看看为元素：

```
p:first-letter {color: red}
<p>I am stephen lee.</p>

```

![img](http://segmentfault.com/img/bVcccs) //伪元素 `:first-letter` 添加样式到第一个字母
那么如果我们不使用伪元素，要达到上述效果，应该怎么做呢？

```
.first-letter {color: red}
<p><span class='first-letter'>I</span> am stephen lee.</p>

```

即我们给第一个字母添加一个 `span`，然后给 `span` 增加样式。
两者的区别已经出来了。那就是：

> 伪类的效果可以通过添加一个实际的类来达到，而伪元素的效果则需要通过添加一个实际的元素才能达到，这也是为什么他们一个称为伪类，一个称为伪元素的原因。

## 总结

伪元素和伪类之所以这么容易混淆，是因为他们的效果类似而且写法相仿，但实际上 `css3` 为了区分两者，已经明确规定了伪类用一个冒号来表示，而伪元素则用两个冒号来表示。

```
:Pseudo-classes
::Pseudo-elements

```

但因为兼容性的问题，所以现在大部分还是统一的单冒号，但是抛开兼容性的问题，我们在书写时应该尽可能养成好习惯，区分两者。

