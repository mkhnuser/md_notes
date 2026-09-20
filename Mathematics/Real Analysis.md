# Real Analysis

## Overview

Here I note my observations on Real Analysis based on Terence Tao's "Analysis" book, 4th edition.
https://teorth.github.io/tao-web/analysis-i.html

## Progress

* The book has been started on Aug 18, 2026.
* The first five chapters, which construct the number line, have been finished on Sep 20, 2026.

## Starting at the Beginning: the Natural Numbers

### Addition

The Five Peano Axioms give rise to a set of natural numbers.

### Multiplication

Incrementation -> Addition -> Multiplication -> Exponentiation.

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
Lemma 5.1.15 asserts that every Cauchy Sequence is bounded.

### Equivalent Cauchy Sequences

Proposition 5.2.8 assumes the existence of an object and then defines this object.

### The Construction of the Real Numbers

Define a real number to be a limit of a Cauchy sequence of rational numbers.
Then two reals are equal iff their Cauchy Sequences are equivalent.
In this paragraph, the laws of algebra for reals are proved.

In this sense, every real number is an equivalence class.

    https://math.stackexchange.com/questions/4887565/proposition-5-4-9-analysis-i-terence-tao?rq=1
    https://math.stackexchange.com/questions/2825726/confusion-about-taos-construction-of-reals?rq=1

Exercise 5.3.5 shows that a limit of n approaching infinity of 1 over n equals zero.

### Ordering the Reals

Proposition 5.4.8 proves that if x > y > 0, then the inverse operation reverses the order.

Proposition 5.4.9 says that if a Cauchy Sequence is entirely non-negative,
then its limit is a non-negative real number.

Corollary 5.4.10 proves a limit property:
if terms of one Cauchy Sequence greater than or equal to the terms of the other,
then the limit of the first is greater than or equal to the limit of the other.

Proposition 5.4.12 proves that given a positive real x,
there will be a rational q < x and there will be a positive integer N > x.

Corollary 5.4.13 proves Archimedean property.

Proposition 5.4.14 proves that given any two reals, there is a rational between them.

Now we can use the usual order on reals.

### The Least Upper Bound Property

One of the main advantages of the real numbers is the presence of the supremum.
Every non-empty upper-bounded subset of reals will have the l.u.b.

Exercise 5.5.4 shows a proper Corollary 5.4.10 usage.
Exercise 5.5.5 extends Proposition 5.4.14
by saying that given any two reals, there is a real between them.

### Real Exponentiation

Definition 5.6.4 defines an nth root of a non-negative real x.
Observe: Tao explicitly notes that nth roots are defined for a non-negative arguments in his text.

Lemma 5.6.6 and Lemma 5.6.9 present a number of important inequalities.

Now we can assume usual laws of algebra, order, and exponentiation for reals.
