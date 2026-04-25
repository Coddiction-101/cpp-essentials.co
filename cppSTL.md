## C++ STL Overview

The **Standard Template Library (STL)** is a powerful library in C++ providing optimized implementations of commonly used data structures and algorithms. It eliminates the need to reinvent efficient code for structures like arrays, stacks, queues, lists, maps, and sets—most are pre-implemented with performance optimizations and exception handling. Developers reuse this code, saving time and ensuring reliability across positive, negative, happy, and corner cases.       

**Why use STL?** It offers efficiency, reusability, and safety. Instead of writing data structures from scratch (useful for learning), prefer STL when allowed for production code.      

STL divides into **four components**:
- **Containers**: Data structures for storing data (focus of first chapter).
- **Algorithms**: Operations on containers (e.g., sorting, searching).
- **Iterators**: Standardized way to traverse containers.
- **Functors**: Function objects (less commonly covered in detail elsewhere).

Containers are simply another name for data structures—like buckets storing specific data with unique storage/retrieval/manipulation methods (e.g., stack LIFO, queue FIFO).      

| Component | Description | Coverage Note |
|-----------|-------------|---------------|
| Containers | Data structures (vector, list, stack, queue, set, map) | Detailed here; most complete coverage |
| Algorithms | Operations on data | In-depth, beyond typical tutorials     |
| Iterators | Traversal mechanism | Separate deep session |
| Functors | Function-like objects | Often skipped elsewhere   |

## Vector: Dynamic Array Container

**Vector** is a dynamic array using contiguous memory locations to store same-type elements (e.g., all ints). Unlike static arrays (fixed size at compile-time, e.g., `int arr[5]`), vectors grow/shrink at runtime automatically.      

**How growth works**: Starts with initial capacity. When full (e.g., 4 elements), it creates a new array (typically 2x size, e.g., 8), copies old elements, and uses the new array. This enables runtime resizing without manual intervention.         

**Key advantages**:
- Fast random access (O(1) via index, like arrays).
- Linear storage for sequential data.
- Prefer over static arrays to avoid size limits.    

  

As shown above, capacity doubles on overflow (e.g., 4→8→16), but **size** tracks inserted elements only.  

## Vector Creation Methods

Include `<vector>` header. Basic syntax: `vector<int> v;`

| Method | Syntax | Effect |
|--------|--------|--------|
| Default | `vector<int> marks;` | Empty vector, size=0, capacity grows as needed    |
| Sized | `vector<int> miles(10);` | 10 blocks, uninitialized    |
| Sized + Initialized | `vector<int> distances(15, 0);` | 15 blocks, all set to 0    |

## Key Vector Member Functions

**Iterators** (pointer-like objects for safe traversal): `begin()` points to first element; `end()` to past-the-end position. Use `*it` to access value; `it++` to advance. Loop: `for(auto it = v.begin(); it!= v.end(); ++it) cout << *it;`. Full details in Iterators chapter.              



Iterators standardize traversal across containers (vector, list, set).  

| Function | Description | Example Output (for v = {10,20,30,40}) |
|----------|-------------|---------------------------------------|
| `push_back(x)` | Insert at end | v.push_back(50) → {10,20,30,40,50}     |
| `pop_back()` | Remove last | v.pop_back() → {10,20,30}    |
| `size()` | Number of elements | 4    |
| `front()` | First element | 10    |
| `back()` | Last element | 40    |
| `empty()` | True if size=0 | false      |
| `v[i]` | Access/modify at index i (no bounds check; index must exist) | v[0]=100 → changes first to 100              |
| `at(i)` | Access at i with bounds checking | v.at(0) → 10 (throws if invalid)     |
| `capacity()` | Allocated storage | 4 (doubles to 8 after push when full)        |

**Rules for []**: Vector must have size/elements; index < size. Empty vector → segfault.      

**Size vs Capacity**:
- **Size**: Inserted elements (e.g., 5).
- **Capacity**: Allocated blocks (e.g., 8 after doubling).
Print both to verify growth.  

## Practical Usage Notes

- Vectors spend most time here due to importance; others covered faster.
- 2D vectors (vector of vectors) next.
- Comparators in Functors; iterator types in Iterators chapter.      

Run code hands-on: Create, push/pop, traverse, check size/capacity to internalize.    

---

## Vector Capacity and Size Management

Vector maintains two key properties: **size** (number of elements currently stored) and **capacity** (allocated memory blocks). When elements are added via `push_back`, size increases, and capacity doubles when full to amortize reallocations—this was verified by printing size=5 and capacity=8 after insertions.    

- `reserve(n)`: Pre-allocates minimum capacity `n` without adding elements, similar to Java's `ensureCapacity`. Example: Empty vector has capacity 0; after `reserve(10)`, capacity becomes 10. Prevents frequent reallocations for known large sizes.   
- `max_size()`: System-dependent maximum size limit based on process boundaries (e.g., very large number like 4611686018427387903); varies by compiler/OS.     

  

This doubling strategy ensures average O(1) amortized insertion time.  

## Vector Modification Functions

Four core functions handle element management:

| Function | Purpose | Effect on Size | Example |
|----------|---------|----------------|---------|
| `clear()` | Removes **all** elements | Size → 0 (capacity unchanged) | Size 4 → 0 after `clear()`     |
| `insert(iterator_pos, value)` | Inserts `value` **before** `pos` | Size++ | `insert(v.begin(), 50)` adds 50 at index 0         |
| `erase(iterator_pos)` or `erase(start_iter, end_iter)` | Removes element(s) at/from range | Size decreases by removed count | `erase(v.begin(), v.end())` clears all        |
| `swap(other_vector)` | Exchanges **all** contents (size + capacity) | No change to sizes | Vector{10,11,12,13} swaps with {100,200,300,400}          |

