# 📘 Algorithms & Data Structures Practice Plan (Java-focused)

Mục tiêu: nâng cấp kỹ năng **thuật toán + DSA** phục vụ interview Senior
Backend Engineer. File này gồm: - Lộ trình 4 tuần (có thể lặp lại/đẩy độ
khó). - Danh mục **pattern** + **template code Java**. - Bộ đề gợi ý
theo từng chủ đề (Easy → Medium → Hard). - Checklist, rubric tự chấm, và
mock test mẫu.

------------------------------------------------------------------------

## 🎯 Mục tiêu tổng quát

-   Ôn 15--20 **pattern** cốt lõi, thuộc **template** để tái sử dụng
    nhanh.
-   Luyện tốc độ: giải **2--3 bài/ngày** trong 60--90 phút (tối đa).
-   Ghi chú **invariants** & **edge cases** sau mỗi bài.
-   Đạt khả năng **phân tích độ phức tạp** & **trade-off** rõ ràng khi
    trình bày.

------------------------------------------------------------------------

## 🗓️ Lộ trình 4 tuần (có thể xoay vòng)

### Tuần A --- Mảng, Chuỗi, Hash, Two Pointers, Sliding Window

-   **Ngày 1:** Arrays & Prefix Sum (Two Sum, Subarray Sum = K, Product
    Except Self)
-   **Ngày 2:** Two Pointers (3Sum, Container With Most Water, Remove
    Duplicates)
-   **Ngày 3:** Sliding Window (Longest Substring w/o Repeating, Min
    Window, Anagrams)
-   **Ngày 4:** HashMap/Set Patterns (Group Anagrams, Top K Frequent,
    Ransom Note)
-   **Ngày 5:** Stack/Monotonic (Valid Parentheses, Daily Temperatures,
    Histogram)
-   **Ngày 6:** Sorting & Intervals (Merge Intervals, Non-overlapping,
    Meeting Rooms II)
