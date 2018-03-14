## [绑定 HTML Class](https://cn.vuejs.org/v2/guide/class-and-style.html#%E7%BB%91%E5%AE%9A-HTML-Class) {#绑定-HTML-Class}

### [对象语法](https://cn.vuejs.org/v2/guide/class-and-style.html#%E5%AF%B9%E8%B1%A1%E8%AF%AD%E6%B3%95) {#对象语法}

我们可以传给`v-bind:class`一个对象，以动态地切换 class：

```html
<div v-bind:class="{ active: isActive }"></div>
```

上面的语法表示`active`这个 class 存在与否将取决于数据属性`isActive`

**`v-bind:class`指令也可以与普通的 class 属性共存**

```html
<div class="static"
     v-bind:class="{ active: isActive, 'text-danger': hasError }">
</div>
```

### [数组语法](https://cn.vuejs.org/v2/guide/class-and-style.html#%E6%95%B0%E7%BB%84%E8%AF%AD%E6%B3%95) {#数组语法}

我们可以把一个数组传给`v-bind:class`，以应用一个 class 列表

```html
<div v-bind:class="[activeClass, errorClass]"></div>
```

```js
data: {
  activeClass: 'active',
  errorClass: 'text-danger'
}
```

渲染为：

```html
<div class="active text-danger"></div>
```

如果你也想根据条件切换列表中的 class，可以用三元表达式：

```html
<div v-bind:class="[isActive ? activeClass : '', errorClass]"></div>
```

```html
<div v-bind:class="[{ active: isActive }, errorClass]"></div>
```

### [用在组件上](https://cn.vuejs.org/v2/guide/class-and-style.html#%E7%94%A8%E5%9C%A8%E7%BB%84%E4%BB%B6%E4%B8%8A) {#用在组件上}

例如，如果你声明了这个组件：

```
Vue.component('my-component', {
  template: '<p class="foo bar">Hi</p>'
})
```

然后在使用它的时候添加一些 class：

```
<my-component class="baz boo"></my-component>
```

HTML 将被渲染为:

```
<p class="foo bar baz boo">Hi</p>
```

## [绑定内联样式](https://cn.vuejs.org/v2/guide/class-and-style.html#%E7%BB%91%E5%AE%9A%E5%86%85%E8%81%94%E6%A0%B7%E5%BC%8F) {#绑定内联样式}

### [对象语法](https://cn.vuejs.org/v2/guide/class-and-style.html#%E5%AF%B9%E8%B1%A1%E8%AF%AD%E6%B3%95-1) {#对象语法-1}

```
<div v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }"></div>
```

```
data: {
  activeColor: 'red',
  fontSize: 30
}
```

### [数组语法](https://cn.vuejs.org/v2/guide/class-and-style.html#%E6%95%B0%E7%BB%84%E8%AF%AD%E6%B3%95-1) {#数组语法-1}

```
<div v-bind:style="[baseStyles, overridingStyles]"></div>
```

### [自动添加前缀](https://cn.vuejs.org/v2/guide/class-and-style.html#%E8%87%AA%E5%8A%A8%E6%B7%BB%E5%8A%A0%E5%89%8D%E7%BC%80) {#自动添加前缀}

当`v-bind:style`使用需要添加[浏览器引擎前缀](https://developer.mozilla.org/zh-CN/docs/Glossary/Vendor_Prefix)的 CSS 属性时，如`transform`，Vue.js 会自动侦测并添加相应的前缀。





