# Rust Complete Notes (Beginner to Advanced)

## 1. Introduction to Rust
Rust is a systems programming language focused on **performance**, **memory safety**, and **concurrency**. It eliminates entire classes of bugs such as null-pointer dereferencing and data races using its unique ownership model.

### Why Rust?
- No Garbage Collector
- Zero-cost abstractions
- Memory safety guaranteed at compile time
- High performance like C/C++
- Great tooling (Cargo)

---

## 2. Installing Rust
Install Rust using Rustup:
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
Check installation:
```bash
rustc --version
```

---

## 3. Cargo – Rust's Build System & Package Manager
Create a new project:
```bash
cargo new project_name
```
Build & run:
```bash
cargo build
cargo run
```
Add dependencies in **Cargo.toml**.

---

## 4. Basic Syntax
### Hello World
```rust
fn main() {
    println!("Hello, Rust!");
}
```

### Variables
```rust
let x = 10;        // immutable
let mut y = 20;    // mutable
y = 30;
```

### Constants
```rust
const PI: f32 = 3.14;
```

### Data Types
- Integer: i32, i64, u32
- Float: f32, f64
- Bool
- Char
- String and &str

---

## 5. Ownership, Borrowing, and Lifetimes (Core to Rust)
### Ownership Rules
1. Each value has a single owner.
2. A value is dropped when its owner goes out of scope.
3. Move semantics transfer ownership.

Example:
```rust
let s1 = String::from("hello");
let s2 = s1; // move
```
`s1` is now invalid.

### Borrowing
```rust
fn main() {
    let s = String::from("hello");
    let len = calculate_length(&s); // borrow
}

fn calculate_length(s: &String) -> usize { s.len() }
```

### Mutable Borrowing
```rust
fn change(s: &mut String) {
    s.push_str(" world");
}
```

### Lifetimes (Basic Idea)
Ensures references are valid for the correct scope.
```rust
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() { x } else { y }
}
```

---

## 6. Functions
```rust
fn add(a: i32, b: i32) -> i32 {
    a + b
}
```
Functions automatically return the last expression.

---

## 7. Control Flow
### If-Else
```rust
if x > 10 {
    println!("Big");
} else {
    println!("Small");
}
```

### Loops
```rust
loop {}
while x < 10 {}
for i in 0..5 {}
```

---

## 8. Structs & Enums
### Structs
```rust
struct User {
    name: String,
    age: u8,
}

let u = User { name: "Alen".into(), age: 21 };
```

### Enums
```rust
enum Direction {
    North,
    South,
    East,
    West
}
```

---

## 9. Pattern Matching
```rust
match num {
    1 => println!("one"),
    2..=5 => println!("2 to 5"),
    _ => println!("other"),
}
```

---

## 10. Error Handling
### Option
```rust
let name: Option<&str> = Some("Rust");
```

### Result
```rust
fn divide(a: i32, b: i32) -> Result<i32, String> {
    if b == 0 { Err("Cannot divide".into()) }
    else { Ok(a / b) }
}
```

---
## 11. Collections

- Vec< T>
- HashMap<K, V>
- String

Example:
```rust
let mut v = vec![1,2,3];
v.push(4);
```

---

## 12. Traits
```rust
trait Greet {
    fn greet(&self) -> String;
}

struct Person;
impl Greet for Person {
    fn greet(&self) -> String {
        "Hello".into()
    }
}
```

---

## 13. Generics
```rust
fn largest<T: PartialOrd>(list: &[T]) -> &T {
    let mut largest = &list[0];
    for item in list {
        if item > largest { largest = item; }
    }
    largest
}
```

---

## 14. Modules & Crates
### Create a module
```rust
mod greetings {
    pub fn hello() {
        println!("Hello");
    }
}
```

### Use
```rust
greetings::hello();
```

---

## 15. Concurrency
### Spawn Threads
```rust
use std::thread;

thread::spawn(|| {
    println!("Hello from thread!");
}).join().unwrap();
```

### Channels
```rust
use std::sync::mpsc;

let (tx, rx) = mpsc::channel();
tx.send("Hi").unwrap();
println!("{}", rx.recv().unwrap());
```

---

## 16. Async Programming
Add in Cargo.toml:
```toml
tokio = { version = "1", features = ["full"] }
```

Example:
```rust
#[tokio::main]
async fn main() {
    async fn work() { println!("Done"); }
    work().await;
}
```

---

## 17. File Handling
```rust
use std::fs;

let data = fs::read_to_string("file.txt")?;
```

---

## 18. Useful Commands
```bash
cargo fmt       # format
cargo clippy    # linter
cargo doc --open
```

---

## 19. Building for Production
```bash
cargo build --release
```
This creates an optimized build.

---

## 20. Rust Best Practices
- Prefer immutability
- Use `?` for error propagation
- Avoid cloning unless necessary
- Use Rustfmt + Clippy

---

## 21. Interview-Level Concepts
- Ownership model
- Borrow checker
- Lifetimes
- Smart pointers (Box, Rc, Arc)
- Concurrency without data races

---

## 22. Smart Pointers
### Box
```rust
let b = Box::new(10);
```
### Rc
```rust
use std::rc::Rc;
let a = Rc::new(5);
```
### Arc (Thread-safe Rc)
```rust
use std::sync::Arc;
```

---

## 23. Final Tips
- Learn ownership deeply—it's core.
- Practice with small projects.
- Use Cargo and crates ecosystem.
- Rust is strict but rewarding.

---


