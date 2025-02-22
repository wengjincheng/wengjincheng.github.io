---
title: JavaScript Operators
published: 2025-02-22
description: ''
image: ''
tags: ['JavaScript']
category: ''
draft: false 
---

*In my working experience as a senior JavaScript/TypeScript Engineer, I always met some JavaScript operators my co-workers writed, some of these always make me confused. This feeling is very suck, and everytime I figure it out by reading MDN or using LLM(ChatGpt or Deepseek), I will do this: Oh yes, I know it! Serveral days past or maybe a few months, I met this operator again, oh fuck, what is it? Same thing happen again!*

**So Today, let me do this very work to really understand JS operators and pin these thing in my brain!!! Oh I mean I am seriously!**

## All these fuck JavaScript Operators

### ??

**Definition**: The nullish coalescing (??) operator is a logical operator that returns its right-hand side operand when its left-hand side operand is null or undefined, and otherwise returns its left-hand side operand.

```JavaScript

let left_side = null
const right_side = 'Oh, It is me!'
const res = left_side ?? right_side // Oh, It is me!

left_side = 'HA, It is me now, fuck right!'
const res2 = left_side ?? right_side // HA, It is me now, fuck right!

```

MDN: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing