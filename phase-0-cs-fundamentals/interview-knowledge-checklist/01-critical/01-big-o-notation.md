# 01. Big O Notation — Nền Tảng Của Mọi Câu Trả Lời

> 📖 Tài liệu chi tiết: [0.4.1-Big-O-Notation.md](../../0.4.1-Big-O-Notation.md)

> **Tại sao Big O là NỀN TẢNG?** Vì MỌI câu trả lời trong phỏng vấn kỹ thuật đều KẾT THÚC bằng: _"Time complexity is O(n), space complexity is O(1)."_ Nếu bạn không nói được câu này — hoặc nói sai — interviewer sẽ đánh giá bạn CHƯA SẴN SÀNG. Big O không chỉ là kiến thức lý thuyết — nó là **NGÔN NGỮ GIAO TIẾP** giữa bạn và interviewer.

## Checklist Học

- [ ] Hiểu Time Complexity vs Space Complexity
- [ ] Thuộc lòng bảng so sánh: O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ) < O(n!)
- [ ] Phân biệt Best / Average / Worst case
- [ ] Biết amortized analysis (ArrayList resize, HashMap rehash)
- [ ] Giải thích được TẠI SAO — không chỉ nêu O(n)
- [ ] Biết cách đếm operations trong nested loops
- [ ] Hiểu log n tới từ đâu (chia đôi, chia ba input)
- [ ] Nắm vững space complexity cho recursion (call stack depth)
- [ ] Biết khi nào O(n²) chấp nhận được vs khi nào PHẢI optimize
- [ ] Master multi-variable complexity: O(n × m), O(V + E)

---

## 1. Định Nghĩa Chính Thức — Big O, Big Ω, Big Θ

### Big O — Upper Bound (Worst Case)

```
f(n) = O(g(n)) nếu tồn tại c > 0 và n₀ sao cho:
f(n) ≤ c × g(n) với MỌI n ≥ n₀

Ý nghĩa: "Algorithm KHÔNG BAO GIỜ chậm hơn g(n)"
```

> **Trong phỏng vấn**: Khi interviewer hỏi "What's the time complexity?", họ muốn **Big O (worst case)**, trừ khi nói rõ khác. Đây là convention industry, không phải formal math.

### Big Ω (Omega) — Lower Bound — Giải Thích Chi Tiết

#### Định nghĩa toán học

```
f(n) = Ω(g(n)) nếu TỒN TẠI hằng số c > 0 VÀ n₀ ≥ 0 sao cho:

     f(n)  ≥  c × g(n)     với MỌI n ≥ n₀

Đọc: "f(n) là Omega của g(n)"
```

#### Hiểu bằng ngôn ngữ đời thường

```
Big O  = TRẦN NHÀ — function KHÔNG BAO GIỜ vượt qua
Big Ω  = SÀN NHÀ  — function KHÔNG BAO GIỜ rơi xuống dưới

Ví dụ thực tế:
• Lương tối thiểu = Ω — "bạn sẽ được trả ÍT NHẤT 10 triệu/tháng"
• Lương tối đa    = O — "bạn sẽ không được trả QUÁ 50 triệu/tháng"
• Thu nhập ổn định = Θ — "bạn luôn nhận KHOẢNG 20 triệu/tháng"

Áp dụng cho algorithm:
• f(n) = Ω(n) nghĩa là: "Dù input TỐT ĐẾN ĐÂU,
  algorithm vẫn phải làm ÍT NHẤT n bước."
• Nó đặt ra RÀO CẢN DƯỚI — không thể nhanh hơn được.
```

#### Chứng minh toán học từng bước — Ví dụ 1

```
CHỨNG MINH: f(n) = 3n + 5 là Ω(n)

Cần tìm c > 0 và n₀ ≥ 0 sao cho: 3n + 5 ≥ c × n, ∀n ≥ n₀

Bước 1: Nhận xét rằng 3n + 5 ≥ 3n    (vì 5 > 0)

Bước 2: 3n ≥ 3 × n → chọn c = 3

Bước 3: 3n + 5 ≥ 3n ≥ 3 × n → đúng với MỌI n ≥ 1

Bước 4: Chọn c = 3, n₀ = 1

Kiểm tra:
  n = 1:  3(1) + 5 = 8  ≥  3 × 1 = 3   ✅
  n = 10: 3(10) + 5 = 35 ≥ 3 × 10 = 30  ✅
  n = 100: 305 ≥ 300                       ✅

KẾT LUẬN: f(n) = 3n + 5 = Ω(n) ✅

Nghĩa là: 3n + 5 LUÔN lớn hơn hoặc bằng c × n (với c = 3)
→ Function này "ít nhất cũng phải chạy" n bước.
```

#### Chứng minh toán học — Ví dụ 2 (phức tạp hơn)

```
CHỨNG MINH: f(n) = n² - 10n + 25 là Ω(n²)

Cần tìm c > 0, n₀ sao cho: n² - 10n + 25 ≥ c × n², ∀n ≥ n₀

Bước 1: Chia cả hai vế cho n² (n > 0):
         1 - 10/n + 25/n² ≥ c

Bước 2: Khi n đủ lớn, -10/n và 25/n² → 0
         Vế trái → 1

Bước 3: Cần: 1 - 10/n + 25/n² ≥ c
         Chọn c = 1/2

         1 - 10/n + 25/n² ≥ 1/2
         1/2 ≥ 10/n - 25/n²
         1/2 ≥ 10/n  (vì -25/n² là âm, bỏ đi chỉ strict hơn)
         n ≥ 20

Bước 4: Chọn c = 1/2, n₀ = 20

Kiểm tra:
  n = 20: 400 - 200 + 25 = 225 ≥ 1/2 × 400 = 200  ✅
  n = 50: 2500 - 500 + 25 = 2025 ≥ 1/2 × 2500 = 1250  ✅

KẾT LUẬN: n² - 10n + 25 = Ω(n²) ✅

INSIGHT: Dù có trừ 10n, khi n đủ lớn, n² vẫn DOMINANT.
Nên lower bound vẫn là n².
```

#### ⚠️ HIỂU LẦM PHỔ BIẾN: Big Ω ≠ Best Case!

```
NHIỀU NGƯỜI NGHĨ:
  Big O = worst case
  Big Ω = best case     ← SAI! Đây là hiểu lầm #1

SỰ THẬT:
  Big O, Ω, Θ = quan hệ toán học giữa 2 functions
  Best/Average/Worst = loại INPUT

CHÚNG LÀ HAI DIMENSIONS KHÁC NHAU:

                  Best Case    Average Case    Worst Case
  ──────────────────────────────────────────────────────
  Big O (≤)        có           có              có
  Big Ω (≥)        có           có              có
  Big Θ (=)        có           có              có

VÍ DỤ:
  Insertion Sort:
  • Best case time  = Θ(n)       — đã sorted, chỉ scan
  • Worst case time = Θ(n²)      — sorted ngược
  • Average case    = Θ(n²)      — random input

  → Insertion Sort best case là Θ(n), KHÔNG phải Ω(n)
  → Insertion Sort worst case là Θ(n²), KHÔNG phải O(n²)
     (cả O và Ω đều là n² cho worst case)

TẠI SAO NHẦM?
  Vì trong THỰC TẾ, người ta HAY dùng:
  • Big O khi nói worst case
  • Big Ω khi nói lower bound (không thể nhanh hơn)

  Nhưng CHÍNH XÁC thì:
  Big Ω CỦA MỘT PROBLEM = lower bound cho MỌI algorithm
  giải problem đó — không phải best case của 1 algorithm cụ thể.

VÍ DỤ CHÍNH XÁC:
  "Comparison-based sorting là Ω(n log n)"
  = BẤT KỲ algorithm nào sort bằng so sánh
    đều cần ÍT NHẤT n log n comparisons.
  = Không có cách nào sort NHANH HƠN n log n
    nếu chỉ dùng phép so sánh.
  → Đây là property của PROBLEM, không phải algorithm.
```

#### Ứng Dụng Trong Phỏng Vấn — Chứng Minh Optimality

```
KHI INTERVIEWER HỎI: "Is your solution optimal?"

CÁCH TRẢ LỜI SỬ DỤNG Big Ω:

Tình huống 1 — Tìm kiếm trong unsorted array:
"Any algorithm must examine every element at least once.
 Otherwise, the answer could be in an unexamined element.
 So the lower bound is Ω(n).
 My solution is O(n), which matches Ω(n).
 Therefore, it's optimal."

Tình huống 2 — Sorting:
"The information-theoretic lower bound for comparison sort
 is Ω(n log n). This comes from the decision tree argument:
 there are n! possible permutations, and each comparison
 gives 1 bit of information, so we need at least
 log₂(n!) ≈ n log n comparisons.
 My Mergesort solution is O(n log n), matching this bound."

Tình huống 3 — Graph traversal:
"To ensure we visit every vertex and edge,
 the lower bound is Ω(V + E).
 BFS/DFS runs in O(V + E), so it's optimal."

→ Dùng Ω đúng cách = chứng minh bạn hiểu SÂU,
  không chỉ memorize Big O tables.
```

### Big Θ (Theta) — Tight Bound — Giải Thích Chi Tiết

#### Định nghĩa toán học

```
f(n) = Θ(g(n)) khi ĐỒNG THỜI:
    f(n) = O(g(n))    → g(n) là UPPER bound (trần)
    VÀ
    f(n) = Ω(g(n))    → g(n) là LOWER bound (sàn)

Tương đương: Tồn tại c₁, c₂ > 0 và n₀ sao cho:

    c₁ × g(n)  ≤  f(n)  ≤  c₂ × g(n)     ∀n ≥ n₀
    ─────────     ──────     ─────────
    sàn nhà       nằm giữa   trần nhà

f(n) bị "KẸP" giữa c₁ × g(n) và c₂ × g(n).
```

#### Hiểu bằng hình ảnh

```
Hàm f(n) = 3n² + 7n + 2

          ↑ (operations)
          │
          │              c₂ × n² (trần)  ╱
          │                            ╱
          │                         ╱
          │                      ╱  ← f(n) nằm trong
          │                   ╱      vùng này
          │                ╱
          │             ╱
          │          ╱
          │       ╱    c₁ × n² (sàn)
          │    ╱   ╱
          │ ╱  ╱
          │╱╱
          ├────────────────────────→ n
          0    n₀

Từ n₀ trở đi:
  c₁ × n²  ≤  3n² + 7n + 2  ≤  c₂ × n²
  ────────     ──────────────     ────────
  sàn (Ω)     hàm thực tế        trần (O)

→ f(n) = Θ(n²)
→ f(n) tăng với TỐC ĐỘ ĐÚNG BẰNG n² (chỉ khác hệ số)
```

#### Chứng minh toán học từng bước

```
CHỨNG MINH: f(n) = 3n² + 7n + 2 là Θ(n²)

Cần chứng minh 2 phần:

═══ PHẦN 1: f(n) = O(n²) — tìm upper bound ═══

  Cần: 3n² + 7n + 2 ≤ c₂ × n²

  Khi n ≥ 1:
    7n ≤ 7n²    (vì n ≤ n²)
    2 ≤ 2n²     (vì 1 ≤ n²)

  → 3n² + 7n + 2 ≤ 3n² + 7n² + 2n² = 12n²

  Chọn c₂ = 12, n₀ = 1

  Kiểm tra n = 5: 3(25) + 35 + 2 = 112  ≤  12(25) = 300  ✅


═══ PHẦN 2: f(n) = Ω(n²) — tìm lower bound ═══

  Cần: 3n² + 7n + 2 ≥ c₁ × n²

  Vì 7n ≥ 0 và 2 ≥ 0 khi n ≥ 0:
    3n² + 7n + 2 ≥ 3n²

  Chọn c₁ = 3, n₀ = 0

  Kiểm tra n = 5: 112 ≥ 3(25) = 75  ✅


═══ KẾT HỢP ═══

  c₁ = 3, c₂ = 12, n₀ = 1

  3 × n²  ≤  3n² + 7n + 2  ≤  12 × n²    ∀n ≥ 1

  → f(n) = Θ(n²) ✅

NGHĨA LÀ: 3n² + 7n + 2 "tăng với TỐC ĐỘ ĐÚNG n²"
— không nhanh hơn cũng không chậm hơn.
```

#### Ví dụ thêm: Khi Theta KHÔNG tồn tại

```
QUICKSORT — Theta KHÔNG ÁP DỤNG cho "general case"

  Best case:    Θ(n log n)  — pivot chia đều
  Average case: Θ(n log n)  — random pivot
  Worst case:   Θ(n²)       — pivot luôn min/max

  Ta chỉ có thể nói:
  • Quicksort là O(n²)      — worst case KHÔNG BAO GIỜ tệ hơn n²
  • Quicksort là Ω(n log n) — best case KHÔNG BAO GIỜ tốt hơn n log n

  NHƯNG KHÔNG THỂ nói Quicksort là Θ(n log n) hay Θ(n²)
  vì best ≠ worst → không bị "kẹp" vào MỘT bound duy nhất.

SO SÁNH VỚI MERGESORT:

  Best case:    Θ(n log n)
  Average case: Θ(n log n)
  Worst case:   Θ(n log n)

  → Best = Average = Worst = n log n
  → CÓ THỂ nói: Mergesort là Θ(n log n)
  → Mergesort chạy LUÔN LUÔN cùng tốc độ, bất kể input.
```

#### Big Θ Trong Phỏng Vấn — Khi Nào Dùng?

```
✅ DÙNG Θ khi algorithm có complexity GIỐNG NHAU cho mọi input:
   "Mergesort is Θ(n log n) — it always divides and merges,
    regardless of input order."
   "HashMap lookup is Θ(1) amortized on average."

❌ KHÔNG DÙNG Θ khi best ≠ worst:
   "Quicksort is O(n²)" — nói O, KHÔNG nói Θ
   "Binary search is O(log n)" — best case O(1) ≠ worst O(log n)

💡 NẾU bạn dùng Θ CHÍNH XÁC, interviewer sẽ hỏi:
   "Why Θ and not just O?"
   → Bạn trả lời: "Because the complexity is the same
   for all inputs — best, average, and worst case are
   all n log n. So I can use tight bound Θ."
   → Đây là STRONG SIGNAL = bạn hiểu sâu, không chỉ memorize.
```

### So Sánh Toàn Diện — Big O vs Big Ω vs Big Θ

```
╔═══════════╦════════════════════╦════════════════════════════════════╦══════════════════════╗
║ Ký hiệu    ║ Ý nghĩa            ║ Ví dụ                              ║ Khi nào dùng          ║
╠═══════════╬════════════════════╬════════════════════════════════════╬══════════════════════╣
║           ║ TRẦN NHÀ           ║ Quicksort là O(n²)                ║ 99% phỏng vấn        ║
║ O(g(n))   ║ f(n) ≤ c × g(n)   ║ (worst case không quá n²)         ║ Nêu worst case        ║
║           ║ "không tệ hơn"     ║                                    ║ complexity            ║
╠═══════════╬════════════════════╬════════════════════════════════════╬══════════════════════╣
║           ║ SÀN NHÀ            ║ Comparison sort là Ω(n log n)     ║ Chứng minh            ║
║ Ω(g(n))   ║ f(n) ≥ c × g(n)   ║ (không thể nhanh hơn n log n)     ║ solution là           ║
║           ║ "ít nhất phải"     ║                                    ║ OPTIMAL               ║
╠═══════════╬════════════════════╬════════════════════════════════════╬══════════════════════╣
║           ║ ĐÚNG = BẰNG        ║ Mergesort là Θ(n log n)           ║ Khi best = worst      ║
║ Θ(g(n))   ║ c₁g(n) ≤ f ≤ c₂g  ║ (luôn luôn n log n)              ║ → precise             ║
║           ║ "chính xác là"     ║                                    ║ analysis              ║
╚═══════════╩════════════════════╩════════════════════════════════════╩══════════════════════╝
```

#### Ví Dụ Tổng Hợp — Hiểu Qua Comparison Sort

```
BÀI TOÁN: Sort n numbers bằng phương pháp so sánh.

LOWER BOUND (Ω) — Tại sao Ω(n log n)?
─────────────────────────────────────────
Có n! cách sắp xếp n phần tử (permutations).
Mỗi phép so sánh cho 2 kết quả (true/false) = 1 bit information.
Để phân biệt n! permutations, cần ít nhất log₂(n!) bits.

  log₂(n!) = log₂(1 × 2 × 3 × ... × n)
           = log₂(1) + log₂(2) + ... + log₂(n)
           ≥ (n/2) × log₂(n/2)      (lấy n/2 terms lớn nhất)
           = Θ(n log n)

→ BẤT KỲ comparison sort nào cũng cần Ω(n log n) comparisons.
→ Đây là MATHEMATICAL PROOF, không phải estimate.

UPPER BOUND (O) — Mergesort đạt O(n log n):
─────────────────────────────────────────
  T(n) = 2T(n/2) + O(n) = O(n log n)

SẢN PHẨM CỦA HAI BOUNDS:
─────────────────────────────────────────
  • Problem lower bound: Ω(n log n)
  • Mergesort upper bound: O(n log n)
  • Ω = O → Mergesort là Θ(n log n) VÀ tối ưu!

KHI PHỎNG VẤN, NÓI:
"My sorting solution is O(n log n). This is optimal because
 the information-theoretic lower bound for comparison sort
 is Ω(n log n). Since my upper bound matches the lower bound,
 no comparison-based algorithm can do better."

→ Câu này = INSTANT strong hire signal 🟢
```

#### Quick Reference — Khi Nào Dùng Cái Nào Trong Phỏng Vấn

```
╔═════════════════════════════════════════════════════════════════╗
║  TÌNH HUỐNG                        │ NÓI                        ║
╠═════════════════════════════════════════════════════════════════╣
║ Nêu complexity solution            │ "O(n)" — dùng Big O       ║
║ Hỏi "is this optimal?"             │ Dùng Ω để chứng minh      ║
║ Algorithm luôn cùng speed          │ "Θ(n log n)" — dùng Θ     ║
║ Best case khác worst case          │ Nêu CẢ HAI + dùng O, Ω    ║
║ So sánh 2 algorithms               │ So sánh Big O (worst)     ║
║ Interviewer hỏi "can you prove"    │ Lower bound Ω + matching O ║
║ Chỉ muốn nói nhanh                 │ Dùng Big O — safe nhất    ║
╚═════════════════════════════════════════════════════════════════╝

RULE OF THUMB:
  • 99% thời gian → dùng Big O (safe, industry standard)
  • Muốn impress → dùng Ω khi prove optimality
  • Muốn precise → dùng Θ khi best = worst
  • KHÔNG BAO GIỜ dùng sai Θ khi best ≠ worst → red flag!
```

---

## 2. Bảng Complexity Phổ Biến — Chi Tiết

| Complexity | Tên          | Ví dụ                                                            | n = 10 | n = 100 | n = 10⁶ | Chấp nhận khi |
| ---------- | ------------ | ---------------------------------------------------------------- | ------ | ------- | ------- | ------------- |
| O(1)       | Constant     | Array access `arr[i]`, HashMap lookup, stack push/pop            | 1      | 1       | 1       | Luôn luôn ✅  |
| O(log n)   | Logarithmic  | Binary search, balanced BST lookup, exponentiation by squaring   | 3      | 7       | 20      | Luôn luôn ✅  |
| O(√n)      | Square Root  | Prime checking, sqrt decomposition                               | 3      | 10      | 1000    | Luôn luôn ✅  |
| O(n)       | Linear       | Single loop, linear search, counting occurrences                 | 10     | 100     | 10⁶     | n ≤ 10⁸ ✅    |
| O(n log n) | Linearithmic | Mergesort, Heapsort, Timsort, nhiều divide-and-conquer           | 33     | 664     | 2×10⁷   | n ≤ 10⁶ ✅    |
| O(n²)      | Quadratic    | Nested loops, bubble sort, selection sort, brute force pairs     | 100    | 10⁴     | 10¹² ❌ | n ≤ 10³ ✅    |
| O(n³)      | Cubic        | 3 nested loops, naive matrix multiplication, Floyd-Warshall      | 1000   | 10⁶     | ☠️      | n ≤ 500 ⚠️    |
| O(2ⁿ)      | Exponential  | Subsets, recursion without memoization, brute force combinations | 1024   | 10³⁰    | ☠️      | n ≤ 20 ⚠️     |
| O(n!)      | Factorial    | All permutations, brute force TSP                                | 3.6M   | ☠️      | ☠️      | n ≤ 10 ⚠️     |

