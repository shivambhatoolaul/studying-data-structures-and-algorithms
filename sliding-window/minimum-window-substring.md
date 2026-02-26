# 🪟🤏 minimum-window-substring

**Problem:** Given two strings `s` and `t`, return the shortest substring of `s` such that every character in `t`, including duplicates, is present in the substring. If such a substring does not exist, return an empty string `""`.

You may assume that the correct output is always unique.

**Example:**
```shell
Input: s = "OUZODYXAZV", t = "XYZ"

Output: "YXAZ"

Input: s = "xyz", t = "xyz"

Output: "xyz"

Input: s = "x", t = "xy"

Output: ""
```
---

**Solution:**
```python
def min_window(s: str, t: str) -> str:
    shortest = ""

    need = Counter(t)
    need_count = len(need)

    have = { key: 0 for key in need }
    have_count = 0

    l = 0
    for r in range(len(s)):
        char = s[r]
        if char in need:
            have[char] += 1
            if have[char] == need[char]:
                have_count += 1

            while have_count == need_count:
                # let's check if current substring is the shortest
                substring = s[l:r+1]  # ⚠️ store indices of substring to optimize
                shortest = substring if len(substring) < len(shortest) or shortest == "" else shortest

                # let's try shrinking the window and looking for shorter
                remove_char = s[l]
                l += 1
                if remove_char in need:
                    have[remove_char] -= 1
                    if have[remove_char] < need[remove_char]:
                        have_count -= 1

    return shortest
```

---

**Takeaway(s):** Track required character frequencies and maintain a count of when requirements are fully met for efficiency. Expand the window to satisfy constraints, then greedily shrink it to find the minimum valid window.
