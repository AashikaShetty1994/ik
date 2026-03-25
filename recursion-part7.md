# Recursive Algorithms and the Tower of Hanoi Problem

## 1. Overview of Recursive Problems
- **Mathematical Functions**: Return a value, solved using mathematical definitions.
- **Procedures**: No return value, algorithmic, manipulate data (e.g., sorting: insertion sort, merge sort, quick sort).

## 2. The Tower of Hanoi Problem
- Move disks from one peg to another with rules: one disk at a time, larger not on smaller.
- Pegs: A (source), B (destination), C (auxiliary).
- N disks, goal: move all from A to B using C.
- N=1: Move disk from A to B.
- N=2: Move smaller to C, larger to B, smaller to B (3 moves).

## 3. General Recursive Solution
1. Move top N-1 disks from A to C using B as auxiliary.
2. Move largest disk from A to B.
3. Move N-1 disks from C to B using A as auxiliary.

## 4. Key Recursive Strategy
- **Base Case**: N=1, move disk from source to destination.
- **Recursive Step**: Solve for N-1, move largest, solve for N-1 again.

## 5. Pseudo-Code
```python
def tower_of_hanoi(n, source, destination, auxiliary):
    # Base case: if only one disk is left
    if n == 1:
        print(f"Move disk 1 from {source} to {destination}")
        return
    # Recursive case
    tower_of_hanoi(n-1, source, auxiliary, destination)  # Move N-1 disks to auxiliary
    print(f"Move disk {n} from {source} to {destination}")  # Move the largest disk
    tower_of_hanoi(n-1, auxiliary, destination, source)  # Move N-1 disks to destination
```

## 6. Time Complexity
- T(N) = 2 * T(N-1) + 1
- O(2^N)