### Biểu Đồ Tăng Trưởng — Hình Dung Trực Quan

```
Operations
    |
10⁹ |                                              O(n!)
    |                                         /
    |                                    O(2ⁿ)
    |                               /
    |                          O(n²)
10⁶ |                     /
    |               O(n log n)
    |          /
    |     O(n)
    |  ___________________  O(log n)
    | ___________________  O(1)
    |__________________________________ n
    0     100    1000    10⁴    10⁵

CHÚ Ý: Đường O(n²) "nổ" rất nhanh sau n = 10⁴
→ Đó là lý do interviewer LUÔN hỏi "can you do better?"
khi bạn đưa ra O(n²) solution.
```

---

## 3. Best / Average / Worst Case — Chi Tiết

### Định Nghĩa

```
╔═══════════════╦══════════════════════════════════════════════╗
║ Case           ║ Ý nghĩa                                      ║
╠═══════════════╬══════════════════════════════════════════════╣
║ Best Case      ║ Input TỐT NHẤT cho algorithm                  ║
║                ║ Ví dụ: array đã sorted → insertion sort O(n)  ║
╠═══════════════╬══════════════════════════════════════════════╣
║ Average Case   ║ Input TRUNG BÌNH (random)                     ║
║                ║ Ví dụ: quicksort random pivot → O(n log n)    ║
╠═══════════════╬══════════════════════════════════════════════╣
║ Worst Case     ║ Input TỆ NHẤT cho algorithm                   ║
║                ║ Ví dụ: quicksort pivot = min/max → O(n²)      ║
╚═══════════════╩══════════════════════════════════════════════╝
```

### Ví Dụ Chi Tiết — Quicksort

```python
# BEST CASE O(n log n): pivot luôn chia đều array
[3, 1, 4, 1, 5, 9, 2, 6]
          pivot = 4
[3, 1, 1, 2] [4] [5, 9, 6]    # 2 halves roughly equal
# Mỗi level: n operations (partitioning)
# Số levels: log n (chia đôi mỗi lần)
# → n × log n = O(n log n)

# WORST CASE O(n²): pivot luôn là min hoặc max
[1, 2, 3, 4, 5, 6, 7, 8]
 pivot = 1
[] [1] [2, 3, 4, 5, 6, 7, 8]  # 1 empty, 1 has n-1
# Mỗi level: n operations
# Số levels: n (giảm 1 mỗi lần, không chia đôi)
# → n × n = O(n²)

# FIX: random pivot hoặc median-of-3
# → Average case trở thành O(n log n) với xác suất rất cao
```

### Bảng Best/Average/Worst Cho Các Algorithm Quan Trọng

| Algorithm      | Best       | Average    | Worst      | Space    | Ghi chú                          |
| -------------- | ---------- | ---------- | ---------- | -------- | -------------------------------- |
| Binary Search  | O(1)       | O(log n)   | O(log n)   | O(1)     | Best: target ở giữa              |
| Insertion Sort | O(n)       | O(n²)      | O(n²)      | O(1)     | Best: đã sorted                  |
| Mergesort      | O(n log n) | O(n log n) | O(n log n) | O(n)     | Luôn giống nhau                  |
| Quicksort      | O(n log n) | O(n log n) | O(n²)      | O(log n) | Worst: bad pivot                 |
| HashMap lookup | O(1)       | O(1)       | O(n)       | —        | Worst: all keys collide          |
| BST search     | O(1)       | O(log n)   | O(n)       | —        | Worst: skewed tree (linked list) |

---

## 4. Cách Đếm Operations — Từng Bước

> **Tại sao phải biết ĐẾM?** Vì interviewer KHÔNG chấp nhận "I think it's O(n)." Bạn phải CHỨNG MINH: đếm operations, viết summation, simplify. Đây là skill #1 mà SDE-1/SDE-2 cần có.

### 4.1 Phương Pháp Đếm — Framework 4 Bước

```
FRAMEWORK ĐẾM OPERATIONS:

Bước 1: XÁC ĐỊNH operations cần đếm
        → Comparisons? Assignments? Function calls?
        → Thường đếm "dominant operation" (expensive nhất)

Bước 2: ĐẾM mỗi operation bao nhiêu lần
        → Viết thành BIỂU THỨC toán học theo n

Bước 3: CỘNG tất cả operations
        → Viết thành SUM hoặc PRODUCT

Bước 4: SIMPLIFY bằng Big O rules
        → Drop constants, drop lower-order terms
```

### 4.2 Single Loop — O(n)

#### Ví dụ cơ bản: Tìm Max

```python
def find_max(arr):
    max_val = arr[0]       # 1 assignment
    for x in arr:          # Loop body chạy n lần
        if x > max_val:    #   1 comparison × n = n
            max_val = x    #   1 assignment × (0 to n) = tối đa n
    return max_val         # 1 return

# ĐẾM CHI TIẾT:
# ┌──────────────────────┬───────────┬────────────────────┐
# │ Operation             │ Số lần     │ Giải thích          │
# ├──────────────────────┼───────────┼────────────────────┤
# │ max_val = arr[0]      │ 1         │ Khởi tạo            │
# │ Loop iteration        │ n         │ Duyệt toàn bộ       │
# │ x > max_val (compare) │ n         │ Mỗi iteration 1 lần │
# │ max_val = x (assign)  │ 0 → n    │ Best: 0, Worst: n   │
# │ return                │ 1         │ Kết thúc             │
# └──────────────────────┴───────────┴────────────────────┘
#
# Total: 1 + n + n + (0..n) + 1
#      = 2n + 2  (best)  →  3n + 2  (worst)
#      = O(n)  ← drop constants & lower terms
```

#### Ví dụ: Loop với multiple operations bên trong

```python
def process_array(arr):
    n = len(arr)                # O(1)
    total = 0                   # O(1)
    count = 0                   # O(1)
    for i in range(n):          # n lần
        total += arr[i]         #   O(1) × n   = n
        count += 1              #   O(1) × n   = n
        avg = total / count     #   O(1) × n   = n
        if avg > 100:           #   O(1) × n   = n
            print(avg)          #   O(1) × (0..n)
    return total / n            # O(1)

# Total = 3 + 4n + 1 = 4n + 4
# → O(n)
#
# KEY INSIGHT: Dù loop body có 4-5 operations,
# mỗi cái đều O(1) → body = O(1)
# n iterations × O(1) body = O(n)
#
# RULE: Số operations TRONG loop body = CONSTANT
#       → nhân với n → O(n)
#       KHÔNG phải O(4n) hay O(5n) — constants drop!
```

#### ⚠️ Trap: Loop body KHÔNG PHẢI luôn O(1)!

```python
# CASE 1: Loop body chứa ANOTHER operation O(k)
def has_word(sentences, target):
    for sentence in sentences:            # n sentences
        if target in sentence:            # O(len(sentence))!
            return True                   #   KHÔNG phải O(1)!

# Nếu mỗi sentence dài trung bình m characters:
# → Total = n × m = O(n × m)
# → KHÔNG phải O(n)!
#
# NARRATE: "For each of the n sentences, the 'in' check
#           scans up to m characters. Total: O(n × m)."

# CASE 2: Loop body chứa sort
def sort_each_row(matrix):
    for row in matrix:         # n rows
        row.sort()             # O(m log m) per row!

# Total = n × m log m = O(n × m log m)

# CASE 3: Loop body chứa list copy/slice
for i in range(n):
    copy = arr[:]              # O(n) mỗi lần copy TOÀN BỘ array!

# Total = n × n = O(n²) ← HIDDEN quadratic!
# Đây là BẪY phổ biến trong phỏng vấn Python.
```

#### Tóm tắt Single Loop

```
╔═══════════════════════════════════════════════════════════╗
║  SINGLE LOOP COMPLEXITY                                    ║
╠═══════════════════════════════════════════════════════════╣
║  Loop n times × O(1) body     = O(n)                      ║
║  Loop n times × O(m) body     = O(n × m)                  ║
║  Loop n times × O(log n) body = O(n log n)                ║
║  Loop n times × O(n) body     = O(n²)  ← HIDDEN!         ║
║                                                           ║
║  → LUÔN kiểm tra body cost TRƯỚC khi kết luận!           ║
╚═══════════════════════════════════════════════════════════╝
```

### 4.3 Nested Loops — Chi Tiết Toán Học

#### Case 1: Cả hai loop chạy n lần — O(n²)

```python
for i in range(n):           # n lần
    for j in range(n):       # n lần MỖI iteration của i
        process(i, j)        # O(1)

# ĐẾM:
# i=0: j chạy n lần
# i=1: j chạy n lần
# i=2: j chạy n lần
# ...
# i=n-1: j chạy n lần
#
# Tổng = n + n + n + ... + n (n lần)
#       = n × n = n²
# → O(n²)
```

#### Case 2: Inner loop PHỤ THUỘC outer — VẪN O(n²)!

```python
# DẠNG 1: j bắt đầu từ i+1
for i in range(n):
    for j in range(i+1, n):     # j chạy n-1-i lần
        process(i, j)

# ĐẾM CHI TIẾT:
# i=0:   j chạy n-1 lần    (j = 1, 2, ..., n-1)
# i=1:   j chạy n-2 lần    (j = 2, 3, ..., n-1)
# i=2:   j chạy n-3 lần    (j = 3, 4, ..., n-1)
# ...
# i=n-2: j chạy 1 lần      (j = n-1)
# i=n-1: j chạy 0 lần      (không vào loop)
#
# Tổng = (n-1) + (n-2) + (n-3) + ... + 1 + 0
#
# ═══ TOÁN HỌC: Công thức tổng dãy số ═══
#
# Sum = 1 + 2 + 3 + ... + (n-1)
#
# Gauss's formula: Σ(k=1 → m) k = m(m+1)/2
#
# Với m = n-1:
# Sum = (n-1)(n-1+1)/2 = (n-1)n/2 = n²/2 - n/2
#
# Big O: drop 1/2 (constant), drop -n/2 (lower-order)
# → O(n²)
#
# TRỰC QUAN:
# ┌─────────────────────┐
# │ × × × × × × × × ×  │  i=0: n-1 = 8 ops
# │   × × × × × × × ×  │  i=1: n-2 = 7 ops
# │     × × × × × × ×  │  i=2: n-3 = 6 ops
# │       × × × × × ×  │  i=3: n-4 = 5 ops
# │         × × × × ×  │  i=4: n-5 = 4 ops
# │           × × × ×  │  i=5: n-6 = 3 ops
# │             × × ×  │  i=6: n-7 = 2 ops
# │               × ×  │  i=7: n-8 = 1 op
# │                 ×  │  i=8: 0 ops
# └─────────────────────┘
# = Tam giác = n²/2 ≈ HALF of n×n grid
# → VẪN O(n²)! Constants drop.


# DẠNG 2: j bắt đầu từ 0 đến i
for i in range(n):
    for j in range(i):          # j chạy i lần
        process(i, j)

# ĐẾM:
# i=0: 0 lần
# i=1: 1 lần
# i=2: 2 lần
# ...
# i=n-1: n-1 lần
#
# Tổng = 0 + 1 + 2 + ... + (n-1) = n(n-1)/2
# → O(n²) — CÙNG kết quả!


# DẠNG 3: j chạy từ 0 đến 2*i
for i in range(n):
    for j in range(2*i):        # j chạy 2i lần
        process(i, j)

# Tổng = 0 + 2 + 4 + ... + 2(n-1)
#       = 2 × (0 + 1 + 2 + ... + (n-1))
#       = 2 × n(n-1)/2 = n(n-1) = n² - n
# → O(n²)
```

#### ⚠️ NHƯNG: Nested loop KHÔNG LUÔN là O(n²)!

```python
# CASE A: Inner loop là CONSTANT → O(n)
for i in range(n):
    for j in range(10):         # 10 lần, KHÔNG phải n!
        process(i, j)

# Total = n × 10 = 10n → O(n)
# GIẢI THÍCH: Inner loop không phụ thuộc n
# → Nó là constant → chỉ nhân thêm hệ số → drop


# CASE B: Inner loop là O(log n) → O(n log n)
for i in range(n):
    j = i
    while j > 0:
        process(i, j)
        j //= 2                # Chia đôi → log n

# Mỗi inner loop: O(log i) ≈ O(log n)
# Total = Σ(i=1→n) log(i) = log(1×2×3×...×n) = log(n!)
#
# Stirling's approximation: log(n!) ≈ n log n - n
# → O(n log n)


# CASE C: Two pointers — nested NHƯNG O(n)!
left = 0
for right in range(n):          # right: 0 → n-1
    while left < right and bad_condition:
        left += 1               # left CHỈ TĂNG, KHÔNG reset!

# PHÂN TÍCH:
# right di chuyển n lần (outer loop)
# left di chuyển TỐI ĐA n lần TỔNG CỘNG (không reset)
# → Total operations = n (right) + n (left) = 2n
# → O(n)
#
# TẠI SAO KHÔNG O(n²)?
# Vì left KHÔNG reset về 0 mỗi iteration!
# Nếu left = 0 ở đầu mỗi outer loop → O(n²)
# Nhưng left GIỮ NGUYÊN vị trí → amortized O(1) per iteration
#
# NARRATE: "Although this looks like nested loops,
#           the left pointer only moves forward — never resets.
#           Total movements: at most n for right + n for left = O(n)."
#
# ĐÂY LÀ PATTERN SLIDING WINDOW / TWO POINTERS
# → RẤT HAY GẶP trong phỏng vấn
# → Nhiều candidate nói sai O(n²) → mất điểm


# CASE D: Inner loop giảm dần nhưng NHANH → O(n)
for i in range(n):
    j = n
    while j > 0:
        process(i, j)
        j //= 2

# CHỜ: mỗi inner loop chạy O(log n) lần
# → Total = n × O(log n) = O(n log n)
# → KHÔNG phải O(n²)!
```

#### Bảng Tổng Hợp Nested Loops

```
╔═══════════════════════════════════════════════════════════════╗
║  PATTERN                            │ COMPLEXITY              ║
╠═══════════════════════════════════════════════════════════════╣
║ for i(n): for j(n):                 │ O(n²)                  ║
║ for i(n): for j(i+1, n):            │ O(n²) — n(n-1)/2      ║
║ for i(n): for j(i):                 │ O(n²) — n(n-1)/2      ║
║ for i(n): for j(10):                │ O(n)  — constant inner ║
║ for i(n): while j > 0: j//=2       │ O(n log n)             ║
║ Two pointers (left never resets)     │ O(n)  — amortized     ║
║ for i(n): for j(m):  [m ≠ n]       │ O(n × m)               ║
║ 3 nested loops: for i(n) j(n) k(n) │ O(n³)                  ║
╚═══════════════════════════════════════════════════════════════╝

QUY TẮC VÀNG:
  1. Xác định inner loop chạy BAO NHIÊU LẦN TỔNG CỘNG
  2. Viết thành SUM, tính sum
  3. ĐỪNG giả định nested = n² — kiểm tra!
```

### 4.4 Loop Với Bước Nhảy Khác Thường — Toán Học Chi Tiết

> Đây là phần HAY BỊ HỎI trong phỏng vấn vì nhiều candidate không biết đếm khi loop variable tăng/giảm theo cách khác `i++`.

#### Pattern 1: Nhân đôi — O(log n)

```python
i = 1
while i < n:
    process(i)    # O(1)
    i *= 2        # i = 1, 2, 4, 8, 16, ..., ?

# TOÁN HỌC:
# Sau k bước: i = 2^k
# Loop dừng khi: i ≥ n → 2^k ≥ n
# → k ≥ log₂(n)
# → Số bước = ⌈log₂(n)⌉ = O(log n)
#
# TRACE với n = 100:
# k=0: i=1    (1 < 100 ✓)
# k=1: i=2    (2 < 100 ✓)
# k=2: i=4    (4 < 100 ✓)
# k=3: i=8    (8 < 100 ✓)
# k=4: i=16   (16 < 100 ✓)
# k=5: i=32   (32 < 100 ✓)
# k=6: i=64   (64 < 100 ✓)
# k=7: i=128  (128 < 100 ✗) → STOP!
# → 7 bước = ⌈log₂(100)⌉ = ⌈6.64⌉ = 7 ✅
```

#### Pattern 2: Chia đôi — O(log n)

```python
i = n
while i >= 1:
    process(i)
    i //= 2       # i = n, n/2, n/4, ..., 1

# TOÁN HỌC:
# Sau k bước: i = n / 2^k
# Loop dừng khi: i < 1 → n / 2^k < 1 → 2^k > n
# → k > log₂(n)
# → Số bước = ⌊log₂(n)⌋ + 1 = O(log n)
#
# CŨNG ÁP DỤNG CHO:
# i //= 3      → O(log₃ n) = O(log n)  (log base doesn't matter)
# i //= 10     → O(log₁₀ n) = O(log n)
# i = i >> 1   → right shift = chia 2 → O(log n)
```

#### Pattern 3: Bình phương — O(log log n)

```python
i = 2
while i < n:
    process(i)
    i = i * i     # i = 2, 4, 16, 256, 65536, ...

# TOÁN HỌC (cấp cao):
# Sau k bước: i = 2^(2^k)
# Loop dừng khi: 2^(2^k) ≥ n → 2^k ≥ log₂(n)
# → k ≥ log₂(log₂(n))
# → O(log log n) — RẤT HIẾM nhưng cần biết
#
# n = 10⁹: log log n ≈ log(30) ≈ 5 — cực nhanh!
```

#### Pattern 4: Căn bậc hai — O(√n)

```python
# DẠNG 1: i * i < n
i = 0
while i * i < n:
    process(i)
    i += 1

# TOÁN HỌC:
# Loop dừng khi: i² ≥ n → i ≥ √n
# → Số bước = ⌈√n⌉ = O(√n)
#
# ỨNG DỤNG:
# • Kiểm tra số nguyên tố: thử chia từ 2 đến √n
# • Sqrt decomposition (competitive programming)

# DẠNG 2: n giảm bằng cách chia cho i
# (tìm ước số)
for i in range(1, int(n**0.5) + 1):
    if n % i == 0:
        print(i, n // i)

# → O(√n) — vì loop chạy đến √n
```

#### Pattern 5: Harmonic Series — O(n log n)

```python
# Nested nhưng KHÔNG phải O(n²)!
for i in range(1, n+1):
    for j in range(i, n+1, i):  # j = i, 2i, 3i, ..., n
        process(i, j)

# ĐẾM CHI TIẾT:
# i=1: j chạy n/1 = n lần       (j = 1, 2, 3, ..., n)
# i=2: j chạy n/2 lần           (j = 2, 4, 6, ..., n)
# i=3: j chạy n/3 lần           (j = 3, 6, 9, ..., n)
# ...
# i=n: j chạy n/n = 1 lần       (j = n)
#
# Tổng = n/1 + n/2 + n/3 + ... + n/n
#       = n × (1 + 1/2 + 1/3 + ... + 1/n)
#       = n × Hₙ
#
# ═══ TOÁN HỌC: Harmonic Series ═══
# Hₙ = 1 + 1/2 + 1/3 + ... + 1/n ≈ ln(n) + γ
# (γ ≈ 0.5772 = Euler–Mascheroni constant)
#
# → Tổng = n × ln(n) ≈ n × log(n)
# → O(n log n)
#
# ỨNG DỤNG: Sieve of Eratosthenes!
# Đó là lý do Sieve có complexity O(n log log n)

# NARRATE: "The inner loop runs n/i times for each i.
#           Summing across all i gives the harmonic series,
#           which is approximately n × ln(n) = O(n log n)."
```

