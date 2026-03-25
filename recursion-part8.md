# Recursion Part 8: Exhaustive Search / Enumeration (Concise)

## Overview
- Exhaustive search enumerates all combinatorial objects from n distinct elements.
- Categories:
  - Permutations: order matters (with/without repetition).
  - Combinations: order doesn’t matter (with/without repetition).

## Binary Strings (Permutation with Repetition)

### Recursive version (returns full list)
```python
def binarystrings(n):
    if n == 1:
        return ["0", "1"]
    prev = binarystrings(n-1)
    result = []
    for s in prev:
        result.append(s + "0")
        result.append(s + "1")
    return result
```
- Time: O(2^n), Space: O(2^n).

### Iterative version
```python
def binarystrings(n):
    result = ["0", "1"]
    for i in range(2, n+1):
        newresult = []
        for s in result:
            newresult.append(s + "0")
            newresult.append(s + "1")
        result = newresult
    return result
```
- Time: O(2^n), Space: O(2^n).

### Optimized recursive streaming (accumulator)
```python
def binarystrings_helper(slate, n):
    if n == 0:
        print(slate)
    else:
        binarystrings_helper(slate + "0", n - 1)
        binarystrings_helper(slate + "1", n - 1)

def binarystrings(n):
    binarystrings_helper("", n)
```
- Time: O(2^n), Space: O(n) stack depth.

## Combinations (C(n,k)) Recap
```python
def combination(n, k):
    if k == 0 or k == n:
        return 1
    return combination(n - 1, k - 1) + combination(n - 1, k)

# Memoized

def combination_memo(n, k, memo=None):
    if memo is None:
        memo = {}
    key = (n, k)
    if key in memo:
        return memo[key]
    if k == 0 or k == n:
        memo[key] = 1
    else:
        memo[key] = combination_memo(n - 1, k - 1, memo) + combination_memo(n - 1, k, memo)
    return memo[key]
```
- Recursive C(n,k) without memo: O(2^n) in worst case.
- With memo: O(n*k).