**Mechanism**: Insert/erase use iterators for position; `begin()` points to first, `end()` to past-last. Swap is efficient—no copying.  

## Vector Traversal Methods

Three ways to iterate:

1. **Traditional for-loop**: `for(int i=0; i<v.size(); i++) cout << v[i];`   
2. **Range-based for-each loop** (C++11+): `for(int i: v) cout << i;` — reads "for each `int i` in `v`". Cleaner, no index management.        
3. **Iterator-based**: 
   ```
   vector<int>::iterator it = v.begin();
   while(it!= v.end()) {
       cout << *it;  // Dereference with *
       it++;         // Advance
   }
   ```
   Iterators act like pointers to elements; `begin()` → first, `end()` → sentinel.             

For-each is preferred for simplicity; iterators enable algorithms later.  

## 2D Vectors (Matrix Representation)

Vector of vectors simulates 2D arrays: `vector<vector<int>> arr(rows, vector<int>(cols, init_val));`

- **Uniform columns**: `vector<vector<int>> arr(5, vector<int>(4, 0));` → 5 rows, 4 columns, all initialized to 0.     
- **Row count**: `arr.size()`      
- **Column count** (assuming uniform): `arr[0].size()`     

  

**Why it works**: Outer vector stores row-vectors; each inner `vector<int>` holds column elements. Linear 1D vector → single row; nested → matrix.                                  

## Jagged 2D Vectors (Variable Columns per Row)

For non-uniform rows (jagged array):

1. Create outer: `vector<vector<int>> br(rows);`
2. Assign per row: `br[0] = vector<int>(4); br[1] = vector<int>(2);` etc.             

- Row count: `br.size()`
- Columns in row `i`: `br[i].size()`
- Total columns requires loop: `for(int i=0; i<br.size(); i++) max_cols = max(max_cols, br[i].size());`    

Handles irregular matrices efficiently.  

## Introduction to std::list (Doubly Linked List)

STL `list` implements **doubly linked list**—collection of **nodes** with non-contiguous memory. Each node: `prev` pointer, `data`, `next` pointer.   

**Advantages over array/vector**:
- Fast insertions/removals (no shifting)
- Non-contiguous: Nodes scattered (e.g., addresses 108, 216, 104), linked via pointers     

**Limitations**:
- No random access: Traverse sequentially (O(n) access vs. O(1) in vector)
- Head="first node", Tail="last node"; null prev/next at ends           

  

**Creation/Operations**:
```
#include <list>
list<int> mylist;
mylist.push_back(10);  // End insert
mylist.push_front(5);  // Front insert
mylist.pop_back();     // End remove
mylist.pop_front();    // Front remove
mylist.size();         // Element count                 
```

Push/pop front/back are O(1); simulates queue/deque behaviors. Further member functions follow vector pattern.      

**Note**: Algorithms like sort/reverse covered later in STL algorithms section.    

---

## List Container Member Functions

The `list` container in C++ Standard Template Library (STL) is a **doubly-linked list** where each node has pointers to both previous and next nodes, enabling efficient insertions and deletions from both ends (O(1) time). Unlike vectors, it doesn't use contiguous memory, so random access is O(n), but traversal with iterators is efficient.

Key operations mirror deque but work on both ends:

| Operation | Description | Example Code | Effect |
|-----------|-------------|--------------|--------|
| `push_back(value)` | Adds element at rear | `myList.push_back(20);` | List: 10 → 20 → 30   |
| `pop_back()` | Removes rear element | `myList.pop_back();` | Removes 30   |
| `push_front(value)` | Adds element at front | `myList.push_front(5);` | List: 5 → 10 → 20   |
| `pop_front()` | Removes front element | `myList.pop_front();` | Removes 5   |

- **Size check**: `myList.size()` returns number of elements (e.g., 3 after operations).  
- **Clear**: `myList.clear()` removes all elements, setting size to 0.  
- **Empty check**: `myList.empty()` returns `true` if no elements (post-clear).   

**Front/Back Access**:
- `myList.front()` returns first element (head, leftmost: 10).   
- `myList.back()` returns last element (tail, rightmost: 30).   

  

**Iterators for Traversal**:
- `begin()` points to first node (head address).   
- `end()` points to past-the-end (null after tail).  
- Traverse like vectors: `for(auto it = myList.begin(); it!= myList.end(); ++it) { cout << *it; }` prints entire list (10 20 30).     

**Remove Specific Value**: `myList.remove(value)` deletes **all occurrences** (e.g., remove(10) from [10,20,30,10] → [20,30]).    

**Swap**: `list1.swap(list2)` exchanges contents efficiently (e.g., list1=[10,20,30] ↔ list2=[100,200,300]).    

**Insert at Position**: `myList.insert(iterator_position, value)` adds before position (e.g., insert(begin(), 100) on [10,20,30] → [100,10,20,30]).   

**Erase Range**: `myList.erase(begin(), end())` deletes from start to end, emptying list (size 4 → 0).    

## Queue Container (FIFO)

**Queue** implements **First-In-First-Out (FIFO)** data structure: insertions at **rear** (back), deletions at **front**. Real-world analogy: lines at ATMs, school assembly, or free laptop distribution—new person joins rear, front person leaves first.    

  

**Header**: `#include <queue>`

| Operation | Description | Time | Example |
|-----------|-------------|------|---------|
| `push(value)` | Insert at rear | O(1) | q.push(10); → front:10   |
| `pop()` | Remove from front | O(1) | After pushes [10,20,30,40], pop() removes 10   |
| `front()` | Access front | O(1) | Returns 20 after one pop   |
| `back()` | Access rear | O(1) | Returns 40   |
| `size()` | Element count | O(1) | 4 after four pushes   |
| `empty()` | Check if empty | O(1) | false if size > 0   |
| `swap(q2)` | Exchange contents | O(1) | q1=[10,20] ↔ q2=[100,200]    |

