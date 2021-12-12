---
title: "React单元测试-如何测试Ant-design的组件"
date: 2021-12-01T17:12:05+08:00
draft: false
categories:
  - Unit Test
tags:
  - Unit Test
---

**本章记录踩过的前端单元测试的坑**

### React项目中使用例如Ant-design的库后，如何测试？

比如一个表单页面，最常见的必须要测试表单的render、validation、以及提交。

但是使用Jest, React-testing-library的情况下来测试表单内容的填写以及提交会遇到Select组件的Options找不到的情况下

比如：

```JavaScript
userEvent.selectOptions(await findByPlaceholderText('Please select priority'),'A-Critical');
```

跑一下test 肯定会提示你'A-Critical'找不到

这里的解决方法是：Mock Antd使用的组件，这里就是Select

```JavaScript
// Mock Antd , including Select
jest.mock('antd', () => {
  const antd = jest.requireActual('antd');

  const Select = ({ children, onChange, ...otherProps }: any) => {
    // otherProps必须加上，因为Select组件的值还是蛮多的，要是你加了但是这里没mock，会找不到
    return <select onChange={e => onChange(e.target.value)} {...otherProps}>{children}</select>;
  };

  Select.Option = ({ children, ...otherProps }: any) => {
    return <option {...otherProps}>{children}</option>;
  }
  
  // 为什么使用jest.fn()，其实我们test只关心function的触发，而jest.fn() jest可以记录是否被调用
  return {
    ...antd,  
    Select,
    Modal: {
      success: jest.fn()
    }
  }
});
```


### 参考
https://github.com/ant-design/ant-design/issues/21080