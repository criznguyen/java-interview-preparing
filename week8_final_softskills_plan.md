# Tuần 8 --- Tổng duyệt & Soft Skills

## Ngày 50 --- Coding Mock Interview (Timed)

### 🎯 Mục tiêu

-   Luyện phản xạ giải bài đúng giờ; code sạch, test nhanh. \### 📚 Học
    lý thuyết
-   Quy trình: Clarify → Plan → Complexity → Implement → Test →
    Optimize.\
-   Patterns: two pointers, sliding window, binary search, heap, prefix
    sum. \### 💻 Thực hành

1)  Làm 2 bài medium trong 90' (45' mỗi bài) trên IDE local (không tra
    cứu).\
2)  Viết test unit nhỏ cho edge cases; review code sau 10'.
    -   **Tiêu chí**: pass hết test, code rõ ràng, phân tích độ phức
        tạp. \### 🧮 Bài tập DSA

-   Đề xuất: "3Sum", "Binary Tree Zigzag Level Order Traversal". \### 📦
    Deliverables
-   `day50/` solutions + "Postmortem-Day50.md".

------------------------------------------------------------------------

## Ngày 51 --- System Design Mock: Real-time Chat

### 🎯 Mục tiêu

-   Trình bày kiến trúc end-to-end với yêu cầu & ràng buộc rõ ràng. \###
    📚 Học lý thuyết
-   Requirements: online presence, typing indicator, delivery/read
    receipts, multi-device sync.\
-   Kiến trúc: WebSocket, gateway, chat service, presence service,
    storage (NoSQL), queue, cache.\
-   Scale & consistency: partitioning rooms, ordering per room,
    backpressure. \### 💻 Thực hành

1)  Viết **Architecture Doc**: non-functional requirements (SLA, p95,
    RPS), schema, APIs, flows.\
2)  Nêu trade-offs: at-least-once + idempotency, ordering local per
    room, fanout.
    -   **Tiêu chí**: sơ đồ & luồng rõ; khả năng mở rộng & fallback
        cases. \### 🧮 Bài tập DSA

-   "Design Search Autocomplete System" (trie/heap).\
-   "Serialize and Deserialize Binary Tree" (design). \### 📦
    Deliverables
-   `day51/ChatSystem.md` (kiến trúc + diagram ASCII), "Tradeoffs.md".

------------------------------------------------------------------------

## Ngày 52 --- System Design Mock: Payment System

### 🎯 Mục tiêu

-   Thiết kế cổng thanh toán (capture/authorize, idempotency,
    reconciliation). \### 📚 Học lý thuyết
-   Flows: auth → capture → refund; ledger, double-entry.\
-   Idempotency keys, replay handling; PCI concerns (khái niệm).\
-   Anti-fraud signals (rate, velocity, device). \### 💻 Thực hành

1)  API hợp đồng cho payments; xử lý **idempotent** và **exactly-once
    effect** qua outbox.\
2)  Reconciliation job so sánh với provider logs.
    -   **Tiêu chí**: không double-charge; nhật ký khớp. \### 🧮 Bài tập
        DSA

-   "Random Pick with Weight" (prefix sums).\
-   "Find Duplicate Subtrees" (hashing + tree). \### 📦 Deliverables
-   `day52/PaymentSystem.md`, `recon/ReconciliationJob.java`,
    "Payment-Tradeoffs.md".

------------------------------------------------------------------------

## Ngày 53 --- Behavioral Interview (STAR) & Leadership

### 🎯 Mục tiêu

-   Chuẩn hóa 4--5 câu chuyện theo STAR; nhấn mạnh impact & metrics.
    \### 📚 Học lý thuyết
-   STAR: Situation, Task, Action, Result (+ Reflection).\
-   Leadership: ownership, conflict resolution, mentorship, stakeholder
    mgmt. \### 💻 Thực hành

1)  Viết 4 câu chuyện: "Fix production incident", "Lead migration",
    "Resolve conflict", "Scale 10x".\
2)  Đo lường: số liệu trước/sau; bài học rút ra.
    -   **Tiêu chí**: ngắn gọn, định lượng. \### 🧮 Bài tập DSA

-   (Tùy chọn) 1 bài nhẹ để giữ nhịp: "Two Sum II". \### 📦 Deliverables
-   `day53/STAR-Stories.md` (mỗi câu chuyện ≤ 300 từ, có metrics).

------------------------------------------------------------------------

## Ngày 54 --- Communication & Presentation (PREP, Whiteboard)

### 🎯 Mục tiêu

-   Trình bày mạch lạc, vào trọng tâm; xử lý Q&A khó. \### 📚 Học lý
    thuyết
-   PREP: Point--Reason--Example--Point; Pyramid principle.\
-   Whiteboarding & structuring answers; "I don't know, here's how I'd
    find out". \### 💻 Thực hành

1)  Trình bày 5' cho đề tài "Thiết kế Rate Limiter" + Q&A 5'.\
2)  Ghi hình & tự review (hoặc nhờ bạn góp ý).
    -   **Tiêu chí**: rõ ràng, thời lượng đúng, cấu trúc chặt. \### 🧮
        Bài tập DSA

-   "Design Twitter" (object design). \### 📦 Deliverables
-   `day54/Talk-Ratelimiter.md`, "Presentation-Checklist.md".

------------------------------------------------------------------------

## Ngày 55 --- Full Mock (45' Coding + 60' Design + 30' Behavioral)

### 🎯 Mục tiêu

-   Tổng duyệt theo format công ty sản phẩm lớn. \### 📚 Học lý thuyết
-   Checklist trước mock: env, template code, test skeleton, talking
    points. \### 💻 Thực hành
-   45' coding (1 medium + 1 easy).\
-   60' system design (dịch vụ bạn mạnh nhất).\
-   30' behavioral (3 câu chuyện).
    -   **Tiêu chí**: giữ nhịp thời gian, ghi chú self-review. \### 🧮
        Bài tập DSA
-   "Word Break" (DP).\
-   "Rotting Oranges" (BFS). \### 📦 Deliverables
-   `day55/` solutions + "FullMock-Postmortem.md".

------------------------------------------------------------------------

## Ngày 56 --- Final Revision & Logistics

### 🎯 Mục tiêu

-   Tổng hợp cheat sheets, checklist logistics; thư giãn hợp lý. \### 📚
    Học lý thuyết
-   Cheat sheet: Java, Spring, JPA, Security, System Design, Ops.\
-   Logistics: môi trường phỏng vấn, setup IDE/SDK, network, timezone.
    \### 💻 Thực hành

1)  Soạn **CheatSheet.md** (≤ 10 trang) + **Q&A bank** (≤ 3 trang).\
2)  Lập kế hoạch ngủ/nghỉ; chuẩn bị câu hỏi cho interviewer.
    -   **Tiêu chí**: checklist đầy đủ, tâm lý sẵn sàng. \### 🧮 Bài tập
        DSA

-   Nghỉ hoặc 1 easy để "đủ tay" (Two Sum). \### 📦 Deliverables
-   `day56/CheatSheet.md`, "Interview-Logistics.md",
    "Week8-Retrospective.md".
