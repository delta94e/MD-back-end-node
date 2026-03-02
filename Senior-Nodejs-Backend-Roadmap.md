# 🚀 ROADMAP: Trở Thành Senior Node.js Backend Developer

> **Mục tiêu**: Từ zero CS knowledge → Senior Backend Developer chuyên sâu Node.js, đủ sức phỏng vấn bất kỳ Big Tech nào (Google, Meta, Amazon, Microsoft, Apple, Netflix, Stripe, Shopify…).
>
> **Triết lý**: Hiểu **tận gốc** (first principles), không học vẹt. Mỗi phần đều đào đến mức có thể **giải thích cho người khác** và **trả lời câu hỏi follow-up** ở bất kỳ độ sâu nào.
>
> **Thời gian ước tính**: 18–24 tháng học nghiêm túc (4–6 giờ/ngày).

---

## 📋 Mục Lục

| Phase | Chủ đề                                                                   | Thời gian |
| ----- | ------------------------------------------------------------------------ | --------- |
| 0     | [Nền Tảng Computer Science](#phase-0--nền-tảng-computer-science)         | 3–4 tháng |
| 1     | [JavaScript Mastery](#phase-1--javascript-mastery)                       | 2–3 tháng |
| 2     | [Node.js Deep Dive](#phase-2--nodejs-deep-dive)                          | 2–3 tháng |
| 3     | [Database & Data Layer](#phase-3--database--data-layer)                  | 2–3 tháng |
| 4     | [API Design & Communication](#phase-4--api-design--communication)        | 1–2 tháng |
| 5     | [System Design & Architecture](#phase-5--system-design--architecture)    | 2–3 tháng |
| 6     | [DevOps, Cloud & Infrastructure](#phase-6--devops-cloud--infrastructure) | 1–2 tháng |
| 7     | [Security](#phase-7--security)                                           | 1 tháng   |
| 8     | [Testing & Quality](#phase-8--testing--quality)                          | 1 tháng   |
| 9     | [Soft Skills & Interview Prep](#phase-9--soft-skills--interview-prep)    | Liên tục  |

---

## Phase 0 — Nền Tảng Computer Science

> 🎯 **Tại sao quan trọng**: Big Tech luôn hỏi CS fundamentals. Không có nền tảng này, bạn sẽ không thể giải thích **tại sao** một giải pháp tốt hơn giải pháp khác.

### 0.1 — Cách Máy Tính Hoạt Động

**Mục tiêu**: Hiểu máy tính từ hardware lên software.

| Chủ đề                   | Độ sâu cần đạt                                                                       | Tài nguyên                                                                      |
| ------------------------ | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------- |
| Binary & số học nhị phân | Chuyển đổi thành thạo, hiểu two's complement, floating point (IEEE 754)              | _Code: The Hidden Language of Computer Hardware and Software_ – Charles Petzold |
| CPU Architecture         | Instruction cycle (fetch-decode-execute), registers, ALU, cache (L1/L2/L3), pipeline | CS:APP (Computer Systems: A Programmer's Perspective)                           |
| Memory Hierarchy         | RAM vs ROM, virtual memory, paging, page faults, TLB                                 | CS:APP Chapter 6, 9                                                             |
| OS Fundamentals          | Process vs Thread, context switching, scheduling algorithms, deadlock, IPC           | OSTEP (Operating Systems: Three Easy Pieces) — miễn phí                         |
| File Systems             | Inodes, file descriptors, block storage, journaling                                  | OSTEP                                                                           |
| I/O Models               | Blocking vs Non-blocking, Synchronous vs Asynchronous, select/poll/epoll/kqueue      | _Understanding Unix/Linux Programming_                                          |

**Câu hỏi phỏng vấn cần trả lời được**:

- Process vs Thread khác nhau thế nào ở mức OS? Context switch của thread có thực sự nhẹ hơn process không? Tại sao?
- Giải thích Virtual Memory hoạt động ra sao. Page fault xảy ra khi nào? TLB miss ảnh hưởng performance thế nào?
- `epoll` khác `select` và `poll` ra sao? Tại sao `epoll` hiệu quả hơn ở scale lớn? Liên hệ với Event Loop của Node.js?
- Deadlock xảy ra khi nào? 4 điều kiện cần và đủ (Coffman conditions)? Cách phòng tránh?

---

### 0.2 — Cấu Trúc Dữ Liệu & Giải Thuật (DSA)

> ⚠️ **Đây là phần QUAN TRỌNG NHẤT cho phỏng vấn Big Tech**. Cần luyện hàng ngày.

#### 0.2.1 — Data Structures

| Cấu trúc        | Độ sâu                                                                                                         | Big-O cần nhớ                                |
| --------------- | -------------------------------------------------------------------------------------------------------------- | -------------------------------------------- |
| **Array**       | Contiguous memory, cache-friendly, dynamic arrays (amortized doubling)                                         | Access O(1), Search O(n), Insert/Delete O(n) |
| **Linked List** | Singly, Doubly, Circular. Pointer manipulation, sentinel nodes                                                 | Access O(n), Insert/Delete O(1) tại node     |
| **Stack**       | LIFO, call stack, undo operations, expression parsing                                                          | Push/Pop O(1)                                |
| **Queue**       | FIFO, BFS, task scheduling. Circular queue, Deque                                                              | Enqueue/Dequeue O(1)                         |
| **Hash Table**  | Hash functions, collision resolution (chaining vs open addressing), load factor, rehashing, amortized analysis | Average: Insert/Search/Delete O(1)           |
| **Tree**        | Binary Tree, BST, AVL, Red-Black Tree. Traversal (in/pre/post/level-order)                                     | BST Average O(log n), Worst O(n)             |
| **Heap**        | Min-heap, Max-heap, binary heap implementation bằng array, heapify                                             | Insert/Extract O(log n), Build O(n)          |
| **Trie**        | Prefix tree, autocomplete, dictionary                                                                          | Insert/Search O(m) — m = word length         |
| **Graph**       | Adjacency list vs matrix, directed/undirected, weighted, DAG                                                   | Depends on algorithm                         |
| **Advanced**    | Segment Tree, Fenwick Tree, Disjoint Set (Union-Find), Bloom Filter, Skip List                                 | Tùy bài                                      |

#### 0.2.2 — Algorithms

| Nhóm                    | Thuật toán                                                                                 | Phải thành thạo                                                              |
| ----------------------- | ------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------- |
| **Sorting**             | Bubble, Selection, Insertion, Merge Sort, Quick Sort, Heap Sort, Counting Sort, Radix Sort | Viết code không nhìn. Phân tích stability, in-place, best/worst/average case |
| **Searching**           | Binary Search (và các biến thể), DFS, BFS                                                  | Template binary search cho mọi biến thể                                      |
| **Dynamic Programming** | Top-down (memoization) vs Bottom-up (tabulation), state transition, space optimization     | Nhận diện bài DP, viết recurrence relation                                   |
| **Greedy**              | Activity selection, Huffman coding, interval scheduling                                    | Chứng minh greedy choice property                                            |
| **Graph**               | Dijkstra, Bellman-Ford, Floyd-Warshall, Topological Sort, Kruskal, Prim, Tarjan (SCC)      | Implement + biết khi nào dùng                                                |
| **Backtracking**        | N-Queens, Sudoku solver, permutations/combinations                                         | Template + pruning                                                           |
| **String**              | KMP, Rabin-Karp, Longest Common Substring/Subsequence                                      | Ít nhất KMP                                                                  |
| **Divide & Conquer**    | Merge Sort, Quick Select, Closest Pair                                                     | Master Theorem                                                               |
| **Bit Manipulation**    | XOR tricks, bit masking, power of 2, counting bits                                         | Các bài LeetCode phổ biến                                                    |

#### 0.2.3 — Lộ Trình Luyện LeetCode

```
Tháng 1-2: Easy (150 bài)
  → Nắm vững Array, String, Hash Map, Two Pointers, Sliding Window
  → Stack, Queue, Linked List basics
  → Binary Search template

Tháng 3-4: Medium (200 bài)
  → Tree/Graph: DFS, BFS, BST operations
  → Dynamic Programming: 1D, 2D, knapsack
  → Backtracking, Greedy
  → Heap, Trie

Tháng 5-6: Hard (50-80 bài) + Contest
  → Advanced DP, Graph (network flow nếu đủ thời gian)
  → System Design kết hợp

Tổng tối thiểu: 400-430 bài
Pattern-based approach > brute-force grinding
```

**Tài nguyên**:

- **NeetCode 150** (roadmap miễn phí tốt nhất)
- **Blind 75** (bộ kinh điển)
- _Grokking the Coding Interview_ (pattern-based)
- _Introduction to Algorithms_ (CLRS) — reference, không đọc hết
- _Algorithm Design Manual_ — Steven Skiena (dễ đọc hơn CLRS)

---

### 0.3 — Networking Fundamentals

| Chủ đề                 | Độ sâu                                                                                                                           | Tại sao quan trọng cho Backend                         |
| ---------------------- | -------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| **OSI Model / TCP/IP** | 7 layers, encapsulation, PDU ở mỗi layer                                                                                         | Hiểu data đi qua network thế nào                       |
| **TCP**                | 3-way handshake, 4-way teardown, sequence numbers, ACK, sliding window, congestion control (Slow Start, AIMD), Nagle's algorithm | Giải thích tại sao TCP reliable, ảnh hưởng đến latency |
| **UDP**                | Connectionless, use cases (DNS, gaming, video streaming)                                                                         | Khi nào chọn UDP vs TCP                                |
| **HTTP/HTTPS**         | Request/Response cycle, methods, status codes, headers, cookies, HTTP/1.1 vs HTTP/2 vs HTTP/3 (QUIC)                             | Core protocol cho web backend                          |
| **TLS/SSL**            | Handshake, certificates, symmetric vs asymmetric encryption, certificate chain, HSTS                                             | Bảo mật giao tiếp                                      |
| **DNS**                | Recursive vs Iterative resolution, caching, TTL, record types (A, AAAA, CNAME, MX, NS, TXT)                                      | Domain resolution, CDN routing                         |
| **WebSocket**          | Upgrade handshake, full-duplex, heartbeat, reconnection                                                                          | Real-time features                                     |
| **gRPC**               | Protocol Buffers, HTTP/2 transport, streaming types (unary, server, client, bidirectional)                                       | Microservice communication                             |

**Câu hỏi phỏng vấn**:

- HTTP/2 multiplexing giải quyết vấn đề gì của HTTP/1.1? Head-of-line blocking ở tầng nào?
- HTTP/3 dùng QUIC thay TCP — tại sao? Lợi ích gì?
- Giải thích toàn bộ flow khi bạn gõ `https://google.com` vào trình duyệt.
- WebSocket vs SSE vs Long Polling — trade-offs?

---

### 0.4 — Toán Cho Lập Trình

| Chủ đề                   | Cần biết                                                             |
| ------------------------ | -------------------------------------------------------------------- |
| **Big-O Notation**       | Time & Space complexity, amortized analysis, best/worst/average case |
| **Logarithms**           | log₂(n), tại sao BST/Binary Search là O(log n)                       |
| **Combinatorics cơ bản** | Permutation, Combination — cho backtracking problems                 |
| **Probability cơ bản**   | Load balancing, consistent hashing, Bloom filter false positive rate |
| **Modular Arithmetic**   | Hashing, cryptography basics                                         |
| **Graph Theory cơ bản**  | Degree, path, cycle, connected components, DAG                       |

---

## Phase 1 — JavaScript Mastery

> 🎯 **Mục tiêu**: Hiểu JS engine-level, không chỉ syntax. Bạn phải giải thích được **tại sao** JS hoạt động như vậy, không chỉ **cách** dùng.

### 1.1 — Engine & Runtime

| Chủ đề                     | Độ sâu                                                                                                                                                                                                                                                                  |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **V8 Engine Architecture** | Parser → AST → Ignition (interpreter) → TurboFan (JIT compiler). Hidden Classes, Inline Caches                                                                                                                                                                          |
| **Memory Management**      | Stack vs Heap, Generational GC (Young Gen → Old Gen), Scavenger vs Mark-Sweep-Compact, V8's Orinoco (concurrent/incremental/parallel GC)                                                                                                                                |
| **Execution Context**      | Global EC, Function EC, Eval EC. Creation Phase vs Execution Phase. Variable Environment vs Lexical Environment                                                                                                                                                         |
| **Call Stack**             | Stack frames, stack overflow, tail call optimization (TCO)                                                                                                                                                                                                              |
| **Event Loop**             | Cực kỳ chi tiết: Call Stack → Microtask Queue (Promise, queueMicrotask, MutationObserver) → Macrotask Queue (setTimeout, setInterval, I/O, setImmediate). Phase order trong Node.js (libuv): timers → pending callbacks → idle/prepare → poll → check → close callbacks |
| **Hoisting**               | `var` hoisting (declaration, not initialization), `let`/`const` TDZ (Temporal Dead Zone), function declaration vs expression hoisting                                                                                                                                   |

**Câu hỏi phỏng vấn cần master**:

```javascript
// Bạn phải giải thích output và TẠI SAO
console.log(1);
setTimeout(() => console.log(2), 0);
Promise.resolve().then(() => console.log(3));
process.nextTick(() => console.log(4));
console.log(5);
// Output: 1, 5, 4, 3, 2 — GIẢI THÍCH TỪ MỨC EVENT LOOP PHASES
```

---

### 1.2 — Core Language Deep Dive

| Chủ đề                             | Kiến thức cần đạt                                                                                                                                                                                            |
| ---------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Types & Coercion**               | 8 types (undefined, null, boolean, number, bigint, string, symbol, object). Abstract equality (==) algorithm step-by-step. `typeof null === 'object'` tại sao (legacy bug). `Number.isNaN` vs global `isNaN` |
| **Scope & Closures**               | Lexical scope, scope chain lookup, closure memory model (chỉ capture biến cần, không capture entire scope trong V8 tối ưu hóa). Module pattern, data privacy                                                 |
| **`this` keyword**                 | 4 rules theo thứ tự ưu tiên: new binding > explicit binding (call/apply/bind) > implicit binding > default binding. Arrow function KHÔNG có `this` riêng                                                     |
| **Prototypes**                     | `[[Prototype]]` chain, `Object.create()`, `__proto__` vs `.prototype`, property shadowing, `hasOwnProperty` vs `in`. ES6 class là syntactic sugar — chứng minh                                               |
| **`new` Operator**                 | 4 bước: (1) tạo object mới, (2) set [[Prototype]], (3) bind this, (4) return. Custom `new` implementation                                                                                                    |
| **Iterators & Generators**         | Iterator protocol (`[Symbol.iterator]`, `next()`), Generator functions (`function*`, `yield`), lazy evaluation, infinite sequences, async generators                                                         |
| **Proxy & Reflect**                | Meta-programming, trapping operations, reactive systems (Vue 3 reactivity dùng Proxy)                                                                                                                        |
| **WeakRef & FinalizationRegistry** | Weak references, garbage collection observability                                                                                                                                                            |

---

### 1.3 — Asynchronous JavaScript

| Chủ đề                   | Độ sâu                                                                                                                                                                                                       |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Callbacks**            | Callback hell, error-first convention, inversion of control problem                                                                                                                                          |
| **Promises**             | Promise states (pending/fulfilled/rejected), `.then()` chaining (luôn return new Promise), error propagation, `Promise.all` / `allSettled` / `race` / `any`. Microtask queue. Implement Promise from scratch |
| **async/await**          | Syntactic sugar over generators + promises, error handling pattern (try/catch vs `.catch()`). Sequential vs parallel execution pitfall                                                                       |
| **Concurrency Patterns** | Promise pooling (limit concurrent promises), debounce/throttle, race condition handling, AbortController                                                                                                     |

**Bài tập bắt buộc**:

- Implement `Promise` class from scratch (constructor, then, catch, finally, all, race, allSettled, any)
- Implement `Promise.all` with concurrency limit
- Implement `async/await` using generators

---

### 1.4 — Modern JavaScript (ES6+)

| Feature                                    | Ứng dụng thực tế                                                                                         |
| ------------------------------------------ | -------------------------------------------------------------------------------------------------------- | --- | --- |
| **Destructuring**                          | Parameter extraction, API response parsing                                                               |
| **Spread/Rest**                            | Shallow copy, function arguments, merging objects                                                        |
| **Modules**                                | ESM (`import/export`) vs CommonJS (`require/module.exports`). Tree shaking, circular dependency handling |
| **Optional Chaining & Nullish Coalescing** | `?.` và `??` — khác gì `                                                                                 |     | `   |
| **Map, Set, WeakMap, WeakSet**             | Use cases cho mỗi loại. WeakMap cho private data, caching                                                |
| **Symbols**                                | Well-known symbols: `Symbol.iterator`, `Symbol.toPrimitive`, `Symbol.hasInstance`                        |
| **Tagged Templates**                       | SQL injection prevention (e.g., `sql` tagged template trong Prisma)                                      |

---

## Phase 2 — Node.js Deep Dive

> 🎯 **Mục tiêu**: Hiểu Node.js từ C++ binding lên JavaScript API. Bạn phải giải thích được **libuv**, **V8 integration**, và cách Node.js thực sự xử lý concurrent requests.

### 2.1 — Architecture & Internals

| Chủ đề                   | Độ sâu                                                                                                                                                             |
| ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Node.js Architecture** | V8 + libuv + C++ bindings + JS API. Single-threaded nhưng non-blocking nhờ libuv thread pool                                                                       |
| **libuv Event Loop**     | 6 phases chi tiết: timers → pending callbacks → idle/prepare → poll → check → close. `process.nextTick` vs `setImmediate` vs `setTimeout(fn, 0)`                   |
| **Thread Pool**          | Default 4 threads (UV_THREADPOOL_SIZE), dùng cho: fs operations, DNS lookup (dns.lookup), crypto, zlib. KHÔNG dùng cho network I/O (epoll/kqueue handle trực tiếp) |
| **C++ Addons & N-API**   | Cách viết native addon, khi nào cần (CPU-intensive tasks), N-API stability                                                                                         |
| **Worker Threads**       | `worker_threads` module, SharedArrayBuffer, Atomics, MessageChannel. So sánh với cluster                                                                           |
| **Cluster Module**       | Fork processes, IPC, sticky sessions. So sánh với PM2 cluster mode                                                                                                 |
| **Child Process**        | `spawn` vs `exec` vs `execFile` vs `fork`. IPC channel, stdio                                                                                                      |

**Câu hỏi phỏng vấn nâng cao**:

- Node.js là single-threaded — vậy nó handle 10,000 concurrent requests thế nào? Giải thích chi tiết từ kernel level (epoll) lên application level.
- `process.nextTick` có thể gây starvation cho event loop không? Tại sao? Khi nào nên dùng?
- Thread pool mặc định 4 threads — nếu có 100 concurrent `fs.readFile`, chuyện gì xảy ra?

---

### 2.2 — Core Modules Mastery

| Module             | Kiến thức cần đạt                                                                                                                                                                                       |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **`fs`**           | Sync vs Async vs Promises API. Streams-based file operations. `fs.watch` vs `chokidar`. File descriptors                                                                                                |
| **`http`/`https`** | Raw server creation, request/response lifecycle, keep-alive, connection pooling, `http.Agent`                                                                                                           |
| **`net`**          | TCP server/client, socket programming, backpressure                                                                                                                                                     |
| **`stream`**       | **CỰC KỲ QUAN TRỌNG**: Readable, Writable, Transform, Duplex, PassThrough. Backpressure mechanism (`highWaterMark`, `drain` event). Pipeline (`stream.pipeline`). Object mode. Implement custom streams |
| **`buffer`**       | Binary data handling, encoding (utf-8, base64, hex), Buffer.alloc vs Buffer.allocUnsafe, ArrayBuffer relationship                                                                                       |
| **`events`**       | EventEmitter internals, `on` vs `once` vs `addListener`, memory leaks (MaxListenersExceededWarning), `removeListener`, error handling convention                                                        |
| **`crypto`**       | Hashing (SHA-256, bcrypt for passwords), HMAC, symmetric encryption (AES), asymmetric (RSA), key pair generation, `crypto.randomBytes`                                                                  |
| **`path`**         | Cross-platform path handling, `path.resolve` vs `path.join`, `__dirname` vs `import.meta.url`                                                                                                           |
| **`os`**           | CPU info cho load balancing decisions, memory monitoring                                                                                                                                                |
| **`cluster`**      | Multi-process architecture, load balancing, zero-downtime restarts                                                                                                                                      |
| **`zlib`**         | Compression/decompression streams, gzip cho HTTP responses                                                                                                                                              |

---

### 2.3 — Streams Deep Dive

> Streams là **kiến thức signature** của senior Node.js developer. Hầu hết junior/mid không hiểu sâu.

```
                    ┌─────────────────────────────────────────┐
                    │           Node.js Streams               │
                    │                                         │
                    │  ┌──────────┐      ┌──────────┐        │
                    │  │ Readable │─────▶│ Writable │        │
                    │  └──────────┘      └──────────┘        │
                    │                                         │
                    │  ┌──────────┐      ┌──────────┐        │
                    │  │  Duplex  │      │Transform │        │
                    │  │(Read+    │      │(Transform│        │
                    │  │ Write)   │      │ data)    │        │
                    │  └──────────┘      └──────────┘        │
                    │                                         │
                    │  Backpressure: highWaterMark + drain    │
                    └─────────────────────────────────────────┘
```

**Phải implement được**:

1. Custom Readable stream (e.g., đọc data từ database theo batch)
2. Custom Transform stream (e.g., CSV parser, encryption)
3. Pipeline with error handling
4. Backpressure handling manual (không dùng `pipeline`)

**Real-world scenarios**:

- Upload file lớn (multi-GB) mà không hết memory
- ETL pipeline: đọc CSV → transform → write to database
- Real-time log processing
- Video transcoding pipeline

---

### 2.4 — Package & Module System

| Chủ đề         | Độ sâu                                                                                                                                          |
| -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| **CommonJS**   | `require` resolution algorithm, module caching, circular dependencies handling                                                                  |
| **ES Modules** | Static analysis, top-level await, interop với CJS, `.mjs` vs `"type": "module"`                                                                 |
| **npm**        | `package.json` deep dive, semver, `package-lock.json` tại sao quan trọng, `peerDependencies`, `optionalDependencies`, npm workspaces (monorepo) |
| **Security**   | `npm audit`, supply chain attacks, dependency scanning, lockfile integrity                                                                      |

---

### 2.5 — Error Handling & Debugging

| Chủ đề                    | Kiến thức                                                                                                                                                |
| ------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Error Types**           | Operational errors vs Programmer errors. Custom error classes, error codes                                                                               |
| **Async Error Handling**  | unhandledRejection, uncaughtException, domain (deprecated) → why `async_hooks`                                                                           |
| **Debugging**             | `--inspect`, Chrome DevTools, CPU profiling, heap snapshots, flame graphs                                                                                |
| **Memory Leaks**          | Closures giữ reference, EventEmitter listeners, global variables, detached DOM (ít liên quan BE). Tools: `--max-old-space-size`, `heapdump`, `clinic.js` |
| **Performance Profiling** | `perf_hooks`, `console.time`, clinic flame, 0x, autocannon (load testing)                                                                                |

---

### 2.6 — NestJS Framework

> NestJS là framework **enterprise-grade** phổ biến nhất cho Node.js backend. Hầu hết các công ty lớn sử dụng NestJS hoặc framework tương tự. **Bắt buộc phải master**.

| Chủ đề                         | Độ sâu                                                                                                                                                                                                                 |
| ------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Architecture**               | Modular architecture (Modules, Controllers, Providers). So sánh với Express: tại sao cần structure? Inspiration từ Angular (decorators, DI). Opinionated vs unopinionated frameworks                                   |
| **Dependency Injection**       | IoC Container, Provider scope (DEFAULT/REQUEST/TRANSIENT), custom providers (`useClass`, `useValue`, `useFactory`, `useExisting`), circular dependency handling (`forwardRef`). Hiểu DI pattern sâu — không chỉ NestJS |
| **Modules**                    | Feature modules, shared modules, global modules, dynamic modules (`forRoot`/`forRootAsync`/`forFeature`). Lazy-loading modules. Module encapsulation                                                                   |
| **Controllers & Routing**      | Decorators (`@Get`, `@Post`, `@Param`, `@Body`, `@Query`), route parameters, sub-domain routing, request lifecycle, versioning                                                                                         |
| **Providers & Services**       | Service layer architecture, repository pattern, custom providers, optional providers                                                                                                                                   |
| **Middleware**                 | Functional vs Class middleware, global middleware, route-specific middleware. So sánh với Express middleware                                                                                                           |
| **Guards**                     | Authentication guards (`canActivate`), role-based authorization, `@SetMetadata` + `Reflector`. Execution order: Middleware → Guards → Interceptors → Pipes → Handler                                                   |
| **Interceptors**               | Request/Response transformation, logging, caching, timeout, `RxJS` operators (`map`, `tap`, `catchError`). AOP (Aspect-Oriented Programming) concept                                                                   |
| **Pipes**                      | Validation (`ValidationPipe` + `class-validator` + `class-transformer`), transformation, custom pipes. Global vs scoped pipes                                                                                          |
| **Exception Filters**          | Built-in HTTP exceptions, custom exception filters, global filters, exception hierarchy                                                                                                                                |
| **TypeORM/Prisma Integration** | Module configuration, repository injection, transaction management, migration strategies                                                                                                                               |
| **Authentication**             | Passport.js integration, JWT strategy, Local strategy, OAuth2, session-based auth, custom `AuthGuard`                                                                                                                  |
| **Microservices**              | Transport layers (TCP, Redis, NATS, Kafka, gRPC, RabbitMQ), message patterns (`@MessagePattern`, `@EventPattern`), hybrid application (HTTP + microservice)                                                            |
| **WebSocket**                  | `@WebSocketGateway`, rooms, namespaces, Socket.io vs ws adapter                                                                                                                                                        |
| **CQRS Module**                | Commands, Queries, Events, Sagas — khi nào dùng, khi nào overkill                                                                                                                                                      |
| **Testing**                    | Unit testing với `@nestjs/testing` (`Test.createTestingModule`), mocking providers, e2e testing với Supertest, testing guards/interceptors/pipes                                                                       |
| **Configuration**              | `@nestjs/config`, validation schema (Joi/Zod), environment-specific configs, namespaced configuration                                                                                                                  |
| **Swagger/OpenAPI**            | Auto-generated API docs (`@nestjs/swagger`), decorators (`@ApiTags`, `@ApiResponse`, `@ApiProperty`), DTO documentation                                                                                                |

**Câu hỏi phỏng vấn NestJS**:

- NestJS request lifecycle: middleware → guards → interceptors (before) → pipes → handler → interceptors (after) → exception filters. Giải thích chi tiết thứ tự và use case mỗi layer.
- Dependency Injection hoạt động thế nào trong NestJS? Provider scope ảnh hưởng gì đến memory và performance?
- So sánh NestJS vs Express vs Fastify — khi nào dùng framework nào? Trade-offs?
- Làm sao implement CQRS + Event Sourcing trong NestJS cho hệ thống e-commerce?
- `forRoot` vs `forFeature` dynamic module pattern — giải thích use case và cách implement.

**Tài nguyên**:

- NestJS official documentation (docs.nestjs.com — rất tốt)
- _NestJS in Action_ — practical projects
- NestJS course by Ariel Weinberger (Udemy)

---

## Phase 3 — Database & Data Layer

### 3.1 — PostgreSQL Deep Dive

| Chủ đề                 | Độ sâu                                                                                                                                                                                                                      |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **SQL Mastery**        | JOINs (INNER, LEFT, RIGHT, FULL, CROSS, SELF), Subqueries vs CTEs, Window Functions (ROW_NUMBER, RANK, DENSE_RANK, LAG, LEAD, SUM OVER), HAVING vs WHERE, GROUP BY, UNION/INTERSECT/EXCEPT                                  |
| **Schema Design**      | Normalization (1NF → BCNF), denormalization trade-offs, many-to-many relationships, polymorphic associations, table inheritance                                                                                             |
| **Indexing**           | B-tree, Hash, GIN, GiST, BRIN. Composite indexes (column order matters!). Partial indexes. Expression indexes. Index-only scans. EXPLAIN ANALYZE đọc thành thạo                                                             |
| **Query Optimization** | Sequential Scan vs Index Scan vs Bitmap Scan. Join algorithms (Nested Loop, Hash Join, Merge Join). Query planner statistics. `pg_stat_statements`                                                                          |
| **Transactions**       | ACID properties chi tiết. Isolation levels (Read Uncommitted, Read Committed, Repeatable Read, Serializable) — hiểu từng anomaly mà mỗi level prevent. MVCC (Multi-Version Concurrency Control) — cách PostgreSQL implement |
| **Locks**              | Row-level vs Table-level locks, advisory locks, deadlock detection, `FOR UPDATE` / `FOR SHARE` / `SKIP LOCKED`                                                                                                              |
| **Partitioning**       | Range, List, Hash partitioning. Partition pruning. When to partition                                                                                                                                                        |
| **Replication**        | Streaming replication, logical replication, WAL (Write-Ahead Log), synchronous vs asynchronous. Read replicas. Failover                                                                                                     |
| **Advanced Features**  | JSONB operations, full-text search, materialized views, triggers, stored procedures, PL/pgSQL                                                                                                                               |

**Câu hỏi phỏng vấn**:

- MVCC hoạt động thế nào trong PostgreSQL? Transaction ID, tuple visibility, vacuum?
- Thiết kế schema cho social network (users, posts, followers, likes) — normalize hay denormalize? Trade-offs?
- Query chậm — bạn debug thế nào? Walk through EXPLAIN ANALYZE output.
- Khi nào dùng Read Committed vs Serializable? Phantom read là gì? Write skew là gì?

---

### 3.2 — MongoDB

| Chủ đề                         | Độ sâu                                                                                         |
| ------------------------------ | ---------------------------------------------------------------------------------------------- |
| **Document Model**             | Schema design patterns (embedding vs referencing), data modeling for read-heavy vs write-heavy |
| **Indexing**                   | Single field, compound, multikey, text, geospatial, TTL. `explain()`                           |
| **Aggregation Pipeline**       | `$match`, `$group`, `$lookup`, `$unwind`, `$project`, `$facet`. Performance considerations     |
| **Replication**                | Replica sets, elections, read preferences, write concerns, oplog                               |
| **Sharding**                   | Shard key selection (cardinality, frequency, monotonicity), chunks, balancer, zone sharding    |
| **Transactions**               | Multi-document transactions (4.0+), distributed transactions, performance implications         |
| **When MongoDB vs PostgreSQL** | Honest trade-offs, not "NoSQL is always faster"                                                |

---

### 3.3 — Redis

| Chủ đề                | Độ sâu                                                                                                                                  |
| --------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| **Data Structures**   | String, List, Set, Sorted Set, Hash, Stream, Bitmap, HyperLogLog, Geospatial                                                            |
| **Use Cases**         | Caching (cache-aside, write-through, write-behind), session store, rate limiting, leaderboards, pub/sub, distributed locks, task queues |
| **Persistence**       | RDB vs AOF vs hybrid. Trade-offs                                                                                                        |
| **Cluster**           | Hash slots (16384), resharding, failover, Redis Sentinel                                                                                |
| **Performance**       | Single-threaded model (I/O event loop), pipelining, Lua scripting (atomic operations)                                                   |
| **Advanced Patterns** | Distributed lock (Redlock algorithm — and its controversy), Bloom filter module, Redis Streams vs Kafka                                 |

---

### 3.4 — ORM & Query Builders

| Tool        | Kiến thức                                                                                       |
| ----------- | ----------------------------------------------------------------------------------------------- |
| **Prisma**  | Schema definition, migrations, type safety, query optimization, connection pooling, raw queries |
| **TypeORM** | Active Record vs Data Mapper patterns, entity relations, migrations, query builder              |
| **Knex.js** | Query builder, migrations, seed files. Khi nào query builder vs ORM                             |
| **Raw SQL** | Khi nào nên viết raw SQL, prepared statements, SQL injection prevention                         |

---

### 3.5 — Data Patterns

| Pattern                 | Giải thích                                                                                   |
| ----------------------- | -------------------------------------------------------------------------------------------- |
| **Connection Pooling**  | PgBouncer, pool size calculation (connections = (core_count \* 2) + effective_spindle_count) |
| **Read Replicas**       | Read/write splitting, eventual consistency, replication lag                                  |
| **CQRS**                | Command Query Responsibility Segregation — khi nào cần, khi nào overkill                     |
| **Event Sourcing**      | Store events thay vì current state, event replay, snapshots                                  |
| **Database Migrations** | Blue/green deployments, backward-compatible migrations, zero-downtime schema changes         |

---

## Phase 4 — API Design & Communication

### 4.1 — RESTful API Design

| Chủ đề                | Độ sâu                                                                                                     |
| --------------------- | ---------------------------------------------------------------------------------------------------------- |
| **REST Principles**   | Stateless, resource-based, HATEOAS (thực tế ít dùng nhưng cần biết lý thuyết), uniform interface           |
| **URL Design**        | Resource naming conventions, nested resources, query parameters, pagination (cursor-based vs offset-based) |
| **HTTP Status Codes** | Sử dụng đúng: 200, 201, 204, 301, 302, 304, 400, 401, 403, 404, 409, 422, 429, 500, 502, 503, 504          |
| **Versioning**        | URL path vs header vs query param versioning. Trade-offs                                                   |
| **Error Handling**    | Consistent error response format, error codes, RFC 7807 (Problem Details)                                  |
| **Pagination**        | Cursor-based (preferred) vs Offset-based. Keyset pagination. Trade-offs                                    |
| **Rate Limiting**     | Token bucket, leaky bucket, sliding window, fixed window. `429 Too Many Requests`                          |
| **Idempotency**       | Idempotency keys, safe vs unsafe methods, retry strategies                                                 |

---

### 4.2 — GraphQL

| Chủ đề                   | Độ sâu                                                                            |
| ------------------------ | --------------------------------------------------------------------------------- |
| **Core Concepts**        | Schema, types, queries, mutations, subscriptions                                  |
| **Resolvers**            | N+1 problem → DataLoader pattern                                                  |
| **Performance**          | Query complexity analysis, depth limiting, field-level caching, persisted queries |
| **Federation**           | Apollo Federation, schema stitching, subgraphs                                    |
| **When REST vs GraphQL** | Honest trade-offs, not "GraphQL replaces REST"                                    |

---

### 4.3 — gRPC

| Chủ đề               | Độ sâu                                                                |
| -------------------- | --------------------------------------------------------------------- |
| **Protocol Buffers** | Schema definition, data serialization, backward/forward compatibility |
| **Streaming**        | 4 types: Unary, Server streaming, Client streaming, Bidirectional     |
| **Load Balancing**   | Client-side vs proxy-based, xDS protocol                              |
| **Error Handling**   | gRPC status codes, deadline propagation, retries                      |

---

### 4.4 — Message Queues & Event-Driven

| Technology                | Kiến thức                                                                                                                                     |
| ------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **RabbitMQ**              | AMQP protocol, exchanges (direct, topic, fanout, headers), queues, bindings, acknowledgments, dead letter exchanges, prefetch                 |
| **Apache Kafka**          | Partitions, consumer groups, offsets, exactly-once semantics, log compaction, retention, ISR (In-Sync Replicas), Kafka Streams, Kafka Connect |
| **AWS SQS/SNS**           | Standard vs FIFO queues, fan-out pattern, DLQ                                                                                                 |
| **Event-Driven Patterns** | Event notification, event-carried state transfer, event sourcing, CQRS, Saga pattern (choreography vs orchestration)                          |

**Câu hỏi phỏng vấn**:

- Kafka đảm bảo thứ tự messages thế nào? Partition strategy?
- At-least-once vs at-most-once vs exactly-once delivery — giải thích chi tiết. Tại sao exactly-once "khó thật sự"?
- Saga pattern: Choreography vs Orchestration — trade-offs?

---

## Phase 5 — System Design & Architecture

> 🎯 **Đây là phần quyết định Senior vs Junior trong phỏng vấn Big Tech**.

### 5.1 — Distributed Systems Fundamentals

| Chủ đề                       | Kiến thức cần đạt                                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------------------------------- |
| **CAP Theorem**              | Consistency vs Availability vs Partition Tolerance. CP vs AP systems. PACELC theorem                  |
| **Consistency Models**       | Strong consistency, eventual consistency, causal consistency, linearizability, sequential consistency |
| **Distributed Consensus**    | Paxos (lý thuyết), Raft (implementation friendly), leader election                                    |
| **Clock & Ordering**         | Logical clocks (Lamport timestamps), Vector clocks, Hybrid Logical Clocks (HLC)                       |
| **Failure Modes**            | Byzantine failures, crash-stop, network partitions, split brain                                       |
| **Distributed Transactions** | 2PC (Two-Phase Commit), 3PC, Saga pattern                                                             |

---

### 5.2 — Design Building Blocks

| Component              | Must-know                                                                                                                    |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **Load Balancer**      | L4 vs L7, algorithms (Round Robin, Weighted, Least Connections, IP Hash, Consistent Hashing), health checks, sticky sessions |
| **Reverse Proxy**      | Nginx, HAProxy, SSL termination, request routing, caching                                                                    |
| **CDN**                | Edge caching, cache invalidation, pull vs push CDN, geographic routing                                                       |
| **DNS**                | DNS-based load balancing, GeoDNS, DNS failover                                                                               |
| **Cache**              | Cache-aside, write-through, write-behind, read-through. Cache invalidation strategies. Thundering herd. Cache stampede       |
| **Rate Limiter**       | Token bucket, sliding window log, sliding window counter. Distributed rate limiting                                          |
| **API Gateway**        | Request routing, authentication, rate limiting, request/response transformation, circuit breaker                             |
| **Service Discovery**  | Client-side vs Server-side. Consul, etcd, ZooKeeper                                                                          |
| **Message Queue**      | Async processing, load leveling, fan-out                                                                                     |
| **Search Engine**      | Elasticsearch: inverted index, analyzers, shards, replicas, relevance scoring                                                |
| **Object Storage**     | S3-like storage, pre-signed URLs, multipart upload                                                                           |
| **Consistent Hashing** | Virtual nodes, data redistribution khi add/remove nodes                                                                      |
| **Bloom Filter**       | Probabilistic data structure, false positive rate, use cases                                                                 |

---

### 5.3 — Architecture Patterns

| Pattern                          | Khi nào dùng                                                                               |
| -------------------------------- | ------------------------------------------------------------------------------------------ |
| **Monolith**                     | Small team, new product, rapid prototyping. "Modular monolith" approach                    |
| **Microservices**                | Scale teams independently, technology heterogeneity, independent deployments. Conway's Law |
| **Event-Driven**                 | Loose coupling, async processing, event sourcing                                           |
| **CQRS**                         | Different read/write loads, complex domain logic                                           |
| **Serverless**                   | Event-driven, unpredictable traffic, cost optimization. Cold start problem                 |
| **Hexagonal (Ports & Adapters)** | Testability, swappable dependencies                                                        |
| **Domain-Driven Design**         | Complex business logic, bounded contexts, ubiquitous language, aggregates, domain events   |

---

### 5.4 — System Design Interview Practice

**Must-practice designs** (mỗi bài phải design được trong 35-45 phút):

| System                            | Key Concepts                                                                    |
| --------------------------------- | ------------------------------------------------------------------------------- |
| **URL Shortener**                 | Hashing, Base62 encoding, read-heavy, cache, analytics                          |
| **Twitter/Feed**                  | Fan-out on write vs fan-out on read, timeline service, celebrity problem        |
| **Chat System**                   | WebSocket, presence service, message ordering, offline support                  |
| **YouTube/Netflix**               | Video upload pipeline, transcoding, CDN, adaptive bitrate streaming             |
| **Uber/Ride Sharing**             | Geospatial indexing (QuadTree, Geohash), matching algorithm, real-time tracking |
| **Search Engine**                 | Crawling, indexing, ranking, inverted index, PageRank concept                   |
| **Notification System**           | Push vs Pull, priority queues, rate limiting, template engine                   |
| **Rate Limiter**                  | Token bucket, distributed implementation                                        |
| **Web Crawler**                   | Politeness, BFS/DFS, URL frontier, dedup, robots.txt                            |
| **Distributed Cache**             | Consistent hashing, replication, eviction policies                              |
| **Payment System**                | Idempotency, double-entry bookkeeping, reconciliation, PCI compliance           |
| **E-commerce**                    | Inventory management (distributed locking), order processing, payment flow      |
| **File Storage (Dropbox/GDrive)** | Chunking, dedup, sync conflict resolution, metadata service                     |
| **Monitoring System**             | Time-series DB, alerting, dashboards, log aggregation                           |

**Tài nguyên**:

- _System Design Interview_ — Alex Xu (Vol 1 & 2)
- _Designing Data-Intensive Applications_ — Martin Kleppmann (**KINH THÁNH** của System Design)
- ByteByteGo (YouTube channel)
- Gaurav Sen (YouTube)

---

### 5.5 — Scalability Concepts

| Concept                             | Kiến thức                                                                                                 |
| ----------------------------------- | --------------------------------------------------------------------------------------------------------- |
| **Horizontal vs Vertical Scaling**  | Khi nào dùng loại nào, stateless services, shared-nothing architecture                                    |
| **Database Scaling**                | Replication, partitioning (hash vs range), sharding strategies, denormalization, materialized views       |
| **Caching Strategies**              | Multi-level caching (browser → CDN → API Gateway → Application → Database), invalidation                  |
| **Async Processing**                | Task queues, background jobs, event-driven architecture                                                   |
| **Resilience Patterns**             | Circuit breaker, retry (exponential backoff + jitter), timeout, bulkhead, fallback                        |
| **Observability**                   | Logging (structured logs, ELK), metrics (Prometheus + Grafana), tracing (OpenTelemetry, Jaeger), alerting |
| **Back-of-the-envelope Estimation** | Powers of 2, latency numbers every programmer should know, QPS estimation, storage estimation             |

---

## Phase 6 — DevOps, Cloud & Infrastructure

### 6.1 — Containers & Orchestration

| Chủ đề           | Độ sâu                                                                                                                                                                                                      |
| ---------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Docker**       | Dockerfile best practices, multi-stage builds, layer caching, security (non-root user, minimal base image), Docker Compose, networking (bridge, host, overlay)                                              |
| **Kubernetes**   | Pods, Services (ClusterIP, NodePort, LoadBalancer), Deployments, ReplicaSets, ConfigMaps, Secrets, Ingress, Namespaces, RBAC, HPA (Horizontal Pod Autoscaler), PVC, StatefulSets, DaemonSets, Jobs/CronJobs |
| **Helm**         | Charts, values, templates, releases                                                                                                                                                                         |
| **Service Mesh** | Istio/Linkerd: sidecar pattern, mTLS, traffic management, circuit breaking                                                                                                                                  |

---

### 6.2 — CI/CD

| Chủ đề                    | Kiến thức                                                    |
| ------------------------- | ------------------------------------------------------------ |
| **Pipeline Design**       | Build → Test → Security Scan → Deploy (staging → production) |
| **Tools**                 | GitHub Actions, GitLab CI, Jenkins, CircleCI                 |
| **Deployment Strategies** | Rolling update, Blue/Green, Canary, A/B testing              |
| **GitOps**                | ArgoCD, Flux, declarative infrastructure                     |
| **Feature Flags**         | LaunchDarkly, Unleash. Trunk-based development               |

---

### 6.3 — Cloud Services (AWS focus)

| Service        | Kiến thức                                                                                     |
| -------------- | --------------------------------------------------------------------------------------------- |
| **Compute**    | EC2 (instance types, auto-scaling), Lambda (cold start, concurrency), ECS/Fargate, EKS        |
| **Storage**    | S3 (storage classes, lifecycle policies), EBS, EFS                                            |
| **Database**   | RDS (Multi-AZ, read replicas), DynamoDB (partition key design, GSI, LSI), ElastiCache, Aurora |
| **Networking** | VPC (subnets, security groups, NACLs, NAT Gateway, VPN, Direct Connect), Route 53, CloudFront |
| **Messaging**  | SQS, SNS, EventBridge, Kinesis                                                                |
| **Monitoring** | CloudWatch, X-Ray, CloudTrail                                                                 |
| **IAM**        | Policies, Roles, cross-account access, least privilege principle                              |

---

### 6.4 — Infrastructure as Code

| Tool          | Kiến thức                                                                                   |
| ------------- | ------------------------------------------------------------------------------------------- |
| **Terraform** | HCL, providers, state management, modules, workspaces, remote state (S3 + DynamoDB locking) |
| **AWS CDK**   | TypeScript constructs, L1/L2/L3 constructs, stacks, app                                     |

---

## Phase 7 — Security

### 7.1 — Application Security

| Chủ đề             | Kiến thức                                                                                                                                                                                          |
| ------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **OWASP Top 10**   | SQL Injection, XSS, CSRF, SSRF, Broken Auth, Sensitive Data Exposure, Broken Access Control, Security Misconfiguration, Insecure Deserialization, Insufficient Logging                             |
| **Authentication** | Password hashing (bcrypt, scrypt, Argon2 — tại sao không MD5/SHA), salt, pepper. OAuth 2.0 flows (Authorization Code, PKCE, Client Credentials), OpenID Connect. Session-based vs Token-based auth |
| **Authorization**  | RBAC, ABAC, ACL, Policy-based (OPA). Row-level security                                                                                                                                            |
| **JWT**            | Structure (Header.Payload.Signature), signing algorithms (HS256 vs RS256), access token vs refresh token, token rotation, revocation strategies, JWT pitfalls                                      |
| **API Security**   | Rate limiting, input validation (Joi, Zod), CORS configuration, Helmet.js, HTTPS enforcement, API keys vs OAuth                                                                                    |
| **Data Security**  | Encryption at rest, encryption in transit, key management (KMS), PII handling, GDPR/CCPA basics                                                                                                    |
| **Supply Chain**   | Dependency scanning, lockfile integrity, signed commits, SBOM                                                                                                                                      |

---

### 7.2 — Infrastructure Security

| Chủ đề                 | Kiến thức                                                                                       |
| ---------------------- | ----------------------------------------------------------------------------------------------- |
| **Network Security**   | Firewall rules, VPN, private subnets, bastion hosts                                             |
| **Secrets Management** | HashiCorp Vault, AWS Secrets Manager, environment variables best practices (don't commit .env!) |
| **Container Security** | Image scanning, non-root users, read-only filesystems, Seccomp, AppArmor                        |

---

## Phase 8 — Testing & Quality

### 8.1 — Testing Strategy

| Layer                   | Tools & Techniques                                                                                                                                                                             |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Unit Testing**        | Jest/Vitest. AAA pattern (Arrange-Act-Assert). Mocking (jest.mock, manual mocks, dependency injection). Code coverage (line, branch, function, statement) — nhưng biết rằng coverage ≠ quality |
| **Integration Testing** | Supertest (HTTP), testcontainers (database), test database setup/teardown                                                                                                                      |
| **E2E Testing**         | Playwright, Cypress — cho API và flow testing                                                                                                                                                  |
| **Load Testing**        | Artillery, k6, autocannon. Define SLAs, test breaking points                                                                                                                                   |
| **Contract Testing**    | Pact — consumer-driven contract testing cho microservices                                                                                                                                      |
| **Chaos Engineering**   | Gremlin, Chaos Monkey concepts. Game days                                                                                                                                                      |

---

### 8.2 — Code Quality

| Chủ đề               | Tools                                                                                                                      |
| -------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| **Linting**          | ESLint (custom rules), Prettier                                                                                            |
| **Type Safety**      | TypeScript strict mode, utility types, generics, conditional types, mapped types                                           |
| **Design Patterns**  | Factory, Strategy, Observer, Decorator, Adapter, Repository, Dependency Injection, Singleton (và tại sao nó controversial) |
| **SOLID Principles** | Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion                       |
| **Clean Code**       | Meaningful names, small functions, DRY vs WET, YAGNI, KISS                                                                 |
| **Code Review**      | Cách review hiệu quả, cách nhận review, constructive feedback                                                              |

---

## Phase 9 — Soft Skills & Interview Prep

### 9.1 — Behavioral Interview (STAR Method)

| Chủ đề                  | Chuẩn bị                                                                            |
| ----------------------- | ----------------------------------------------------------------------------------- |
| **Leadership**          | Dẫn dắt project, mentor junior developers. "Tell me about a time you led a project" |
| **Conflict Resolution** | Disagreement với teammate, trade-off decisions                                      |
| **Failure**             | Incident response, postmortem, lessons learned                                      |
| **Impact**              | Measurable results, performance improvements, cost savings                          |
| **Communication**       | Present technical concepts to non-technical stakeholders                            |
| **Growth Mindset**      | Learning new technologies, adapting to change                                       |

---

### 9.2 — Technical Interview Framework

```
┌─────────────────────────────────────────────────────────┐
│                  Technical Interview                     │
│                                                         │
│  Round 1: Coding (DSA)          45-60 min               │
│  ├── 1-2 medium/hard problems                           │
│  ├── Think aloud, communicate approach                  │
│  └── Optimize: brute force → optimal                    │
│                                                         │
│  Round 2: System Design          45-60 min              │
│  ├── Requirements gathering (functional + non-func.)    │
│  ├── High-level design → deep dive components           │
│  ├── Data model, API design                             │
│  └── Scalability, reliability, monitoring               │
│                                                         │
│  Round 3: Domain Deep Dive       45-60 min              │
│  ├── Node.js internals, performance tuning              │
│  ├── Database design, optimization                      │
│  ├── Past project deep dive                             │
│  └── Architecture decisions and trade-offs              │
│                                                         │
│  Round 4: Behavioral              45-60 min             │
│  ├── STAR method stories                                │
│  ├── Leadership & mentorship                            │
│  └── Culture fit                                        │
│                                                         │
│  Round 5 (possible): Bar Raiser / Cross-functional      │
│  ├── Mixed technical + behavioral                       │
│  └── Culture and collaboration assessment               │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

---

### 9.3 — Senior-Level Expectations

**Bạn cần demonstrate được**:

| Skill                  | Biểu hiện                                                                     |
| ---------------------- | ----------------------------------------------------------------------------- |
| **Technical Depth**    | Giải thích từ high-level xuống byte-level bất kỳ concept nào trong stack      |
| **Technical Breadth**  | Biết trade-offs giữa các lựa chọn, không chỉ biết 1 cách duy nhất             |
| **System Thinking**    | Nhìn bức tranh toàn cảnh, hiểu impact của mỗi thay đổi                        |
| **Trade-off Analysis** | Không nói "X tốt hơn Y" mà nói "X tốt hơn Y trong context Z vì..."            |
| **Mentorship**         | Kinh nghiệm giúp đỡ, dạy junior/mid                                           |
| **Ownership**          | End-to-end ownership, không chỉ code mà cả monitoring, on-call, documentation |
| **Communication**      | RFC/Design Doc writing, presenting to stakeholders                            |

---

## 📚 Tài Nguyên Tổng Hợp (Theo Thứ Tự Ưu Tiên)

### Sách Bắt Buộc (Must-Read)

| #   | Sách                                                       | Tại sao                                         |
| --- | ---------------------------------------------------------- | ----------------------------------------------- |
| 1   | _Designing Data-Intensive Applications_ — Martin Kleppmann | **Kinh thánh System Design**. Đọc ít nhất 2 lần |
| 2   | _System Design Interview_ Vol 1 & 2 — Alex Xu              | Framework cho system design interviews          |
| 3   | _Node.js Design Patterns_ — Mario Casciaro                 | Patterns chuyên sâu cho Node.js                 |
| 4   | _You Don't Know JS_ (book series) — Kyle Simpson           | JS từ gốc rễ                                    |
| 5   | _Clean Code_ + _Clean Architecture_ — Robert C. Martin     | Code quality & architecture                     |
| 6   | _Introduction to Algorithms_ (CLRS)                        | Reference cho algorithms                        |
| 7   | _Database Internals_ — Alex Petrov                         | Hiểu databases từ engine level                  |
| 8   | _Web Scalability for Startup Engineers_ — Artur Ejsmont    | Practical scalability                           |

### Online Courses

| Course                               | Platform                                               |
| ------------------------------------ | ------------------------------------------------------ |
| CS50 (CS foundations)                | edX / Harvard (miễn phí)                               |
| Algorithms Part I & II               | Coursera / Princeton (miễn phí audit)                  |
| NeetCode 150/300                     | neetcode.io                                            |
| Hussein Nasser — Backend Engineering | YouTube (miễn phí)                                     |
| Node.js — The Complete Guide         | Udemy — Maximilian Schwarzmüller                       |
| System Design Primer                 | github.com/donnemartin/system-design-primer (miễn phí) |

---

## 🗓️ Timeline Tổng Quan (18-24 Tháng)

```
Month 1-4:   ┃ Phase 0: CS Fundamentals + DSA (bắt đầu LeetCode song song)
             ┃ Phase 1: JavaScript Mastery
             ┃
Month 5-7:   ┃ Phase 2: Node.js Deep Dive
             ┃ Phase 3: Database (bắt đầu)
             ┃ LeetCode: tiếp tục hàng ngày (2-3 bài/ngày)
             ┃
Month 8-10:  ┃ Phase 3: Database (hoàn thiện)
             ┃ Phase 4: API Design
             ┃ Bắt đầu side projects
             ┃
Month 11-14: ┃ Phase 5: System Design (❗ giai đoạn QUAN TRỌNG NHẤT)
             ┃ Phase 6: DevOps & Cloud
             ┃ Đọc DDIA
             ┃
Month 15-17: ┃ Phase 7: Security
             ┃ Phase 8: Testing
             ┃ System Design practice (mock interviews)
             ┃
Month 18-24: ┃ Phase 9: Interview Prep chuyên sâu
             ┃ Mock interviews (Pramp, interviewing.io)
             ┃ LeetCode contest hàng tuần
             ┃ System Design mock 2-3 lần/tuần
             ┃ Behavioral stories preparation
             ┃
             ▼ 🎯 SẴN SÀNG PHỎNG VẤN
```

---

## 🏗️ Side Projects Gợi Ý

> Build real projects để demonstrate skills. Mỗi project nên có **README chuyên nghiệp**, **tests**, **CI/CD**, **Docker**, và **documentation**.

| Project                        | Skills Demonstrated                                                        |
| ------------------------------ | -------------------------------------------------------------------------- |
| **Real-time Chat Application** | WebSocket, Redis pub/sub, message queuing, authentication, database design |
| **URL Shortener at Scale**     | Distributed system design, caching, analytics, rate limiting               |
| **E-commerce Backend**         | Payment integration, inventory management, order processing, microservices |
| **Task Queue System**          | Job scheduling, retry logic, dead letter queues, monitoring                |
| **API Gateway**                | Reverse proxy, authentication, rate limiting, request transformation       |
| **Blog Platform with CMS**     | CRUD, rich text, media upload, search (Elasticsearch), caching             |

---

## ⚡ Daily Routine Gợi Ý

```
┌──────────────────────────────────────────────────┐
│  6:00 - 7:30   LeetCode (2-3 bài)               │
│  7:30 - 8:00   Review giải thuật đã giải hôm qua │
│  8:00 - 12:00  Học theory (xem video/đọc sách)   │
│  13:00 - 17:00 Code practice / Side project       │
│  20:00 - 21:00 System Design (đọc/practice)       │
│  21:00 - 21:30 Review notes / Spaced repetition   │
│                                                   │
│  Weekend:                                         │
│  - LeetCode contests (Saturday/Sunday)            │
│  - System Design mock interview                   │
│  - Deep reading (DDIA, etc.)                      │
└──────────────────────────────────────────────────┘
```

---

## 🎯 Checklist Từng Phase

### Phase 0 Checklist

- [ ] Hiểu binary, memory, CPU operation
- [ ] Nắm vững OS: process, thread, IPC, scheduling
- [ ] Master 15+ data structures
- [ ] Master 10+ algorithm categories
- [ ] Giải 400+ LeetCode (150 Easy, 200 Medium, 50+ Hard)
- [ ] Hiểu networking: TCP/IP, HTTP, DNS, TLS

### Phase 1 Checklist

- [ ] Giải thích được V8 engine pipeline
- [ ] Vẽ và giải thích Event Loop chi tiết
- [ ] Master closures, prototypes, `this`
- [ ] Implement Promise from scratch
- [ ] Hiểu ES Modules vs CommonJS sâu

### Phase 2 Checklist

- [ ] Giải thích Node.js architecture từ C++ lên JS
- [ ] Master Streams & backpressure
- [ ] Biết khi nào dùng Worker Threads vs Cluster
- [ ] Debug memory leaks proficiently
- [ ] Profile & optimize Node.js performance

### Phase 3 Checklist

- [ ] Viết complex SQL (Window Functions, CTEs)
- [ ] Design normalized/denormalized schemas
- [ ] Đọc EXPLAIN ANALYZE thành thạo
- [ ] Hiểu MVCC, isolation levels
- [ ] Master Redis data structures & use cases
- [ ] Biết trade-offs SQL vs NoSQL

### Phase 4 Checklist

- [ ] Design RESTful APIs theo best practices
- [ ] Hiểu GraphQL N+1 problem & DataLoader
- [ ] Implement messaging patterns (pub/sub, queue)
- [ ] Biết khi nào REST vs GraphQL vs gRPC

### Phase 5 Checklist

- [ ] Design 10+ systems (35-45 min each)
- [ ] Explain CAP theorem với examples
- [ ] Master caching, load balancing, rate limiting
- [ ] Back-of-envelope estimation thành thạo
- [ ] Đọc xong DDIA ít nhất 1 lần

### Phase 6 Checklist

- [ ] Viết production Dockerfile
- [ ] Deploy app trên Kubernetes
- [ ] Setup CI/CD pipeline
- [ ] Dùng Terraform cho IaC
- [ ] Hiểu core AWS services

### Phase 7 Checklist

- [ ] Biết OWASP Top 10 và cách phòng tránh
- [ ] Implement auth (JWT, OAuth 2.0) correctly
- [ ] Secure API endpoints
- [ ] Handle secrets properly

### Phase 8 Checklist

- [ ] Viết unit tests với coverage > 80%
- [ ] Integration tests với real database
- [ ] Load testing baseline
- [ ] TypeScript strict mode project

### Phase 9 Checklist

- [ ] 10+ STAR stories prepared
- [ ] 50+ mock coding interviews
- [ ] 20+ mock system design interviews
- [ ] Resume optimized
- [ ] Portfolio site / GitHub profile polished

---

> 💡 **Lời khuyên cuối**: Đừng cố nhớ tất cả. Hãy **hiểu tại sao**, rồi bạn có thể **suy luận** ra câu trả lời cho bất kỳ câu hỏi nào. Senior engineer không phải người biết mọi thứ, mà là người **hiểu đủ sâu để giải quyết vấn đề chưa từng gặp**.
>
> Mỗi khi học một concept, hãy tự hỏi: _"Nếu interviewer hỏi follow-up, tôi có thể đi sâu thêm 3 tầng nữa không?"_ Nếu không, bạn chưa hiểu đủ.
