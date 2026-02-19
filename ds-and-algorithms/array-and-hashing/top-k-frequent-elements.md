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
    num_count = defaultdict(int)
    for num in nums:
        num_count[num] += 1

    # sort them into buckets where bucket[i] contains elements that appear i(-1) times in nums
    buckets = [[] for _ in nums]
    for num, count in num_count.items():
        buckets[count-1].append(num)
    
    # flatten buckets
    ans = []
    for bucket in buckets:
        for item in bucket:
            ans.append(item)

    return ans[::-1][:k] # reverse order, take first k elements
```

---

**Takeaway(s):** Use bucket sort for distributed data of same types over a known range.
