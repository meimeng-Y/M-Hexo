---
title:  vue监听数组和对象的方法
date: 2022-09-15
tags:
- vue
categories:
- [VUE,VUE2]
---
# vue监听数组和对象的方法

```js
// 监听对象：
// numList: [1,2,3] //vue监听数组时只能监听到数组的长度变化
// oneObj: {name: 'aa', 'aeg': '11'}


// 第一种监听方式，使用deep深度监听。
// 不推荐，性能消耗很大
watch: {
  oneObj: function(newVal, oldVal) {
      // 处理语句
    },
    deep: True
}


// 第二种方式，利用计算属性
computed: {
    name: function() {
      return this.oneObj.name
    }
},
//监听计算属性name
watch: {
    name: function(newVal, oldVal) {
      // 处理语句
    }
}

// 三，直接监听对象中的属性
watch: {
    'oneObj.name': function(newVal, oldVal) {
      // 处理语句
  }
}
```