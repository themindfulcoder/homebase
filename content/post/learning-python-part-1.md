---
title: "Learning Python Part 1"
date: 2018-01-29T22:14:34+02:00
draft: true
---

https://stackoverflow.com/questions/41589655/whats-the-difference-between-python3-x-and-python3-xm#41589841

https://www.python.org/dev/peps/pep-0008/

variables
note: must start with a character or underscore

first_name = "Dwayne"
_pi = 3.14

naming convention - camelCase vs under_score_is_preferred

types
note: integers do not have a limit, it'll accept any number as long as there is enough memory to allocate it
note: float has a restricted precision
    name = "John Doe"
    age = 12
    pi = 3.14

    print(name)
    John Doe
    print(type(name))
    <class 'string'>

    print(age)
    12
    print(type(age))
    <class 'int'>
    print(pi)
    3.14
    print(type(pi))
    <class 'float'>

    big_integer = 123456789012345678901234567890
    print(big_integer)
    123456789012345678901234567890

    precise_float = 123.123456789012345678901234567890
    print(precise_float)
    123.123456789012345

type casting
note: type casting float to int will round down
    print(int(precise_float))
    123
