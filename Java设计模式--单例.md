---
title: 'Java设计模式--单例'
href: '2018-07-31-design-pattern-singleton'
categories: 后端
date: 2018-07-31 17:18:21
tags:
  - Java设计模式
keywords: Java, 设计模式, 单例模式, Singleton
---
一个类有且仅有一个实例，并且提供了一个全局的访问点
<!--more-->
# 概述
```java
public class Singleton {

    private static Singleton uniqueInstance;

    private Singleton() {
    }

    public static Singleton getUniqueInstance() {
        if (uniqueInstance == null) {
            uniqueInstance = new Singleton();
        }
        return uniqueInstance;
    }
}
```

# 优点

# 缺点

# 应用场景

# 实现


