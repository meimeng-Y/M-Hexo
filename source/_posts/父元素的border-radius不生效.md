---
title:  父元素的border-radius不生效
date: 2022-09-8
tags:
- 小问题
categories:
- [小问题]
---
# 父元素的border-radius不生效
## 问题
>设置了父元素的border-radius，但不生效
>

## 解决
1. 通过 **设置overflow: hidden;** 生效了
2. 有**hover**效果的情况下再次失效了
3. 但是可以通过**设置transform属性**来解决

>
>在父元素上设置了border-radius，但不生效。
>可以在父元素上再设置：overflow: hidden;。
>部分浏览器不兼容这种方式
>可以在父元素上再增加一个transform属性

```css
.parent {
  transform: translate(0,0);
  /* 或 */
  transform: scale(0);
  /* 或 */
  transform: rotate(0deg);
}
```

