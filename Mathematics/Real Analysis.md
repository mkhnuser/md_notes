# Real Analysis

## Overview

Here I note my observations on Real Analysis based on Terence Tao's "Analysis" book, 4th edition.
Errata on the book can be found here:

https://teorth.github.io/tao-web/analysis-i.html

## Starting at the Beginning: the Natural Numbers

### Addition

The Five Peano Axioms allow one to define a set of natural numbers.

### Multiplication

Just as an increment operation gives rise to the addition,
addition gives rise to multiplication,
and finally multiplication gives rise to exponentiation.

## Set Theory

### Foundations

Tao defines a set as an unordered collection of elements.
Note that there is no claim about uniqueness of these elements;
a set `{3, 3, 3, 4, 4, 5}` is possible, but it possesses redundancy.

### Russell's Paradox

The chapter contains hard exercises on proving set theoretic axioms from axioms.

### Functions

...

### Images and Inverse Images

Understand: forward images and inverse images are defined for all functions,
not only for one-to-one correspondences.

Tao deduces the power set as a consequence of a more general axiom.
See Axiom 3.11 (Power Set Axiom).

The section contains exercises on proving axioms from other axioms.

### Cartesian Products

Remark 3.5.9 explains that an n-tuple is in fact a finite sequence.
Or, in other words, an ordered sequence of n elements.

### Cardinality of Sets

Cardinality of finite sets is discusses in this section.
A lot of enumerative combinatorics principles are proved here.

Exercise 3.6.6 is challenging.
Exercise 3.6.12 discusses permutations.

## Integers and Rationals

### The Integers

One has to define integers to perform an operation of subtraction.
a - b = c - d iff a + d = c + b.

### The Rationals

a/b = c/d iff a * d = c * b
The rational number equals to zero iff its numerator equals to zero.

### Absolute Value and Exponentiation

A first notion of epsilon and delta closeness is introduced.
Further, important results on inequalities are proved.

Pay special attention to Exercise 4.3.4 on proving inequalities.

### Gaps in the Rational Numbers

Discusses the principle of infinite descent which is similar to the WOP.

## Real Numbers

### Overview

Rational numbers are fine for algebra.
However, real numbers are needed for geometry and trigonometry.
Further, real numbers fill in the gaps of a rational number line.

Observe: to prove the epsilon-delta propositions,
Proposition 4.3.7 can sometimes be used.

### Cauchy Sequences

By definition, a sequence is meant to be infinite.
Proposition 5.1.11 assumes the existence of an object and then defines this object.

### Equivalent Cauchy Sequences

As Tao notes, if we are to define real numbers a limits of a sequence of rationals,
we need to understand when two sequences of rationals are equivalent.

Proposition 5.2.8 assumes the existence of an object and then defines this object.

### The Construction of the Real Numbers

Define a real number to be a limit of a Cauchy sequence of rational numbers.
Then two reals are equal iff their Cauchy Sequences are equivalent.
In this paragraph, the laws of algebra for reals are proved.

In this sense, every real number is an equivalence class.

    https://math.stackexchange.com/questions/4887565/proposition-5-4-9-analysis-i-terence-tao?rq=1
    https://math.stackexchange.com/questions/2825726/confusion-about-taos-construction-of-reals?rq=1

### Ordering the Reals

In this paragraph, the laws of order for reals are proved.
Proposition 5.4.8 proves that if x > y > 0, then the inverse operation reverses the order.
Corollary 5.4.10 proves a limit property.
Corollary 5.4.13 proves Archimedean property.

Overall, quite an important chapter on inequalities and limit properties.

### The Least Upper Bound Property

One of the main advantages of the real numbers is that
every non-empty upper-bounded subset of reals will have the least upper bound.

Page 100, an aside note, is plus infinity a number in extended R?
See Remark 5.5.11 on this as well.

Exercise 5.5.4 shows a proper Corollary 5.4.10 usage.

Hence, the continuous number line has been constructed.
