---
title:  CSS中Flex弹性盒子尺寸 
date: 2022-09-7
tags:
- css
- Flex
categories:
- [CSS]
---
# CSS中Flex弹性盒子尺寸
## 1.
父盒子有<u>**display:flex**</u>;父盒子<u>**有高度**</u>

子盒子<u>**有宽，有高**</u>

<u>**未对**</u>子盒子设置侧轴对齐方式=即采用默认值,align-self:stretch;

> 结果：子盒子大小为<u>**自身宽高大小**</u>
>> ![图片消失了!](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305181548684.png)

## 2. 
父盒子有<u>**display:flex**</u>;父盒子<u>**有高度**</u>

子盒子<u>**有宽，有高**</u>

<u>**对**</u>子盒子设置侧轴对齐方式align-self:center;

>结果：子盒子大小为<u>**自身宽高大小**</u>
>> ![图片消失了!](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305181550123.png)

## 3. 
父盒子有<u>**display:flex**</u>;父盒子有高度

子盒子<u>**有宽，无高**</u>

<u>**未对**</u>子盒子设置侧轴对齐方式=即采用默认值,align-self:stretch;

> 结果：子盒子<u>**高度**</u>在侧轴拉伸到<u>**和父盒子一样高**</u>
>> ![图片消失了!](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305181554188.png)

## 4.
父盒子有<u>**display:flex**</u>;父盒子<u>**有高度**</u>

子盒子<u>**有宽，无高**</u>

<u>**对子盒子设置侧轴对齐**</u>方式align-self:center;(该例子中只对第二个子级div设置)

> 结果：设置了侧轴对齐方式align-self:center;的<u>**子盒子**</u>高度<u>**和内容一样高**</u>（看第二个子级div盒子）
```html
    <!DOCTYPE html>
    <html lang="zh">
     
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title></title>
        <style>
            * {
                margin: 0;
                padding: 0;
            }
     
            .box {
                display: flex;
                height: 300px;
                margin: auto;
                border: 1px solid #000;
            }
     
            .box div {
                width: 100px;
                /* height: 100px; */
                background-color: pink;
            }
     
            .box div:nth-child(2) {
                align-self: center;
            }
        </style>
    </head>
     
    <body>
        <div class="box">
            <div>1</div>
            <div>2</div>
            <div>3</div>
        </div>
    </body>
     
    </html>
```
>> ![图片消失了!](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305181601614.png)

## 5.
父盒子有<u>**display:flex**</u>;父盒子<u>**有高度**</u>

子盒子<u>**无宽，无高**</u>

<u>**未对**</u>子盒子设置侧轴对齐方式=即采用默认值,align-self:stretch;

> 结果：子盒子<u>**高度**</u>在侧轴拉伸到和父盒子<u>**一样高**</u>，<u>**宽度和内容一样宽**</u>
> ![图片消失了!](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305181603562.png)


## 6.
父盒子有<u>**display:flex**</u>;父盒子<u>**有高度**</u>

子盒子<u>**无宽，无高**</u>

<u>**对子盒子设置侧轴对齐**</u>方式align-self:center;(该例子中只对第二个子级div设置)

> 结果：<u>**设置了侧轴对齐**</u>方式align-self:center;的<u>**子盒子高度和宽度和内容一样**</u>（看第二个子级div盒子）

```HTML
    <!DOCTYPE html>
    <html lang="zh">
     
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title></title>
        <style>
            * {
                margin: 0;
                padding: 0;
            }
     
            .box {
                display: flex;
                height: 300px;
                margin: auto;
                border: 1px solid #000;
            }
     
            .box div {
                /* width: 100px; */
                /* height: 100px; */
                background-color: pink;
            }
     
            .box div:nth-child(2) {
                align-self: center;
            }
        </style>
    </head>
     
    <body>
        <div class="box">
            <div>111</div>
            <div>222222</div>
            <div>3</div>
        </div>
    </body>
     
    </html>
```
>> ![图片消失了!](https://cdn.jsdelivr.net/gh/meimeng-Y/comments@main//imgs/202305181606008.png)
