# Understanding Recursion using Factorials and Combinatorics

## 1. Understanding Recursion through Simple Examples
- Recursion solves problems by breaking them into smaller subproblems of the same type.
- Ideal introduction: Recursive mathematical functions like factorial (n!).

## 2. Combinatorics Basics: Rule of Sum & Rule of Product
**Rule of Sum**: If an action can be done in A ways or B ways, total ways = A + B (e.g., 4 short-sleeved + 6 long-sleeved shirts = 10 choices).

**Rule of Product**: If an action has A ways followed by B ways, total ways = A × B (e.g., 10 shirts × 8 pants = 80 outfits).

## 3. Permutations and Arrangements
**Without Repetition (Permutations)**: Arranging n distinct items: n! = n × (n-1) × ... × 1 (e.g., 4 letters: 4! = 24).

**With Repetition (Arrangements)**: Each position has n options: n^n (e.g., binary strings of length n: 2^n; 4-digit passcodes: 10^4 = 10,000).

## 4. Recursive Definition of Factorial
factorial(n) = 1 if n = 0  
= n × factorial(n - 1) if n > 0  

- Analogy: Lazy manager delegates factorial(n-1) and multiplies result by n.

## 5. Recursive vs Iterative Implementation
**Recursive Implementation**  
```python
def fact(n):
    if n == 0:
        return 1
    return n * fact(n - 1)
```
- Follows definition directly.
- Uses call stack.
- Space: O(n), Time: O(n)

**Iterative Implementation**  
```python
def fact(n):
    result = 1
    for i in range(1, n + 1):
        result *= i
    return result
```
- Uses loop.
- Space: O(1), Time: O(n)

## 6. Recursive Call Stack Explained (Factorial of 4)
- factorial(4) → factorial(3) → factorial(2) → factorial(1) → factorial(0)
- Unwinds: 1 → 1×1 → 2×1 → 3×2 → 4×6 = 24
- Each call adds to stack; pops after base case.

## 7. Recursive Thinking: "Leap of Faith"
- Focus on your level; assume recursive calls work for smaller problems.
- Don't trace entire chain unless needed.

## 8. Formal Proof: Mathematical Induction
- Base Case: factorial(0) = 1 correct.
- Inductive Step: If factorial(n-1) correct, then factorial(n) = n × factorial(n-1) correct.

## 9. Time and Space Complexity

| Approach   | Time Complexity | Space Complexity |
|------------|-----------------|------------------|
| Recursive  | O(n)           | O(n) (stack)    |
| Iterative  | O(n)           | O(1)            |