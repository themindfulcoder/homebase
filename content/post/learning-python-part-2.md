---
title: "Learning Python Part 2"
date: 2018-02-05
draft: true
---

![Languages are complex](language-word-cloud.jpg)
Strings are at the heart of many programs. We asks our users for information that our code requires to do the task. We provide feedback to the users when the task has completed or failed. We share information with other systems. This is almost always done using strings and string manipulation.

In part 2 we are going to look at how we use strings. How we can change these strings using the Python library. How we can give the information back to the user in useful manner and how to get information from the user to begin with.

- [Defining strings](#defining-strings)
- [Comments](#comments)
- [Arithmetic operators on strings](#arithmetic-operators-on-strings)
- [String Methods](#string-methods)
- [More string methods](#more-string-methods)
- [Chaining methods](#chaining-methods)
- [Strings as immutables](#strings-as-immutables)
- [String formatting](#string-formatting)
- [User Input](#user-input)

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
``` bash
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
``` bash
> I won't shout.
```

``` python
# \" will insert a double quote.
sentence = "I shouted \"Hooray!\""
print(sentence)
```
``` bash
> I shouted "Hooray!"
```

``` python
# \\ will insert a backslash.
sentence = "He\\She went to the market."
print(sentence)
```
``` bash
> He\She went to the market.
```

``` python
# \t will insert a tab.
sentence = "Name\tAge"
print(sentence)
```
``` bash
> Name    Age
```

``` python
# \n will insert a new line.
sentence = "My first sentence.\nMy second sentence."
print(sentence)
```
``` bash
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
``` bash
> John Doe
```

Repetition can be achieved using the `*` symbol.

``` python
cheer = "Hooray! "
cheer = cheer * 3
print(cheer)
```
``` bash
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
``` bash
> Where is my coffee
>  hello
```

Using the `lower` method will return the string with all lowercase characters.

``` python
sentence = "wHeRe iS My CoFFee"
print(sentence.lower())
```
``` bash
> where is my coffee
```

Similarly, using the `upper` method will return the string with all uppercase
characters.

``` python
sentence = "wHeRe iS My CoFFee"
print(sentence.upper())
```
``` bash
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
``` bash
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
``` bash
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
``` bash
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
sentence = "  []example.com"
characters_to_remove = "[] mo.c"
print(sentence.strip(characters_to_remove))
```
``` bash
> example
```

``` python
sentence = "   wHeRe iS My CoFFee   "
print(sentence.strip('efsw'))
print(sentence.strip('e fsw'))
```
``` bash
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
``` bash
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
``` bash
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
``` bash
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
``` bash
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
``` bash
> hello world
> HELLO WORLD
> hello world
> HELLO WORLD
```

# String formatting

The string type has a `format` method which is an extremely powerful way to
present information as a string. It method works a little like the `replace`
method and uses a *replacement field* surrounded by curly braces `{}`.

``` python
#!/usr/bin/env python3
sentence = "My {} sentence"
replacement_field = "original"
print(sentence.format(replacement_field))
```
``` bash
> My original sentence
```

We can do this with multiple variables at a time.

The example uses *implicit* positioning. The first parameter in `format` will
replace the first occurrence of a *replacement field*, the second parameter will
replace the second occurrence of a *replacement field* and so on.

``` python
sentence = "{} {} {}"
day_1 = "Monday"
day_2 = "Tuesday"
day_3 = "Wednesday"
month_1 = "January"
month_2 = "February"
month_3 = "March"

print(sentence.format(day_1, day_2, day_3))
print(sentence.format(month_1, month_2, month_3))
```
``` bash
> Monday Tuesday Wednesday
> January February March
```

We can get more control of which parameter to use with our *replacement field* 
using *explicit* positioning.

In this example the *replacement field* has a *parameter index value*.
A *parameter index value* begin from zero and indicate the position of which
parameter to use. This means that the first parameter, `first_name` an index of
zero, the second parameter `last_name` will then have an index of one. In the
example, `{1}` refers to the parameter with an index of one which is the
variable `last_name`.

``` python
#!/usr/bin/env python3
first_name = "Dwayne"
last_name = "Hinterlang"

full_name = "{1}, {0}"

print(full_name.format(first_name, last_name))
```
``` bash
> Hinterlang, Dwayne
```

We can also use *explicit* positioning using a *field name* which is many times
more readable. This example uses `{last_name}` as a *replacement field*. It uses
`last_name` as the field name. The way we provide parameters changes as well in
this example. We assign the variable `my_last_name` to the field name `last_name`

``` python
#!/usr/bin/env python3

my_first_name = "Dwayne"
my_last_name = "Hinterlang"
full_name = "{last_name}, {first_name}"
print(full_name.format(
    last_name = my_last_name,
    first_name = my_first_name))
```
``` bash
Hinterlang, Dwayne
```

Now that we can position the parameters, we can apply the [Format Specification](https://docs.python.org/3/library/string.html#format-specification-mini-language)
to them. We do this by using a colon `:` and then the rules to apply after it.
One of the *rules* we can apply is the minimum amount of character space
a parameter can use. This is called padding. In this example we specify a
*replacement field* with a padding of ten.

``` python
#!/usr/bin/env python3
word1 = "Hello"
word2 = "World"
sentence = "{0:10}{1}"
print(sentence.format(word1, word2))
```
``` bash
> Hello     World
```

We can also indicate the style in which to apply padding, left `<` aligned,
right `>` aligned or even center `^` aligned.

``` python
#!/usr/bin/env python3
left = "Left"
center = "Center"
right = "Right"
output = "|{0:<10}|{1:^20}|{2:>10}|"
print(output.format(left, center, right))
```
``` bash
> |Left      |       Center       |     Right|
```

We can also format other data types like *decimal* and *float* which has a
default precision of six and applies rounding.

``` python
print("{:d}".format(12)) # Decimal
print("{:f}".format(123.123456789)) # Float
```
``` bash
12
12.123457
```

This example looks at specifying the precision to use `.2f`, combining it with
padding `8.2f` as well as choosing a fill character other than space `08.2f`.

``` python
print("{:.2f}".format(123.123456789))
print("{:8.2f}".format(123.123456789))
print("{:08.2f}".format(123.123456789))
```
``` bash
123.12
  123.12
00123.12
```

# User Input

Getting information from the user to do a task for the user is important. In
this example I show you the `input` method which provides the user with a prompt
and then waits for the user to type in information and save it as a variable.

``` python
name = input("Name: ")
print(name)
```
``` bash
> Name: Dwayne
> Dwayne
```

We can use type casting with the `input` method, this can lead to errors for the
user so be careful.

``` python
age = int(input("Age: "))
print(age)
age = int(input("Age: "))
print(age)
```
``` base
> Age: 30
> 30
> Age: thirty
> ValueError: invalid literal for int() with base 10: 'thirty'
```

An example with a little of everything

``` python
#!/usr/bin/env python3
first_name = str(input("What is your first name? "))
middle_name = str(input("What is your middle name? "))
last_name = str(input("What is your last name? "))
age = int(input("How old are you? "))

first_name = first_name.capitalize()
middle_name = middle_name.capitalize()
last_name = last_name.capitalize()

candidate = "{age:3} - {first_name}, {middle_name_initial:.1}. {last_name}"
print(candidate.format(
    first_name = first_name,
    middle_name_initial = middle_name,
    last_name = last_name,
    age = age
))
```
``` bash
>  30 - Dwayne, L. Hinterlang
```