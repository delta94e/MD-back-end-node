# 01. Dynamic Programming — Fibonacci, Knapsack, LCS

> 📖 Tài liệu chi tiết: [0.2.6-Dynamic-Programming.md](../../0.2.6-Dynamic-Programming.md)

## Checklist Học

- [ ] Nhận diện DP: overlapping subproblems + optimal substructure
- [ ] Top-down (memoization) vs Bottom-up (tabulation)
- [ ] Định nghĩa dp[i] / dp[i][j] BẰNG LỜI trước khi code
- [ ] Recurrence relation: dp[i] = f(dp[i-1], dp[i-2], ...)
- [ ] Base case: dp[0] = ?, dp[1] = ?
- [ ] Fill order: left→right? top→bottom? diagonal?
- [ ] 1D DP: Fibonacci, climbing stairs, house robber, coin change
- [ ] 2D DP: LCS, edit distance, knapsack, unique paths
- [ ] Space optimization: rolling array (O(n) → O(1))

---

## Framework Narration

```
"Let me check: does this have overlapping subproblems?
 If I draw the recursion tree...

 fib(5)
    ├── fib(4)
    │   ├── fib(3) ← OVERLAP!
    │   └── fib(2) ← OVERLAP!
    └── fib(3) ← OVERLAP!

 Yes! I see repeated computations → DP.

 dp[i] = the answer for input of size i
 Recurrence: dp[i] = dp[i-1] + dp[i-2]
 Base case: dp[0] = 0, dp[1] = 1
 Fill order: left to right (dp[i] depends on dp[i-1], dp[i-2])
 Time: O(n), Space: O(n) → optimizable to O(1)"
```

---

## Câu Hỏi Phỏng Vấn Mẫu

1. "Climbing Stairs" — 1D DP, Fibonacci variant
2. "Coin Change" — 1D DP, unbounded knapsack
3. "Longest Common Subsequence" — 2D DP
4. "Word Break" — 1D DP + HashSet
5. "0/1 Knapsack" — 2D DP
6. "Edit Distance" — 2D DP

---

## Liên Kết

- 📖 Chi tiết: [0.2.6-Dynamic-Programming.md](../../0.2.6-Dynamic-Programming.md)
- 🗺️ LeetCode: [0.2.8-LeetCode-Roadmap.md](../../0.2.8-LeetCode-Roadmap.md)
