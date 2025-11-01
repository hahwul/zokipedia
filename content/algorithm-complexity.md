+++
title = "Algorithm Complexity"
date = 2025-11-01
updated = 2025-11-01
description = "Understanding time and space complexity in algorithms with mathematical notation."
tags = ["algorithms", "complexity", "computer-science", "math"]
+++

Understanding algorithm complexity is crucial for writing efficient code. We use mathematical notation to express how algorithms scale.

## Big O Notation

Big O notation describes the upper bound of an algorithm's growth rate. Here are common complexity classes:

### Constant Time - O(1)

{% math() %}
f(n) = O(1)
{% end %}

Operations that take the same time regardless of input size.

### Logarithmic Time - O(log n)

{% math() %}
f(n) = O(\log n)
{% end %}

Common in binary search algorithms where the problem is divided in half each iteration.

### Linear Time - O(n)

{% math() %}
f(n) = O(n)
{% end %}

Algorithms that scale linearly with input size, like iterating through an array.

### Linearithmic Time - O(n log n)

{% math() %}
f(n) = O(n \log n)
{% end %}

Efficient sorting algorithms like merge sort and quicksort have this complexity.

### Quadratic Time - O(n²)

{% math() %}
f(n) = O(n^2)
{% end %}

Nested loops often result in quadratic complexity.

## Mathematical Formulas

### Sum of First n Natural Numbers

{% math() %}
\sum_{i=1}^{n} i = \frac{n(n+1)}{2}
{% end %}

### Geometric Series

{% math() %}
\sum_{i=0}^{n} r^i = \frac{r^{n+1} - 1}{r - 1} \quad \text{for } r \neq 1
{% end %}

### Master Theorem

For recurrence relations of the form $T(n) = aT(n/b) + f(n)$:

{% math() %}
T(n) = \begin{cases}
\Theta(n^{\log_b a}) & \text{if } f(n) = O(n^{\log_b a - \epsilon}) \\
\Theta(n^{\log_b a} \log n) & \text{if } f(n) = \Theta(n^{\log_b a}) \\
\Theta(f(n)) & \text{if } f(n) = \Omega(n^{\log_b a + \epsilon})
\end{cases}
{% end %}

## Space Complexity

Space complexity measures memory usage. For example, recursive algorithms use stack space:

{% math() %}
S(n) = O(h)
{% end %}

where $h$ is the height of the recursion tree.

## Amortized Analysis

The average time per operation over a sequence of operations:

{% math() %}
\text{Amortized Cost} = \frac{\text{Total Cost}}{n}
{% end %}

Understanding these mathematical foundations helps in analyzing and optimizing algorithms effectively.
