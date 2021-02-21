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

The goal of this post is to learn how to define a function and control logic flow.

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
    return rand::thread_rng().gen_range(nmin, nmax + 1);
}
```

This function accepts two arguments called `nmin` and `nmax` of type `i32` (signed integer that takes 32 bit of space)
and its return type is specified after the arrow `-> i32`.

In the above example, the result is returned explicitly with `return` but in Rust, the return value of
the function is synonymous with the value of the final expression. Meaning that `get_secret_number()`
can be modified as follows:

```rust
fn get_secret_number(nmin: i32, nmax: i32) -> i32 {
    use rand::Rng;
    // gen_range() is inclusive of nmin but exclusive of nmax
    rand::thread_rng().gen_range(nmin, nmax + 1)
}
```

> `rand` is an external package so the `[dependencies]` section of the `Cargo.toml` configuration file needs
> to be updated like so:
> ```
> ...
> [dependencies]
> rand = "0.6.0"
> ```

Please note that in this syntax, the semicolon `;` is removed to prevent the expression to become a 
statement.

Here is a more complete example:

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

## Source code

Material for this post is available on [GitHub](https://github.com/GuillaumeFavelier/blog_rust_basics_2).
