# 🚀 Senior Node.js Backend Developer — Study Documents

> Roadmap chi tiết từ zero → Senior Backend Developer chuyên sâu Node.js.
> Mỗi document được viết theo phong cách article/blog chuyên sâu, có sơ đồ, code examples, và câu hỏi phỏng vấn.

---

## 📖 Thứ Tự Học (Quan Trọng!)

Học tuần tự từ trên xuống. Mỗi bài xây dựng trên kiến thức bài trước.

---

### Phase 0 — Nền Tảng Computer Science

#### §0.1 — Cách Máy Tính Hoạt Động

| #   | Chủ đề                      | File                                                                                             | Prerequisite   |
| --- | --------------------------- | ------------------------------------------------------------------------------------------------ | -------------- |
| 1   | 🔢 Binary & Số học nhị phân | [0.1.1-Binary-va-So-Hoc-Nhi-Phan.md](phase-0-cs-fundamentals/0.1.1-Binary-va-So-Hoc-Nhi-Phan.md) | Không          |
| 2   | 🖥️ CPU Architecture         | [0.1.2-CPU-Architecture.md](phase-0-cs-fundamentals/0.1.2-CPU-Architecture.md)                   | §0.1.1         |
| 3   | 📦 Memory Hierarchy         | [0.1.3-Memory-Hierarchy.md](phase-0-cs-fundamentals/0.1.3-Memory-Hierarchy.md)                   | §0.1.1, §0.1.2 |
| 4   | ⚙️ OS Fundamentals          | [0.1.4-OS-Fundamentals.md](phase-0-cs-fundamentals/0.1.4-OS-Fundamentals.md)                     | §0.1.2, §0.1.3 |
| 5   | 💾 File Systems             | [0.1.5-File-Systems.md](phase-0-cs-fundamentals/0.1.5-File-Systems.md)                           | §0.1.3, §0.1.4 |
| 6   | 🔄 I/O Models               | [0.1.6-IO-Models.md](phase-0-cs-fundamentals/0.1.6-IO-Models.md)                                 | §0.1.4, §0.1.5 |

> 💡 **§0.1.6 (I/O Models)** là bài **quan trọng nhất** trong section này — nó giải thích **tại sao Node.js Event Loop hoạt động được** từ mức kernel.

---

### Phase 1 — JavaScript Mastery

> 🎯 **Hiểu JS engine-level**, không chỉ syntax. Giải thích được **tại sao** JS hoạt động như vậy.

| #   | Chủ đề                      | File                                                                                        | Prerequisite |
| --- | --------------------------- | ------------------------------------------------------------------------------------------- | ------------ |
| 1   | ⚙️ V8 Engine & Runtime      | [1.1-Engine-va-Runtime.md](phase-1-javascript-mastery/1.1-Engine-va-Runtime.md)             | §0.1         |
| 2   | 🔬 Core Language Deep Dive  | [1.2-Core-Language-Deep-Dive.md](phase-1-javascript-mastery/1.2-Core-Language-Deep-Dive.md) | §1.1         |
| 3   | ⏳ Asynchronous JavaScript  | [1.3-Asynchronous-JavaScript.md](phase-1-javascript-mastery/1.3-Asynchronous-JavaScript.md) | §1.1, §1.2   |
| 4   | 🚀 Modern JavaScript (ES6+) | [1.4-Modern-JavaScript-ES6.md](phase-1-javascript-mastery/1.4-Modern-JavaScript-ES6.md)     | §1.2         |

> 💡 **§1.3 (Async JavaScript)** bao gồm implement **Promise from scratch** — bài tập bắt buộc cho phỏng vấn Big Tech.

---

### Phase 2 — Node.js Deep Dive

> ⚙️ **Hiểu Node.js từ C++ binding lên JavaScript API** — libuv, V8 integration, và cách Node.js thực sự xử lý concurrent requests.

| #   | Chủ đề                        | File                                                                                              | Prerequisite |
| --- | ----------------------------- | ------------------------------------------------------------------------------------------------- | ------------ |
| 1   | 🏗️ Architecture & Internals   | [2.1-Architecture-va-Internals.md](phase-2-nodejs-deep-dive/2.1-Architecture-va-Internals.md)     | §1.1         |
| 2   | 📦 Core Modules               | [2.2-Core-Modules.md](phase-2-nodejs-deep-dive/2.2-Core-Modules.md)                               | §2.1         |
| 3   | 🌊 Streams Deep Dive          | [2.3-Streams-Deep-Dive.md](phase-2-nodejs-deep-dive/2.3-Streams-Deep-Dive.md)                     | §2.2         |
| 4   | 📋 Package & Module System    | [2.4-Package-va-Module-System.md](phase-2-nodejs-deep-dive/2.4-Package-va-Module-System.md)       | §1.4         |
| 5   | 🐛 Error Handling & Debugging | [2.5-Error-Handling-va-Debugging.md](phase-2-nodejs-deep-dive/2.5-Error-Handling-va-Debugging.md) | §2.1, §2.2   |
| 6   | 🏢 NestJS Framework           | [2.6-NestJS-Framework.md](phase-2-nodejs-deep-dive/2.6-NestJS-Framework.md)                       | §2.1–§2.5    |

