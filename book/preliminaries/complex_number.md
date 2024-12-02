# Introduction to Complex Numbers

In this page, we will introduce **complex numbers**, which are fundamental in mathematics, physics, and engineering. You will learn what complex numbers are, how to perform basic operations, and their geometrical representation.

## What are Complex Numbers?

A **complex number** is a number of the form:

$$
z = a + bi
$$

where:
- \(a\) is the **real part** (\(\operatorname{Re}(z) = a\)),
- \(b\) is the **imaginary part** (\(\operatorname{Im}(z) = b\)),
- \(i\) is the imaginary unit, defined as \(i^2 = -1\).

For example:
- \(z = 3 + 4i\): Real part is 3, Imaginary part is 4.
- \(z = -2 - i\): Real part is -2, Imaginary part is -1.

Complex numbers allow us to solve equations that have no real solutions, such as:

$$
x^2 + 1 = 0 \quad \Rightarrow \quad x = \pm i
$$

## Geometric Representation

Complex numbers can be represented as points or vectors in a **2D plane** called the **complex plane**:
- The horizontal axis (real axis) represents the real part (\(a\)).
- The vertical axis (imaginary axis) represents the imaginary part (\(b\)).

The complex number \(z = a + bi\) is represented as the point \((a, b)\) in the plane.

### Polar Form

A complex number can also be expressed in **polar form**:

$$
z = r(\cos\theta + i\sin\theta)
$$

where:
- \(r = |z| = \sqrt{a^2 + b^2}\) is the **magnitude** (or modulus),
- \(\theta = \tan^{-1}\left(\frac{b}{a}\right)\) is the **angle** (or argument).

The polar form is useful for multiplication and division of complex numbers.

## Basic Operations

### Addition and Subtraction

Addition and subtraction are performed component-wise:

$$
(a + bi) + (c + di) = (a + c) + (b + d)i
$$

For example:
- \((3 + 4i) + (1 + 2i) = 4 + 6i\)
- \((3 + 4i) - (1 + 2i) = 2 + 2i\)

### Multiplication

To multiply two complex numbers, use the distributive property and \(i^2 = -1\):

$$
(a + bi)(c + di) = (ac - bd) + (ad + bc)i
$$

Example:
- \((1 + 2i)(3 + 4i) = -5 + 10i\)

### Conjugate and Division

The **conjugate** of \(z = a + bi\) is:

$$
\overline{z} = a - bi
$$

Division of complex numbers uses the conjugate:

$$
\frac{a + bi}{c + di} = \frac{(a + bi)(c - di)}{c^2 + d^2}
$$

Example:
- \(\frac{1 + 2i}{3 + 4i} = \frac{11}{25} - \frac{2}{25}i\)

## Applications

Complex numbers are used in:
- Electrical engineering (AC circuits, impedance),
- Signal processing,
- Quantum mechanics,
- Control theory.

Explore the exercises below to deepen your understanding.

## Quiz: Understanding Complex Numbers

:::{card} Exercise 1
What is the result of \((2 + 3i) + (-1 - i)\)?

```{admonition} Solution
:class: tip, dropdown
$begin:math:text$1 + 2i$end:math:text$