- **No clear()**: Queues lack direct clear; use loop with pop() or reconstruct.  
- **No iterators**: Cannot use `begin()/end()` (no member). Access via repeated front()/pop().  
- **Random access**: O(n) worst-case (must pop front-to-target).  

**Why FIFO?** Ensures order: first arrival (front) served first, new arrivals (rear) wait.

## Stack Container (LIFO)

**Stack** implements **Last-In-First-Out (LIFO)**: insertions/deletions only at **top**. Analogy: wedding plates—last placed (top) picked first.     

  

**Header**: `#include <stack>`

| Operation | Description | Time | Example |
|-----------|-------------|------|---------|
| `push(value)` | Insert at top | O(1) | st.push(30); → top:30   |
| `pop()` | Remove from top | O(1) | From [10,20,30] (top=30), pop() → [10,20]   |
| `top()` | Access top | O(1) | Returns 20 post-pop   |
| `size()` | Element count | O(1) | 3 after three pushes   |
| `empty()` | Check if empty | O(1) | false if size=1   |
| `swap(s2)` | Exchange contents | O(1) | Similar to queue   |

- **No iterators**: No `begin()/end()`; access via repeated top()/pop().   
- **Used in**: Function calls, recursion (call stack).  
- **Traversal**: Only by popping (destructive).  

**Key Insight**: Stack/queue are **adapter containers** built on deque/list by default, restricting access to one/both ends for enforced FIFO/LIFO.   

## Deque (Double-Ended Queue) Teaser

**Deque** (pronounced "deck") is **Doubly-Ended Queue**: allows push/pop at **both front and rear** (all O(1)). Extends queue with bidirectional access.    (Continued in next section.)

---

## Double-Ended Queue (deque)

A **double-ended queue (deque)** extends the standard queue by allowing insertions and deletions at **both ends** (front and rear), unlike a regular queue which only pushes at rear and pops from front. This makes it ideal for **sliding window pattern** problems where efficient access to both ends is needed.    

Deque is created using the `<queue>` header:
```cpp
#include <queue>
deque<int> dq;  // Integer deque named 'dq'
```
- **push_back(10)**: Adds 10 at rear → `[10]`
- **push_back(20)**: Adds 20 at rear → `[10, 20]`
- **push_front(100)**: Adds 100 at front → `[100, 10, 20]`
- **push_front(200)**: Adds 200 at front → `[200, 100, 10, 20]`    

**Removal operations**:
- **pop_front()**: Removes from front (e.g., removes 200 → `[100, 10, 20]`)  
- **pop_back()**: Removes from rear (e.g., removes 20 → `[100, 10]`)  

| Operation | Time Complexity | Description |
|-----------|-----------------|-------------|
| push_back, push_front | O(1) amortized | Insert at rear/front |
| pop_back, pop_front | O(1) amortized | Remove from rear/front |
| size() | O(1) | Returns element count (e.g., 4)   |
| front() | O(1) | Access first element (e.g., 100)   |
| back() | O(1) | Access last element (e.g., 10)   |
| empty() | O(1) | Checks if empty   |

**Iteration and Indexing** (random access like vector):
```cpp
for(auto it = dq.begin(); it!= dq.end(); ++it) {
    cout << *it << " ";  // Prints all elements  
}
dq[0]  // Accesses first element (200)  
dq.at(2)  // Safer indexed access  
```
Other vector-like functions work identically: **insert**, **erase**, **clear**, **swap**.    


As shown above, deque maintains order while allowing flexible end operations.  

## Priority Queue

A **priority queue** serves elements based on **priority** (highest first), not insertion order. By default, it uses a **max-heap** where largest value has highest priority (like serving a minister before normal people in line).   

Include `<queue>` header:
```cpp
priority_queue<int> pq;  // Max-heap (largest at top)
```
**Key operations** (log n for push due to heapify; O(1) for top/pop):
```cpp
pq.push(10); pq.push(25); pq.push(55); pq.push(21);
// Internally: [55, 25, 10, 21] (55 at top)
cout << pq.top();  // 55 (highest priority)  
pq.pop();  // Removes 55  
cout << pq.top();  // Now 25  
pq.size();  // 3  
pq.empty(); // false  
```

| Default (max-heap) | Min-heap Creation | Behavior |
|--------------------|-------------------|----------|
| `priority_queue<int> pq;` | `priority_queue<int, vector<int>, greater<int>> pq;`   | Top pops largest/smallest |

**Min-heap example**:
```cpp
priority_queue<int, vector<int>, greater<int>> pq;
pq.push(100); pq.push(50); pq.push(75);  // Top: 50 (smallest)  
pq.pop();  // Removes 50  
```
Always pops highest priority element (max for default, min for greater comparator). No clear(), but swap() exists.  

  
**Time complexities**: push O(log n), top/pop O(1).   

## Map Containers

**Map** stores **key-value pairs** (entries) where keys are **unique**. Think of it as a table/index mapping chapters to names (e.g., key=1 → "Intro to C++"). Keys must be unique—no duplicates.    

Two types in this context:
| Type | Underlying DS | Order | Operations Time |
|------|---------------|-------|-----------------|
| **unordered_map** | Hash table/array   | Random | O(1) average   |
| **map** (ordered) | (Homework: comment what DS?)   | Sorted by key | O(log n)   |

**Creation** (include `<map>` and `<unordered_map>`):
```cpp
unordered_map<string, string> table;  // string key → string value  
```

**Insertion** (3 ways):
1. `table["IN"] = "India";`  
2. `table.insert({"EN", "England"});` or `make_pair("EN", "England")`  
3. Explicit pair: `pair<string,string> p = {"BR", "Brazil"}; table.insert(p);`  

