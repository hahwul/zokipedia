+++
title = "Algorithm Complexity"
date = 2025-11-01
updated = 2025-11-06
description = "A practical, math-backed guide to time/space complexity: definitions, classes, pitfalls, measurement, data structures, and key formulas."
tags = ["algorithms", "complexity", "asymptotics", "big-o", "analysis", "data-structures", "recurrences", "amortized", "benchmarking", "math", "parallel"]
+++

Understanding algorithmic complexity is essential for writing efficient, scalable software and for communicating performance trade-offs. This guide combines precise definitions with practical tips, common pitfalls, and reference formulas you can use in day-to-day engineering.

## What do we measure?

- Time complexity: how running time scales with input size `n` under a chosen model of computation (often a unit-cost RAM model with word size w = Θ(log n)).
- Space complexity: how memory usage scales with `n` (peak or additional space).
- Input size: number of items (`n` elements), bit-length of numeric values, number of vertices/edges `(V, E)`, etc. Always state which input model you use.

Real-world note: the same asymptotic complexity can lead to very different wall-clock performance due to constants, memory locality, parallelism, and hardware effects.

## Asymptotic notation (precise definitions)

Let `f(n)` and `g(n)` be nonnegative for sufficiently large `n`.

- Big-O (upper bound):
  {% math() %}
  f(n) = O(g(n)) \iff \exists c>0,\, n_0\ge 1:\ \forall n\ge n_0,\ 0 \le f(n) \le c\,g(n)
  {% end %}

- Big-Ω (lower bound):
  {% math() %}
  f(n) = \Omega(g(n)) \iff \exists c>0,\, n_0:\ \forall n\ge n_0,\ f(n) \ge c\,g(n)
  {% end %}

- Big-Θ (tight bound):
  {% math() %}
  f(n) = \Theta(g(n)) \iff f(n)=O(g(n))\ \text{and}\ f(n)=\Omega(g(n))
  {% end %}

- little-o (strictly smaller):
  {% math() %}
  f(n) = o(g(n)) \iff \lim_{n\to\infty} \frac{f(n)}{g(n)} = 0
  {% end %}

- little-ω (strictly larger):
  {% math() %}
  f(n) = \omega(g(n)) \iff \lim_{n\to\infty} \frac{f(n)}{g(n)} = \infty
  {% end %}

Worst-case, average-case, and amortized bounds each use these notations—always specify which one you mean.

## Common complexity classes (with examples)

- Constant: `O(1)` — array indexing, stack push/pop (amortized for dynamic arrays).
- Inverse Ackermann: `O(α(n))` — nearly constant; disjoint set union-find with path compression + union by rank.
- Logarithmic: `O(log n)` — binary search; height of balanced BSTs; divide-by-2 loops.
- Polylogarithmic: `O(log^k n)` — some multi-level structures and index trees.
- Sublinear: `O(√n)` — trial division primality bound; 2D grid radius scans.
- Linear: `O(n)` — single pass over an array; counting; BFS on adjacency lists is `O(V+E)`.
- Linearithmic: `O(n log n)` — mergesort, heapsort, typical quicksort average.
- Quadratic/Cubic/Polynomial: `O(n^2)`, `O(n^3)`, `O(n^k)` — nested loops over independent dimensions; classical matrix multiplication `O(n^3)`.
- Near-linear with bounded keys: `O(n + k)` — counting/radix sort on small integer ranges; `k` = key range.
- Quasi-polynomial: `O(2^{(\log n)^c})` — arises in some approximation/derandomization results.
- Exponential: `O(c^n)` — brute-force subset search, exact TSP via Held-Karp `O(n^2 2^n)`.
- Factorial: `O(n!)` — enumerating permutations.

Related: fast multiplication `O(n^{\log_2 3})` (Karatsuba), fast matrix multiply `O(n^\omega)` with `ω < 2.373` (theoretical).

## Worst-case, average-case, amortized

- Worst-case: bound on the slowest valid input of size `n`.
- Average-case: expected complexity over a distribution of inputs (distribution must be stated).
- Amortized: average per operation over a sequence where occasional expensive ops occur.
  - Example: dynamic array doubling. Total moves across `n` appends is `< 2n`, so amortized append is `O(1)`.

{% math() %}
\text{Amortized cost} = \frac{\text{Total cost over } n \text{ ops}}{n}
{% end %}

## Practical measurement and inference

How to empirically validate complexity:

- Isolate the workload
  - Exclude I/O and logging; measure pure compute.
  - Warm up (JITs, caches); then time multiple runs.
- Vary problem size `n`
  - Use logarithmic steps (e.g., n = 2^k). Ensure enough data points.
  - For `n \log n`, plot `T(n)/n` vs `\log n` (flat line suggests `n \log n`).
- Use log–log plots
  - Fit a line to `(x, y) = (\log n, \log T(n))`. Slope ≈ polynomial exponent.
  {% math() %}
  s \approx \frac{\log T(n_2) - \log T(n_1)}{\log n_2 - \log n_1}
  {% end %}
- Statistics
  - Use medians or trimmed means; report variance.
  - Remove outliers; pin CPU; avoid thermal throttling.
- Space profiling
  - Track peak usage, allocation counts, and per-element overhead.
  - Consider GC/allocator metadata and fragmentation.

Caution: microbenchmarks can be misleading due to dead-code elimination, branch prediction, prefetching, and caching. Validate with profilers and counters when possible.

## Data structures at a glance (selected ops)

- Static array
  - Index: `O(1)`
  - Search: `O(n)` (linear), `O(log n)` if sorted + binary search
  - Insert/delete at index: `O(n)` due to shifts
- Dynamic array (amortized doubling)
  - Append: `O(1)` amortized, `O(n)` worst when resizing
  - Insert/delete in middle: `O(n)`
- Singly/doubly linked list
  - Prepend: `O(1)`; Append: `O(1)` with tail pointer; Search: `O(n)`; Random index: `O(n)`
- Stack / Queue / Deque
  - Push/Pop/Enqueue/Dequeue: `O(1)` (amortized or worst-case depending on implementation)
- Hash table (separate chaining / open addressing)
  - Average: find/insert/delete `O(1)` at healthy load factor
  - Worst-case: `O(n)` (adversarial collisions)
  - Resizing: `O(n)` occasionally; amortized constant per op
- Ordered map/set (balanced BST: red–black, AVL, B-tree)
  - Find/insert/delete: `O(log n)`; predecessor/successor: `O(log n)`; iteration: `O(n)`
- Heap (binary heap)
  - Find-min: `O(1)`; insert: `O(log n)`; extract-min: `O(log n)`; build-heap: `O(n)`
  - Decrease-key: `O(log n)` (Fibonacci heap: amortized `O(1)`, but large constants)
- Disjoint set (union–find)
  - With path compression + union by rank/size: `O(α(n))` amortized per op
- Trie / prefix tree (alphabet size `σ`)
  - Insert/lookup: `O(L)` for key length `L`; memory can be large (`σ` fans)
- Bloom filter
  - Membership test (no deletes): `O(k)` time, `O(m)` space, false positives allowed
  {% math() %}
  p \approx \left(1 - e^{-kn/m}\right)^k,\quad k_{\text{opt}} = \frac{m}{n}\ln 2,\quad p_{\min} \approx (0.6185)^{m/n}
  {% end %}

Graph representations:

- Adjacency list: space `O(V+E)`; BFS/DFS `O(V+E)`
- Adjacency matrix: space `O(V^2)`; edge check `O(1)`

Classic graph algorithm costs:

- BFS/DFS: `O(V+E)`
- Dijkstra (nonnegative weights): binary heap `O((V+E)\log V)`, Fibonacci heap `O(E + V \log V)`
- 0–1 BFS: `O(V+E)` with deque
- MST: Kruskal `O(E \log V)`, Prim (binary heap) `O(E \log V)`

Sorting and selection:

- Comparison sorting lower bound: `Ω(n \log n)`
- Mergesort/heapsort: `O(n \log n)`; Quicksort: average `O(n \log n)`, worst `O(n^2)`
- Counting/radix sort: `O(n + k)` for key range `k`
- Quickselect (k-th order statistic): average `O(n)`, worst `O(n^2)`; Median-of-medians worst-case `O(n)`

## Recurrences and key formulas

Sums and approximations:

- Sum of first n:
  {% math() %}
  \sum_{i=1}^{n} i = \frac{n(n+1)}{2}
  {% end %}

- Geometric series:
  {% math() %}
  \sum_{i=0}^{n} r^i = \frac{r^{n+1} - 1}{r - 1}\quad (r \ne 1)
  {% end %}

- Harmonic numbers:
  {% math() %}
  H_n = \sum_{i=1}^{n} \frac{1}{i} = \ln n + \gamma + \Theta\!\left(\frac{1}{n}\right)
  {% end %}
  where `γ` is the Euler–Mascheroni constant.

- Log-factorial / Stirling:
  {% math() %}
  \log n! = \Theta(n \log n),\quad
  n! \sim \sqrt{2\pi n}\left(\frac{n}{e}\right)^{n}
  {% end %}

Recurrence examples:

- Binary search:
  {% math() %}
  T(n) = T(n/2) + \Theta(1) \ \Rightarrow\ T(n)=\Theta(\log n)
  {% end %}

- Mergesort:
  {% math() %}
  T(n) = 2T(n/2) + \Theta(n) \ \Rightarrow\ T(n)=\Theta(n \log n)
  {% end %}

