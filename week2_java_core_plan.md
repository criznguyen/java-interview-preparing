# Tuần 2 --- Java Core Nâng Cao (tiếp) + Ôn DSA

## Ngày 8 --- Generics nâng cao & Stream Performance

### 🎯 Mục tiêu

-   Thành thạo PECS (Producer Extends, Consumer Super).
-   Hiểu type erasure & hạn chế của generics.
-   So sánh hiệu năng **Stream API** vs vòng lặp thường.

### 📚 Học lý thuyết

-   PECS nguyên tắc: `? extends` vs `? super`.
-   Type erasure: mất thông tin type lúc runtime.
-   Khi nào `Class<T>` giữ type, khi nào bị xóa.
-   Streams: overhead, boxing/unboxing, lazy eval.

### 💻 Thực hành

1.  Viết util
    `copyList(List<? super Number> dst, List<? extends Number> src)`.
    -   **Tiêu chí**: không warning unchecked, test compile-time.
2.  Benchmark `sum()` 1e6 số bằng:
    -   For-loop
    -   Stream sequential
    -   Stream parallel
    -   **Tiêu chí**: có kết quả thời gian, phân tích overhead.

### 🧮 Bài tập DSA

-   2 bài LeetCode medium: "Merge Intervals", "Group Anagrams".

### 📦 Deliverables

-   `GenericsUtils.java`, `StreamBenchmark.java`, "Generics-Notes.md".

------------------------------------------------------------------------

## Ngày 9 --- Collections nâng cao

### 🎯 Mục tiêu

-   Hiểu rõ TreeMap, LinkedHashMap, ConcurrentHashMap.
-   Tránh lỗi ConcurrentModificationException.

### 📚 Học lý thuyết

-   TreeMap vs HashMap: O(log n) vs O(1).
-   ConcurrentHashMap: segmentation, no fail-fast.
-   Fail-fast iterator trong ArrayList/HashMap.

### 💻 Thực hành

1.  Viết demo lỗi `ConcurrentModificationException` khi iterate &
    modify.
2.  So sánh tốc độ lookup 1e6 phần tử giữa HashMap & TreeMap.
    -   **Tiêu chí**: có số liệu benchmark + giải thích.

### 🧮 Bài tập DSA

-   1 bài tree traversal (Binary Tree Level Order).
-   1 bài map-set (Top K Frequent Elements).

### 📦 Deliverables

-   `CollectionsBenchmark.java`, "CollectionsPitfalls.md".

------------------------------------------------------------------------

## Ngày 10 --- Concurrency: ThreadPool Executor tuning

### 🎯 Mục tiêu

-   Hiểu cách sizing ThreadPool cho CPU-bound vs IO-bound.
-   Viết custom ThreadPoolExecutor + RejectedExecutionHandler.

### 📚 Học lý thuyết

-   Executors factory methods: newFixedThreadPool, newCachedThreadPool.
-   Queue types: LinkedBlockingQueue, SynchronousQueue.
-   Khi nào dùng CallerRunsPolicy.

### 💻 Thực hành

1.  Viết custom ThreadPoolExecutor (core=2, max=4, queue=2).
2.  Demo reject policy: log cảnh báo khi bị từ chối.
    -   **Tiêu chí**: log rõ task nào bị drop, test concurrency.

### 🧮 Bài tập DSA

-   2 bài heap/priority queue (Meeting Rooms II, Task Scheduler).

### 📦 Deliverables

-   `CustomThreadPool.java`, "ThreadPoolTuning.md".

------------------------------------------------------------------------

## Ngày 11 --- Concurrency: ForkJoinPool & Parallelism

### 🎯 Mục tiêu

-   Hiểu cơ chế work-stealing của ForkJoinPool.
-   Viết thuật toán song song đơn giản.

### 📚 Học lý thuyết

-   ForkJoinTask: RecursiveTask vs RecursiveAction.
-   Parallelism level & steal queue.
-   So sánh với ThreadPoolExecutor.

### 💻 Thực hành

1.  Viết `ParallelSumTask` tính tổng mảng lớn bằng ForkJoinPool.
    -   **Tiêu chí**: compare với sequential + parallel stream.
2.  Demo RecursiveTask: quicksort song song.

### 🧮 Bài tập DSA

-   1 bài divide & conquer (Maximum Subarray).
-   1 bài binary search phân hoạch (Find Minimum in Rotated Sorted
    Array).

### 📦 Deliverables

-   `ParallelSumTask.java`, `ParallelQuickSort.java`,
    "ForkJoinNotes.md".

------------------------------------------------------------------------

## Ngày 12 --- JVM GC Profiling

### 🎯 Mục tiêu

-   Biết dùng công cụ profile GC (VisualVM, JFR).
-   Nhận biết allocation storm & GC pause.

### 📚 Học lý thuyết

-   G1GC regions, young/old gen.
-   Latency vs throughput trade-off.
-   Tools: VisualVM, Flight Recorder.

### 💻 Thực hành

1.  Viết app tạo nhiều object ngắn hạn → quan sát GC activity.
2.  Benchmark với -XX:+UseG1GC vs -XX:+UseZGC.
    -   **Tiêu chí**: log GC pause time, so sánh.

### 🧮 Bài tập DSA

-   1 bài string handling (Longest Substring Without Repeating).

### 📦 Deliverables

-   `GcStormDemo.java`, "GC-Profiling-Notes.md".

------------------------------------------------------------------------

## Ngày 13 --- Functional Programming nâng cao

### 🎯 Mục tiêu

-   Biết pitfalls khi dùng Optional.
-   Áp dụng functional composition, higher-order function.

### 📚 Học lý thuyết

-   Optional: orElse vs orElseGet, tránh null Optional.
-   Function\<T,R\> composition (`andThen`, `compose`).
-   Method reference nâng cao.

### 💻 Thực hành

1.  Viết `Retry<T>` function wrapper (lambda) retry tối đa 3 lần.
    -   **Tiêu chí**: generic, test timeout.
2.  Viết `compose` utils kết hợp nhiều function xử lý chuỗi.

### 🧮 Bài tập DSA

-   2 bài functional-style: (Word Ladder, Subsets).

### 📦 Deliverables

-   `RetryFunction.java`, `FunctionalUtils.java`, "OptionalPitfalls.md".

------------------------------------------------------------------------

## Ngày 14 --- Tổng kết Java Core (Tuần 2)

### 🎯 Mục tiêu

-   Tích hợp kiến thức Tuần 2 vào mini project.

### 📚 Học lý thuyết

-   Review Generics, Collections, Concurrency, JVM, FP.

### 💻 Thực hành --- Mini Project

**Log Analyzer CLI** - Input: log file (GB). - Nhiệm vụ: - Parse
multi-thread (ThreadPool). - Dùng Stream API để group theo log level,
count errors. - Cache kết quả intermediate trong LRU. - Thêm option phân
tích parallel bằng ForkJoinPool. - **Tiêu chí**: - Chạy nhanh hơn
single-thread ≥ 2x. - Unit test ≥ 80% coverage. - Tài liệu README.md
giải thích kiến trúc + trade-offs.

### 🧮 Assessment

-   15 câu trắc nghiệm lý thuyết.
-   1 bài DSA (heap/map).
-   1 câu tự luận: "Trade-off giữa parallel stream vs ForkJoinPool".

### 📦 Deliverables

-   `week2/` folder (source, test, README, notes).
-   "Week2-Retrospective.md" ghi lại lesson learned.
