# 5个数组Array方法:

## indexOf、filter、forEach、map、reduce使用实例

在ES5中，一共有9个Array方法

Array.prototype.indexOf

Array.prototype.lastIndexOf

Array.prototype.every

Array.prototype.some

Array.prototype.forEach

Array.prototype.map

Array.prototype.filter

Array.prototype.reduce

Array.prototype.reduceRight

**indexOf**

indexOf\(\)方法返回在该数组中第一个找到的元素位置，如果它不存在则返回-1。

不使用indexOf时

```
var arr = ['apple','orange','pear'],
found = false;

for(var i= 0, l = arr.length; i< l; i++){
if(arr[i] === 'orange'){
found = true;
}
}

console.log("found:",found);
```

使用后

```
var arr = ['apple','orange','pear'];

console.log("found:", arr.indexOf("orange") != -1);
```

**filter**

该filter\(\)方法创建一个新的匹配过滤条件的数组。

不用 filter\(\) 时

```
var arr = [
  {"name":"apple", "count": 2},
  {"name":"orange", "count": 5},
  {"name":"pear", "count": 3},
  {"name":"orange", "count": 16},
];

var newArr = [];

for(var i= 0, l = arr.length; i< l; i++){
  if(arr[i].name === "orange" ){
newArr.push(arr[i]);
}
}

console.log("Filter results:",newArr);
```

用了 filter\(\):

```
var arr = [
  {"name":"apple", "count": 2},
  {"name":"orange", "count": 5},
  {"name":"pear", "count": 3},
  {"name":"orange", "count": 16},
];

var newArr = arr.filter(function(item){
  return item.name === "orange";
});


console.log("Filter results:",newArr);
```

**forEach\(\)**

forEach为每个元素执行对应的方法

```
var arr = [1,2,3,4,5,6,7,8];

// Uses the usual "for" loop to iterate
for(var i= 0, l = arr.length; i< l; i++){
console.log(arr[i]);
}

console.log("========================");

//Uses forEach to iterate
arr.forEach(function(item,index){
console.log(item);
});
```

**map\(\)**

map\(\)对数组的每个元素进行一定操作（映射）后，会返回一个新的数组，

不使用map

```
var oldArr = [{first_name:"Colin",last_name:"Toh"},{first_name:"Addy",last_name:"Osmani"},{first_name:"Yehuda",last_name:"Katz"}];
 
function getNewArr(){
   
  var newArr = [];
   
  for(var i= 0, l = oldArr.length; i< l; i++){
    var item = oldArr[i];
    item.full_name = [item.first_name,item.last_name].join(" ");
    newArr[i] = item;
  }
   
  return newArr;
}
 
console.log(getNewArr());
```

使用map后

```
var oldArr = [{first_name:"Colin",last_name:"Toh"},{first_name:"Addy",last_name:"Osmani"},{first_name:"Yehuda",last_name:"Katz"}];
 
function getNewArr(){
     
  return oldArr.map(function(item,index){
    item.full_name = [item.first_name,item.last_name].join(" ");
    return item;
  });
   
}
 
console.log(getNewArr());
```

**reduce\(\)**

reduce\(\)可以实现一个累加器的功能，将数组的每个值（从左到右）将其降低到一个值。

说实话刚开始理解这句话有点难度，它太抽象了。

场景： 统计一个数组中有多少个不重复的单词

不使用reduce时

```
var arr = ["apple","orange","apple","orange","pear","orange"];
 
function getWordCnt(){
  var obj = {};
   
  for(var i= 0, l = arr.length; i< l; i++){
    var item = arr[i];
    obj[item] = (obj[item] +1 ) || 1;
  }
   
  return obj;
}
 
console.log(getWordCnt());
```

使用reduce\(\)后

```
var arr = ["apple","orange","apple","orange","pear","orange"];
 
function getWordCnt(){
  return arr.reduce(function(prev,next){
    prev[next] = (prev[next] + 1) || 1;
    return prev;
  },{});
}
 
console.log(getWordCnt());
```

让我先解释一下我自己对reduce的理解。reduce\(callback, initialValue\)会传入两个变量。回调函数\(callback\)和初始值\(initialValue\)。假设函数它有个传入参数，prev和next,index和array。prev和next你是必须要了解的。

一般来讲prev是从数组中第一个元素开始的，next是第二个元素。但是当你传入初始值\(initialValue\)后，第一个prev将是initivalValue，next将是数组中的第一个元素。

比如：

```
/*
* 二者的区别，在console中运行一下即可知晓
*/
 
var arr = ["apple","orange"];
 
function noPassValue(){
  return arr.reduce(function(prev,next){
    console.log("prev:",prev);
    console.log("next:",next);
     
    return prev + " " +next;
  });
}
function passValue(){
  return arr.reduce(function(prev,next){
    console.log("prev:",prev);
    console.log("next:",next);
     
    prev[next] = 1;
    return prev;
  },{});
}
 
console.log("No Additional parameter:",noPassValue());
console.log("----------------");
console.log("With {} as an additional parameter:",passValue());
```





