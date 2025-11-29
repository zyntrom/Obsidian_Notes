# DART LANGUAGE — COMPLETE NOTES (BEGINNER TO ADVANCED)

---

## 1. Introduction to Dart

**What is Dart?**

- Dart is an object-oriented, class-based, garbage-collected language.
- Developed by Google for building apps (especially Flutter).
- Compiles to native code (for mobile, desktop) or JavaScript (for web).
- Open-source and fast — JIT (Just-in-Time) for development, AOT (Ahead-of-Time) for release.

**File extension:** `.dart`  
**Command to run Dart file:**  
`dart run filename.dart`

---

## 2. Basic Syntax

**Program structure:**  
Every Dart program starts from `main()` function.

Example:  

```dart
main() {  
	print('Hello Dart!');  
}
```

### Comments

- Single line: `// comment`
- Multi-line: `/* comment */`
- Documentation: `/// comment`

---

## 3. Variables & Data Types

### Variable Declaration

`var` — automatically infers type  
`dynamic` — can hold any type, changes at runtime  
`final` — value assigned once  
`const` — compile-time constant

Example:  

```dart
var name = 'Zyn';  
dynamic age = 20;  
final country = 'India';  
const pi = 3.1415;
```

### Data Types

|Type|Example|Description|
|---|---|---|
|int|10|Whole numbers|
|double|3.14|Decimal numbers|
|num|10 or 10.5|Can hold both int and double|
|String|'hello'|Text|
|bool|true/false|Boolean|
|var/dynamic|depends|Flexible|

---

## 4. Operators

### Arithmetic

```dart
+ - * / % ~/  
```

(`~/` gives integer division result)

### Comparison

```dart
== != > < >= <=
```

### Logical

```dart
&& || !
```

### Assignment

```dart
= += -= *= /= %=
```

### Type Test

```dart
is, is!
```

Example:  

```dart
if (x is int) print('Integer');
```

### Conditional / Ternary

```dart
condition ? expr1 : expr2
```

### Null-aware Operators

- `??` → if null, use right value
- `??=` → assign if null  
    Example:  

    name ??= 'Guest';


---

## 5. Strings

### Declaration

Single or double quotes: `'hello'` or `"hello"`  
Multi-line: `'''hello'''` or `"""hello"""`

### Interpolation

```
'Hello $name' or 'Sum = ${a + b}'
```

### String methods:

|Method|Description|
|---|---|
|length|returns string length|
|toUpperCase()|converts to upper|
|toLowerCase()|converts to lower|
|contains()|check substring|
|replaceAll()|replace text|
|substring()|extract part|
|split()|split into list|
|trim()|remove spaces|

---

## 6. Lists (Arrays)

### Declaration

```dart
var list = 1, 2, 3;
```

### Operations

```dart
list.add(4);  
list.remove(2);  
list.insert(0, 10);  
list.contains(3);  
list.length;  
list.isEmpty;  
list.sort();  
list.clear();
```

### Spread Operator

```dart
var list2 = 0, ...list;
```

### Fixed-length list

```dart
var fixed = List.filled(3, 0);
```

---

## 7. 🔑 Sets

### Declaration

```dart
var set = {1, 2, 3};
```

### Operations

```dart
set.add(4);  
set.remove(2);  
set.contains(1);  
set.union(otherSet);  
set.intersection(otherSet);  
set.difference(otherSet);
```

---

## 8. Maps (Key-Value)

### Declaration

```dart
var map = {'name': 'John', 'age': 20};
```

### Access & Modify

```dart
map'name';  
map'city' = 'Delhi';  
map.containsKey('name');  
map.keys;  
map.values;  
map.remove('age');
```

---

## 9. Control Flow

### If / Else

```dart
if (a > b) { 
	... 
} 
else if (...) { 
	... 
} 
else { 
	... 
}
```
### Switch

```dart
switch(day) {  
	case 'Mon': 
		print('Start'); 
		break;  
	default: 
		print('Unknown');  
}
```

### Loops

```dart
for (var i = 0; i < 5; i++) { 
	...
}  

for (var x in list) { 
	... 
}  

while (condition) { 
	... 
}  

do { 
	... 
} while (condition);
```

### Break & Continue

- `break` exits loop
- `continue` skips iteration

---

## 10. Functions

### Syntax

ReturnType name(parameters) { ... }

Example:  

```dart
int add(int a, int b) { return a + b; }
```
### Arrow Function

```dart
int add(int a, int b) => a + b;
```

### Optional & Named Parameters

