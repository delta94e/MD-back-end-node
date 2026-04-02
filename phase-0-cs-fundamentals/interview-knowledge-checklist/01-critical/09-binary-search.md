# 09. Binary Search — Xuất Hiện Cực Kỳ Nhiều!

> 📖 Tài liệu chi tiết: [0.2.5-Sorting-and-Searching.md](../../0.2.5-Sorting-and-Searching.md)

## Checklist Học

- [ ] Classic template: left, right, mid, while left <= right
- [ ] Boundary handling: left < right vs left <= right — biết KHI NÀO dùng cái nào
- [ ] Search space: không chỉ sorted array — bất kỳ monotonic predicate nào
- [ ] Variations: find first/last occurrence, search in rotated array
- [ ] Binary search on answer: "minimize the maximum" / "maximize the minimum"
- [ ] Time: O(log n), Space: O(1)
- [ ] mid = left + (right - left) // 2 — tránh integer overflow

---

## Templates

### Template 1: Find Exact Match

```python
left, right = 0, len(arr) - 1
while left <= right:
    mid = left + (right - left) // 2
    if arr[mid] == target: return mid
    elif arr[mid] < target: left = mid + 1
    else: right = mid - 1
return -1
```

### Template 2: Find First True (Lower Bound)

```python
left, right = 0, len(arr)  # right = len, not len-1
while left < right:         # <, not <=
    mid = left + (right - left) // 2
    if condition(mid): right = mid      # shrink right
    else: left = mid + 1               # move left past
return left  # first position where condition is true
```

### Template 3: Binary Search on Answer

```python
left, right = min_answer, max_answer
while left < right:
    mid = left + (right - left) // 2
    if is_feasible(mid): right = mid   # try smaller
    else: left = mid + 1
return left

Script: "The answer lies in range [min, max].
 I binary search on the answer space.
 For each candidate, I check if it's feasible in O(n).
 Total: O(n log(max-min))."
```

---

## Câu Hỏi Phỏng Vấn Mẫu

1. "Binary Search" — classic
2. "Search in Rotated Sorted Array" — modified binary search
3. "Find First and Last Position" — two binary searches
4. "Search a 2D Matrix" — treat as 1D sorted array
5. "Koko Eating Bananas" — binary search on answer
6. "Median of Two Sorted Arrays" — binary search on partition

---

## Liên Kết

- 📖 Chi tiết: [0.2.5-Sorting-and-Searching.md](../../0.2.5-Sorting-and-Searching.md)
