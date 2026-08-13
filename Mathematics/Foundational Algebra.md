# Foundational Algebra

## Function nomenclature

1. Power functions - степенные функции;

        x ** (1/2), x ** -(2/3), x ** -14, x ** 3, etc.

        Understand:

        * if the exponent is a positive fraction,
        some texts impose restrictions on the base to be >= 0.
        * if the exponent is a negative fraction,
        some texts impose restriction on the base to be > 0.

2. Exponential functions - показательные функции;

        2 ** x, (1/2) ** x, etc.
        Understand: some texts impose restrictions on the base to be > 0 and != 1.
        The first part of the restriction comes from the definition of a rational exponent.
        The second part comes from a uselessness of a usage of 1 as the base.

3. Root functions are inverses to power ones;
4. Logarithmic functions are inverses to exponential ones.

## Roots

### Root properties

See Mordkovich Algebra, 11th grade, Page 47-48 and exercise 6 after the chapter.
See domain restriction on logarithms for similarities.

## Rational Exponent

### Rational Exponent Careful Definition

In some texts, the expression `a ** (p / q)` makes sense only if `a >= 0`.
In some texts, the expression `a ** -(p / q)` makes sense only if `a > 0`.
Obviously, the domain restriction has to be applied to equations and inequalities which contain these expressions.

See Mordkovich Algebra, 11th grade, Page 54-55.
See Mordkovich Algebra, 11th grade, Page 56, example 1 on the important of restriction on the base `a >= 0`.
See Mordkovich Algebra, 11th grade, Page 58, example 3.

Understand: some texts don't impose such a restriction
if the resulting root expression is not even,
so be especially careful with the definition of a rational exponent.

### Domain restriction on expressions

When someone writes the even root of `x`, it's implied that `x >= 0`.
Similarly, if someone writes `a ** (1/3)`, `a >= 0` is implied, etc.

See Mordkovich Algebra, 11th grade, the top of Page 52.
See Mordkovich Algebra, 11th grade, the top of Page 57, example 2.

## Exponential Functions

### Overview

One can consider exponential functions when an irrational exponent has been discussed.
That is, given the base `a`, one can examine a function `a ** x`, where `x` is any real number.
Some texts impose restrictions on the base to be > 0 and != 1: `a > 0 and a != 1`.

Observe that `a > 0`, and not just `a >= 0`,
to accommodate for a potential negative fraction in the exponent.

### Exponential Equations

Some texts impose restriction on the base of the equation to be > 0 and != 1: `a > 0 and a != 1`.
There are no restrictions on the exponent: it can be any real number.
To solve an exponential equation, arrive at the common base, and equate exponents.

### Exponential Inequalities

Some texts impose restriction on the base of the inequality to be > 0 and != 1: `a > 0 and a != 1`.
There are no restrictions on the exponent: it can be any real number.

To solve an exponential equation:

1. Arrive at the common base;
2. Consider a strategy depending on whether the base `0 < a < 1` or `a > 1`.

## Logarithmic functions

### Overview

Logarithmic functions are inverse functions to exponential ones.
Because of this, one must restrict:

1. The argument.

        The argument must be > 0.
        That's because exponential functions map onto positive reals.

2. The logarithm base.

        The base must be > 0 and != 1.
        That's because exponential functions impose restrictions on the base.

To summarize, log base a of b equals c <=> a ** c = b.

### Logarithmic Properties

Logarithmic properties (sum, difference, etc.) are proved for strictly positive arguments.
Notice that the root properties are proved for non-negative arguments.

### Inverses to Logarithms

A graphical approach to algebra and trigonometry, Section 5.4.
Contains exercises for finding inverse functions for logarithms and exponential functions.

### Applications of Logarithms

See A graphical approach to algebra and trigonometry, Section 5.6, for applications of logarithms.

## Domain restrictions

It's important to ensure that an argument to a logarithm function is always positive.
It's important to ensure that an argument to an even root is non-negative.
One should use modulus for this or an explicit domain restriction.

See Mordkovich Algebra, 11th grade, Page 47-48 for examples on roots.
See Mordkovich Algebra, 11th grade, Page 124 for examples on logarithms.
See "A graphical approach to algebra and trigonometry", Section 5.4, Exercise 51.
https://math.stackexchange.com/questions/3732407/logarithm-power-rule-does-not-provide-a-complete-solution-have-the-logarithm-ru

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
