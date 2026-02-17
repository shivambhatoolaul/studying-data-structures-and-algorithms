# 🔁 contains-duplicate

**Problem:** Given an integer array `nums`, return `true` if any value appears more than once in the array, otherwise return `false`.

---

**Solution:**
```python
def has_duplicates(nums):
        return len(set(nums)) != len(nums)
```

---

**Takeaway(s):** Converting to a hash set eliminates duplicates.
