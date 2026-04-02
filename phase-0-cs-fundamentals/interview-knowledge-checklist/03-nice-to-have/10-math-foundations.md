# 10. Math Foundations — Discrete Math, Probability, Bit Manipulation

> 📖 Tài liệu chi tiết: [0.4.2-Toan-Ung-Dung.md](../../0.4.2-Toan-Ung-Dung.md) + [0.1.1-Binary-va-So-Hoc-Nhi-Phan.md](../../0.1.1-Binary-va-So-Hoc-Nhi-Phan.md)

## Checklist Học

- [ ] Discrete math: counting, pigeonhole principle, inclusion-exclusion
- [ ] Permutations: n! / (n-k)! — order matters
- [ ] Combinations: n! / (k! × (n-k)!) — order doesn't matter
- [ ] Probability basics: independent events, conditional probability
- [ ] Bit manipulation: AND, OR, XOR, NOT, shifts
- [ ] Bit tricks: n & (n-1), n & (-n), XOR properties
- [ ] Powers of 2: check with n & (n-1) == 0

---

## Bit Manipulation Cheat Sheet

```
a & b    AND: cả hai bit = 1
a | b    OR:  ít nhất 1 bit = 1
a ^ b    XOR: exactly 1 bit = 1
~a       NOT: flip all bits
a << n   Left shift:  × 2ⁿ
a >> n   Right shift: ÷ 2ⁿ

Tricks:
n & (n-1)   Clear lowest set bit
n & (-n)    Isolate lowest set bit
a ^ a = 0   Self-cancel (find unique)
a ^ 0 = a   Identity
```

---

## Liên Kết

- 📖 Binary: [0.1.1-Binary-va-So-Hoc-Nhi-Phan.md](../../0.1.1-Binary-va-So-Hoc-Nhi-Phan.md)
- 📖 Toán ứng dụng: [0.4.2-Toan-Ung-Dung.md](../../0.4.2-Toan-Ung-Dung.md)
- 📝 Narration: [0.5.1-Technical-Interview-Preparation.md §6.17.18](../../0.5.1-Technical-Interview-Preparation.md)