**Access/Update**:
- `table["IN"]` or `table.at("IN")` → "India", also **updates** if assigned  
- `table.size()` → 3  
- `table.empty()`  
- `table.clear()`  

**Iteration** (entries are pairs):
```cpp
for(auto it = table.begin(); it!= table.end(); ++it) {
    pair<string,string> p = *it;
    cout << p.first << ": " << p.second << endl;  // e.g., EN: England  
}
```
Unordered_map prints in random order.  

**Erase**:
```cpp
table.erase(table.begin(), table.end());  // Clears all  
```

**Key Functions** (covered next in source): find, count—critical for key existence checks.  


Maps enable arbitrary key types (e.g., string→string), unlike arrays' integer indices.  

---

## Map Container: Find and Count Functions

The `std::map` (ordered map) and `std::unordered_map` store unique key-value pairs. The `find` function searches for a specific key and returns an **iterator** pointing to that element if found, or `map.end()` if not found. This works by linearly checking elements from `begin()` until the key matches or `end()` is reached—common sense dictates that reaching `end()` means the key doesn't exist.        

To use `find`:
- `auto it = table.find("IN");`
- `if (it!= table.end()) { /* key found */ } else { /* key not found */ }`

If the key exists (e.g., "IN" for India), `it` points to its location; dereference with `*it` to access the pair. For non-existent keys (e.g., "IM"), it equals `end()`.      

The `count` function returns the **number of elements** with the specified key. Since maps enforce unique keys, it returns either **1** (found) or **0** (not found)—never more than 1.   
- `if (table.count("IN") == 1) { /* key found */ } else { /* key not found */ }`
This mirrors `find` logic but returns a count instead of an iterator.      

| Function | Returns | Found Case | Not Found Case | Use Case |
|----------|---------|------------|----------------|----------|
| `find(key)` | Iterator | Iterator to key | `end()` | Locate and access element |
| `count(key)` | `size_t` (0 or 1) | 1 | 0 | Check existence without iterator   |

## Ordered vs Unordered Map

All operations (`insert`, `erase`, `traverse`, `find`, `count`) work identically on both `std::map` (ordered) and `std::unordered_map`. The key difference:

- **Unordered Map**: Constant time (`O(1)`) operations via hash table; traversal yields **random order**.  
- **Ordered Map** (`std::map`): Logarithmic time (`O(log n)`) via self-balancing BST (red-black tree); traversal yields **sorted order** by key (lexicographic for strings, numeric for ints).      

Example with string keys ("Brazil", "England", "India"):
```
Unordered: Random (e.g., India → Brazil → England)
Ordered: Brazil → England → India (B→E→I)    
```

With integer keys (1→"lov", 2→"anita", 3→"babita"), ordered map prints **1,2,3** despite insertion order 3,1,2—keys dictate sort order.        

  

## Set Container Fundamentals

`std::set` stores **unique elements only**—duplicates are automatically rejected (e.g., inserting 10 multiple times stores it once). Like maps, two variants:    

- **Unordered Set** (`std::unordered_set`): Hash table, `O(1)` operations, random order. Requires `<unordered_set>` header.   
- **Ordered Set** (`std::set`): Self-balancing BST, `O(log n)` operations, **sorted ascending order** by default. Requires `<set>` header.    

**Creation and Basic Operations** (same for both):
```cpp
set<int> s;  // or unordered_set<int>
s.insert(10); s.insert(15); s.insert(8); s.insert(4);  // Duplicates ignored    
```
- `size()`: Returns element count (e.g., 4).   
- `empty()`: `true` if no elements.    
- `clear()`: Removes all elements (size → 0).   

**Traversal** (iterator-based, like vectors/lists):
```cpp
for (auto it = s.begin(); it!= s.end(); ++it) {
    cout << *it << " ";  // Ordered: 4 8 10 15; Unordered: random        
}
```
**Erase Range**:
```cpp
s.erase(s.begin(), s.end());  // Empties set     
```

## Set: Find and Count

Identical to map behavior, since sets store unique keys (elements act as keys):
- `find(value)`: Iterator to element if found, `end()` if not.     
  ```cpp
  if (s.find(15)!= s.end()) { /* found */ }  // Prints "found"    
  ```
- `count(value)`: 1 (found) or 0 (not found).   
  ```cpp
  if (s.count(15) == 1) { /* found */ }  // For 155: "not found"   
  ```

All map code applies to sets (minor type adjustments).    

## STL Algorithms Introduction

STL `<algorithm>` provides **pre-defined functions** for common operations on containers (vectors, lists, sets, maps) via iterators: sort, reverse, find, count, etc. These operate on **ranges** (`begin()` to `end()`).    

**Algorithm Definition**: A series of steps to perform a task (e.g., cooking Maggi: boil water → add Maggi → stir).   

## Iterators and Iterating Algorithms

### for_each
Applies a **function to every element** in a range.
```cpp
void printDouble(int a) { cout << 2*a << " "; }
vector<int> arr = {10,20,30,40,50};
for_each(arr.begin(), arr.end(), printDouble);  // Outputs: 20 40 60 80 100            
```
Modifies container in-place if function alters elements.

### find
Returns iterator to **first occurrence** of target; `end()` if none.
```cpp
auto it = find(arr.begin(), arr.end(), 40);
if (it!= arr.end()) cout << *it;  // 40 (valid iterator)      
else cout << 0;  // For 400: 0 (end() as zero)  
```

### find_if
Finds **first element matching a condition** (predicate function).
```cpp
bool checkEven(int a) { return a%2 == 0; }
auto it = find_if(arr.begin(), arr.end(), checkEven);
cout << *it;  // 20 (first even)          
```

### count
Returns **occurrences** of a value.
```cpp
int ans = count(arr.begin(), arr.end(), 11);  // 3    
```

