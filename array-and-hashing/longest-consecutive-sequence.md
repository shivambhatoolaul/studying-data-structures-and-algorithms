# 🚂 longest-consecutive-sequence

**Problem:** Given an array of integers `nums`, return the length of the longest consecutive sequence of elements that can be formed.

A consecutive sequence is a sequence of elements in which each element is exactly `1` greater than the previous element. The elements do not have to be consecutive in the original array.

You must write an algorithm that runs in *O(n)* time.

**Example:**
```shell
Input: nums = [2,20,4,10,3,4,5]

Output: 4

Input: nums = [0,3,2,5,4,6,1,1]

Output: 7
```
---

**Solution:**
```python
def longest_consecutive_sequence(nums: List[int]) -> int:
    nums_set = set(nums)  # for O(1) lookup
    longest = 0
    for num in nums_set:
        if num-1 not in nums_set:  # this is the start of a seq
            length = 1
            while num + length in nums_set:  # look for where seq end
                length += 1
            longest = max(longest, length)
    return longest
```

---

**Takeaway(s):** Use a hash set for *O(1)* lookups, and only start counting sequences from numbers with no predecessor (`num-1 not in set`) to find the longest consecutive sequence in *O(n)* time.
