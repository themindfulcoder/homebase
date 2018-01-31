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
