# 🔀🔀 group-anagrams

**Problem:** Given an array of strings `strs`, group all anagrams together into sublists. You may return the output in any order.

An anagram is a string that contains the exact same characters as another string, but the order of the characters can be different.

**Example:**
```
Input: strs = ["act","pots","tops","cat","stop","hat"]

Output: [["hat"],["act", "cat"],["stop", "pots", "tops"]]
```
---

**Solution:**
```python
def group_anagrams(strs: List[str]) -> List[List[str]]:
    anagrams = defaultdict(list)  # key: char counter representation, value: list of words in strs

    for word in strs:
        word_repr = [0] * 26
        for char in word:
            word_repr[ord(char) - ord('a')] += 1

        anagrams[str(word_repr)].append(word)

    return list(anagrams.values())
```

---

**Takeaway(s):** You can't use other hashmaps as keys to a hashmap, but you can find creative ways to workaround this to get the same desired effect. Use ord() to get an integer value of a character. Use defaultdict() so you don't have to do initial existence check.