### count_if
Counts elements matching a **condition**.
```cpp
int ans = count_if(arr.begin(), arr.end(), checkEven);  // 2 (20,40)     
```

  

## Sorting and Reversing

### sort
Sorts range in **ascending order** (default).
```cpp
vector<int> arr = {11,40,10,20,12};
sort(arr.begin(), arr.end());  // 10 11 12 20 40      
```

### reverse
Reverses range order.
```cpp
reverse(arr.begin(), arr.end());  // 40 20 12 11 10     
```

## Rotate Algorithm

**Right-rotates** a range by `n` positions (circular shift right).
- Elements from `begin` to `middle` move to `middle`; rest shift cyclically.
Example: `{10,20,30,40,50,60}` rotate right by 3 → `{40,50,60,10,20,30}`.
```cpp
rotate(arr.begin(), arr.begin()+3, arr.end());                
```
**Mechanism**: Each element shifts right by 3; overflow wraps around (40→pos0, 50→pos1, etc.). Left rotate: homework (use negative or adjust middle).   

## Additional Algorithms: is_unique (Partial)

For **sorted ranges**, `unique` removes **consecutive duplicates** (must sort first).  

---

## std::unique: Removing Duplicates from Sorted Ranges

`std::unique` removes consecutive duplicate elements from a **sorted range**, shifting unique elements to the front and returning an iterator to the new end of the unique sequence. Duplicates remain in the container after the returned iterator but must be erased manually for complete removal.

**Mechanism**: It rearranges elements so identical consecutive elements are grouped at the end, preserving relative order of unique elements. Works only on sorted ranges because it identifies duplicates by adjacency.

**Usage Pattern**:
```
auto it = std::unique(arr.begin(), arr.end());
arr.erase(it, arr.end());  // Remove duplicates after unique iterator   
```
**Example**: Input `{1,1,2,2,2,3}` → After `unique`: `{1,2,3,2,2}` (iterator points after `3`), then `erase` yields `{1,2,3}`.    

## std::partition: Rearranging by Predicate

`std::partition` rearranges a range so all elements satisfying a **predicate** (criterion) come before those that don't, returning an iterator to the first non-matching element. Order within partitions is not preserved.

**Mechanism**: Elements matching the predicate (e.g., even numbers) are moved to the front; others to the back. Stable version `std::stable_partition` preserves relative order.

**Usage**:
```
auto it = std::partition(arr.begin(), arr.end(), is_even);
```
**Example**: `{10,11,12,13,14,15}` with `is_even` → `{10,12,14,11,13,15}` (iterator after `14`). Print verifies partitioning.

## Numeric Algorithms

These perform mathematical operations on ranges. Require `<numeric>` header.

### std::accumulate: Compute Sum (or Custom Reduction)
Sums range elements starting from an initial value.
```
int sum = std::accumulate(arr.begin(), arr.end(), 0);  // 0 is initial value  
```
**Example**: `{10,20,30,40,50}` → `150`. Initial value adds to result (e.g., `1000` → `1150`).

### std::inner_product: Dot Product of Two Ranges
Multiplies corresponding elements and sums results.
```
int product = std::inner_product(first.begin(), first.end(), second.begin(), 0);
```
**Example**: `{1,2,3}` and `{3,4,5}` → `(1*3 + 2*4 + 3*5) = 26`.

### std::partial_sum: Prefix Sums
Writes cumulative sums to output range.
```
std::partial_sum(first.begin(), first.end(), result.begin());  
```
**Example**: `{1,2,3,4}` → `{1,3,6,10}`.

### std::iota: Fill Sequential Values
Fills range with incrementing values from a start value.
```
std::iota(first.begin(), first.end(), 250);  // Fills 250,251,252,253,254  
```
**Use**: Generate consecutive integers.

| Algorithm | Purpose | Time Complexity | Key Parameters |
|-----------|---------|-----------------|---------------|
| accumulate | Sum/reduction | $$O(n)$$ | initial value   |
| inner_product | Dot product | $$O(n)$$ | two ranges + initial   |
| partial_sum | Prefix sums | $$O(n)$$ | output iterator   |
| iota | Sequential fill | $$O(n)$$ | start value   |   

## Searching Algorithms (Require Sorted Ranges)

From `<algorithm>`. Binary search variants need **monotonic (sorted)** data.

### std::binary_search
Returns `true` if target exists in sorted range ($$O(\log n)$$).
```
bool found = std::binary_search(arr.begin(), arr.end(), 40);  // true  
```
**Note**: Returns boolean, not iterator.

### std::lower_bound
Returns iterator to **first** element `>=` value (or end if none).
```
auto it = std::lower_bound(arr.begin(), arr.end(), 35);  // Points to 40   
```

### std::upper_bound
Returns iterator to **first** element `>` value.
```
auto it = std::upper_bound(arr.begin(), arr.end(), 40);  // Points to 50   
```
**Key Difference**:
- `lower_bound(35)` → `>=35` (40 if 35 absent)
- `upper_bound(35)` → `>35` (always next larger, even if 35 exists)   

**Example Range**: `{10,20,30,40,50}`. All $$O(\log n)$$.

## Min/Max Algorithms

### Pairwise min/max
```
int max_val = std::max(a, b);  // 15 from 10,15  
int min_val = std::min(a, b);  // 10  
```

### Range min/max (returns iterator)
```
auto min_it = std::min_element(arr.begin(), arr.end());  // *min_it = 10  
auto max_it = std::max_element(arr.begin(), arr.end());  // *max_it = 50  
```
**Example Range**: `{10,20,30,40,50}`.

## Heap Algorithms (Max-Heap by Default)

Transform vectors into heaps (related to `priority_queue`). Require sorted or heap-maintained state.

