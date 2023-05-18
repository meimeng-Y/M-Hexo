---
title:  SpringBoot使用给静态变量注入值
date: 2022-09-23
tags:
- SpringBoot
- java
- jar
categories:
- [SpringBoot]
---

# SpringBoot使用给静态变量注入值
**SpringBoot中使用@Value()只能给普通变量注入值，不能直接给静态变量赋值**
## 方案一：
若要给静态变量赋值，可以使用**<u>set()</u>**方法，其中需要在**<u>类上加入@Component注解</u>**，方法名（和参数名）可以任意命名
```java
@Component
public class test {
    public static String name;
    
    @Autowired(required = false)
    @Value(value="${具体的值：默认值}")
    public void setName( String name) {
        test.name = name;
    }
}
```
## 方案二（未尝试过）
可以使用**@ConfigurationProperties**注解代替

1. 前缀要写合适
2. 方法名（例如seName）必须和属性保持一致,写为其他会注入失败
3. 类上加入@Component注解
