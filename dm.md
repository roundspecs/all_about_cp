---
title: Discrete Mathematics
toc-title: Table of Content
---

# Proposition
**Definition:** A statement that can is either true or false

Examples of proposition:

- 3+2=4

- 1+1=2

- Elephants can fly

Examples of statements that are not proposition:

- Bring me a glass of water

- Is the window open?

- This statement is false

## Problem with human languages
Languages like English and Bengali are okay for normal conversations but they are to precise enough for mathematics. Lets see an example:

"Take a lalmohon or kalojam"\
Does that mean I can take both? Or, just one?

Confusing right? That is why we have to learn some symbols and definitions to ensure that there is no ambiguity.

## Propositional Variable
**Definition:** A variable that represents a proposition

Example:\
P = Elephants can fly\
P is false

Conventionally, we use letters: p,q,r,s to represent propositional variables

# Compound Proposition
**Definition:** New proposition formed from existing proposition(s) using logical operator(s)

George Boole first discussed about compound proposition in his book, "The laws of Thought"

## Not
Negation of $P = \neg P$

| $P$ | $\neg P$ |
|-----|----------|
| T   | F        |
| F   | T        |

Example:\
If $P=$ Birds can fly\
then, $\neg P=$ Birds can't fly

## Conjunction/And
Conjunction of $P$ and $Q = P\land Q$

$P\land Q$ is true, only if both $P$ and $Q$ are true

| $P$ | $Q$ | $P\land Q$ |
|-----|-----|------------|
| T   | T   | T          |
| T   | F   | F          |
| F   | T   | F          |
| F   | F   | F          |

Example:\
If $P=$ Roses are red and $Q=$ Violets are blue\
then, $P\land Q=$ Roses are red and violets are blue

## Disjunction/Or
Disjunction of $P$ and $Q = P\lor Q$

$P\lor Q$ is true, if at least one of $P$ and $Q$ is true and false otherwise

| $P$ | $Q$ | $P\lor Q$ |
|-----|-----|------------|
| T   | T   | T          |
| T   | F   | T          |
| F   | T   | T          |
| F   | F   | F          |

Example:\
If $P=$ Roses are red\
then, $P\lor\neg P=$ Roses are red or roses are not red

## Exclusive OR
Exclusive OR of $P$ and $Q = P\oplus Q$

$P\oplus Q$ is true, if only one of $P$ and $Q$ is true and false otherwise

| $P$ | $Q$ | $P\oplus Q$ |
|-----|-----|-------------|
| T   | T   | F           |
| T   | F   | T           |
| F   | T   | T           |
| F   | F   | F           |

Example:\
If $P=$ Roses are red\
then, $P\lor\neg P=$ Either roses are red or roses are not red


## Implication
$P$ imples $Q = P\implies Q$

$P\implies Q$ is false, if $P$ is true and $Q$ is false and true otherwise

| $P$ | $Q$ | $P\oplus Q$ |
|-----|-----|-------------|
| T   | T   | T           |
| T   | F   | F           |
| F   | T   | T           |
| F   | F   | T           |

Think of implication as a contract.

Example:\
If $P=$ I get elected and $Q=$ I will plant trees\
then, $P\implies Q=$ If I get elected, then I will plan trees

Terminologies:

- The *if-part* is called hypothesis/antecident/premise

- The *then-part* is called consequence/conclusion

## If and only if/IFF
$P$ IFF $Q = P\iff Q$

$P\iff Q$ means $P$ and $Q$ are logically equivalent

| $P$ | $Q$ | $P\iff Q$ |
|-----|-----|-------------|
| T   | T   | T           |
| T   | F   | F           |
| F   | T   | F           |
| F   | F   | T           |


Example:\
If $P$ is $x^2-4\ge 0$ and $Q$ is $|x|\ge 2$\
then, $P\iff Q=$ For some values of both $P$ and $Q$ are true and for others, both are false