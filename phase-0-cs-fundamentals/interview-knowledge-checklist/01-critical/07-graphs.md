# 07. Graphs — Adjacency List, Matrix, Traversal

> 📖 Tài liệu chi tiết: [0.2.4-Graphs.md](../../0.2.4-Graphs.md) + [0.4.3-Graph-Theory-Co-Ban.md](../../0.4.3-Graph-Theory-Co-Ban.md)

## Checklist Học

- [ ] Representations: adjacency list (thông dụng nhất), adjacency matrix, edge list
- [ ] Directed vs Undirected, Weighted vs Unweighted
- [ ] BFS: shortest path (unweighted), level-by-level
- [ ] DFS: path finding, cycle detection, connected components
- [ ] Visited set: PHẢI CÓ để tránh infinite loop
- [ ] Build graph from problem input (nodes & edges)
- [ ] Cycle detection: directed (DFS visiting states) vs undirected (parent tracking)

---

## Patterns Phỏng Vấn

### 1. BFS — Shortest Path (Unweighted)

```
queue = [start]
visited = {start}
distance = 0
while queue:
    for _ in range(len(queue)):
        node = queue.pop(0)
        if node == target: return distance
        for neighbor in graph[node]:
            if neighbor not in visited:
                visited.add(neighbor)
                queue.append(neighbor)
    distance += 1

Script: "For shortest path in unweighted graph, BFS is optimal.
 Each level of BFS represents one step further from source."
```

### 2. DFS — Connected Components / Island Counting

```
visited = set()
count = 0
for node in all_nodes:
    if node not in visited:
        dfs(node, visited)
        count += 1

Script: "I model this as a graph. Each cell is a node,
 adjacent cells are edges. DFS marks all connected cells.
 Each new DFS call = a new island/component."
```

### 3. Topological Sort — DAG Ordering

```
Kahn's Algorithm (BFS-based):
1. Count in-degrees for all nodes
2. Add nodes with in-degree 0 to queue
3. Process queue: remove edges, add new in-degree 0

Script: "This is a dependency problem → topological sort.
 I use Kahn's algorithm: start with nodes that have
 no prerequisites (in-degree 0)."
```

---

## Câu Hỏi Phỏng Vấn Mẫu

1. "Number of Islands" — DFS/BFS on grid
2. "Clone Graph" — BFS + HashMap
3. "Course Schedule" — topological sort / cycle detection
4. "Word Ladder" — BFS shortest transformation
5. "Pacific Atlantic Water Flow" — multi-source DFS
6. "Network Delay Time" — Dijkstra (weighted)

---

## Liên Kết

- 📖 Chi tiết: [0.2.4-Graphs.md](../../0.2.4-Graphs.md)
- 📖 Graph Theory: [0.4.3-Graph-Theory-Co-Ban.md](../../0.4.3-Graph-Theory-Co-Ban.md)
