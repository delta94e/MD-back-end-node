# 📋 Interview Knowledge Checklist — Cấu Trúc Thư Mục

> Tổ chức toàn bộ kiến thức cần thiết cho phỏng vấn kỹ thuật theo 3 cấp ưu tiên, liên kết đến các tài liệu chi tiết đã có trong project.

## Cấu Trúc

```
interview-knowledge-checklist/
│
├── 🔴 01-critical/                    # PHẢI biết 100% — thiếu = fail
│   ├── 01-big-o-notation.md           # Time & Space, Best/Avg/Worst
│   ├── 02-hash-tables.md              # DS quan trọng nhất (>50% bài phỏng vấn)
│   ├── 03-arrays-strings.md           # Manipulation, two pointers, sliding window
│   ├── 04-stacks-queues.md            # FILO vs FIFO, monotonic stack
│   ├── 05-linked-lists.md             # Singly, doubly, circular, fast/slow pointer
│   ├── 06-trees.md                    # Binary, BST, N-ary, Trie
│   ├── 07-graphs.md                   # Adjacency list/matrix, objects+pointers
│   ├── 08-sorting.md                  # Quicksort, Mergesort (PHẢI biết detail)
│   ├── 09-binary-search.md            # Template, variations, boundary handling
│   └── 10-bfs-dfs-traversals.md       # Tree + Graph traversal, Inorder/Pre/Post
│
├── 🟡 02-important/                   # NÊN biết — đặc biệt Mid/Senior
│   ├── 01-dynamic-programming.md      # Fibonacci, Knapsack, LCS, 1D/2D DP
│   ├── 02-dijkstra-shortest-path.md   # Weighted graph, priority queue
│   ├── 03-topological-sort.md         # DAG, Kahn's, DFS-based
│   ├── 04-greedy-algorithms.md        # Greedy choice property, proof sketch
│   ├── 05-programming-language.md     # Thành thạo 1 ngôn ngữ (JS/Python/Java)
│   └── 06-oop-design.md              # SOLID, Polymorphism, Encapsulation
│
├── 🟢 03-nice-to-have/               # Senior / System Design rounds
│   ├── 01-system-design-overview.md   # Scoping, use cases, constraints
│   ├── 02-database-schema.md          # SQL vs NoSQL, normalization, indexes
│   ├── 03-scaling.md                  # Vertical vs Horizontal, CAP theorem
│   ├── 04-caching.md                  # Redis, CDN, cache invalidation
│   ├── 05-load-balancing.md           # Round robin, consistent hashing
│   ├── 06-db-replication.md           # Master-slave, sharding, partitioning
│   ├── 07-microservices.md            # Service communication, saga pattern
│   ├── 08-message-queues.md           # Kafka, RabbitMQ, pub/sub
│   ├── 09-estimation.md              # Back-of-envelope calculations
│   └── 10-math-foundations.md         # Discrete math, probability, bit manipulation
│
└── README.md                          # File này
```

## Liên Kết Đến Tài Liệu Chi Tiết Đã Có

| Topic                                   | File chi tiết                                                                                           | Phase   |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------- | ------- |
| Big O Notation                          | [0.4.1-Big-O-Notation.md](../0.4.1-Big-O-Notation.md)                                                   | Phase 0 |
| Hash Tables                             | [0.2.2-Hash-Table-Deep-Dive.md](../0.2.2-Hash-Table-Deep-Dive.md)                                       | Phase 0 |
| Arrays / Stacks / Queues / Linked Lists | [0.2.1-Linear-Data-Structures.md](../0.2.1-Linear-Data-Structures.md)                                   | Phase 0 |
| Trees & Heaps                           | [0.2.3-Trees-and-Heaps.md](../0.2.3-Trees-and-Heaps.md)                                                 | Phase 0 |
| Graphs                                  | [0.2.4-Graphs.md](../0.2.4-Graphs.md) + [0.4.3-Graph-Theory-Co-Ban.md](../0.4.3-Graph-Theory-Co-Ban.md) | Phase 0 |
| Sorting & Searching                     | [0.2.5-Sorting-and-Searching.md](../0.2.5-Sorting-and-Searching.md)                                     | Phase 0 |
| Dynamic Programming                     | [0.2.6-Dynamic-Programming.md](../0.2.6-Dynamic-Programming.md)                                         | Phase 0 |
| Advanced Algorithms (Greedy, Topo Sort) | [0.2.7-Advanced-Algorithms.md](../0.2.7-Advanced-Algorithms.md)                                         | Phase 0 |
| LeetCode Roadmap                        | [0.2.8-LeetCode-Roadmap.md](../0.2.8-LeetCode-Roadmap.md)                                               | Phase 0 |
| JavaScript Mastery                      | [Phase 1](../../phase-1-javascript-mastery/)                                                            | Phase 1 |
| System Design                           | [Phase 5](../../phase-5-system-design/)                                                                 | Phase 5 |
| Interview Prep Framework                | [0.5.1-Technical-Interview-Preparation.md](../0.5.1-Technical-Interview-Preparation.md)                 | Phase 0 |
| Behavioral Interview                    | [9.1-Behavioral-Interview.md](../../phase-9-interview-prep/9.1-Behavioral-Interview.md)                 | Phase 9 |

## Cách Sử Dụng

1. **Bắt đầu từ 🔴 CRITICAL** — master 100% trước khi chuyển sang level tiếp theo
2. **Mỗi file** chứa: lý thuyết tóm tắt, patterns phỏng vấn, câu hỏi mẫu, script Think Out Loud
3. **Liên kết** đến tài liệu chi tiết đã có trong project
4. **Checklist** ở mỗi file để track tiến độ học
