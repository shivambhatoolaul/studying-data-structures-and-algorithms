# 🔁 linked-list-cycle-detection

**Problem:** Given the beginning of a linked list `head`, return `true` if there is a cycle in the linked list. Otherwise, return `false`.

There is a cycle in a linked list if at least one node in the list can be visited again by following the `next` pointer.

Internally, `index` determines the index of the beginning of the cycle, if it exists. The tail node of the list will set it's `next` pointer to the `index-th` node. If `index = -1`, then the tail node points to `null` and no cycle exists.

Note: `index` is not given to you as a parameter.

**Example:**
```shell
Input: head = [1,2,3,4], index = 1

Output: true

Input: head = [1,2,3,4], index = 1

Output: true
```
---

**Solution:**
```python
def has_cycle(head: Optional[ListNode]) -> bool:
    fast, slow = head, head
    while fast and fast.next:
        fast = fast.next.next
        slow = slow.next
        if fast == slow:
            return True
    return False
```

---

**Takeaway(s):** Floyd’s Tortoise and Hare: Use two pointers moving at different speeds (slow = 1 step, fast = 2 steps) to detect cycles without extra memory. If a cycle exists, the fast pointer will eventually meet the slow pointer inside the loop. Analogy: A faster runner will eventually catch up to a slower runner on a track. This allows cycle detection in **O(n)** time and **O(1)** space without modifying the list or using a hash set.