#### Pattern 6: Geometric Series — O(n)

```python
# Chia đôi input mỗi level nhưng process TẤT CẢ
def process_levels(n):
    size = n
    while size >= 1:
        for i in range(size):    # process 'size' elements
            work(i)
        size //= 2               # chia đôi

# ĐẾM:
# Level 0: n operations
# Level 1: n/2 operations
# Level 2: n/4 operations
# ...
# Level log n: 1 operation
#
# Tổng = n + n/2 + n/4 + ... + 1
#
# ═══ TOÁN HỌC: Geometric Series ═══
# a + ar + ar² + ... + ar^k = a × (1 - r^(k+1)) / (1 - r)
#
# Với a = n, r = 1/2, k = log n:
# Sum = n × (1 - (1/2)^(log n + 1)) / (1 - 1/2)
#     = n × (1 - 1/n) / (1/2)
#     = 2n × (1 - 1/n)
#     ≈ 2n
# → O(n)!
#
# KEY INSIGHT: Dù có log n levels,
# mỗi level làm ÍT HƠN một nửa → tổng = 2n = O(n)
# Đây là lý do nhiều divide-and-conquer có O(n) work.

# NARRATE: "Each level does half the work of the previous.
#           The geometric series sum converges to 2n = O(n)."
```

#### Bảng Tổng Hợp Bước Nhảy

```
╔══════════════════════════════╦══════════════╦═══════════════════╗
║ Pattern                       ║ Complexity    ║ Toán học           ║
╠══════════════════════════════╬══════════════╬═══════════════════╣
║ i *= 2  (nhân đôi)           ║ O(log n)     ║ 2^k = n → k=logn  ║
║ i //= 2 (chia đôi)           ║ O(log n)     ║ n/2^k = 1 → k=logn║
║ i *= 3  (nhân ba)            ║ O(log n)     ║ log base irrelevant║
║ i = i*i (bình phương)        ║ O(log log n) ║ 2^(2^k) = n        ║
║ i*i < n (căn)                ║ O(√n)        ║ i² = n → i = √n    ║
║ Harmonic (n/1+n/2+...+n/n)   ║ O(n log n)   ║ Hₙ ≈ ln(n)         ║
║ Geometric (n+n/2+n/4+...+1)  ║ O(n)         ║ Sum → 2n            ║
╚══════════════════════════════╩══════════════╩═══════════════════╝
```

### 4.5 Recursion — Đếm Bằng Recursion Tree (Chi Tiết)

> **Tại sao quan trọng?** Recursion xuất hiện trong >60% bài phỏng vấn (trees, graphs, DP, backtracking). Biết đếm complexity cho recursion = MUST HAVE.

#### Framework Đếm Recursion — 3 Bước

```
Bước 1: VẼ recursion tree (ít nhất 3 levels)
        → Xác định: branching factor, depth, work per node

Bước 2: ĐẾM tổng work
        → Total = Σ (work at each level)
        → Hoặc: Total = (số nodes) × (work per node)

Bước 3: SPACE = max depth của tree
        → Vì call stack giữ tất cả frames trên 1 đường path
```

#### Pattern 1: Linear Recursion — O(n) time, O(n) space

```python
def factorial(n):
    if n <= 1: return 1           # BASE CASE
    return n * factorial(n - 1)   # 1 recursive call, giảm 1

# RECURSION TREE (thực ra là "chain"):
#
# factorial(5) → factorial(4) → factorial(3) → factorial(2) → factorial(1)
#     5×           4×              3×              2×            return 1
#
# PHÂN TÍCH:
# • Branching factor: 1 (chỉ 1 recursive call)
# • Depth: n (giảm 1 mỗi level)
# • Work per node: O(1) (chỉ 1 phép nhân)
#
# TIME  = n nodes × O(1) work = O(n)
# SPACE = depth = O(n) ← call stack!
#
# TRACE call stack khi n = 5:
# ┌────────────────────┐
# │ factorial(5)        │  ← top of stack
# │ factorial(4)        │
# │ factorial(3)        │
# │ factorial(2)        │
# │ factorial(1) = 1    │  ← base case, start returning
# └────────────────────┘
# Stack depth = 5 = n → O(n) space
```

#### Pattern 2: Binary Recursion — O(2ⁿ) hoặc O(n) (với memo)

```python
def fib(n):
    if n <= 1: return n
    return fib(n-1) + fib(n-2)   # 2 recursive calls

# RECURSION TREE cho fib(6):
#
#                          fib(6)
#                       /          \
#                  fib(5)            fib(4)
#                /      \           /      \
#           fib(4)      fib(3)   fib(3)   fib(2)
#          /    \       /   \     /   \     /  \
#       fib(3) fib(2) f(2) f(1) f(2) f(1) f(1) f(0)
#       /  \   / \    / \
#     f(2) f(1) f(1) f(0) f(1) f(0)
#     / \
#   f(1) f(0)
#
# PHÂN TÍCH:
# • Branching factor: 2 (2 recursive calls)
# • Depth: n
# • Work per node: O(1)
#
# ═══ TOÁN HỌC: Đếm nodes ═══
# Level 0: 1 node
# Level 1: 2 nodes (tối đa)
# Level 2: 4 nodes (tối đa)
# ...
# Level k: 2^k nodes (tối đa)
#
# Total nodes ≤ 1 + 2 + 4 + ... + 2^n = 2^(n+1) - 1
# → O(2ⁿ)
#
# CHÍNH XÁC HƠN: Fibonacci tree không phải "full" binary tree.
# Exact number of calls = fib(n+1) - 1 ≈ φⁿ / √5
# (φ = golden ratio ≈ 1.618)
# → Chính xác là O(φⁿ) ≈ O(1.618ⁿ)
# → Nhưng trong phỏng vấn, nói O(2ⁿ) là ACCEPTABLE.
#
# SPACE = max depth = O(n)
# (chỉ tính đường path dài nhất, không phải tất cả nodes)


# ═══ VỚI MEMOIZATION → O(n)! ═══
memo = {}
def fib_memo(n):
    if n in memo: return memo[n]    # O(1) lookup
    if n <= 1: return n
    memo[n] = fib_memo(n-1) + fib_memo(n-2)
    return memo[n]

# RECURSION TREE VỚI MEMO (chỉ compute 1 lần):
#
# fib(6) → fib(5) → fib(4) → fib(3) → fib(2) → fib(1) ← base
#                                                → fib(0) ← base
#                             → fib(1) ← CACHED!
#                  → fib(2) ← CACHED!
#           → fib(3) ← CACHED!
#        → fib(4) ← CACHED!
#
# Mỗi fib(k) chỉ tính MỘT LẦN → n unique subproblems
# TIME = O(n), SPACE = O(n) (memo + call stack)
```

#### Pattern 3: Divide & Conquer — O(n log n)

```python
def mergesort(arr):
    if len(arr) <= 1: return arr
    mid = len(arr) // 2
    left = mergesort(arr[:mid])      # T(n/2)
    right = mergesort(arr[mid:])     # T(n/2)
    return merge(left, right)         # O(n) merge step

# RECURSION TREE:
#
# Level 0: [████████████████]              → n work (merge)
#           /              \
# Level 1: [████████] [████████]           → n work (n/2 + n/2)
#           /    \     /    \
# Level 2: [████] [████] [████] [████]     → n work (n/4 × 4)
#           /  \  /  \   /  \  /  \
# Level 3: [██][██][██][██][██][██][██][██] → n work (n/8 × 8)
#
# TOÁN HỌC:
# Recurrence: T(n) = 2T(n/2) + O(n)
#
# Level k: 2^k subproblems × size n/2^k each
#          Work per level = 2^k × (n/2^k) = n  ← CONSTANT!
#
# Number of levels: n/2^k = 1 → k = log₂(n)
#
# Total = n × log₂(n) = O(n log n)
# Space = O(n) auxiliary array + O(log n) stack = O(n)
```

#### Pattern 4: Backtracking — O(k^n) hoặc O(n!)

```python
# Subsets: chọn hoặc không chọn mỗi element → 2ⁿ
def subsets(nums, index, current, result):
    if index == len(nums):
        result.append(current[:])
        return
    # CHOOSE: include nums[index]
    current.append(nums[index])
    subsets(nums, index + 1, current, result)
    # UN-CHOOSE: exclude nums[index]
    current.pop()
    subsets(nums, index + 1, current, result)

# RECURSION TREE cho [1, 2, 3]:
#                    []
#                  /    \
#               [1]      []
#              /   \    /   \
#          [1,2] [1] [2]    []
#          / \   / \  / \   / \
#     [123][12][13][1][23][2][3][]
#
# Branching factor = 2 (include or exclude)
# Depth = n (one decision per element)
# Total leaves = 2ⁿ = tất cả subsets
# TIME = O(2ⁿ × n)  ← 2ⁿ subsets × O(n) copy each
# SPACE = O(n) ← recursion depth


# Permutations: n! orderings
def permute(nums, start, result):
    if start == len(nums):
        result.append(nums[:])
        return
    for i in range(start, len(nums)):
        nums[start], nums[i] = nums[i], nums[start]  # swap
        permute(nums, start + 1, result)
        nums[start], nums[i] = nums[i], nums[start]  # un-swap

# Branching factor GIẢM mỗi level:
# Level 0: n choices
# Level 1: n-1 choices
# Level 2: n-2 choices
# ...
# Total = n × (n-1) × (n-2) × ... × 1 = n!
# TIME = O(n! × n)  ← n! permutations × O(n) copy
```

#### Pattern 5: Tree Recursion với Work ≠ O(1)

```python
# Mỗi node làm O(n) work thay vì O(1)
def count_inversions(arr):
    if len(arr) <= 1: return arr, 0
    mid = len(arr) // 2
    left, left_inv = count_inversions(arr[:mid])
    right, right_inv = count_inversions(arr[mid:])
    merged, split_inv = merge_count(left, right)  # O(n) work
    return merged, left_inv + right_inv + split_inv

# Giống Mergesort: T(n) = 2T(n/2) + O(n) = O(n log n)

# SO SÁNH: Nếu work per node = O(n²):
# T(n) = 2T(n/2) + O(n²)
# Master Theorem: a=2, b=2, c=2 → log₂(2) = 1 < 2
# → Case 3: T(n) = O(n²)  ← work dominates recursion!
```

#### Bảng Tổng Hợp Recursion

```
╔═══════════════════════════╦═══════════╦══════════╦════════════════════╗
║ Pattern                    ║ Time       ║ Space    ║ Ví dụ               ║
╠═══════════════════════════╬═══════════╬══════════╬════════════════════╣
║ Linear: T(n) = T(n-1)+O(1)║ O(n)      ║ O(n)    ║ Factorial, DFS list  ║
║ Binary: T(n) = 2T(n-1)    ║ O(2ⁿ)    ║ O(n)    ║ Fibonacci (no memo)  ║
║ Binary + memo              ║ O(n)      ║ O(n)    ║ Fibonacci (memo)     ║
║ D&C: T(n) = 2T(n/2)+O(n)  ║ O(n log n)║ O(n)    ║ Mergesort            ║
║ D&C: T(n) = 2T(n/2)+O(1)  ║ O(n)      ║ O(log n)║ Count nodes in tree  ║
║ D&C: T(n) = T(n/2)+O(1)   ║ O(log n)  ║ O(log n)║ Binary search        ║
║ Backtrack: 2ⁿ subsets      ║ O(2ⁿ × n) ║ O(n)    ║ Subset generation    ║
║ Backtrack: n! perms         ║ O(n! × n) ║ O(n)    ║ Permutations         ║
║ Backtrack: nᵏ combos        ║ O(nᵏ)     ║ O(k)    ║ N-Queens approx.     ║
╚═══════════════════════════╩═══════════╩══════════╩════════════════════╝

SPACE luôn = MAX DEPTH (không phải tổng nodes!)
Vì call stack chỉ giữ 1 path từ root đến leaf.
```

### 4.6 Master Theorem — Chi Tiết & Intuition

> **Master Theorem** là "công thức thần" để tính complexity cho mọi divide-and-conquer. Nếu bạn biết recurrence, bạn biết NGAY answer.

#### Công thức

```
T(n) = a × T(n/b) + O(nᶜ)

 a = số subproblems (bao nhiêu recursive calls?)
 b = factor chia nhỏ (mỗi call giảm input bao nhiêu?)
 c = exponent của work ngoài recursion (combine step)

So sánh c với log_b(a):
```

#### Intuition Trực Quan — 3 Cases

```
CASE 1:  c < log_b(a)  →  T(n) = O(n^(log_b(a)))
─────────────────────────────────────────────────
"Recursion NẶNG hơn combine step"
Work TĂNG theo mỗi level → most work ở BOTTOM (leaves)

Hình dung:
Level 0: ○                    → ít work
Level 1: ○ ○ ○                → nhiều work hơn
Level 2: ○ ○ ○ ○ ○ ○ ○ ○ ○   → NHIỀU work nhất
→ Leaves dominate → count leaves = a^(log_b(n)) = n^(log_b(a))


CASE 2:  c = log_b(a)  →  T(n) = O(nᶜ × log n)
─────────────────────────────────────────────────
"Recursion và combine step CÂN BẰNG"
Mỗi level có CÙNG LƯỢNG work → total = work_per_level × levels

Hình dung:
Level 0: ████████████████  → n work
Level 1: ████████████████  → n work  (same!)
Level 2: ████████████████  → n work  (same!)
→ log n levels × n work each = O(n log n)


CASE 3:  c > log_b(a)  →  T(n) = O(nᶜ)
─────────────────────────────────────────────────
"Combine step NẶNG hơn recursion"
Work GIẢM theo mỗi level → most work ở TOP (root)

Hình dung:
Level 0: ████████████████████████  → NHIỀU work nhất
Level 1: ████████████              → ít hơn
Level 2: ████████                  → ít nhất
→ Root dominates → T(n) = O(nᶜ) (cost of root only)
```

#### Ví dụ Chi Tiết — Áp Dụng Từng Bước

```
═══ VÍ DỤ 1: Mergesort ═══
T(n) = 2T(n/2) + O(n)

Bước 1: Xác định a, b, c
  a = 2 (chia thành 2 subproblems)
  b = 2 (mỗi subproblem size n/2)
  c = 1 (merge step là O(n¹))

Bước 2: Tính log_b(a)
  log₂(2) = 1

Bước 3: So sánh
  c = 1 = log₂(2) = 1  →  c = log_b(a)  →  CASE 2

Bước 4: Áp dụng
  T(n) = O(nᶜ × log n) = O(n¹ × log n) = O(n log n) ✅


═══ VÍ DỤ 2: Binary Search ═══
T(n) = T(n/2) + O(1)

  a = 1 (chỉ 1 recursive call)
  b = 2 (size giảm một nửa)
  c = 0 (work ngoài recursion là O(n⁰) = O(1))
  log₂(1) = 0
  c = 0 = log_b(a) → CASE 2
  T(n) = O(n⁰ × log n) = O(log n) ✅


═══ VÍ DỤ 3: Strassen Matrix Multiply ═══
T(n) = 7T(n/2) + O(n²)

  a = 7  (7 recursive multiplications)
  b = 2  (matrices half in each dimension)
  c = 2  (O(n²) addition work)
  log₂(7) ≈ 2.807
  c = 2 < 2.807 = log_b(a) → CASE 1
  T(n) = O(n^(log₂7)) = O(n^2.807) ✅
  (better than naive O(n³)!)


═══ VÍ DỤ 4: Karatsuba Multiplication ═══
T(n) = 3T(n/2) + O(n)

  a = 3  (3 recursive multiplications thay vì 4)
  b = 2
  c = 1  (O(n) additions)
  log₂(3) ≈ 1.585
  c = 1 < 1.585 = log_b(a) → CASE 1
  T(n) = O(n^1.585) ✅ (tốt hơn naive O(n²))


═══ VÍ DỤ 5: Closest Pair of Points ═══
T(n) = 2T(n/2) + O(n log n)

  ⚠️ KHÔNG ÁP DỤNG ĐƯỢC Master Theorem trực tiếp!
  Vì f(n) = n log n ≠ nᶜ (có thêm log factor)

  Giải bằng recursion tree:
  Level 0: n log n
  Level 1: 2 × (n/2) log(n/2) = n(log n - 1) = n log n - n
  → Mỗi level ≈ n log n, có log n levels
  → T(n) = O(n log²n)

  (Có thể optimize merge step → O(n) → T(n) = O(n log n))
```

#### Quick Reference — Master Theorem

```
╔══════════════════════════════════════════════════════════════════╗
║  Recurrence              │ a  b  c │ Case │ Result              ║
╠══════════════════════════════════════════════════════════════════╣
║ T(n)= T(n/2)+O(1)       │ 1  2  0 │  2   │ O(log n)           ║
║ T(n)= T(n/2)+O(n)       │ 1  2  1 │  3   │ O(n)               ║
║ T(n)= 2T(n/2)+O(1)      │ 2  2  0 │  1   │ O(n)               ║
║ T(n)= 2T(n/2)+O(n)      │ 2  2  1 │  2   │ O(n log n)         ║
║ T(n)= 2T(n/2)+O(n²)     │ 2  2  2 │  3   │ O(n²)              ║
║ T(n)= 3T(n/2)+O(n)      │ 3  2  1 │  1   │ O(n^1.585)         ║
║ T(n)= 4T(n/2)+O(n)      │ 4  2  1 │  1   │ O(n²)              ║
║ T(n)= 7T(n/2)+O(n²)     │ 7  2  2 │  1   │ O(n^2.807)         ║
║ T(n)= T(n/3)+O(1)       │ 1  3  0 │  2   │ O(log n)           ║
║ T(n)= 3T(n/3)+O(n)      │ 3  3  1 │  2   │ O(n log n)         ║
╚══════════════════════════════════════════════════════════════════╝

NHỚ: log₂(2) = 1, log₂(4) = 2, log₂(8) = 3,
      log₂(3) ≈ 1.585, log₂(7) ≈ 2.807
```

### 4.7 Bài Tập Đếm Thực Hành — Interview Style

```python
# === BÀI 1: HashMap + Loop ===
def two_sum(nums, target):
    seen = {}                           # O(1) init
    for i, num in enumerate(nums):      # n iterations
        comp = target - num             # O(1)
        if comp in seen:                # O(1) amortized lookup
            return [seen[comp], i]      # O(1)
        seen[num] = i                   # O(1) amortized insert
    return []

# ĐẾM: n × O(1) = O(n) time, O(n) space (HashMap)
# NARRATE: "Single pass O(n). HashMap gives O(1) lookup."


# === BÀI 2: Sort + Two Pointers ===
def three_sum(nums):
    nums.sort()                          # O(n log n)
    result = []
    for i in range(len(nums) - 2):       # n iterations
        left, right = i+1, len(nums)-1
        while left < right:              # ← nested!
            total = nums[i] + nums[left] + nums[right]
            if total == 0:
                result.append([nums[i], nums[left], nums[right]])
                left += 1; right -= 1
            elif total < 0: left += 1
            else: right -= 1

# ĐẾM:
# Sort: O(n log n)
# Outer loop: n iterations
# Inner while: left + right move tối đa n lần MỖI outer iteration
# → n × n = O(n²)
# Total: O(n log n) + O(n²) = O(n²)  ← n² dominates


# === BÀI 3: DFS trên tree ===
def max_depth(root):
    if not root: return 0               # O(1) base case
    left = max_depth(root.left)          # T(left subtree)
    right = max_depth(root.right)        # T(right subtree)
    return max(left, right) + 1          # O(1) combine

# ĐẾM:
# Visit mỗi node ĐÚNG 1 LẦN → O(n) time
# Space = max depth = O(h)
# Balanced: O(log n), Skewed: O(n)


# === BÀI 4: BFS trên graph ===
def bfs(graph, start):
    visited = {start}                    # O(1)
    queue = [start]                      # O(1)
    while queue:                         # ← chạy bao nhiêu lần?
        node = queue.pop(0)              # O(1) amortized w/ deque
        for neighbor in graph[node]:     # degree(node) iterations
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)

# ĐẾM:
# While loop: mỗi node vào queue TỐI ĐA 1 lần → O(V)
# Inner for: mỗi edge xét TỐI ĐA 2 lần → O(E)
# Total: O(V + E)
# ⚠️ KHÔNG phải O(V × E)!
```

