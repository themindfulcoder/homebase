---
title: "Learning Python Part 2"
date: 2018-01-31T07:12:07+02:00
draft: true
---

Basic Strings

single_quote = 'single quote'
double_quote = "double quote"
mixed_sentence_1 = "They can't quit"
mixed_sentence_2 = 'They shouted "Hooray!" when it worked'

escaped_sentence_1 = 'They can\'t quite'
escaped_sentence_2 = "They shouted \"Hooray!\" when it worked"

tripple_quote = ''' This is a
multiple line sentence or
paragraph'''

''' tripple quotes that are not assigned variables are comments '''
# is a single line comment

String Functions

lowercase_word = "hello world"
lowercase_word = lowercase_word.upper()
uppercase_word = "SCIENCE"
uppercase_word = uppercase_word.lower()

name = "john doe"
name = name.title()

whitespace = "   vision     "
whitespace = whitespace.strip().upper()

to find out what you can use, like upper refer to the python library documentation
https://docs.python.org/3/library/stdtypes.html#string-methods

advanced string manipulation

concatenation
``` python
first_name = "John"
last_name = "Doe"
separator = " "
full_name = first_name + separator + last_name
print(full_name)
```

>John Doe

duplication
``` python
item = "[item], "
item = item * 3
print(item)
```

>[item], [item], [item]

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

count

``` python
sentence = "three simple words"
print(sentence.count("e"))
print(sentence.count("ee"))
```

>3
>1

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