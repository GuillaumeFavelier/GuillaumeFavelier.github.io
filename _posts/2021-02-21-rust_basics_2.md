---
layout: post
title: "Rust Basics (2)"
date: 2021-02-21
desc: "Function and control flow"
keywords: "rust,easy"
categories: [Rust]
tags: [Rust]
icon: icon-html
---

The goal of this post is to learn how to **define a function** and **control instructions flow**.

## Function

A good example of a simple function is in the `hello_world` project described in the [previous post](https://guillaumefavelier.github.io/rust/2021/02/13/rust_basics_1.html):

```rust
fn main() {
    println!("Hello, world!");
}
```

Notice the `fn` keyword to start the definition of the function. But in this example,
`main()` does not accept arguments nor return anything.

Maybe a more interesting example would be a function that generates a random integer
in a range:

```rust
fn get_secret_number(nmin: i32, nmax: i32) -> i32 {
    use rand::Rng;
    // gen_range(low, high) is inclusive of low but exclusive of high
    return rand::thread_rng().gen_range(nmin, nmax + 1);
}
```
> `rand` is an external package so the `[dependencies]` section of the `Cargo.toml` configuration file needs
> to be updated like so:
> ```
> ...
> [dependencies]
> rand = "0.6.0"
> ```

This function accepts two arguments called `nmin` and `nmax` of type `i32` (signed integer that takes 32 bit of space)
and its return type is specified after the arrow `-> i32`.

In the above example, the result is returned explicitly with `return` but in Rust, the return value of
the function is synonymous with the value of the final expression. Meaning that `get_secret_number()`
can be modified as follows:

```rust
fn get_secret_number(nmin: i32, nmax: i32) -> i32 {
    use rand::Rng;
    rand::thread_rng().gen_range(nmin, nmax + 1)
}
```

Please note that with this syntax, the semicolon `;` is removed to prevent the expression to become a 
**statement** (which *does not* return a value).

Here is a complete example:

```rust
fn get_secret_number(nmin: i32, nmax: i32) -> i32 {
    use rand::Rng;
    rand::thread_rng().gen_range(nmin, nmax + 1)
}

fn main() {
    let secret_number = get_secret_number(1, 100); // function call here!
    println!("The secret number is {}.", secret_number);
}
```

---

## Control Flow

In Rust, branching is mainly done with the keyword `if`, the block of code that follows
is executed only if the described condition is evaluated to `true`:

```rust
fn strip_line(line: &mut String) {
    // enter the code block only if the last character of the String is '\n'
    if line.ends_with("\n") {
        line.pop(); // remove this last character '\n'
        // enter the code block only if the last character of the String is '\r'
        if line.ends_with("\r") {
          line.pop(); // and remove this last character '\r'
        }
    }
}
```

Multiple instruction branches can be chained together with the keywords `else if` and `else`:

```rust
fn main() {
    let secret_number = get_secret_number(1, 100);
    let guess = 50;
    if guess < secret_number {
        println!("The secret number is greater.");
    }
    else if guess > secret_number {
        println!("The secret number is lower.");
    }
    else {
        println!("Congratulations! The secret number {} is found.", guess);
    }
}
```

A particular Rust mechanic can simplify the code above. It's called **pattern matching**
and it is based on the **match** keyword. Please note that each matching arm is evaluated
and *all possible values must be covered*:

```rust
fn main() {
    let secret_number = get_secret_number(1, 100);
    let guess = 50;
    // the cmp() function returns an Ordering enumeration
    match guess.cmp(&secret_number) {
        std::cmp::Ordering::Less => println!("The secret number is greater."),
        std::cmp::Ordering::Greater => println!("The secret number is lower."),
        std::cmp::Ordering::Equal => println!("Congratulations! The secret number {} is found.", guess),
    };
}
```
> An `Enum` in its simplest form holds a set of mutually exclusive values:
> ```rust
> Enum Ordering {
>     Less,
>     Greater,
>     Equal,
> }
> ```

---

## Reference

Material for this post is available on [GitHub](https://github.com/GuillaumeFavelier/blog_rust_basics_2).

More infos on the [Rust documentation](https://doc.rust-lang.org).

*Next post available soon.*
