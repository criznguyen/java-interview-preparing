# Tuần 5 --- System Design & Database

## Ngày 29 --- Database Design (Schema, Indexing, Keys)

### 🎯 Mục tiêu

-   Thiết kế schema chuẩn và có thể mở rộng cho domain điển hình
    (User--Product--Order--Payment).
-   Chọn khóa chính (surrogate vs natural), chuẩn hóa vs phi chuẩn hóa
    hợp lý.
-   Đặt chỉ mục đúng (B-Tree, composite, partial, covering), viết naming
    convention và audit fields.

### 📚 Học lý thuyết

-   Chuẩn hóa (1NF/2NF/3NF) vs phi chuẩn hóa (materialized views,
    duplicate columns).
-   Surrogate key (UUID/sequence) vs natural key; unique constraints,
    foreign keys, on delete/update policy.
-   Index: cấu trúc B-Tree, khi nào cần composite index (prefix), index
    selectivity, covering index, partial index, expression index.
-   Soft delete vs hard delete; audit columns: `created_at`,
    `updated_at`, `deleted_at`, `version`.
-   Migrations: Flyway/Liquibase best practices (idempotent, repeatable,
    baseline).

### 💻 Thực hành

1)  Thiết kế **ERD** cho E-commerce (User, Address, Product, Inventory,
    Order, OrderItem, Payment, Refund).
    -   **Tiêu chí**: khóa, ràng buộc, mối quan hệ rõ ràng; đặt index
        hợp lý (FK, lookup thường dùng, unique).\
2)  Viết **migrations** bằng **Flyway**: tạo schema + seed tối thiểu.\
3)  Viết **query** cho các use case: top products (30 ngày), doanh thu
    theo ngày, churn user (30 ngày không mua).
    -   **Tiêu chí**: explain plan hợp lý (không seq scan nặng nếu không
        cần), index được sử dụng.

### 🧮 Bài tập DSA

-   "Design Underground System" (map/hashmap + composite key).\
-   "Range Sum Query -- Mutable" (Fenwick/Segment Tree -- hiểu khái
    niệm).

### 📦 Deliverables

-   `db/schema.sql`, `db/V1__init.sql`, `db/V2__seed.sql` (Flyway).\
-   `queries/analysis.sql`, "Schema-Design-Notes.md",
    "Indexing-Guidelines.md".

------------------------------------------------------------------------

## Ngày 30 --- Transactions & Locking (ACID, Isolation, JPA Locking)

### 🎯 Mục tiêu

-   Hiểu anomaly: dirty read, non-repeatable, phantom; mapping với
    isolation levels.
-   Nắm optimistic vs pessimistic locking trong JPA, và rollback rules
    với @Transactional.

### 📚 Học lý thuyết

-   ACID & isolation: READ COMMITTED, REPEATABLE READ, SERIALIZABLE
    (PostgreSQL).\
-   Write skew, phantom; gap locks (MySQL), predicate locks (Postgres).\
-   JPA: `@Version` (optimistic), `LockModeType.PESSIMISTIC_*`;
    propagation & rollbackFor.

### 💻 Thực hành

1)  Viết **2 threads** update cùng một Order để minh họa **lost
    update**; sửa bằng **optimistic locking** (`@Version`).\
2)  Demo **pessimistic lock** cho case đọc-sửa-ghi cạnh tranh (select
    for update).\
3)  So sánh **READ COMMITTED** vs **REPEATABLE READ** với 2 transaction
    song song (sử dụng Testcontainers + Postgres).
    -   **Tiêu chí**: test tái lập được; log thể hiện sự khác biệt.

### 🧮 Bài tập DSA

-   "Design Hit Counter" (idempotency/throttle tư duy).\
-   "Min Stack" (stack 2 ngăn -- luyện invariants).

### 📦 Deliverables

-   `TransactionDemoIT.java`, `LockingDemoIT.java`,
    "Tx-Isolation-Notes.md".

------------------------------------------------------------------------

## Ngày 31 --- Scaling Databases (Replication, Sharding, Partitioning)

### 🎯 Mục tiêu

-   Phân biệt read-replica vs multi-primary; đọc--ghi tách biệt ở app.\
-   Hiểu sharding strategies (range/hash/consistent) & routing logic.\
-   Áp dụng partitioning theo `created_at` (time-based) trong Postgres.

### 📚 Học lý thuyết

-   Read-write splitting, lag & read-your-writes (sticky/after-write
    read).\
-   Shard key lựa chọn & anti-patterns (cross-shard joins).\
-   Partitioning: list/range/hash; constraints exclusion; hot vs cold
    data.

### 💻 Thực hành

1)  Tạo **partitioned table** cho `orders` theo tháng; migration kèm
    trigger tạo partition auto.\
2)  Viết **RoutingDataSource** (read/write) + annotation `@ReadOnly` để
    route sang replica (giả lập).\
3)  Tài liệu **sharding plan** cho bảng `events` lưu khối lượng lớn.
    -   **Tiêu chí**: query latency giảm trên data lớn; test routing
        chính xác.

### 🧮 Bài tập DSA

-   "Kth Largest Element in an Array" (heap/quickselect).\
-   "Median of Data Stream" (2 heap).

### 📦 Deliverables

-   `db/V3__orders_partition.sql`, `replica/RoutingDataSource.java`,
    "Sharding-Playbook.md".

------------------------------------------------------------------------

