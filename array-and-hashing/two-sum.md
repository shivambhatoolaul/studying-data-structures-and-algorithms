# 2️⃣ two-sum

**Problem:** Given an array of integers nums and an integer target, return the indices `i` and `j` such that `nums[i] + nums[j] == target` and `i != j`.

You may assume that every input has exactly one pair of indices `i` and `j` that satisfy the condition.

Return the answer with the smaller index first.

**Example:**
```
Input: 
nums = [3,4,5,6], target = 7

Output: [0,1]
```

---

**Solution:**
```python
def two_sum(nums: List[int], target: int) -> List[int]:
    memory = {} # key = target - nums[j], value = j
    for j in range(len(nums)):
        need = target - nums[j]
        if need in memory:
            i = memory[need]
            return [i, j]
        memory[nums[j]] = j
```

---

**Takeaway(s):** Store past lookups (e.g., in this problem: `memory[nums[j]] = j`) in hashmaps for quick *O(1)* re-lookups.
