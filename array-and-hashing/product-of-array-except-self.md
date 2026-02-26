# 🧍 product-of-array-except-self

**Problem:** Given an integer array `nums`, return an array `output` where `output[i]` is the product of all the elements of `nums` except `nums[i]`.

Each product is guaranteed to fit in a 32-bit integer.

Follow-up: Could you solve it in *O(n)* time without using the division operation?

**Example:**
```shell
Input: nums = [1,2,4,6]

Output: [48,24,12,8]
```
---

**Solution:**
```python
def product_except_self(nums: List[int]) -> List[int]:
    prefix = []
    postfix = []
    for i in range(len(nums)):
        if i == 0:
            prefix.append(nums[i])
            postfix.append(nums[-1])
        else:
            prefix.append(nums[i] * prefix[i-1])
            postfix.append(nums[len(nums)-1-i] * postfix[i-1])
    postfix = postfix[::-1]
    
    output = []
    for i in range(len(nums)):
        if i == 0:
            output.append(postfix[i+1])
        elif i == len(nums)-1:
            output.append(prefix[i-1])
        else:
            output.append(postfix[i+1] * prefix[i-1])
    return output
```

> ⚠️ This problem can also be solved with less space complexity by using the output array to calculate the prefix and postfix in place, but that solution is less readable and intuitive as a pattern to remember for interviews...

---

**Takeaway(s):** Use the prefix/postfix method for problems involving calculating all except 1 element in a collection. 

To iterate backwards on a list, use this indexing: `len(list)-1-i`.
