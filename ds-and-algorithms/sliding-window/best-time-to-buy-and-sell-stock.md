# 📈 best-time-to-buy-and-sell-stock

**Problem:** You are given an integer array `prices` where `prices[i]` is the price of NeetCoin on the *ith* day.

You may choose a single day to buy one NeetCoin and choose a different day in the future to sell it.

Return the maximum profit you can achieve. You may choose to not make any transactions, in which case the profit would be `0`.

**Example:**
```
Input: prices = [10,1,5,6,7,1]

Output: 6

Input: prices = [10,8,7,5,2]

Output: 0
```
---

**Solution:**
```python
def max_profit(prices: List[int]) -> int:
        max_profit = 0
        min_day = prices[0]
        for i in range(1, len(prices)):
            min_day = min(min_day, prices[i])
            max_profit = max(max_profit, prices[i] - min_day)
        return max_profit
```

---

**Takeaway(s):** Use sliding window by keeping track of current `min_day` (start of window) and current `prices[i]` (end of window). We calculate the `profit` we would get for this window and move the window accordingly.