---

## 5. Amortized Analysis — Trung Bình Dài Hạn (Chi Tiết)

> **Amortized analysis** là kỹ thuật phân tích complexity khi MỘT operation đôi khi rất đắt, nhưng trung bình trên NHIỀU operations thì rẻ. Đây là concept HAY BỊ HỎI ở level Senior+.

### 5.1 Định Nghĩa Chính Thức

```
AMORTIZED COST = Tổng chi phí THỰC TẾ cho n operations
                 chia cho n operations

Ký hiệu: T_amortized = (Σ cost of n ops) / n

KEY INSIGHT:
  Worst case 1 operation = O(n)     ← đắt
  Amortized per operation = O(1)     ← rẻ trung bình

KHÁC VỚI AVERAGE CASE:
┌────────────────────────────────────────────────────────────┐
│ Average case: dựa trên XÁC SUẤT — "trung bình" input      │
│ Amortized:    dựa trên WORST CASE — "trung bình" operations│
│                                                            │
│ Average = probabilistic (có thể xui)                       │
│ Amortized = GUARANTEED (luôn đúng cho n ops liên tiếp)    │
│                                                            │
│ → Amortized MẠNH HƠN average case vì không có "xui"       │
└────────────────────────────────────────────────────────────┘
```

### 5.2 Ba Phương Pháp Phân Tích Amortized

```
╔══════════════════════════════════════════════════════════════════╗
║  PHƯƠNG PHÁP         │ Ý TƯỞNG                │ KHI NÀO DÙNG   ║
╠══════════════════════════════════════════════════════════════════╣
║ 1. Aggregate         │ Tính tổng cost cho n   │ Đơn giản nhất  ║
║    (Summation)       │ ops, chia cho n        │ Dynamic array   ║
╠══════════════════════════════════════════════════════════════════╣
║ 2. Accounting        │ "Charge nhiều hơn" cho │ Stack multipop  ║
║    (Banker's)        │ ops rẻ, "tiết kiệm"   │ increment       ║
║                      │ cho ops đắt            │ counter         ║
╠══════════════════════════════════════════════════════════════════╣
║ 3. Potential         │ Định nghĩa "potential  │ Splay trees     ║
║    (Physicist's)     │ energy" function       │ Fibonacci heaps ║
║                      │ cho data structure     │ (advanced)       ║
╚══════════════════════════════════════════════════════════════════╝

Trong PHỎNG VẤN: chỉ cần biết Aggregate method + intuition.
Accounting method = bonus. Potential method = overkill.
```

---

### 5.3 Dynamic Array (ArrayList) Resize — Chi Tiết

> Đây là ví dụ KINH ĐIỂN nhất, hay bị hỏi nhất.

#### Cơ Chế Hoạt Động

```
Dynamic Array = array tự tăng size khi full.

STRATEGY: Khi full → tạo array mới GẤP ĐÔI size → copy tất cả.

TẠI SAO GẤP ĐÔI (×2) mà không phải +1 hay +10?
• +1 mỗi lần: n appends → copy 1+2+3+...+n = O(n²) ← TỆ!
• +10 mỗi lần: n appends → copy ≈ n²/20 = vẫn O(n²) ← TỆ!
• ×2 mỗi lần: n appends → copy 1+2+4+...+n = O(n) ← TỐT!

→ Doubling strategy là foundation cho amortized O(1).
```

#### Trace Chi Tiết — 16 Appends

```python
# TRACE từng bước append cho dynamic array, initial size = 1

# ┌─────────┬──────────┬──────────┬───────────┬───────────────────┐
# │ append# │ Capacity │ Resize?  │ Copy cost │ Total cost        │
# ├─────────┼──────────┼──────────┼───────────┼───────────────────┤
# │    1    │  1 → 1   │ No       │     0     │ 1 (write)         │
# │    2    │  1 → 2   │ YES ×2   │     1     │ 1 + 1 = 2         │
# │    3    │  2 → 4   │ YES ×2   │     2     │ 1 + 2 = 3         │
# │    4    │  4       │ No       │     0     │ 1                 │
# │    5    │  4 → 8   │ YES ×2   │     4     │ 1 + 4 = 5         │
# │    6    │  8       │ No       │     0     │ 1                 │
# │    7    │  8       │ No       │     0     │ 1                 │
# │    8    │  8       │ No       │     0     │ 1                 │
# │    9    │  8 → 16  │ YES ×2   │     8     │ 1 + 8 = 9         │
# │   10   │ 16       │ No       │     0     │ 1                 │
# │   11   │ 16       │ No       │     0     │ 1                 │
# │   12   │ 16       │ No       │     0     │ 1                 │
# │   13   │ 16       │ No       │     0     │ 1                 │
# │   14   │ 16       │ No       │     0     │ 1                 │
# │   15   │ 16       │ No       │     0     │ 1                 │
# │   16   │ 16       │ No       │     0     │ 1                 │
# └─────────┴──────────┴──────────┴───────────┴───────────────────┘
#
# TỔNG COST = 16 (writes) + 1+2+4+8 (copies) = 16 + 15 = 31
# AVERAGE = 31/16 ≈ 1.94 ≈ O(1) per append ✅
```

#### Chứng Minh Toán Học — Aggregate Method

```
CHO n appends:

═══ COST 1: Normal writes ═══
Mỗi append ghi 1 element → n lần
→ Cost = n

═══ COST 2: Resize copies ═══
Resize xảy ra khi size = 1, 2, 4, 8, ..., n
(giả sử n là lũy thừa 2 cho đơn giản)

Copy costs: 1 + 2 + 4 + 8 + ... + n/2

Đây là GEOMETRIC SERIES:
 1 + 2 + 4 + ... + 2^k = 2^(k+1) - 1

Với 2^k = n/2:
 Sum = 1 + 2 + 4 + ... + n/2 = n - 1

═══ TỔNG ═══
Total cost = n (writes) + (n - 1) (copies) = 2n - 1

Amortized cost = (2n - 1) / n ≈ 2 = O(1) ✅

═══ TRỰC QUAN ═══
Resize cost cho 16 appends:

Cost: █ ██ ████ █ ████████ █ █ █ █ █ █ █ █
      1  2   3  4    5     6 7 8 9 ...   16
      ↑  ↑   ↑       ↑
    resize resize  resize  resize

→ "Spikes" ngày càng xa nhau
→ Nhưng spread over tất cả ops → O(1) average

VISUAL — "Trải đều" cost:
Nếu mỗi append "trả trước" 3 coins:
• 1 coin cho chính nó (write)
• 2 coins "tiết kiệm" cho resize tương lai
→ Khi resize xảy ra → đủ coins chi trả!
→ Đây chính là ACCOUNTING METHOD.
```

#### Nếu Growth Factor Khác 2?

```
╔═══════════════════════════════════════════════════════════╗
║ Growth     │ Amortized │ Wasted Space   │ Used in        ║
║ Factor     │ Append    │ (worst case)   │                ║
╠═══════════════════════════════════════════════════════════╣
║ ×2         │ O(1)      │ 50%            │ Java ArrayList ║
║ ×1.5       │ O(1)      │ 33%            │ C++ vector     ║
║ ×1.125     │ O(1)      │ 12.5%          │ Python list    ║
║ +constant  │ O(n)!     │ ~0%            │ KHÔNG AI dùng  ║
╚═══════════════════════════════════════════════════════════╝

HỎI: "Tại sao Python dùng ×1.125 thay vì ×2?"
TRẢ LỜI: "Trade-off giữa time và space.
  ×2 = ít resize hơn (fast) nhưng waste 50% memory.
  ×1.125 = resize thường hơn nhưng waste chỉ 12.5%.
  Cả hai đều amortized O(1), chỉ khác constant factor."
```

---

### 5.4 HashMap Rehash — Chi Tiết

```
HASHMAP REHASH:

Khi load_factor = n/capacity > THRESHOLD:
  1. Tạo array MỚI gấp đôi capacity
  2. Re-hash TẤT CẢ n entries → O(n)
  3. Insert entries vào array mới

DEFAULTS:
  Java HashMap:    threshold = 0.75, growth = ×2
  Python dict:     threshold = 2/3 ≈ 0.67, growth = ×2 (roughly)
  C++ unordered_map: threshold = 1.0, growth = ×2

═══ TOÁN HỌC ═══

Rehash happens khi n = 0.75 × capacity
→ Capacity doubles: c, 2c, 4c, 8c, ...
→ Rehash tại n = 0.75c, 1.5c, 3c, 6c, ...

Cost of rehash i: rehash 0.75 × 2^(i-1) × c entries

Total rehash cost cho n inserts:
= 0.75c + 1.5c + 3c + ... ≈ 2n (geometric series)

Amortized insert = (n + 2n) / n = 3 = O(1) ✅

NHƯNG WORST CASE 1 INSERT = O(n) ← do rehash
→ Trong real-time systems → CẦN reserve capacity trước!

NARRATE: "HashMap put is O(1) amortized. When the load
 factor exceeds 0.75, rehashing copies all n entries,
 which is O(n). But this happens infrequently — the next
 rehash won't occur until we insert another n entries.
 So the cost is spread out: amortized O(1)."
```

#### HashMap vs ArrayList — So Sánh Amortized

```
╔════════════════════════════════════════════════════════════╗
║                    │ ArrayList         │ HashMap           ║
╠════════════════════════════════════════════════════════════╣
║ Trigger evento     │ Capacity full     │ Load factor > 0.75║
║ Action            │ Double + copy     │ Double + rehash    ║
║ Cost mỗi resize   │ O(n)             │ O(n)               ║
║ Frequency          │ Every n elements │ Every ~0.75n       ║
║ Amortized insert   │ O(1)             │ O(1)               ║
║ Worst single op    │ O(n)             │ O(n)               ║
║ Can pre-allocate?  │ Yes (initial cap)│ Yes (initial cap)  ║
╚════════════════════════════════════════════════════════════╝
```

---

### 5.5 Ví Dụ Khác — Stack Multipop

> Ví dụ KINH ĐIỂN trong textbook, đôi khi bị hỏi trong phỏng vấn.

```python
class AmortizedStack:
    """Stack với 3 operations: push, pop, multipop"""

    def __init__(self):
        self.stack = []

    def push(self, x):          # O(1)
        self.stack.append(x)

    def pop(self):              # O(1)
        if self.stack:
            return self.stack.pop()

    def multipop(self, k):      # O(min(k, len)) ← expensive!
        """Pop k elements cùng lúc"""
        count = min(k, len(self.stack))
        for _ in range(count):
            self.stack.pop()
        return count

# HỎI: n operations (mix push, pop, multipop) → total cost?
#
# WORST CASE 1 operation: multipop(n) = O(n) ← đắt!
# NAIVE analysis: n ops × O(n) each = O(n²) ← QUÁ BI QUAN!
#
# AMORTIZED ANALYSIS (Accounting method):
#
# Mỗi element chỉ có thể pop TỐI ĐA 1 LẦN.
# Mỗi element được push ĐÚNG 1 LẦN.
# → Total pops (bao gồm multipop) ≤ total pushes ≤ n
#
# Total cost = n (pushes) + n (pops trong mọi multipop) = 2n
# → Amortized per operation = 2n/n = O(1) ✅
#
# KEY: "Charge" 2 coins cho mỗi push:
#   1 coin cho push itself
#   1 coin "để dành" cho pop/multipop tương lai
# → Mỗi element đã "pre-paid" chi phí pop khi nó được push.
```

---

### 5.6 Union-Find (Disjoint Set) — Inverse Ackermann

```
UNION-FIND với Path Compression + Union by Rank:

Worst case 1 operation: O(log n)  (без path compression)
Amortized for n operations: O(α(n)) per operation

α(n) = INVERSE ACKERMANN FUNCTION
  • α(n) ≤ 4 cho MỌI n THỰC TẾ (n < 2^65536)
  • Grow cực kỳ chậm — chậm hơn log, log log, log*, ...
  • Trong thực tế: α(n) ≈ constant ≈ O(1)

═══ TẠI SAO GẦN NHƯ O(1)? ═══

Path Compression: Mỗi find() "phẳng hóa" cây
                  → Các find() SAU nhanh hơn find() TRƯỚC

Union by Rank: Cây luôn balanced → max depth log n

Kết hợp: Sau đủ nhiều operations, mọi node
         gần như trỏ TRỰC TIẾP đến root → O(1)

═══ TRONG PHỎNG VẤN ═══
NÓI: "Union-Find with path compression and union by rank
      gives amortized O(α(n)) per operation, which is
      effectively O(1) for all practical input sizes."

ĐỪNG NÓI: "Union-Find is O(1)" ← thiếu "amortized" = sai
ĐỪNG NÓI: "Union-Find is O(log n)" ← quên path compression
```

---

### 5.7 Khi Nào Nói "Amortized" Trong Phỏng Vấn?

```
╔══════════════════════════════════════════════════════════════════╗
║  ✅ NÊN NÓI "amortized" khi:                                     ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║  1. ArrayList / Dynamic Array                                    ║
║     "Append is amortized O(1). Occasionally O(n) for resize,   ║
║      but averaged over n operations, it's constant."             ║
║                                                                  ║
║  2. HashMap / HashSet                                            ║
║     "Put/Get is amortized O(1). Rehashing is O(n) but          ║
║      infrequent due to load factor management."                  ║
║                                                                  ║
║  3. Union-Find (Disjoint Set Union)                              ║
║     "With path compression and union by rank,                    ║
║      it's amortized O(α(n)), effectively constant."              ║
║                                                                  ║
║  4. Splay Trees (nếu được hỏi)                                  ║
║     "Splay trees have amortized O(log n) per operation          ║
║      due to self-adjusting rotations."                            ║
║                                                                  ║
╠══════════════════════════════════════════════════════════════════╣
║  ❌ KHÔNG NÊN nói "amortized" khi:                                ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║  • Fixed array access → "O(1)" (exact, không cần amortized)    ║
║  • Binary search → "O(log n)" (exact worst case)               ║
║  • Mergesort → "O(n log n)" (exact, mọi input)                 ║
║  • Single operation worst case đã hỏi → nói O(n)               ║
║                                                                  ║
╠══════════════════════════════════════════════════════════════════╣
║  ⚠️ TRAPS — Sai lầm phổ biến:                                    ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║  TRAP 1: "HashMap is O(1)"                                       ║
║  → Thiếu context! Cần nói: "O(1) AMORTIZED AVERAGE case.       ║
║    Worst case single lookup can be O(n) due to collisions."     ║
║                                                                  ║
║  TRAP 2: "ArrayList append is always O(1)"                       ║
║  → SAI! "Amortized O(1), but single append can be O(n)         ║
║    when resize is triggered."                                    ║
║                                                                  ║
║  TRAP 3: Dùng "amortized" cho probabilistic operations          ║
║  → "Randomized quicksort is O(n log n) EXPECTED, not amortized."║
║    Amortized = deterministic guarantee, expected = probabilistic ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝
```

#### Interview Scripts — Cách Nói Chuẩn

```
SCRIPT 1 — Khi dùng HashMap trong solution:
"My solution uses a HashMap for O(1) amortized lookup.
 The total time is O(n) with O(n) space for the map."
→ Nếu interviewer hỏi follow-up: "What about worst case?"
→ "Worst case for a single lookup is O(n) due to hash
   collisions, but with a good hash function and load
   factor management, this is extremely rare in practice."

SCRIPT 2 — Khi dùng dynamic array:
"I'll use a dynamic array. Append is amortized O(1) —
 occasionally O(n) when resizing, but the geometric
 growth ensures the average stays constant."

SCRIPT 3 — Khi interviewer hỏi "is it really O(1)?":
"It's amortized O(1), meaning over any sequence of n
 operations, the total cost is O(n). Individual operations
 can be O(n) in worst case, but this is guaranteed to
 happen infrequently — at most log n times in n operations."

SCRIPT 4 — Khi dùng Union-Find:
"I'm using Union-Find with path compression and union by
 rank. Each operation is amortized O(α(n)), which is
 effectively constant — α(n) never exceeds 4 for any
 practical input size."
```

### 5.8 Bảng Tổng Hợp — Amortized vs Worst Case

```
╔═══════════════════════════════════╦═══════════╦══════════════╗
║ Operation                         ║ Worst Case ║ Amortized    ║
╠═══════════════════════════════════╬═══════════╬══════════════╣
║ ArrayList append                  ║ O(n)      ║ O(1)         ║
║ HashMap put/get (avg)             ║ O(n)      ║ O(1)         ║
║ HashMap put/get (worst: all same  ║ O(n)      ║ O(n)         ║
║   hash = linked list)             ║           ║              ║
║ Stack push                        ║ O(1)      ║ O(1)         ║
║ Stack multipop(k)                 ║ O(k)      ║ O(1) per elem║
║ Union-Find (with optimizations)   ║ O(log n)  ║ O(α(n)) ≈ O(1)║
║ Splay Tree operations             ║ O(n)      ║ O(log n)     ║
║ Fibonacci Heap decrease-key       ║ O(1)      ║ O(1)         ║
║ Fibonacci Heap delete-min         ║ O(n)      ║ O(log n)     ║
║ Binary Counter increment          ║ O(log n)  ║ O(1)         ║
╚═══════════════════════════════════╩═══════════╩══════════════╝

RULE OF THUMB cho phỏng vấn:
  → Nếu "đôi khi đắt nhưng hiếm" → nói amortized
  → Nếu "luôn cùng cost" → nói exact (không cần amortized)
  → Nếu "phụ thuộc random" → nói expected (không phải amortized)
```

---

## 6. Space Complexity — Phần Hay Bị Quên (Chi Tiết)

> **Tại sao quan trọng?** ~40% candidates quên phân tích space complexity. Interviewer LUÔN hỏi "What about space?" sau khi bạn phân tích time. Nói được space complexity = strong signal.

### 6.1 Định Nghĩa — 3 Loại Space

```
╔══════════════════════════════════════════════════════════════════╗
║  LOẠI SPACE            │ ĐỊNH NGHĨA               │ VÍ DỤ       ║
╠══════════════════════════════════════════════════════════════════╣
║ 1. Input Space         │ Bộ nhớ cho INPUT         │ Array n phần ║
║                        │ (thường KHÔNG đếm)       │ tử = O(n)    ║
╠══════════════════════════════════════════════════════════════════╣
║ 2. Auxiliary Space     │ Bộ nhớ THÊM ngoài input  │ HashMap phụ  ║
║                        │ (thường ĐÚNG LÀ CÁI      │ = O(n)       ║
║                        │  interviewer muốn)       │              ║
╠══════════════════════════════════════════════════════════════════╣
║ 3. Total Space         │ Input + Auxiliary         │ = O(2n)      ║
║                        │ (hiếm khi hỏi)           │ = O(n)       ║
╚══════════════════════════════════════════════════════════════════╝

TRONG PHỎNG VẤN:
  Interviewer nói "space complexity" → 99% là AUXILIARY SPACE
  → Nếu không chắc → HỎI: "Do you mean auxiliary space,
    or total space including the input?"
  → Hỏi này = show maturity + precision thinking
```

#### Ví Dụ Minh Họa — Cùng Bài Nhưng Khác Space

