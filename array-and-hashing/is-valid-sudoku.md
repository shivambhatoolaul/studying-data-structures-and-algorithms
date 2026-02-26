# 🔢 is-valid-sudoku

**Problem:** You are given a `9 x 9` Sudoku board `board`. A Sudoku board is valid if the following rules are followed:

Each row must contain the digits `1-9` without duplicates.
Each column must contain the digits `1-9` without duplicates.
Each of the nine `3 x 3` sub-boxes of the grid must contain the digits `1-9` without duplicates.
Return true if the Sudoku board is valid, otherwise return false.

Note: A board does not need to be full or be solvable to be valid.

**Example:**
```
Input: board =
[["1","2",".",".","3",".",".",".","."],
 ["4",".",".","5",".",".",".",".","."],
 [".","9","8",".",".",".",".",".","3"],
 ["5",".",".",".","6",".",".",".","4"],
 [".",".",".","8",".","3",".",".","5"],
 ["7",".",".",".","2",".",".",".","6"],
 [".",".",".",".",".",".","2",".","."],
 [".",".",".","4","1","9",".",".","8"],
 [".",".",".",".","8",".",".","7","9"]]

Output: true

Input: board =
[["1","2",".",".","3",".",".",".","."],
 ["4",".",".","5",".",".",".",".","."],
 [".","9","1",".",".",".",".",".","3"],
 ["5",".",".",".","6",".",".",".","4"],
 [".",".",".","8",".","3",".",".","5"],
 ["7",".",".",".","2",".",".",".","6"],
 [".",".",".",".",".",".","2",".","."],
 [".",".",".","4","1","9",".",".","8"],
 [".",".",".",".","8",".",".","7","9"]]

Output: false  # there are two 1's in the top-left 3x3 sub-box
```
---

**Solution:**
```python
def is_valid_sudoku(board: List[List[str]]) -> bool:
    rows = defaultdict(set)
    cols = defaultdict(set)
    quads = defaultdict(set)

    for row in range(9):
        for col in range(9):
            quad = (row // 3, col // 3)

            cell = board[row][col]
            if (cell in rows[row] or 
                cell in cols[col] or 
                cell in quads[quad]):
                return False
            if cell != '.':
                rows[row].add(cell)
                cols[col].add(cell)
                quads[quad].add(cell)
    
    return True
```

> ⚠️ This problem can also be solved with less space complexity by using bitmasks, but I haven't revised bit manipulation yet. This current solution is also more readable and intuitive as a pattern to remember for interviews...

---

**Takeaway(s):** Since tuples are immutable, they can be used for more complex hashmap keys like in this problem when checking the quadrant: `(row // 3, col // 3)`. 
