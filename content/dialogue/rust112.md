+++
title = "Oxidizing 15-112"
date = "2022-08-20"
draft = true
[taxonomies]
Series = ["Oxidizing"]
Year = ["2022"]
[extra]
toc = true
+++

Learning computer science has felt like a blur. I've learned many things, but it's been getting harder to remember *when* I learned what I know, so I figured I'd start a series on oxidizing the CS classes I've taken at CMU as a way of revisiting those classes while also making some helpful content.

It's been two years since I took 15-112, Carnegie Mellon's infamous introductory computer science course. This article covers computer science at the 112 level — the absolute basics — but in Rust instead of Python. If you're a Carnegie Mellon student that recently finished 15-112 and you want to dip into Rust, this is for you.

## Basics

All Rust programs start within a `main` function.

```rust
fn main() {
    println!("Hello, World!");
}
```

Running this program, you'll see:

```text
Hello, World!
```

Comments can be used to annotate code with explanations. The computer ignores everything within comments.

```rust
fn main() {
    println!("Hello, World!");
    // println!("Goodbye, World!");
}
```

If we were to run this program, we would only get the same greeting.

## Variables

`let` is used to declare a variable. Declared variables can be assigned a value.

```rust
let x;
x = 5;

let y = 6; // This can also happen in one line
```

Variable bindings are immutable by default. Trying to mutate an immutable variable will give an error when you try to compile.

```rust
let x = 5;
x = 4; // This line will cause the program to panic
```

Bindings can be mutable using the `mut` keyword.

```rust
let mut x = 5;
x = 4; // This is now ok
```

<!-- Shadowing? -->

Variables exist within a scope.

```rust

```

## Types

In previous examples we omitted giving types to our variables. This is because the computer infers the types of variables if not given one.

All variables must have a type. We can explicitly denote a variable's type with a colon.

```rust
let x: i32 = 5;
let y: u8 = 5;
```

`x` and `y` both contain the value 5, but `x` is a signed 32-bit integer whereas `y` is an unsigned 8-bit integer.



## Functions

## Conditionals

## Loops

## Strings

## Arrays, Vectors, Slices

## Maps and Sets

## Recursion

## Wrap Up