-   **Ngày 7:** Mock A (2 medium + 1 easy, 90')

### Tuần B --- Linked List, Tree, BST, Heap, Binary Search

-   **Ngày 1:** Linked List (Reverse List, Merge Two Lists, Cycle I/II)
-   **Ngày 2:** Binary Search Patterns (Rotated Array, Kth in Sorted
    Matrix, Search Range)
-   **Ngày 3:** Heap/PQ (Kth Largest, Top K Frequent, Merge k Sorted
    Lists)
-   **Ngày 4:** Binary Tree Traversal (BFS/DFS, Right Side View, Level
    Order)
-   **Ngày 5:** BST (Validate BST, Kth Smallest, Lowest Common Ancestor)
-   **Ngày 6:** Tries / Prefix (Implement Trie, Word Search II -- nếu
    còn thời gian)
-   **Ngày 7:** Mock B (2 medium + 1 hard tùy sức, 90')

### Tuần C --- Graph & Shortest Paths & Topo

-   **Ngày 1:** Graph Basics (Adj list, BFS/DFS, Clone Graph)
-   **Ngày 2:** Topological Sort (Course Schedule I/II, Alien
    Dictionary\*)
-   **Ngày 3:** Shortest Path (Dijkstra, Network Delay Time, Cheapest
    Flights K stops)
-   **Ngày 4:** Union-Find (Number of Provinces, Accounts Merge,
    Redundant Connection)
-   **Ngày 5:** Grid BFS/DFS (Number of Islands, Rotten Oranges,
    Shortest Path in Binary Matrix)
-   **Ngày 6:** Backtracking (Subsets, Permutations, Combination Sum,
    N-Queens\*)
-   **Ngày 7:** Mock C (1 graph + 1 backtracking + 1 bonus)

### Tuần D --- Dynamic Programming & Bits

-   **Ngày 1:** 1D DP (Climbing Stairs, House Robber I/II, Coin Change)
-   **Ngày 2:** String DP (Edit Distance, Longest Common Subsequence,
    Palindromic Substring)
-   **Ngày 3:** Interval/Partition DP (Burst Balloons\*, Palindrome
    Partitioning)
-   **Ngày 4:** Knapsack & Variants (0/1, Unbounded; Target Sum)
-   **Ngày 5:** LIS/Greedy (LIS, Russian Doll Envelopes\*, Jump Game
    I/II)
-   **Ngày 6:** Bit Manipulation (Single Number, Hamming Weight, Missing
    Number, Bit DP\*)
-   **Ngày 7:** Mock D (2 DP medium + 1 bất kỳ)

> *Dấu * gợi ý bài nâng cao --- cân nhắc nếu còn thời gian.

------------------------------------------------------------------------

## 🧩 Patterns & Template (Java)

### 1) Two Pointers (sorted / window boundary)

``` java
int i = 0, j = nums.length - 1;
while (i < j) {
  int sum = nums[i] + nums[j];
  if (sum == target) { /* ... */ break; }
  if (sum < target) i++; else j--;
}
```

### 2) Sliding Window (variable window)

``` java
int left = 0; Map<Character,Integer> freq = new HashMap<>(); int best = 0;
for (int right = 0; right < s.length(); right++) {
  char c = s.charAt(right);
  freq.put(c, freq.getOrDefault(c,0)+1);
  while (/* window invalid */) {
    char d = s.charAt(left++);
    freq.put(d, freq.get(d)-1);
    if (freq.get(d)==0) freq.remove(d);
  }
  best = Math.max(best, right-left+1);
}
```

### 3) Prefix Sum / HashMap

``` java
int sum = 0, ans = 0; Map<Integer,Integer> seen = new HashMap<>();
seen.put(0, 1);
for (int x : nums) {
  sum += x;
  ans += seen.getOrDefault(sum - k, 0);
  seen.put(sum, seen.getOrDefault(sum, 0) + 1);
}
```

### 4) Monotonic Stack (Next Greater / Histogram)

``` java
Deque<Integer> st = new ArrayDeque<>();
for (int i = 0; i < n; i++) {
  while (!st.isEmpty() && h[st.peek()] > h[i]) {
    int idx = st.pop();
    int left = st.isEmpty() ? -1 : st.peek();
    int width = i - left - 1;
    // area = h[idx] * width
  }
  st.push(i);
}
// cleanup with i = n
```

### 5) Binary Search (on answer / predicate)

``` java
long lo = min, hi = max; // hi is feasible
while (lo < hi) {
  long mid = (lo + hi) >>> 1;
  if (can(mid)) hi = mid; else lo = mid + 1;
}
return lo;
```

### 6) BFS (graph/grid)

``` java
Queue<int[]> q = new ArrayDeque<>();
boolean[][] seen = new boolean[m][n];
q.offer(new int[]{sx, sy}); seen[sx][sy] = true;
int[] dr = {1,-1,0,0}, dc = {0,0,1,-1};
while (!q.isEmpty()) {
  int[] cur = q.poll();
  for (int k = 0; k < 4; k++) {
    int nr = cur[0]+dr[k], nc = cur[1]+dc[k];
    if (0 <= nr && nr < m && 0 <= nc && nc < n && !seen[nr][nc] && grid[nr][nc]==1) {
      seen[nr][nc] = true; q.offer(new int[]{nr,nc});
    }
  }
}
```

### 7) Dijkstra (PQ)

``` java
List<int[]>[] g = new ArrayList[n];
for (int i=0;i<n;i++) g[i]=new ArrayList<>();
// add edges: g[u].add(new int[]{v, w});
int[] dist = new int[n]; Arrays.fill(dist, Integer.MAX_VALUE);
PriorityQueue<int[]> pq = new PriorityQueue<>(Comparator.comparingInt(a -> a[1]));
dist[src] = 0; pq.offer(new int[]{src, 0});
while (!pq.isEmpty()) {
  int[] cur = pq.poll(); int u = cur[0], d = cur[1];
  if (d != dist[u]) continue;
  for (int[] e : g[u]) {
    int v = e[0], w = e[1];
    if (dist[v] > d + w) { dist[v] = d + w; pq.offer(new int[]{v, dist[v]}); }
  }
}
```

### 8) Union-Find (Disjoint Set)

``` java
class DSU {
  int[] p, r;
  DSU(int n){ p=new int[n]; r=new int[n]; for (int i=0;i<n;i++) p[i]=i; }
  int find(int x){ return p[x]==x?x:(p[x]=find(p[x])); }
  boolean union(int a,int b){
    a=find(a); b=find(b); if(a==b) return false;
    if(r[a]<r[b]){ p[a]=b; } else if(r[a]>r[b]){ p[b]=a; } else { p[b]=a; r[a]++; }
    return true;
  }
}
```

### 9) Topological Sort (Kahn's)

``` java
int[] indeg = new int[n];
List<Integer>[] g = new ArrayList[n]; for (int i=0;i<n;i++) g[i]=new ArrayList<>();
// build g & indeg
Queue<Integer> q = new ArrayDeque<>();
for (int i=0;i<n;i++) if (indeg[i]==0) q.offer(i);
List<Integer> order = new ArrayList<>();
while (!q.isEmpty()) {
  int u = q.poll(); order.add(u);
  for (int v : g[u]) if (--indeg[v]==0) q.offer(v);
}
```

### 10) DP (1D rolling)

``` java
int[] dp = new int[n+1];
for (int i = 1; i <= n; i++) {
  dp[i] = /* transition từ dp[i-1], dp[i-2], ... */;
}
return dp[n];
```

------------------------------------------------------------------------

## 📚 Bộ đề gợi ý (theo chủ đề)

> Chọn **2--3 bài/chủ đề**. Nếu mất \>25' để "mắc kẹt", xem lại
> pattern + template rồi thử lại.

-   **Arrays & Hashing:** Two Sum, Valid Anagram, Group Anagrams,
    Product Except Self, Encode/Decode Strings.
-   **Two Pointers:** Valid Palindrome, 3Sum, Trapping Rain Water\*,
    Container With Most Water.
-   **Sliding Window:** Longest Substring w/o Repeating, Min Window
    Substring\*, Permutation in String.
-   **Stack/Monotonic:** Valid Parentheses, Daily Temperatures, Largest
    Rectangle in Histogram\*.
-   **Intervals:** Merge Intervals, Insert Interval, Non-overlapping
    Intervals, Meeting Rooms II.
-   **Binary Search:** Search in Rotated Sorted Array, Kth Smallest in
    Sorted Matrix\*, Find Peak Element.
-   **Linked List:** Reverse List, Merge K Sorted Lists\*, Reorder List,
    Detect Cycle.
-   **Trees:** BFS right side view, DFS path sum, LCA BST/BT, Serialize
    & Deserialize\*.
-   **Heap/PQ:** Kth Largest, Top K Frequent Elements, Task Scheduler,
    Merge K Lists\*.
-   **Graph:** Clone Graph, Course Schedule I/II, Network Delay Time,
    Cheapest Flights K Stops\*.
-   **Union-Find:** Number of Provinces, Accounts Merge, Redundant
    Connection.
-   **DP 1D:** Climbing Stairs, House Robber I/II, Coin Change, Decode
    Ways.
-   **String DP:** Longest Palindromic Substring, Edit Distance\*,
    Longest Common Subsequence.
-   **Backtracking:** Subsets, Permutations, Combination Sum, Word
    Search\*.
-   **Greedy:** Jump Game, Erase Overlap Intervals, Partition Labels,
    Gas Station.
-   **Math/Bit:** Single Number, Missing Number, Counting Bits, Reverse
    Bits.

(\*) nâng cao.

------------------------------------------------------------------------

## 🧪 Mock Test Mẫu (90')

-   **Phần 1 (45'):** 2 bài medium: Sliding Window + Heap.\
-   **Phần 2 (30'):** 1 bài Graph/BFS hoặc Topo.\
-   **Phần 3 (15'):** Trình bày phân tích độ phức tạp + tối ưu thêm (nếu
    có).

Rubric: - Đúng thuật toán & biên (edge cases) (40%) - Độ phức tạp hợp lý
(25%) - Code sạch + đặt tên tốt + test nhỏ (25%) - Giao tiếp/giải thích
(10%)

------------------------------------------------------------------------

## ✅ Checklist theo ngày

-   [ ] Đặt **mục tiêu** pattern (vd: Sliding Window + Stack).
-   [ ] Làm **2--3 bài** (≥1 medium).
-   [ ] Viết **note**: ý tưởng, invariant, edge.
-   [ ] Đo **thời gian** và tự chấm theo rubric.
-   [ ] Cập nhật **template** nếu phát hiện tối ưu.

------------------------------------------------------------------------

## 📝 Tips trình bày trong interview

-   Bắt đầu: nhắc lại **bài toán + constraints**; hỏi về input size,
    ordered?, duplicates?, streaming?
-   Đề xuất **2--3 hướng**; chọn 1 hướng chính, phân tích độ phức tạp.
-   Viết **pseudo-code**, sau đó code; test với **3 bộ input** (min,
    normal, edge).
-   Nói to về **invariants** và **bẫy** (overflow, index out of bounds,
    null).
-   Nếu kẹt, quay lại **pattern** gần nhất và template bạn thuộc.

Chúc bạn luyện tập hiệu quả! 🚀
