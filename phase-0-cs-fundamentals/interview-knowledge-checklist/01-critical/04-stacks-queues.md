# 04. Stacks & Queues — FILO vs FIFO

> 📖 Tài liệu chi tiết: [0.2.1-Linear-Data-Structures.md](../../0.2.1-Linear-Data-Structures.md)

## Checklist Học

- [ ] Stack: FILO — push, pop, peek — tất cả O(1)
- [ ] Queue: FIFO — enqueue, dequeue, front — tất cả O(1)
- [ ] Implement Stack using Array vs Linked List
- [ ] Implement Queue using Array (circular) vs Linked List
- [ ] Monotonic Stack pattern: next greater/smaller element
- [ ] Stack for DFS, Queue for BFS
- [ ] Deque (double-ended queue): sliding window maximum

---

## Patterns Phỏng Vấn

### 1. Matching / Validation — Stack

```
Sử dụng khi: valid parentheses, HTML tag matching
for char in s:
    if opening: stack.push(char)
    if closing: if stack.empty or not match: return false
               else: stack.pop()
return stack.empty()

Script: "Parentheses matching is a classic stack problem.
 Opening brackets push, closing brackets pop and check match."
```

### 2. Monotonic Stack — Next Greater Element

```
Sử dụng khi: next greater element, daily temperatures, stock span
stack = []  # stores indices, maintains monotonic order
for i in range(n):
    while stack and arr[i] > arr[stack[-1]]:
        result[stack.pop()] = arr[i]
    stack.push(i)

Script: "I'll use a monotonic decreasing stack.
 When I find a larger element, it's the 'next greater'
 for all pending elements in the stack."
```

### 3. Stack as History — Undo / Calculator

```
Sử dụng khi: basic calculator, undo operations, min stack
Mỗi operation push vào stack → undo = pop

Script: "Stack naturally handles nested/history operations.
 I push operands, and when I see an operator, I pop
 two operands and push the result."
```

---

## Câu Hỏi Phỏng Vấn Mẫu

1. "Valid Parentheses" — stack matching
2. "Min Stack" — stack + auxiliary min stack
3. "Daily Temperatures" — monotonic stack
4. "Evaluate Reverse Polish Notation" — operand stack
5. "Implement Queue using Stacks" — 2 stacks
6. "Sliding Window Maximum" — deque

---

## Liên Kết

- 📖 Chi tiết: [0.2.1-Linear-Data-Structures.md](../../0.2.1-Linear-Data-Structures.md)
