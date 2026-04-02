# 05. Linked Lists — Singly, Doubly, Circular

> 📖 Tài liệu chi tiết: [0.2.1-Linear-Data-Structures.md](../../0.2.1-Linear-Data-Structures.md)

## Checklist Học

- [ ] Singly linked list: insert, delete, search — O(n)
- [ ] Doubly linked list: O(1) delete nếu có reference đến node
- [ ] Circular linked list: detection & applications
- [ ] Fast/Slow (Floyd's tortoise and hare) pointer technique
- [ ] Dummy head node trick — simplify edge cases
- [ ] Reverse linked list (iterative + recursive)
- [ ] Merge two sorted lists

---

## Patterns Phỏng Vấn

### 1. Fast/Slow Pointer — Cycle Detection

```
slow = fast = head
while fast and fast.next:
    slow = slow.next
    fast = fast.next.next
    if slow == fast: return True  # cycle!

Script: "Floyd's algorithm: slow moves 1 step, fast moves 2.
 If there's a cycle, they MUST meet. If not, fast hits null."
```

### 2. Dummy Head — Simplify Edge Cases

```
dummy = ListNode(0)
dummy.next = head
# ... operations ...
return dummy.next

Script: "I use a dummy head to avoid special-casing
 when the head itself might be removed or changed."
```

### 3. Reverse In-Place

```
prev = None
curr = head
while curr:
    next_node = curr.next
    curr.next = prev
    prev = curr
    curr = next_node
return prev

Script: "Three pointers: prev, curr, next.
 At each step, I reverse curr's pointer to prev."
```

---

## Câu Hỏi Phỏng Vấn Mẫu

1. "Reverse Linked List" — iterative (3 pointers) + recursive
2. "Linked List Cycle" — fast/slow pointer
3. "Merge Two Sorted Lists" — dummy head
4. "Remove Nth Node From End" — fast ahead by N, then both move
5. "LRU Cache" — doubly linked list + HashMap
6. "Add Two Numbers" — digit by digit with carry

---

## Liên Kết

- 📖 Chi tiết: [0.2.1-Linear-Data-Structures.md](../../0.2.1-Linear-Data-Structures.md)
- 📝 LRU Cache walkthrough: [0.5.1-Technical-Interview-Preparation.md §6.17.12](../../0.5.1-Technical-Interview-Preparation.md)
