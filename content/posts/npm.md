---
title: "NPM 开发相关"
date: 2021-11-02T23:02:05+08:00
draft: false
categories:
  - NPM
tags:
  - NPM
---

## NPM源相关代理/镜像

- 切换为淘宝源 

``` bash
npm config set registry https://registry.npm.taobao.org
```

- 临时使用淘宝源

``` bash
npm install xxxx --save --registry https://registry.npm.taobao.org
```

- 切换为官方源

``` bash
npm config set registry https://registry.npmjs.org/
```

- 查看当前使用源

``` bash
npm config get registry
```