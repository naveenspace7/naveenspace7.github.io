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

[5. unordered_multiset](#unorderedmultiset)

[6. map](#map)

[7. multimap](#multimap)

[8. unordered_map](#unorderedmap)

[9. unordered_multimap](#unorderedmultimap)

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
* Operations: find, count, equal_range
* Observers: hash_function, key_eq, get_allocator
* Hash Policy: load_factor, max_load_factor, rehash, reserve
* Buckets: bucket_count, max_bucket_count, bucket_size, bucket

A small demo program to show how to implement an unordered_set for custom classes is shown <a href="https://gist.github.com/naveenspace7/d44e137e788b6fc7a686125091b4ff9a">here</a>

___


### 5. std::unordered_multiset <a name="unorderedmultiset"></a>

Present in the header file `unordered_set`.

The only difference between this container and unorder set is that this container can hold multiple keys.

<!-- General purpose and properties -->
Unordered set container stores **multiple equal elements** whose values once entered **cannot be modified later** (immutable), they can only be inserted and removed. The elements in a set are accessed by their **key instead of position**. The elements are placed in no particular order, which makes it easier for faster retrieval.

<!-- Implementation -->
Unordered multiset is also implemented as a **chained hash table**, which arranges the elements into buckets based on the hash of the element. Therefore, it also has the provision to make use of a custom hash function as a template parameter. It can also take an allocator object when default memory allocation needs to be modified.

<!-- Figure of binary search tree -->

<!-- Access times -->
Since they are implemented as a chained hash table, the time to **insert, erase and find** an element is `O(1)`. It is worth mentioning that set can make use of hints to decrease the operation times.

<!-- How to use it -->

<!-- Operations possible -->
Set allows the following operations:
* Iterators: begin, end, cbegin, cend
* Capacity: empty, size
* Modification: insert, erase, clear, emplace, emplace_hint
* Operations: find, count, equal_range
* Observers: hash_function, key_eq, get_allocator
* Hash Policy: load_factor, max_load_factor, rehash, reserve
* Buckets: bucket_count, max_bucket_count, bucket_size, bucket

___

### 6. std::map <a name="map"></a>

<!-- Header file -->
Present in header file `map`.

<!-- General purpose and properties -->
Map container stores **unique key elements**. The elements in a set are accessed by their **key instead of position** and the value held by the key can be extracted (keys and mapped to values). The elements are sorted according to a particular order as they are inserted.

<!-- Implementation -->
Maps is most commonly implemented as a **binary search tree** (red-black trees). Therefore, it also has the provision to make use of a custom comparison function as a template parameter (requiring signature `bool comp(T lhs, T rhs)`). It can also take an allocator object when default memory allocation needs to be modified. An entry in the map can be accessed with `pair<const T1 K, T2 V> entry`.

<!-- Figure of binary search tree -->

<!-- Access times -->
Since they are implemented in a binary search trees, the time to **insert, erase and find** an element is `O(log n)` (the size of the tree). It is worth mentioning that set can make use of hints to decrease the operation times.

<!-- Operations possible -->
Set allows the following operations:
* Iterators: begin, end, rbegin, rend, cbegin, cend, crbegin, crend
* Capacity: empty, size, max_size
* Element Access: operator[], at
* Modification: insert, erase, clear, emplace, emplace_hint
* Observers: key_comp, value_comp
* Operations: find, lower_bound, upper_bound, equal_range
* Allocator: get_allocator

___

### 7. std::multimap <a name="multimap"></a>

<!-- Header file -->
Present in header file `map`.

<!-- General purpose and properties -->
Multi map container stores **multiple equal elements**. The elements in a multi map are accessed by their **key instead of position**. The elements are sorted according to a particular order as they are inserted.

<!-- Implementation -->
Set is most commonly implemented as a **binary search tree** (red-black trees). Therefore, it also has the provision to make use of a custom comparison function as a template parameter (requiring signature `bool comp(T lhs, T rhs)`). It can also take an allocator object when default memory allocation needs to be modified. An entry in the map can be accessed with `pair<const T1 K, T2 V> entry`.

<!-- Figure of binary search tree -->

<!-- Access times -->
Since they are implemented in a binary search trees, the time to **insert, erase and find** an element is `O(log n)` (the size of the tree). It is worth mentioning that set can make use of hints to decrease the operation times. Count takes `O(log n)` to find the matching element and linear time to count the number of elements.

<!-- Operations possible -->
Set allows the following operations:
Set allows the following operations:
* Iterators: begin, end, rbegin, rend, cbegin, cend, crbegin, crend
* Capacity: empty, size, max_size
* Modification: insert, erase, clear, emplace, emplace_hint
* Observers: key_comp, value_comp
* Operations: find, count, lower_bound, upper_bound, equal_range
* Allocator: get_allocator

___

### 8. std::unordered_map <a name="unorderedmap"></a>

___

### 9. std::unordered_multimap <a name="unorderedmultimap"></a>

___

### std::list

### std::forward_list

### std::deque

### std::queue

### std::stack

### std::array

### std::priority_queue

## Summary

<!-- Final verdict -->

Q. Why to choose set against unordered_set when there is very little benefit gained by using the former? 

If you need to iterator through the container or need the elements to be sorted and using a small container with 100 elements, choose set.
For smaller sets prefer the usage of set, otherwise use an unordered_set. However, always benchmark when counting for performance.

Reference: 
<!-- https://stackoverflow.com/questions/1349734/why-would-anyone-use-set-instead-of-unordered-set -->
