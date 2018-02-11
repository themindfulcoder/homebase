---
title: "Learning Python Part 2"
date: 2018-02-05
draft: true
---

![Languages are complex](language-word-cloud.jpg)
Strings are at the heart of many programs. We asks our users for information
that our code requires to do the task. We provide feedback to the users when the
task has completed or failed. We share information with other systems. This is
almost always done using strings and string manipulation.

In part 2 we are going to look at how we use strings. How we can change these
strings using the Python library. How we can give the information back to the 
user in useful manner and how to get information from the user to begin with.

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

It is recommended that you choose either the single or double quote method and 
stick to it throughout your project for the sake of consistency.

Straightforward situations look like this

``` python
# Single quote example
sentence = 'Where is my coffee?'
# Double quote example
sentence = "Where is my coffee?"
```

You will come across more complicated scenarios in which case it is recommended 
you use these variations

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

The triple quote method allows for multiple line strings. It is preferred that 
the string starts immediately after the opening quotes and the closing quotes 
are on their own line. Whitespace is honored in multiple line quote, so pay 
attention to any spacing you might use.

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

A `\` in a string is not simply a backslash, it is known as the *escape sequence*.
Here are some examples of common uses of the *escape sequence*.

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

We can combine different strings together using concatenation `+`.

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
available by the Python library. More information on string methods can be found
[here](https://docs.python.org/3/library/stdtypes.html#string-methods "String methods")

Using the `capitalize` method, only the first character will be uppercase and
the remaining characters will be lowercase.

``` python
print("wHeRe iS My CoFFee".capitalize())
print(" hello".capitalize())
```
``` bash
> Where is my coffee 123
>  hello
```

Using the `lower` method will return a string with all lowercase characters.

``` python
print("wHeRe iS My CoFFee".lower())
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
print("wHeRe iS My CoFFee".title())
print("you're a python legend".title())
```
``` bash
> Where Is My Coffee
> You'Re A Python Legend
```

# More string methods

You can do a lot more than simply change the capitalization of your string.
For example, we can `count` how many occurrences there are of a string within
a string.

``` python
sentence = "how much wood would a wood chuck chuck if a wood chuck could chuck wood"
print(sentence.count("wood"))
print(sentence.count("would"))
```
``` bash
> 4
> 1
```

We can also remove any unwanted *whitespace* from the *leading* and *trailing* 
part of our string using the `strip` method.

``` python
sentence = "   wHeRe iS My CoFFee   "
print(sentence)
print(sentence.strip())
```
``` bash
>   wHeRe iS My CoFFee   
> wHeRe iS My CoFFee
```

The `strip` method can take on a *chars* argument, a string containing the 
characters to strip from the *leading* and *trailing* parts of our string. 
The *chars* argument is case sensitive.

``` python
sentence = "   wHeRe iS My CoFFee   "
characters_to_remove = "e fsw"
print(sentence.strip(characters_to_remove))
```
``` bash
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
that it can't be modified once created. The methods actually return completely 
new strings and don't manipulate the original variable at all. We can however 
assign the return value of the method to our variable.

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
present information as a string. The method works a little like the `replace`
method and uses a *replacement field* surrounded by curly braces `{}`.

``` python
sentence = "My {} sentence"
replacement_field = "original"
print(sentence.format(replacement_field))
```
``` bash
> My original sentence
```

We can do this with multiple variables at a time, We can use *implicit* 
positioning. The first parameter in `format` will replace the first occurrence 
of a *replacement field*, the second parameter will replace the second 
occurrence of a *replacement field* and so on.

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
using *explicit* positioning, The *replacement field* has a *parameter index 
value*. The *parameter index value* begins at zero and indicates the position 
of which parameter to use. This means that the first parameter, `first_name` 
has an index of zero, the second parameter `last_name` will then have an index 
of one.

``` python
first_name = "John"
last_name = "Doe"

full_name = "{1}, {0}"

print(full_name.format(first_name, last_name))
```
``` bash
> Doe, John
```

We can also use *explicit* positioning using a *field name* which is many times
more readable. `{last_name}` is a *replacement field* using the field name 
`last_name`. The way we provide parameters to `format` changes as well. We 
assign the variable `my_last_name` to the field name `last_name`

``` python
my_first_name = "John"
my_last_name = "Doe"
full_name = "{last_name}, {first_name}"
print(full_name.format(
    last_name = my_last_name,
    first_name = my_first_name))
```
``` bash
Doe, John
```

Now that we can position the parameters, we can apply the [Format Specification](https://docs.python.org/3/library/string.html#format-specification-mini-language)
to them. We do this by using a colon `:` and then the rules to apply after it.
One of the *rules* we can apply is the minimum amount of character space
a parameter can use. This is called padding. In this example we specify a
*replacement field* with a padding of ten.

``` python
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

We can also format other data types like *decimal* and *float*, which has a
default precision of six and applies rounding.

``` python
print("{:d}".format(12)) # Decimal
print("{:f}".format(123.123456789)) # Float
```
``` bash
12
123.123457
```

This example looks at specifying the precision to use `.2f`, combining it with
padding `8.2f` as well as choosing zero as a fill character `08.2f`.

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

The `input` method provides the user with a prompt and waits for them to type 
in information which we assign to a variable.

``` python
name = input("Name: ")
print(name)
```
``` bash
> Name: John
> John
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
> Age: 12
> 12
> Age: twelve
> ValueError: invalid literal for int() with base 10: 'twelve'
```

Finally we can achieve something like this.

``` python
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
> What is your first name? John
> What is your middle name? Matthew
> What is your last name? Doe
> How old are you? 12
>  12 - John, M. Doe
```

I hope you enjoyed reading this. Feel free to give me feedback on Twitter or report an issue on GitHub (links at the bottom of the page)