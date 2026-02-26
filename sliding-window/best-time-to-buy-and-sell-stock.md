# 📈 best-time-to-buy-and-sell-stock

**Problem:** You are given an integer array `prices` where `prices[i]` is the price of NeetCoin on the `i`th day.

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
    l = 0  # min
    max_profit = 0
    for r in range(1, len(prices)):
        l = r if prices[r] < prices[l] else l
        max_profit = max(max_profit, prices[r] - prices[l])
    return max_profit
```

---

**Takeaway(s):** Use sliding window by keeping track of current mininum: `l`: `prices[l]` (start of window) and current price on day `r`: `prices[r]` (end of window). In this problem, we only move the start of the window if a new minimum is found, and update the `max_profit` by calculating `prices[r] - prices[l]`.
