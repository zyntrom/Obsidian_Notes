### 🟦 1. Basic Structure

|Component|Syntax|Description|
|---|---|---|
|Header file|`#include <stdio.h>`|Includes standard input/output library|
|Main function|`int main() { /*...*/ return 0; }`|Entry point of a C program|
|Return|`return 0;`|Ends the function, returns value|

---

### 🟦 2. Data Types

|Type|Description|Example|
|---|---|---|
|`int`|Integer (4 bytes)|`int a = 10;`|
|`float`|Single precision decimal|`float x = 3.14;`|
|`double`|Double precision decimal|`double y = 2.718;`|
|`char`|Single character (1 byte)|`char c = 'A';`|
|`void`|No value (used for functions)|`void func() {}`|

Modifiers:

|Modifier|Use Case|Example|
|---|---|---|
|`short`|Smaller int (2 bytes)|`short s = 12;`|
|`long`|Larger int or double|`long l = 123456789;`|
|`signed`|Default for numbers (with sign)|`signed int a = -5;`|
|`unsigned`|Only positive numbers|`unsigned int b = 5;`|

---

### 🟦 3. Variables & Constants

| Syntax                   | Description                         |
| ------------------------ | ----------------------------------- |
| `int a = 10;`            | Declaring and initializing variable |
| `const float PI = 3.14;` | Constant (read-only after init)     |

---

### 🟦 4. Input/Output

|Function|Syntax Example|Use|
|---|---|---|
|`scanf`|`scanf("%d", &a);`|Takes input from user|
|`printf`|`printf("Value: %d", a);`|Prints output to screen|

Format Specifiers:

|Type|Specifier|
|---|---|
|`int`|`%d`|
|`float`|`%f`|
|`double`|`%lf`|
|`char`|`%c`|
|`string`|`%s`|

---

### 🟦 5. Operators

#### Arithmetic Operators

|Operator|Use|Example|
|---|---|---|
|`+`|Addition|`a + b`|
|`-`|Subtraction|`a - b`|
|`*`|Multiplication|`a * b`|
|`/`|Division|`a / b`|
|`%`|Modulus|`a % b`|

#### Relational & Logical Operators

| Type       | Operators            | Description    |
| ---------- | -------------------- | -------------- |
| Relational | ==, !=, <, >, <=, >= | Compare values |
| Logical    | `&&`, `              |                |

#### Assignment Operators

|Operator|Meaning|Example|
|---|---|---|
|`=`|Assign value|`a = 5`|
|`+=`|Add and assign|`a += 2`|
|`-=`|Subtract and assign|`a -= 2`|
|`*=`|Multiply and assign|`a *= 2`|

---

### 🟦 6. Control Structures

#### If-Else

```c
if (a > b) {   
	// code 
} 
else {   
	// code 
}
```
#### Switch

```c
switch (var) {   
	case 1: break;   
	default: break; 
}
```

---

### 🟦 7. Loops

|Loop Type|Syntax Example|Use|
|---|---|---|
|`for`|`for(i=0; i<n; i++)`|Repeat known number of times|
|`while`|`while(condition)`|Repeat while condition is true|
|`do-while`|`do { } while(condition);`|Guaranteed one-time loop|

Loop Controls:

|Keyword|Use|
|---|---|
|`break;`|Exit loop immediately|
|`continue;`|Skip to next iteration|

---

### 🟦 8. Functions

|Component|Syntax|
|---|---|
|Declaration|`int add(int, int);`|
|Definition|`int add(int a, int b) { return a+b; }`|
|Call|`add(3, 4);`|
|Void function|`void show() { }`|
|Return function|`int getValue() { return 10; }`|

---

### 🟦 9. Arrays

|Syntax Example|Description|
|---|---|
|`int arr[5];`|Declaration|
|`arr[0] = 1;`|Accessing an element|
|`int arr[] = {1,2,3};`|Initialization|

---

### 🟦 10. Strings

|Syntax Example|Description|
|---|---|
|`char str[20] = "Hello";`|Declare and initialize|
|`scanf("%s", str);`|Input string|
|`printf("%s", str);`|Output string|

String Functions:

|Function|Description|
|---|---|
|`strlen()`|String length|
|`strcpy()`|Copy one string to another|
|`strcmp()`|Compare two strings|
|`strcat()`|Concatenate strings|

---

### 🟦 11. Pointers

|Syntax Example|Description|
|---|---|
|`int *p;`|Pointer declaration|
|`p = &a;`|Store address of variable in `p`|
|`*p`|Dereference (get value)|

---

### 🟦 12. Structures

`struct Student {   char name[20];   int age; };`

Usage:

`struct Student s1; strcpy(s1.name, "Alen"); s1.age = 21;`

---

### 🟦 13. Unions

`union Data {   int i;   float f; }; union Data d1; d1.i = 5;`

- Memory shared for all fields.
    
---

### 🟦 14. Enums

`enum Day {Mon, Tue, Wed}; enum Day today = Tue;`

- Assigns names to integral constants.

---

### 🟦 15. Typedef

`typedef unsigned int uint; uint a = 100;`

- Creates an alias name for types.

---

### 🟦 16. Dynamic Memory

|Function|Use|
|---|---|
|`malloc()`|Allocate memory|
|`calloc()`|Allocate & initialize to 0|
|`realloc()`|Resize memory|
|`free()`|Free allocated memory|

Example:

`int *arr = (int*)malloc(5 * sizeof(int)); free(arr);`

---

### 🟦 17. File I/O

|Function|Use|
|---|---|
|`fopen()`|Open a file|
|`fclose()`|Close file|
|`fprintf()`|Write formatted data|
|`fscanf()`|Read formatted data|
|`fgetc()`, `fputc()`|Character read/write|

---

### 🟦 18. Preprocessor

|Directive|Purpose|
|---|---|
|`#define PI 3.14`|Define macro|
|`#include`|Include files|
|`#ifdef`, `#ifndef`, `#endif`|Conditional compilation|

---

### 🟦 19. Storage Classes

|Keyword|Scope/Use|
|---|---|
|`auto`|Local (default for local vars)|
|`register`|CPU register storage hint|
|`static`|Persistent across function calls|
|`extern`|Access global variable outside file|

---

### 🟦 20. Misc

|Syntax|Use|
|---|---|
|`sizeof(var)`|Returns size of variable in bytes|
|`goto label;`|Jump to label (avoid using)|
|`volatile`|