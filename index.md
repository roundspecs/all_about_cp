---
title: All about CP
toc-title: Table of Content
---

# Development
This book is publicly developed on GitHub. If you find anything confusing, or you think that there is a better way to express the idea, please make a pull request.

# Bit Manipulation
## XOR
### How to visualize XOR
#### Method-1: Non-equivalence Operator
$A\oplus B$ is $true$ if truth value of $A$ and $B$ are different
```{.cpp .numberLines}
bool xor(bool a, bool b) {
  if (a!=b)
    return true;
  return false;
}
```
#### Method-2: Programmable Inverter
Think of XOR as a machine with an on/off button, that takes one bit as input and one bit as output. If the machine is on, the ouput bit will be inverse of input bit, otherwise, the output bit will be the same as input bit.\
In $A\oplus B$, one bit decides if the other should be flipped.
```{.cpp .numberLines}
bool xor(bool a, bool b) {
  if (a)
    return !b;
  return b;
}
```