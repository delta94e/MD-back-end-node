# 03. Arrays & Strings — Dạng Bài Phổ Biến Nhất

> 📖 Tài liệu chi tiết: [0.2.1-Linear-Data-Structures.md](../../0.2.1-Linear-Data-Structures.md)

## Checklist Học

- [ ] Array operations: access O(1), insert/delete O(n), append amortized O(1)
- [ ] String immutability (Java/Python/JS) — cần StringBuilder/array cho modifications
- [ ] Two Pointers pattern: same direction, opposite direction
- [ ] Sliding Window pattern: fixed size, variable size
- [ ] Prefix Sum pattern: range sum queries O(1)
- [ ] In-place operations: reverse, rotate, partition
- [ ] Sorting + scanning pattern: sort first, then linear scan

---

## Patterns Phỏng Vấn

### 1. Two Pointers — Opposite Direction

```
Sử dụng khi: sorted array, palindrome check, container with most water
left = 0, right = n-1
while left < right:
    if condition: left++
    else: right--

Script: "Since the array is sorted, I can use two pointers
 from both ends. This avoids the O(n²) brute force."
```

### 2. Two Pointers — Same Direction (Fast/Slow)

```
Sử dụng khi: remove duplicates, linked list cycle, merge arrays
slow = 0
for fast in range(n):
    if condition: arr[slow] = arr[fast]; slow++

Script: "I'll use fast/slow pointers. Slow marks the
 position for valid elements, fast scans ahead."
```

### 3. Sliding Window — Variable Size

```
Sử dụng khi: longest/shortest substring with condition
left = 0
for right in range(n):
    add arr[right] to window
    while window invalid:
        remove arr[left] from window
        left++
    update answer

Script: "I recognize 'contiguous subarray' → sliding window.
 I'll expand right, shrink left when constraint is violated."
```

### 4. Prefix Sum

```
Sử dụng khi: range sum, subarray sum equals K
prefix[i] = sum(arr[0..i-1])
sum(arr[l..r]) = prefix[r+1] - prefix[l]

Script: "To avoid recomputing sums, I'll precompute a
 prefix sum array. Each range query becomes O(1)."
```

---

## Câu Hỏi Phỏng Vấn Mẫu

1. "Two Sum" — HashMap (O(n)) hoặc sort + two pointers (O(n log n))
2. "Container With Most Water" — two pointers opposite
3. "Longest Substring Without Repeating Characters" — sliding window + HashSet
4. "Minimum Size Subarray Sum" — sliding window variable
5. "Product of Array Except Self" — prefix/suffix products
6. "Valid Palindrome" — two pointers opposite

---

## Liên Kết

- 📖 Chi tiết: [0.2.1-Linear-Data-Structures.md](../../0.2.1-Linear-Data-Structures.md)
- 🗺️ LeetCode patterns: [0.2.8-LeetCode-Roadmap.md](../../0.2.8-LeetCode-Roadmap.md)
