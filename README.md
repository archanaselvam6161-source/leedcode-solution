# LeetCode 3963: Create Grid With Exactly One Path

## Problem Description

Given two integers `m` and `n`, create an `m x n` grid containing only:

- `.` — Free cell
- `#` — Obstacle cell

The grid must have exactly one valid path from the top-left cell `(0, 0)` to the bottom-right cell `(m - 1, n - 1)`.

You can move only **right** or **down**.

## Approach

1. Create an `m x n` grid filled with `#`.
2. Change every cell in the first row to `.`.
3. Change every cell in the last column, starting from the second row, to `.`.
4. Return the grid.

This creates a single L-shaped path from the starting cell to the ending cell.

## C++ Solution

```cpp
class Solution {
public:
    vector<string> createGrid(int m, int n) {
        vector<string> grid(m, string(n, '#'));

        for (int j = 0; j < n; j++) {
            grid[0][j] = '.';
        }

        for (int i = 1; i < m; i++) {
            grid[i][n - 1] = '.';
        }

        return grid;
    }
};
```

## Example

**Input**
```text
m = 2, n = 3
```

**Output**
```text
["...", "##."]
```

**Path:**

`(0,0) → (0,1) → (0,2) → (1,2)`

There is exactly one valid path from the start to the destination.

## Complexity Analysis

- **Time Complexity:** `O(m × n)` — initializing the grid takes `O(m × n)` time.
- **Space Complexity:** `O(m × n)` — the grid stores `m × n` characters.

## Key Concept

By making only the first row and last column free, we create an L-shaped path while keeping the remaining cells blocked.

## Technologies Used

- Language: C++
- Platform: LeetCode
- Topic: Matrix and Grid Construction
