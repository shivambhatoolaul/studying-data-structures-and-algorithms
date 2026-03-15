# 🪄 reorder-linked-list

**Problem:** You are given the head of a singly linked-list.

The positions of a linked list of `length = 7` for example, can intially be represented as:

`[0, 1, 2, 3, 4, 5, 6]`

Reorder the nodes of the linked list to be in the following order:

`[0, 6, 1, 5, 2, 4, 3]`

Notice that in the general case for a list of `length = n` the nodes are reordered to be in the following order:

`[0, n-1, 1, n-2, 2, n-3, ...]`

You may not modify the values in the list's nodes, but instead you must reorder the nodes themselves.

**Example:**
```shell
Input: head = [2,4,6,8]

Output: [2,8,4,6]

Input: head = [2,4,6,8,10]

Output: [2,10,4,8,6]
```
---

**Solution:**
```python
def reorder_list(head: Optional[ListNode]) -> None:
    # 1. Use a fast and slow pointer to get the middle of the list
    fast = slow = head
    while fast and fast.next:
        fast = fast.next.next
        slow = slow.next

    # 2. Disconnect 1st half and 2nd half of list
    second = slow.next
    slow.next = None

    # 3. Reverse 2nd half of list to make reordering easier
    prev = None
    while second:
        next_iter = second.next

        second.next = prev
        prev = second

        second = next_iter

    # 4. Reorder by taking 1 item from 1st half of the list, then reversed 2nd half
    first = head
    second = prev
    while second:
        next_iter_first = first.next
        next_iter_second = second.next

        first.next = second
        second.next = next_iter_first

        first = next_iter_first
        second = next_iter_second


```

---

**Takeaway(s):** Always break complex linked list problems into clear phases, since they are often a combination of simpler patterns:  
  1. Find the middle (fast & slow pointers)  
  2. Reverse a linked list  
  3. Merge two lists alternately  
  
  Always disconnect halves (`slow.next = None`) before modifying pointers to avoid cycles.
