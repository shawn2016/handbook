# **插入排序**

插入排序的思想非常简单，主要如下：

步骤：

1.首先将数组第1个数看成是一个有序序列。

2.将数组的第2个数按照关键字大小插入到这个有序序列中，插入后得到了一包含两个数的有序序列。

3.接下来再重复上面的步骤将第3，第4……第n-1个数分别插入到该有序序列中，最终得到一个包含n个数的有序序列。

代码描述：

```js
function insertSort(arr){
  var temp;  //temp变量用于临时存储待插入元素
  for(var i=1; i<arr.length; i++){
     temp = arr[i];
      //从前往后查找插入位置
     for(var j=i; j>0&&arr[j-1]>temp; j--){
         arr[j]=arr[j-1]; //将大于temp的arr[j]元素后移
     }
      arr[j]=temp;
  }
}
 //测试
 var testArr = [35,22,1,56,88,25];
 insertSort(testArr);
 alert(testArr); //输出1,22,25,35,56,88
```



