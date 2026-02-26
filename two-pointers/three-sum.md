# 3️⃣ three-sum

**Problem:** Given an integer array `nums`, return all the triplets `[nums[i], nums[j], nums[k]]` where `nums[i] + nums[j] + nums[k] == 0`, and the indices `i, j and k` are all distinct.

The output should not contain any duplicate triplets. You may return the output and the triplets in any order.

**Example:**
```shell
Input: nums = [-1,0,1,2,-1,-4]

Output: [[-1,-1,2],[-1,0,1]]
```
---

**Solution:**
```python
def two_sum(numbers: List[int], target: int) -> List[List[int]]:
    # Same solution as two-sum-ii.md, but looking for more than 1 pair
    res = []
    l = 0
    r = len(numbers) - 1
    while l < r:
        curr_sum = numbers[l] + numbers[r]
        if curr_sum < target:
            l += 1
        elif curr_sum > target:
            r -= 1
        else:  # curr_sum == target
            res.append([numbers[l], numbers[r]])  # add actual values in list + continue if possible
            l += 1
            r -=1
            while numbers[r] == numbers[r+1] and l < r:  # skip over duplicate numbers[l] + numbers[r] values
                r -= 1
    return res

def three_sum(nums: List[int]) -> List[List[int]]:
    nums.sort()  # to use 2 pointers technique
    
    res = []
    
    for i, num in enumerate(nums):
        if num > 0:
            break  # all remaining numbers are positive, won't find something to cancel it out to 0, skip
        
        if i > 0 and num == nums[i-1]:
            continue  # duplicate numbers, skip

        two_sum_list = two_sum(nums[i+1:], -num)
        if two_sum_list:
            for two_sum_ans in two_sum_list:
                res.append([num] + two_sum_ans)

    return res

```
> ⚠️ This problem can also be solved with less space complexity by looking for the `two_sum_list`s without a new function. However for clarity—and to show how it relates to `two-sum-ii`—I chose this solution. 
---

**Takeaway(s):** Same as two-sum-ii.md, but with an extra takeway: If we want more than 1 solution to a two pointer problem—that isn't a duplicate—we can also increase the left pointer xor decrease the right pointer and keep looking.
