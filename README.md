# 📌 Roadmap Ôn Luyện Senior Backend Engineer (Java + Spring Boot)

# Tuần 1 --- Java Core Nâng Cao (Day by Day Plan)

## Ngày 1 --- OOP & Design Principles

### Mục tiêu

-   Hiểu và áp dụng SOLID trong thiết kế class/service.
-   Viết class immutable, đúng equals/hashCode/toString.
-   Nhận diện và refactor code smells.

### Học lý thuyết

-   SOLID principles với ví dụ thực tế (Order, Payment).
-   Immutability và builder pattern.
-   equals/hashCode hợp đồng và pitfalls.

### Thực hành

1.  Viết class `Money` (immutable) với currency + amount.
2.  Refactor một "God Service" thành nhiều interface theo ISP.

### Bài tập DSA

-   2 bài array/hashmap mức medium.

### Deliverables

-   `Money.java`, `MoneyTest.java`, "Refactor Notes.md".

------------------------------------------------------------------------

## Ngày 2 --- Generics & Collections Internals

### Mục tiêu

-   Hiểu type erasure, wildcards, PECS.
-   Biết độ phức tạp và đặc tính ArrayList, LinkedList, HashMap,
    TreeMap, PriorityQueue.

### Học lý thuyết

-   Generics nâng cao: PECS, type erasure.
-   HashMap internals: treeify, loadFactor, fail-fast iterator.

### Thực hành

1.  Viết `LruCache<K,V>` extends LinkedHashMap với access-order.
2.  Viết API generic minh họa PECS.

### Bài tập DSA

-   2 bài heap/map mức medium.

### Deliverables

-   `LruCache.java`, `GenericsPlayground.java`.

------------------------------------------------------------------------

## Ngày 3 --- Concurrency cơ bản

### Mục tiêu

-   Nắm Java Memory Model: happens-before, visibility vs atomicity.
-   Dùng volatile, Atomic, LongAdder đúng chỗ.

### Học lý thuyết

-   Thread lifecycle, Runnable vs Callable.
-   Happens-before: lock/unlock, volatile write→read.

### Thực hành

1.  Viết Counter 3 biến thể: volatile, AtomicLong, LongAdder.
2.  Safe-publication: hot-reload config với AtomicReference.

### Bài tập DSA

-   1--2 bài queue/stack medium.

### Deliverables

-   `CounterBenchmark.java`, `HotReloadingConfig.java`,
    "ConcurrencyNotes-Day3.md".

------------------------------------------------------------------------

## Ngày 4 --- Concurrency nâng cao

### Mục tiêu

-   Chọn thread pool phù hợp.
-   Biết dùng ReentrantLock, ReadWriteLock, tránh deadlock.
-   Thành thạo CompletableFuture.

### Học lý thuyết

-   Executors: fixed, cached, work-stealing.
-   Deadlock & cách tránh.
-   CompletableFuture pipeline & error handling.

### Thực hành

1.  `UserProfileAggregator` dùng CompletableFuture (song song 3 nguồn,
    timeout).
2.  Deadlock demo và fix bằng lock ordering/tryLock.

### Bài tập DSA

-   1 bài graph BFS/DFS medium.

### Deliverables

-   `UserProfileAggregator.java`, `DeadlockDemo.java`,
    `DeadlockFixed.java`, "ThreadPoolSizing.md".

------------------------------------------------------------------------

## Ngày 5 --- JVM Internals

### Mục tiêu

-   Hiểu Heap/Stack/Metaspace, escape analysis cơ bản.
-   Nắm GC (G1, ZGC) và JIT cơ bản.
-   Tránh memory leak phổ biến.

### Học lý thuyết

-   GC: pause, throughput, latency.
-   String concat, intern, boxing/unboxing.
-   AutoCloseable & try-with-resources.

### Thực hành

1.  Viết demo memory leak (listener không remove).
2.  Benchmark string concat vs StringBuilder.

### Bài tập DSA

-   1 bài string manipulation medium.

### Deliverables

-   `LeakDemo.java`, `StringConcatBench.java`, "JVM-GC-Notes.md".

------------------------------------------------------------------------

## Ngày 6 --- Functional Style & Streams

### Mục tiêu

-   Thành thạo Stream API (map/filter/reduce).
-   Biết pitfalls: stateful lambda, boxing/unboxing.
-   Viết custom Collector.

### Học lý thuyết

-   Intermediate vs Terminal ops, laziness.
-   Collectors: groupingBy, mapping, teeing.

### Thực hành

1.  `OrderAnalytics`: top 10 sản phẩm, thống kê đa cấp.
2.  Viết custom Collector tính median/percentile.

### Bài tập DSA

-   1--2 bài sorting/grouping.

### Deliverables

-   `OrderAnalytics.java`, `PercentileCollector.java`,
    "StreamsPitfalls.md".

------------------------------------------------------------------------

## Ngày 7 --- Tổng kết Tuần 1

### Mục tiêu

-   Khóa kiến thức qua assessment + mini project.

### Assessment

-   Trắc nghiệm lý thuyết (20 câu).\
-   1 bài DSA medium.\
-   3 câu tự luận ngắn.

### Mini Project

-   Product Insights CLI: đọc JSON orders, phân tích song song, cache
    LRU, export CSV.

### Deliverables

-   `week1/` folder chứa source, test, README, notes.\
-   "Week1-Retrospective.md" báo cáo học được gì và điểm yếu cần cải
    thiện.

------------------------------------------------------------------------

# ✅ Checklist Week 1

-   [ ] Money class + equals/hashCode chuẩn\
-   [ ] LRU cache chạy đúng\
-   [ ] Counter demo (volatile vs Atomic vs LongAdder)\
-   [ ] Deadlock demo & fix\
-   [ ] Hot-reload config bằng AtomicReference\
-   [ ] Memory leak demo & fix\
-   [ ] Streams analytics + custom collector\
-   [ ] Mini project chạy OK + test pass\
-   [ ] Retrospective hoàn thành

# Tuần 2 --- Java Core Nâng Cao (tiếp) + Ôn DSA

## Ngày 8 --- Generics nâng cao & Stream Performance

-   Ôn PECS, type erasure, bounded generics.
-   Viết util generic để merge list an toàn.
-   Thực hành: benchmark stream vs for-loop.

## Ngày 9 --- Collections nâng cao

-   TreeMap vs HashMap vs ConcurrentHashMap.
-   Viết demo concurrent modification exception.
-   Bài tập DSA: tree traversal.

## Ngày 10 --- Concurrency: ThreadPool Executor tuning

-   Lý thuyết: sizing, queue types (LinkedBlockingQueue,
    SynchronousQueue).
-   Thực hành: viết custom ThreadPoolExecutor + RejectedHandler.

## Ngày 11 --- Concurrency: ForkJoinPool & Parallelism

-   Lý thuyết: divide and conquer, work stealing.
-   Thực hành: implement parallel sum với ForkJoinTask.

## Ngày 12 --- JVM GC Profiling

-   Dùng JVisualVM/Flight Recorder.
-   Thực hành: tạo app gây GC pause và phân tích.

## Ngày 13 --- Functional Programming nâng cao

-   Optional pitfalls, functional composition.
-   Viết custom higher-order function utils.

## Ngày 14 --- Tổng kết Java Core

-   Mini project: Log Analyzer CLI (multi-thread parse, Stream
    analytics, memory profiling).
-   Retrospective viết báo cáo.

------------------------------------------------------------------------

# Tuần 3 --- Spring Core

## Ngày 15 --- Spring Container

-   Bean lifecycle, scope, @Configuration, @ComponentScan.
-   Thực hành: custom BeanPostProcessor.

## Ngày 16 --- Dependency Injection

-   Field vs Constructor injection.
-   Circular dependency demo & fix.

## Ngày 17 --- Spring AOP

-   Pointcut, advice, proxy.
-   Thực hành: logging aspect + annotation-driven security.

## Ngày 18 --- Transactions

-   @Transactional propagation & isolation.
-   Demo dirty read vs repeatable read.

## Ngày 19 --- Profiles & Environment

-   Multi-profile config (dev/test/prod).
-   Externalized config (YAML, env vars).

## Ngày 20 --- Spring Test

-   JUnit 5 + Mockito basics.
-   Test context caching & pitfalls.

## Ngày 21 --- Tổng kết Spring Core

-   Mini project: Task Manager API với AOP logging, transactional
    service, profile switching.
-   Retrospective.

------------------------------------------------------------------------

# Tuần 4 --- Spring Boot & Data

## Ngày 22 --- Spring Boot Autoconfiguration

-   Hiểu @EnableAutoConfiguration, @Conditional.
-   Thực hành: viết starter nhỏ.

## Ngày 23 --- Spring Data JPA cơ bản

-   Entity mapping, query method, paging & sorting.
-   Demo CRUD với H2.

## Ngày 24 --- JPA nâng cao

-   N+1 problem và giải pháp (EntityGraph, JOIN FETCH).
-   Demo QueryDSL.

## Ngày 25 --- Spring Security cơ bản

-   Username/password, in-memory users.
-   CSRF, session vs stateless.

## Ngày 26 --- Spring Security nâng cao

-   JWT, OAuth2 resource server.
-   Demo: login + access token.

## Ngày 27 --- Spring WebFlux

-   Reactive streams, Mono/Flux.
-   Thực hành: build reactive API.

## Ngày 28 --- Tổng kết Spring Boot & Data

-   Mini project: E-commerce API (product, order, auth với JWT, cache
    Redis).
-   Retrospective.

------------------------------------------------------------------------

# Tuần 5 --- System Design & Database

## Ngày 29 --- Database Design

-   Indexing, normalization vs denormalization.
-   Demo: EXPLAIN query plans.

## Ngày 30 --- Transactions & Locking

-   Optimistic vs Pessimistic locking.
-   Demo concurrent update scenario.

## Ngày 31 --- Scaling Databases

-   Sharding, replication, partitioning.
-   Trade-off CAP theorem.

## Ngày 32 --- Caching Strategies

-   Write-through, write-behind, cache-aside.
-   Redis demo with Spring.

## Ngày 33 --- Message Queues

-   RabbitMQ vs Kafka use-cases.
-   Demo event-driven order system.

## Ngày 34 --- Event Sourcing & CQRS (concepts)

-   Lý thuyết + example code đơn giản.

## Ngày 35 --- Tổng kết Database & System Design (Part 1)

-   Mini project: Order Processing Service (JPA + Kafka + Redis cache).
-   Retrospective.

------------------------------------------------------------------------

# Tuần 6 --- System Design (Part 2)

## Ngày 36 --- REST API Design

-   Idempotency, pagination, rate limiting.

## Ngày 37 --- API Gateway & Load Balancing

-   Reverse proxy, Zuul/Spring Cloud Gateway demo.

## Ngày 38 --- Microservices vs Monolith

-   Pros/cons, communication patterns.
-   Demo: split service.

## Ngày 39 --- Scalability Patterns

-   Vertical vs Horizontal scaling.
-   Demo horizontal scaling with Docker compose.

## Ngày 40 --- Consistency Models

-   Strong vs Eventual, quorum reads/writes.
-   Demo: simulate eventual consistency.

## Ngày 41 --- Distributed Systems Basics

-   Leader election, consensus protocols overview.

## Ngày 42 --- Tổng kết System Design

-   Mini project: Social Feed Service (microservices, cache, async
    queue).
-   Retrospective.

------------------------------------------------------------------------

# Tuần 7 --- Production & Scaling

## Ngày 43 --- Observability

-   Logging, metrics, tracing.
-   Micrometer + Prometheus + Grafana demo.

## Ngày 44 --- CI/CD Pipelines

-   GitHub Actions workflow build + test + deploy.

## Ngày 45 --- Docker & Containerization

-   Dockerfile best practices.
-   Multi-stage build demo.

## Ngày 46 --- Kubernetes basics

-   Pod, Deployment, Service.
-   Demo deploy Spring Boot.

## Ngày 47 --- Cloud Services (AWS/GCP)

-   S3, EC2, Cloud Run, Pub/Sub basics.

## Ngày 48 --- Performance Testing

-   JMeter / k6 load test demo.

## Ngày 49 --- Tổng kết Production

-   Mini project: Monitoring + Deployment pipeline cho Order API.
-   Retrospective.

------------------------------------------------------------------------

# Tuần 8 --- Tổng duyệt + Soft Skills

## Ngày 50 --- Coding Mock Interview

-   2 bài LeetCode medium + review.

## Ngày 51 --- System Design Mock Interview

-   Thiết kế Chat App real-time.

## Ngày 52 --- System Design Mock Interview

-   Thiết kế Payment System.

## Ngày 53 --- Behavioral Interview Prep

-   STAR method practice.
-   3 câu chuyện project story.

## Ngày 54 --- Communication Skills

-   Trả lời ngắn gọn, structure (PREP: Point-Reason-Example-Point).

## Ngày 55 --- Mock Interview Full

-   45' coding + 60' system design + 30' behavioral.

## Ngày 56 --- Final Revision

-   Cheat sheet ôn nhanh.
-   Nghỉ ngơi + chuẩn bị tinh thần.

------------------------------------------------------------------------

# ✅ Checklist Weeks 2--8

-   [ ] Mini project mỗi tuần hoàn thành.\
-   [ ] Retrospective hàng tuần viết xong.\
-   [ ] Mock interview coding + design pass.\
-   [ ] Behavioral stories chuẩn bị rõ ràng.
