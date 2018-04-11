### 不定宽度

#### 让4周的拉力均匀-常用

```
      position:absolute;
      top:0; /* 四周拉力相同 */
      right:0; /* 四周拉力相同 */
      bottom:0; /* 四周拉力相同 */
      left:0; /* 四周拉力相同 */
      margin:auto; /* 再设置 marign 自动 */
      width: 20px;
      height: 20px;
```

#### c3的属性，移动自己大小的一半

```
      width: 20px;
      height: 20px;
      position:absolute;
      top:50%;
      left:50%;
      transform:translate(-50%,-50%);
      margin:auto; /* 再设置 marign 自动 */
```

### 知道自身高度的情况下，使用负边距，-margin自身高度的一半

```
      width: 20px;
      height: 20px;
      position:absolute;
      left:50%;
      top:50%;
      margin-left:-10px; /* 知道自己大小的情况，自身高度的一半 */
      margin-top:-10px; /* 知道自己大小的情况，自身高度的一半 */
```

