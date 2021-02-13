---
layout: post
title: "Rust Basics (1)"
date: 2021-02-13
desc: "Installation, hello_world"
keywords: "rust,easy"
categories: [Rust]
tags: [Rust]
icon: icon-html
---

*The following instructions are valid for Linux*

### Installation

To install `rustup`:

```sh
curl --proto '=https' --tlsv1.2 https://sh.rustup.rs -sSf | sh
```

Once installed, Rust tools can be updated with:

```sh
rustup update
```

Or can be removed with:

```sh
rustup self uninstall
```

### Hello world

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

And execute the binary:

```sh
./main
```

The following is expected:

```
Hello, world!
```

---
