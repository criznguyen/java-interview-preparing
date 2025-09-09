# Tuần 4 --- Spring Boot & Data

## Ngày 22 --- Spring Boot Autoconfiguration

### 🎯 Mục tiêu

-   Hiểu cách Spring Boot khởi tạo bean tự động.
-   Biết viết starter nhỏ.

### 📚 Học lý thuyết

-   @EnableAutoConfiguration, @ConditionalOnClass,
    @ConditionalOnMissingBean.
-   Cách hoạt động META-INF/spring.factories.

### 💻 Thực hành

1.  Viết custom starter "hello-spring-boot-starter".
    -   **Tiêu chí**: thêm dependency là có sẵn bean HelloService.
2.  Demo bật/tắt auto-config bằng exclude.

### 🧮 Bài tập DSA

-   1 bài hashmap nâng cao (LRU Cache).

### 📦 Deliverables

-   `hello-spring-boot-starter/`, "AutoConfigNotes.md".

------------------------------------------------------------------------

## Ngày 23 --- Spring Data JPA cơ bản

### 🎯 Mục tiêu

-   Mapping entity, CRUD repository, query method.
-   Phân biệt Paging & Sorting Repository.

### 📚 Học lý thuyết

-   @Entity, @Id, @GeneratedValue.
-   Query derivation vs @Query annotation.

### 💻 Thực hành

1.  Viết UserRepository CRUD với H2.
    -   **Tiêu chí**: chạy được test CRUD.
2.  Thêm query method findByEmailContaining.

### 🧮 Bài tập DSA

-   1 bài SQL-like (Find Duplicate Subtrees).

### 📦 Deliverables

-   `User.java`, `UserRepository.java`, `UserRepositoryTest.java`.

------------------------------------------------------------------------

## Ngày 24 --- JPA nâng cao

### 🎯 Mục tiêu

-   Tránh N+1 problem.
-   Thành thạo mapping @OneToMany, @ManyToOne.

### 📚 Học lý thuyết

-   EntityGraph, JOIN FETCH.
-   Lazy vs Eager fetch.

### 💻 Thực hành

1.  Viết Order--OrderItem mapping.
    -   **Tiêu chí**: demo N+1 khi fetch orders + items.
2.  Fix bằng JOIN FETCH + EntityGraph.

### 🧮 Bài tập DSA

-   1 bài graph traversal (Course Schedule).

### 📦 Deliverables

-   `Order.java`, `OrderItem.java`, `JpaNPlusOneDemo.java`.

------------------------------------------------------------------------

## Ngày 25 --- Spring Security cơ bản

### 🎯 Mục tiêu

-   Authentication cơ bản bằng username/password.
-   CSRF, session vs stateless.

### 📚 Học lý thuyết

-   SecurityFilterChain, AuthenticationManager.
-   PasswordEncoder.

### 💻 Thực hành

1.  Viết login form cơ bản với in-memory user.
    -   **Tiêu chí**: login success + failed đúng.
2.  Thử bật/tắt CSRF.

### 🧮 Bài tập DSA

-   1 bài stack (Valid Parentheses).

### 📦 Deliverables

-   `SecurityConfig.java`, "SpringSecurityBasics.md".

------------------------------------------------------------------------

## Ngày 26 --- Spring Security nâng cao

### 🎯 Mục tiêu

-   Triển khai JWT-based auth.
-   Biết tích hợp OAuth2 resource server.

### 📚 Học lý thuyết

-   JWT structure: header, payload, signature.
-   Stateless authentication.

### 💻 Thực hành

1.  Viết JWT auth filter (generate, validate).
    -   **Tiêu chí**: login trả token, access API bằng token.
2.  Demo OAuth2 login với GitHub.

### 🧮 Bài tập DSA

-   1 bài hashing (Longest Palindrome).

### 📦 Deliverables

-   `JwtAuthFilter.java`, `OAuth2Config.java`, "JwtNotes.md".

------------------------------------------------------------------------

## Ngày 27 --- Spring WebFlux

### 🎯 Mục tiêu

-   Hiểu reactive programming, Mono/Flux.
-   Biết khi nào nên dùng WebFlux thay MVC.

### 📚 Học lý thuyết

-   Reactive streams, backpressure.
-   Router function vs annotation.

### 💻 Thực hành

1.  Viết Product API với WebFlux.
    -   **Tiêu chí**: trả Flux`<Product>`{=html}, test với
        WebTestClient.
2.  Demo backpressure với Flux.range.

### 🧮 Bài tập DSA

-   1 bài streaming (Sliding Window Maximum).

### 📦 Deliverables

-   `ProductHandler.java`, `ProductRouter.java`, `WebFluxDemoTest.java`.

------------------------------------------------------------------------

## Ngày 28 --- Tổng kết Spring Boot & Data

### 🎯 Mục tiêu

-   Kết hợp Spring Boot, JPA, Security, Redis cache vào 1 app.

### 📚 Học lý thuyết

-   Review AutoConfig, JPA, Security, WebFlux.

### 💻 Thực hành --- Mini Project

**E-commerce API** - Features: - CRUD product, order. - Auth bằng JWT. -
Redis cache top products. - Unit test + integration test. - **Tiêu
chí**: - Test pass. - Cache hit rate \> 70%. - README mô tả kiến trúc.

### 🧮 Assessment

-   20 câu quiz Spring Boot & JPA.
-   1 bài DSA medium (Kth Smallest in BST).
-   1 câu tự luận: "Trường hợp nào nên chọn WebFlux thay MVC?".

### 📦 Deliverables

-   `week4/` folder (source, test, README).
-   "Week4-Retrospective.md".
