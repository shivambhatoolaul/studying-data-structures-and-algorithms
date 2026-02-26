# 1️⃣2️⃣ binary-search

**Problem:** You are given an array of distinct integers `nums`, sorted in ascending order, and an integer `target`.

Implement a function to search for `target` within `nums`. If it exists, then return its index, otherwise, return `-1`.

Your solution must run in *O(logn) time*

**Example:**
```
Input: nums = [-1,0,2,4,6,8], target = 4

Output: 3

Input: nums = [-1,0,2,4,6,8], target = 3

Output: -1
```
---

**Solution:**
```python
def search(nums: List[int], target: int) -> int:
    l = 0
    r = len(nums)-1

    while l <= r:
        m = (l+r) // 2  # l + (r - l) // 2 to prevent overflow in most languages, not python

        if nums[m] > target:  # search left side
            r = m-1

        elif nums[m] < target:  # search right side
            l = m+1

        else:  # nums[m] == target
            return m

    return -1
```

---

**Takeaway(s):** Eliminating half the search at each iteration greatly improves time complexity—from *O(n)* to *O(logn)*. 
