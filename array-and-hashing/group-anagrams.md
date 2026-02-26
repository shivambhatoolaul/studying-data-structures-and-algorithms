# 👥👥 group-anagrams

**Problem:** Given an array of strings `strs`, group all anagrams together into sublists. You may return the output in any order.

An anagram is a string that contains the exact same characters as another string, but the order of the characters can be different.

**Example:**
```shell
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

**Takeaway(s):** Standard hash maps can’t have other mutable structures (like lists or dicts) as keys, but you can creatively represent data in a hashable form (e.g., convert a character count list to a string) to use as a key like in this problem: `word_repr[ord(char) - ord('a')] += 1`. 

Use `ord()` to get the integer value of a character. 

Use `defaultdict()` to avoid manually checking for key existence before appending or updating values.
