---
title: "Learning Python Part 2"
date: 2018-02-05
draft: true
---

![Languages are complex](language-word-cloud.jpg)
Strings are at the heart of many programs. We asks our users for information that our code requires to do the task. We provide feedback to the users when the task has completed or failed. We share information with other systems. This is almost always done using strings and string manipulation.

In part 2 we are going to look at how we use strings. How we can change these strings using the Python library. How we can give the information back to the user in useful manner and how to get information from the user to begin with.

* [Defining strings](#defining-strings)
* [Comments](#comments)
* [Arithmetic operators on strings](#arithmetic-operators-on-strings)
* [String methods](#string-methods)
* [More string methods](#more-string-methods)
* [Chaining methods](#chaining-methods)
* [Strings as immutables](#strings-as-immutables)
* [String formatting](#string-formatting)
* [User Input](#user-input)

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

The string type has a number of methods for you to use. These methods are made
available by the Python library. You can read more about all the methods in 
the [Python documentation](https://docs.python.org/3/library/stdtypes.html#string-methods "String methods")

Using the `capitalize` method, only the first character will be uppercase and
the remaining characters will be lowercase. Keep in mind that it is the very
first character and not the letter of an alphabet that it will try to uppercase.

``` python
sentence = "wHeRe iS My CoFFee"
print(sentence.capitalize())
print(" hello")
```
``` shell
> Where is my coffee
>  hello
```

Using the `lower` method will return the string with all lowercase characters.

``` python
sentence = "wHeRe iS My CoFFee"
print(sentence.lower())
```
``` shell
> where is my coffee
```

Similarly, using the `upper` method will return the string with all uppercase
characters.

``` python
sentence = "wHeRe iS My CoFFee"
print(sentence.upper())
```
``` shell
> WHERE IS MY COFFEE
```

Using the `title` method, will capitalize the first letter of each word
separated by a space. Apostrophe's used for word contraction may lead to
undesired results. You can find a way around that scenario [here](https://docs.python.org/3/library/stdtypes.html#str.title)

``` python
sentence = "wHeRe iS My CoFFee"
print(sentence.title())
print("you're a python legend".title())
```
``` shell
> Where Is My Coffee
> You'Re A Python Legend
```

# More string methods

You can do a lot more than simply change the capitalization of your string.
For example, we can `count` how many occurrences there are of a string within
your string.

``` python
sentence = "how much wood would a wood chuck wood if a wood chuck could chuck wood"
print(sentence.count("wood"))
print(sentence.count("would"))
```
``` shell
> 5
> 1
```

We can also remove any unwanted *whitespace* from the *leading* and *trailing* part
of our string using the `strip` method.

``` python
sentence = "   wHeRe iS My CoFFee   "
print(sentence)
print(sentence.strip())
```
``` shell
>   wHeRe iS My CoFFee   
> wHeRe iS My CoFFee
```

The `strip` method can take on a argument for characters to strip from the
*leading* and *trailing* part of our string. The order of the characters
in the argument does not matter. Note, that this does not remove all
occurrences of the characters but only if they are the leading or
trailing part of the string. The characters in the argument are also case
sensitive.

``` python
sentence = "   wHeRe iS My CoFFee   "
print(sentence.strip('efsw'))
print(sentence.strip('e fsw'))
```
``` shell
>    wHeRe iS My CoFFee   
> HeRe iS My CoFF
```

Using the `replace` method we can substitute an *old* set of characters for
a *new* set of characters within a string.

``` python
sentence = "the dog chased the cat"
sentence = sentence.replace("dog", "canine")
sentence = sentence.replace("cat", "feline")
print(sentence)
sentence = sentence.replace("the", "a")
print(sentence)
```
``` shell
> the canine chased the feline
> a canine chased a feline
```

The `replace` method takes a third argument, *count*, which can limit how
many occurrences to replace in the string.

``` python
sentence = "words words words"
sentence = sentence.replace("words", "three", 1)
sentence = sentence.replace("words", "simple", 1)
print(sentence)
```
``` shell
> three simple words
```

# Chaining methods

Until now we've seen a variety of ways to manipulate strings using methods.
These methods can be *chained* together. Have a look at the example below
which tries to create a friendly readable string from a filename.

``` python
file_name = "[Book]_learning-python-book-part-2.pdf"
print(file_name)
file_name = file_name.lower()
print(file_name)
file_name = file_name.replace("book", "", 1)
print(file_name)
file_name = file_name.replace("pdf", "")
print(file_name)
file_name = file_name.strip("[]_.")
print(file_name)
file_name = file_name.replace("-", " ")
print(file_name)
file_name = file_name.title()
print(file_name)
```
``` shell
> [Book]_learning-python-book-part-2.pdf
> [book]_learning-python-book-part-2.pdf
> []_learning-python-book-part-2.pdf
> []_learning-python-book-part-2.
> learning-python-book-part-2
> learning python book part 2
> Learning Python Book Part 2
```

We can *chain* the methods together to look like this
``` python
file_name = "[Book]_learning-python-book-part-2.pdf"
file_name = file_name.lower().replace("book", "", 1).replace("pdf", "")
file_name = file_name.strip("[]_.").replace("-", " ").title()
print(file_name)
```
``` shell
> Learning Python Book Part 2
```

# Strings as immutables

Strings are immutable but what does that even mean? Simply it just means
that it can't be modified once created. The string methods actually return
completely new string objects and don't manipulate the original string at
all. That does not mean we can't assign new values to our string variable
it only means that the string object that the variables point to can not
be modified.

``` python
sentence = "hello world"
print(sentence)
print(sentence.upper())
print(sentence)
sentence = sentence.upper()
print(sentence)
```
``` shell
> hello world
> HELLO WORLD
> hello world
> HELLO WORLD
```

# String formatting

The string type has a method `format` which is an extremely powerful way to
present information as a string. The `format` method works a little like the
replace method. You specify a format with placeholders, `{}` and then provide
it with the parameters to place in those placeholders.

``` python
#!/usr/bin/env python3
first_name = "Dwayne"
last_name = "Hinterlang"
full_name_format = "{}, {}"
full_name = full_name_format.format(last_name, first_name)
print(full_name)
```
``` shell
> Hinterlang, Dwayne
```
The `{}` got replaced with the variable values passed as parameters in the format
method. How did it know which variable goes where? When using just `{}` the format
method uses *implicit* positioning. The first parameter will replace the first
occurrence of `{}`, the second parameter will replace the second `{}` and so on.

We can get more control over this by using *explicit* positioning.
``` python
#!/usr/bin/env python3
first_name = "Dwayne"
last_name = "Hinterlang"
full_name_format = "{1}, {0}"
full_name = full_name_format.format(first_name, last_name)
print(full_name)
```
``` shell
> Hinterlang, Dwayne
```
Our format in this example has numbers inside the `{}` these numbers are parameter
index values. Parameters are zero indexed meaning the first parameters index value
is zero. Our format method will now replace our placeholder with the specific
parameter at the index we specified. In the example, `{1}` refers to the parameter
at position 1, which is `last_name`

`format` can also specify the minimum amount of character space a parameter can use.
This is called padding.
``` python
#!/usr/bin/env python3
padded = "Hello"
not_padded = "World"
pad_format = "{0:10}{1}"
print(pad_format(padded, not_padded))
```
``` shell
>      HelloWorld
```
The format string `{0:10}` now says, for the parameter at index zero `0` apply
these rules `:` to take up at minimum 10 character spaces or pad 10 `10`

We can specify which side the padding will be applied.
``` python
#!/usr/bin/env python3
pad_on_right = "Hello"
pad_on_left = "World"
pad_format = "{0:<10}|{1:>10}"
print(pad_format(padded, not_padded))
```
``` shell
> Hello     |     World
```


 Let's look at an example where we try display
a shopping list receipt

``` python
#!/usr/bin/env python3

price1 = 4.99
quantity1 = 3
name1 = "Item 1"
description1 = "An every day item"
total1 = price1 * quantity1

price2 = 2.67
quantity2 = 5
name2 = "Item 2"
description2 = "A cost effective condiment for steak"
total2 = price2 * quantity2


# Print a heading
print("Name Description Price Qty Total")
# Print a line item
print(name1 + ' ' + description1 + ' ' + str(price1) + ' ' + str(quantity1) + ' ' + str(total1))
print(name2 + ' ' + description2 + ' ' + str(price2) + ' ' + str(quantity2) + ' ' + str(total2))
```
``` shell
> Name Description Price Qty Total
> Item 1 An every day item 4.99 3 14.97
> Item 2 A cost effective condiment for steak 2.67 5 13.35
```

This is okay, all the information is being displayed but it is terrible to read.

[String Formatting Doc]("https://docs.python.org/3/library/string.html#formatstrings")

``` python
print("{:d}".format(12)) # Decimal
print("{:f}".format(123.123456789)) # Float
print("{:.2f}".format(123.123456789)) # Float with precision of 2
print("{:8.2f}".format(123.123456789)) # Float with precision of 2 and padding of 8
print("{:052f}".format(123.123456789)) # Float with precision of 2 and padding of 8, zero filled
[See the format specification mini-language]("https://docs.python.org/3/library/string.html#formatspec")

# implicit positional formatting
print("{} is from {}".format("John", "Earth"))
# explicit positional formatting
print("{0} is from {1}".format("John", "Earth"))

# alias formatting
print("{last_name}, {first_name}".format(

    first_name="John",
    last_name="Doe"
))
```

# User Input

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