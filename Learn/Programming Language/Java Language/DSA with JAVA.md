## 📦 DATA STRUCTURES

### 1. Arrays

- Declaration: `int[] arr = new int[5];`
- Initialization: `int[] arr = {1, 2, 3};`
- Loop: `for (int i : arr) {}` or `for (int i = 0; i < arr.length; i++)`

**Key Topics:** Sliding Window, Prefix Sum, Kadane's Algo, Two Pointers, Binary Search

---

### 2. Strings

- Declaration: `String s = "hello";`
- Char access: `s.charAt(i)`
- Substring: `s.substring(start, end)`
- Conversion: `s.toCharArray()`, `String.valueOf(charArray)`

**Key Topics:** Anagrams, Palindromes, Pattern Matching, Z-Algorithm, KMP

---

### 3. Linked List

- Definition:

```java
class ListNode {     
	int val;     
	ListNode next;    
	ListNode(int x) { val = x; } 
}
```

- Traversal: `while (node != null) { node = node.next; }`

**Key Topics:** Reverse, Detect Cycle, Merge, K-th Node, Linked List as Stack/Queue

---

### 4. Stack & Queue

- Stack: `Stack<Integer> stack = new Stack<>();`
- Queue: `Queue<Integer> queue = new LinkedList<>();`

**Key Topics:** Balanced Parentheses, Monotonic Stack, Sliding Window Max, BFS

---

### 5. HashMap & HashSet

- Map: `Map<Integer, Integer> map = new HashMap<>();`
- Set: `Set<Integer> set = new HashSet<>();`

**Key Topics:** Frequency Count, Two Sum, Longest Substring, Hash Collision

---

### 6. Trees & Binary Trees

- Definition:

```java
class TreeNode {     
	int val;     
	TreeNode left, right;     
	TreeNode(int x) { val = x; } 
}
```

- Traversal: Preorder, Inorder, Postorder, Level-order (BFS)

**Key Topics:** DFS, LCA, Diameter, Height, Serialize/Deserialize, BST validation

---

### 7. Heaps / Priority Queues

- Max Heap: `PriorityQueue<Integer> pq = new PriorityQueue<>(Collections.reverseOrder());`
- Min Heap: `PriorityQueue<Integer> pq = new PriorityQueue<>();`

**Key Topics:** Top K, Median, Merge K Lists, Sliding Window

---

### 8. Graphs

- Representation:

```java
List<List<Integer>> adj = new ArrayList<>(); Map<Integer, List<Integer>> graph = new HashMap<>();
```

- Traversal: DFS, BFS

**Key Topics:** Shortest Path (Dijkstra, Bellman-Ford), Union Find, Topo Sort, MST (Prim/Kruskal)

---

### 9. Tries

- TrieNode class with 26 children (for lowercase letters)

```java
class TrieNode {     
	TrieNode[] children = new TrieNode[26];     
	boolean isEnd; 
}
```

**Key Topics:** Insert/Search, Prefix Match, Word Dictionary, Ternary Search Tree

---

### 10. Segment Trees / Fenwick Trees

- Use for range queries:
    - Segment Tree: Build, Update, Query in `O(log n)`
    - Fenwick Tree (BIT): Prefix sum structure

---

### 11. Disjoint Set (Union Find)

```java
int[] parent = new int[n]; 
int find(int x) { return parent[x] == x ? x : (parent[x] = find(parent[x])); } void union(int a, int b) { parent[find(a)] = find(b); }
```

**Key Topics:** Connected Components, Kruskal’s Algorithm, Cycle Detection

---

### 12. Matrix & Grid

- 2D Array: `int[][] grid = new int[m][n];`
- Loop: `for (int i = 0; i < m; i++) for (int j = 0; j < n; j++)`

**Key Topics:** Flood Fill, Island Count, Shortest Path, DFS/BFS in matrix

---

## 🧠 ALGORITHMS

### 🔁 Recursion & Backtracking

- Key Problems: Subsets, Permutations, Sudoku Solver, N-Queens

---

### 📊 Sorting & Searching

- Built-in: `Arrays.sort(arr);`, `Collections.sort(list);`
- Custom comparator: `(a, b) -> b - a`

**Algorithms:** Merge Sort, Quick Sort, Binary Search, Counting Sort

---

### 🧮 Binary Search

- Template:

```java
int low = 0, 
high = n; 
while (low <= high) {     
	int mid = (low + high) / 2;     
	if (condition) 
		high = mid - 1;     
	else 
		low = mid + 1; 
}
```

---

### 💡 Dynamic Programming (DP)

**Types:**

- 1D DP: Fibonacci, Climb Stairs
- 2D DP: Knapsack, LCS, Matrix Path
- State Compression
- DP on Trees/Graphs

---

### 📈 Greedy

- Sort + Take Best at Every Step

**Key Problems:** Activity Selection, Jump Game, Gas Station, Huffman Coding

---

### 🔗 Sliding Window

- Two pointers with fixed or variable-size windows

**Key Problems:** Max Subarray Sum, Longest Unique Substring, Min Window Substring

---

### 🧩 Bit Manipulation

- AND `&`, OR `|`, XOR `^`, NOT `~`, Shift `<<`, `>>`

**Key Topics:** Single Number, Subsets, Power of Two, Bitmask DP

---

### 🔀 Combinatorics

- Permutations: `backtrack(nums)`
- nCr: Precompute factorials + mod inverse

---

### 📌 Topological Sort

- Kahn’s Algorithm (BFS), DFS + stack

---

### 🧮 Math + Number Theory

- GCD: `BigInteger.valueOf(a).gcd(BigInteger.valueOf(b)).intValue();`
- Primes: Sieve of Eratosthenes
- Modular Arithmetic: `%`, `(a * b) % mod`

---

## 🧰 Java Utility Classes

|Class|Description|
|---|---|
|`Arrays`|`sort`, `binarySearch`, `fill`|
|`Collections`|`sort`, `reverse`, `shuffle`|
|`Deque`|`ArrayDeque`, for BFS/sliding|
|`Map`|`HashMap`, `TreeMap`, `LinkedHashMap`|
|`Set`|`HashSet`, `TreeSet`|
|`List`|`ArrayList`, `LinkedList`|
|`Queue`|`LinkedList`, `PriorityQueue`|

---

## 🚦 LeetCode-Specific Patterns

1. Two Pointers
2. Fast & Slow Pointers
3. Sliding Window
4. Prefix Sum
5. Merge Intervals
6. Tree Recursion
7. Backtracking Template
8. Bitmask DP
9. Union-Find Applications
10. Topological Sorting
11. Dijkstra / BFS from multiple sources
12. Trie with DFS/BFS