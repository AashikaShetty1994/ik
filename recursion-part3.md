# Recursive Functions: Power and Number of Subsets

## 1. Recursive Power (n^k)
- Goal: compute n^k for integers n, k.
- Definition: n^k = n × n × ... × n (k times), and n^0 = 1.

```python
def RaiseIntToPower(n, k):
    if k == 0:
        return 1
    else:
        return n * RaiseIntToPower(n, k - 1)
```
- Time: O(k), Space: O(k).

## 2. Iterative Power (n^k)
```python
def RaiseIntToPower(n, k):
    result = 1
    for i in range(1, k + 1):
        result *= n
    return result
```
- Time: O(k), Space: O(1).

## 3. Number of Subsets of a Set (size n)
- Problem: count subsets of an n-element set.
- Recurrence: S(0)=1, S(n)=2*S(n-1).

```python
def subsets(n):
    if n == 0:
        return 1
    else:
        return 2 * subsets(n - 1)
```
- Time: O(n), Space: O(n).

## 4. Optimized Power (Exponentiation by Squaring)
- Use halving of exponent.

```python
def optimizedPower(n, k):
    if k == 0:
        return 1
    elif k % 2 == 0:
        half = optimizedPower(n, k // 2)
        return half * half
    else:
        half = optimizedPower(n, (k - 1) // 2)
        return half * half * n
```
- Time: O(log k), Space: O(log k).

## 5. Recursion Patterns & Complexity
- Linear recursion: O(n) (e.g., subtracting 1 each call).
- Divide and conquer (halving): O(log n) (e.g., exponentiation by squaring).
- Exponential recursion: O(2^n) possible for exhaustive subset generation, not here.

## 6. Key Takeaway
- Recursive solutions can be simple and direct (like power and subset count).
- Smart recurrence reductions (k/2) strongly improve performance.
- Always identify base case and recursive step clearly.
