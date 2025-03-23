---
title: Binary Exponentiation
published: 2024-12-15
description: ''
image: './binary-exponentiation.jpg'
tags: ['Algorithm', 'Trick', 'Arithmetic']
category: 'Algorithm'
draft: false 
---

### What is Binary Exponentiation - The Definition

Binary Exponentiation(also known as fast exponentiation) is a very hig efficient algorithm for computing large exponents. The key important advance is it can reduce the time complexity from O(n) -> O(logn).

Its core idea is to decompose the exponent into its binary representation and leverage a divide-and-conquer strategy to minimize multiplication operations. This method is widely used in cryptography, number theory, and scenarios involving large exponents.

### How It Works?

Theory of Binary Exponentiation has two key package:

**Binary Decomposition**

Represent the exponent in binary form. For example, 13 in binary is 1101, which corresponds to:
a^13 = a^(8+4+1) = a^8 * a^4 * a^1.

**Divide-and-Conquer**

Recursively or iteratively split the exponent into halves and combine results to avoid redundant calculations.

**Code Example**

``` javascript

function powerIterative(a, b) {
  let result = 1;
  while (b > 0) {
    if (b % 2 === 1) {// check whether the current bit is 1
      result *= a;
    }
    a *= a;// auto update the base
    b = Math.floor(b / 2);// to the next
  }
  return result;
}


console.log(powerIterative(3, 5)); // output 243

```

### LeetCode question

**LeetCode.50.Pow(x, n)**

``` javascript

/**
 * @param {number} x
 * @param {number} n
 * @return {number}
 */
var myPow = function(x, n) {
    let ans = 1

    if (n < 0) {
        n = -n
        x = 1 / x
    }

    while (n) {
        if (n % 2) {
            ans *= x
        }

        x *= x
        n = Math.floor(n / 2)
    }

    return ans
};


```