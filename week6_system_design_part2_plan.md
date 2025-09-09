# Tuần 6 --- System Design (Phần 2)

## Ngày 36 --- REST API Design (Idempotency, Pagination, Versioning, Validation)

### 🎯 Mục tiêu

-   Thiết kế API rõ ràng, idempotent; pagination & filtering ổn định;
    versioning chiến lược. \### 📚 Học lý thuyết
-   Idempotency keys cho POST (tạo tài nguyên).\
-   Cursor-based vs offset-based pagination; sorting stable; filtering
    an toàn.\
-   Versioning: URI vs header; backward compatibility; deprecation
    policy.\
-   Validation & error model (problem+json). \### 💻 Thực hành

1)  Thiết kế & code `Payments API` với **idempotency key** (header).\
2)  Áp dụng **cursor pagination** cho `GET /transactions`.\
3)  Bean Validation (JSR-380) + error response chuẩn hóa.
    -   **Tiêu chí**: post-idempotent; pagination ổn định; test contract
        (Spring REST Docs). \### 🧮 Bài tập DSA

-   "Design Rate Limiter" (concept).\
-   "Validate Binary Search Tree" (invariants). \### 📦 Deliverables
-   `payments/` module, `IdempotencyInterceptor.java`,
    `ApiErrorHandler.java`, "API-Design-Notes.md".

------------------------------------------------------------------------

## Ngày 37 --- API Gateway & Load Balancing (Rate Limit, Circuit Breaker)

### 🎯 Mục tiêu

-   Dùng **Spring Cloud Gateway** (hoặc Nginx) để route, limit,
    circuit-breaker. \### 📚 Học lý thuyết
-   L7 routing, canary, header-based routing.\
-   Rate limiting (token bucket, leaky bucket), distributed counters.\
-   Circuit breaker (resilience4j), bulkhead, timeout, retry with
    jitter. \### 💻 Thực hành

1)  Gateway route `api/*` đến các service; thêm **rate limit** per API
    key.\
2)  **Circuit breaker** cho downstream chậm; fallback response.\
3)  Canary: 90/10 routing (demo).
    -   **Tiêu chí**: test integration chứng minh limit & fallback hoạt
        động. \### 🧮 Bài tập DSA

-   "Network Delay Time" (Dijkstra).\
-   "Course Schedule II" (topo sort). \### 📦 Deliverables
-   `gateway/` config, `RateLimitFilter.java`, `CBConfig.java`,
    "Gateway-Runbook.md".

------------------------------------------------------------------------

## Ngày 38 --- Microservices vs Monolith (Sagas, Boundaries, Data Ownership)

### 🎯 Mục tiêu

-   Biết cách **tách monolith** hợp lý; thiết kế ranh giới (bounded
    context) & luồng Sagas. \### 📚 Học lý thuyết
-   Bounded Context (DDD); shared kernel anti-pattern.\
-   Sagas: orchestrator vs choreography; failure & compensation.\
-   Data ownership & anti-corruption layer. \### 💻 Thực hành

1)  Tách **Order** khỏi Monolith thành service riêng; API hợp đồng &
    schema events.\
2)  Thiết kế **saga**: tạo đơn → trừ tồn kho → thanh toán → xác
    nhận/compensate.
    -   **Tiêu chí**: event flow rõ; thử nghiệm case fail giữa chừng.
        \### 🧮 Bài tập DSA

-   "Reorganize String" (greedy/heap).\
-   "Minimum Window Substring" (sliding window). \### 📦 Deliverables
-   `order-service/` + "MigrationPlan.md", "Saga-Design.md".

------------------------------------------------------------------------

## Ngày 39 --- Scalability Patterns (Stateless, Horizontal Scale, Caching Layers)

### 🎯 Mục tiêu

-   Xây dựng service stateless để **scale out**; cân nhắc session,
    shared state. \### 📚 Học lý thuyết
-   Stateless vs stateful; sticky sessions; externalize state
    (cache/db/queue).\
