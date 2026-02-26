# 🔍 search-in-sorted-rotated-array

**Problem:** You are given an array of length `n` which was originally sorted in ascending order. It has now been rotated between `1` and `n `times. For example, the array `nums = [1,2,3,4,5,6]` might become:
- `[3,4,5,6,1,2]` if it was rotated `4` times.
- `[1,2,3,4,5,6]` if it was rotated `6` times.

Notice that rotating the array `4` times moves the last four elements of the array to the beginning. Rotating the array `6` times produces the original array.

Given the rotated sorted array `nums` and an integer `target`, return the index of `target` within `nums`, or `-1` if it is not present.

You may assume all elements in the sorted rotated array `nums` are unique,

A solution that runs in *O(n)* time is trivial, can you write an algorithm that runs in *O(log n)* time?

**Example:**
```shell
Input: nums = [3,4,5,6,1,2]

Output: 1

Input: nums = [4,5,0,1,2,3]

Output: 0

Input: nums = [4,5,6,7]

Output: 4
```
---

**Solution:**
```python
def search(nums: List[int], target: int) -> int:
    l, r = 0, len(nums)-1
    while l <= r:
        m = (l+r) // 2
        if nums[m] == target:
            return m
            
        if nums[m] >= nums[l]:  # left-sorted portion
            if nums[l] <= target <= nums[m]:
                r = m-1 
            else:
                l = m+1

        else:  # right-sorted-portion
            if nums[m] <= target <= nums[r]:
                l = m+1
            else:
                r = m-1

    return -1
```

---

**Takeaway(s):** Again, like every binary search problem, you need to find in which case to keep looking into the left subarray or right subarray. Like in `find-minimum-in-rotated-sorted-array`, we know that if the middle element is bigger than the left-most element: `nums[m] >= nums[l]`, the left subarray is sorted, else the right subarray is sorted. Then, we check if the target is within the bounds of the sorted portion. If the target is in the sorted portions, we only keep looking in those sorted portions, else the other subarray.
