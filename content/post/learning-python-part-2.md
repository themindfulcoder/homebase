---
title: "Learning Python Part 2"
date: 2018-02-05
draft: true
---

![Languages are complex](language-word-cloud.jpg)
Strings are at the heart of many programs. We asks our users for information that our code requires to do the task. We provide feedback to the users when the task has completed or failed. We share information with other systems. This is almost always done using strings and string manipulation.

In part 2 we are going to look at how we use strings. How we can change these strings using the Python library. How we can give the information back to the user in useful manner and how to get information from the user to begin with.

The outline looks like this:

* Defining strings
* Comments
* Arithmetic operators on strings
* String methods
* More string methods
* Chaining methods
* Strings as immutables
* String formatting
* User Input

# Defining strings

Strings are defined in a number of different ways, all of which use quotes.

It is recommended that you choose either the single or double quote method and stick to it through out your project for the sake of consistency.

Straightforward situations look like this

``` python
# Single quote example
sentence = 'Where is my coffee?'
# Double quote example
sentence = "Where is my coffee?"
```

You will come across more complicated scenarios in which case it is recommended you use these variations

``` python
# Single quote with quotation
sentence = 'I shouted "Hooray!"'
# Double quote with word contraction
sentence = "You shouldn't have"
```

When the options above aren't enough you've got these options

``` python
# Triple quote
sentence = """You shouldn't have shouted "Hooray!" so soon."""
# Escape Sequence
sentence = "You shouldn't have shouted \"Hooray!\" so soon."
```

The triple quote method allows for multiple line strings. It is preferred that the string starts immediately after the opening quotes and the closing quotes are on their own line. Whitespace is honored in the multiple line quote, so pay attention to any spacing you might use.

``` python
multiple_line = """Hello,
    I am learning Python.
        The end.
"""
print(multiple_line)
```
``` shell
> Hello,
      I am learning Python.
          The end.
```

A `\` in a string is not simply a backslash, it is known as an escape sequence character. Escape sequence is tricky at first because it is the combination of the escape sequence character and the **next** character that determines what will be output.

``` python
# \' will insert a single quote.
sentence = "I won\'t shout."
print(sentence)
```
``` shell
> I won't shout.
```

``` python
# \" will insert a double quote.
sentence = "I shouted \"Hooray!\""
print(sentence)
```
``` shell
> I shouted "Hooray!"
```

``` python
# \\ will insert a backslash.
sentence = "He\\She went to the market."
print(sentence)
```
``` shell
> He\She went to the market.
```

``` python
# \t will insert a tab.
sentence = "Name\tAge"
print(sentence)
```
``` shell
> Name    Age
```

``` python
# \n will insert a new line.
sentence = "My first sentence.\nMy second sentence."
print(sentence)
```
``` shell
> My first sentence.
  My second sentence.
```

The escape sequence is not recommended for readability reasons. You can find out more about string literals and escape sequences in the [Python documentation](https://docs.python.org/3/reference/lexical_analysis.html#string-and-bytes-literals "String literals")

# Comments

It is common practice to provide comments with your code. Comments are used to provide context to the reader of the code.

``` python
""" Documentation Comment

    This uses the triple quote method, specifically the
    double quote.

    These comments can be used to generate documentation
    and provide a summary of methods or classes.
    """
    
# You can also comment using a single hash
#
# Do not forget to keep comments accurate or it
# will mislead the reader

full_name = "" # In-line comments should be avoided
```

# Arithmetic operators on strings

We can combine different strings together using concatenation or the `+` symbol.
``` python
first_name = "John"
last_name = "Doe"
separator = " "
full_name = first_name + separator + last_name
print(full_name)
```
``` shell
> John Doe
```

Repetition can be achieved using the `*` symbol.
``` python
cheer = "Hooray! "
cheer = cheer * 3
print(cheer)
```
``` shell
> Hooray! Hooray! Hooray! 
```

# String Methods

The string type has a number of methods for you to use. These methods are made available by the Python library. You can read more about all the methods in the [Python documentation](https://docs.python.org/3/library/stdtypes.html#string-methods "String methods")

``` python
>>> sentence = "wHeRe iS My CoFFee"
>>> print(sentence.capitalize())
Where is my coffee

>>> print(sentence.lower())
where is my coffee

>>> print(sentence.upper())
WHERE IS MY COFFEE

>>> print(sentence.title())
Where Is My Coffee
```

Let's have a look at some more methods used with the string type.

``` python
>>> sentence = "   wHeRe iS My CoFFee   "
>>> print(sentence)
   wHeRe iS My CoFFee   

>>> print(sentence.count("e"))
4

>>> print(sentence.count("ee"))
1

>>> print(sentence.strip())
wHeRe iS My CoFFee

>>> print(sentence.strip().strip('ewF'))
HeRe iS My Co
```

The last example used method chaining. You can call methods one after another without having to assign it to the variable in multiple steps, you can also chain different methods together.

``` python
>>> sentence = "   hello world!!!##    "
>>> print(sentence)
   hello world!!!##    
>>> sentence = sentence.strip()
>>> print(sentence)
hello world!!!##
>>> sentence = sentence.strip("#")
>>> print(sentence)
hello world!!!
>>> sentence = sentence.upper()
>>> print(sentence)
HELLO WORLD!!!
```

The above can be achieved like this

``` python
>>> sentence = "   hello world!!!##    "
>>> sentence = sentence.strip().strip("#").upper()
>>> print(sentence)
HELLO WORLD!!!
```

replace
``` python
sentence = "The dog chased the cat"
sentence = sentence.replace("dog", "canine")
sentence = sentence.replace("cat", "feline")
print(sentence)
sentence = sentence.replace("the", "a")
print(sentence)
sentence = sentence.replace("ine", "t")
print(sentence)
```

>The canine chased the feline
>The canine chased a feline
>The cant chased a felt

``` python
sentence = "words words words"
sentence = sentence.replace("words", "three", 1)
sentence = sentence.replace("words", "simple", 1)
print(sentence)
```

>three simple words

formatting

[String Formatting Doc]("https://docs.python.org/3/library/string.html#formatstrings")

``` python
print("{:d}".format(12)) # Decimal
print("{:f}".format(123.123456789)) # Float
print("{:.2f}".format(123.123456789)) # Float with precision of 2
print("{:8.2f}".format(123.123456789)) # Float with precision of 2 and padding of 8
print("{:052f}".format(123.123456789)) # Float with precision of 2 and padding of 8, zero filled
[See the format specification mini-language]("https://docs.python.org/3/library/string.html#formatspec")

# positional formatting
print("{0} is from {1}".format("John", "Earth"))

# alias formatting
print("{last_name}, {first_name}".format(
    first_name="John",
    last_name="Doe"
))
```

User input

``` python
first_name = str(input("What is your first name? "))
middle_name = str(input("What is your middle name? "))
last_name = str(input("What is your last name? "))
age = int(input("How old are you? "))

first_name = first_name.capitalize()
middle_name = middle_name.capitalize()
last_name = last_name.capitalize()

candidate_format = "{age:3} - {first_name}, {middle_name_initial:.1}. {last_name}"
print(candidate_format.format(
    first_name = first_name,
    middle_name_initial = middle_name,
    last_name = last_name,
    age = age
))
```

> 30 - Dwayne, L. Hinterlang