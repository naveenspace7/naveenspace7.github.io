---
layout: post
title: Data Structures in C++
excerpt_separator: <!--more-->
tags: C++ Datastructures
---

<!--more-->

[1. vector](#vector)

[2. set](#set)

[3. multiset](#multiset)

[4. unordered_set](#unorderedset)

<!-- ### Types of initialization <a name="initializations"></a> -->
___

### 1. std::vector <a name="vector"></a>

___

### 2. std::set <a name="set"></a>

<!-- Header file -->
Present in header file `set`.

<!-- General purpose and properties -->
Set container stores **unique elements** whose values once entered **cannot be modified later**, they can only be inserted and removed. The elements in a set are accessed by their **key instead of position**. The elements are sorted according to a particular order as they are inserted.

<!-- Implementation -->
Set is most commonly implemented as a **binary search tree** (red-black trees). Therefore, it also has the provision to make use of a custom comparison function as a template parameter (requiring signature `bool comp(T lhs, T rhs)`). It can also take an allocator object when default memory allocation needs to be modified.

<!-- Figure of binary search tree -->

<!-- Access times -->
Since they are implemented in a binary search trees, the time to **insert, erase and find** an element is `O(log n)` (the size of the tree). It is worth mentioning that set can make use of hints to decrease the operation times.

<!-- Operations possible -->
Set allows the following operations:
* Iterators: begin, end, rbegin, rend, cbegin, cend, crbegin, crend
* Capacity: empty, size
* Modification: insert, erase, clear, emplace, emplace_hint
* Operations: find, lower_bound, upper_bound

___

### 3. std::multiset <a name="multiset"></a>

<!-- Header file -->
Present in header file `set`.

<!-- General purpose and properties -->
Multiset container stores **multiple equal elements** whose values once entered **cannot be modified later**, they can only be inserted and removed. The elements in a set are accessed by their **key instead of position**. The elements are sorted according to a particular order as they are inserted.

<!-- Implementation -->
Set is most commonly implemented as a **binary search tree** (red-black trees). Therefore, it also has the provision to make use of a custom comparison function as a template parameter (requiring signature `bool comp(T lhs, T rhs)`). It can also take an allocator object when default memory allocation needs to be modified.

<!-- Figure of binary search tree -->

<!-- Access times -->
Since they are implemented in a binary search trees, the time to **insert, erase and find** an element is `O(log n)` (the size of the tree). It is worth mentioning that set can make use of hints to decrease the operation times. Count takes `O(log n)` to find the matching element and linear time to count the number of elements.

<!-- Operations possible -->
Set allows the following operations:
* Iterators: begin, end, rbegin, rend, cbegin, cend, crbegin, crend
* Capacity: empty, size
* Modification: insert, erase, clear, emplace, emplace_hint
* Operations: find, count, lower_bound, upper_bound

___

### 4. std::unordered_set <a name="unorderedset"></a>

Present in the header file `unordered_set`.

<!-- General purpose and properties -->
Unordered set container stores **unique elements** whose values once entered **cannot be modified later** (immutable), they can only be inserted and removed. The elements in a set are accessed by their **key instead of position**. The elements are placed in no particular order, which makes it easier for faster retrieval.

<!-- Implementation -->
Unordered set is implemented as a **chained hash table**, which arranges the elements into buckets based on the hash of the element. Therefore, it also has the provision to make use of a custom hash function as a template parameter. It can also take an allocator object when default memory allocation needs to be modified.

<!-- Figure of binary search tree -->

<!-- Access times -->
Since they are implemented as a chained hash table, the time to **insert, erase and find** an element is `O(1)`. It is worth mentioning that set can make use of hints to decrease the operation times.

<!-- How to use it -->

<!-- Operations possible -->
Set allows the following operations:
* Iterators: begin, end, cbegin, cend
* Capacity: empty, size
* Modification: insert, erase, clear, emplace, emplace_hint
* Operations: find, count, lower_bound, upper_bound
* Observers: hash_function, key_eq
* Hash Policy: load_factor, max_load_factor, rehash, reserve
* Buckets: bucket_count, max_bucket_count, bucket_size, bucket

A small demo program to show how to implement an unordered_set for custom classes is shown <a href="https://gist.github.com/naveenspace7/d44e137e788b6fc7a686125091b4ff9a">here</a>

<!-- <div>
  <h1>Your Code Embed</h1>
  <script src="https://gist.github.com/naveenspace7/d44e137e788b6fc7a686125091b4ff9a.js"></script>
</div> -->

___





### std::unordered_multiset

### std::map

### std::multimap

### std::unordered_map

### std::unordered_multimap

### std::list

### std::forward_list

### std::deque

### std::queue

### std::stack

### std::array

### std::priority_queue