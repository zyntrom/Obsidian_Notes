# **KOTLIN — Complete Notes (Basics → Advanced)**

_A clean, well-structured, exam-ready guide_

---

# 1. **Introduction to Kotlin**

### **What is Kotlin?**

- A modern, statically typed programming language.
- Developed by **JetBrains** (Android Studio makers).
- Used for **Android development**, server-side apps, desktop apps, and even web apps (Kotlin JS).

### **Why Kotlin?**

- Interoperable with Java.
- Null safety.
- Concise & expressive.
- Official language for Android (Google, 2017).
- Supports functional + OOP.

---

# 2. **Basic Syntax**

### **Hello World**

```kotlin
fun main() {     
	println("Hello Kotlin") 
}
```

### **Variables**

|Type|Keyword|Example|
|---|---|---|
|Mutable|`var`|`var age = 21`|
|Immutable|`val`|`val pi = 3.14`|

### **Data Types**

- Numeric: `Int`, `Long`, `Float`, `Double`
- Character: `Char`
- String: `String`
- Boolean: `Boolean`

### **Type Inference**

```kotlin
val name = "Alen"   // Kotlin automatically infers type String
```

---

# 3. **Strings**

### **String Templates**

```kotlin
val name = "Alen" println("Hello $name")
```

### **Multiline Strings**

```kotlin
val text = 
	"""     This is      multi-line     string """.trimIndent()
```

---

# 4. **Control Flow**

### **If / Else**

```kotlin
val max = if (a > b) a else b
```

### **When (Switch)**

```kotlin
when (x) {     
	1 -> println("One")     
	2,3 -> println("Two or Three")     
	in 4..10 -> println("Between 4 and 10")     
else -> println("Unknown") }
```

---

# 5. **Loops**

### **For Loop**

```kotlin
for (i in 1..5) 
	println(i)
```

### **While**

```kotlin
while (i < 5) i++
```

### **Ranges**

- `1..5` (includes 5)
- `1 until 5` (excludes 5)
- `10 downTo 1`
- `1..10 step 2`

---

# 6. **Functions**

### **Basic Function**

```kotlin
fun add(a: Int, b: Int): Int {     
	return a + b 
}
```

### **Single Expression Function**

```kotlin
fun mul(a: Int, b: Int) = a * b
```

### **Default Parameters**

```kotlin
fun greet(name: String = "User") {     
	println("Hello $name") 
}
```

### **Named Arguments**

```kotlin
greet(name = "Alen")
```

---

# 7. **Null Safety (Kotlin’s Superpower)**

### **Nullable Type**

```kotlin
var name: String? = null
```

### **Safe Call Operator “?.“**

```kotlin
println(name?.length)
```

### **Elvis Operator " ?: "**

Provides default when null.

```kotlin
val length = name?.length ?: 0
```

### **Not-Null Assertion “!!”**

(Throws exception if null)

```kotlin
val l = name!!.length
```

---

# 8. **Collections**

### **List**

```kotlin
val list = listOf(1,2,3)       // Immutable 
val mlist = mutableListOf(1,2) // Mutable
```

### **Set**

```kotlin
val set = setOf(1,2,2,3)       // Unique elements
```

### **Map**

```kotlin
val map = mapOf("a" to 1, "b" to 2)
```

---

# 9. **Object-Oriented Programming**

## **Classes**

```kotlin
class Person(val name: String, var age: Int)
```

## **Creating Objects**

```kotlin
val p = Person("Alen", 21)
```

## **Inheritance**

- `open` keyword allows inheritance.

```kotlin
open class Animal {     
	open fun sound() = println("Animal sound") 
}  
class Dog : Animal() {     
	override fun sound() = println("Bark") 
}
```

## **Abstract Classes**

```kotlin
abstract class Shape {     
	abstract fun area(): Double 
}
```

## **Interfaces**

```kotlin
interface A {     
	fun show() 
}
```

## **Data Classes**

Automatically generates:

- equals()
- toString()
- hashCode()
- copy()

```kotlin
data class User(val name: String, val age: Int)
```

---

# 10. **Constructors**

### **Primary Constructor**

```kotlin
class Student(val name: String, val roll: Int)
```

### **Secondary Constructor**

```kotlin
class Test {     
	constructor(x: Int) {         
		println(x)     
	} 
}
```

---

# 11. **Objects and Companion Objects**

### **Singleton**

```kotlin
object Database {     
	fun connect() = println("Connected") 
}
```

### **Companion Object**

```kotlin
class Utils {     
	companion object {         
		fun msg() = println("Static-like method")     
	} 
}
```

---

# 12. **Lambda Expressions & Functional Programming**

### **Lambda**

```kotlin
val sum = { a: Int, b: Int -> a + b }
```

### **Higher-Order Function**

```kotlin
fun operate(a: Int, b: Int, op: (Int, Int) -> Int): Int {
	return op(a, b) 
}
```

### **Calling**

```kotlin
operate(2, 3, sum)
```

---

# 13. **Extension Functions**

Add new functions to existing classes.

```kotlin
fun String.lastChar(): Char = this[this.length - 1]  println("Hello".lastChar())
```

---

# 14. **Generics**

```kotlin
class Box<T>(val item: T)
```

---

# 15. **Coroutines (Advanced Topic)**

Used for asynchronous programming.

### **Basic Coroutine**

```kotlin
import kotlinx.coroutines.*  fun main() = runBlocking {     
	launch {         
		delay(1000)         
		println("World")     
	}     
	println("Hello") 
}
```

### **Coroutine Builders**

- `launch` → Fire & forget
- `async` → Returns result (like future)

---

# 16. **Kotlin in Android**

### **Key Features**

- View Binding / Data Binding
- Coroutines
- Kotlin Extensions
- Jetpack Compose support

---

# 17. **Kotlin DSL & Build Scripts**

Gradle uses Kotlin DSL.

```kotlin
plugins {     
	kotlin("jvm") version "2.0.0" 
}
```

---

# 18. **Sealed Classes**

Used for representing restricted hierarchies (useful in MVVM).

```kotlin
sealed class Result data class Success(val data: String): Result() object Error: Result()
```

---

# 19. **Delegation**

### **Class Delegation**

```kotlin
interface Base { fun print() }  
class BaseImpl : Base {     
	override fun print() = println("Hello") 
}  
class Derived(b: Base) : Base by b
```

---

# 20. **Important Kotlin Features to Remember**

✅ Interoperable with Java  
✅ Null Safety  
✅ Concise syntax  
✅ Data classes  
✅ Coroutines  
✅ Extension functions  
✅ Smart casts  
✅ Sealed classes