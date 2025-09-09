# Tuần 7 --- Production & Scaling

## Ngày 43 --- Observability (Logging, Metrics, Tracing)

### 🎯 Mục tiêu

-   Chuẩn hóa log, thêm metrics & trace end-to-end. \### 📚 Học lý
    thuyết
-   Structured logging (JSON), correlation id/trace id.\
-   Micrometer metrics (counter, gauge, timer, histogram).\
-   OpenTelemetry traces; sampling; baggage. \### 💻 Thực hành

1)  Thêm **correlation id** filter cho toàn API; log JSON.\
2)  Expose **/actuator/prometheus**; vẽ dashboard Grafana (RPS, p95,
    error%).\
3)  Thêm tracing với OpenTelemetry SDK (exporter OTLP).
    -   **Tiêu chí**: thấy được trace qua các service, dashboard hoạt
        động. \### 🧮 Bài tập DSA

-   "Subarray Sum Equals K" (prefix sum).\
-   "Binary Tree Right Side View" (BFS). \### 📦 Deliverables
-   `ObservabilityConfig.java`, `grafana/dashboards.json`,
    "Tracing-Notes.md".

------------------------------------------------------------------------

## Ngày 44 --- CI/CD Pipelines (Build, Test, Docker, Deploy)

### 🎯 Mục tiêu

-   Thiết lập pipeline tự động hóa build--test--scan--package--deploy.
    \### 📚 Học lý thuyết
-   GitHub Actions (hoặc Jenkins): jobs, caching, matrix build.\
-   Security scans (dependency check), secrets management. \### 💻 Thực
    hành

1)  Workflow: PR → build + unit test + coverage badge.\
2)  Build Docker image (multi-stage) + push registry.\
3)  Deploy staging (kubectl or helm) sau khi test pass.
    -   **Tiêu chí**: pipeline xanh từ PR đến deploy; artifacts
        versioned. \### 🧮 Bài tập DSA

-   "Evaluate Reverse Polish Notation" (stack).\
-   "Merge k Sorted Lists" (heap). \### 📦 Deliverables
-   `.github/workflows/ci.yml`, `.github/workflows/cd.yml`,
    "CICD-Runbook.md".

------------------------------------------------------------------------

## Ngày 45 --- Docker & Containerization

### 🎯 Mục tiêu

-   Viết Dockerfile tối ưu & bảo mật; tối thiểu kích thước, nhanh
    startup. \### 📚 Học lý thuyết
-   Multi-stage build; JLink/JDK slim; distroless images.\
-   Non-root user, read-only FS; healthcheck. \### 💻 Thực hành

1)  Dockerfile multi-stage + **Jib** (tuỳ chọn).\
2)  Giảm size image ≥ 50%; chạy bằng non-root.\
3)  Healthcheck + graceful shutdown (SIGTERM).
    -   **Tiêu chí**: image nhỏ, scan không có CVE nghiêm trọng. \### 🧮
        Bài tập DSA

-   "Daily Temperatures" (monotonic stack).\
-   "Number of Islands" (BFS/DFS). \### 📦 Deliverables
-   `Dockerfile`, `jib.gradle`/`pom.xml`, "Docker-BestPractices.md".

------------------------------------------------------------------------

## Ngày 46 --- Kubernetes Basics (Deploy, Service, Config, Probes)

### 🎯 Mục tiêu

-   Triển khai app lên K8s với readiness/liveness; config/secret riêng.
    \### 📚 Học lý thuyết
-   Deployment, Service, Ingress, HPA.\
-   ConfigMap vs Secret; probes; resources requests/limits. \### 💻 Thực
    hành

1)  Manifests: `deployment.yaml`, `service.yaml`, `ingress.yaml`.\
2)  Thêm **readiness/liveness probes**, **HPA** theo CPU/requests.\
3)  Mount config/secret an toàn.
    -   **Tiêu chí**: rollout không downtime; autoscale hoạt động. \###
        🧮 Bài tập DSA

-   "K Closest Points to Origin" (heap).\
-   "Course Schedule" (topo). \### 📦 Deliverables
-   `k8s/` manifests, `helm/` (tuỳ chọn), "K8s-Runbook.md".

------------------------------------------------------------------------

## Ngày 47 --- Cloud Services (AWS/GCP) Integration

### 🎯 Mục tiêu

-   Tích hợp object storage, pub/sub hoặc queue & secret manager. \###
    📚 Học lý thuyết
-   AWS: S3, SQS/SNS, Parameter Store/Secrets Manager.\
-   GCP: Cloud Storage, Pub/Sub, Secret Manager. \### 💻 Thực hành

1)  Upload/download file đến S3/Cloud Storage (localstack giả lập).\
2)  Gửi/nhận message qua SQS/PubSub (lib tương ứng).
    -   **Tiêu chí**: code cấu hình an toàn; retry + backoff. \### 🧮
        Bài tập DSA

-   "Longest Increasing Subsequence" (DP).\
-   "Design File System" (tree & hashmap). \### 📦 Deliverables
-   `cloud/StorageService.java`, `cloud/QueueClient.java`,
    "Cloud-Notes.md".

------------------------------------------------------------------------

## Ngày 48 --- Performance Testing (k6/JMeter) & Tuning

### 🎯 Mục tiêu

-   Viết test tải, theo dõi p95/p99; xác định bottleneck & tối ưu. \###
    📚 Học lý thuyết
-   Workload modeling; soak vs spike; think time; ramping VUs.\
-   Connection pool tuning, G1 params, JVM flags. \### 💻 Thực hành

1)  Viết k6 script cho 3 endpoints nóng; đặt mục tiêu p95 \< 120ms.\
2)  Tối ưu connection pool (Hikari), batch, cache; đo lại.
    -   **Tiêu chí**: báo cáo "trước/sau", đạt mục tiêu hoặc giải thích.
        \### 🧮 Bài tập DSA

-   "Longest Subarray with Sum K" (hashmap).\
-   "Top K Frequent Words" (heap + hashmap). \### 📦 Deliverables
-   `k6/perf_test.js`, "Performance-Tuning-Report.md".

------------------------------------------------------------------------

## Ngày 49 --- Tổng kết Tuần 7 --- Mini Project "Prod-Ready Order API"

### 🎯 Mục tiêu

-   Đưa Order API lên trạng thái production-ready với observability +
    CI/CD + K8s. \### 📚 Học lý thuyết
-   Review tuần 7: logging/metrics/tracing, CI/CD, container, k8s,
    cloud, perf. \### 💻 Thực hành --- Mini Project
-   Triển khai Order API với full observability, pipeline CI/CD,
    manifests K8s, HPA, secrets, health.\
-   Test tải với k6 & dashboards.\
-   **Tiêu chí**: deploy xanh, p95 đạt mục tiêu, dashboards đầy đủ. \###
    🧮 Assessment
-   20 câu quiz (devops/ops).\
-   1 bài DSA medium (Merge k Sorted Lists).\
-   1 tự luận: "Chiến lược rollback & feature flags trên K8s?" \### 📦
    Deliverables
-   `week7/` full source + manifests + workflows + `README.md`,
    "Week7-Retrospective.md".