-   Batch vs streaming; fanout/fanin.\
-   Autoscaling signals (CPU, p95 latency, queue depth). \### 💻 Thực
    hành

1)  Dockerize 3 replicas của `order-service`; test **horizontal scale**
    với k6.\
2)  Thêm **read-through cache** trước DB cho hot endpoints.
    -   **Tiêu chí**: RPS tăng tuyến tính \~replicas; p95 cải thiện.
        \### 🧮 Bài tập DSA

-   "Largest Rectangle in Histogram" (stack).\
-   "Find Peak Element" (binary search). \### 📦 Deliverables
-   `docker-compose.scale.yml`, `k6/scale_test.js`, "Scaling-Notes.md".

------------------------------------------------------------------------

## Ngày 40 --- Consistency Models (Strong vs Eventual, Quorum)

### 🎯 Mục tiêu

-   Chọn consistency phù hợp theo use case; hiểu quorum reads/writes.
    \### 📚 Học lý thuyết
-   Strong/Eventual; Monotonic reads; Read-your-writes; Causal
    consistency.\
-   Quorum N/R/W; conflict resolution (LWW, vector clock -- khái niệm).
    \### 💻 Thực hành

1)  Thử nghiệm **eventual consistency**: viết vào instance A, đọc từ B
    (replica lag).\
2)  Triển khai **read-your-writes** tạm thời bằng sticky session sau
    ghi.
    -   **Tiêu chí**: minh họa được hiện tượng & cách giảm ảnh hưởng.
        \### 🧮 Bài tập DSA

-   "Find Median from Data Stream" (2 heaps).\
-   "Time Based Key-Value Store" (map + binary search). \### 📦
    Deliverables
-   `consistency/Demo.java`, "Consistency-Playbook.md".

------------------------------------------------------------------------

## Ngày 41 --- Distributed Systems Basics (Leader Election, Heartbeats, Locks)

### 🎯 Mục tiêu

-   Xây cơ chế **leader election** đơn giản; hiểu **distributed lock**.
    \### 📚 Học lý thuyết
-   Leader election: Redis `SET NX PX`, DB-based, Zookeeper/etcd
    overview.\
-   Heartbeat/lease; fencing tokens. \### 💻 Thực hành

1)  Implement **LeaderElectionService** dùng Redis `SETNX` + TTL
    (lease).\
2)  Viết **DistributedLock** wrapper với token (fencing).
    -   **Tiêu chí**: test contention 5 threads, chỉ 1 leader; lock
        không bị giữ mãi. \### 🧮 Bài tập DSA

-   "Clone Graph" (graph).\
-   "Critical Connections in a Network" (Tarjan). \### 📦 Deliverables
-   `LeaderElectionService.java`, `DistributedLock.java`,
    "DistributedBasics-Notes.md".

------------------------------------------------------------------------

## Ngày 42 --- Tổng kết Tuần 6 --- Mini Project "Social Feed Service"

### 🎯 Mục tiêu

-   Thiết kế & triển khai service **news feed** (write heavy/read heavy)
    với cache & queue. \### 📚 Học lý thuyết
-   Fanout-on-write vs fanout-on-read; push vs pull; ranking signals;
    timeline merge. \### 💻 Thực hành --- Mini Project **Social Feed
    Service**\
-   API: post, follow/unfollow, get feed (cursor pagination).\
-   Kiến trúc: Write path qua queue; Read path dùng cache (Redis) +
    fanout chiến lược.\
-   Rate limit & circuit breaker ở gateway.\
-   **Tiêu chí**: feed API p95 \< 100ms với N users giả lập; test e2e.
    \### 🧮 Assessment
-   20 câu quiz (API, gateway, microservices, consistency,
    distributed).\
-   1 bài DSA medium (Network Delay Time).\
-   1 tự luận: "Chọn fanout chiến lược khi user siêu nổi tiếng?" \### 📦
    Deliverables
-   `week6/` full source, `k6/feed_test.js`, dashboards, `README.md`,
    "Week6-Retrospective.md".
