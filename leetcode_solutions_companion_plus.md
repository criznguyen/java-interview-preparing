# LeetCode Companion --- Cách giải + Bẫy thường gặp + Test Case mẫu (Java)

> Tổng hợp theo **nhóm chủ đề**. Mỗi mục gồm: **Ý tưởng**, **Bước
> giải**, **Độ phức tạp**, **Bẫy thường gặp**, **Test case mẫu**, và
> **Code sketch (Java rút gọn)**. *Không chép đề gốc.*

------------------------------------------------------------------------

## 1) Arrays & Hashing

### Two Sum (HashMap)

**Ý tưởng:** map\<value,index\> để tìm `target - a[i]` trong O(1).\
**Bước:** duyệt a; nếu đã có `need = target-a[i]` trong map → trả kết
quả; else put(a\[i\]).\
**Độ phức tạp:** O(n) time, O(n) space.\
**Bẫy thường gặp:** - Dùng cùng 1 phần tử 2 lần (cần thứ tự put/kiểm tra
chuẩn). - Dữ liệu có duplicate → map phải lưu index đầu tiên phù hợp ngữ
nghĩa bài.\
**Test case mẫu:** - `a=[2,7,11,15], t=9 → [0,1]` (basic)\
- `a=[3,3], t=6 → [0,1]` (duplicate)\
- `a=[1,2,3], t=7 → not found` (không có đáp án)

``` java
int[] twoSum(int[] a, int t){
  Map<Integer,Integer> m = new HashMap<>();
  for(int i=0;i<a.length;i++){
    int need = t - a[i];
    if(m.containsKey(need)) return new int[]{m.get(need), i};
    m.put(a[i], i);
  }
  return new int[]{-1,-1};
}
```

### Product of Array Except Self (Prefix/Suffix)

**Ý tưởng:** nhân prefix & suffix, không dùng chia.\
**Bẫy:** overflow (dùng long nếu cần), phần tử 0 (công thức
prefix-suffix an toàn).\
**Tests:** `[1,2,3,4]→[24,12,8,6]`, `[0,1,2]→[2,0,0]`.

### Group Anagrams

**Ý tưởng:** chữ ký là mảng đếm 26 hoặc chuỗi đã sort.\
**Bẫy:** chữ hoa/thường, ký tự Unicode → cân nhắc chuẩn hóa; hiệu năng
sort khi chuỗi dài.\
**Tests:** `["eat","tea","tan","ate","nat","bat"]`.

------------------------------------------------------------------------

## 2) Two Pointers

### 3Sum (Sort + 2 con trỏ)

**Bẫy:** trùng kết quả (cần skip duplicates ở i, l, r), tràn số khi cộng
(dùng long).\
**Tests:** `[-1,0,1,2,-1,-4] → [[-1,-1,2],[-1,0,1]]`.

### Container With Most Water

**Bẫy:** di chuyển sai con trỏ (luôn co cột thấp hơn).\
**Tests:** `height=[1,8,6,2,5,4,8,3,7] → 49`.

------------------------------------------------------------------------

## 3) Sliding Window

### Longest Substring Without Repeating

**Bẫy:** không cập nhật `l = max(l,last[c]+1)`, ký tự ASCII/Unicode.\
**Tests:** `"abcabcbb"→3`, `"bbbbb"→1`, `"pwwkew"→3`.

### Minimum Window Substring

**Bẫy:** điều kiện hợp lệ (thiếu đủ ký tự hay chỉ số loại?), co cửa sổ
đến bé nhất; ký tự lặp nhiều.\
**Tests:** `s="ADOBECODEBANC", t="ABC" → "BANC"`.

------------------------------------------------------------------------

## 4) Stack / Monotonic

### Valid Parentheses

**Bẫy:** stack rỗng khi gặp đóng; còn dư mở sau cùng.\
**Tests:** `"()[]{}"→true`, `"(]"→false`, `"([)]"→false`.

### Daily Temperatures (Monotonic Decreasing)

**Bẫy:** nhầm điều kiện pop; quên xử lý phần tử chưa có ngày ấm hơn
(0).\
**Tests:** `[73,74,75,71,69,72,76,73] → [1,1,4,2,1,1,0,0]`.

### Largest Rectangle in Histogram

