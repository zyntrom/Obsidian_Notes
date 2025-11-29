## 🧱 1. Basic Java Syntax

```java
public class Main {     
	public static void main(String[] args) {
		System.out.println("Hello, World!");     
	} 
}
```

- `public class Main` → Declares a class named `Main`.
- `main` → The starting point of every Java program.
- `System.out.println()` → Prints text to the console.

---

## 🔢 2. Variables and Data Types

```java
int age = 20; 
double price = 99.99; 
char grade = 'A'; 
boolean isJavaFun = true;
String name = "Alice";
```

**Common data types**:

|Type|Example|Description|
|---|---|---|
|`int`|`int x = 5;`|Integer|
|`double`|`double d = 5.5;`|Decimal number|
|`char`|`'A'`|Single character|
|`boolean`|`true` / `false`|Logic values|
|`String`|`"hello"`|Text (object type)|

---

## 🎯 3. Control Flow

### `if-else`

```java
int age = 18; 
if (age >= 18) {     
	System.out.println("Adult"); } 
else {     
	System.out.println("Minor"); }
```

### `switch`

```java
int day = 3; 
switch(day) {     
	case 1: System.out.println("Mon"); 
			break;     
	case 2: System.out.println("Tue"); 
			break;     
	default: System.out.println("Other"); 
}
```

### `for`, `while`, `do-while`

```java
for (int i = 0; i < 5; i++) {     
	System.out.println(i); 
}  
int j = 0; 
while (j < 5) {     
	System.out.println(j);     
	j++; 
}
```

---

## 🧮 4. Functions (Methods)

```java
public class Main {     
	public static int add(int a, int b) {         
		return a + b;     
}      
	public static void main(String[] args) {         
		int result = add(3, 4);         
		System.out.println(result); // 7     
		} 
}
```

**Syntax:**

```java
[access_modifier] [static] return_type function_name(parameters) {     
	// body 
}
```

---

## 🧱 5. Classes and Objects

```java
class Dog {     
	String breed;      
	void bark() {         
		System.out.println("Woof!");     
	} 
}  
public class Main {     
	public static void main(String[] args) {         
		Dog myDog = new Dog();     // object created         
		myDog.breed = "Labrador";         
		myDog.bark();     
	} 
}
```

---

## ⚙️ 6. Object-Oriented Programming (OOP)

### 🔹 Encapsulation

Wrap data + code together (like above).

Use `private` + `getters/setters`:

```java
class Person {     
	private int age;      
	public void setAge(int a) {         
		age = a;     
	}      
	public int getAge() {         
		return age;     
	} 
}
```

---

### 🔹 Inheritance

```java
class Animal {     
	void eat() {         
		System.out.println("eating...");     
	} 
}  
class Dog extends Animal {     
	void bark() {         
		System.out.println("barking...");     
	} 
}
```

---

### 🔹 Polymorphism

#### Method Overloading (same method name, different args)

```java
class Math {     
	int add(int a, int b) {         
		return a + b;     
	}      
	double add(double a, double b) {         
		return a + b;     
	} 
}
```

#### Method Overriding (child replaces parent method)

```java
class Animal {     
	void sound() {         
		System.out.println("Some sound");     
	} 
}  
class Cat extends Animal {     
	void sound() {         
		System.out.println("Meow");     
	} 
}
```

---

### 🔹 Abstraction

**Using abstract class**:

```java
abstract class Shape {     
	abstract void draw(); 
}  
class Circle extends Shape {     
	void draw() {         
		System.out.println("Drawing Circle");     
	} 
}
```

## 🔧 How to Achieve Abstraction in Java?

### 1. Using **Abstract Classes**

An abstract class:

- Can have **abstract methods** (no body)
- Can have **regular methods** too
    

```java
abstract class Animal {     
	abstract void sound();  // no body = must be implemented by subclass
	void eat() {         
		System.out.println("This animal eats food");     
	} 
}
```

### 2. Using **Interfaces**

An interface:

- Is **100% abstract** by default (Java 8+ allows default methods though)
- All methods are **public and abstract** unless stated otherwise
- A class **implements** an interface

```java
interface Shape {     
	void draw();  // no body 
}
```

---

## 🧪 Example with Abstract Class

```java
abstract class Animal {     
	abstract void sound();  // abstract method      
	void sleep() {         
		System.out.println("Sleeping...");     
	} 
}  
class Dog extends Animal {    
	void sound() {         
		System.out.println("Barks");     
	} 
}
```

**Output:**

```
Barks 
Sleeping...
```

You can’t do: `Animal a = new Animal();` (it's abstract)

---

## 🧪 Example with Interface

```java
interface Shape {     
	void draw();  // abstract method }  
class Circle implements Shape {     
	public void draw() {         
		System.out.println("Drawing Circle");     
	} 
}
```
---

## 🧰 7. Constructors

```java
class Student {     
	String name;      
	Student(String n) {         
		name = n;     
	} 
}
```

---

## 📌 Java Access Modifiers

|Modifier|Meaning|
|---|---|
|`public`|Accessible everywhere|
|`private`|Only in the same class|
|`protected`|Same package or subclass|
|(default)|Same package only|

---

## ✅ Practice Tip

You can practice all these in:

- Online: [https://replit.com](https://replit.com) or [https://www.jdoodle.com](https://www.jdoodle.com)
- Or run using terminal and `javac filename.java` + `java ClassName`

---