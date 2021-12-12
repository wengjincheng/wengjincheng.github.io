---
title: "TypeScript 开发问题和解决方法"
date: 2021-12-11T09:02:05+08:00
draft: false
categories:
  - TypeScript
tags:
  - TypeScript
---

*本文记录本人在日常工作中遇到的TypeScript的小问题*

### 关于 extends 已有 interface 后需要忽略一些不需要参数的问题

假如你有一个这样的interface:

```TypeScript
    interface A {
        name: string,
        age: number,
        job: string,
    }
```

你需要extends 这个 A 类型 到 B类型：

```TypeScript
    interface B extends A {}
```
但你不需要其中的job，那么怎么办？这么办：

```TypeScript
    interface B extends Omit<A, 'job'> {}
```

----