| Operation | Function | Steps | Time |
|-----------|----------|--------|------|
| Create Heap | `make_heap(arr.begin(), arr.end())` | Converts range to max-heap   | $$O(n)$$   |
| Insert | `push_back(99); push_heap(begin, end)` | Append then heapify    | $$O(\log n)$$   |
| Delete Max | `pop_heap(begin, end); pop_back()` | Heapify then remove    | $$O(\log n)$$   |
| Sort | `sort_heap(begin, end)` | Sorts heap into ascending   | $$O(n)$$   |

**Example**: `{22,11,55,56,77,66}` → Max-heap `{77,66,55,...}`. Insert 99 requires `push_heap` to maintain property.

## Set Algorithms

Operate on **sorted ranges** (no duplicates in result). Output to result via `insert` iterator.

**Syntax** (for vectors `first={1,2,3,4}`, `second={3,4,5,6}`):
```
std::set_union(first.begin(), first.end(), second.begin(), second.end(), inserter(result, result.begin()));
```

| Operation | Result | Example Output |
|-----------|--------|---------------|
| `set_union` | Unique elements from both   | `{1,2,3,4,5,6}`   |
| `set_intersection` | Common elements   | `{3,4}`   |
| `set_difference` (first - second)   | In first, not second | `{1,2}`   |
| `set_symmetric_difference`   | In exactly one range | `{1,2,5,6}`   |

**Mechanism**: Treat sorted ranges as sets; results are sorted, unique.

## Summary of Iterating Algorithms Recap

- `for_each`: Apply function to range  
- `find`/`find_if`: Locate element   
- `count`/`count_if`: Occurrence count  
- `sort`: Ascending order  
- `reverse`: Reverse elements  
- `rotate`: Shift/rotate  
- Followed by unique, partition.

These STL algorithms enable efficient non-modifying sequences, reductions, searches, and transformations on containers.

---

## What Are Iterators in C++ STL?

Iterators are **pointer-like objects** that point to a specific position (element) within a Standard Template Library (STL) container, such as a vector, list, or deque. They provide a **standardized way** to traverse elements across **all compatible containers**, unlike raw pointers which are container-specific.        

Why use them? Containers like vectors, lists, and deques share a uniform traversal method via iterators (`begin()` and `end()`), enabling consistent access regardless of internal storage (e.g., contiguous array in vector vs. linked nodes in list).   

**Key positions:**
- `container.begin()`: Points to the **first element** (starting position).
- `container.end()`: Points to the **position past the last element** (not the last element itself; used as loop sentinel).    

  

This loop traverses until `it!= end()`: `while (it!= container.end()) { cout << *it++; }`.     

## Creating and Using Iterators

**Syntax**: `vector<int>::iterator it = arr.begin();` (or `auto it = arr.begin();` in modern C++).    

**Example code** (vector of integers):
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> arr;
    arr.push_back(10); arr.push_back(20); arr.push_back(30);
    
    vector<int>::iterator it = arr.begin();
    while (it!= arr.end()) {
        cout << *it << " ";  // Dereference: *it
        ++it;                // Advance
    }
    // Output: 10 20 30
    return 0;
}
```
**Mechanism**: `it` starts at `begin()`, dereferences (`*it`) to access value, increments (`++it`) to next position, stops at `end()`.        

For-each style (range-based) uses iterators under the hood but simplifies syntax.  

## Iterator Operations

Iterators support pointer-like operations for navigation and access. Assume `vector<int> arr = {10,20,30,40}; auto itr = arr.begin();` (itr points to 10).    

| Operation | Description | Effect on itr (at 10) | Equivalent |
|-----------|-------------|-----------------------|------------|
| `*itr` | Dereference: value at current position | 10 | Value at itr |
| `++itr` or `itr++` or `itr = itr + 1` | Move forward 1 position | Points to 20 | Next element   |
| `--itr` or `itr--` or `itr = itr - 1` | Move backward 1 position | Points before begin() (undefined for some types) | Previous   |
| `itr + n` (e.g., `itr + 3`) | Jump forward n positions | Points to 40    | Random forward   |
| `itr1 == itr2` | Equal if same position | true/false   |
| `itr1!= itr2` | Not equal positions   | true/false   |
| `itr1 = itr2` | Copy position   | itr1 now at itr2 |

**Special dereference for complex types** (e.g., `map` entries are `pair<key,value>`):
- `*itr` or `itr->first` / `itr->second` accesses pair members (arrow `->` equivalent to `(*itr).first`).            
- Use `.` on `*itr` or `->` on `itr` for custom objects/pairs.

## Types of Iterators

STL defines **5 iterator categories** with increasing capabilities (hierarchy: Input < Forward < Bidirectional < Random Access). Each supports operations matching its power; stronger types are backward-compatible.   

| Type | Read | Write | Movement | Example Container |
|------|------|-------|----------|-------------------|
| **Input** | Yes (read-only) | No | Forward only (`++`)     | Input streams (e.g., `find`, `for_each`)   |
| **Output** | No | Yes (write-only) | Forward only    | Output streams   |
| **Forward** | Yes | Yes | Forward only    | `forward_list` (singly-linked)    |
| **Bidirectional** | Yes | Yes | Forward (`++`) + Backward (`--`)    | `list`, `deque`     |
| **Random Access** | Yes | Yes | Forward/backward + random jumps (e.g., `+n`, `-n`, `[]`)   | `vector`, `array`, `deque` |

**Why categories matter**: Match iterator type to container for efficiency/safety. Compiler enforces via syntax (e.g., `--` fails on forward iterators).  

  

## Forward Iterator Example: forward_list

`forward_list` is singly-linked (data + next pointer only), so **forward-only movement**.     

**Code** (read + write):
```cpp
#include <forward_list>
forward_list<int> flist;
flist.push_front(30); flist.push_front(20); flist.push_front(10);  // 10→20→30

