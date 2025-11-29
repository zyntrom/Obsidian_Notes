# 🐍 Python Full Basic Syntax Reference

---
1
## 📌 1. **Comments**

- **Single-line comment**:  
```python
#This is a comment
```
- **Multi-line (docstring-style) comment**:  
```python
'''This is a multi-line comment'''  
```
- or  
```python
"""This is another multi-line comment"""
```

---

## 📌 2. **Variables and Data Types**

- **Declaration**:  
```python
x = 10
```
- **Dynamic typing**: No need to declare the type.

### **Common Data Types**

|Type|Example|
|---|---|
|int|`x = 10`|
|float|`pi = 3.14`|
|str|`name = "Zyn"`|
|bool|`flag = True`|
|list|`l = [1, 2, 3]`|
|tuple|`t = (1, 2)`|
|set|`s = {1, 2, 3}`|
|dict|`d = {"a": 1}`|
|NoneType|`x = None`|

---

## 📌 3. **Input & Output**

- **Input**:  
```python
x = input("Enter: ") # Always returns a string
```
- **Convert input**:  
```python
x = int(input()), float(), str()
```
- **Output**:  
```python
print("Hello", x)
```
- **Formatted strings**:  
```python
print(f"Name is {name})"
```

---

## 📌 4. **Operators**

### **Arithmetic Operators**

|Operator|Meaning|Example|
|---|---|---|
|+|Addition|1 + 2|
|-|Subtraction|3 - 1|
|*|Multiplication|2 * 3|
|/|Division|5 / 2 = 2.5|
|//|Floor division|5 // 2 = 2|
|%|Modulo|5 % 2 = 1|
|**|Power|2 ** 3 = 8|

### **Comparison Operators**

|Operator|Meaning|Example|
|---|---|---|
|==|Equal to|x == y|
|!=|Not equal|x != y|
|>|Greater than|x > y|
|<|Less than|x < y|
|>=|Greater or eq|x >= y|
|<=|Less or eq|x <= y|

### **Logical Operators**

|Operator|Example|
|---|---|
|and|x > 5 and x < 10|
|or|x < 5 or x > 10|
|not|not(x > 5)|

---

## 📌 5. **Conditionals**

```python
if condition:     
	# block 
elif condition:     
	# block 
else:     
	# block
```

---

## 📌 6. **Loops**

### **while loop**

```python
i = 0 
while i < 5:     
	print(i)     
	i += 1
```

### **for loop**

```python
for i in range(5):     
	print(i)
```

### **range(start, stop, step)**

```python
range(1, 10, 2)  # 1, 3, 5, 7, 9
```

### **Loop controls**

|Keyword|Usage|
|---|---|
|break|Exit loop immediately|
|continue|Skip to next iteration|
|pass|Do nothing (placeholder)|

---

## 📌 7. **Functions**

### **Define function**

```python
def greet(name):     
	return "Hello " + name
```

### **Call function**

```python
greet("Zyn")
```

### **Default arguments**

```python
def add(a, b=5): 
	return a + b
```

---

## 📌 8. **String Methods**

### **Common String Operations**

```python
s = "  Hello World!  "
```

|Method|Description|
|---|---|
|s.lower()|Convert to lowercase|
|s.upper()|Convert to uppercase|
|s.strip()|Remove leading/trailing spaces|
|s.replace("o", "x")|Replace substring|
|s.split(" ")|Split by delimiter|
|s.find("World")|Index of substring or -1|
|len(s)|Length of string|
|s.startswith("He")|Check prefix|
|s.endswith("!")|Check suffix|
|s.isdigit()|Check if all characters are digits|
|s.isalpha()|Check if all characters are alphabets|
|s.count("l")|Count occurrences|
|s[0]|Indexing|
|s[-1]|Negative indexing|
|s[1:5]|Slicing|

---

## 📌 9. **Math Functions** (import math)

```python
import math
```

|Function|Description|
|---|---|
|math.sqrt(x)|Square root|
|math.pow(x, y)|x^y|
|math.ceil(x)|Round up|
|math.floor(x)|Round down|
|math.factorial(x)|Factorial|
|math.pi|Value of π|
|math.e|Value of e|
|math.log(x)|Natural log|
|math.log10(x)|Log base 10|
|math.sin(x)|Sine (x in radians)|
|math.radians(x)|Degrees to radians|
|math.degrees(x)|Radians to degrees|

---

## 📌 10. **Lists**

```python
fruits = ["apple", "banana", "cherry"]
```

|Operation|Usage|
|---|---|
|fruits.append("grape")|Add to end|
|fruits.insert(1, "kiwi")|Insert at index|
|fruits.remove("banana")|Remove by value|
|fruits.pop()|Remove last|
|fruits[0]|Access by index|
|fruits[-1]|Last item|
|fruits[1:3]|Slicing|
|len(fruits)|Number of items|
|fruits.sort()|Sort list|
|fruits.reverse()|Reverse order|

---

## 📌 11. **Tuples**

```python
t = (1, 2, 3)
```

- Immutable
- Access like lists: `t[0]`
- Can unpack: `a, b, c = t`

---

## 📌 12. **Dictionaries**

```python
d = {"name": "Zyn", "age": 21}
```

|Operation|Usage|
|---|---|
|d["name"]|Get value by key|
|d.get("age")|Safe access|
|d["city"] = "NY"|Add new key-value pair|
|d.keys()|Get all keys|
|d.values()|Get all values|
|d.items()|Get key-value pairs|
|d.pop("name")|Remove by key|

---

## 📌 13. **Sets**

```python
s = {1, 2, 3}
```

|Operation|Usage|
|---|---|
|s.add(4)|Add element|
|s.remove(2)|Remove element|
|s.union({4,5})|Set union|
|s.intersection({2,3})|Set intersection|
|s.difference({2})|Set difference|

---

## 📌 14. **Type Conversion**

|Function|Converts to...|
|---|---|
|int(x)|Integer|
|float(x)|Float|
|str(x)|String|
|list(x)|List|
|tuple(x)|Tuple|
|set(x)|Set|
|dict(x)|Dictionary|
|bool(x)|Boolean|

---

## 📌 15. **Exception Handling**

```python
try:     
	x = 10 / 0 
except ZeroDivisionError:     
	print("Cannot divide by zero") 
finally:     
	print("Always runs")
```

---

## 📌 16. **Modules**

```python
import math 
import random  
from math 
import pi, sqrt
```

---

## 📌 17. **Useful Built-in Functions**

|Function|Purpose|
|---|---|
|len(x)|Length of string/list/etc.|
|type(x)|Get type|
|max(x)|Maximum|
|min(x)|Minimum|
|sum(x)|Sum of elements|
|sorted(x)|Return sorted list|
|range(n)|Generate sequence|
|enumerate(x)|Index with elements|
|zip(a, b)|Combine iterables|
|input()|Get user input|
|print()|Display output|