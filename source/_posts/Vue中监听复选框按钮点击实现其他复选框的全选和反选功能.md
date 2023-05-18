---
title:  Vue中监听复选框按钮点击实现其他复选框的全选和反选功能
date: 2022-09-16
tags:
- vue
- Elementui
categories:
- [VUE,VUE2]
---
# Vue中监听复选框按钮点击实现其他复选框的全选和反选功能
```html
<div class="monitoring_checkall">

    <el-checkbox border 
                 class="checkall"
                 v-model="allCheck"
                 @change="changeAllChecked(allCheck)">全选
    </el-checkbox>
  </div>
  <div class="group_box">
    <div class="node_group" 
         v-for="(item, index) in nodeStyle" 
         :key="index" >
      <div :style="item" class="node_group_checked">
      </div>
      <el-checkbox label="item" 
                   border 
                   class="node"
                   :key="index"
                   v-model="item.isCheck">{{item.name}}
      </el-checkbox>
    </div>
  </div>
```

>>data中的数据
```js
data() {
return {
  allCheck: false,
  nodeStyle: [
    { name: '节点1', isCheck: false },
    { name: '节点2', isCheck: false },
    { name: '节点3', isCheck: false }
  ],
}
}
```
> methods里面绑定的方法，forEach遍历实现全选和反选的功能
> 
```js
//全选和反选的方法
changeAllChecked(allCheck) {
  console.log(allCheck)
    if (!allCheck) {
    this.nodeStyle.forEach(function (item) {
      item.isCheck = false;
    });
  } else {
    this.nodeStyle.forEach(function (item) {
      item.isCheck = true;
    });
  }
}
```

> watch监听判断全选按钮的选择状态
```js
watch: {
    nodeStyle: {
        handler(value) {
            var count = 0;
            for (var i=0; i<value.length; i++){
                if (value[i].isCheck == true){
                //统计选择的个数
                    count ++;
                }
            }
            if (count == value.length){
                this.allCheck = true;
            } else {
                this.allCheck = false;
            }
        },
        deep: true
    },
  },
```
