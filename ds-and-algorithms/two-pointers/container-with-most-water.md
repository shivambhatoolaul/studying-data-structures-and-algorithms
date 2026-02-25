# 💧 container-with-most-water

**Problem:** You are given an integer array `heights` where `heights[i]` represents the height of the *ith* bar.

You may choose any two bars to form a container. Return the maximum amount of water a container can store.

**Example:**
```
Input: height = [1,7,2,5,4,7,3,6]

Output: 36

Input: height = [2,2,2]

Output: 4
```
---

**Solution:**
```python
def max_area(heights: List[int]) -> int:
    l = 0
    r = len(heights)-1
    max_water = 0
    for num in heights:
        height = min(heights[l], heights[r])
        width = r - l
        curr_water =  height * width
        max_water = max(max_water, curr_water)
        if heights[l] > heights[r]:
            r -= 1
        else:
            l += 1
    return max_water
```

---

**Takeaway(s):** You can use the two pointers pattern without a sorted array, if the problem just requires comparing the instantiated left and right pointers. 
