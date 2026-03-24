# Recursion Part 5: Fibonacci Memoized Summary

## Recursive Fibonacci with Memoization
- Problem: naive recursive Fibonacci is O(2^n) due to repeated subcalls.
- Solution: cache results in memo dictionary to avoid duplicate work.

```python
def fibonacci_memo(n, memo=None):
    if memo is None:
        memo = {0: 0, 1: 1}
    if n not in memo:
        memo[n] = fibonacci_memo(n - 1, memo) + fibonacci_memo(n - 2, memo)
    return memo[n]
```

- Base values: Fib(0)=0, Fib(1)=1.
- Recurrence: Fib(n)=Fib(n-1)+Fib(n-2).

## Complexity
- Time: O(n)
- Space: O(n)

## Notes
- `memo` persists values across recursion in one call-tree.
- This retains standard recursive structure while eliminating redundant recursion.
