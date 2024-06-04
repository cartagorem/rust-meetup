##   
## **Meetup:**
## **Introducción a Rust**

---

##   

**Descubre el poder de la programación**

**segura y eficiente con Rust**

---

## Compiler for Modern Developers

- Cargo toolset (e.g. fmt, clippy, code analyzer)
- Compiler's feedback
- Incremental compilation

---

## Immutability by Default

---

## Structs and Traits

---

## Owning and Security
## (Ownership & Borrow Checking)

*fighting the borrow checker*

---

## Heap and Stack

---

##   
## Algebraic Typing
## Pattern Matching = robustness

---

## Metaprogramming or
## Compilation Time Programming

```rust
fn main() {
    todo!() // Macros
}
```

---

## Hands on

1. Hello World
2. CRUD with poem
3. Sistemas Embebidos
4. LLM with Rust

---

## 1. Hello World

```rust
fn main() {
    println!("Hello World!");
}
```

---

## 2. CRUD with _Poem_

---

## 3. Sistemas Embebidos 

---

## 4. LLMs with Rust

```rust
use auto_rust::llm_tool;
     
#[llm_tool]
// This function returns n^2 + 1 of a number
fn n_squared_plus_one(n: u64) -> u64 {
    todo!()
}
    
fn main() {
    let res = n_squared_plus_one(4);
    
    println!("{:?}", res);
}
```

---

## 4. LLMs with Rust

```bash
echo 'respuesta de auto-rust'
```

<!--
## slides
- tools: [mdBook](https://rust-lang.github.io/mdBook/index.html) probar mdSlides, [rust beam](https://lib.rs/crates/rust-beam), [rusty slider](https://ollej.github.io/rusty-slider/demo/example-slideshows.html#)
-->
