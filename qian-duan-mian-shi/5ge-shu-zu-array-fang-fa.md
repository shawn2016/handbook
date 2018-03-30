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

























