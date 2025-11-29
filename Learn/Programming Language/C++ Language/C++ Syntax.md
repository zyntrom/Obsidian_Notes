## 📘 1. **Basic Syntax**

### Headers & Main Function

```cpp
#include <iostream> 
using namespace std;  
int main() {     
	// code     
	return 0; 
}
```

### Input/Output

```cpp
cin >> var;           // input 
cout << var << endl;  // output
```

### Variables & Data Types

```cpp
int, float, double, char, bool; long, long long, unsigned int;
```

### Constants

```cpp
const int x = 10; 
#define PI 3.14
```

### Conditionals
```cpp
if (condition) { 

} 
else if () { 

} else {
	
} 
switch (var) {     
	case value: break;     
	default: break; 
}
```

### Loops

```cpp
for (int i = 0; i < n; i++) { 

} 
while (condition) { 

} do { 

} while (condition);
```

### Functions

```cpp
returnType functionName(parameters) {     
	// body     
	return value; 
}
```

---

## 📘 2. **Data Structures**

### Arrays

```cpp
int arr[5] = {1, 2, 3, 4, 5}; 
int arr2D[3][3];
```

### Strings

```cpp
#include <string> 
string s = "hello"; 
s.length(); 
s.size(); 
s += " world"; 
s.substr(0, 3); 
s.find("lo"); 
s.erase(pos, len);
```

### Vectors

## 🧰 Commonly Used Vector Functions

Below is a **complete reference table** of vector functions you’ll use most often:

| Function            | Description                                 | Example                      |
| ------------------- | ------------------------------------------- | ---------------------------- |
| `v.size()`          | Returns number of elements                  | `int n = v.size();`          |
| `v.empty()`         | Checks if vector is empty                   | `if(v.empty())`              |
| `v.push_back(x)`    | Adds element `x` at the end                 | `v.push_back(10);`           |
| `v.pop_back()`      | Removes last element                        | `v.pop_back();`              |
| `v.front()`         | Access first element                        | `cout << v.front();`         |
| `v.back()`          | Access last element                         | `cout << v.back();`          |
| `v[i]`              | Access i-th element (0-based index)         | `v[2] = 10;`                 |
| `v.at(i)`           | Safe access (throws error if out of bounds) | `v.at(2)`                    |
| `v.begin()`         | Iterator to first element                   | `auto it = v.begin();`       |
| `v.end()`           | Iterator to position after last element     | `auto it = v.end();`         |
| `v.insert(it, x)`   | Insert `x` at position `it`                 | `v.insert(v.begin()+2, 99);` |
| `v.erase(it)`       | Remove element at iterator position         | `v.erase(v.begin()+1);`      |
| `v.clear()`         | Removes all elements                        | `v.clear();`                 |
| `v.resize(n)`       | Resizes vector to `n` elements              | `v.resize(10);`              |
| `v.assign(n, val)`  | Fills vector with `n` copies of `val`       | `v.assign(5, 0);`            |
| `v.swap(v2)`        | Swap contents with another vector           | `v.swap(v2);`                |
| `v.capacity()`      | Returns allocated memory capacity           | `cout << v.capacity();`      |
| `v.shrink_to_fit()` | Reduces capacity to current size            | `v.shrink_to_fit();`         |
### Pairs

```c++
#include <utility>  
pair<int, int> p = {1, 2}; 
p.first; 
p.second;
```

### Sets

```c++
#include <set>  
set<int> s;
s.insert(5); 
s.erase(5); 
s.count(5); 
s.find(5);
```

### Maps

```c++
#include <map>  
map<string, int> m; 
m["apple"] = 3; 
m.count("apple");
```

### Stack

```c++
#include <stack>  
stack<int> s; s
.push(1); 
s.top(); 
s.pop(); 
s.empty();
```

### Queue

```c++
#include <queue>  
queue<int> q; 
q.push(1); 
q.front(); 
q.back(); 
q.pop();
```

### Priority Queue

```c++
#include <queue>  
priority_queue<int> maxHeap; 
priority_queue<int, vector<int>, greater<int>> minHeap;
```

---

## 📘 3. **Algorithms Library**

```c++
#include <algorithm>
```

### Sorting & Reversing

```c++
sort(v.begin(), v.end()); 
reverse(v.begin(), v.end());
```

