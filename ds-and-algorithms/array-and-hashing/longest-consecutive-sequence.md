# 🔢 longest-consecutive-sequence

**Problem:** Given an array of integers `nums`, return the length of the longest consecutive sequence of elements that can be formed.

A consecutive sequence is a sequence of elements in which each element is exactly `1` greater than the previous element. The elements do not have to be consecutive in the original array.

You must write an algorithm that runs in `O(n)` time.

**Example:**
```
Input: nums = [2,20,4,10,3,4,5]

Output: 4

Input: nums = [0,3,2,5,4,6,1,1]

Output: 7
```
---

**Solution:**
```python
def longest_consecutive_sequence(nums: List[int]) -> int:
    if not nums:
        return 0

    nums = set(nums)  # for O(1) lookup
    smallest = min(nums)
    largest = max(nums)
    length = largest - smallest
    ordered = []
    for i in range(length+1):
        ordered.append(smallest + i)
    
    curr_length = 0
    longest = 0
    for num in ordered:
        if num in nums:
            curr_length += 1
            continue
        if curr_length > longest:
            longest = curr_length
        curr_length = 0
    
    return max(curr_length, longest)
```
> ⚠️ This problem can also be solved with less space complexity by converting `nums` to a hashset, iterating through each `num`, seeing if `num-1` exists; if it doesn't, this means this is the start of a sequence—so, we see if `num+1`, `num+2`, and so on exists. Longest sequence found like this wins.
---

**Takeaway(s):** Use hashsets for quick `O(1)` lookups on old values. If space complexity is not a problem, and you know the min and max values for an array of numbers, you can sort by iterating through the range of numbers and seeing if they exist in the original array converted to a hashset. 
