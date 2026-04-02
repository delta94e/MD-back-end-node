# 09. Back-of-Envelope Estimation — Tính Toán Nhanh

## Checklist Học

- [ ] Estimating QPS: DAU × requests/user / 86400
- [ ] Storage estimates: records × size × retention
- [ ] Bandwidth: QPS × request size
- [ ] Các con số cần nhớ: powers of 2, latency numbers
- [ ] Read/Write ratio: typical = 100:1, social = 1000:1

---

## Bảng Số Cần Nhớ

```
1 KB  = 10³  bytes
1 MB  = 10⁶  bytes
1 GB  = 10⁹  bytes
1 TB  = 10¹² bytes

1 day = 86,400 seconds ≈ 10⁵ seconds
1 month ≈ 2.5 × 10⁶ seconds
1 year ≈ 3 × 10⁷ seconds

Latency numbers:
L1 cache:           1 ns
L2 cache:           4 ns
RAM:               100 ns
SSD random read:   150 μs
HDD seek:          10 ms
Network (same DC):  0.5 ms
Network (cross DC): 150 ms
```