**Bẫy:** quên "cleanup" với chỉ số sentinel cuối; sai độ rộng
`width = i - left - 1`.\
**Tests:** `[2,1,5,6,2,3] → 10`.

------------------------------------------------------------------------

## 5) Intervals

### Merge Intervals

**Bẫy:** sort theo start; khi chồng lấn phải cập nhật
`end = max(end, cur.end)`.\
**Tests:** `[[1,3],[2,6],[8,10],[15,18]] → [[1,6],[8,10],[15,18]]`.

### Meeting Rooms II

**Bẫy:** nhầm tiêu chí heap (end time), quên pop phòng kết thúc trước
khi dùng phòng mới.\
**Tests:** `[[0,30],[5,10],[15,20]] → 2`.

------------------------------------------------------------------------

## 6) Binary Search

### Search in Rotated Sorted Array

**Bẫy:** so sánh nửa sorted: `nums[l] <= nums[mid]` để biết trái
sorted.\
**Tests:** `nums=[4,5,6,7,0,1,2], target=0 → 4`.

### Kth Smallest in Sorted Matrix (BS trên đáp án)

**Bẫy:** hàm đếm ≤ mid phải O(n) từ góc phải-trên; cẩn thận int/long.\
**Tests:** `[[1,5,9],[10,11,13],[12,13,15]], k=8 → 13`.

------------------------------------------------------------------------

## 7) Linked List

### Reverse List / Cycle Detection

**Bẫy:** mất head mới khi reverse; Floyd phải kiểm tra null trước khi
next-next.\
**Tests:** `[1,2,3,4,5] → [5,4,3,2,1]`; cycle at pos=1 → true.

### Merge K Sorted Lists (Heap)

**Bẫy:** Nút null; compare theo `val`; rò rỉ nếu không nối đúng next.\
**Tests:** `[[1,4,5],[1,3,4],[2,6]]`.

------------------------------------------------------------------------

## 8) Trees

### Level Order / Right Side View

**Bẫy:** phân mức chính xác (size queue), right view lấy phần tử cuối
mức.\
**Tests:** cây lệch trái/phải, cây rỗng.

### LCA (BST/BT)

**Bẫy:** nhầm logic BST vs BT; với BT, trả về node khi tìm thấy ở 2
nhánh.\
**Tests:** LCA cho p,q cùng nhánh và khác nhánh.

### Serialize & Deserialize

**Bẫy:** phải encode null rõ ràng; đồng bộ thứ tự duyệt.\
**Tests:** cây rỗng; cây một nhánh dài.

------------------------------------------------------------------------

## 9) Heap / Priority Queue

### Top K Frequent Elements

**Bẫy:** min-heap size k; hoặc bucket sort để O(n).\
**Tests:** `[1,1,1,2,2,3], k=2 → [1,2]`.

### Task Scheduler

**Bẫy:** áp dụng công thức
`max( (maxFreq-1)*(n+1) + countMax, tasks.length )` hoặc mô phỏng
PQ+queue.\
**Tests:** `["A","A","A","B","B","B"], n=2 → 8`.

------------------------------------------------------------------------

## 10) Graph

### Clone Graph

**Bẫy:** quên map trước khi DFS/BFS neighbor; đồ thị có cycle.\
**Tests:** 1 node; 4 node vòng kín.

### Network Delay Time (Dijkstra)

**Bẫy:** so sánh d hiện tại với dist\[u\] trước khi relax; node
unreachable → -1.\
**Tests:** đồ thị không liên thông.

### Cheapest Flights Within K Stops

**Bẫy:** dùng Bellman-Ford giới hạn k vòng; cần mảng dist tạm cho vòng.\
**Tests:** ví dụ classic với k=1, k=2 khác nhau.

------------------------------------------------------------------------

## 11) Union-Find

### Number of Provinces / Accounts Merge

**Bẫy:** path compression + union by rank; chuyển email → id.\
**Tests:** mảng disjoint và có vòng.

------------------------------------------------------------------------

## 12) Dynamic Programming

### House Robber I/II

**Bẫy:** bản II chạy 2 lần: \[0..n-2\] và \[1..n-1\].\
**Tests:** `[2,3,2] → 3`, `[1,2,3,1] → 4`.

