---
title: "Learning Python Part 1"
date: 2018-01-29T22:14:34+02:00
draft: true
---

Let's begin with some information regarding python. Python has been around since 1991, that is an impressive 26 years. Python is an open source language driven by the community and managed by the [Python Software Foundation](https://www.python.org/psf-landing/ "Python Software Foundation").

Python focuses on readability and features multiple programming paradigms. So whether you are completely new to programming, come from an object orientated background or even feel more comfortable with a functional approach, python has you covered.

Python boasts an impressive collection of packages, over 100 000, created by a very enthusiastic community and is available to you using PyPI, more on that later. Python can run almost everywhere, on most operating systems and even embedded devices. The Python language is heavily focused on readability and getting the job done simply. Without any further delay, let's jump right in.

---

### Variables

Variables are names pointing to actual information. Think of it like label stickers on objects around the house. The label itself is meaning less, however the object presents some value.

![Variables are like labels](variables-are-labels.png)

> Note: Variable names must start with a character or an underscore

``` python
first_name = "John"
_pi = 3.14
```

The above python code snippet, demonstrates creating two *variables*. The first, ```first_name``` is a named placeholder for the value ```John``` while ```_pi``` is the named placeholder for the value ```3.14```

In python, there are two popular conventions for naming your variables.

1. Camel case convention ```firstName```
2. Underscore convention ```first_name```

The underscore convention is the *preferred* style of the python community. Whichever you choose, be sure to maintain the style throughout the project. Consistency is an important factor when it comes to readability and maintaining projects later on.


### Types

Python supports multiple data types. ```String```, ```integer``` and ```float``` are the ones we will be looking at.

A string is a collection of characters, to form words, sentences or paragraphs amongst other things.
An integer is a number without a decimal value. It is either positive or negative and has no restriction on how large the number can be, other than how much memory you have on your machine.
A float is a number with a decimal value, even if the decimal value is zero, floats however have a restriction on the precision they can keep.

```python
name = "John Doe"
age = 12
pi = 3.14
big_integer = 1234567890123456789012345678901234567890
precise_float = 123.123456789012345678901234567890

print("String example")
print(name)
print(type(name))
print("Integer example")
print(age)
print(type(age))
print("Float example")
print(pi)
print(type(pi))
print("Really large integer example")
print(big_integer)
print("Really precise float example")
print(precise_float)
```

Will output the below

``` shell
String example
John Doe
<class 'str'>
Integer example
12
<class 'int'>
Float example
3.14
<class 'float'>
Really large integer example
1234567890123456789012345678901234567890
Really precise float example
123.12345678901235
```

    

type casting
note: type casting float to int will round down
    print(int(precise_float))
    123

Operators
Addition = 3 + 6
Subtraction = 2 - 1
Subtraction = 2 - -2
Multiplication = 3 * 2
Exponential = 2 ** 4
Division = 4 / 2
FloorDivision = 4.5 // 2
Remainder = 4.5 % 2

note: decimal division is the default in python
note: floor division will round down
note: floor division with floats will return a float
note: python does not support division by zero


https://stackoverflow.com/questions/41589655/whats-the-difference-between-python3-x-and-python3-xm#41589841

from terminal type `which python3` to get the location of your python interpreter
set scripts shebang using the location like so
`#!/usr/bin/python3.6`

https://www.python.org/dev/peps/pep-0008/