---
layout: post
title: Bit Manipulation Tricks
excerpt_separator: <!--more-->
tags: interview tricks
---



<!--more-->

## 1. Swapping two numbers

``` c
a = a ^ b;
b = a ^ b; // = (a ^ b) ^ b = a
a = a ^ b; // = (a ^ b) ^ a = b
a = a ^ b;
```

## 2. Check if ith bit is set

``` c
bool result = (n & (1 << i)) == 1;
```

## 3. Set ith bit

``` c
n = n | (1 << i);
```

## 4. Clear ith bit

``` c
n = n & ~(1 << i);
```

## 5. Toggle ith bit

``` c
n = n ^ (1 << i);
```

## 6. Remove rightmost set bit

``` c
n = n & (n - 1);
```

## 7. Count number of set bits

``` c
while (n) {
    if (n & 1) count++;
    n = n >> 1;
}
```