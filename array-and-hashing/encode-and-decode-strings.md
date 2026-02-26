# 🤫 encode-and-decode-strings

**Problem:** Design an algorithm to encode a list of strings to a string. The encoded string is then sent over the network and is decoded back to the original list of strings.



**Example:**
```
Input: dummy_input = ["Hello","World"]

Output: ["Hello","World"]

Explanation:
Machine 1:
Codec encoder = new Codec();
String msg = encoder.encode(strs);
Machine 1 ---msg---> Machine 2

Machine 2:
Codec decoder = new Codec();
String[] strs = decoder.decode(msg);

Input: dummy_input = [""]

Output: [""]
```
---

**Solution:**
```python
def encode(strs: List[str]) -> str:
    s = ""
    for word in strs:
        s += str(len(word)) + '#' + word
    return s

def decode(s: str) -> List[str]:
    strs = []
    i = 0

    while i < len(s):
        j = i
        while s[j] != '#':
            j += 1
        length = int(s[i:j])
        i = j + 1
        j = i + length
        strs.append(s[i:j])
        i = j

    return strs
```

---

**Takeaway(s):** Strings are essentially arrays of characters, so you can process them index by index.  

When creating a custom delimiter, make sure it is before the actual string data, so you read the delimiter first, and make sure the delimiter is encoding how much to read, so no character in the string can be mistaken for the delimiter.
