# 🤏 find-minimum-in-rotated-sorted-array

**Problem:** You are given an array of length `n` which was originally sorted in ascending order. It has now been rotated between `1` and `n `times. For example, the array `nums = [1,2,3,4,5,6]` might become:
- `[3,4,5,6,1,2]` if it was rotated `4` times.
- `[1,2,3,4,5,6]` if it was rotated `6` times.

Notice that rotating the array `4` times moves the last four elements of the array to the beginning. Rotating the array `6` times produces the original array.

Assuming all elements in the rotated sorted array nums are unique, return the minimum element of this array.

A solution that runs in *O(n)* time is trivial, can you write an algorithm that runs in *O(log n)* time?

**Example:**
```
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
def find_min(nums: List[int]) -> int:
    l, r = 0, len(nums)-1

    while l <= r:
        m = (l+r) // 2

        if nums[l] <= nums[r]:  # sorted
            return nums[l]

        if nums[m] < nums[l]:
            r = m
        else:  # nums[m] >= nums[l]
            l = m+1
```

---

**Takeaway(s):** The essence of binary search is to half the search by either searching the left subarray or the right subarray. As a reminder, in regular binary search with a sorted array, if the middle element is not equal to the target: `nums[m] != target` and `nums[m] > target`, we continue looking in the left subarray—with smaller elements, else the right subarray—with bigger elements.

In this question, when finding the minimum element in a rotated sorted array, we follow this pattern, but deciding whether to search the left or right subarray requires more thinking vs. regular binary search. The key is to notice that with rotated arrays, if the left-most element is less than or equal to the right-most element: `nums[l] <= nums[r]`, then the array is already sorted, so we can return `nums[l]`. Else, if `nums[m] < nums[l]`, you know at some point in the left subarray, the array elements decreased, so the minimum element needs to be there. Thus, to continue the search, we do: `r = m` (inclusive of `nums[m]`), else `l = m+1` (exclusive of `nums[m]`)
