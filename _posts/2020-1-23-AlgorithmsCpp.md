---
layout: post
title: Algorithms in C++
excerpt_separator: <!--more-->
tags: C++ Algorithms
---

<!--more-->

| ToC        | ToC           | ToC  |
| ------------- | ------------- | ------------- |
| [1. accumulate](#accumulate)      | [2. count](#count) | [3. count_if](#count_if) |
| [4. find](#find)     | [5. find_if](#findif)      |  [6. for_each](#feach) |
| [7. sort](#sort) | [8. stable_sort](#stabsort)      | [9. partial_sort](#par_sort) |
| [10. partial_sort_copy](#par_sort_cpy) | [11. min_element](#mnelem)      | [12. max_element](#mxelem) |
| [13. search](#srch) | [14. search_n](#srchn)      | [15. binary_search](#bsrch) |
| [16. copy](#cpy) | [17. copy_if](#cpyif)      | [18. nth_element](#nthelem) |
| [19. reverse](#rvr) | [20. reverse_copy](#rcopy)      | [21. set_difference](#sdiff) |
| [22. set_symmetric_difference](#ssdiff) | [23. transform](#transform)      | [24. iota](#iota) |
| [25. reduce](#reduce) | [26. adjacent_difference](#adiff) | [27. inner_product](#inner_product) |
| [28. generate](#generate) |  |  |


<!-- Pipeline: -->
<!-- reduce  and this vs accumulate -->
<!-- transform_reduce -->
<!-- partial_sum -->
<!-- inclusive_scan -->
<!-- transform_inclusive_scan -->
<!-- transform_exclusive_scan -->





<!-- [1. accumulate](#accumulate)

[2. count](#count)

[3. count_if](#count_if)

[4. find](#find)

[5. find_if](#findif)

[6. for_each](#feach)

[7. sort](#sort)

[8. stable_sort](#stabsort)

[9. partial_sort](#par_sort)

[10. partial_sort_copy](#par_sort_cpy)

[11. min_element](#mnelem)

[12. max_element](#mxelem)

[13. search](#srch)

[14. search_n](#srchn)

[15. binary_search](#bsrch)

[16. copy](#cpy)

[17. copy_if](#cpyif)

[18. nth_element](#nthelem)

[19. reverse](#rvr)

[20. reverse_copy](#rcopy)

[21. set_difference](#sdiff)

[22. set_symmetric_difference](#ssdiff) -->

<!-- ### Types of initialization <a name="initializations"></a> -->

<!-- ___ -->

### 1. std::accumulate <a name="accumulate"></a>

Used to add all the values in the container and return the result. Found in the header file `numeric`. More implementation details in `accumulate_demo.cpp`. `WARNING`: init value should be of the same type as others. For example when using a container with type float or double, the init type should be 0f or 0.0 and not just 0.

##### Usage:
* `std::accumulate(v.begin(), v.end(), init)`, needs an overload of `operator+` for custom objects.

* `std::accumulate(v.begin(), v.end(), init, custom_obj)`

* `std::accumulate(v.begin(), v.end(), init, custom_function)`, in custom_function can be a static function `(signature int sum(int, type))` that belongs to a class that is contained in v.

More info [here](http://www.cplusplus.com/reference/numeric/accumulate/)

___


### 2. std::count <a name="count"></a>
Used to find the number of time a value is occuring in the container. Present in the `algorithm` header.

##### Usage:
* `std::count(begin(v1), end(v1), val)`

More info [here](http://www.cplusplus.com/reference/algorithm/count/).

___

### 3. std::count_if <a name="count_if"></a>
Used to find the number of time a value is occuring in the container. Present in the `algorithm` header. For user defined data types, the operator `==` must be overloaded for the function to work as intended. The predicate condition can also be a lambda.

##### Usage:
* `std::count(begin(v1), end(v1), predicate)`

More info [here](http://www.cplusplus.com/reference/algorithm/count_if/).

___

### 4. std::find <a name="find"></a>
Returns an iterator to the first occurence in the range provided. If no matching element is found, the iterator to the last element is returned. Present in the `algorithm` header.

##### Usage:
* `std::find(begin(v1), end(v1), val)`

More info [here](http://www.cplusplus.com/reference/algorithm/find/).

___

### 5. std::find_if <a name="findif"></a>

Returns an iterator to the first occurance in the range provided. If no matching element is found, the iterator to the last element is returned.
Present in the `algorithm` header. This function needs a predicate condition to evaluate.

##### Usage:
* `std::find_if(begin(v1), end(v1), predicate)`

More info [here](http://www.cplusplus.com/reference/algorithm/find_if/).

___

### 6. std::for_each <a name="feach"></a>

Applied the function `fn` for all the elements present within the range given by the iterators. Present in the `algorithm` header.

##### Usage:
* `std::for_each(begin(v1), end(v1), fn)`

More info [here](http://www.cplusplus.com/reference/algorithm/for_each/).

___

### 7. sort <a name="sort"></a>

Sort the content given in the range. If a comparison function is given, it is used while sorting. Present in the `algorithm` header. `greater<type>` and other comparison functors can be used as well. The elements are compared with the overloaded `operator<` when no compare function is provided. Performs `O(N·log(N))` comparisons. This algorithm is unstable sort, in which when there are two equal elements, their positions **would** (but not guaranteed) be swapped or changed.

##### Usage:
* `std::sort(begin(v1), end(v1))`

* `std::sort(begin(v1), end(v1), compare)`

* `std::sort(begin(v1), end(v1), class_name)`, in this case the `class_name` needs an overload of `bool operator()(type& arg1, type& arg2)` function.

##### Extras:
Most implementations of std::sort use quicksort, (or usually a hybrid algorithm like introsort, which combines quicksort, heapsort and insertion sort).

**The only thing the standard requires is that std::sort somehow sort the data according to the specified ordering with a complexity of approximately O(N log(N))**; it is not guaranteed to be stable. Technically, introsort better meets the complexity requirement than quicksort, because quicksort has quadratic worst-case time.

[Question](https://stackoverflow.com/questions/1840121/which-type-of-sorting-is-used-in-the-stdsort)

More info [here](http://www.cplusplus.com/reference/algorithm/sort/).

___

### 8. std::stable_sort <a name="stabsort"></a>
Applies the function `fn` for all the elements present within the range given by the iterators. Present in the `algorithm` header. As the name suggests, the order of equal elements is preserved.

##### Usage:
* `std::stable_sort(begin(v1), end(v1))`

* `std::stable_sort(begin(v1), end(v1), fn)`

The order of equal elements is **guaranteed** to be preserved. Complexity: `O(N·log^2(N))`, where N = std::distance(first, last) applications of cmp. If additional memory is available, then the complexity is `O(N·log(N))`.

[Stackoverflow](https://stackoverflow.com/questions/23985891/what-is-the-difference-between-stdsort-and-stdstable-sort/23986246)

More info [here](http://www.cplusplus.com/reference/algorithm/stable_sort/).

___

### 9. std::partial_sort <a name="par_sort"></a>

Sort the content given in the range from begin to end but making sure all the elements till `middle` are sorted. If a comparison function is given, it is used while sorting. Present in the `algorithm` header. `greater<type>` and other comparison functors can be used as well. The elements are compared with the overloaded `operator<` when no compare function is provided. 

##### Usage:
* `std::partial_sort(begin, middle, end)`

* `std::partial_sort(begin, middle, end, func)`

"On average, less than linearithmic in the distance between first and last: Performs approximately N*log(M) comparisons of elements (where N is this distance, and M is the distance between first and middle). It also performs up to that many element swaps (or moves)."

More info [here](http://www.cplusplus.com/reference/algorithm/partial_sort/).

___

### 10. std::partial_sort_copy <a name="par_sort_cpy"></a>

Sort the content given in the range from begin to end and copies the sorted elements into a new container. If a comparison function is given, it is used while sorting. Present in the `algorithm` header. `greater<type>` and other comparison functors can be used as well. The elements are compared with the overloaded `operator<` when no compare function is provided.

##### Usage:
* `std::partial_sort_copy(begin, middle, end)`

* `std::partial_sort_copy(begin, middle, end, func)`

"On average, less than linearithmic in the distance between first and last: Performs approximately N*log(min(N,M)) comparisons of elements (where N is this distance, and M is the distance between result_first and result_last). It also performs up to that many element swaps (or moves) and min(N,M) assignments between ranges."

More info [here](http://www.cplusplus.com/reference/algorithm/partial_sort_copy/).

___

### 11. std::min_element <a name="mnelem"></a>

Returns a iterator to the first occurring smallest element in the container within the range provided. Present in the `algorithm` header.

##### Usage:
* `std::min_element(begin(v1), end(v1))`

* `std::min_element(begin(v1), end(v1), comp)`

Has linear complexity for searching and finding the least element.

More info [here](http://www.cplusplus.com/reference/algorithm/min_element/).

___

### 12. std::max_element <a name="mxelem"></a>

Returns a iterator to the first occurring largest element in the container within the range provided. Present in the `algorithm` header.

##### Usage:
* `std::max_element(begin(v1), end(v1))`

* `std::max_element(begin(v1), end(v1), comp)`

Has linear complexity for searching and finding the least element.

More info [here](http://www.cplusplus.com/reference/algorithm/max_element/).

___

### 13. std::search <a name="srch"></a>

This function returns the iterator to the element whose value is found in the target search list, not just the value but also the entire subsequence has to be present. Present in the `algorithm` header.

##### Usage:
* `std::search(begin(v1), end(v1), begin(v2), end(v2))`

* `std::search(begin(v1), end(v1), begin(v2), end(v2), comp)`

Linear complexity for searching.

More info [here](http://www.cplusplus.com/reference/algorithm/search/).

___

### 14. std::search_n <a name="srchn"></a>

This function returns the iterator to the element whose `val` is found along with it's `val_count` of consecutive occurances. Present in the `algorithm` header.

##### Usage:
* `std::search_n(begin(v1), end(v1), val_count, val)`

* `std::search_n(begin(v1), end(v1), val_count, comp)`

Linear complexity for searching.

More info [here](http://www.cplusplus.com/reference/algorithm/search_n/).

___

### 15. binary_search <a name="bsrch"></a>

This function returns the **boolean** value as the result for which whose value is equal to the value specified. Present in the `algorithm` header. **This algorithms expects the input to be sorted to work as desired**.

##### Usage:
* `bool std::binary_search(begin(v1), end(v1), val)`

* `bool std::binary_search(begin(v1), end(v1), val, comp)`

Performs approximately `log2(N)+2` element comparisons (where N is this distance).

More info [here](http://www.cplusplus.com/reference/algorithm/binary_search/).

___

### 16. std::copy <a name="cpy"></a>

Performs an element wise copy from source to the destination. Returns the end of the destination where the elements have been copied. Present in the `algorithm` header.

##### Usage:

* `std::copy(begin(v1), end(v1), begin(v2))`

* `std::copy(begin(v1), end(v1), back_inserter(v2))`

Linear time complexity.

More info [here](http://www.cplusplus.com/reference/algorithm/copy/).

___

### 17. copy_if <a name="cpyif"></a>
Performs an element wise copy from source to the destination which matches the predicate condition. Returns the end of the destination where the elements have been copied. Present in the `algorithm` header. Should perf be a concern, consider instead of using `std::back_inserter` to populate the destination with the same size as the source.

##### Usage:

* `std::copy_if(begin(v1), end(v1), begin(v2), pred)`

* `std::copy_if(begin(v1), end(v1), back_inserter(v2), pred)`

Linear time complexity.

More info [here](http://www.cplusplus.com/reference/algorithm/copy_if/).

___

### 18. std::nth_element <a name="nthelem"></a>

Rearranges elements such that `n`th element specified is in the right place (as it would have been in a sorted sequence). Present in the `algorithm` header. To compare custom objects, the class should overload `operator<` and `operator>`.

##### Usage:

* `std::nth_element(begin(v1), begin(v1)+n, end(v1))`

* `std::nth_element(begin(v1), begin(v1)+n, end(v1), pred)`

Hint: for `pred` use: `less<T>()` for sorting in ascending order and `greater<T>()` for sorting in descending order.

Linear (in length) time complexity, on average.

More info [here](http://www.cplusplus.com/reference/algorithm/nth_element/).

___

### 19. std::reverse <a name="rvr"></a>

Reverses the elements present in the container pointed by the range. Present in the `algorithm` header. Uses `iter_swap` on the elements that are being iterated.

##### Usage:

* `std::reverse(begin(v1), end(v1))`

Linear (in half the length) complexity.

More info [here](http://www.cplusplus.com/reference/algorithm/reverse/).

___

### 20. std::reverse_copy <a name="rcopy"></a>

Reverses the elements present in the container pointed by the range. Present in the `algorithm` header.

##### Usage:

* `std::reverse_copy(begin(v1), end(v1), begin(dest_v))`

Linear complexity.

More info [here](http://www.cplusplus.com/reference/algorithm/reverse_copy/).

___

### 21. std::set_difference <a name="sdiff"></a>

Gives the set difference between two sets. In this case, the order of the containers matter. Present in the header `algorithm`. In order for the function to work as intended, the container should be sorted before being passed to the function.

##### Usage:

* `std::set_difference(begin(v1), end(v1), begin(v2), end(v2), begin(v3))`

* `std::set_difference(begin(v1), end(v1), begin(v2), end(v2), back_inserter(v3))` // for an empty array

Linear complexity. 

More info [here](http://www.cplusplus.com/reference/algorithm/set_difference/).

___

### 22. std::set_symmetric_difference <a name="ssdiff"></a>

Gives the set difference between two sets regardless of the ordering. In other words the element present in one container but missing in the other are obtained. Present in the header `algorithm`. In order for the function to work as intended, the container should be sorted before being passed to the function.

##### Usage:

* `std::set_symmetric_difference(begin(v1), end(v1), begin(v2), end(v2), begin(v3))`

* `std::set_symmetric_difference(begin(v1), end(v1), begin(v2), end(v2), back_inserter(v3))` // for an empty array

Linear complexity. 

More info [here](http://www.cplusplus.com/reference/algorithm/set_symmetric_difference/).

___

### 23. std::transform <a name="transform"></a>

Present in the `algorithm` header. This function can take either one or two containers and perform unary or binary operation and copy the results into another container. To elaborate it, transform can do one of the two functions:

Take a container, pass each of the element to the function given, collect the output into another container.

![Transform Unary Operation]({{site.url}}/assets/images/transform_unary.png)


Take two containers, pass each of the element as a pair to the binary function given and collect the output into another container.

![Transform Binary Operation]({{site.url}}/assets/images/transform_binary.png)


##### Usage:

* `std::transform(begin(v1), end(v1), begin(res_v), unary_op)`

* `std::transform(begin(v1), end(v1), begin(v2), begin(res_v), binary_op)`

Linear complexity.

More info [here](http://www.cplusplus.com/reference/algorithm/transform/).

___

### 24. std::iota <a name="iota"></a>

Present in the `numeric` header. This function store increasing sequence of numbers (of init, with delta as 1) in a container.

##### Usage:

* `std::iota(begin(v1), begin(v1) + 3, 100)` v1 will contain {100, 101, 102}

Linear complexity.

More info [here](http://www.cplusplus.com/reference/numeric/iota/)

___

### 25. std::reduce <a name="reduce"></a>

___

### 26. std::adjacent_difference <a name="adiff"></a>

Present in the `numeric` header. Assigns to every element a difference between two consecutive values. This operation leaves the first value unchanged.

##### Usage:

* `std::adjacent_difference(begin(v1), end(v1), begin(v_result))`

* `std::adjacent_difference(begin(v1), end(v1), begin(v_result), binary_op)`

Linear complexity.

More info [here](http://www.cplusplus.com/reference/numeric/adjacent_difference/)

___

### 27. std::inner_product <a name="inner_product"></a>

Present in the `numeric` header. Takes two containers and performs op1 on each of the pair and performs op2 on all the elements in the resulting container. By default, these operations are op1 = addition (reduce operation) and op2 = multiplication.

##### Usage:

* `std::inner_product(begin(v1), end(v1), begin(v2), init)`

* `std::inner_product(begin(v1), end(v1), begin(v2), init, op1, op2)`

Linear complexity.

More info [here](http://www.cplusplus.com/reference/numeric/inner_product/)

___

### 24. std::merge <a name="merge"></a>

___

### 25. std::set_union <a name="setun"></a>

___

### 26. std::set_intersection <a name="setin"></a>

___

### 28. std::generate <a name="generate"></a>

Present in the `algorithm` header. Calls `gen` for filling every element in the container.

##### Usage:

* `std::generate(begin(v1), end(v1), gen)`

Linear complexity.

More info [here](http://www.cplusplus.com/reference/algorithm/generate/)

___