### Min/Max

```c++
min(a, b); 
max(a, b);
```

### Accumulate (Sum)

```c++
#include <numeric> 
accumulate(v.begin(), v.end(), 0);
```

### Binary Search

```c++
binary_search(v.begin(), v.end(), value);
```

### Lower/Upper Bound

```c++
lower_bound(v.begin(), v.end(), value); 
upper_bound(v.begin(), v.end(), value);
```

### Next Permutation

```c++
next_permutation(s.begin(), s.end());
```

---

## 📘 4. **Math Functions**

```c++
#include <cmath>  
sqrt(x);     // Square root 
pow(x, y);   // x^y 
abs(x);      // Absolute 
ceil(x);     // Round up 
floor(x);    // Round down 
round(x);    // Nearest integer 
log(x); 
log10(x);
```

---

## 📘 5. **Time & Random**

```c++
#include <ctime> 
#include <cstdlib>  
srand(time(0)); 
int r = rand() % 100;
```

---

## 📘 6. **Useful Macros and Typedefs**

```c++
#define fastIO ios::sync_with_stdio(0); 
cin.tie(0); 
#define all(x) x.begin(), x.end() typedef long long ll;
```

---

## 📘 7. **File I/O**

```c++
#include <fstream>  
ifstream in("input.txt"); 
ofstream out("output.txt"); 
in >> x; 
out << x;
```

---

## 📘 8. **Exception Handling**

```c++
try {     
	// code 
} catch (exception &e) {     
	cout << e.what(); 
}
```

---
## 📘 1. **String Library**

```c++
#include <string>
```

## 📌 Common String Methods (for `std::string`)

|Function|Description|
|---|---|
|`s.length()` or `s.size()`|Returns length of string|
|`s.empty()`|Checks if string is empty|
|`s.append("abc")`|Appends string|
|`s += "abc"`|Concatenates|
|`s.substr(pos, len)`|Substring from position|
|`s.find("abc")`|Returns index of first occurrence|
|`s.rfind("abc")`|Returns index of last occurrence|
|`s.erase(pos, len)`|Erases part of the string|
|`s.insert(pos, "abc")`|Inserts string at position|
|`s.replace(pos, len, "xyz")`|Replaces part of string|
|`s.c_str()`|Converts to C-style char* string|
|`s.compare("abc")`|Compares strings (returns 0 if equal)|

---

## 📘 2. **Character Functions**

```c++
#include <cctype>
```

## 📌 Useful Char Functions (for `char ch`)

|Function|Description|
|---|---|
|`isalpha(ch)`|True if letter (a-zA-Z)|
|`isdigit(ch)`|True if digit (0-9)|
|`isalnum(ch)`|True if letter or digit|
|`islower(ch)`|True if lowercase|
|`isupper(ch)`|True if uppercase|
|`isspace(ch)`|True if space, tab, newline|
|`tolower(ch)`|Converts to lowercase|
|`toupper(ch)`|Converts to uppercase|

---

## 📘 3. **Numeric Functions**

```c++
#include <cmath> 
#include <cstdlib> 
#include <limits> 
#include <numeric>
```

## 📌 Math / Numeric Functions

|Function|Description|
|---|---|
|`abs(x)`|Absolute value|
|`pow(x, y)`|x raised to power y|
|`sqrt(x)`|Square root|
|`log(x)`|Natural log|
|`log10(x)`|Base-10 log|
|`floor(x)`|Largest int ≤ x|
|`ceil(x)`|Smallest int ≥ x|
|`round(x)`|Nearest integer|
|`max(a, b)`|Maximum|
|`min(a, b)`|Minimum|
|`accumulate(begin, end, init)`|Sum of range from `<numeric>`|

## 📌 Random Numbers

```c++
#include <cstdlib> 
#include <ctime>  
srand(time(0));       // Seed random 
int r = rand() % 100; // Random number from 0 to 99
```

---

## 📘 4. **Limits & Constants**

```c++
#include <limits>
```

## 📌 Examples:

```c++
INT_MAX   // Max value of int 
INT_MIN   // Min value of int L
ONG_MAX  // Max of long 
DBL_MAX   // Max double 
numeric_limits<int>::max() numeric_limits<double>::lowest()
```