- Karatsuba multiplication:
  {% math() %}
  T(n) = 3T(n/2) + O(n) \ \Rightarrow\ T(n)=O\!\left(n^{\log_2 3}\right)\approx O(n^{1.585})
  {% end %}

- Strassen matrix multiply:
  {% math() %}
  T(n) = 7T(n/2) + O(n^2) \ \Rightarrow\ T(n)=O\!\left(n^{\log_2 7}\right)\approx O(n^{2.807})
  {% end %}

Master theorem (divide-and-conquer):
{% math() %}
T(n) = a\,T(n/b) + f(n),\ a\ge 1,\ b>1 \\
T(n) =
\begin{cases}
\Theta\!\left(n^{\log_b a}\right) & \text{if } f(n)=O\!\left(n^{\log_b a - \epsilon}\right) \\
\Theta\!\left(n^{\log_b a}\log n\right) & \text{if } f(n)=\Theta\!\left(n^{\log_b a}\right) \\
\Theta\!\left(f(n)\right) & \text{if } f(n)=\Omega\!\left(n^{\log_b a + \epsilon}\right)\ \text{and regularity holds}
\end{cases}
{% end %}

Akra–Bazzi (general form intuition):
Given {% math() %}T(x) = \sum_{i=1}^{k} a_i\,T(b_i x) + g(x){% end %}, find `p` such that {% math() %}\sum a_i b_i^p = 1{% end %}. Then
{% math() %}
T(x) = \Theta\!\left(x^p\left(1 + \int_{1}^{x} \frac{g(u)}{u^{p+1}}\,du\right)\right)
{% end %}

## Parallelism: work and span

Let `T1` be total work (1 core), `T∞` be span/critical path (infinite cores). With `P` processors:

- Lower bound:
  {% math() %}
  T_P \ge \max\!\left(\frac{T_1}{P},\ T_{\infty}\right)
  {% end %}
- Amdahl’s law (fixed workload, parallel fraction `P_f`):
  {% math() %}
  S(N) = \frac{1}{(1-P_f) + \frac{P_f}{N}}
  {% end %}
- Gustafson’s law (scaled workloads):
  {% math() %}
  S(N) = N - (1-P_f)(N-1)
  {% end %}

Implication: asymptotic improvements that reduce span (dependencies) often matter more than raw work on highly parallel hardware.

## Memory hierarchy and I/O awareness

- Algorithms with the same `O(n)` can vary by orders of magnitude based on locality and block transfers.
- Cache-aware/oblivious designs optimize transfers between layers (L1/L2/LLC/DRAM/disk).
- External memory (I/O) model tracks block size `B` and memory size `M`; aim to minimize cache misses and scans.

## Common pitfalls

- Ignoring constants and memory: `O(n)` with scattered random access can be slower than `O(n log n)` with tight sequential scans for real `n`.
- Comparing apples to oranges: average-case of algorithm A vs worst-case of algorithm B.
- Assuming distribution: hash tables need a good hash function and controlled load factors; adversarial inputs can degrade to `O(n)`.
- Mistaking amortized for worst-case: dynamic array append is not guaranteed `O(1)` per operation.
- Small `n` realities: lower-order terms dominate; choose simpler algorithms for tiny inputs.
- Overfitting benchmarks: JIT, branch prediction, dead-code elimination, and warmup can skew results.
- Ignoring I/O/network: Many systems are I/O-bound or latency-bound, not CPU-bound.

## Putting it to work: a quick checklist

1. Define the input model and size parameters (`n`, `V`, `E`, key range `k`, string length `L`).
2. Choose meaningful complexity targets (worst/average/amortized) and justify them.
3. Consider data-structure trade-offs (time vs space vs simplicity).
4. Validate with both math (recurrences, bounds) and measurement (multiple `n`, log–log fits).
5. Watch memory behavior (peak, locality, allocations) and parallel scalability (span).
6. Add assertions/metrics to prevent regressions (budget in CI, performance tests).

## Mathematical appendix (handy references)

- Sum of logs:
  {% math() %}
  \sum_{i=1}^{n} \log i = \log n! = \Theta(n \log n)
  {% end %}

- Sum of squares and cubes:
  {% math() %}
  \sum_{i=1}^{n} i^2 = \frac{n(n+1)(2n+1)}{6},\quad
  \sum_{i=1}^{n} i^3 = \left(\frac{n(n+1)}{2}\right)^2
  {% end %}

- Comparing `n^a` vs `n \log n`:
  - If `a > 1`, then `n^a = ω(n \log n)`.
  - If `a = 1`, then `n \log n = ω(n)`.

With these tools—precise notation, realistic measurement, and a sense for data-structure trade-offs—you can analyze, compare, and improve algorithms with confidence.