## Ngày 32 --- Caching Strategies (Cache-aside, Write-through, TTL, Invalidation)

### 🎯 Mục tiêu

-   Chọn chiến lược cache phù hợp; tính **consistency** và
    **staleness**.\
-   Dùng Spring Cache + Redis; đo **hit rate** & latency.

### 📚 Học lý thuyết

-   Patterns: cache-aside, read-through, write-through, write-behind.\
-   TTL, TTI, stampede protection (single-flight), versioned key, cache
    invalidation.\
-   Caffeine vs Redis; near cache; cache metrics.

### 💻 Thực hành

1)  Áp dụng **cache-aside** cho `ProductService.getById` với Redis.\
2)  Thêm **versioned cache key** cho danh sách top products + **bust**
    khi có order mới.\
3)  Đo **hit/miss** bằng Micrometer; báo cáo p95 latency trước/sau.
    -   **Tiêu chí**: hit rate ≥ 70%, latency giảm đáng kể.

### 🧮 Bài tập DSA

-   "LRU Cache" (design).\
-   "LFU Cache" (nâng cao -- tùy chọn).

### 📦 Deliverables

-   `CachingConfig.java`, `ProductServiceCacheIT.java`,
    "Cache-Strategy-Notes.md".

------------------------------------------------------------------------

## Ngày 33 --- Message Queues (RabbitMQ vs Kafka) & Idempotency

### 🎯 Mục tiêu

-   Phân biệt queue vs log (Rabbit vs Kafka), exactly-once khó;
    at-least-once + idempotency.\
-   Thiết kế **outbox pattern** chống mất sự kiện.

### 📚 Học lý thuyết

-   Kafka vs RabbitMQ: ordering, fanout, throughput, delay.\
-   Delivery semantics: at-most/at-least/exactly-once (thực tế:
    at-least-once + idempotent consumer).\
-   Outbox & CDC (Debezium).

### 💻 Thực hành

1)  Tạo **OrderCreated** event (Kafka/Rabbit tuỳ chọn) từ OrderService
    (transactional outbox).\
2)  Consumer idempotent sử dụng **idempotency key** + Redis set
    (expire).\
3)  Retry + DLQ (dead-letter) cho consumer lỗi.
    -   **Tiêu chí**: không nhân đôi side-effects; có test e2e.

### 🧮 Bài tập DSA

-   "Insert Delete GetRandom O(1)" (hash + list).\
-   "Design Tic-Tac-Toe" (state & idempotency mindset).

### 📦 Deliverables

-   `outbox/OutboxTable.sql`, `producer/OrderEventPublisher.java`,
    `consumer/OrderEventConsumer.java`, "Messaging-Notes.md".

------------------------------------------------------------------------

## Ngày 34 --- Event Sourcing & CQRS (Concept → Prototype)

### 🎯 Mục tiêu

-   Hiểu sự khác biệt Event Sourcing vs CRUD truyền thống.\
-   Tạo **event store** đơn giản & rebuild read model.

### 📚 Học lý thuyết

-   Event store: append-only, version, snapshot.\
-   CQRS: write model (commands) tách read model (queries).\
-   Trade-offs: phức tạp, eventual consistency, migration khó.

### 💻 Thực hành

1)  Triển khai **Account** theo event sourcing: `AccountOpened`,
    `MoneyDeposited`, `MoneyWithdrawn`.\
2)  Build **read model** (balance per account) cập nhật async từ event
    stream.\
3)  Snapshot mỗi N events.
    -   **Tiêu chí**: rebuild state từ đầu cho ra đúng kết quả; test
        concurrency optimistic version.

### 🧮 Bài tập DSA

-   "Number of Islands" (BFS/DFS).\
-   "Accounts Merge" (DSU -- union find).

### 📦 Deliverables

-   `eventstore/AccountAggregate.java`,
    `readmodel/BalanceProjector.java`, "ES-CQRS-Notes.md".

------------------------------------------------------------------------

## Ngày 35 --- Tổng kết Tuần 5 --- Mini Project "Order Processing Service"

### 🎯 Mục tiêu

-   Tích hợp DB chuẩn + giao dịch + cache + message queue vào một
    service hoàn chỉnh.

### 📚 Học lý thuyết

-   Review: schema/indexing, locking, replication/partition, cache,
    queue, ES/CQRS (ý tưởng).

### 💻 Thực hành --- Mini Project

**Order Processing Service**\
- Chức năng: tạo đơn, cập nhật tồn kho, phát sự kiện, cache danh sách
top products.\
- Tính năng: idempotency key cho API tạo đơn, outbox pattern, read/write
splitting giả lập, partitioned orders.\
- Kiểm thử: Testcontainers cho Postgres + Redis + MQ; đo hit rate &
p95.\
- **Tiêu chí**:\
- Tính đúng & idempotent.\
- Test e2e pass (≥ 80% lines hoặc ≥ 90% critical paths).\
- Tài liệu kiến trúc + runbook.

### 🧮 Assessment

-   20 câu quiz (DB/index/locking/cache/queue).\
-   1 bài DSA medium (Kth Largest / Median of Data Stream).\
-   1 tự luận: "Chọn chiến lược cache và invalidation cho catalog thay
    đổi liên tục".

### 📦 Deliverables

-   `week5/` full source + `docker-compose.yml`, test, dashboards,
    `README.md`, "Week5-Retrospective.md".
