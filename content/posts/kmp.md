---
title: "Kmp"
date: 2021-11-02T23:09:57+08:00
draft: false
categories:
  - 算法
  - C++
tags:
  - KMP
  - C++
---

``` C++
#include <iostream>

using namespace std;

// 计算Next数组
void makeNext(const char p[], int next[]) {
    int q, k; // q是字符串下标，k是最大公共前缀
    int m = strlen(p);
    next[0] = 0; // 第一个字符的最大公共前缀是0
    for (q = 1, k = 0; q < m; ++q) { // for循环从第二个字符开始依次计算出每个字符对应的next值
        while (k > 0 && p[q] != p[k]) {
            k = next[k - 1];
        }
        if (p[q] == p[k]) {
            k++;
        }

        next[q] = k;
    }
}

// KMP算法
int kmp(const char T[], const char P[], int next[]) {
    int n, m;
    int i, q;
    n = strlen(T);
    m = strlen(P);
    makeNext(P, next);

    for (i = 0, q = 0; i < n; ++i) { // 这里是从头到尾跑一遍字符串T，KMP就是不回头的
        while (q > 0 && P[q] != T[i]) { // 如果出现了字符串不相符，通过NEXT数组找到P字符串该从哪个字符开始
            q = next[q - 1];
        }

        if (P[q] == T[i]) { // 两个字符串相等自然就去比对下一个
            q++;
        }

        if (q == m) {
            printf("Pattern occurs with shift:%d\n",(i-m+1));
        }
    }
}

int main(){
    int next[20]={0};
    char T[] = "googlogoogle";
    char P[] = "google";

    printf("%s\n",T);
    printf("%s\n",P);
    kmp(T, P, next);
    return 0;
} 
```

### Refer:

- 参考阮一峰的文章求的NEXT数组：https://www.cnblogs.com/c-cloud/p/3224788.html

