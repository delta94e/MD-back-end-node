# 06. Trees — Binary, BST, N-ary, Trie

> 📖 Tài liệu chi tiết: [0.2.3-Trees-and-Heaps.md](../../0.2.3-Trees-and-Heaps.md)

## Checklist Học

- [ ] Binary Tree: node có tối đa 2 children
- [ ] BST: left < root < right — inorder traversal = sorted
- [ ] Traversals: Inorder (Left-Root-Right), Preorder (Root-Left-Right), Postorder (Left-Right-Root)
- [ ] BFS level-order traversal (Queue)
- [ ] DFS recursive + iterative (Stack)
- [ ] Height, depth, balanced tree
- [ ] N-ary tree: multiple children
- [ ] Trie (Prefix Tree): autocomplete, word search
- [ ] Heap: min-heap, max-heap — O(log n) insert/extract

---

## Patterns Phỏng Vấn

### 1. DFS Recursive — Base Case First

```
def dfs(node):
    if not node: return base_value  # BASE CASE LUÔN TRƯỚC!
    left = dfs(node.left)
    right = dfs(node.right)
    return combine(left, right)    # POST-ORDER processing

Script: "I'll start with the base case: if null, return [X].
 Then recursively solve left and right subtrees.
 The information flows UPWARD from leaves to root."
```

### 2. BFS Level-Order — Queue Snapshot

```
queue = [root]
while queue:
    level_size = len(queue)  # SNAPSHOT current level
    for i in range(level_size):
        node = queue.pop(0)
        process(node)
        if node.left: queue.append(node.left)
        if node.right: queue.append(node.right)

Script: "For level-by-level processing, I use BFS with a queue.
 The key trick: snapshot the queue length at each level."
```

### 3. BST — Inorder = Sorted

```
Validate BST: inorder traversal must be strictly increasing
Kth smallest: inorder traversal, return Kth element
Search: O(h) — left if smaller, right if larger

Script: "BST property: inorder traversal gives sorted order.
 I can leverage this for Kth smallest by doing inorder
 and counting — O(h + k) time."
```

---

## Câu Hỏi Phỏng Vấn Mẫu

1. "Maximum Depth of Binary Tree" — DFS recursive
2. "Invert Binary Tree" — DFS swap children
3. "Validate BST" — DFS with min/max bounds
4. "Level Order Traversal" — BFS with queue
5. "Lowest Common Ancestor" — DFS
6. "Implement Trie" — design data structure
7. "Kth Smallest Element in BST" — inorder

---

## Liên Kết

- 📖 Chi tiết: [0.2.3-Trees-and-Heaps.md](../../0.2.3-Trees-and-Heaps.md)
