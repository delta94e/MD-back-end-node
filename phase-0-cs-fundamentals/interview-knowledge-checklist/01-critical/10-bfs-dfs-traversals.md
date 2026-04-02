# 10. BFS & DFS — Tree + Graph Traversals

> 📖 Tài liệu chi tiết: [0.2.3-Trees-and-Heaps.md](../../0.2.3-Trees-and-Heaps.md) + [0.2.4-Graphs.md](../../0.2.4-Graphs.md)

## Checklist Học

- [ ] BFS: Queue-based, level-by-level, shortest path (unweighted)
- [ ] DFS: Stack/Recursion-based, go deep first, backtrack
- [ ] Tree Traversals: Inorder (Left-Root-Right), Preorder (Root-Left-Right), Postorder (Left-Right-Post)
- [ ] Khi nào BFS vs DFS: shortest path → BFS, explore all paths → DFS
- [ ] Space: BFS O(width), DFS O(height/depth)
- [ ] Graph vs Tree: graph CẦN visited set, tree KHÔNG (no cycles)
- [ ] Multi-source BFS: add multiple start nodes to queue

---

## Khi Nào Dùng Cái Nào?

| Criteria                   | BFS               | DFS                           |
| -------------------------- | ----------------- | ----------------------------- |
| Shortest path (unweighted) | ✅ Tối ưu         | ❌ Không đảm bảo              |
| Explore ALL paths          | ❌ Phức tạp       | ✅ Tự nhiên                   |
| Level-by-level processing  | ✅ Native         | ❌ Cần thêm logic             |
| Space (tree)               | O(width) = O(n/2) | O(height) = O(log n balanced) |
| Detect cycle               | ✅ Có thể         | ✅ Có thể                     |
| Topological sort           | ✅ Kahn's         | ✅ DFS + finish time          |

## Tree Traversals — Phải Thuộc!

```
        1
       / \
      2   3
     / \
    4   5

Inorder   (Left-Root-Right):  4, 2, 5, 1, 3  ← BST → sorted!
Preorder  (Root-Left-Right):  1, 2, 4, 5, 3  ← serialize tree
Postorder (Left-Right-Root):  4, 5, 2, 3, 1  ← delete bottom-up
Level-order (BFS):            1, 2, 3, 4, 5  ← breadth-first
```

---

## Câu Hỏi Phỏng Vấn Mẫu

1. "Binary Tree Level Order Traversal" — BFS
2. "Number of Islands" — DFS/BFS on grid
3. "Maximum Depth of Binary Tree" — DFS
4. "Word Ladder" — BFS shortest transformation
5. "Binary Tree Inorder Traversal" — recursive + iterative
6. "Serialize and Deserialize Binary Tree" — preorder

---

## Liên Kết

- 📖 Trees: [0.2.3-Trees-and-Heaps.md](../../0.2.3-Trees-and-Heaps.md)
- 📖 Graphs: [0.2.4-Graphs.md](../../0.2.4-Graphs.md)
