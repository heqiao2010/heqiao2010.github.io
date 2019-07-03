---
layout:     post
title:      "Java诊断工具Arthas之watch命令"
subtitle:   " \"Arthas阿尔沙斯\""
date:       2019-07-01 18:00:00
author:     "HQ"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - Arthas
---

>Arthas是一个开元的Java诊断工具,详见:https://alibaba.github.io/arthas/index.html. 今天第一次在项目中排查问题使用到它,发现其功能确实很强大.这里记录一下watch命令的使用.

### 安装
安装JDK然后以jar包的形式运行即可.
```
wget https://alibaba.github.io/arthas/arthas-boot.jar
java -jar arthas-boot.jar
```

### 诊断方法调用

通过Arthas的watch方法可以在没有打印日志的情况下,看到方法的入参和返回值.这点在
```
$ sc *Math*
demo.MathGame
io.netty.util.internal.MathUtil
java.lang.Math
Affect(row-cnt:3) cost in 17 ms.
$ sm demo.MathGame*
demo.MathGame <init>()V
demo.MathGame primeFactors(I)Ljava/util/List;
demo.MathGame main([Ljava/lang/String;)V
demo.MathGame run()V
demo.MathGame print(ILjava/util/List;)V
Affect(row-cnt:5) cost in 9 ms.
```


