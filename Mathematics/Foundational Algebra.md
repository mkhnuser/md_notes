# Foundational Algebra

## Function nomenclature

1. Power functions - `x ** 2` - степенные функции;
2. Exponential functions - `2 ** x` - показательные функции;
3. Root functions are inverses to power functions;
4. Logarithmic functions are inverses to exponential functions.

## Roots

### Root properties

Understand: the nth root properties are proven for non-negative bases.
One can use the nth root properties for any real numbers if n is odd.
However, when n is even, the domain restriction can happen.

See Mordkovich Algebra, 11th grade, Page 47-48 and exercise 6 after the chapter.
See domain restriction on logarithms for similarities.

### Rational Exponent

#### Rational Exponent definition

The expression `a ** (p / q)` makes sense if `a >= 0`.
The expression `a ** -(p / q)` makes sense if `a > 0`.
Obviously, the domain restriction also applies to equations and inequalities.

See Mordkovich Algebra, 11th grade, Page 54-55.
See Mordkovich Algebra, 11th grade, Page 56, example 1 on the important of restriction on the base `a >= 0`.
See Mordkovich Algebra, 11th grade, Page 58, example 3 on the important of restriction on the base `a >= 0`.

### Domain restriction on expressions

When someone writes the even root of `x`, it's implied that `x >= 0`.
Similarly, if someone writes `a ** (1/3)`, `a >= 0` is implied, etc.

See Mordkovich Algebra, 11th grade, the top of Page 52.
See Mordkovich Algebra, 11th grade, the top of Page 57, example 2.

## Logarithms

### Overview

Logarithms are defined only for positive numbers
since logarithmic functions are inverse functions for exponential ones.
Also, because logarithms are inverses to exponential functions,
bases of logarithms must be positive numbers not equal to one.

### Domain restriction

A graphical approach to algebra and trigonometry, Section 5.4, Exercise 51.
It's important to ensure that an argument to a logarithm function is always positive;
one should use modulus for this.

https://math.stackexchange.com/questions/3732407/logarithm-power-rule-does-not-provide-a-complete-solution-have-the-logarithm-ru
See Mordkovich Algebra, 11th grade, Page 47-48 for examples on roots.

### Inverses to Logarithms

A graphical approach to algebra and trigonometry, Section 5.4.
Contains exercises for finding inverse functions for logarithms and exponential functions.

### Applications of Logarithms

See A graphical approach to algebra and trigonometry, Section 5.6, for applications of logarithms.

## Logical equivalences of equations

You can say that `a = b` is logically equivalent to `a ** n = b ** n`,
if `n > 0` is an odd natural number since functions `x ** n` for positive odd `n` are one-to-one.

However, functions `x ** n` for `n` positive even `n` are not one-to-one,
and so there is no logical equivalence, but rather a mere implication.

Be careful double check the roots you obtain for an even case.
Recall: you can visualize this process using the graphs of `x ** 2` and `x ** 3`.
Pictorially:

    a = b iff a ** 3 = b ** 3.
    a = b => a ** 2 = b ** 2.

## Logical equivalences of inequalities

Pictorially:

    a ** 3 < b ** 3 iff a < b.
    a ** 2 < b ** 2 => |a| < |b|.

A generalization to any positive `n` is permissible.

Note that it's wrong to say:

    a ** 2 < b ** 2 => a < b.

Choose `a = -2` and `b = -3` to serve as counterexamples.
