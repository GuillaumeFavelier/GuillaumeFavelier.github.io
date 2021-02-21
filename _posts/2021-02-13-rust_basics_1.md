---
layout: post
title: "Rust Basics (1)"
date: 2021-02-13
desc: "Installation, hello_world and Cargo"
keywords: "rust,easy"
categories: [Rust]
tags: [Rust]
icon: icon-html
---

The goal of this post is to learn how to install the **necessary tools** to program in Rust,
compile a **minimal example** and learn the basics of **Cargo**.

*The following instructions are valid for Linux or macOS. For Windows, please refer to the [Rust documentation](https://doc.rust-lang.org/book/ch01-01-installation.html)*

## Installation

To install `rustup`:

```sh
curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
```

Once installed, Rust set of tools can be updated with:

```sh
rustup update
```

Or can be removed with:

```sh
rustup self uninstall
```
---

## Hello world

It's time for the first program in Rust!

Let's create our working directory first:

```sh
mkdir hello_world
cd hello_world
```

Then create a source file called `main.rs`:

```rust
fn main() {
    println!("Hello, world!");
}
```

It's possible to compile the code with:

```sh
rustc main.rs
```

And execute the **binary**:

```sh
./main
```

The following is expected:

```
Hello, world!
```
---

## Cargo

Cargo is Rust's **package manager**. To check the installed version:

```sh
cargo --version
```

To create a new project with Cargo, just enter:

```sh
cargo new hello_world
```

The command creates the project tree, initializes the **Git** repository
with `.gitignore`, adds the **TOML** config file `Cargo.toml` and
populates the `src` directory with a minimal `hello_world` source code.

Essential commands:

cmd | desc
----|-----
`cargo build` | Build the project (unoptimized + debug)
`cargo run` | Run the project (after compiling if necessary)
`cargo check` | Ensure that the source code compiles

To build the optimized/release target, enter:

```sh
cargo build --release
```
---

## Source code

Material for this post is available on [GitHub](https://github.com/GuillaumeFavelier/blog_rust_basics_1).

*[Go to the next post of the serie.](https://guillaumefavelier.github.io/rust/2021/02/21/rust_basics_2.html)*
