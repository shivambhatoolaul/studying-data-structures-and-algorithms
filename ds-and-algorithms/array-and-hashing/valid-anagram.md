# 🔀 valid-anagram

**Problem:** Given two strings `s` and `t`, return `true` if the two strings are anagrams of each other, otherwise return `false`.

An anagram is a string that contains the exact same characters as another string, but the order of the characters can be different.

---

**Solution:**
```python
def is_anagram(s, t):
    if len(s) != len(t):
        return False

    s_dict, t_dict = {}, {}
    for i in range (len(s)):  # or len(t)
        s_dict[s[i]] = 1 + s_dict.get(s[i], 0)
        t_dict[t[i]] = 1 + t_dict.get(t[i], 0)

    return s_dict == t_dict
```

---

**Takeaway(s):** Hash maps allow us to count frequency of elements.
