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

Decide conscientemente cuando tus

variables sean capaces de mutar

```rust
fn main() {
    let p = Point {x: 3.0, y: 4.2};
    
    //Error: cannot assign to `p.x`,
    //as `p` is not declared as mutable
    p.x = 13.0;
}
```

---

## Structs and Traits

```rust
struct Point {
    x: f32,
    y: f32
}
    
trait Quadrant {
    fn get_quadrant(self) -> QuadrantNum;
}
```

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

## Algebraic Typing

structures, enumerators

```rust
enum QuadrantNum {
    CENTER,
    I,
    II,
    III,
    IV
}
    
struct Point {
    x: f32,
    y: f32
}
```

---

##  

```rust
impl Quadrant for Point {
    fn get_quadrant(self) -> QuadrantNum {
        if self.x > 0.0 && self.y >= 0.0 {
            QuadrantNum::I
        } else if self.x <= 0.0 && self.y > 0.0 {
            QuadrantNum::II } else if self.x < 0.0 && self.y <= 0.0 {
            QuadrantNum::III
        } else if self.x >= 0.0 && self.y < 0.0 {
            QuadrantNum::IV
        } else {
            QuadrantNum::CENTER
        }
    }
}
```

---


## Pattern Matching = robustness

match, if let pattern

```rust
impl Point {
    fn show_quad(self) {
        match self.get_quadrant() {
            QuadrantNum::I => println!("Quadrant I"),
            QuadrantNum::II => println!("Quadrant II"),
            QuadrantNum::III => println!("Quadrant III"),
            QuadrantNum::IV => println!("Quadrant IV"),
            QuadrantNum::CENTER => println!("It's not in a quadrant"),
        }
    }
}
```

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

```rust
#[tokio::main]
async fn main() -> Result<(), std::io::Error> {
    if std::env::var_os("RUST_LOG").is_none() {
        std::env::set_var("RUST_LOG", "poem=debug");
    }
    tracing_subscriber::fmt::init();

    let api_service =
        OpenApiService::new(Api::default(), "Users", "1.0").server("http://localhost:3000/api");
    let ui = api_service.swagger_ui();

    Server::new(TcpListener::bind("0.0.0.0:3000"))
        .run(Route::new().nest("/api", api_service).nest("/", ui))
        .await
}
```

---

## 2. CRUD with _Poem_

```rust
#[derive(Default)]
struct Api {
    users: Mutex<Slab<User>>,
}
    
#[OpenApi]
impl Api {
    /// Create a new user
    #[oai(path = "/users", method = "post", tag = "ApiTags::User")]
    async fn create_user(&self, user: Json<User>) -> CreateUserResponse { ... }
    
    /// Find user by id
    #[oai(path = "/users/:user_id", method = "get", tag = "ApiTags::User")]
    async fn find_user(&self, user_id: Path<i64>) -> FindUserResponse { ... }
    
    /// Delete user by id
    #[oai(path = "/users/:user_id", method = "delete", tag = "ApiTags::User")]
    async fn delete_user(&self, user_id: Path<i64>) -> DeleteUserResponse { ... }
    
    /// Update user by id
    #[oai(path = "/users/:user_id", method = "put", tag = "ApiTags::User")]
    async fn put_user(&self, user_id: Path<i64>, update: Json<UpdateUser>) -> UpdateUserResponse { ... }
}
```

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
