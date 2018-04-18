---
image: difference.png
title: 'Eloquent JS: A Deep Comparison'
---

This post follows the process of solving Exercise 4.4, “A Deep Comparison" in Chapter 4 of [Eloquent JavaScript, 2nd Edition](http://eloquentjavascript.net/), written by Marijn Haverbeke.  We are asked to create a program that can compare two values and determine if they are identical--and if they are not, but they are both objects, determine if they have the same properties. The exercise highlights equality operators, value types, and using recursion to do something more useful than replacing a for or while loop.

![Image alt]({{ site.baseurl }}/assets/images/difference.png)

- [About the Book](#about-the-book)
- [The Instructions](#the-instructions)
- [Objects and Properties](#objects-and-properties)
- [Values and Types](#values-and-types)
- [Identity](#identity)
- [Equality Operators](#equality-operators)
- [The Exercise](#the-exercise)
    - [The First Two Steps](#the-first-two-steps)
    - [The Third Step](#the-third-step)
    - [The Fourth Step: Comparing the Properties of Two Objects](#the-fourth-step-comparing-the-properties-of-two-objects)
    - [Recursion](#recursion)
- [Conclusion](#conclusion)
- [Full code](#full-code)

## About the Book

[Eloquent JavaScript, 2nd Edition](http://eloquentjavascript.net/) is often used by JavaScript Meetup and Free Code Camp groups because the digital versions are free, it has a great online interface to work out the problems, can be downloaded as an ePub book for mobile reading, and lends itself well to group work. The exercises can be challenging when solving them alone and can require a bit of research for a beginner.

## The Instructions

> The == operator compares objects by identity. But sometimes, you would prefer to compare the values of their actual properties.

> Write a function, deepEqual, that takes two values and returns true only if they are the same value or are objects with the same properties whose values are also equal when compared with a recursive call to deepEqual.

> To find out whether to compare two things by identity (use the === operator for that) or by looking at their properties, you can use the typeof operator. If it produces object for both values, you should do a deep comparison. But you have to take one silly exception into account: by a historical accident, typeof null also produces "object".

So our steps are (and we will discuss these thoroughly as we go through them):

1. Write a function `deepEqual`.
1. Use `===` to determine if the two values provided to `deepEqual` are _identical_.
1. Check for and remove any `null` values, and use `typeof` to remove any other remaining _primitives_.
1. If we are left with two _objects_ (that are not identical), check that they have the same number of properties; then use a _recursion_ to compare those properties and see if they are the same in both objects (Haverbeke calls this a 'deep comparison').

I began this exercise by reviewing some definitions: _object_, _property_, _value_, _type_ and _identity_. Finally before starting the exercise I wanted to thoroughly understand the two different equality operators `==` and `===`. The refreshers made following the exercise much easier.

## Objects and Properties

We can knock out *objects* and *properties* with a great explanation from MDN's JavaScript Guide:

> An object is a collection of properties, and a property is an association between a name (or key) and a value [objects contain key-value pairs]. A property's value can be a function, in which case the property is known as a method.
-[MDN: Working with Objects](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Working_with_Objects)

Objects are either *intrinsic*, those built into JavaScript like `Math` or `Array` (the list of all twelve built-in objects can be seen [here](https://docs.microsoft.com/en-us/scripting/javascript/intrinsic-objects-javascript)), or those we create ourselves to do our work, like `Employee`, `Contact`, or `Car`.

## Values and Types

According to the [ECMAScript 2015 standard](http://www.ecma-international.org/ecma-262/6.0/), or ES2015 (formally known as ES6) *any piece of data that can be manipulated is a **value***. The ES2015 documentation explains that all values belong to just seven JavaScript *types*. They are _object_, _boolean_, _string_, _number_, _symbol_ (new in ES2015), _null_ and _undefined_.

The `typeof` operator can be used on any value to determine its type, except `null` (a historical vestige that cannot currently be corrected).

All JavaScript types (and their values) fall into one of two categories, which are easy to remember because they are simply _objects_ and *everything else*. In JavaScript everything that is not an object is considered a _primitive_, so almost everything in JavaScript is either an object or a primitive. Since an object is one of the seven JavaScript types, primitives include the rest of the value types: booleans, strings, numbers, symbols, null and undefined.

**The major characteristic that separates objects from primitives is that all primitives are immutable, and objects are not.** That's almost a double negative, but essentially object 'parts' can be changed, primitive 'parts' cannot. Once you create a string, say `i='abc';` you cannot use any *method* (such as `.splice`, `.push`, etc.) to change the value of `abc` as it exists in the JavaScript-verse. This is unlike objects (and *arrays* which are a special kind of object) that we can do almost anything to. The string `abc`, which is pointed to by the variable `i`, can be replaced by reassigning the variable that points to it (`i='dce';`), but it cannot be modified in place by replacing just `a` with `e`. (Note that this is not true for all object-oriented, or OOP, languages for example in C).

## Identity

**Identity** refers to *objects* and is: the whole of an object's properties. One of these properties includes the object's *memory reference*, or where it physically resides in the computer's memory. Whether or not two different objects have all of the same property *values* can be tested (and we will do this shortly), like duplicate contact entries in a physical address book, but they cannot have the same *identity* since two things cannot physically exist in the same space. That is, two separately created objects cannot both be stored in the same memory reference regardless of their contents. In the example of duplicate address book contacts, it is obvious that you can physically edit, erase, or scribble out information on one contact entry without affecting the other, but two different contacts can't exist in the same space on the page. It is the same with JavaScript objects.

You CAN, however, create a new object with a different name that points to an existing object’s identity. This can be useful in more complex JavaScript programs. It is like a house on a corner that the owner adds a new driveway to from a second bordering street; it doesn't change the house's address, or make two houses, it simply creates another way to access the same house from a different direction.

If there are objects with alternate pointers like this in a program, properly employing equality operators becomes important in order to identify them because changing one, changes both (since they both point to the same space, or 'value' in memory).

## Equality Operators

There are two equality operators we can use to compare our values, and their subtle differences are important. They are:

* Loose equality ("double equals") using ==
* Strict equality (or "triple equals" or "identity") using ===

When using `==` to compare two primitive values, e.g., `‘1’ == 1` (the first being a string and the second a number), the `==` operator in JavaScript will convert one or the other to the same type (depending on a myriad of rules for the two types being compared) and in our example return `true`. Using `==` is discouraged because it is not strict, but it can be useful when the primitives are known to be of different types and are being compared solely for their values.

The `===` operator compares for strict equality, which includes the value *type*. It does not convert either value for the comparison. If the values are the same, as in the above example of 1s, but the types are not (number vs. string) it will return `false`.

Do note that when comparing two objects (as opposed to primitives), there is no difference between `==` and `===` since when used on two objects, both check the objects' identities. It is simply recommended for consistency to use `===` for object comparisons.

## The Exercise

### The First Two Steps

1. Write a function `deepEqual`.
1. Use `===` to determine if the two values provided to `deepEqual` are identical.

We will write a function that begins by checking if the two arguments provided are strictly equal with `===`, and end the function with `true` if they are.

Our strict comparison will return `true` if:

1. We are comparing two primitives with the same type and value.
1. If we are comparing two objects, one of which is a pointer to the other.
1. If we are comparing an object to itself.

```javascript
  function deepEqual(a, b) {
    if (a === b) {
      return true;
    }
  }
```

### The Third Step

Step 3: Check for and remove any `null` values, and use `typeof` to remove any other remaining primitives.

We'll check for and remove null values first because we know they will return `typeof: object`. Then we'll check any remaining values with the `typeof` operator to see if they are objects (if they are primitives, we know that they are `false` anyway because they didn’t return `true` in our previous equality check).

This will leave us with only objects to compare and check if they have the same properties in our last step.

There are four conditions we can use to test our values and terminate the test with `false` if any are `true`.

This is our pseudocode:

1. If a is null; or
1. a is NOT an object; or
1. b is null; or
1. b is NOT an object:
1. return false.

We'll use an `if` statement that employs equality and the logical operator for 'or' to check all four of our conditions:

```javascript
  if (a === null || typeof a !== "object" ||
      b === null || typeof b !== "object") {
    return false;
  }
```

If anything is left now it is two objects with different identities, although not necessarily different contents, for our final comparison.

### The Fourth Step: Comparing the Properties of Two Objects

Step four has two parts:

1. If we are left with two objects (that are not identical), check that they have the same number of properties;
1. Then use a recursion to compare those properties and see if they are the same in both objects.

To set up our function to compare the objects' properties, we’ll create two loops, one for object a and one for object b. Within each loop, we will assign the current property in each object to a variable, `prop`, that we can use for our comparisons. We will also use an additional variable to count how many properties we check in each object.

Before creating the loops we'll declare our property count variables:

```javascript
  var propsInA = 0;
  var propsInB = 0;
```

Next we create the loops for `a` and `b`. The `in` operator is very useful for returning a boolean value based on the condition it is provided. While using `for...in` for each instance of a property in `a` or `b`, each respective property at that point in the loop is assigned to the variable `prop` and our `propsInA` and `propsInB` variables are iterated respectively:

```javascript
  for (var prop in a) {
    propsInA += 1;
  }
  for (var prop in b) {
      propsInB += 1;
```

Our last real task is the most complex of the exercise. Still within the `b` loop (notice that we have not closed the `b` loop brace in our code above), if a property exists in `b`, then see if a property also exists in `a`, if it does not, then fail the test. See the first half of the `if` statement below.

### Recursion

A quick break here about recursion. If this is your first experience with programming, and you didn’t fully “get” Haverbeke’s earlier explanation in the text, and you haven't read my solution to Exercise 4.3, you may want to check out [Codecademy’s lesson](https://www.codecademy.com/courses/javascript-lesson-205/0/1) on it. It has 26 sections, is free, can be done in a couple of hours, and while you won’t be a master at it afterward you will at least understand why it exists and can be useful.

Back to our assignment. If both objects have properties in the current `prop` variables, call `deepEqual` *again* (our recursion), this time passing `a[prop]` and `b[prop]` as the new arguments. This will re-use the comparison code we’ve already written: `if (a === b) { return true; }` to determine if they are equal.

```javascript
    if (!(prop in a) || !deepEqual(a[prop], b[prop]))
      return false;
  } // Close 'b' loop when done with all properties
```

If either of these halves of the statement is not (`!`) true, stop and return `false`, ending the program. If the program hasn't terminated before the recursion begins (or repeats), the variables `propsInA` and `propsInB` maintain and continue their count with each new recursion. This recursive loop will keep running until there are no properties left to compare (the first half of the `if` statement will fail then, preventing an infinite loop in the recursion).

If it reaches the end of all properties without failing, we close the `b` loop and use our count variables to provide the final output:

```javascript
  return propsInA === propsInB;
```

This closing statement serves two purposes, it confirms that the property counts are the same, and either way, returns our final answer in boolean form.

## Conclusion

That’s it. We've covered objects and properties, values and types, identity, equality operators, and recursion, all in one exercise. Not a bad day.

Now we just need to put it all together and call it with Haverbeke’s tests. My code is below with comments, and I added a few extra tests for primitives to show that those are also considered in our function.

Happy coding!

## Full code

```javascript
/***********************************************
*
* Author: Sherrie Fuqua, 2016
*
* Fuction: deepEqual to compare objects and
*     primitives for identity and properties.
*
************************************************/

// Declare a function deepEqual with two
// arguments
function deepEqual(a, b) {

  // See if a and b are strictly identical and
  // end the comparison with true if they are,
  // there is no need to continue.
  if (a === b) {
    return true;
  }

  // If either a or b are null, or are not both
  // objects, end the comparison with a fail
  if (a === null ||
      typeof a !== "object" ||
      b === null ||
      typeof b !== "object") {
    return false;
  }

  // Declare variables for property counts
  var propsInA = 0;
  var propsInB = 0;

  // Iterate through each object’s properties
  // with a for..in loop and add 1 to the count
  // variable for each property it contains
  for (var prop in a) {
    propsInA += 1;
  }
  for (var prop in b) {
    propsInB += 1;

    // Within the for loop for b:
    // 1. For each property encountered in b
    // during the loop, check if there is also
    // an existing property in a.
    // 2. For each property at the same index
    // during the loop, call deepEqual again
    // to see if the property and it's values
    // are equal for both a and b.
    // 3. If not return false. If true, loop again
    // until there are no more properties.
    if (!(prop in a) || !deepEqual(a[prop], b[prop]))
      return false;
  }

  // Return true if there are an equal number of
  // properties in a and b, and false if not
  return propsInA === propsInB;
}

// Test
var obj = {here: {is: "an"}, object: 2};
console.log(deepEqual(obj, obj));
// → true
console.log(deepEqual(obj, {here: 1, object: 2}));
// → false
console.log(deepEqual(obj, {here: {is: "an"}, object: 2}));
// → true

// Additional tests on primitives
var a = 1;
var b = 1;
var c = '1';
var d = '1';
console.log(deepEqual(a, b));
// → true
console.log(deepEqual(a, c));
// → false
console.log(deepEqual(b, c));
// → false
console.log(deepEqual(d, c));
// → true
```