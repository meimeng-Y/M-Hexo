---
title:  vue父子组件传值
date: 2022-09-27
tags:
- vue
categories:
- [VUE,VUE2]
---

父子组件传值通过 **$emit和props**
### 构建父子组件
假设父组件为：
```html
<app></app>
```
里面嵌套了子组件：
```html
<app>
	<child></child>
</app>
```
假设子组件的内容为：
```html
<div>
	<p>我是子组件</p>
	<p>{{message}}</p>
	<button></button>
</div>
```

### 子组件向父组件传值
> **子组件向父组件传值利用的是 $emit**
> **点击按钮时将子组件中 message 的内容传递给父组件**

#### 在子组件中
1. 为 button 绑定 click 事件
```html
<button @click="submit()"></button>
```
2. 当触发点击事件时,在函数中使用 **$emit**
```html
submit () {
	this.$emit('childFn',this.message)
}
```
其中 **$emit** 中的两个参数，第一个为父组件的事件，第二个为想要传的值
#### 在父组件中
```html
<app>
	<child @childFn="parentFn"></child>
</app>
```
> childFn是子组件 **$emit** 的第一个参数
> parentFn 是父组件要触发的方法
> 

在父组件中创建 parentFn() 函数，写入传的参数，获取子组件中 message 的值
```js
parentFn (message) {
	//写逻辑
}
```
 >parentFn的参数 message 就是子组件的内容
 >

### 父组件向子组件传值
父组件向子组件传值利用的是 **props**
#### 在父组件中
为嵌套的子组件绑定传的值：
```html
<app>
	<child :childMessage="parentMessage"></child>
</app>
```
> childMessage 是子组件要接收的形参，可任意取名
> parentMessage 是传参的具体的值：例如

```js
export default {
  data () {
  	return {
		parentMessage: '我是来自父组件的值'
	}
  }
```
#### 在子组件中
增加 props
```js
export default {
  props: ['childMessage'],
  data () {
  	return {
		...
	}
  }
```
> props 的值要与父组件的形参值要一样
> props 的形参可以直接使用