```python
# BÀI: Sort một array

# === CÁCH 1: Mergesort → O(n) auxiliary ===
def mergesort(arr):
    if len(arr) <= 1: return arr
    mid = len(arr) // 2
    left = mergesort(arr[:mid])     # tạo array MỚI!
    right = mergesort(arr[mid:])    # tạo array MỚI!
    return merge(left, right)        # tạo array MỚI!
# Auxiliary: O(n) — cần array phụ cho merge
# Stack: O(log n) — recursion depth
# Total auxiliary: O(n)

# === CÁCH 2: Quicksort in-place → O(log n) auxiliary ===
def quicksort(arr, lo, hi):
    if lo >= hi: return
    pivot = partition(arr, lo, hi)   # swap IN-PLACE, không tạo array mới
    quicksort(arr, lo, pivot - 1)
    quicksort(arr, pivot + 1, hi)
# Auxiliary: O(1) — chỉ dùng vài biến (pivot, i, j)
# Stack: O(log n) average, O(n) worst
# Total auxiliary: O(log n) average

# === CÁCH 3: Heapsort → O(1) auxiliary ===
# Build heap in-place + extract max
# Auxiliary: O(1) — hoàn toàn in-place
# Stack: O(1) — iterative (không recursion)

# NARRATE: "Mergesort uses O(n) extra space for the merge step.
#           Quicksort is in-place with O(log n) stack space.
#           If space is a constraint, quicksort or heapsort
#           would be better choices than mergesort."
```

---

### 6.2 Recursion Stack = Hidden Space (Chi Tiết)

> **Call stack** là nguồn space THƯỜNG BỊ QUÊN nhất. Mỗi recursive call push 1 frame lên stack → chiếm memory.

#### Mỗi Stack Frame Chứa Gì?

```
MỖI STACK FRAME GỒM:
  ├── Return address (quay về đâu sau khi function kết thúc)
  ├── Local variables (biến cục bộ trong function)
  ├── Parameters (tham số truyền vào)
  └── Saved registers (state của CPU)

→ Mỗi frame ≈ O(1) space (constant per frame)
→ TỔNG space = O(depth) × O(1) per frame = O(depth)

KEY: Space = MAX DEPTH của call stack tại BẤT KỲ thời điểm nào
     (KHÔNG phải tổng số calls — vì frames được pop khi return)
```

#### 4 Patterns Recursion Stack

```python
# ═══ PATTERN 1: Linear recursion → O(n) stack ═══
def factorial(n):
    if n <= 1: return 1
    return n * factorial(n - 1)

# Call stack khi n = 5:
# ┌──────────────────┐
# │ factorial(5)      │ frame 5
# │ factorial(4)      │ frame 4
# │ factorial(3)      │ frame 3
# │ factorial(2)      │ frame 2
# │ factorial(1) = 1  │ frame 1 ← base, bắt đầu return
# └──────────────────┘
# Max depth = n → O(n) space


# ═══ PATTERN 2: Binary tree recursion → O(h) stack ═══
def inorder(node):
    if not node: return
    inorder(node.left)       # đi trái trước
    print(node.val)
    inorder(node.right)      # rồi mới đi phải

# QUAN TRỌNG: Khi đi left, right CHƯA ĐƯỢC GỌI.
# → Chỉ CÓ 1 đường path trên stack tại mỗi thời điểm.
#
# Balanced tree (h = log n):
# ┌──────────┐
# │ inorder(root)    │
# │ inorder(left)    │
# │ inorder(left.left)│
# │ ...              │ ← max log n frames
# └──────────┘
# → O(log n) space
#
# Skewed tree (h = n):
# ┌──────────┐
# │ inorder(1) │
# │ inorder(2) │
# │ inorder(3) │
# │ ...        │ ← max n frames
# │ inorder(n) │
# └──────────┘
# → O(n) space ← WORST CASE!
#
# NARRATE: "Space is O(h) where h is the tree height.
#  Best case O(log n) for balanced, worst O(n) for skewed."


# ═══ PATTERN 3: BFS → O(width) = O(n) queue ═══
from collections import deque
def bfs(root):
    if not root: return
    queue = deque([root])       # khởi tạo queue
    while queue:
        node = queue.popleft()
        if node.left: queue.append(node.left)
        if node.right: queue.append(node.right)

# Queue size = SỐ NODES TẠI 1 LEVEL
# Max width của binary tree = n/2 (level cuối cùng)
# → O(n) space cho queue
#
# DFS vs BFS tradeoff:
# DFS: O(h) space ← tốt hơn khi tree wide
# BFS: O(w) space ← tốt hơn khi tree deep/narrow


# ═══ PATTERN 4: Tail recursion → O(1) có thể ═══
# (nếu language hỗ trợ Tail Call Optimization)
def factorial_tail(n, acc=1):
    if n <= 1: return acc
    return factorial_tail(n - 1, acc * n)  # TAIL CALL

# VỚI TCO (Scheme, Kotlin, Scala):
#   → Compiler reuse frame → O(1) space
# KHÔNG CÓ TCO (Python, Java, JavaScript*):
#   → Vẫn O(n) space — mỗi call vẫn push frame
#
# *JavaScript: TCO spec'd in ES6, nhưng chỉ Safari implement
```

---

### 6.3 In-Place Algorithms — Deep Dive

> **"In-place"** = algorithm chỉ dùng O(1) auxiliary space (không kể input và recursion stack).

```
╔══════════════════════════════════════════════════════════════════╗
║  ALGORITHM          │ In-Place? │ Auxiliary  │ Tổng Space       ║
╠══════════════════════════════════════════════════════════════════╣
║ Bubble Sort         │ ✅ YES    │ O(1)       │ O(1)             ║
║ Selection Sort      │ ✅ YES    │ O(1)       │ O(1)             ║
║ Insertion Sort      │ ✅ YES    │ O(1)       │ O(1)             ║
║ Heapsort            │ ✅ YES    │ O(1)       │ O(1)             ║
║ Quicksort           │ ⚠️ GẦN   │ O(1) swap  │ O(log n) stack   ║
║ Mergesort           │ ❌ NO     │ O(n)       │ O(n)             ║
║ Counting Sort       │ ❌ NO     │ O(k)       │ O(k)             ║
║ Radix Sort          │ ❌ NO     │ O(n+k)     │ O(n+k)           ║
║ Two Pointers        │ ✅ YES    │ O(1)       │ O(1)             ║
║ Reverse array       │ ✅ YES    │ O(1)       │ O(1)             ║
║ Dutch National Flag │ ✅ YES    │ O(1)       │ O(1)             ║
╚══════════════════════════════════════════════════════════════════╝

⚠️ Quicksort: swap in-place nhưng recursion stack dùng O(log n).
   Technically "in-place" vì auxiliary = O(1),
   nhưng stack space vẫn tồn tại.
```

#### Ví Dụ: In-Place Partition (Quicksort)

```python
def partition(arr, lo, hi):
    pivot = arr[hi]              # chọn pivot = last element
    i = lo - 1                   # i = boundary of "smaller" region

    for j in range(lo, hi):      # scan từ lo → hi-1
        if arr[j] <= pivot:
            i += 1
            arr[i], arr[j] = arr[j], arr[i]  # swap IN-PLACE

    arr[i+1], arr[hi] = arr[hi], arr[i+1]    # pivot vào đúng chỗ
    return i + 1

# TRACE cho arr = [3, 6, 8, 2, 5], pivot = 5:
# Step 0: i=-1  [3, 6, 8, 2, 5]  j=0, arr[0]=3 ≤ 5 → swap → i=0
# Step 1: i=0   [3, 6, 8, 2, 5]  j=1, arr[1]=6 > 5 → skip
# Step 2: i=0   [3, 6, 8, 2, 5]  j=2, arr[2]=8 > 5 → skip
# Step 3: i=0   [3, 6, 8, 2, 5]  j=3, arr[3]=2 ≤ 5 → swap(1,3) → i=1
#         →     [3, 2, 8, 6, 5]
# Final:  swap pivot: swap(2,4)
#         →     [3, 2, 5, 6, 8]  ← pivot 5 ở đúng vị trí!
#
# AUXILIARY SPACE = O(1): chỉ dùng i, j, pivot (3 biến)
# KHÔNG tạo array mới!
```

#### Khi "In-Place" Gây Hiểu Lầm

```
⚠️ TRAP: "str.replace() is in-place" → SAI!
  Strings trong Python/Java/JS là IMMUTABLE
  → str.replace() tạo STRING MỚI → O(n) space

⚠️ TRAP: "arr.sort() is in-place" → ĐÚNG cho Python/JS
  Nhưng nó dùng Timsort (variant of mergesort)
  → Cần O(n) auxiliary space bên trong!
  → "In-place API" ≠ "O(1) space algorithm"

⚠️ TRAP: "sorted(arr) is in-place" → SAI!
  sorted() TẠO LIST MỚI → O(n) space
  arr.sort() modify in-place (nhưng vẫn O(n) nội bộ)

NARRATE: "I'll solve this in-place — modifying the input
 array directly without creating a new one. This gives
 O(1) auxiliary space, excluding the recursion stack."
```

---

### 6.4 Space Optimization Techniques — Phỏng Vấn

> Interviewer thường hỏi follow-up: "Can you optimize the space?"

#### Technique 1: Rolling Array — DP 2D → 1D

```python
# BÀI: Unique Paths — đếm đường đi từ (0,0) → (m-1, n-1)
# Grid m × n, chỉ đi RIGHT hoặc DOWN

# === TRƯỚC: O(m × n) space ===
def unique_paths_2d(m, n):
    dp = [[1] * n for _ in range(m)]  # ← O(m×n) space!
    for i in range(1, m):
        for j in range(1, n):
            dp[i][j] = dp[i-1][j] + dp[i][j-1]
    return dp[m-1][n-1]

# === SAU: O(n) space — rolling array ===
def unique_paths_1d(m, n):
    dp = [1] * n                       # ← O(n) space!
    for i in range(1, m):
        for j in range(1, n):
            dp[j] = dp[j] + dp[j-1]   # dp[j] cũ = dp[i-1][j]
    return dp[n-1]                      # dp[j-1] = dp[i][j-1]

# TẠI SAO HOẠT ĐỘNG?
# dp[i][j] chỉ phụ thuộc vào dp[i-1][j] và dp[i][j-1]
# → Chỉ cần GIỮ 1 ROW, overwrite dần
# → Space: O(m×n) → O(min(m,n))
#
# NARRATE: "I can optimize space from O(m×n) to O(n) by
#  using a rolling array. Since each cell only depends on
#  the current and previous row, I only need to keep one row."
```

#### Technique 2: Bit Manipulation — O(n) → O(1)

```python
# BÀI: Tìm số xuất hiện 1 lần (others appear 2 lần)

# === TRƯỚC: O(n) space — HashSet ===
def single_number_hash(nums):
    seen = set()                        # O(n) space
    for num in nums:
        if num in seen: seen.remove(num)
        else: seen.add(num)
    return seen.pop()

# === SAU: O(1) space — XOR ===
def single_number_xor(nums):
    result = 0                          # O(1) space!
    for num in nums:
        result ^= num                   # a XOR a = 0
    return result

# XOR properties: a ^ a = 0, a ^ 0 = a, commutative + associative
# [4, 1, 2, 1, 2] → 4^1^2^1^2 = 4^(1^1)^(2^2) = 4^0^0 = 4
```

#### Technique 3: Input Modification — "Borrow" Space

```python
# BÀI: Find duplicates trong array n numbers, range [1, n]

# === O(1) space — modify input array as "visited" marker ===
def find_duplicates(nums):
    result = []
    for num in nums:
        index = abs(num) - 1           # map value → index
        if nums[index] < 0:            # đã visited → duplicate!
            result.append(abs(num))
        else:
            nums[index] = -nums[index] # mark as visited (negate)
    return result

# AUXILIARY SPACE = O(1)! (không kể output)
# Trick: dùng SIGN BIT của input array elements
#
# ⚠️ CAVEAT: modify input → hỏi interviewer trước!
# "Can I modify the input array? If so, I can solve this
#  in O(1) extra space by using the sign bit as a marker."
```

#### Technique 4: Two Pointers — Avoid Extra Array

```python
# BÀI: Remove duplicates from SORTED array IN-PLACE

def remove_duplicates(nums):
    if not nums: return 0
    write = 1                           # pointer ghi vị trí mới
    for read in range(1, len(nums)):    # pointer đọc
        if nums[read] != nums[read - 1]:
            nums[write] = nums[read]
            write += 1
    return write

# [1, 1, 2, 2, 3] → write pointer:
# read=1: 1==1 → skip
# read=2: 2≠1 → nums[1]=2, write=2
# read=3: 2==2 → skip
# read=4: 3≠2 → nums[2]=3, write=3
# Result: [1, 2, 3, _, _] → return 3
# SPACE = O(1) — chỉ 2 pointers
```

---

### 6.5 Hidden Space — Những Cái Bẫy

```python
# ═══ TRAP 1: String concatenation → O(n²) hidden space! ═══
result = ""
for char in string:          # n iterations
    result += char            # TẠO STRING MỚI mỗi lần!
# Python strings = IMMUTABLE
# "abc" + "d" → tạo "abcd" (copy 3 + write 1 = 4 chars)
# Total copies: 1 + 2 + 3 + ... + n = O(n²) time VÀ space!
#
# FIX: Dùng list → join
parts = []
for char in string:
    parts.append(char)        # O(1) amortized
result = "".join(parts)       # O(n) — tạo 1 lần
# Total: O(n) time, O(n) space


# ═══ TRAP 2: Slice trong Python → O(k) space! ═══
arr = [1, 2, 3, 4, 5]
sub = arr[1:4]               # TẠO LIST MỚI [2, 3, 4]!
# arr[1:4] = O(3) = O(k) space, k = length of slice
#
# TRONG RECURSION, điều này RẤT NGUY HIỂM:
def mergesort(arr):
    left = mergesort(arr[:mid])   # ← O(n/2) space MỖI LẦN!
    right = mergesort(arr[mid:])  # ← O(n/2) space MỖI LẦN!
# Total hidden space: O(n log n)! (n/2 per level × log n levels)
# FIX: Truyền index thay vì slice
def mergesort_fix(arr, lo, hi):   # ← O(1) per call, NO copy


# ═══ TRAP 3: sorted() vs .sort() ═══
sorted_arr = sorted(arr)     # TẠO LIST MỚI → O(n) space
arr.sort()                    # In-place → O(1) space*
# *Internally Timsort dùng O(n) auxiliary, nhưng không tạo copy


# ═══ TRAP 4: Dictionary/Set from comprehension ═══
seen = {x for x in arr}      # O(n) space — set mới
counter = {x: arr.count(x) for x in arr}  # O(n) space + O(n²) time!
# .count() = O(n) per call × n keys = O(n²) ← HIDDEN TRAP!
# FIX: collections.Counter(arr) → O(n) time


# ═══ TRAP 5: Graph — adjacency list vs matrix ═══
# Adjacency List: O(V + E) space
# Adjacency Matrix: O(V²) space
# Dense graph (E ≈ V²): cả hai gần nhau
# Sparse graph (E << V²): list TỐT HƠN NHIỀU
#
# NARRATE: "I'll use an adjacency list since the graph
#  is sparse — O(V+E) space vs O(V²) for a matrix."
```

---

### 6.6 Bảng Space Complexity Toàn Diện

```
╔═══════════════════════════════════════════════════════════════════╗
║ Category              │ Structure / Op        │ Space             ║
╠═══════════════════════════════════════════════════════════════════╣
║                        │                       │                   ║
║ ARRAYS & STRINGS       │ Extra array/hashmap   │ O(n)              ║
║                        │ Two pointers          │ O(1)              ║
║                        │ Sliding window        │ O(1) or O(k)      ║
║                        │ String concat (loop)  │ O(n²) ← TRAP!    ║
║                        │ String join           │ O(n)              ║
║                        │ Array slice a[i:j]    │ O(j-i)            ║
║                        │                       │                   ║
║ SORTING                │ Mergesort             │ O(n) auxiliary    ║
║                        │ Quicksort             │ O(log n) stack    ║
║                        │ Heapsort              │ O(1)              ║
║                        │ Counting sort         │ O(k) (range)      ║
║                        │ Timsort (Python/Java) │ O(n) internal     ║
║                        │                       │                   ║
║ TREES                  │ DFS recursion          │ O(h) stack       ║
║                        │  ├── Balanced         │ O(log n)          ║
║                        │  └── Skewed           │ O(n)              ║
║                        │ BFS queue             │ O(width) ≤ O(n)   ║
║                        │ Morris traversal      │ O(1) ← no stack!  ║
║                        │                       │                   ║
║ GRAPHS                 │ Visited set           │ O(V)              ║
║                        │ BFS queue             │ O(V)              ║
║                        │ DFS stack (explicit)  │ O(V)              ║
║                        │ Adjacency list        │ O(V + E)          ║
║                        │ Adjacency matrix      │ O(V²)             ║
║                        │                       │                   ║
║ DP                     │ 2D table              │ O(n × m)          ║
║                        │ 1D rolling            │ O(min(n, m))      ║
║                        │ Constant vars         │ O(1)              ║
║                        │ (Fibonacci optimized) │                   ║
║                        │                       │                   ║
║ SPECIAL DATA STRUCTURES│ Trie                  │ O(total chars)    ║
║                        │ Segment Tree          │ O(4n) ≈ O(n)      ║
║                        │ Union-Find            │ O(n)              ║
║                        │ Min/Max Heap          │ O(n)              ║
║                        │ Monotonic Stack       │ O(n)              ║
║                        │                       │                   ║
╚═══════════════════════════════════════════════════════════════════╝
```

---

### 6.7 Space-Time Trade-off — Framework Trong Phỏng Vấn

```
╔══════════════════════════════════════════════════════════════════╗
║  TRADE-OFF PATTERN           │ ĐỔI GÌ?                          ║
╠══════════════════════════════════════════════════════════════════╣
║ HashMap                      │ +O(n) space → -O(n) time         ║
║ (Two Sum: O(n²) → O(n))     │ Time: O(n²) → O(n)               ║
╠══════════════════════════════════════════════════════════════════╣
║ Memoization                   │ +O(n) space → -O(2ⁿ) time      ║
║ (Fib: O(2ⁿ) → O(n))        │ Time: exponential → linear       ║
╠══════════════════════════════════════════════════════════════════╣
║ Sorting                      │ +O(n log n) time → -O(n) space   ║
║ (Use sorting instead of hash)│ Time: O(n) → O(n log n)          ║
║                              │ Space: O(n) → O(1)               ║
╠══════════════════════════════════════════════════════════════════╣
║ Bit manipulation              │ +complexity → -O(n) space        ║
║ (XOR for single number)      │ Space: O(n) → O(1)               ║
╠══════════════════════════════════════════════════════════════════╣
║ Two Pointers                  │ +clever logic → -O(n) space      ║
║ (Remove duplicates in-place) │ Space: O(n) → O(1)               ║
╚══════════════════════════════════════════════════════════════════╝

NARRATE: "There's a space-time trade-off here. I can either:
 1. Use a HashMap for O(n) time but O(n) space, or
 2. Sort first for O(n log n) time but O(1) extra space.
 Which would you prefer?"

→ Interviewer LOVES khi bạn present MULTIPLE approaches
  với trade-off analysis. Đây là strong senior signal.
```

---

### 6.8 Interview Scripts — Space Complexity

