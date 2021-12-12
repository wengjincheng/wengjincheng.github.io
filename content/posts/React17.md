---
title: "React 项目开发过程中的记录"
date: 2021-12-11T09:02:05+08:00
draft: false
categories:
  - React
tags:
  - React
  - Hooks
---

*本文记录本人在日常工作中遇到的React的小问题*

## React hooks

### 当需要更新完指定state后再处理有些函数（发起http请求等）

一般在class类的react项目中是这样写的：

```TypeScript
    setState({
        id: 2
    }, () => {
        // 这里处理一些函数或者其他操作
    })
```

到了Hooks的话，用的是 useState，需要换一种思路：

因为你所操作的函数或者其他操作是依赖这个state的，那么直接使用useEffect则可以，因为useEffect可以帮到相关依赖，当依赖的state更新，自动运行

```TypeScript
    // 初始化state
    const [id, setId] = useState<number>(0);
    const [name, setName] = useState<string>('');

    // 设置useEffect来确保当id更新时候一定会刷新name
    useEffect(() => {
        fetch('api').then((res) => {
            setName(res);
        })
    }, [id])
```
参考资料：

- https://stackoverflow.com/questions/54954091/how-to-use-callback-with-usestate-hook-in-react