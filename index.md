---
title: All about CP
toc-title: Table of Content
---

# Development
This book is publicly developed on GitHub. If you find anything confusing, or you think that there is a better way to express the idea, please make a pull request.

# FastIO
## The magic line
```{.cpp .numberLines}
cin.tie(0)->sync_with_stdio(0);
```

# Bit Manipulation
## Binary literal in C++
You can represent binary numbers in C++ by using the `0b` prefix.\
For example: $13$ in binary is `0b1101`.
```{.cpp .numberLines}
assert(13 == 0b1101);
```
## Signed and Unsigned Integers
Positive integers (both signed and unsigned) are just represented with their binary digits, and negative signed numbers (which can be positive and negative) are usually represented with the Two's complement ^[[cp-algorithms - bit manipulation](https://cp-algorithms.com/algebra/bit-manipulation.html)]

## XOR
### How to visualize XOR
#### Method-1: Non-equivalence Operator {-}
$A\oplus B$ is $true$ if truth value of $A$ and $B$ are different.\
The following function uses this algorithm:
```{.cpp .numberLines}
bool xor(bool a, bool b) {
  if (a!=b)
    return true;
  return false;
}
```
#### Method-2: Programmable Inverter {-}
Think of XOR as a machine with an on/off button, that takes one bit as input and one bit as output. If the machine is on, the ouput bit will be inverse of input bit, otherwise, the output bit will be the same as input bit.\
In $A\oplus B$, one bit decides if the other should be flipped.\
The following function uses this algorithm:
```{.cpp .numberLines}
bool xor(bool a, bool b) {
  if (a)
    return !b;
  return b;
}
```
