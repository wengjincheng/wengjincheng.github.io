---
title: JavaScript Operators
published: 2025-02-22
description: ''
image: './pic-jsoperators.webp'
tags: ['JavaScript']
category: 'JavaScript'
draft: false 
---

*Throughout my tenure as a Senior JavaScript/TypeScript Engineer, I've frequently encountered colleagues' usage of obscure JS operators that initially led to ambiguity. This recurring pattern of temporary confusion followed by documentation/MDN research (or LLM consultation via ChatGPT/Deepseek) creates an unproductive cycle:
"Ah, right! Got it now!" → Months later → "Wait, what's this operator again?!"*

**Today I'm breaking this loop:**

I'm implementing deliberate, structured learning to achieve:

1. Deep conceptual understanding (not just surface-level recognition)

2. Long-term retention through active recall techniques

3. Systematic documentation of operator behaviors and edge cases

This isn't another casual review - it's targeted cognitive reinforcement for professional mastery. Time to turn transient awareness into permanent engineering intuition.

## All these fuck JavaScript Operators

### ??

**Definition**: The nullish coalescing (??) operator is a logical operator that returns its right-hand side operand when its left-hand side operand is null or undefined, and otherwise returns its left-hand side operand.

``` javascript

let left_side = null
const right_side = 'Oh, It is me!'
const res = left_side ?? right_side // Oh, It is me!

left_side = 'HA, It is me now, fuck right!'
const res2 = left_side ?? right_side // HA, It is me now, fuck right!

```

MDN: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing

### !!

**Tips**: The !! operator is not official operator but use two ! operator, the first ! make the content to boolean type and the second make it reversed.

*This is always the way I met !! in my work days! Always make me confused, sucks!*

``` javascript

const my_content = underfind

const result = !!my_content // false, the first ! make it to true, the second ! make it to false


```

MDN: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing