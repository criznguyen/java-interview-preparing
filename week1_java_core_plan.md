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
