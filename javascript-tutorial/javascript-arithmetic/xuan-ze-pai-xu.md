# 选择排序

步骤如下：

1.从数组的开头起，**将第一个元素和其他所有元素都进行一次比较，选择出最小的元素放在数组的第一个位置**。

2.然后再从第二个元素开始，将第二个元素和除第一个之外的所有元素进行一次比较，选择出最小的元素放在数组的第二个位置。

3.对后面的第三，第四……的元素分别重复上面的步骤，知道所有的数据完成排序。

代码描述如下：

```js
function selectSort(arr){
    var minIndex;//定义minIndex变量用于存储每一趟比较时的最小数的下标
    for(var i=0; i<arr.length; i++){
        minIndex = i;
        for(var j=i+1; j<arr.length; j++){
           if(arr[minIndex]>arr[j]){
               minIndex = j;
           }
        }
        //每轮比较后若arr[i]不是我们需要的最小那个数，则进行交换
        if(minIndex!=i){
           var temp = arr[i];
            arr[i] = arr[minIndex];
            arr[minIndex] = temp;
        }
    }
}
 //测试
 var testArr = [35,22,1,56,88,25];
 selectSort(testArr);
 console.log(testArr); //输出1,22,25,35,56,88
```

总结：

1. 选择第一个为最小下标。
2. 循环该数组从该下标往右寻找比当前值还小的下标。
3. 交换位置。





