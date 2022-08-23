+++
title = "Leetcode in Rust #000"
date = "2022-08-22"
draft = false
[taxonomies]
Series = ["Leetcode"]
Year = ["2022"]
+++

# [Problem 217. Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)

## Description

Given an integer array `nums`, return `true` if any value appears at least twice in the array, and return `false` if every element is distinct.


```
Examples

Input: nums = [1,2,3,1]
Output: true

Input: nums = [1,2,3,4]
Output: false

Input: nums = [1,1,1,3,3,4,3,2,4,2]
Output: true

Constraints:
1 <= nums.length <= 105
-109 <= nums[i] <= 109

```

```rust
impl Solution {
    pub fn contains_duplicate(nums: Vec<i32>) -> bool {
        ...
    }
}
```

## Solving

To see if an element appears twice in an array, we probably need to look at every element of the array at least once, meaning the minimum time complexity is probably `O(n)`.
In plain English, I'd like to iterate over the elements while keeping track of what I've seen so far. If I come across a duplicate, I'd then immediately break and signal that I'd seen a duplicate.

```rust
use std::collections::HashSet;

impl Solution {
    pub fn contains_duplicate(nums: Vec<i32>) -> bool {
        let mut seen = HashSet::new();
        for x in nums {
            if seen.contains(&x) { return true; }
            else { seen.insert(x); }
        }
        return false;
    }
}
```

This is pretty much a literal, Rust translation of our English pseudocode. This solution makes use of Rust's standard hash set for `O(1)` insertion and retrieval.

However, a closer inspection of [`HashSet::insert`](https://doc.rust-lang.org/std/collections/struct.HashSet.html#method.insert) reveals that the method returns a `bool` of whether or not the element we wanted to insert was already in the set.
Using this fact, we can skip using `HashSet::contains` altogether.

```rust
...

    pub fn contains_duplicate(nums: Vec<i32>) -> bool {
        let mut seen = HashSet::new();
        for x in nums {
            if !seen.insert(x) { return true; }
        }
        return false;
    }

...
```

Computationally this is an improvement, since we're saving ourselves from an extra method call.

For a cleaner, more functional way of solving this, we can make use of [`Iterator::all`](https://doc.rust-lang.org/std/iter/trait.Iterator.html#method.all),
which checks if all of the iterator's elements satisfy some predicate (i.e. that every number inserted hasn't already been inserted before).

```rust
...

    pub fn contains_duplicate(nums: Vec<i32>) -> bool {
        let mut seen = HashSet::new();
        !nums.iter().all(|&x| seen.insert(x))
    }

...
```

This solution is elegant and written idiomatically in Rust.

An alternative to this solution would be to add all of the elements to a set and then check if the size of the set is less than the length of the array.
Since dupliates aren't added to sets, and difference in size lets us know that there are duplicates.
For this we can use the [`FromIterator`](https://doc.rust-lang.org/std/collections/struct.HashSet.html#impl-FromIterator%3CT%3E) trait for hash sets.

```rust
...

    pub fn contains_duplicate(nums: Vec<i32>) -> bool {
        let seen: HashSet<i32> = HashSet::from_iter(nums.clone());
        nums.len() != seen.len()
    }

...
```

While this solution *looks* just as clean as the previous one and may perform similarly in the worst case, the previous solution does better in the average case, where a duplicate may appear in the middle of an array. Adding all of the elements of an array to a set obviously touches every single element, but iterating while also adding elements to the set has the potential to break early.
