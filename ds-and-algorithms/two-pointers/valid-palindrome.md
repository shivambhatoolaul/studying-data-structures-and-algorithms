# 🔁 valid-palindrome

**Problem:** Given a string `s`, return `true` if it is a palindrome, otherwise return `false`.

A palindrome is a string that reads the same forward and backward. It is also case-insensitive and ignores all non-alphanumeric characters.

Note: Alphanumeric characters consist of letters `(A-Z, a-z)` and numbers `(0-9)`.

**Example:**
```
Input: s = "Was it a car or a cat I saw?"

Output: true

Input: s = "tab a cat"

Output: false
```
---

**Solution:**
```python
def is_alphanum(c: str) -> bool:
    return (ord('a') <= ord(c) <= ord('z') or
            ord('A') <= ord(c) <= ord('Z') or
            ord('0') <= ord(c) <= ord('9')) 

def is_palindrome(s: str) -> bool:
    l = 0
    r = len(s)-1

    while l < r:
        while l < r and not is_alphanum(s[l]):
            l += 1
        while l < r and not is_alphanum(s[r]):
            r -= 1
        if s[l].lower() != s[r].lower():
            return False
        l += 1
        r -= 1
    
    return True
```

---

**Takeaway(s):** Instead of using extra space complexity (removing non-alphanumeric characters and reversing the array and comparing), you can initialize two pointers to efficiently check the front and the back of the array in place!
