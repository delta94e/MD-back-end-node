# 08. Sorting — Quicksort & Mergesort (PHẢI Biết Detail)

> 📖 Tài liệu chi tiết: [0.2.5-Sorting-and-Searching.md](../../0.2.5-Sorting-and-Searching.md)

## Checklist Học

- [ ] Mergesort: divide & conquer, O(n log n) guaranteed, O(n) space, STABLE
- [ ] Quicksort: partition, O(n log n) average, O(n²) worst, in-place, UNSTABLE
- [ ] Pivot selection strategies: random, median-of-3
- [ ] Counting Sort: O(n+k), non-comparison, integer keys
- [ ] Khi nào dùng sort nào: stability, space, worst case
- [ ] Comparison sort lower bound: Ω(n log n)
- [ ] Built-in sort: Timsort (Python/Java), V8 sort (JS)

---

## So Sánh Nhanh

| Algorithm     | Best       | Average    | Worst      | Space    | Stable |
| ------------- | ---------- | ---------- | ---------- | -------- | ------ |
| Mergesort     | O(n log n) | O(n log n) | O(n log n) | O(n)     | ✅     |
| Quicksort     | O(n log n) | O(n log n) | O(n²)      | O(log n) | ❌     |
| Heapsort      | O(n log n) | O(n log n) | O(n log n) | O(1)     | ❌     |
| Counting Sort | O(n+k)     | O(n+k)     | O(n+k)     | O(k)     | ✅     |

## Interview Narration

```
"I need to sort this array first.
 Built-in sort is O(n log n) — Timsort in Python/Java.
 Sorting enables binary search and two-pointer techniques.

 Why not Quicksort here? Although it's O(n log n) average,
 the O(n²) worst case matters when the array could be
 already sorted. Mergesort guarantees O(n log n)."
```

---

## Câu Hỏi Phỏng Vấn Mẫu

1. "Implement Mergesort from scratch"
2. "Implement Quicksort — explain pivot selection"
3. "Sort Colors (Dutch National Flag)" — 3-way partition
4. "Merge Intervals" — sort by start, then merge
5. "Kth Largest Element" — quickselect O(n) average

---

## Liên Kết

- 📖 Chi tiết: [0.2.5-Sorting-and-Searching.md](../../0.2.5-Sorting-and-Searching.md)
