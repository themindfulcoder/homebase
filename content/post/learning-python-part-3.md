---
title: "Learning Python Part 3"
date: 2018-02-18
draft: false
---

Using *lists* we organize and categorize ourselves and the environment around 
us.  In Python *lists* are essentially a container of sequenced objects that 
are alike in nature.  You are not restricted to having *lists* of only a 
single data type, however it is often not seen as very intuitive to use 
different types in a *list*.

Lists like strings are a sequence type which really means that we can use an 
index to access the data, we'll have a look at slicing which is a feature of 
sequence types, allowing us to get portions of data instead of a singular item.

- [Basic Manipulation](#basic-manipulation)
- [Methods vs Functions](#methods-vs-functions)
- [List Methods](#list-methods)
- [Built-in Functions](#built-in-functions)
- [Slicing](#slicing)
- [Multiple dimensions](#multiple-dimensions)
- [Reference Items](#reference-items)

# Basic Manipulation

Lists can be defined using box brackets `[]` and items are seperated by a comma 
`,`.

``` python
empty_list = []
numbers = [5, 12, 13, -1]
names = [
    "Joe",
    "Tom",
    "Bob"
]
mixed = [1, "1", 2, "Joe"]
```

To get a specific item from the list, we can use an index value. Using an index 
value that does not exist will however throw an error.

``` python
print(names[0])
print(names[3])
```
``` bash
> Joe
> IndexError: list index out of range
```

We can remove items from the list by using the `del` operator.

``` python
del names[1]
print(names)
```
``` bash
> ["Joe", "Bob"]
```

Even though both strings and lists are sequence types, a string is immutable 
and the `del` operator will throw an error.

``` python
word = "Hello"
del word[1]
```
``` bash
> TypeError: <str> object does not support item deletion
```

We are going to need to be able to add to our list as well, we can do so using 
the `+` operator.

``` python
names = names + ["Peter", "Jane"]
print(names)
```
``` bash
> ["Joe", "Bob", "Peter", "Jane"]
```

# Methods vs Functions

Let's quickly talk about the difference between methods and functions. Methods 
are part of an object and act on an object while functions are stand alone 
operations and take on arguments.
``` python
object.method()   # this would be a method
function(object)  # this would be a function
```
# List Methods

List objects have several methods available we will cover some of the more 
common options.

We can add to our list using the `append` method.

``` python
names.append("Sarah")
print(names)
```
``` bash
> ["Joe", "Bob", "Peter", "Jane", "Sarah"]
```

The `append` method only adds one item at a time, when we need to add a range 
of items we can use the `extend` method.

``` python
names.extend(["Lisa", "Zack"])
print(names)
```
``` bash
> ["Joe", "Bob", "Peter", "Jane", "Sarah", "Lisa", "Zack"]
```

We can also remove from our list using the `remove` method. The `remove` method 
will remove the *first* occurence of the item in the list.

``` python
names.remove("Peter")
print(names)
```
``` bash
> ["Joe", "Bob", "Jane", "Sarah", "Lisa", "Zack"]
```

Say we want to sort our list of names, we can use the `sort` method.

``` python
names.sort()
print(names)
```
``` bash
> ["Bob", "Jane", "Joe", "Lisa", "Sarah", "Zack"]
```

We can add an item to a specific location using the `insert` method.

``` python
names.insert(1, "Chloe")
print(names)
```
``` bash
> ["Bob", "Chloe", "Jane", "Joe", "Lisa", "Sarah", "Zack"]
```

# Built-in Functions

The `min` function will return the smallest item in the list.

``` python
print(min(names))
```
``` bash
> Bob
```

Similarly `max` will return the largest item in the list.

``` python
print(max(names))
```
``` bash
> Zack
```

The `sum` function will return the items of the list added together, however it 
is not valid for strings

``` python
numbers = [1,2,3]
print(sum(numbers))
print(sum(names))
```
``` bash
> 6
> TypeError: unsupported operand type(s) for +: 'int' and 'str'
```

The `len` function will return the number of items in the list. Unlike indexes 
the `len` function is not zero based.

``` python
print(len(names))
print(len(numbers))
```
``` bash
> 7
> 3
```

# Slicing

Slicing is really powerful once you are familiar with it. It allows you to 
modify your list in portions or slices.

The slicing syntax is as follows `object[start:end:step]`. The step argument is 
optional and we'll talk about it a little later, for now let's print our list 
using slicing syntax.

``` python
print(names[:])
```
``` bash
> ["Bob", "Chloe", "Jane", "Joe", "Lisa", "Sarah", "Zack"]
```

Now say that we want the last three names in the list? Let's provide a start 
position using the index value `4`

``` python
print(names[4:])
```
``` bash
> ["Lisa", "Sarah", "Zack"]
```

Say we want to get the first three names from our list? Let's provide a end 
position using the index value of `3`

``` python
print(names[:3])
```
``` bash
> ["Bob", "Chloe", "Jane"]
```

Say we want all the names except the first two names and last two names?

``` python
print(names[2:-2])
```
``` bash
> ["Jane", "Joe", "Lisa"]
```

Notice how we used `-2` as a position? This indicates that it is the index 
value calculated from the end of the list. This concept can be used for all 
the indexing operations we've looked at up until now, including indexing in 
string objects.

It is important to know that the slicing start argument is *inclusive* and the 
end argument is *exclusive*. What does this mean? Let's try and get `Jane` and 
`Joe` from the list.

``` python
print(names[2])
print(names[4])
print(names[2:4])
```
``` bash
> Jane
> Lisa
> ["Jane", "Joe"]
```

Notice how Jane was included but Lisa was not. This is what is what is meant by 
inclusive and exclusive.

Now let's try and get every second or third name in the list using the step 
argument.

``` python
print(names[::2])
print(names[::3])
```
``` bash
> ["Bob", "Jane", "Lisa", "Zack"]
> ["Bob", "Joe", "Zack"]
```

We can provide a negative value for the step argument, which would also reverse 
the list.

``` python
print(names[::-1])
print(names[::-2])
```
``` bash
> ['Zack', 'Sarah', 'Lisa', 'Joe', 'Jane', 'Chloe', 'Bob']
> ['Zack', 'Lisa', 'Jane', 'Bob']
```

We can do some interesting things though, for example we can replace a slice 
with something completely new. Let's replace `Jane` and `Joe` with a new list 
of people.

``` python
names[2:4] = ["Theo", "Mandy", "Arnold", "Kim"]
print(names)
```
``` bash
> ['Bob', 'Chloe', 'Theo', 'Mandy', 'Arnold', 'Kim', 'Lisa', 'Sarah', 'Zack']
```

Something to note is that the slice will return an entirely new list and not 
modify the existing list at all.

# Multiple dimensions

We can create multiple dimension arrays as well, this really means that 
arrays are nested inside arrays. A common occurence of this is a 2d matrix.

``` python
array0 = [1, 2, 3]
array1 = [4, 5, 6]
array2 = [7, 8, 9]
arrays = [array0, array1, array2]
```

Accessing the items are much the same as before by providing an index.

``` python
print(arrays[1])
```
``` bash
> [4, 5, 6]
```

And getting a specific nested item like `5` would look like this

``` python
print(arrays[1][1])
```
``` bash
> 5
```

We can also modify items just like before with the newer syntax

``` python
arrays[1][1] = "MODIFIED"

print(array1)
print(arrays)
```
``` bash
> [4, "MODIFIED", 6]
> [[1, 2, 3],[4, "MODIFIED", 6],[7, 8, 9]]
```

There is no limit to how many dimensions your array can have, however it is 
uncommon to go beyond two dimensions. It becomes extremely complicated to 
maintain a mental model of what is happening in your code.

# Reference Items

Lists unlike strings are not immutable and use a reference that points to the 
original object. This means that we can change the original object and it would 
reflect in the list as well and visa versa.

Let's say we have a list of chores.

``` python
chores = ["Takeout trash", "Feed animals", "Water plants"]
```

And we need to do these same chores every few days of the week.

``` python
#       Mon     Thu     Sat
week = [chores, chores, chores]
```

You become environmentally aware and decide to recycle your trash.

``` python
chores[0] = "Recycle Trash"
print(week)
```
``` bash
> [["Recycle Trash", "Feed animals", "Water plants"],
   ["Recycle Trash", "Feed animals", "Water plants"],
   ["Recycle Trash", "Feed animals", "Water plants"]]
```

Notice how the value changed in all the items in the array. That is because of 
the reference to the chores variable which we modified.

What if we wanted to only change a specific occurence? We will then want to 
change the way we create our week list.

A little earlier, I said that slicing returns an entirely new array, lets use 
that to create unique copies.

``` python
week = [chores[:], chores[:], chores[:]]
```

And now let's do laundry on saturday instead of watering plants.

``` python
week[2][2] = "Laundry"
print(week)
```
``` bash
> [["Recycle Trash", "Feed animals", "Water plants"],
   ["Recycle Trash", "Feed animals", "Water plants"],
   ["Recycle Trash", "Feed animals", "Laundry"]]
```

This brings us to the end of lists in python. Hope you enjoyed it! Don't 
hesitate to get in contact with me on any of the platforms provided at the 
bottom of the page.