```
SCRIPT 1 — Khi report complexity:
"Time is O(n log n) for the sort, and O(n) for the scan.
 Overall O(n log n) time. Space is O(n) for the auxiliary
 array used in mergesort, plus O(1) for my variables."

SCRIPT 2 — Khi bị hỏi "can you reduce space?":
"Currently I'm using O(n) space for the HashMap. I could
 sort the array first and use two pointers — that would
 make space O(1) but increase time from O(n) to O(n log n).
 Want me to explore that approach?"

SCRIPT 3 — Khi dùng recursion:
"The recursion depth is O(log n) for a balanced tree,
 so the call stack uses O(log n) space. In the worst case
 of a skewed tree, it could be O(n). If stack space is
 a concern, I can convert to an iterative approach with
 an explicit stack."

SCRIPT 4 — Khi modify input:
"I can do this in O(1) extra space if I'm allowed to
 modify the input array. I'll use the sign bit to mark
 visited elements. Is that acceptable?"

LUÔN NHỚ: Nói CẢ TIME VÀ SPACE cho mọi solution.
  "Time: O(n), Space: O(n)" ← complete answer
  "Time: O(n)" ← INCOMPLETE — interviewer sẽ hỏi space
```

## 7. Quy Tắc Tính Big O — 7 Rules (Chi Tiết)

> **7 rules này** là "từ điển Big O" — nắm vững chúng là giải quyết được 90% câu hỏi complexity trong phỏng vấn. Mỗi rule dưới đây được giải thích SÂU với toán, ví dụ, và TRAPS.

### Rule 1: Drop Constants — Bỏ Hằng Số

```
O(2n) → O(n)
O(100n) → O(n)
O(n/2) → O(n)
O(3n² + 5n + 7) → O(n²)

═══ TẠI SAO? ═══

Big O đo RATE OF GROWTH (tốc độ tăng trưởng),
không phải giá trị cụ thể.

Chứng minh bằng LIMIT:
  lim(n→∞) 2n/n = 2  ← hằng số, không phải ∞
  → 2n và n grow CÙNG TỐC ĐỘ → cùng Big O class

So sánh:
  n = 1,000        → 2n = 2,000     (chênh 2×)
  n = 1,000,000    → 2n = 2,000,000 (chênh 2×)
  n = 1,000,000,000 → 2n = 2,000,000,000 (vẫn chênh 2×)
  → Hệ số KHÔNG THAY ĐỔI theo n → không ảnh hưởng "growth"
```

#### Constants MATTER Trong Thực Tế!

```
NHƯNG: Trong production code, constants CÓ ẢNH HƯỞNG!

VÍ DỤ:
  Algorithm A: 2n operations, constant = 2
  Algorithm B: 1000n operations, constant = 1000

  Cả hai = O(n), nhưng B chậm hơn 500×!

  Với n = 10,000:
    A: 20,000 ops  → 0.02ms
    B: 10,000,000 ops → 10ms

TRONG PHỎNG VẤN — Cách nói CHUẨN:
  ❌ "It's O(n)" (đúng nhưng thiếu depth)
  ✅ "It's O(n). More precisely, it does about 2n comparisons
     and n swaps, so the constant factor is around 3."
  → Show bạn hiểu CẢ theory VÀ practice.

KHI NÀO CONSTANTS QUYẾT ĐỊNH?
  • Khi cả hai algorithms cùng Big O:
    Quicksort vs Mergesort: cả hai O(n log n)
    Quicksort nhanh hơn 2-3× nhờ cache locality + ít copy
  • Khi n nhỏ:
    O(n²) có thể nhanh hơn O(n log n) khi n < 50
    → Vì sao Timsort dùng Insertion Sort cho n < 64
```

---

### Rule 2: Drop Lower-Order Terms — Bỏ Hạng Thấp

```
O(n² + n) → O(n²)
O(n³ + n² + n) → O(n³)
O(2ⁿ + n³) → O(2ⁿ)
O(n log n + n) → O(n log n)
O(n + log n) → O(n)

═══ TOÁN HỌC — TẠI SAO? ═══

Khi n → ∞, term cao nhất DOMINATES:

n = 1,000:
  n²  = 1,000,000
  n   = 1,000       ← chiếm 0.1% → BỎ QUA

n = 1,000,000:
  n²  = 10¹²
  n   = 10⁶         ← chiếm 0.0001% → CÀng BỎ QUA hơn

CHỨNG MINH:
  lim(n→∞) (n² + n) / n² = lim(n→∞) (1 + 1/n) = 1
  → n² + n và n² grow CÙNG TỐC ĐỘ → cùng Big O class

═══ THỨ TỰ DOMINANCE ═══

O(1) < O(log n) < O(√n) < O(n) < O(n log n) < O(n²) < O(n³) < O(2ⁿ) < O(n!)

Nếu sum = f(n) + g(n) và f(n) > g(n) khi n → ∞:
  → O(f(n) + g(n)) = O(f(n))
```

#### Tricky Cases — Khi Nào KHÔNG Drop?

```python
# ⚠️ TRAP: Khác biến → KHÔNG DROP!

def process(arr1, arr2):
    for x in arr1:           # O(n)
        ...
    for y in arr2:           # O(m)
        ...

# ĐÚNG: O(n + m)  ← KHÔNG drop m vì n và m KHÁC NHAU!
# SAI: O(n) hoặc O(m)

# n và m có thể khác nhau rất nhiều:
#   n = 1,000,000 và m = 10 → O(n) reasonable
#   n = 10 và m = 1,000,000 → O(m) reasonable
# → Phải giữ cả hai: O(n + m)


# ⚠️ TRAP: Same variable nhưng INDEPENDENT computations

def complex(arr):
    sorted_arr = sorted(arr)     # O(n log n)
    pairs = find_all_pairs(arr)  # O(n²)

# ĐÚNG: O(n log n + n²) = O(n²) ← DROP n log n (same var, lower order)
# → Khi cùng variable, rule vẫn áp dụng.
```

---

### Rule 3: Different Inputs → Different Variables

```python
# ═══ NGUYÊN TẮC ═══
# KHI 2+ inputs KHÁC NHAU → dùng BIẾN KHÁC NHAU

def intersect(arr1, arr2):
    for x in arr1:          # O(n)   ← n = len(arr1)
        for y in arr2:      # O(m)   ← m = len(arr2)
            if x == y: ...
# → O(n × m), KHÔNG phải O(n²)!

# SAI: "O(n²) because nested loops"
# ĐÚNG: "O(n × m) where n is the size of arr1 and m is arr2"
```

#### Ví Dụ Chi Tiết — Multi-Variable

```python
# ═══ VÍ DỤ 1: Graph ═══
# BFS/DFS: O(V + E)  ← V vertices, E edges
# V và E là ĐỘC LẬP: sparse graph E = O(V), dense graph E = O(V²)

# ═══ VÍ DỤ 2: Matrix ═══
for i in range(rows):      # O(r)
    for j in range(cols):  # O(c)
        process(M[i][j])
# → O(r × c)
# KHÔNG nói O(n²) trừ khi SQUARE matrix! (rows = cols = n)

# ═══ VÍ DỤ 3: String matching ═══
# Brute force: O(n × m) ← n = text length, m = pattern length
# KMP: O(n + m)
# Rabin-Karp: O(n + m) average

# ═══ VÍ DỤ 4: Merge two sorted arrays ═══
def merge(a, b):
    # a has length n, b has length m
    result = []
    i = j = 0
    while i < len(a) and j < len(b):  # at most n + m steps
        if a[i] <= b[j]:
            result.append(a[i]); i += 1
        else:
            result.append(b[j]); j += 1
    result.extend(a[i:])
    result.extend(b[j:])
    return result
# → O(n + m), KHÔNG phải O(n) hay O(m)
# NARRATE: "Merging takes O(n + m) where n and m are the
#           lengths of the two sorted arrays."

# ═══ VÍ DỤ 5: HashMap contains check trên K queries ═══
# Build: O(n) cho n elements
# Query: O(1) × K queries = O(K)
# Total: O(n + K) ← hai biến!
```

---

### Rule 4: Sequential = Add, Nested = Multiply

```
═══ QUY TẮC ═══

SEQUENTIAL (nối tiếp): CỘNG
  do A; then do B; → O(A + B)

NESTED (lồng nhau): NHÂN
  for each A: do B; → O(A × B)
```

#### Sequential — Cộng

```python
def process(arr):
    # STEP 1
    arr.sort()                    # O(n log n)

    # STEP 2
    for x in arr:                 # O(n)
        print(x)

    # STEP 3
    result = binary_search(arr, target)  # O(log n)

# Total: O(n log n) + O(n) + O(log n)
#      = O(n log n)  ← keep highest term (Rule 2)

# VISUAL:
# ├── sort ────────────── O(n log n) ──┐
# ├── scan ───── O(n) ─────────────────┤ → ADD
# └── search ─ O(log n) ──────────────┘
# Total = n log n + n + log n = O(n log n)
```

#### Nested — Nhân

```python
def process(matrix):
    for row in matrix:              # O(n) — n rows
        for col in row:             # O(m) — m columns
            process_cell(col)       # O(1)

# Total: O(n × m × 1) = O(n × m)

# VISUAL:
# ┌── outer loop (n) ──────────────────┐
# │  ┌── inner loop (m) ──────────┐    │
# │  │  process_cell: O(1)        │    │ → MULTIPLY
# │  └─────────────────────────────┘    │
# └────────────────────────────────────┘
# Total = n × m × 1 = O(n × m)
```

#### Tricky Cases — Mixed Sequential + Nested

```python
# ═══ CASE 1: Sequential INSIDE nested ═══
for i in range(n):          # O(n)
    sort(items[i])          # O(k log k) — k items each
    search(items[i], x)     # O(log k)

# Mỗi iteration: O(k log k + log k) = O(k log k)
# Total: O(n × k log k)

# ═══ CASE 2: Nested nhưng KHÔNG PHẢI multiply ═══
for i in range(n):          # O(n)
    for j in range(i):      # j chạy 0, 1, 2, ..., n-1
        ...                 # O(1)

# KHÔNG PHẢI O(n²)... wait, nó LÀ O(n²)!
# 0 + 1 + 2 + ... + (n-1) = n(n-1)/2 = O(n²)
# → Nhưng constant factor nhỏ hơn "true" n² (chỉ n²/2)

# ═══ CASE 3: Early termination ═══
for i in range(n):
    for j in range(n):
        if found: return    # CÓ THỂ return sớm!

# Worst case: O(n²) ← nếu tìm thấy ở cuối
# Best case: O(1) ← nếu tìm thấy ngay đầu
# → Nói: "O(n²) worst case, but early termination giúp
#         average case tốt hơn nhiều."

# ═══ CASE 4: Function call TRONG loop ═══
for x in arr:               # O(n)
    result += process(x)    # process = O(?) ← PHẢI BIẾT!

# NẾU process(x) = O(1) → Total = O(n × 1) = O(n)
# NẾU process(x) = O(n) → Total = O(n × n) = O(n²)
# NẾU process(x) = O(log n) → Total = O(n log n)
# → LUÔN phân tích function bên trong trước!
```

---

### Rule 5: Log Base Không Quan Trọng

```
O(log₂ n) = O(log₃ n) = O(log₁₀ n) = O(log n)

═══ CHỨNG MINH — Change of Base Formula ═══

log_b(n) = log_a(n) / log_a(b)

Ví dụ:
  log₂(n) = log₁₀(n) / log₁₀(2)
           = log₁₀(n) × (1/0.301)
           = log₁₀(n) × 3.32

→ log₂(n) = 3.32 × log₁₀(n)
→ Chỉ khác CONSTANT 3.32 → Rule 1: drop constants!
→ O(log₂ n) = O(log₁₀ n)

═══ VÌ SAO DÙNG LOG₂ TRONG CS? ═══

Trong CS, "log" thường ngầm hiểu là log₂ vì:
  • Binary search: chia đôi → log₂
  • Binary tree height: chia đôi → log₂
  • Bits needed: biểu diễn n cần log₂(n) bits

Nhưng khi viết Big O, chỉ cần viết "log n" (bỏ base).
```

#### Exceptions — Khi Base MATTERS

```
⚠️ NHƯNG: Base quan trọng khi log là EXPONENT!

  O(n^(log₂ 3)) ≠ O(n^(log₃ 3))

  log₂(3) ≈ 1.585
  log₃(3) = 1

  → n^1.585 ≠ n^1  ← KHÁC NHAU!

⚠️ Cũng quan trọng trong Master Theorem:
  T(n) = aT(n/b) + O(nᶜ)  →  compare c với log_b(a)
  → Base b CỦA log ở đây MATTERS!

RULE: Log base chỉ "không quan trọng" khi log đứng MỘT MÌNH
      (không phải khi log là exponent).
```

---

### Rule 6: Sum 1 + 2 + ... + n = O(n²)

```
═══ GAUSS FORMULA ═══

1 + 2 + 3 + ... + n = n(n + 1) / 2

CHỨNG MINH (matching pairs):
  S   = 1   + 2     + 3     + ... + n
  S   = n   + (n-1) + (n-2) + ... + 1
  2S  = (n+1) + (n+1) + (n+1) + ... + (n+1)
      = n × (n+1)
  S   = n(n+1)/2

Big O: n(n+1)/2 = n²/2 + n/2 → O(n²) (drop constants & lower terms)

═══ KHI NÀO XUẤT HIỆN? ═══

PATTERN 1: Inner loop phụ thuộc outer index
for i in range(n):
    for j in range(i):      # j chạy 0, 1, 2, ..., n-1
        process(i, j)
→ Total iterations: 0 + 1 + 2 + ... + (n-1) = n(n-1)/2 = O(n²)

PATTERN 2: Selection Sort
for i in range(n):
    min_idx = i
    for j in range(i+1, n):  # n-1, n-2, ..., 1 iterations
        if arr[j] < arr[min_idx]:
            min_idx = j
    swap(arr[i], arr[min_idx])
→ (n-1) + (n-2) + ... + 1 = n(n-1)/2 = O(n²)

PATTERN 3: All pairs (i < j)
for i in range(n):
    for j in range(i+1, n):
        compare(arr[i], arr[j])
→ Số pairs = C(n,2) = n(n-1)/2 = O(n²)
```

#### Các Công Thức Tổng Liên Quan

```
╔══════════════════════════════════════════════════════════════════╗
║  TỔNG                         │ CÔNG THỨC        │ Big O         ║
╠══════════════════════════════════════════════════════════════════╣
║ 1 + 2 + ... + n              │ n(n+1)/2         │ O(n²)         ║
║ 1² + 2² + ... + n²           │ n(n+1)(2n+1)/6   │ O(n³)         ║
║ 1 + 2 + 4 + ... + 2^k        │ 2^(k+1) - 1      │ O(2^k)        ║
║ 1 + 1/2 + 1/3 + ... + 1/n    │ ≈ ln(n) + γ      │ O(log n)      ║
║ n + n/2 + n/4 + ... + 1      │ 2n - 1            │ O(n)          ║
╚══════════════════════════════════════════════════════════════════╝

HỌC THUỘC: Arithmetic series → O(n²)
           Geometric series (×2) → O(2^k) hoặc O(n)
           Harmonic series → O(log n)
```

---

### Rule 7: Log n Xuất Hiện Khi Input Bị Chia

```
═══ NGUYÊN TẮC CỐT LÕI ═══

Bất kỳ khi nào input bị CHIA (÷2, ÷3, ÷k) mỗi bước:
→ Số bước = log_k(n)
→ O(log n)

TẠI SAO? Giải phương trình:
  n / 2^k = 1  (sau k bước chia đôi, còn 1)
  2^k = n
  k = log₂(n)
→ Cần log₂(n) bước để "hết" input.
```

#### Bảng Triggers — Khi Nào Thấy log n?

```
╔══════════════════════════════════════════════════════════════════╗
║  TRIGGER                        │ ALGORITHM          │ WHY log n ║
╠══════════════════════════════════════════════════════════════════╣
║ "Sorted array + search"        │ Binary Search      │ ÷2 mỗi bước║
║ "Balanced BST"                  │ BST operations    │ Height=log n║
║ "Divide and conquer"            │ Mergesort levels  │ ÷2 mỗi level║
║ "i *= 2" hoặc "i /= 2"        │ Loop patterns     │ ÷2 / ×2     ║
║ "Heap insert/extract"           │ Heap operations   │ Height=log n║
║ "Exponentiation by squaring"    │ Fast power         │ ÷2 exponent║
║ "GCD (Euclid)"                  │ Euclidean algo    │ ÷2~ mỗi step║
║ "Priority Queue"                │ Heap-based PQ     │ Sift up/down║
║ "How many digits?"              │ Number of digits  │ log₁₀(n)   ║
║ "How many bits?"                │ Bit representation│ log₂(n)    ║
╚══════════════════════════════════════════════════════════════════╝

CÂU TRIGGER PHỎNG VẤN:
  Khi nghe: "sorted", "can I discard half?", "balanced tree"
  → NGAY LẬP TỨC nghĩ: "log n involved"
```

#### n log n — Khi Nào?

```
O(n log n) xuất hiện khi:
  "Xử lý n items, MỖI item tốn log n work"
  HOẶC
  "Chia input log n levels, MỖI level xử lý n items"

VÍ DỤ:
  • Sorting tối ưu: Mergesort, Quicksort, Heapsort
  • Xây Balanced BST từ array
  • n × binary search lookups
  • Closest pair of points (simple)

CHÚ Ý:
  O(n log n) = LOWER BOUND cho comparison-based sorting
  → Không có sort nào nhanh hơn O(n log n) bằng comparison!
  → Counting sort O(n+k), Radix sort O(d(n+k)) = non-comparison
```

---

### Cheat Sheet — 7 Rules Tóm Tắt

```
╔══════════════════════════════════════════════════════════════════╗
║  #  │ RULE                        │ VÍ DỤ                       ║
╠══════════════════════════════════════════════════════════════════╣
║  1  │ Drop constants              │ O(2n) → O(n)                ║
║  2  │ Drop lower-order terms      │ O(n²+n) → O(n²)            ║
║  3  │ Different inputs→diff vars  │ O(n×m) ≠ O(n²)             ║
║  4  │ Sequential=ADD, Nested=MULT │ A;B→O(A+B), A{B}→O(A×B)   ║
║  5  │ Log base doesn't matter     │ O(log₂n) = O(log₁₀n)      ║
║  6  │ 1+2+...+n = O(n²)          │ Gauss: n(n+1)/2             ║
║  7  │ Input ÷ every step → log n  │ Binary search, BST height  ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║  BONUS:                                                          ║
║  • n operations × O(1) each = O(n)                               ║
║  • n operations × O(n) each = O(n²) ← cẩn thận function call!  ║
║  • Recursion: vẽ tree, đếm nodes × work per node                ║
║  • Amortized: expensive rare ops averaged over many cheap ops    ║
║  • Space: LUÔN mention kèm time                                  ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## 8. Multi-Variable Complexity — Hay Bị Hỏi! (Chi Tiết)

> **Tại sao quan trọng?** Đây là nơi candidates SAI NHIỀU NHẤT. Phần lớn lỗi Big O trong phỏng vấn đến từ việc dùng 1 biến cho 2+ inputs khác nhau. Interviewer rất thích hỏi vì nó test depth of understanding.

### 8.1 Nguyên Tắc Cốt Lõi

```
═══ KHI NÀO CẦN MULTI-VARIABLE? ═══

Khi algorithm có 2+ inputs KÍCH THƯỚC KHÁC NHAU:
  → PHẢI dùng BIẾN KHÁC NHAU cho mỗi input

VÍ DỤ:
  • Graph: V vertices, E edges → O(V + E)
  • Two arrays: n elements, m elements → O(n + m) hoặc O(n × m)
  • Matrix: r rows, c columns → O(r × c)
  • String matching: n text length, m pattern length → O(n × m)
  • Tree: n nodes, h height → O(n) hoặc O(h)

═══ SAI LẦM #1 PHỔ BIẾN NHẤT ═══

❌ SAI: "Nested loops → O(n²)"
✅ ĐÚNG: "Nested loops trên KHÁC inputs → O(n × m)"

❌ SAI: "BFS is O(n)"
✅ ĐÚNG: "BFS is O(V + E)"

Hỏi bản thân: "Tất cả inputs có CÙNG SIZE không?"
  → CÓ → dùng 1 biến: O(n²)
  → KHÔNG → dùng nhiều biến: O(n × m)
