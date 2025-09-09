# Tuần 3 --- Spring Core

## Ngày 15 --- Spring Container

### 🎯 Mục tiêu

-   Hiểu Bean lifecycle, scope, cách Spring quản lý context.
-   Biết sử dụng @Configuration, @Bean, @ComponentScan.

### 📚 Học lý thuyết

-   Bean lifecycle: instantiation → dependency injection → init →
    destroy.
-   Bean scope: singleton, prototype, request, session.
-   Component scanning vs explicit @Bean.

### 💻 Thực hành

1.  Tạo ứng dụng Spring với @Configuration và @ComponentScan.
    -   **Tiêu chí**: bean được load từ package scan thành công.
2.  Viết custom BeanPostProcessor log lifecycle của bean.
    -   **Tiêu chí**: log rõ instantiation, initialization.

### 🧮 Bài tập DSA

-   2 bài: (Binary Search Tree validation, Serialize & Deserialize
    Binary Tree).

### 📦 Deliverables

-   `AppConfig.java`, `CustomBeanPostProcessor.java`,
    "SpringContainerNotes.md".

------------------------------------------------------------------------

## Ngày 16 --- Dependency Injection

### 🎯 Mục tiêu

-   So sánh field injection, setter injection, constructor injection.
-   Giải quyết vấn đề circular dependency.

### 📚 Học lý thuyết

-   Ưu tiên constructor injection.
-   Circular dependency: A → B → A.
-   Giải pháp: @Lazy, refactor design.

### 💻 Thực hành

1.  Demo circular dependency với 2 service.
    -   **Tiêu chí**: ứng dụng fail startup.
2.  Fix bằng constructor injection + @Lazy.
    -   **Tiêu chí**: ứng dụng chạy thành công.

### 🧮 Bài tập DSA

-   1 bài graph cycle detection (Detect Cycle in Directed Graph).

### 📦 Deliverables

-   `CircularDemo.java`, "DependencyInjectionNotes.md".

------------------------------------------------------------------------

## Ngày 17 --- Spring AOP

### 🎯 Mục tiêu

-   Hiểu aspect, advice, pointcut, proxy.
-   Biết cách dùng @Aspect để logging & security.

### 📚 Học lý thuyết

-   AOP concepts: cross-cutting concerns.
-   Proxy-based AOP: JDK Dynamic Proxy, CGLIB.
-   Advice types: before, after, around.

### 💻 Thực hành

1.  Viết LoggingAspect log thời gian thực thi method service.
    -   **Tiêu chí**: log method name + duration.
2.  Viết @SecuredAspect chặn method nếu thiếu quyền.
    -   **Tiêu chí**: test pass cho 2 case user/admin.

### 🧮 Bài tập DSA

-   1 bài string pattern (Implement strStr).

### 📦 Deliverables

-   `LoggingAspect.java`, `SecuredAspect.java`, "AOPNotes.md".

------------------------------------------------------------------------

## Ngày 18 --- Transactions

### 🎯 Mục tiêu

-   Hiểu @Transactional, propagation & isolation.
-   Thấy được các anomaly: dirty read, phantom read.

### 📚 Học lý thuyết

-   ACID trong DB.
-   Propagation: REQUIRED, REQUIRES_NEW, NESTED.
-   Isolation: READ_COMMITTED, REPEATABLE_READ, SERIALIZABLE.

### 💻 Thực hành

1.  Demo dirty read bằng 2 transaction song song.
    -   **Tiêu chí**: log kết quả khác nhau với isolation level.
2.  Viết service OrderService với @Transactional, rollback on exception.

### 🧮 Bài tập DSA

-   1 bài concurrency simulation (Dining Philosophers).

### 📦 Deliverables

-   `OrderService.java`, `TransactionDemo.java`, "TransactionNotes.md".

------------------------------------------------------------------------

## Ngày 19 --- Profiles & Environment

### 🎯 Mục tiêu

-   Quản lý config nhiều môi trường (dev/test/prod).
-   Externalized configuration.

### 📚 Học lý thuyết

-   @Profile annotation.
-   application-{profile}.yml.
-   PropertySource & Environment.

### 💻 Thực hành

1.  Tạo 2 profile dev/prod với cấu hình DB khác nhau.
    -   **Tiêu chí**: chạy dev dùng H2, prod dùng MySQL.
2.  Đọc property qua @Value và Environment.

### 🧮 Bài tập DSA

-   1 bài hashmap + config (Two Sum II).

### 📦 Deliverables

-   `application-dev.yml`, `application-prod.yml`, "ProfileNotes.md".

------------------------------------------------------------------------

## Ngày 20 --- Spring Test

### 🎯 Mục tiêu

-   Viết test với Spring Boot Test.
-   Dùng Mockito để mock bean.

### 📚 Học lý thuyết

-   @SpringBootTest vs @DataJpaTest.
-   Test context caching.
-   Mockito basics.

### 💻 Thực hành

1.  Viết integration test cho UserRepository với H2.
    -   **Tiêu chí**: CRUD chạy đúng.
2.  Viết unit test cho UserService với Mockito mock UserRepository.

### 🧮 Bài tập DSA

-   2 bài array & testable function (Valid Sudoku, Rotate Image).

### 📦 Deliverables

-   `UserRepositoryTest.java`, `UserServiceTest.java`,
    "SpringTestNotes.md".

------------------------------------------------------------------------

## Ngày 21 --- Tổng kết Spring Core

### 🎯 Mục tiêu

-   Tích hợp kiến thức Spring Core vào mini project.

### 📚 Học lý thuyết

-   Review container, DI, AOP, Transaction, Profile, Testing.

### 💻 Thực hành --- Mini Project

**Task Manager API** - REST API cho task CRUD. - Logging bằng AOP. -
Transactional service đảm bảo tính nhất quán. - 2 profile: dev (H2),
prod (Postgres). - Unit test và integration test.

-   **Tiêu chí**:
    -   API CRUD pass test.
    -   Logging aspect hoạt động.
    -   Transaction rollback đúng.
    -   Profile switch OK.

### 🧮 Assessment

-   20 câu trắc nghiệm Spring Core.
-   1 bài DSA medium (linked list cycle detection).
-   1 câu tự luận: "Tại sao constructor injection an toàn hơn field
    injection?".

### 📦 Deliverables

-   `week3/` folder với source, test, README.
-   "Week3-Retrospective.md".
