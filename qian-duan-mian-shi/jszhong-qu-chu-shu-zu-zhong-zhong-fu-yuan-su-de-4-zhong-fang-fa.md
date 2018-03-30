

## Js中去除数组中重复元素的4种方法

方法一：

**判断当前数组下标为i的元素是否已经保存到临时数组**  

```
Array.prototype.method1 = function(){  
            var arr[];    //定义一个临时数组  
            for(var i = 0; i < this.length; i++){    //循环遍历当前数组  
                //判断当前数组下标为i的元素是否已经保存到临时数组  
                //如果已保存，则跳过，否则将此元素保存到临时数组中  
                if(arr1.indexOf(this[i]) == -1){  
                    arr.push(this[i]);  
                }  
            }  
            return arr;  
        }  
```

方法2：

建立临时hash表，判断这个hash表是否有该元素，最后push到数组。

```
  Array.prototype.method2 = function(){  
            var h{};    //定义一个hash表  
            var arr[];  //定义一个临时数组  
              
            for(var i = 0; i < this.length; i++){    //循环遍历当前数组  
                //对元素进行判断，看是否已经存在表中，如果存在则跳过，否则存入临时数组  
                if(!h[this[i]]){  
                    //存入hash表  
                    h[this[i]] = true;  
                    //把当前数组元素存入到临时数组中  
                    arr.push(this[i]);  
                }  
            }  
            return arr;  
        }  
```

