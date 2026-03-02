# ⛙ merge-two-sorted-linked-lists

**Problem:** You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists into one sorted linked list and return the head of the new sorted linked list.

The new list should be made up of nodes from `list1` and `list2`.

**Example:**
```shell
Input: list1 = [1,2,4], list2 = [1,3,5]

Output: [1,1,2,3,4,5]

Input: list1 = [], list2 = [1,2]

Output: [1,2]

Input: list1 = [], list2 = []

Output: []
```
---

**Solution:**
```python
def merge_two_lists(list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
    dummy = node = ListNode()  # keep dummy so we can point back to it

    while list1 and list2:
        if list1.val < list2.val:
            node.next = list1
            list1 = list1.next
        else:
            node.next = list2
            list2 = list2.next
        node = node.next

    node.next = list1 or list2

    return dummy.next
```

---

**Takeaway(s):** Use a dummy node to save a reference of the head to return later.

Traverse both lists simultaneously, always attaching the smaller node to maintain sorted order. Once one list is exhausted, append the remaining nodes from the other list directly.  