> 💡 **§2.3 (Streams)** là kiến thức **signature** của senior Node.js — backpressure, custom Transform. **§2.6 (NestJS)** = enterprise-grade framework bắt buộc master.

---

### Phase 3 — Database & Data Layer

> 🗄️ **Master databases** từ SQL fundamentals đến internals — PostgreSQL, MongoDB, Redis, ORM patterns.

| #   | Chủ đề                  | File                                                                          | Prerequisite |
| --- | ----------------------- | ----------------------------------------------------------------------------- | ------------ |
| 1   | 🐘 PostgreSQL Deep Dive | [3.1-PostgreSQL-Deep-Dive.md](phase-3-database/3.1-PostgreSQL-Deep-Dive.md)   | §0.2         |
| 2   | 🍃 MongoDB              | [3.2-MongoDB.md](phase-3-database/3.2-MongoDB.md)                             | §3.1         |
| 3   | ⚡ Redis                | [3.3-Redis.md](phase-3-database/3.3-Redis.md)                                 | §0.3         |
| 4   | 🔧 ORM & Query Builders | [3.4-ORM-va-Query-Builders.md](phase-3-database/3.4-ORM-va-Query-Builders.md) | §3.1         |
| 5   | 📐 Data Patterns        | [3.5-Data-Patterns.md](phase-3-database/3.5-Data-Patterns.md)                 | §3.1–§3.3    |

> 💡 **§3.1 (PostgreSQL)** là bài DÀI NHẤT — từ Window Functions, MVCC đến Replication. **§3.5 (Data Patterns)** chứa CQRS, Event Sourcing — câu hỏi system design.

---

### Phase 4 — API Design & Communication

> 🌐 **Thiết kế API chuẩn production** — REST, GraphQL, gRPC, Message Queues, Event-Driven Architecture.

| #   | Chủ đề                           | File                                                                                              | Prerequisite |
| --- | -------------------------------- | ------------------------------------------------------------------------------------------------- | ------------ |
| 1   | 🔗 RESTful API Design            | [4.1-RESTful-API-Design.md](phase-4-api-design/4.1-RESTful-API-Design.md)                         | §0.3         |
| 2   | 📊 GraphQL                       | [4.2-GraphQL.md](phase-4-api-design/4.2-GraphQL.md)                                               | §4.1         |
| 3   | ⚡ gRPC                          | [4.3-gRPC.md](phase-4-api-design/4.3-gRPC.md)                                                     | §0.3         |
| 4   | 📨 Message Queues & Event-Driven | [4.4-Message-Queues-va-Event-Driven.md](phase-4-api-design/4.4-Message-Queues-va-Event-Driven.md) | §3.5         |

> 💡 **§4.1 (REST)** chứa rate limiting (4 algorithms), idempotency keys, RFC 7807 error format. **§4.4 (Message Queues)** so sánh RabbitMQ vs Kafka + Saga pattern — câu hỏi system design nâng cao.

---

### Phase 5 — System Design & Architecture

> 🏗️ **Phần quyết định Senior vs Junior** — distributed systems, design building blocks, architecture patterns, interview practice.

| #   | Chủ đề                     | File                                                                                   | Prerequisite |
| --- | -------------------------- | -------------------------------------------------------------------------------------- | ------------ |
| 1   | 🌍 Distributed Systems     | [5.1-Distributed-Systems.md](phase-5-system-design/5.1-Distributed-Systems.md)         | §3.5, §4.4   |
| 2   | 🧱 Design Building Blocks  | [5.2-Design-Building-Blocks.md](phase-5-system-design/5.2-Design-Building-Blocks.md)   | §3.3, §5.1   |
| 3   | 📐 Architecture Patterns   | [5.3-Architecture-Patterns.md](phase-5-system-design/5.3-Architecture-Patterns.md)     | §5.1         |
| 4   | 🎯 System Design Interview | [5.4-System-Design-Interview.md](phase-5-system-design/5.4-System-Design-Interview.md) | §5.1–§5.3    |
| 5   | 📈 Scalability Concepts    | [5.5-Scalability-Concepts.md](phase-5-system-design/5.5-Scalability-Concepts.md)       | §5.2         |

> 💡 **§5.4 (Interview Practice)** chứa 8 bài design (URL Shortener, Feed, Chat, Payment...) + back-of-envelope numbers. **§5.5 (Scalability)** bao gồm circuit breaker, retry patterns, observability (p99).

---

### Phase 6 — DevOps, Cloud & Infrastructure

> ☁️ **Production-ready infrastructure** — Docker, Kubernetes, CI/CD, AWS services, Terraform/CDK.

