---
title: "Learning Python Part 1"
date: 2018-02-01
draft: false
---

Let's begin with some information regarding Python. It has been around since 1991, that is an impressive 26 years. It is an open source language driven by the community and managed by the [Python Software Foundation](https://www.python.org/psf-landing/ "Python Software Foundation").

Python focuses on readability and features multiple programming paradigms. So whether you are completely new to programming, come from an object orientated background or even feel more comfortable with a functional approach, Python has you covered.

Python boasts an impressive collection of packages, over 100 000, created by a very enthusiastic community and is available to you using PyPI, more on that later. It can run almost everywhere, on most operating systems and even embedded devices. Without any further delay, let's jump right in.

### Variables

Variables are names pointing to actual information. Think of it like label stickers on objects around the house. The label itself is meaning less, however the object presents some value.

![Variables are like labels](variables-are-labels.png)

> Note: Variable names must start with a character or an underscore

``` python
first_name = "John"
_pi = 3.14
```

The snippet demonstrates creating two *variables*. `first_name` is a named placeholder for the value `John` while `_pi` is the named placeholder for the value `3.14`

There are two popular conventions for naming your variables.

1. Camel case convention `firstName`
2. Underscore convention `first_name`

The underscore convention is the *preferred* style of the Python community. Whichever you choose, be sure to maintain the style throughout the project. Consistency is an important factor when it comes to readability and maintaining projects later on.


### Types

Python supports multiple data types, the ones we will be looking at are `string`, `integer` and `float`.

A `string` is a collection of characters to form words, sentences or paragraphs to name a few uses.

``` python
name = "John Doe"
print(type(name))
print(name)
```

Output

``` shell
<class 'str'>
John Doe
```

An `integer` is a number without a decimal value, it can be either positive or negative. There are no restrictions on how large the number can be except for how much memory you have available on your machine.

``` python
age = 12
big_integer = 1234567890123456789012345678901234567890
print(type(age))
print(age)
print(big_integer)
```

Output

``` shell
<class 'int'>
12
1234567890123456789012345678901234567890
```

A `float` is a number with a decimal value, even if the decimal value is zero, floats however have a restriction on the precision they can keep.

```python
pi = 3.14
zero_float = 4.0
precise_float = 123.123456789012345678901234567890
print(type(pi))
print(pi)
print(zero_float)
print(precise_float)
```

Output

``` shell
<class 'float'>
3.14
4.0
123.12345678901235
```

# Type casting

Type casting is a conversion from one type to another. In the example we cast a float to an integer and a string to an integer

``` python
age = "12"
precise_float = 123.123456789012345678901234567890
print(int(age))
print(int(precise_float))
```

Output

``` shell
12
123
```

>Note: type casting float to int will only keep the whole number before the decimals.

Be careful when casting types, you can cause your script to break like in this example which complains that the `string` weight is not an `integer`

``` python
weight = "50.5"
print(int(weight))
```

Output

``` shell
ValueError: invalid literal for int() with base 10: '50.5'
```

# Operators

Python supports general arithmetic operators for calculations

``` python
addition = 3 + 6
subtraction = 2 - 1
subtract_negative = 2 - -2
multiplication = 3 * 2
exponential = 2 ** 4
division = 4 / 2
floor_division = 4.5 // 2
remainder = 4.5 % 2

print(addition)
print(subtraction)
print(subtract_negative)
print(multiplication)
print(exponential)
print(division)
print(floor_division)
print(remainder)
```

Output

``` shell
9
1
4
6
16
2.0
2.0
0.5
```

Decimal division is the default, however you can change this using floats

``` python
print(6.0/2.0)
```

Output

``` shell
3.0
```

If you are familiar with math, the output of floor division is expected. For the rest of us, it is important to know that floor division will round down to the nearest whole number.
Floor division with floats will return a float and not an integer.

``` python
print(7//2)
print(7.0//2)
```

Output

``` shell
3
3.0
```

One last thing to note about arithmetic, division by zero will cause an error.

``` python
print(3/0)
```

Output

``` shell
ZeroDivisionError: division by zero
```

### Conclusion

This wraps up learning Python part 1, we spoke about variables, variable naming, types, type casting, arithmetic operations and some of the behavior they exhibit. Learning Python part 2 will take a closer look at strings and how we can do some manipulation of strings.

I hope you enjoyed reading this. Feel free to give me feedback on Twitter or report an issue on GitHub (links at the bottom of the page)