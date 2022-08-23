+++
title = "Leetcode in Rust #001"
date = "2022-08-05"
draft = true
[taxonomies]
Series = ["Leetcode"]
Year = ["2022"]
+++

# [Problem 155. Min Stack](https://leetcode.com/problems/min-stack/)

## Description

Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.

Implement the `MinStack` class:

- `new: fn() -> MinStack` initializes the stack object.
- `push: fn(&mut MinStack, i32) -> ()` pushes the element `val` onto the stack.
- `pop: fn(&mut MinStack) -> ()` removes the element on the top of the stack.
- `top: fn(&MinStack) -> i32` gets the top element of the stack.
- `getMin: fn(&MinStack) -> i32` retrieves the minimum element in the stack.

You must implement a solution with `O(1)` time complexity for each function.


```text
Example

Input
["MinStack","push","push","push","getMin","pop","top","getMin"]
[[],[-2],[0],[-3],[],[],[],[]]

Output
[null,null,null,null,-3,null,0,-2]
```

```rust
struct MinStack {
    ...
}

impl MinStack {

    fn new() -> Self { ... }
    
    fn push(&mut self, val: i32) -> () { ... }
    
    fn pop(&mut self) -> () { ... }
    
    fn top(&self) -> i32 { ... }
    
    fn get_min(&self) -> i32 { ... }

}
```

## Hold Up

This stack obviously makes no sense. 

Popping without getting back a value?
Peeking into and popping from an empty stack?

Let's make some changes so this problem is safer and more practical.

- `new: fn() -> MinStack` initializes the stack.
- `push: fn(&mut MinStack, i32) -> ()` pushes the element `val` onto the stack.
- `pop: fn(&mut MinStack) -> Option<i32>` removes and returns the top element of the stack, *if there is one*.
- `top: fn(&MinStack) -> Option<i32>` gets the top element of the stack, *if there is one*.
- `getMin: fn(&MinStack) -> Option<i32>` retrieves the minimum element in the stack, *if there is one*.

```rust
...

impl MinStack {

    fn new() -> Self { ... }
    
    fn push(&mut self, val: i32) -> () { ... }
    
    fn pop(&mut self) -> Option<i32> { ... }
    
    fn top(&self) -> Option<i32> { ... }
    
    fn get_min(&self) -> Option<i32> { ... }

}
```

## Solving

```rust
use std::cmp::min;

struct MinStack(Vec<i32, i32>);

impl MinStack {

    fn new() -> Self {
        MinStack(Vec::new())
    }
    
    fn push(&mut self, val: i32) -> () {
        let next_min = 
    }
    
    fn pop(&mut self) -> Option<i32> { ... }
    
    fn top(&self) -> Option<i32> { ... }
    
    fn get_min(&self) -> Option<i32> { ... }

}
```
