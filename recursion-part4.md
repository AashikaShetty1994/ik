# Fibonacci Sequence and Recursive Programming

## 1. Introduction
- Fibonacci sequence: Fib(0)=0, Fib(1)=1.
- Recurrence: Fib(n)=Fib(n-1)+Fib(n-2) for n>1.
- Origin: rabbit population growth model by Leonardo of Pisa.

## 2. Recursive Fibonacci (Direct)

```python
def fibonacci(n):
    if n == 0:
        return 0
    if n == 1:
        return 1
    return fibonacci(n - 1) + fibonacci(n - 2)
```

- For n=4: fib(4)=fib(3)+fib(2), fib(3)=2, fib(2)=1, result=3.
- Call tree expands exponentially; overlapping subproblems are recomputed.

## 3. Call Stack Walkthrough
- fib(4) → fib(3)+fib(2)
- fib(3) → fib(2)+fib(1)
- fib(2) → fib(1)+fib(0)
- Base cases return 1 and 0, values bubble up and sum.

## 4. Complexity
- Time: O(2^n) (exponential) due to repeated substrees.
- Space: O(n) stack depth.

## 5. Optimization: Memoization

```python
def fibonacci_memo(n, memo=None):
    if memo is None:
        memo = {}
    if n in memo:
        return memo[n]
    if n == 0:
        return 0
    if n == 1:
        return 1
    memo[n] = fibonacci_memo(n - 1, memo) + fibonacci_memo(n - 2, memo)
    return memo[n]
```

- Optimized Time: O(n)
- Avoids redundant recalculations by storing results.

## 6. Takeaway
- Fibonacci is classic recursive case illustrating base case, recursive case, and call stack.
- Naive recursion is easy but inefficient; memoization or bottom-up DP is recommended for practical use.
