---
title: "Javascript Hoisting"
date: 2017-12-03
draft: true
---

# Hoist me to the top!

Javascript can often be a source of frustration when you don't know some of the nuances of the language. Hoisting is one of those mechanics.

##### What is hoisting?

Simply, it's moving variable and function declarations to the top of the scope. What do you mean it moves variable and function declarations?

##### Example 1;

``` js
console.log(novariable);
```

> **Output:** ReferenceError novariable is not defined

So what happened here? Javascript realised that we were attempting to use something that simply didn't exist in the code hence the reference error.

##### Example 2;

``` js
console.log(wrongPlace);
var wrongPlace = 'Variable is still used before it is declared';
```

> **Output:** undefined

Wait... undefined? Why isn't it a reference error like previously? This is where hoisting comes into play, it moved our variable declaration to the top of the scope. The executed javascript code looked like this.

``` js
var wrongPlace;
console.log(wrongPlace);
wrongPlace = 'Variable is still used before it is declared';
```

Note how the declaration and assignment was not moved? Only the declaration was moved. Okay sure but shouldn't we still get ReferenceError?

##### Example 3;

``` js
console.log(typeof novariable);
```

> **Output:** undefined

Any variable that has not been assigned a value has a type of *undefined*. This should explain the results we got in example 2.

Now that we understand how hoisting moves declarations, let's have a look at how it pertains to scope.

##### Example 4;

``` js
var bgColor = 'red';
console.log(bgColor);

function changeBgColor() {
    console.log(bgColor);
    var bgColor = 'green';
}
changeBgColor();
```

> **Output:** red -> undefined;

This code example looks like this when it is executed

``` js
var bgColor;
bgColor = red;

function changeBgColor() {
    var bgColor;
    console.log(bgColor);
    bgColor = 'green';
}
changeBgColor();
```

The first thing to note is that the same variable name is used inside and outside the function *changeBgColor*. Javascript scope comes into play here where those two variables are NOT the same. Hoisting works as expected and moves variable declarations to the top of the scope.

This last example highlights how hoisting and scope can really impact developers when first starting to use javascript. There are some ways for us to easily combat these problems.

##### Example 5;

``` javascript
var FirstName = 'John';
var LastName = 'Doe';
var Age = 20;
var UserName = undefined; //I will only know your value later

function calculateUserName (firstName, lastName, age) {
    var UserName = '';
    UserName += firstName[0];
    UserName += lastName[0];
    UserName += age.toString();
    return UserName;
}

UserName = calculateUserName(FirstName, LastName, Age);
console.log(UserName);
```

In this example, I show some simple practices you can use to prevent being caught off guard by hoisting. 

One solution is do the hoisting yourself. This can feel very manual labor intensive but it makes sure you are aware of the variable and it's value while reading the code.

Another solution is to declare all variables with the `var` keyword to ensure the code we are writing acts in the correct scope. The threat of **UserName** was neatly avoided by clearly declaring and assigning it in the function. We can also see that in the code outside the function that it was declared and given the value of undefined which gave us clarity in that scope.

Hope this cleared up some unexpected behaviour one might experience when first trying out javascript as a language.