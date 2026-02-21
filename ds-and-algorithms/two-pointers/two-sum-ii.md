# 2️⃣ TODO

**Problem:** Given an array of integers `numbers` that is sorted in non-decreasing order.

Return the indices (1-indexed) of two numbers, `[index1, index2]`, such that they add up to a given target number `target` and `index1 < index2`. Note that `index1` and `index2` cannot be equal, therefore you may not use the same element twice.

There will always be exactly one valid solution.

Your solution must use *O(1)* additional space.

**Example:**
```
Input: numbers = [1,2,3,4], target = 3

Output: [1,2]
```
---

**Solution:**
```python
def two_sum(numbers: List[int], target: int) -> List[int]:
    l = 0
    r = len(numbers) - 1

    while l < r:

        curr_sum = numbers[l] + numbers[r]

        if curr_sum < target:
            l += 1
        
        elif curr_sum > target:
            r -= 1

        else:  # curr_sum == target
            return [l + 1, r + 1]
            
    return []
```

---

**Takeaway(s):** Use two pointers in sorted array problems by increasing the left pointer index for higher values, or decreasing the right pointer value for lower values. 
