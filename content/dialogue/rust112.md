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

Learning computer science has felt like a blur. It's been getting harder to remember *when* I learned what I now know, so I figured I'd start a series on oxidizing the CS classes I've taken at CMU as a way of revisiting those classes while also making some educational Rust content.

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
    /* This
    is a multi-line
    comment */
    println!("Hello, World!");
    // println!("Goodbye, World!");
}
```

If we were to run this program, we would get the same greeting as before.

## Variables, Expressions, Scope

`let` is used to declare a variable. Declared variables can be assigned a value.

```rust
let x;
x = 5;

let y = 6; // This can also happen in one line. 
```

We typically use the second pattern for using variables. Declaring without assigning a value can potentially create uninitialized variables, which would cause an error.

Variable bindings are immutable by default. Trying to mutate an immutable variable will give an error when you try to compile.

```rust
let x = 5;
x = 4; // This line is problematic
```

Variables can be mutable using the `mut` keyword.

```rust
let mut x = 5;
x = 4; // This is now ok
```

<!-- Shadowing? -->

Variables exist within a scope. For example, here is a block:

```rust
let x = 5;
let y = {
    let x = 3; 
    x // x is 3 in here
}
x // x is still 5 out here
y // y is 3
```

Blocks are delineated by brackets. Blocks are expressions that can be reduced to a value.

```rust
let x = 5;          // This...
let x = 2 + 3;      // is of course the same as this...
let x = { 5 };      // but so is this...
let x = { 2 + 3 };  // which is the same as this.
```

**Further Reading:**
- [Variable Bindings](https://doc.rust-lang.org/rust-by-example/variable_bindings.html)

## Types

In previous examples we omitted giving types to our variables. This is because the computer infers the types of variables if not given one.

All variables must have a type. Furthermore, all variables must be assigned values of the same type only. We can explicitly denote a variable's type with a colon.

```rust
let x: i32 = 5;
let y: u8 = 5;
```

`x` and `y` both contain the value 5, but `x` is a signed 32-bit integer whereas `y` is an unsigned 8-bit integer.

There are many different integer types, as well as multiple float types. They all vary in size (how many bits they use), but they're ultimately all just numbers. `i32` is generally good when you need to store a number.

Rust comes with a few more primitive types: the character type (`char`), the boolean type (`bool`), and the unit type (`()`).

Rust also has arrays and tuples, which are somewhat similar to lists and tuples in Python.

**Further Reading:**

- [Primitives - Rust by Example](https://doc.rust-lang.org/rust-by-example/primitives.html)

## Functions

Functions are declared using the fn

## Conditionals

## Loops

## Strings

## Tuples

## Arrays, Vectors, Slices

## Maps and Sets

## Structs

## Wrap Up