auto it = flist.begin();
while (it!= flist.end()) {
    *it = *it + 5;  // Write: +5 each
    ++it;           // Forward only
}
// Now: 15→25→35     
```
`--it` **compiles but fails at runtime** (no prev pointer).      

## Bidirectional Iterator Example: list

`list` is doubly-linked (data + prev + next), enabling **bidirectional traversal**.    

**Forward + read/write**:
```cpp
list<int> lst{10,20,30};
auto it = lst.begin();
while (it!= lst.end()) {
    *it += 2;  // Write
    cout << *it << " ";  // Read: 12 22 32
    ++it;
}    
```

**Backward traversal** (start at `end()`, `--` to last valid):
```cpp
auto it = lst.end();
while (it!= lst.begin()) {
    --it;              // Backward
    cout << *it << " ";  // 30 20 10 (prints after --)
}       
```
`end()` points **past last** (no data), so `--it` first reaches last element.   

**Verification**: Supports read/write + forward/backward fully.  

---

## Random Access Iterator

Random Access Iterators provide the most powerful capabilities among STL iterator types, supporting all operations of previous types plus direct random access to any element. They enable reading (`*it`), writing (`*it = value`), forward movement (`++it`), backward movement (`--it`), and random jumps (`it + n` or `it - n`).

**Key Containers Supporting Random Access Iterators:**
- Arrays
- `std::vector`
- `std::deque` (pronounced "double-ended queue")

### Forward Traversal and Read/Write in Vector
```cpp
#include <vector>
std::vector<int> arr = {10, 20, 30, 40, 50};
auto it = arr.begin();  // Points to first element
while (it!= arr.end()) {
    *it = *it + 7;  // Write: adds 7 to each element
    std::cout << *it << " ";  // Read and print
    ++it;  // Forward move
}
// Output: 17 27 37 47 57    
```
This demonstrates read/write and forward traversal. Alternative initialization uses `push_back` if direct initialization fails due to compiler version.  

### Backward Traversal
To traverse backward, initialize at `arr.end() - 1` (last valid element) or `arr.end()` and decrement first:

```cpp
std::vector<int> arr{10, 20, 30};
auto it = arr.end() - 1;  // Points to last element (30)
while (it!= arr.begin()) {
    std::cout << *it << " ";
    --it;
}
// Avoids printing first element due to loop condition   

auto it2 = arr.end();
while (it2!= arr.begin()) {
    --it2;  // Move back first
    std::cout << *it2 << " ";  // Then read
}
// Output: 30 20 10    
```
`arr.end()` points past the last element; dereferencing causes undefined behavior, so always decrement before reading.   



`arr.end()` marks the end position (one past last element), not dereferenceable.  

### Random Access
Jump directly to any position using offset arithmetic:
```cpp
std::vector<int> arr{10, 20, 30, 40, 50};
auto it = arr.begin() + 3;  // Points to 40 (index 3)
std::cout << *it;  // Output: 40   
```
`arr.begin() + n` computes the iterator for the nth element (0-based).   

## Iterator Type Comparison

| Iterator Type       | Read | Write | Forward (++it) | Backward (--it) | Random Access (it + n) |
|---------------------|------|-------|----------------|-----------------|-------------------------|
| Input         | ✅   | ❌    | ✅             | ❌              | ❌                      |
| Output        | ❌   | ✅    | ✅             | ❌              | ❌                      |
| Forward       | ✅   | ✅    | ✅             | ❌              | ❌                      |
| Bidirectional  | ✅   | ✅    | ✅             | ✅              | ❌                      |
| **Random Access**   | ✅ | ✅    | ✅             | ✅              | ✅                      |

No need to explicitly check iterator types in code—STL handles it. Focus on basic usage: creation (`auto it = container.begin()`), traversal (`while (it!= end())`), and operations (`*it`, `++it`, `--it`).   

## Why Use Iterators?

Iterators provide a **uniform, safe traversal mechanism** across all STL containers (vector, list, deque, stack, queue, set, map, etc.), enabling code reuse and memory efficiency.

**Advantages:**
- **Standardized traversal**: Same syntax for any container  
- **Code reusability**: Write once, use everywhere  
- **Safety**: Bounds-checked via `end()`  
- **Abstraction**: Hide container internals

Practical knowledge suffices: create iterators, apply operations, traverse. Theoretical types rarely needed explicitly.   

## Functors (Function Objects)

Functors are **classes with overloaded `()` operator**, behaving like functions when their objects are called. Requires OOP knowledge (classes, objects, operator overloading).   

**Definition**: A functor is a function object—create class, overload `operator()` for custom behavior.   

### Basic Functor Example (Descending Integer Comparison)
```cpp
class FunctorOne {
public:
    bool operator()(int a, int b) {
        return a > b;  // True if a should precede b (descending)  
    }
};

int main() {
    FunctorOne cmp;
    if (cmp(10, 5)) {  // Calls operator(): treats object like function
        std::cout << "10 > 5";  // Output  
    }
}
```
`return a > b` places larger `a` before `b`, creating descending order.   

### Functor for Custom Objects (Student Comparison)
```cpp
class Student {
public:
    int marks;
    std::string name;
    Student(int m, std::string n): marks(m), name(n) {}
};

class StudentComparator {
public:
    bool operator()(Student a, Student b) {
        return a.marks < b.marks;  // Ascending marks  
    }
};

