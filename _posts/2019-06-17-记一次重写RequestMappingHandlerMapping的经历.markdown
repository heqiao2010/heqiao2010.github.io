---
layout:     post
title:      "记一次重写RequestMappingHandlerMapping的经历"
subtitle:   " \"Spring boot开发日常操作\""
date:       2019-06-1７ 18:00:00
author:     "HQ"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags:
    - Spring
---

>近期公司的产品做了一次安全审查，发现后端提供的接口有**不安全的Http方法**漏洞。不安全的HTTP方法一般包括：TRACE、PUT、DELETE、COPY 等。其中最常见的为TRACE方法可以回显服务器收到的请求，主要用于测试或诊断，恶意攻击者可以利用该方法进行跨站跟踪攻击（即XST攻击），从而进行网站钓鱼、盗取管理员cookie等。

## 原因分析
引起这个问题的原因其实很简单，因为开发人员开发接口的时候偷懒没有指定RequestMapping中的method属性导致的。没有指定method则系统会默认支持除了TRACE之外的其他７中方式所以，你没有看错，这就是我要重写的RequestMappingHandlerMapping原因。

## 分析
网关服务采用Spring boot开发，那么我们可以从
```
org.springframework.boot.autoconfigure.web.WebMvcAutoConfiguration
```
待续...