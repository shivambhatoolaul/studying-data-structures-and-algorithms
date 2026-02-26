# 🫂 longest-repeating-character-replacement

**Problem:** You are given a string s consisting of only uppercase english characters and an integer `k`. You can choose up to `k` characters of the string and replace them with any other uppercase English character.

After performing at most `k` replacements, return the length of the longest substring which contains only one distinct character.

**Example:**
```
Input: s = "XYYX", k = 2

Output: 4

Input: s = "AAABABB", k = 1

Output: 5
```
---

**Solution:**
```python
def character_replacement(s: str, k: int) -> int:
    longest = 0 
    count = defaultdict(int)
    max_freq = 0
    l = 0
    for r in range(len(s)):
        count[s[r]] += 1
        max_freq = max(max_freq, count[s[r]])

        while (r - l + 1) - max_freq > k:  # window rule
            count[s[l]] -= 1
            l += 1
        
        longest = max(longest, r - l + 1)

    return longest
```

---

**Takeaway(s):** Spend time deducing valid window rules from the problem to see whether we need to adjust/slide the window at an iteration. In this problem, the valid window rule is `window_size`: `(r - l + 1)` `- max_freq ≤ k`; track the max frequency to validate the window efficiently.