### Coin Change

**Bẫy:** khởi tạo `INF`; tránh overflow; khi không thể trả về -1.\
**Tests:** `coins=[1,2,5], amount=11 → 3`, `amount=3, coins=[2] → -1`.

### Edit Distance

**Bẫy:** base case hàng/cột; thứ tự i,j; so sánh ký tự đúng.\
**Tests:** `"horse","ros" → 3`.

------------------------------------------------------------------------

## 13) Backtracking

### Subsets / Permutations / Combination Sum

**Bẫy:** duplicate (sort + skip), quản lý `start`/`used[]`, backtrack
đúng vị trí.\
**Tests:** `[1,2,2]` cho subsets/perms; target nhỏ/lớn.

------------------------------------------------------------------------

## 14) Greedy

### Jump Game I/II

**Bẫy:** cập nhật `farthest` trước rồi kiểm tra biên; II đếm bước khi
đến `currentEnd`.\
**Tests:** `[2,3,1,1,4] → true / 2`.

### Partition Labels

**Bẫy:** dùng vị trí cuối của ký tự; kết thúc đoạn khi `i==maxLast`.\
**Tests:** `"ababcbacadefegdehijhklij" → [9,7,8]`.

------------------------------------------------------------------------

## Phụ lục --- Code Sketch bổ sung

**Sliding Window tối thiểu (Min Window Substring)**

``` java
String minWindow(String s, String t){
  int[] need = new int[128]; for(char c: t.toCharArray()) need[c]++;
  int missing = t.length(), l = 0, bestL=0, bestLen = Integer.MAX_VALUE;
  for(int r=0; r<s.length(); r++){
    if(need[s.charAt(r)]-- > 0) missing--;
    while(missing==0){
      if(r-l+1 < bestLen){ bestLen=r-l+1; bestL=l; }
      if(++need[s.charAt(l++)] > 0) missing++;
    }
  }
  return bestLen==Integer.MAX_VALUE ? "" : s.substring(bestL, bestL+bestLen);
}
```

**Histogram (stack)**

``` java
int largestRectangleArea(int[] h){
  Deque<Integer> st=new ArrayDeque<>(); int n=h.length, ans=0;
  for(int i=0;i<=n;i++){
    int cur = (i==n?0:h[i]);
    while(!st.isEmpty() && h[st.peek()] > cur){
      int idx=st.pop();
      int left = st.isEmpty() ? -1 : st.peek();
      ans = Math.max(ans, h[idx]*(i-left-1));
    }
    st.push(i);
  }
  return ans;
}
```

**Dijkstra**

``` java
int networkDelayTime(int[][] times, int n, int k){
  List<int[]>[] g=new ArrayList[n+1];
  for(int i=1;i<=n;i++) g[i]=new ArrayList<>();
  for(int[] e: times) g[e[0]].add(new int[]{e[1], e[2]});
  int[] dist=new int[n+1]; Arrays.fill(dist, Integer.MAX_VALUE);
  PriorityQueue<int[]> pq=new PriorityQueue<>(Comparator.comparingInt(a->a[1]));
  dist[k]=0; pq.offer(new int[]{k,0});
  while(!pq.isEmpty()){
    int[] cur=pq.poll(); int u=cur[0], d=cur[1];
    if(d!=dist[u]) continue;
    for(int[] ed: g[u]){
      int v=ed[0], w=ed[1];
      if(dist[v] > d+w){ dist[v]=d+w; pq.offer(new int[]{v,dist[v]}); }
    }
  }
  int ans=0; for(int i=1;i<=n;i++){ if(dist[i]==Integer.MAX_VALUE) return -1; ans=Math.max(ans, dist[i]); }
  return ans;
}
```

------------------------------------------------------------------------

## ✅ Checklist sử dụng tài liệu

-   [ ] Chọn **1--2 chủ đề**/ngày, đọc nhanh bẫy & test case mẫu.\
-   [ ] Giải **2--3 bài**; tự thêm **edge cases** rồi test code.\
-   [ ] Ghi chú **invariants** sau mỗi bài.\
-   [ ] Định kỳ làm **mock 90'** (2 medium + 1 bonus).

Chúc bạn ôn luyện hiệu quả! 🚀