int main() {
    Student s1(93, "Babbar");
    Student s2(97, "Lakshya");
    StudentComparator cmp;
    if (cmp(s1, s2)) {
        std::cout << "Babbar's marks < Lakshya's";  // Output  
    }
}
```
Custom logic defined inside `operator()`.  



**Purpose**: Define **custom comparison logic** for algorithms like sorting/searching on built-in types or custom objects (e.g., sort students by marks/name). STL `sort` assumes ascending for primitives; custom classes need explicit logic.   

## Custom Comparators in Sorting

Pass functor object to `std::sort` as third argument for custom ordering.

### Descending Sort (Integers)
```cpp
#include <algorithm>
#include <vector>
std::vector<int> arr{20, 10, 15};
class Comparator {
public:
    bool operator()(int a, int b) {
        return a > b;  // Larger first  
    }
};
std::sort(arr.begin(), arr.end(), Comparator());
// Output: 20 15 10  
```
Default `sort` is ascending (`a < b`).   

### Custom Object Sort (Students by Marks)
```cpp
std::vector<Student> arr;
arr.push_back(Student(90, "Love"));
arr.push_back(Student(85, "Lakshya"));
arr.push_back(Student(95, "Kunal"));

class StudentComparator {
public:
    bool operator()(Student a, Student b) {
        if (a.marks!= b.marks)
            return a.marks < b.marks;  // Ascending marks  
        return a.name < b.name;  // Tie-break: lexicographical names  
    }
};
std::sort(arr.begin(), arr.end(), StudentComparator());
// Ascending marks: 85(Lakshya), 90(Love), 95(Kunal)  
```
For descending marks: `return a.marks > b.marks;`. `true` means first arg precedes second.   

Without comparator, custom objects fail to compile in `sort` (no default comparison).   

## Custom Priority Queue

`priority_queue` syntax: `priority_queue<Type, Container, Comparator>`.
- **Type**: Stored data (e.g., `int`, `Student`)
- **Container**: Underlying (default: `vector<T>`)  
- **Comparator**: Functor (default: `less<T>` for max-heap)  

| Syntax Example | Heap Type | Comparator Effect |
|----------------|-----------|-------------------|
| `priority_queue<int> pq;`   | Max-heap (top = max) | `less<int>` (default, omitted) |
| `priority_queue<int, vector<int>, greater<int>> pq2;`   | Min-heap (top = min) | `greater<int>` |
| `priority_queue<int, vector<int>, less<int>> pq3;`   | Max-heap | `less<int>` (explicit) |

**Custom Comparator for Student Min-Heap** (top = lowest marks):
```cpp
class StudentPQComparator {
public:
    bool operator()(Student a, Student b) {
        return a.marks > b.marks;  // Min-heap: smaller marks first  
    }
};
priority_queue<Student, vector<Student>, StudentPQComparator> pq;
```
Understanding parameters separates you from most learners—defaults hide the structure.   

---

## Custom Comparator for Priority Queue with Student Class

Priority Queue (PQ) in C++ Standard Template Library (STL) requires a custom comparator for user-defined classes like `Student` to define ordering. The `Student` class stores data such as name and marks. To create a min-heap PQ (minimum marks at top), use `priority_queue<Student, vector<Student>, Comparator>` where `Comparator` is a functor (function object).   

```cpp
priority_queue<Student, vector<Student>, Comparator> pq;
```

## Functor Implementation for Min Marks Priority

A functor overloads the `()` operator to behave like a function, enabling custom comparison logic. Define `Comparator` as:

```cpp
class Comparator {
public:
    bool operator()(Student a, Student b) {
        return a.marks < b.marks;  // Returns true if a's marks < b's marks
    }
};
```

**Mechanism**: 
- If `a.marks < b.marks`, return `true` → `a` placed before `b` in heap ordering.
- This creates **min-heap behavior**: smallest marks get highest priority (top of PQ).   

**Why it works**: PQ internally uses heap property where parent ≤ children (min-heap). Comparator dictates "less than" for reordering during insertions.

## Insertion and Heap Building Process

Insert students with marks: 95 ("Love"), 90 ("Lakshya"), 27 ("Amit"), 82 ("Vipul").

| Step | Insert | Comparison Logic | Heap State (logical order, root at top) |
|------|--------|------------------|-----------------------------------------|
| 1 | 95 ("Love") | - | 95 |
| 2 | 90 ("Lakshya") | 90 < 95 → 90 before 95 | 90, 95 |
| 3 | 27 ("Amit") | 27 < 90 and 27 < 95 → 27 at root | 27, 90, 95 |
| 4 | 82 ("Vipul") | 82 > 27 but 82 < 90 → between | 27, 82, 95, 90    |

**Key Insight**: Heap rearranges via "sift-up" after each push, bubbling smaller elements toward root using comparator.  



Visual shows sift-up: new element swaps upward if smaller, ensuring min at root.  

## Pop Order and Top() Behavior

`pq.top()` always returns **maximum marks first** despite min-heap intent—due to comparator inversion:

- Prints: 95, 90, 82, 27 (descending order).   
- **Explanation**: Standard PQ `top()` is **max-heap by default** (`greater` yields min-heap top). Custom `return a.marks < b.marks` mimics `less` → **max-heap** (largest at top).   
- To fix for true min-heap: Use `return a.marks > b.marks;` (logical "greater" for min-top).

**Loop to empty**:
```cpp
while (!pq.empty()) {
    Student topStudent = pq.top();
    cout << topStudent.marks << " " << topStudent.name << endl;
    pq.pop();  // Removes top, heapifies next
}
```

## Common Pitfall and Correction

**Mistake**: Assumed `a.marks < b.marks` → min at top, but got max.  

| Desired | Comparator Logic | Resulting Heap Type | top() Returns |
|---------|------------------|---------------------|---------------|
| Min marks top | `return a.marks > b.marks;` | Min-heap | Smallest   |
| Max marks top (as coded) | `return a.marks < b.marks;` | Max-heap | Largest   |

**Fix**: Invert comparator for intended priority. Test by printing `pq.top()` after each push.  

Functors enable treating objects as functions via `()` overload—essential for STL containers like PQ with custom types.