```dart
void greet({String name = 'Guest'}) { 
	print('Hello $name'); 
}  
void show(String? message) { 
	print(message ?? 'none'); 
}
```

### Anonymous Functions

```dart
list.forEach((item) { 
	print(item); 
});
```

---

## 11. Object-Oriented Programming (OOP)

### Class and Object

```dart
class Person {  
	String name;  
	int age;  
	Person(this.name, this.age);  
	void show() => print('$name, $age');  
}
```

```dart
main() {  
	var p = Person('John', 30);  
	p.show();  
}
```

### Constructors

- Default constructor
- Named constructor  
    Example:  
    Person.named(this.name, this.age);

### Getters and Setters

```dart
get info => '$name is $age';  
set changeName(String n) => name = n;
```

### Inheritance

```dart
class Student extends Person { ... }
```

### Method Overriding

```dart
@override  
void show() { ... }
```

### Abstract Class

```dart
abstract class Shape { void draw(); }
```

### Interfaces

```dart
class Dog implements Animal { ... }
```

### Mixins

```dart
mixin Runner { void run() => print('Running'); }
class Athlete with Runner { ... }
```

---

## 12. Exception Handling

```dart
try {  
	var result = 10 ~/ 0;  
} on IntegerDivisionByZeroException {  
	print('Cannot divide by zero');  
} catch (e) {  
	print('Error: $e');  
} finally {  
	print('Done');  
}

throw Exception('Custom error');
```

---

## 13. Asynchronous Programming (Future, async, await)

### Future

```dart
Future<String> fetchData() async {  
	return 'Data loaded';  
}
```

```dart
main() async {  
	var data = await fetchData();  
	print(data);  
}
```

### Stream

```dart
Stream<int> counter() async* {  
	for (int i = 1; i <= 3; i++) yield i;  
}

await for (var value in counter()) print(value);

```
---

## 14. Collections & Iterables

### Useful Methods:

```dart
list.where((x) => x > 2);  
list.map((x) => x * 2).toList();  
list.reduce((a, b) => a + b);  
list.every((x) => x > 0);  
list.any((x) => x < 0);  
list.forEach(print);
```

---

## 15. Null Safety

- Variables cannot be null unless explicitly marked `?`
- Example:  
    String? name;  
    name = null; ✅  
    String nonNull = 'Hi';  
    nonNull = null; ❌

Use `!` to assert non-null: `name!.length`  
Use `?.` for safe access: `name?.length`

---

## 16. Libraries & Imports

```dart
import 'dart:math';  
import 'dart:io';  
import 'package:http/http.dart' as http;
```

### Creating Library

```dart
library mylib;  
part 'file.dart';  
export 'utils.dart';
```

---

## 17. File I/O (dart:io)

```dart
import 'dart:io';

File file = File('data.txt');  
await file.writeAsString('Hello');  
String text = await file.readAsString();  
print(text);
```

---

## 18. Generics

```dart
List<int> numbers = [1, 2, 3];  
T getFirst<T>(List<T> list) => list.first;
```

---

## 19. Enums

```dart
enum Color { red, green, blue }  
var c = Color.red;  
print(c.index);  
print(Color.values);
```

---

## 20. 🧩 Extension Methods

```dart
extension StringExtension on String {  
	String capitalize() => this0.toUpperCase() + substring(1);  
}

'hello'.capitalize();
```

---

## 21. ⚙️ Advanced Topics

### Isolates

```dart
Parallel threads for heavy tasks.  
import 'dart:isolate';  
Isolate.spawn(task, message);
```

### Typedefs

```dart
typedef Operation = int Function(int, int);

Operation add = (a, b) => a + b;
```

### Assert

```dart
assert(age > 0);
```

---

## 22. 🧭 Dart CLI Commands

|Command|Description|
|---|---|
|dart create project_name|Create new Dart project|
|dart run file.dart|Run Dart program|
|dart compile exe file.dart|Compile to native executable|
|dart format .|Format code|
|dart test|Run tests|

---

## 23. 🧰 Common Built-in Libraries

|Library|Purpose|
|---|---|
|dart:core|Core types (int, String, etc.)|
|dart:io|File, network, I/O|
|dart:math|Math functions|
|dart:async|Future, Stream|
|dart:convert|JSON encoding/decoding|
|dart:collection|Collections|
|dart:developer|Debugging tools|

---

## 24. 🧠 Best Practices

- Use `const` wherever possible.
- Use `late` keyword for deferred initialization.
- Prefer immutable data.
- Always handle null safely.
- Use `async`/`await` properly to avoid callback hell.
- Use lint tools and formatters (`dart analyze`, `dart format`).