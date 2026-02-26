# 🔁 reverse-linked-list

**Problem:** Given the beginning of a singly linked list `head`, reverse the list, and return the new beginning of the list.

**Example:**
```shell
Input: head = [0,1,2,3]

Output: [3,2,1,0]

Input: head = []

Output: []
```
---

**Solution:**
```python
def reverse_list(head: Optional[ListNode]) -> Optional[ListNode]:
        prev, curr = None, head
        while curr:
            # Always store the next node before changing pointers, or you will lose access to the rest of the list
            nxt = curr.next

            # Detach curr, connect it to prev and make it new prev
            curr.next = prev
            prev = curr

            # Continue iterating thru the remaining list
            curr = nxt
        return prev
```

---

**Takeaway(s):** Reversing a linked list is done by re-pointing node references one at a time. Always store the next node before changing pointers, or you will lose access to the rest of the list. Maintain three roles while iterating: `nxt` (remaining list), `prev` (reversed portion) and `curr` (current node).
