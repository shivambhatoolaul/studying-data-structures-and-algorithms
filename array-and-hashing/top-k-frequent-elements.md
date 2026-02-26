# 🪣 top-k-frequent-elements

**Problem:** Given an integer array `nums` and an integer `k`, return the `k` most frequent elements within the array.

The test cases are generated such that the answer is always unique.

You may return the output in any order.

**Example:**
```
Input: nums = [1,2,2,3,3,3], k = 2

Output: [2,3]
```
---

**Solution:**
```python
def top_k_frequent_elements(nums: List[int], k: int) -> List[int]:
    # get count of each element
    num_count = Counter(nums)

    # sort them into buckets where bucket[i] contains elements that appear i-1 times in nums
    buckets = [[] for _ in nums]
    for num, count in num_count.items():
        buckets[count-1].append(num)
    
    # flatten buckets
    ans = [item for bucket in buckets for item in bucket]

    # reverse order, then take first k elements
    return ans[::-1][:k]
```
> ⚠️ This problem can be solved with less space complexity by iterating through the buckets backwards—instead of flattening them and reversing the list—then taking `k` elements...

---

**Takeaway(s):** Use bucket sort to group elements by frequency and efficiently retrieve the top-`k` elements without a full sort.

Use `Counter()` to efficiently count the frequency of elements. 
