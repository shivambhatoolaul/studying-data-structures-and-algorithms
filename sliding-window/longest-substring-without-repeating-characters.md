# 🧍 longest-substring-without-repeating-characters

**Problem:** Given a string `s`, find the length of the longest substring without duplicate characters.

A substring is a contiguous sequence of characters within a string.

**Example:**
```
Input: s = "zxyzxyz"

Output: 3

Input: s = "xxxx"

Output: 1
```
---

**Solution:**
```python
def length_of_longest_substring(s: str) -> int:
    longest = 0
    l = 0
    seen = {}
    for r in range(len(s)):
        if s[r] in seen: 
            l = max(l, seen[s[r]] + 1) # can't go back if duplicate was found earlier
        seen[s[r]] = r
        longest = max(longest, r-l+1)
    return longest
```

---

**Takeaway(s):** Track last-seen indices with a hash map (in this problem: `seen`) and jump the sliding window’s left pointer past duplicates to maintain a valid substring in O(n) time.
