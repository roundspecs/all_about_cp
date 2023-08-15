---
title: All about CP
header-includes: |
  \usepackage{amsmath}
toc: true
toc-depth: 2
toc-title: Table of Content
mainfont: NotoSerif-Regular.ttf
mainfontoptions:
- BoldFont=NotoSerif-Bold.ttf
- ItalicFont=NotoSerif-Italic.ttf
- BoldItalicFont=NotoSerif-BoldItalic.ttf
monofont: Inconsolata.ttf
colorlinks: true
linkcolor: #3498DB
urlcolor: #3498DB
toccolor: darkgray
geometry: b5paper,margin=1in
output: pdf_document
---
\pagebreak
# Development
This book is publicly developed on [GitHub](https://github.com/roundspecs/all_about_cp). If you find anything confusing, or you think that there is a better way to express the idea, please make a pull request.

### Contribution {-}
- Avoid comments: Name your variables and functions elaborately, instead
- Set indentation to two spaces
- Keep it concise

Specific to C++:

- Make sure your code supports C++17 standard
- Use `ll` instead of `long long`

\pagebreak
# Fast I/O
## C++
This will save you from TLEs in many problems
```{.cpp}
cin.tie(0) -> sync_with_stdio(0);
```
**Caution:** Either use `printf`/`scanf`, or use `cin`/`cout` with fast I/O. But don't use both
</div>

## Python
```py
# TODO: Insert code here @sorcerer_21
```

\pagebreak
# Language
## Return by reference
Lets define an array for demonstration:
```cpp
int vals[] = {10, 12, 83, 122, 5, 34};
```
The following function returns the value of the i-th element
```cpp
int getVal(int i) {
  return vals[i];  
}
```
The following function returns a reference to the i-th element
```cpp
int& getRef(int i) {
  return vals[i];  
}
```
Demonstration:
```cpp
int x = getVal(2);
x++;                       // Doesn't change array
cout << getVal(2) << '\n'; // Output: 83
int y = getRef(2);
y++;                       // Changes array
cout << getVal(2) << '\n'; // Output: 84
```
**Practice:**

- [This code](https://leetcode.com/problems/combinations/submissions/1009238953/) causes TLE, but [this](https://leetcode.com/problems/combinations/submissions/1009256283/) gets AC

## Inner Functions

\pagebreak
# Maths

## Summation
### Identities

$\sum{c\times f(n)}=c\times \sum{f(n)}$, $c$ is constant

$\sum{(f(n)\pm g(n))}=\sum{f(n)}\pm \sum{g(n)}$

$\sum_{i=1}^n\sum_{j=1}^n{a_ib_j}=(\sum_{i=1}^n{a_i})(\sum_{j=1}^n{b_j})$\

**Practice:**

- [AtCoder ARC A - Simple Math](https://atcoder.jp/contests/arc107/tasks/arc107_a) 

\pagebreak
# String
## Big Integers
1. Take input as string
2. Reverse the string

\pagebreak
# Constructive Algorithm
## From A to B
Think out of the box: Convert from B to A instead

**Practice:**

- [CF1810 - Candies](https://codeforces.com/problemset/problem/1810/B)

\pagebreak
# Bit Manipulation
## Non-decimal Literal in C++
To express integers in number systems other than decimal, use the following prefixes:

| Base | Prefix |
| ---- | ------ |
| bin  | 0b     |
| hex  | 0x     |
| oct  | 0      |

```cpp
assert(13 == 0b1101);
assert(13 == 0xd);
assert(13 == 015);
```

## How integers are stored
Integers are stored as blocks of bytes

| Data Type | No. of Bytes |
| --------- | ------------ |
| char      | 1            |
| short     | 2            |
| int       | 4            |
| long long | 8            |

## I/O with Non-Decimal Numbers
```cpp
int x;
cin >> hex >> x;  // takes input in hex
cout << hex << x; // prints output in hex
cin >> oct >> x;  // takes input in oct
cout << oct << x; // prints output in oct
cin >> dec >> x;  // takes input in dec
cout << dec << x; // prints output in dec

bitset<32> b;
cin >> b;         // takes 32 bit input in bin
cout << b;        // prints 32 bit output in bin
cout << b.to_ulong();
```

## Signed and Unsigned Integers
Positive integers (both signed and unsigned) are just represented with their binary digits, and negative signed numbers (which can be positive and negative) are usually represented with the Two's complement ^[[cp-algorithms - bit manipulation](https://cp-algorithms.com/algebra/bit-manipulation.html)]
```cpp
cout << bitset<3>(5) << "\n";
// Output: 101
cout << bitset<32>(-1) << "\n";
// Output: 11111111111111111111111111111111
```

## Index of Bit
Bits in a bit string are indexed from right to left, starting with 0.
```
bit string: 1 0 1 1 0 1
index:      ... 3 2 1 0
```
In this text, i-th bit means bit with index i.

## Terminologies
| Terms                             | Meaning                                                                               |
| --------------------------------- | ------------------------------------------------------------------------------------- |
| **Set bit**                       | Make the bit 1                                                                        |
| **Unset/Clear bit**               | Make the bit 0                                                                        |
| **Flip bit**                      | Make the bit opposite                                                                 |
| **Lower bit/**<br> **Higher bit** | i-th bit is lower that j-th bit if `i<j`<br>MSB is highest bit, LSB is the lowest bit |

## Thinking in Binary
**Fun fact:** Bit stands for "Binary Digit"

### Position of bits
Every position in a binary number has an index as mentioned [here](#index-of-bit).\
Each position also has a positional value: $2^{index}$\
Here is an example:
```
bit string:  0 1 1 0 1
index:       4 3 2 1 0
value:      16 8 4 2 1
```

### Converting to Decimal
To find decimal representation, we have to add up the positional values of set bits\
As an example, lets convert `0b1101` to decimal:
```
bit string: 1 1 0 1
index:      3 2 1 0
value:      8 4 2 1
```
Therefore, `0b1101` in decimal is -\
$8\times 1+4\times 1+2\times 0+1\times 1$\
$=8+4+1$\
$=13$

### Maximizing/Minimizing bitstrings
Bit string, `A` is greater than `B` if:
- Length of binary representation of A is greater than that of B (ignoring leading zeros)
- If their lenghts are equal, then in the first position where they differ, `A` has `1` and `B` has `0`.

This idea is important to solve problems related to maximizing/minimizing number with binary operations

These problems can be reduced to the following pattern:
You are given a number `n`. Do some bitwise operations on `n` such that `n` is maximized.

The idea behind this pattern of problems is that you have to maximize the length of the bitstring (without leading zeros) and set more significat bits that are unset

## NOT
| Operation | Meaning               |
| --------- | --------------------- |
| `~x`      | 1's complement of `x` |
| `~x+1`    | 2's complement of `x` |
### `-x` in terms of `~x`
``` cpp
assert(-x == ~x+1);
```

## XOR
### How to Visualize XOR
### Method-1: Non-equivalence Operator {-}

`A^B` is `true` if truth value of `A` and `B` are different.\
The following function uses this algorithm:
```cpp
bool xor(bool a, bool b) {
  if (a!=b)
    return true;
  return false;
}
```

### Method-2: Programmable Inverter {-}
Think of XOR as a machine with an on/off button, that takes one bit as input and one bit as output. If the machine is on, the ouput bit will be inverse of input bit, otherwise, the output bit will be the same as input bit.\
In `A^B`, one bit decides if the other should be flipped.\
The following function uses this algorithm:
```cpp
bool xor(bool a, bool b) {
  if (a)
    return !b;
  return b;
}
```

## XOR with AND OR
|  $A$ |  $B$ | $A\lor B$ | $A\land B$ | $A\oplus B$ |
| ---: | ---: | --------: | ---------: | ----------: |
|    0 |    0 |         0 |          0 |           0 |
|    0 |    1 |         1 |          0 |           1 |
|    1 |    0 |         1 |          0 |           1 |
|    1 |    1 |         1 |          1 |           0 |

From the truth table it is clear that:\
$A\oplus B=(A\lor B)-(A\land B)$\
$A\oplus B=(A\lor B)\land \lnot(A\land B)$

This is also valid for bitwise operations:\
`a^b=(a|b)-(a&b)`\
`a^b=(a|b)&~(a&b)`

## Thinking of Bitwise Operators: Fixing one operand
### AND
| Operation | Meaning |
| --------- | ------- |
| `& 1`     | same    |
| `& 0`     | 0       |
### OR
| Operation | Meaning |
| --------- | ------- |
| `         | 1`      | 1    |
| `         | 0`      | same |
### XOR
| Operation | Meaning |
| --------- | ------- |
| `^ 1`     | flip    |
| `^ 0`     | same    |

## Visualizing n-1
When we substract 1 from a number, the rightmost set bit becomes unset and all the bits to its right becomes set
```
n   = xxxx10000
n-1 = xxxx01111
```
There for value of a binary number with all 1s of length n is $2^n-1$

## Common Bit Operations and Checks
### Parity Check
If `n` is an integer(positive or negative) then `n&1` represent parity of `n`. It is similar to `n%2` but better, because unlike `n%2`, `n&1` works for both positive and negative numbers.
```cpp
int n;
n = 5;
assert((n & 1) == 1);
assert((n % 2) == 1);
n = -5;
assert((n & 1) == 1);
assert((n % 2) == -1);
```
In general, `x % (1<<k)` is equivalent to `x & (1<<k)-1`

### Left Shift as $\times 2$
`x<<y` is equivalent to $x\times 2^y$
```cpp
assert((5<<2) == 20);
```

### Right Shift as $\div 2$
`x>>y` is equivalent to $\lfloor \frac{x}{2^y} \rfloor$
```cpp
assert((11>>2) == 2);
```

### Set i-th Bit
OR with a number with only i-th bit set
```cpp
n = n | (1<<i)
```

### Clear i-th Bit
AND with a number with only i-th bit unset
```cpp
n = n & ~(1<<i)
```

### Flip i-th Bit
We already discussed that, XOR works as a programmable inverter.
```cpp
n = n ^ (1<<i)
```

### Check i-th Bit
AND with a number with only i-th bit set
```cpp
n & (1<<i)
```
There is a chance of making overflow of bits, if `n` is of type `long long`. In general, it is better to write it this way:
```cpp
(n>>i) & 1
```

### Unset Rightmost Set Bit
See [Visualizing `n-1`](#visualizing-n-1)
```cpp
n & (n-1)
```

### Check if Power of Two
`n` is power of two, if there is only one set bit. To check if there is only one set bit, unset the last set bit, and check if it becomes zero or greater. If it becomes zero its a power of two
```cpp
n!=0 && (n&(n-1))>0;
```
**Edge Case:** 0

### Count Set Bits: Brian Kernighan's Algorithm
The idea is to count how many times we can unset the rightmost set bit, until we reach 0
```cpp
int countSetBits(int n) {
  int cnt=0;
  while(n)
    n = n & (n-1), cnt++
  return cnt;
}
```

### Set Range of bits
The concept is similar to setting i-th bit, except we will use a different bit mask.\
`1<<i` is i 0s after one 1\
`(1<<i)-1` is i 1s at the end, and rest are 0s\
Now we can leftshift these 1s to fit into the range
```cpp
// Set bits in the range [start, stop)
int setRange(int n, int start, int stop) {
  int length = stop - start;
  int mask = (((1<<length) - 1) << start);
  return n | mask;
}
```

### Clear Range of bits
```cpp
int clearRange(int n, int start, int stop) {
  int length = stop - start;
  int mask = ~(((1<<length) - 1) << start);
  return n & mask;
}
```


### Flip Range of bits
```cpp
int flipRange(int n, int start, int stop) {
  int length = stop-start;
  int mask = (((1<<length) - 1) << start);
  return n ^ mask;
}
```

## Builtin Functions
The g++ compiler provides the following functions for counting bits:\

- `__builtin_clz(x)`:<br> the number of zeros at the beginning of the number
- `__builtin_ctz(x)`:<br> the number of zeros at the end of the number
- `__builtin_popcount(x)`:<br> the number of ones in the number
- `__builtin_parity(x)`:<br> the parity (even or odd) of the number of ones

The functions can be used as follows:
```cpp
int x = 5328; // 00000000000000000001010011010000
cout << __builtin_clz(x) << '\n';       // 19
cout << __builtin_ctz(x) << '\n';       // 4
cout << __builtin_popcount(x) << '\n';  // 5
cout << __builtin_parity(x) << '\n';    // 1
```
While the above functions only support `int` numbers, there are also long long
versions of the functions available with the suffix ll.\
Source: [CSES Book](https://cses.fi/book/index.php)

## Sum with bit operations ##
`a&b` represents the carry bit and `a^b` represents the last digit of `a+b`. Therefore the following formula holds:
```cpp
a + b = ((a & b) << 1) + (a ^ b)
```

Since, `a ^ b` can be written in terms of AND, OR the sum can also be written in terms of AND, OR
```cpp
a + b = ((a & b) << 1) + (a ^ b)
      = 2 * (a & b) + (a | b) - (a & b) 
      = (a & b) + (a | b)
```

Practice: [CF](https://codeforces.com/contest/1556/problem/D)

\pagebreak
# Ranges
## Multiple Ranges 
### Intersections of ranges    
There are n ranges $[l_1,r_1],[l_2,r_2],[l_3,r_3],...[l_n,r_n]$\
Now, the intersections of these ranges is $[L,R]$,where\
$L=\max_{i=1}^n l_i$\
$R=\min_{i=1}^n r_i$\

**Edge Case:**\
If $R<L$ , then the intersection is an empty range.

**Practice:**

- [CF1282A - Temporarily unavailable](https://codeforces.com/problemset/problem/1282/A)
- [CF124A - The number of positions](https://codeforces.com/problemset/problem/124/A)
- [CF714A - Meeting of Old Friends](https://codeforces.com/problemset/problem/714/A)

\pagebreak
# Interactive Prpblem
Make a function called ask that takes the parameters of the question as parameter and returns the return value of the question

Example:
```cpp
int ask(string s, int a, int b) {
  cout << s << ' ' << a << ' ' << b << '\n';
  cout << flush;
  int res;
  cin >> res;
  return res;
}
```

\pagebreak
# Big Integers
If N is a very large number (containing more than **40** digits), then **N should be read as string**.

## Divisibility of Integer N
***N is***

1. Always divisible by 1.

2. Dibisible by 2 if the last digit of N is divisible by 2 i.e., last digit is even.

3. Divisible by 3 if sum of digits is divisible by 3.

4. Divisible by 4 if the number containing only the last two digits of N is divisible by 4.

5. Divisible by 5 if last digit is 0 or 5.

6. Divisible by 6 if it is divisible by both 2 and three i.e.,last digit is even and the sum of all digits is divisible by 3.

\pagebreak
# Number Theory
## Binary Exponentiation ##
$$
x^n=
  \begin{cases}
      1,&n=0\\
      x^{(n/2)}\cdot x^{(n/2)},&n\> \textrm{mod}\> 2=0 \\
      x^{(n-1)}\cdot x,&n\> \textrm{mod}\> 2=1\\
  \end{cases}
$$
**C++ Code:**
```cpp
ll binPow(ll x, ll n) {
  if (n == 0) return 1;
  ll z = modpow(x, n/2);
  z *= z;
  if (n & 1) return x * z;
  return z;
}
```
**Complexity:** $O(logn)$

## Modular Arithmetic ##
### Basic Modular Operations ###
**Modular Addition:**\
$(a+b)\> \textrm{mod}\> m = ((a\> \textrm{mod}\> m)+(b\> \textrm{mod}\> m))\> \textrm{mod}\> m$

**Modular Multiplication**\
$(a\times b)\> \textrm{mod}\> m = ((a\> \textrm{mod}\> m)\times (b\> \textrm{mod}\> m))\> \textrm{mod}\> m$

### Modular Exponentiation ###
**Calculate $x^n$ % m :**\
$$
x^n\> \textrm{mod}\> m=
  \begin{cases}
      1\> \textrm{mod}\> m,&n=0\\
      ((x^{n/2} \> \textrm{mod}\> m)\cdot(x^{n/2}\mod{m}))\> \textrm{mod}\> m,&n\> \textrm{mod}\> 2=0 \\
      ((x^{n/2}\mod{m})\cdot(x\> \textrm{mod}\> m))\> \textrm{mod}\> m,&n\> \textrm{mod}\> 2=1\\
  \end{cases}
$$
```cpp
ll modPow(ll x, ll n, ll m) {
  if(n == 0) return 1 % m;
  ll z = modpow(x, n/2, m) % m;
  z = (z * z) % m
  if (n & 1) return ((x % m) * z) % m;
  return z;
}
```
**Complexity:** $O(logn)$

\pagebreak
# Regular Expression #
## Matching Substring ##
Calculate how many times a certain pattern appears in a string(with duplicates).\
[**Problem-1:**](https://toph.co/p/nobita-and-shizuka)\
The pattern starts and ends with 1, and there are one or more 0s in-between. \
**C++ code:**
```cpp
#include <bits/stdc++.h>
#include <regex>
using namespace std;
int countSubstrings(const string &s) {
  regex pattern("(?=(10+1))");
  sregex_iterator iter(s.begin(), s.end(), pattern);
  sregex_iterator end;
  int count = 0;
  while (iter != end) {
    ++count;
    ++iter;
  }
  return count;
}
```
**Python Code:**
```py
def countSubstrings(s):
  pattern = r'(?=(10+1))'
  matches = finditer(pattern, s)
  count = 0
  for match in matches: count+=1
  return count
```
Now, if we want only the unique substrings we can store those substrings in a set.\
**C++ Code:**
```cpp
set<string> uniqueSubstrings; 
while (iter != end){
  uniqueSubstrings.insert((*iter)[1]);
  ++iter;
}
```
**Python Code:**
```py
uniqueSubstrings = set()
for match in matches:
  uniqueSubstrings.add(match.group(1))
```
*The size of the set **uniqueSubstrings** is the number of unique substrings that matches the pattern.*
