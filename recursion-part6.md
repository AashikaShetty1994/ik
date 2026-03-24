# Recursion Part 6: Combinations and Pascal’s Triangle

## 1. Key Concepts
- Combinations C(N, K): choose K from N, order doesn’t matter, no repetition.
- Symmetry: C(N, K) = C(N, N-K).
- Base cases: C(N, 0)=1 and C(N, N)=1.

## 2. Recursive Combination
```python
def combination(n, k):
    if k == 0 or k == n:
        return 1
    return combination(n - 1, k - 1) + combination(n - 1, k)
```
- Closely mirrors Pascal’s Triangle recursion.
- Time: O(2^N) without memo.

## 2.1 memoized combination
```python
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
- Time: O(n*k) with memo.
- Avoids exponential duplicate subproblems.

## 3. Pascal’s Triangle
- Row n gives C(n, 0)...C(n, n).
- Each entry equals sum of two entries above.
- Symmetric rows (e.g., row 3: 1, 3, 3, 1).
- Row sum is 2^n (all subsets of n elements).

## 4. Iterative/DP optimization (optional)
- Use DP table or direct formula to avoid exponential recursion.
- C(N,K) can be computed in O(K) by iterative accumulation.

## 5. Application
- Committee selection, lotteries, resource distribution.
- Recursive formula shows combinatorial structure clearly.