| #   | Chủ đề                        | File                                                                                    | Prerequisite |
| --- | ----------------------------- | --------------------------------------------------------------------------------------- | ------------ |
| 1   | 🐳 Containers & Orchestration | [6.1-Containers-va-Orchestration.md](phase-6-devops/6.1-Containers-va-Orchestration.md) | §2.1         |
| 2   | � CI/CD                       | [6.2-CICD.md](phase-6-devops/6.2-CICD.md)                                               | §6.1         |
| 3   | ☁️ Cloud Services (AWS)       | [6.3-Cloud-Services-AWS.md](phase-6-devops/6.3-Cloud-Services-AWS.md)                   | §5.2         |
| 4   | 📜 Infrastructure as Code     | [6.4-Infrastructure-as-Code.md](phase-6-devops/6.4-Infrastructure-as-Code.md)           | §6.3         |

> 💡 **§6.1** chứa Dockerfile multi-stage + K8s core resources (HPA, Ingress). **§6.3 (AWS)** bao gồm DynamoDB partition key design — câu hỏi phỏng vấn phổ biến.

---

### Phase 7 — Security

> 🔒 **Bảo mật ứng dụng và infrastructure** — OWASP Top 10, JWT, OAuth 2.0, container hardening, Zero Trust.

| #   | Chủ đề                     | File                                                                              | Prerequisite |
| --- | -------------------------- | --------------------------------------------------------------------------------- | ------------ |
| 1   | 🛡️ Application Security    | [7.1-Application-Security.md](phase-7-security/7.1-Application-Security.md)       | §4.1         |
| 2   | 🏰 Infrastructure Security | [7.2-Infrastructure-Security.md](phase-7-security/7.2-Infrastructure-Security.md) | §6.1, §6.3   |

> 💡 **§7.1** chứa OWASP Top 10, JWT deep dive (RS256, revocation), OAuth 2.0 + PKCE. **§7.2** bao gồm Zero Trust + container hardening.

---

### Phase 8 — Testing & Quality

> ✅ **Viết code đúng** và **viết code sạch** — testing pyramid, design patterns, SOLID, TypeScript advanced.

| #   | Chủ đề              | File                                                               | Prerequisite |
| --- | ------------------- | ------------------------------------------------------------------ | ------------ |
| 1   | 🧪 Testing Strategy | [8.1-Testing-Strategy.md](phase-8-testing/8.1-Testing-Strategy.md) | §2.5         |
| 2   | 💎 Code Quality     | [8.2-Code-Quality.md](phase-8-testing/8.2-Code-Quality.md)         | §1.4         |

> 💡 **§8.1** chứa testing pyramid, k6 load testing, Pact contract testing, chaos engineering. **§8.2** bao gồm SOLID + 7 design patterns + TypeScript advanced (generics, discriminated unions).

---

### Phase 9 — Soft Skills & Interview Prep

> 🎯 **Phần cuối cùng** — behavioral interview (STAR), technical interview framework, senior-level expectations.

| #   | Chủ đề                           | File                                                                                                | Prerequisite |
| --- | -------------------------------- | --------------------------------------------------------------------------------------------------- | ------------ |
| 1   | 🗣️ Behavioral Interview          | [9.1-Behavioral-Interview.md](phase-9-interview-prep/9.1-Behavioral-Interview.md)                   | Tất cả       |
| 2   | 🧠 Technical Interview Framework | [9.2-Technical-Interview-Framework.md](phase-9-interview-prep/9.2-Technical-Interview-Framework.md) | Tất cả       |
| 3   | 🌟 Senior-Level Expectations     | [9.3-Senior-Level-Expectations.md](phase-9-interview-prep/9.3-Senior-Level-Expectations.md)         | Tất cả       |

> 💡 **§9.1** chứa STAR method + story bank + Amazon/Google values. **§9.2** bao gồm 5-round framework + 12-week preparation plan. **§9.3** là bài quan trọng nhất — hiểu Senior = gì.

---

### �📋 Roadmap Tổng Thể

Xem [Senior-Nodejs-Backend-Roadmap.md](Senior-Nodejs-Backend-Roadmap.md) cho lộ trình đầy đủ 10 phases.

| Phase | Chủ đề                         | Trạng thái    |
| ----- | ------------------------------ | ------------- |
| 0     | Nền Tảng Computer Science      | ✅ Hoàn thành |
| 1     | JavaScript Mastery             | ✅ Hoàn thành |
| 2     | Node.js Deep Dive              | ✅ Hoàn thành |
| 3     | Database & Data Layer          | ✅ Hoàn thành |
| 4     | API Design & Communication     | ✅ Hoàn thành |
| 5     | System Design & Architecture   | ✅ Hoàn thành |
| 6     | DevOps, Cloud & Infrastructure | ✅ Hoàn thành |
| 7     | Security                       | ✅ Hoàn thành |
| 8     | Testing & Quality              | ✅ Hoàn thành |
| 9     | Soft Skills & Interview Prep   | ✅ Hoàn thành |

> 🎉 **TẤT CẢ 10 PHASES HOÀN THÀNH!** Tổng cộng **35+ study documents** bao phủ toàn bộ kiến thức cần thiết cho Senior Node.js Backend Developer.