```

---

### 8.2 Graph: O(V + E) — Chi Tiết

> Đây là multi-variable complexity QUAN TRỌNG NHẤT, vì graph problems rất phổ biến.

#### Tại Sao O(V + E) Chứ Không Phải O(V × E)?

```python
# BFS trên adjacency list:

def bfs(graph, start):
    visited = set()
    queue = deque([start])
    visited.add(start)

    while queue:                      # Mỗi vertex vào queue TỐI ĐA 1 lần
        node = queue.popleft()        # → Vòng while chạy TỐI ĐA V lần

        for neighbor in graph[node]:  # Duyệt edges của node
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)

# PHÂN TÍCH CHI TIẾT:
#
# Outer while: chạy TỐI ĐA V lần (mỗi vertex dequeue 1 lần)
# Inner for: cho TỪNG vertex v, chạy deg(v) lần
#
# TỔNG inner iterations = Σ deg(v) cho tất cả v
#                        = 2E (undirected) hoặc E (directed)
#
# → Total = V (dequeue ops) + E (edge checks) = O(V + E)
#
# KHÔNG PHẢI O(V × E) vì:
#   Inner loop KHÁC NHAU cho mỗi vertex!
#   Vertex 1 có 2 edges, Vertex 2 có 100 edges, ...
#   → TỔNG tất cả inner loops = E (không phải V × max_degree)
```

#### Dense vs Sparse — Khi Nào O(V + E) ≈ O(V²)?

```
╔══════════════════════════════════════════════════════════════════╗
║ Graph Type     │ E = ?          │ O(V + E) = ?    │ Ví dụ        ║
╠══════════════════════════════════════════════════════════════════╣
║ Sparse         │ E ≈ V          │ O(V + V) = O(V) │ Tree, chain  ║
║ Medium         │ E ≈ V log V    │ O(V log V)      │ Road network ║
║ Dense          │ E ≈ V²         │ O(V + V²) = O(V²)│ Complete     ║
║ Complete       │ E = V(V-1)/2   │ O(V²)           │ K_n          ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║ TREE: E = V - 1 → O(V + V-1) = O(V) ← edges = vertices - 1   ║
║       → DFS/BFS trên TREE là O(V), không cần nói O(V + E)     ║
║                                                                  ║
║ CONNECTED GRAPH: E ≥ V - 1 → O(V + E) = O(E) vì E dominates  ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝

TRONG PHỎNG VẤN:
  Luôn nói O(V + E), sau đó clarify nếu cần:
  "BFS is O(V + E). For a tree, E = V-1, so it simplifies to O(V).
   For a dense graph, E ≈ V², so it becomes O(V²)."
```

#### Các Graph Algorithms — Complexity Table

```
╔══════════════════════════════════════════════════════════════════╗
║ Algorithm              │ Time              │ Space              ║
╠══════════════════════════════════════════════════════════════════╣
║ BFS                    │ O(V + E)          │ O(V) queue+visited ║
║ DFS                    │ O(V + E)          │ O(V) stack+visited ║
║ Topological Sort (Kahn)│ O(V + E)          │ O(V + E)           ║
║ Topological Sort (DFS) │ O(V + E)          │ O(V)               ║
║ Dijkstra (min-heap)    │ O((V+E) log V)    │ O(V)               ║
║ Dijkstra (array)       │ O(V²)             │ O(V)               ║
║ Bellman-Ford           │ O(V × E)          │ O(V)               ║
║ Floyd-Warshall         │ O(V³)             │ O(V²)              ║
║ Kruskal (MST)          │ O(E log E)        │ O(V) Union-Find    ║
║ Prim (min-heap)        │ O((V+E) log V)    │ O(V)               ║
║ Tarjan (SCC)           │ O(V + E)          │ O(V)               ║
║ Union-Find (n ops)     │ O(n × α(n))       │ O(V)               ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║ CHÚ Ý: Dijkstra với min-heap:                                    ║
║   O((V + E) log V) vì:                                           ║
║   • Extract-min: V lần × O(log V) = O(V log V)                  ║
║   • Decrease-key: E lần × O(log V) = O(E log V)                 ║
║   → Total = O(V log V + E log V) = O((V+E) log V)               ║
║                                                                  ║
║   Sparse: O(V log V)           Dense: O(V² log V)               ║
║   → Khi dense, Dijkstra array O(V²) tốt hơn!                   ║
║                                                                  ║
╚══════════════════════════════════════════════════════════════════╝
```

#### Interview Script — Graph Complexity

```
SCRIPT 1 — BFS/DFS:
"My BFS traversal is O(V + E). Each vertex is enqueued
 and dequeued exactly once — that's O(V). For each vertex,
 I check all its neighbors, and the total neighbor checks
 across all vertices equals the number of edges — O(E)."

SCRIPT 2 — Dijkstra:
"Using Dijkstra with a min-heap, the time complexity is
 O((V + E) log V). The V log V comes from extract-min
 operations, and E log V from decrease-key operations.
 For a sparse graph, this is O(V log V). For a dense
 graph where E ≈ V², it's O(V² log V), which is why
 the simple array-based O(V²) Dijkstra might be better."

SCRIPT 3 — Tree vs Graph:
"Since the input is a tree, not a general graph,
 E = V - 1. So my DFS is O(V), not O(V + E).
 Space is O(h) for the recursion stack, where h
 is the tree height — O(log n) if balanced."
```

---

### 8.3 String Processing: O(n × m) — Chi Tiết

#### Brute Force Pattern Matching — Trace

```python
def brute_match(text, pattern):
    n, m = len(text), len(pattern)

    for i in range(n - m + 1):        # (n - m + 1) starting positions
        match = True
        for j in range(m):             # compare m characters
            if text[i + j] != pattern[j]:
                match = False
                break                  # early exit giúp average case
        if match:
            return i
    return -1

# TRACE: text = "AABAACAAB", pattern = "AACAA"
# n = 9, m = 5
#
# i=0: "AABAA" vs "AACAA" → j=2: B≠C → fail, break
# i=1: "ABAAC" vs "AACAA" → j=1: B≠A → fail, break
# i=2: "BAACA" vs "AACAA" → j=0: B≠A → fail, break
# i=3: "AACAA" vs "AACAA" → j=0..4: all match → return 3
#
# Worst case: O(n × m) — khi phải compare m chars mỗi position
#   VD: text = "AAAAAB", pattern = "AAB" → gần match mỗi lần
# Best case: O(n) — khi mismatch luôn ở char đầu
#   VD: text = "BCDEF", pattern = "AXY" → j=0 fail mỗi lần
```

#### String Algorithms — Comparison Table

```
╔══════════════════════════════════════════════════════════════════╗
║ Algorithm        │ Time              │ Space   │ Khi nào dùng    ║
╠══════════════════════════════════════════════════════════════════╣
║ Brute Force      │ O(n × m)          │ O(1)    │ Simple/short    ║
║ KMP              │ O(n + m)          │ O(m)    │ Single pattern  ║
║ Rabin-Karp       │ O(n + m) avg      │ O(1)    │ Multiple pattern║
║                  │ O(n × m) worst    │         │   (rolling hash)║
║ Boyer-Moore      │ O(n/m) best       │ O(σ)    │ Long patterns   ║
║                  │ O(n × m) worst    │         │                 ║
║ Aho-Corasick     │ O(n + m + z)      │ O(m)    │ Multi-pattern   ║
║                  │ z = # matches     │         │   simultaneously║
║ Suffix Array     │ O(n log n) build  │ O(n)    │ Many queries    ║
║                  │ O(m log n) query  │         │   on same text  ║
╚══════════════════════════════════════════════════════════════════╝

CHỌN ALGORITHM:
  • 1 pattern, 1 text → KMP O(n + m)
  • Nhiều patterns, 1 text → Aho-Corasick
  • 1 pattern, nhiều texts → Rabin-Karp (rolling hash reuse)
  • Text ngắn (< 1000 chars) → Brute force đủ tốt
```

#### String Operations — Hidden Costs

```python
# ═══ TRAP 1: String concatenation ═══
s = ""
for c in chars:         # n chars
    s += c              # TẠO string mới mỗi lần!
# → O(n²) time + space (vì immutable)
# FIX: "".join(chars) → O(n)

# ═══ TRAP 2: String comparison ═══
s1 == s2                # O(min(len(s1), len(s2)))
# KHÔNG phải O(1)! Phải compare từng char.

# ═══ TRAP 3: Substring check ═══
pattern in text         # Python: O(n × m) worst case
# Dùng built-in → internally optimized nhưng vẫn O(n×m) worst

# ═══ TRAP 4: String slicing ═══
s[i:j]                  # O(j - i) — tạo string MỚI!
# Trong loop: for i in range(n): s[:i] → O(1+2+...+n) = O(n²)

# NARRATE: "I need to be careful with string operations.
#  Concatenation in a loop is O(n²) due to string immutability.
#  I'll use a list and join at the end for O(n) total."
```

---

### 8.4 Matrix: O(rows × cols) — Chi Tiết

#### Basic Traversal

```python
# ═══ FULL TRAVERSAL ═══
for i in range(rows):
    for j in range(cols):
        process(matrix[i][j])
# → O(rows × cols) = O(r × c)
# NÓI O(n²) CHỈ KHI square matrix (r = c = n)

# ═══ DIAGONAL TRAVERSAL ═══
for i in range(min(rows, cols)):
    process(matrix[i][i])
# → O(min(r, c))

# ═══ BOUNDARY TRAVERSAL ═══
# Top row + bottom row + left col + right col (minus corners)
# → O(2r + 2c - 4) = O(r + c)
```

#### Search in Sorted Matrix

```python
# BÀI: Search in row-sorted + column-sorted matrix
# (mỗi row sorted, mỗi column sorted)

def search_matrix(matrix, target):
    if not matrix: return False
    rows, cols = len(matrix), len(matrix[0])

    # Start từ TOP-RIGHT corner
    r, c = 0, cols - 1

    while r < rows and c >= 0:
        if matrix[r][c] == target:
            return True
        elif matrix[r][c] > target:
            c -= 1          # loại cả column → đi trái
        else:
            r += 1          # loại cả row → đi xuống

    return False

# TIME: O(rows + cols) ← MỖI BƯỚC loại 1 row HOẶC 1 col
# Max steps: rows + cols (đi hết từ top-right đến bottom-left)
#
# SPACE: O(1)
#
# ⚠️ KHÁC VỚI: Binary search trên từng row → O(rows × log(cols))
# → Top-right approach TỐT HƠN khi rows ≈ cols!
#
# NARRATE: "Starting from the top-right corner, I can
#  eliminate either a row or a column at each step.
#  This gives O(r + c) time, which is better than
#  binary searching each row at O(r × log c)."
```

#### Matrix Multiplication

```python
# Standard matrix multiplication: A(r1×c1) × B(c1×c2)
def matrix_multiply(A, B):
    r1, c1 = len(A), len(A[0])
    c2 = len(B[0])
    result = [[0] * c2 for _ in range(r1)]

    for i in range(r1):           # O(r1)
        for j in range(c2):       # O(c2)
            for k in range(c1):   # O(c1)
                result[i][j] += A[i][k] * B[k][j]

    return result

# TIME: O(r1 × c1 × c2)
# Khi square (r1 = c1 = c2 = n): O(n³)
# SPACE: O(r1 × c2) cho result matrix

# QUAN TRỌNG: 3 biến, KHÔNG chỉ 1!
# NARRATE: "Matrix multiplication is O(n³) for n×n matrices,
#  or more precisely O(r × c1 × c2) for non-square matrices."

# ADVANCED: Strassen → O(n^2.807)
#           Coppersmith-Winograd → O(n^2.376) (theoretical)
```

---

### 8.5 Tree: Height vs Nodes

> Trees là multi-variable đặc biệt: operations phụ thuộc vào **h (height)** hoặc **n (nodes)**, nhưng h phụ thuộc vào n!

```
╔══════════════════════════════════════════════════════════════════╗
║ Tree Type        │ Height h      │ Nodes n    │ Relationship     ║
╠══════════════════════════════════════════════════════════════════╣
║ Balanced BST     │ O(log n)      │ n          │ h = log₂(n)     ║
║ Complete         │ O(log n)      │ n          │ h = ⌊log₂(n)⌋   ║
║ Skewed (worst)   │ O(n)          │ n          │ h = n - 1        ║
║ AVL / Red-Black  │ O(log n)      │ n          │ h ≤ 1.44 log₂(n)║
║ B-Tree (order m) │ O(log_m n)    │ n          │ shorter height   ║
╚══════════════════════════════════════════════════════════════════╝

OPERATIONS phụ thuộc HEIGHT:
  • Search: O(h)     ← đi từ root đến leaf
  • Insert: O(h)     ← tìm vị trí + insert
  • Delete: O(h)     ← tìm + restructure

  Balanced: h = log n → O(log n)
  Skewed: h = n → O(n) ← TỆ NHƯ LINKED LIST!

OPERATIONS phụ thuộc NODES:
  • Traversal (in/pre/post/level): O(n) ← visit ALL nodes
  • Count nodes: O(n)
  • Build tree: O(n) minimum

NARRATE: "BST search is O(h) where h is the tree height.
 For a balanced tree, h = O(log n), so search is O(log n).
 In the worst case of a skewed tree, h = n, degrading to O(n).
 That's why we use self-balancing trees like AVL or Red-Black."
```

---

### 8.6 Multi-Variable Trong Thực Tế — Database & API

```python
# ═══ VÍ DỤ 1: Pagination query ═══
# Query: SELECT * FROM users WHERE active = true LIMIT k OFFSET p

# Time: O(p + k) — DB phải SKIP p rows, rồi return k rows
# → p (offset) VÀ k (limit) là 2 biến!
# → Deep pagination (p lớn) = SLOW! Dùng cursor-based thay thế.

# ═══ VÍ DỤ 2: JOIN query ═══
# SELECT * FROM orders o JOIN users u ON o.user_id = u.id

# Nested loop join: O(n × m) — n orders, m users
# Hash join: O(n + m) — build hash trên smaller table
# Sorted merge join: O(n log n + m log m) — sort cả hai

# ═══ VÍ DỤ 3: API batch processing ═══
def process_batch(items, rules):
    for item in items:          # n items
        for rule in rules:       # k rules
            apply(rule, item)    # O(1)
# → O(n × k) — 2 biến!

# ═══ VÍ DỤ 4: Trie operations ═══
# Insert word: O(L) — L = length of word
# Search word: O(L)
# Build trie from N words: O(N × L_avg)
# → 2 biến: N (number of words) và L (word length)
```

---

### 8.7 Sai Lầm Phổ Biến — Multi-Variable Traps

```
╔══════════════════════════════════════════════════════════════════╗
║  #  │ SAI                      │ ĐÚNG                           ║
╠══════════════════════════════════════════════════════════════════╣
║  1  │ "BFS is O(n)"            │ "BFS is O(V + E)"              ║
║     │                          │ (V vertices, E edges)           ║
╠══════════════════════════════════════════════════════════════════╣
║  2  │ "Nested loops = O(n²)"   │ "O(n × m) if different inputs" ║
║     │                          │ (n ≠ m)                         ║
╠══════════════════════════════════════════════════════════════════╣
║  3  │ "Matrix traversal O(n²)" │ "O(r × c) if not square"       ║
║     │                          │ (rows ≠ cols)                   ║
╠══════════════════════════════════════════════════════════════════╣
║  4  │ "DFS on tree is O(V+E)"  │ "O(V) since E = V-1 for tree"  ║
║     │ (technically correct but │ (simpler, shows understanding)  ║
║     │  overly complex)         │                                  ║
╠══════════════════════════════════════════════════════════════════╣
║  5  │ "Dijkstra is O(V²)"     │ "O((V+E) log V) with min-heap" ║
║     │ (only for array version) │ "O(V²) with array version"      ║
╠══════════════════════════════════════════════════════════════════╣
║  6  │ "BST search is O(log n)" │ "O(h) — O(log n) if balanced,  ║
║     │ (only if balanced!)      │  O(n) if skewed"                ║
╠══════════════════════════════════════════════════════════════════╣
║  7  │ "Trie insert is O(1)"    │ "O(L) where L = word length"   ║
║     │ (confusing with HashMap) │                                  ║
╚══════════════════════════════════════════════════════════════════╝
```

### 8.8 Cheat Sheet — Multi-Variable

```
╔══════════════════════════════════════════════════════════════════╗
║ Context              │ Variables      │ Complexity                ║
╠══════════════════════════════════════════════════════════════════╣
║ Graph BFS/DFS        │ V, E           │ O(V + E)                  ║
║ Dijkstra (heap)      │ V, E           │ O((V+E) log V)           ║
║ Two arrays           │ n, m           │ O(n + m) or O(n × m)     ║
║ Matrix traversal     │ r, c           │ O(r × c)                  ║
║ Matrix search (sorted)│ r, c          │ O(r + c)                  ║
║ Matrix multiply      │ r, c1, c2      │ O(r × c1 × c2)           ║
║ String matching      │ n, m           │ O(n × m) or O(n + m)     ║
║ Tree operations      │ n, h           │ O(h) search, O(n) traverse║
║ Trie operations      │ N words, L len │ O(N × L)                  ║
║ HashMap build+query  │ n build, k quer│ O(n + k)                  ║
║ DB offset pagination │ p offset, k lim│ O(p + k)                  ║
╚══════════════════════════════════════════════════════════════════╝

GOLDEN RULE: Identify ALL input variables TRƯỚC KHI phân tích.
  Hỏi: "What are the dimensions of my input?"
  → Mỗi dimension = 1 biến trong complexity.
```

## 9. Input Size Guide — Biết Ngay Cần Algorithm Nào (Chi Tiết)

> **Tại sao cực quan trọng?** Đọc constraints = biết ngay target complexity = biết ngay dùng thuật gì. Đây là **skill #1** khi đọc đề trong phỏng vấn. Nắm được guide này = tiết kiệm 5-10 phút suy nghĩ.

### 9.1 Nền Tảng — Operations Per Second

```
═══ QUY TẮC 10⁸ ═══

Máy tính hiện đại thực hiện khoảng 10⁸ operations/giây.
(thực tế 10⁸ - 10⁹, nhưng 10⁸ là estimate an toàn)

Phỏng vấn thường cho TIME LIMIT = 1-2 giây.
→ Algorithm cần chạy trong ≤ ~10⁸ operations.

VÍ DỤ:
  n = 10⁵ → O(n²) = 10¹⁰ ops → 100 giây → TLE! ❌
  n = 10⁵ → O(n log n) ≈ 10⁵ × 17 ≈ 1.7 × 10⁶ ops → 0.02s → OK ✅
  n = 10³ → O(n²) = 10⁶ ops → 0.01s → OK ✅

CÔNG THỨC NHANH:
  n × target_complexity(n) ≤ 10⁸
  → Từ n suy ra max complexity cho phép.
```

---

### 9.2 Bảng Input Size — Chi Tiết Từng Tier

#### Tier 1: n ≤ 10-12 → O(n!) hoặc O(2ⁿ)

```
MAX OPS: 12! = 479,001,600 ≈ 5 × 10⁸ → vừa đủ
         2¹² = 4,096 → thoải mái

ALGORITHMS:
  • Brute force tất cả permutations
  • Backtracking không cần pruning mạnh
  • Try ALL subsets (2ⁿ)
  • Factorial recursion

BÀI MẪU:
  • N-Queens (n ≤ 12)
  • Traveling Salesman brute force
  • Permutations / generate all orderings
  • Word Break II (tất cả valid sentences)

CODE PATTERN:
  from itertools import permutations
  for perm in permutations(arr):    # n! permutations
      if is_valid(perm): ...         # O(n) check
  # Total: O(n! × n)

NARRATE: "Since n ≤ 12, I can afford O(n!) brute force.
 12! ≈ 480 million, which fits within the time limit."
