# ✅ valid-parentheses

**Problem:** You are given a string `s` consisting of the following characters: `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`.

The input string `s` is valid if and only if:

Every open bracket is closed by the same type of close bracket.
Open brackets are closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.
Return `true` if `s` is a valid string, and `false` otherwise.

**Example:**
```shell
Input: s = "[]"

Output: true

Input: s = "([{}])"

Output: true

Input: s = "[(])"

Output: false
```
---

**Solution:**
```python
def is_valid(s: str) -> bool:
    order = { '(': ')', '[': ']', '{': '}' }
    stack = []

    for char in s:
        if char in order:  # opening
            stack.append(char)

        else:  # closing
            bracket = stack.pop() if stack else None
            if not bracket or order[bracket] != char:
                return False
    
    return not stack
```

---

**Takeaway(s):** The Last-In-First-Out (LIFO) property of stacks allow us to compare with the last element we pushed in *0(1)*. 
