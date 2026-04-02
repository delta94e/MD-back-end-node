# 02. Hash Tables — Data Structure Quan Trọng Nhất

> 📖 Tài liệu chi tiết: [0.2.2-Hash-Table-Deep-Dive.md](../../0.2.2-Hash-Table-Deep-Dive.md)

## Tại Sao Quan Trọng Nhất?

> Xuất hiện trong **>50% bài phỏng vấn!** Two Sum → HashMap. Anagrams → HashMap. Frequency count → HashMap. Caching (LRU Cache) → HashMap. Duplicate detection → HashSet. Nếu chỉ được chọn 1 data structure để master → chọn **Hash Table**.

## Checklist Học

- [ ] Implement Hash Table từ scratch (array + hashing + collision handling)
- [ ] Collision handling: Chaining (linked list) vs Open Addressing (linear/quadratic probing)
- [ ] Time complexity: O(1) average, O(n) worst case — giải thích TẠI SAO
- [ ] Phân biệt khi nào dùng HashMap (key→value) vs HashSet (chỉ key)
- [ ] Load factor & rehashing — khi nào resize?
- [ ] Hash function requirements: deterministic, uniform distribution, fast
- [ ] Language-specific: JS `Map` vs `Object`, Python `dict`, Java `HashMap`

---

## Tóm Tắt Nhanh

### Operations & Complexity

| Operation | Average | Worst | Ghi chú                      |
| --------- | ------- | ----- | ---------------------------- |
| Insert    | O(1)    | O(n)  | Rehash khi load factor cao   |
| Lookup    | O(1)    | O(n)  | Worst case: all keys collide |
| Delete    | O(1)    | O(n)  | Chaining: remove from list   |
| Contains  | O(1)    | O(n)  | HashSet                      |

### Collision Handling

```
CHAINING (Separate Chaining):
┌───┐
│ 0 │ → [key1, val1] → [key5, val5] → null
├───┤
│ 1 │ → [key2, val2] → null
├───┤
│ 2 │ → null
├───┤
│ 3 │ → [key3, val3] → null
└───┘
• Ưu: đơn giản, không bao giờ "full"
• Nhược: pointer overhead, cache miss

OPEN ADDRESSING (Linear Probing):
┌───┬───────────┐
│ 0 │ [key1, v1] │  ← hash(key1) = 0
├───┼───────────┤
│ 1 │ [key5, v5] │  ← hash(key5) = 0, probe → 1
├───┼───────────┤
│ 2 │  empty     │
├───┼───────────┤
│ 3 │ [key3, v3] │
└───┴───────────┘
• Ưu: cache-friendly, ít memory overhead
• Nhược: clustering, cần resize sớm hơn
```

### Patterns Phỏng Vấn Phổ Biến

```
1. TWO SUM PATTERN — O(n) lookup
   "Tôi cần tìm complement = target - current.
    HashMap cho O(1) lookup thay vì O(n) scan."

2. FREQUENCY COUNT — đếm occurrences
   "HashMap key=element, value=count.
    Một pass O(n) để đếm, một pass O(n) để tìm."

3. GROUPING / ANAGRAM — group by key
   "Sort mỗi string làm key, group anagrams cùng key.
    HashMap<String, List<String>>."

4. DEDUPLICATION — unique elements
   "HashSet cho O(1) membership check.
    Add tất cả → size() = số unique."

5. CACHING — LRU Cache
   "HashMap + Doubly Linked List.
    HashMap cho O(1) lookup, DLL cho O(1) eviction."
```

---

## Câu Hỏi Phỏng Vấn Mẫu

1. "Implement a hash table from scratch with put, get, delete"
2. "Two Sum — find two numbers that sum to target"
3. "Group Anagrams — group strings that are anagrams"
4. "First unique character in a string"
5. "LRU Cache — design with O(1) operations"
6. "Explain collision handling strategies"

## Think Out Loud Script

```
"I'll use a HashMap here because I need O(1) lookup.
 The key will be [X], the value will be [Y].
 This trades O(n) space for O(n²) → O(n) time improvement.

 For collision handling: in practice, hash tables use
 chaining or open addressing. The average case is O(1)
 because a good hash function distributes keys uniformly."
```

---

## Liên Kết

- 📖 Chi tiết: [0.2.2-Hash-Table-Deep-Dive.md](../../0.2.2-Hash-Table-Deep-Dive.md)
- 📝 LRU Cache walkthrough: [0.5.1-Technical-Interview-Preparation.md §6.17.12](../../0.5.1-Technical-Interview-Preparation.md)