```

#### Tier 2: n ≤ 20-25 → O(2ⁿ) hoặc O(2^(n/2))

```
MAX OPS: 2²⁰ = 1,048,576 ≈ 10⁶ → thoải mái
         2²⁵ = 33,554,432 ≈ 3 × 10⁷ → OK

ALGORITHMS:
  • Bitmask DP: dùng integer bits biểu diễn subset
  • Meet in the middle: chia input làm 2 nửa, merge
  • Subset generation + filtering
  • State space search

BÀI MẪU:
  • TSP with bitmask DP: dp[visited_mask][current_city]
  • Subset Sum (n ≤ 20)
  • Maximum clique in small graph
  • Partition into K equal subsets

CODE PATTERN (Bitmask DP):
  # n cities, dp[mask][i] = min cost visiting cities in mask, ending at i
  for mask in range(1 << n):        # 2ⁿ states
      for i in range(n):             # n cities
          if mask & (1 << i):        # city i in mask
              for j in range(n):     # try next city
                  # transition
  # Total: O(2ⁿ × n²)

NARRATE: "With n ≤ 20, I can use bitmask DP.
 The state space is 2²⁰ × 20 ≈ 20 million, which is feasible."
```

#### Tier 3: n ≤ 100 → O(n³) hoặc O(n² × log n)

```
MAX OPS: 100³ = 10⁶ → thoải mái

ALGORITHMS:
  • Floyd-Warshall (all-pairs shortest paths)
  • DP 3D / interval DP
  • Matrix exponentiation (cho n nhỏ)
  • Gaussian elimination

BÀI MẪU:
  • Optimal Matrix Chain Multiplication
  • Burst Balloons (interval DP)
  • All-pairs shortest paths (Floyd-Warshall)
  • Minimum cost to merge stones

CODE PATTERN (Interval DP):
  for length in range(2, n+1):         # khoảng cách
      for i in range(n - length + 1):   # start
          j = i + length - 1             # end
          for k in range(i, j):          # split point
              dp[i][j] = min(dp[i][j], dp[i][k] + dp[k+1][j] + cost)
  # Total: O(n³)

NARRATE: "The input size is 100, so O(n³) = 10⁶ operations
 is perfectly fine. I'll use interval DP."
```

#### Tier 4: n ≤ 1,000 → O(n²)

```
MAX OPS: 1000² = 10⁶ → thoải mái
         5000² = 2.5 × 10⁷ → vẫn OK

ALGORITHMS:
  • DP 2D (LCS, Edit Distance, Knapsack)
  • Brute force tất cả pairs (i, j)
  • Insertion Sort / Selection Sort (sort nhỏ)
  • BFS/DFS trên dense graph (E ≈ V²)

BÀI MẪU:
  • Longest Common Subsequence (LCS)
  • Edit Distance (Levenshtein)
  • 0/1 Knapsack
  • Palindrome Partitioning II

CODE PATTERN:
  dp = [[0] * (m+1) for _ in range(n+1)]
  for i in range(1, n+1):
      for j in range(1, m+1):
          dp[i][j] = ...
  # Total: O(n × m), n, m ≤ 1000

NARRATE: "Both strings are at most 1000 characters,
 so O(n × m) = 10⁶ for the 2D DP table is efficient."
```

#### Tier 5: n ≤ 10⁵ → O(n log n) hoặc O(n × √n)

```
MAX OPS: 10⁵ × log₂(10⁵) ≈ 10⁵ × 17 ≈ 1.7 × 10⁶ → rất tốt
         10⁵ × √(10⁵) ≈ 10⁵ × 316 ≈ 3 × 10⁷ → OK

ALGORITHMS:
  • Sorting + linear scan
  • Divide and conquer
  • Balanced BST / TreeMap / TreeSet
  • Segment Tree / BIT (Fenwick)
  • Merge sort (count inversions)
  • Mo's algorithm (O(n√n))

BÀI MẪU:
  • Merge Intervals (sort + scan)
  • Kth Largest Element (quickselect avg O(n))
  • Count Inversions (merge sort)
  • Range Sum Queries (Segment Tree)
  • Skyline Problem

QUAN TRỌNG — Đây là TIER PHỔ BIẾN NHẤT trong phỏng vấn!
  Phần lớn LeetCode Medium = n ≤ 10⁵ → target O(n log n) hoặc O(n)

NARRATE: "The constraint is n ≤ 10⁵. O(n²) would be
 10¹⁰ — too slow. I need O(n log n) or O(n).
 Let me sort first, then do a linear scan."
```

#### Tier 6: n ≤ 10⁶ → O(n)

```
MAX OPS: 10⁶ → thoải mái cho O(n)
         10⁶ × 20 (log) → cũng OK nhưng tight

ALGORITHMS:
  • Single pass (one for loop)
  • Two pointers
  • Sliding window
  • HashMap / HashSet
  • Counting sort / Radix sort
  • Stack-based (monotonic stack)
  • Kadane's algorithm

BÀI MẪU:
  • Two Sum (HashMap O(n))
  • Maximum Subarray (Kadane's O(n))
  • Longest Substring Without Repeating Characters
  • Trapping Rain Water (stack hoặc two pointers)
  • Next Greater Element (monotonic stack)

CODE PATTERNS:
  # Two pointers
  left, right = 0, len(arr) - 1
  while left < right: ...

  # Sliding window
  for right in range(n):
      window.add(arr[right])
      while invalid:
          window.remove(arr[left])
          left += 1

  # HashMap
  seen = {}
  for i, num in enumerate(arr):
      if target - num in seen: return [seen[target-num], i]
      seen[num] = i

NARRATE: "With n up to 10⁶, I need O(n) or O(n log n).
 I'll use a sliding window / two pointers / HashMap
 for a single-pass O(n) solution."
```

#### Tier 7: n ≤ 10⁸ → O(n) nhưng cẩn thận

```
MAX OPS: 10⁸ → vừa ĐÚNG giới hạn!

CHÚ Ý ĐẶC BIỆT:
  • O(n) VỚI constant nhỏ → OK
  • O(n) VỚI constant lớn → TLE!
  • O(n log n) = 10⁸ × 27 ≈ 3 × 10⁹ → TLE! ❌

ALGORITHMS:
  • Very efficient O(n) — ít overhead
  • Precompute (Sieve of Eratosthenes cho primes ≤ 10⁸)
  • Linear time algorithms (counting sort, prefix sum)

TIPS:
  • Tránh HashMap overhead → dùng array nếu key range nhỏ
  • Tránh recursion → iterative (tránh stack overhead)
  • Tránh object creation → primitive types
  • Tránh I/O đọc chậm → buffer I/O

NARRATE: "n is 10⁸, which is at the limit. I need a clean
 O(n) solution with minimal constant factor — no HashMap
 overhead, no recursion, just array-based computation."
```

#### Tier 8: n ≥ 10⁹ → O(log n), O(√n), hoặc O(1)

```
MAX OPS: log₂(10⁹) ≈ 30 → thoải mái
         √(10⁹) ≈ 31,623 → thoải mái
         log₂(10¹⁸) ≈ 60 → thoải mái

ALGORITHMS:
  • Binary search (trên answer space)
  • Math formula trực tiếp
  • Fast exponentiation (O(log n))
  • Matrix exponentiation (Fibonacci O(log n))
  • Number theory (GCD, modular arithmetic)

BÀI MẪU:
  • Binary search on answer (Koko Eating Bananas)
  • Pow(x, n) — fast exponentiation
  • Fibonacci number (matrix exponentiation)
  • Count primes up to n (Sieve O(n))
  • GCD (Euclidean O(log min(a,b)))

CODE PATTERN (Binary Search on Answer):
  lo, hi = min_possible, max_possible
  while lo < hi:
      mid = (lo + hi) // 2
      if can_achieve(mid):    # O(n) check
          hi = mid
      else:
          lo = mid + 1
  # Total: O(n × log(answer_range))
  # answer_range ≤ 10⁹ → log ≈ 30
  # Nếu n = 10⁵: 10⁵ × 30 = 3 × 10⁶ → OK ✅

NARRATE: "Since n is 10⁹, I can't even iterate through
 all elements. I need O(log n) — likely binary search
 or a mathematical formula."
```

---

### 9.3 Reverse Lookup — Algorithm → Expected Input Size

```
╔══════════════════════════════════════════════════════════════════╗
║ Algorithm / Approach         │ Expected n     │ Max ops          ║
╠══════════════════════════════════════════════════════════════════╣
║ Brute force permutations     │ n ≤ 10-12      │ ~10⁸             ║
║ Bitmask DP                   │ n ≤ 20-25      │ ~10⁷             ║
║ O(n³) DP / Floyd-Warshall    │ n ≤ 100-500    │ ~10⁸             ║
║ O(n²) DP / brute pairs       │ n ≤ 1,000-5,000│ ~10⁷             ║
║ O(n log n) sort + scan       │ n ≤ 10⁵-10⁶   │ ~10⁷             ║
║ O(n) single pass             │ n ≤ 10⁶-10⁷   │ ~10⁷             ║
║ O(√n) factorization          │ n ≤ 10¹²-10¹⁴ │ ~10⁷             ║
║ O(log n) binary search       │ n ≤ 10¹⁸       │ ~60              ║
║ O(1) math formula            │ any n          │ constant          ║
╚══════════════════════════════════════════════════════════════════╝

DÙNG KHI: Bạn chọn algorithm TRƯỚC → check input size CÓ ĐỦ không.
```

---

### 9.4 Chiến Lược Phỏng Vấn — Input Size Flow

```
KHI ĐỌC ĐỀ PHỎNG VẤN:

STEP 1: Đọc CONSTRAINTS trước → biết n bao nhiêu
  ↓
STEP 2: Tra bảng → biết target complexity
  ↓
STEP 3: Filter algorithms → chỉ xét algorithms đạt target
  ↓
STEP 4: Chọn algorithm phù hợp nhất + implement

VÍ DỤ THỰC TẾ:

  Đề: "Given an array of n integers..." → n ≤ 10⁵

  Brain: "10⁵ → O(n log n) hoặc O(n)"
       → Loại: O(n²) brute force ❌
       → Xét:  Sorting? Two pointers? HashMap? Sliding window?
       → Chọn: HashMap → O(n) ✅

  Đề: "Given a string of length n..." → n ≤ 20

  Brain: "20 → O(2ⁿ) OK = 10⁶"
       → Loại: DP O(n²) (overkill, nhưng vẫn OK)
       → Xét:  Bitmask? Backtracking? Subset generation?
       → Chọn: Backtracking + pruning ✅
```

#### Narration Scripts

```
SCRIPT 1 — Khi nhận đề:
"Let me look at the constraints first. n can be up to 10⁵,
 so I need O(n log n) or better. An O(n²) brute force
 would be 10¹⁰ operations — too slow for a 1-second limit."

SCRIPT 2 — Khi justify approach:
"Given n ≤ 1000 and m ≤ 1000, a 2D DP solution with
 O(n × m) = 10⁶ operations should run comfortably
 within the time limit."

SCRIPT 3 — Khi optimize:
"My current O(n²) solution works for n ≤ 1000. But the
 constraints say n can be up to 10⁵, so I need to optimize.
 Let me think about an O(n log n) approach using sorting,
 or O(n) using a HashMap."

SCRIPT 4 — Khi n rất lớn:
"n can be up to 10⁹, which means I can't even iterate
 through all elements. This suggests binary search on
 the answer space, or a mathematical formula."
```

### 9.5 Bảng Tóm Tắt — Quick Reference

```
╔══════════════════════════════════════════════════════════════════════╗
║ n           │ Target       │ Algorithms                  │ Ops      ║
╠══════════════════════════════════════════════════════════════════════╣
║ ≤ 12        │ O(n!)        │ Permutations, brute force   │ ~5×10⁸  ║
║ ≤ 25        │ O(2ⁿ)        │ Bitmask DP, subsets         │ ~3×10⁷  ║
║ ≤ 100       │ O(n³)        │ Floyd-Warshall, interval DP │ ~10⁶    ║
║ ≤ 1,000     │ O(n²)        │ 2D DP, brute pairs          │ ~10⁶    ║
║ ≤ 5,000     │ O(n²)        │ 2D DP (tight)               │ ~2.5×10⁷║
║ ≤ 10⁵       │ O(n log n)   │ Sort+scan, segment tree     │ ~2×10⁶  ║
║ ≤ 10⁶       │ O(n)         │ HashMap, two ptrs, sliding  │ ~10⁶    ║
║ ≤ 10⁷       │ O(n)         │ Simple linear, prefix sum   │ ~10⁷    ║
║ ≤ 10⁸       │ O(n) careful │ No overhead, array-based    │ ~10⁸    ║
║ ≤ 10⁹       │ O(√n)/O(logn)│ Binary search, math         │ ~3×10⁴  ║
║ ≤ 10¹⁸      │ O(log n)     │ Binary search, fast exp     │ ~60     ║
╚══════════════════════════════════════════════════════════════════════╝

HỌC THUỘC LÒNG bảng này. Đây là "cheat code" cho phỏng vấn.
```

## 10. Common Mistakes — Lỗi Hay Gặp Trong Phỏng Vấn

### Mistake 1: "Nested loops = always O(n²)"

```python
# SAI! Phụ thuộc inner loop chạy bao nhiêu lần

# Case 1: O(n) — inner loop constant
for i in range(n):
    for j in range(10):  # 10 lần, không phải n!
        process(i, j)
# → O(10n) = O(n)

# Case 2: O(n) — two pointers dù dùng while
left = 0
for right in range(n):
    while left < right and condition:
        left += 1  # left chỉ tăng, KHÔNG reset
# left di chuyển TỐI ĐA n lần tổng cộng → O(n + n) = O(n)

# Case 3: O(n log n) — inner loop logarithmic
for i in range(n):
    j = i
    while j > 0:
        j //= 2    # logarithmic inner loop
# → n × log n = O(n log n)
```

### Mistake 2: Quên Space Complexity Cho Recursion

```python
# Code trông "O(1) space" nhưng thực ra O(n)!
def reverse_list(head):
    if not head or not head.next:
        return head
    new_head = reverse_list(head.next)  # O(n) STACK FRAMES!
    head.next.next = head
    head.next = None
    return new_head

# Time: O(n) ✅
# Space: O(n) ← call stack! Nhiều người nói O(1) ← SAI!

# Iterative version:
# Space: O(1) ← thật sự O(1), không recursion
```

### Mistake 3: "HashMap is always O(1)"

```
SAI! HashMap là O(1) AMORTIZED AVERAGE case.
Worst case: O(n) — khi tất cả keys hash cùng bucket.

ĐÚNG: "HashMap lookup is O(1) amortized. In the worst case
 with poor hash distribution, it degrades to O(n), but
 with a good hash function this is extremely unlikely."
```

### Mistake 4: ".sort() is O(n)"

```
SAI! Built-in sort là O(n log n).

Python: Timsort → O(n log n) average, O(n) best (nearly sorted)
JavaScript: V8 Timsort → O(n log n)
Java: Dual-pivot Quicksort (primitives), Timsort (objects)

NARRATE: "After sorting in O(n log n), I can use binary
 search in O(log n), making the total O(n log n)."
```

### Mistake 5: Nói Big O Mà Không Giải Thích WHY

```
❌ BAD: "It's O(n)."
✅ GOOD: "It's O(n) because I iterate through the array once.
          The HashMap lookup inside the loop is O(1) amortized,
          so the loop body is constant time, giving O(n) total."

❌ BAD: "Space is O(1)."
✅ GOOD: "Space is O(1) — I only use a few variables regardless
          of input size. No additional data structures needed."

→ Giải thích WHY = show understanding
→ Chỉ nêu answer = show memorization
```

---

## 11. Câu Hỏi Phỏng Vấn Mẫu + Cách Trả Lời

### Q1: "What's the time complexity of your solution?"

```
ANSWER TEMPLATE:
"Time complexity is O(___).

The outer loop runs n times. [O(n)]
Inside, I do [operation] which takes [O(___)] per iteration.
[Optional: HashMap lookup is O(1) amortized.]
Combined: O(n) × O(1) = O(n).

Space complexity is O(___).
[I use a HashMap that stores at most n entries → O(n).]
[OR: I only use constant extra variables → O(1).]

Compared to the brute force O(n²), this is an improvement
from [10¹² operations to 10⁶] for typical input sizes."
```

### Q2: "Can you optimize this from O(n²) to O(n)?"

```
FRAMEWORK:
1. Xác định bottleneck: "The inner loop searches for [X] in O(n)."
2. Trade space for time: "If I precompute this in a HashMap..."
3. Narrate improvement: "Now lookup is O(1) instead of O(n),
   making the total O(n) with O(n) extra space."

COMMON OPTIMIZATIONS:
O(n²) → O(n log n): Sort + two pointers / binary search
O(n²) → O(n):       HashMap / HashSet for O(1) lookup
O(n)  → O(log n):   Binary search (if sorted or monotonic)
O(n)  → O(1):       Math formula / bit manipulation
```

### Q3: "Is this optimal? Can you prove it?"

```
ANSWER TEMPLATE:
"I believe this is optimal. Here's why:

[For search/transform problems:]
Any algorithm must examine each element at least once
to verify the answer. So the lower bound is Ω(n).
My solution is O(n), which matches the lower bound.

[For comparison-based sorting:]
The information-theoretic lower bound for comparison sort
is Ω(n log n). My solution uses comparison sort, matching this.

[For specific problems:]
This problem requires [reading all input / comparing all pairs /
visiting all nodes], so [Ω(n) / Ω(V+E)] is a lower bound."
```

### Q4: "What happens if n is 10⁸?"

```
ANSWER:
"At n = 10⁸:
- O(n) → 10⁸ operations ≈ 1 second (modern CPU ~ 10⁸-10⁹ ops/sec)
  → Barely acceptable, needs efficient constant factors.
- O(n log n) → ~2.7 × 10⁹ → borderline, may TLE
- O(n²) → 10¹⁶ → absolutely impossible, would take ~3 years

So at this scale, I need O(n) or better.
My current solution is O(n), which should work,
but I'd want to minimize the constant factor —
avoid unnecessary allocations, use arrays over HashMaps
where possible, and minimize branch mispredictions."
```

---

## 12. Think Out Loud Scripts — Cho Mọi Tình Huống

### Script 1: Nêu Complexity Sau Khi Code Xong

```
"Let me analyze the complexity.

Time: The main loop runs n times. Inside, I do a HashMap
lookup which is O(1) amortized. So overall: O(n).

Space: I store at most n entries in the HashMap, plus a
constant number of variables. So: O(n).

This is a significant improvement over the brute force O(n²).
For n = 10⁵, that's 10⁵ operations instead of 10¹⁰."
```

### Script 2: Dùng Complexity Để Chọn Approach

```
"The constraint says n ≤ 10⁵. That tells me:
- O(n²) = 10¹⁰ → too slow
- O(n log n) = ~10⁶ → acceptable
- O(n) = 10⁵ → ideal

So I need at least O(n log n). Let me think about what
data structure gives me that... Sorting is O(n log n),
and after sorting I can use two pointers in O(n).
Total: O(n log n)."
```

### Script 3: Justify Optimality

```
"This solution is O(n) time and O(n) space.

Is this optimal? Well, we must read every element at least
once to check if the target exists. So Ω(n) is a lower
bound. My solution matches this lower bound, so it's
optimal in time.

For space, we could potentially reduce to O(1) if the
array were sorted, using two pointers. But sorting
itself costs O(n log n) time, which would be slower.
So O(n) space with O(n) time is the best trade-off."
```

---

## Liên Kết

- 📖 Chi tiết: [0.4.1-Big-O-Notation.md](../../0.4.1-Big-O-Notation.md)
- 🧮 Toán ứng dụng: [0.4.2-Toan-Ung-Dung.md](../../0.4.2-Toan-Ung-Dung.md)
- 📝 Interview Framework: [0.5.1-Technical-Interview-Preparation.md](../../0.5.1-Technical-Interview-Preparation.md)
