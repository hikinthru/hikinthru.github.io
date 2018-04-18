---
image: linked.jpg
title: Eloquent JS - A List
---

A linked list is like an upside down tree. Linked lists connect nodes in defined ways that explain relationships.

![Image alt]({{ site.baseurl }}/assets/images/linked.jpg)

This post steps through the process of solving Exercise 4.3 from Chapter 4 in [Eloquent JavaScript, 2nd Edition](http://eloquentjavascript.net/), written by Marijn Haverbeke. The exercise is titled "A List" and requires using JavaScript object lists. This post will cover what an an object list is, how it fits within JavaScript, and how we can use it to resolve Haverbeke's exercise.

- [About the Book](#about-the-book)
- [Object and Linked Lists](#object-and-linked-lists)
- [The Instructions](#the-instructions)
- [Our Tasks](#our-tasks)
    - [Step One: Building the ``prepend`` Function](#step-one-building-the-prepend-function)
    - [Step Two: Building the ``arrayToList`` Function](#step-two-building-the-arraytolist-function)
    - [Step Three: Building the `listToArray` Function](#step-three-building-the-listtoarray-function)
    - [Step Four: Building the `nth` Function](#step-four-building-the-nth-function)
- [Conclusion](#conclusion)
- [Full Code](#full-code)

## About the Book

[Eloquent JavaScript, 2nd Edition](http://eloquentjavascript.net/) is often used by JavaScript Meetup and Free Code Camp groups because the digital versions are free, it has a great online interface to work out the problems, can be downloaded as an ePub book for mobile reading, and lends itself well to group work. The exercises can be challenging when solving them alone and can require a bit of research for a beginner.

## Object and Linked Lists

In JavaScript a list is not a defined and standardized object type in the same sense as say an array, or as in other programming languages like Python. It is just one way of using JavaScript objects, due to their versatility, to build certain data structures. A 'linked list' (generally referred to here on as just 'list') is two or more JavaScript objects with relationships, or connections, between them. The fact that they have relationships with other objects in this way, makes them list objects. These connections can be linear (as in our exercise and Fig. 2 below), or can form trees (like family or phylogenetic trees), data lists, even types of graphs like this:

![Graph of a Bayesian Network](/images/bayesian-networks.png)

*Fig. 1 -* *Graph of a Causal Bayesian Network*

This is a causal graph that is a type of Bayesian Network. It is built using the concept of linked objects. If your aren’t a mathematician and you’ve still heard the term Bayesian before it is likely because Bayesian filters were a revolution in spam filtering in the late nineties and early 2000s. The Bayesian Network above is a type of acyclic graph that can be built with object lists, using their relationships. This makes object or linked lists, far more interesting (and useful) than is explained in the book.

The lists in our exercise are simpler than the network graph above. They look like this:

A linked list of objects:

![A linked list](/images/Singly-linked-list.svg)

*Fig. 2 - A linked list whose nodes contain two fields: a value, and a link to the next node.*

For a more thorough explanation of linked lists, which I’d advise before tackling this exercise, check this article at [i-programmer.info](http://www.i-programmer.info/programming/javascript/5328-javascript-data-structures-the-linked-list.html), particularly the first and last pages (it’s three pages). The article’s approach to lists employs object constructors, which we haven’t covered yet here (and Haverbeke isn’t looking for in our solution), but the information on “why” use lists and how they work is extremely helpful. See also Wikipedia’s article on [linked lists](https://en.wikipedia.org/wiki/Linked_list).

## The Instructions

![A screenshot of the instructions](/images/eloquent-js-ex.4.3.jpg)

*Fig. 3 - From Chapter 4,* *Exercise 4.3 - Eloquent JavaScript*

1. Write a function ``arrayToList`` that builds up a data structure like the previous one [see above] when given [1, 2, 3] as argument.
1. Write a ``listToArray`` function that produces an array from a list.
1. Write the helper function `prepend`, which takes an element and a list, and creates a new list that adds the element to the front of the input list.
1. Write the helper function `nth`, which takes a list and a number and returns the element at the given position in the list, or undefined when there is no such element.
1. If you haven’t already, also write a recursive version of `nth`.

## Our Tasks

Let’s go through the functions we will create.

1. We will write a helper function and name it `prepend`. It will facilitate adding elements to existing lists by simply taking an element and a list as arguments and formatting them for `arrayToList`. We are actually going to break Haverbeke's instructions order and do this first.
1. In the function `arrayToList` we will take an argument such as `[1,2,3]` and build a list like Haverbeke’s example shown above. It is really just three nested objects and with the `prepend` helper function will be pretty simple.
1. The function `listToArray` is next. This function will do the reverse of `arrayToList` and simply put object values back into a new array. This shouldn’t be difficult either (think .push).
1. The final function, `nth`, will be a type of lookup. A user will pass it the name of an object list along with an index number and it will return the value in that object. Haverbeke would like us to use recursion for iteration in this function.

While the concept of a linked list may be new to some of us the *methods* we will use to complete our tasks are not, they have been covered in the text.

### Step One: Building the ``prepend`` Function

While building the `arrayToList` function is Haverbeke’s first assignment in order, one of the purposes of the `prepend` *helper* function is to provide formatted input that `arrayToList` will use to populate a new list. For some reason Haverbeke doesn’t use it this way in his online solution, but I am going to; he only calls `prepend` in his test scenarios. However using it in `arrayToList`, since making it is part of the exercise anyway, makes the code simpler because we won’t duplicate the `prepend` process within `arrayToList`. You can compare our approach to his solution in the [Code Sandbox](http://eloquentjavascript.net/code/) section of the online book.

`prepend` will be called by `arrayToList` to create our objects (in the context of lists these objects are also called 'nodes'). Here our object will hold two pieces of information, our data value, and our relationship identifier (which Haverbeke labels rest, this label is completely arbitrary). `prepend` will simply format our two inputs into a JavaScript object for `arrayToList`.

Here is the very simple pseudocode:

1. Declare the function `prepend` to accept two arguments, value and rest.
1. Create a simple return statement that formats the object we will output. Haverbeke gives us this format in his instruction hints: {value: ‘X’, rest: list}.

```javascript
  function `prepend`(value, list){
    return {value: value, rest: list};
  }
```

### Step Two: Building the ``arrayToList`` Function

We are going to modify Haverbeke’s hints on `arrayToList`, because as noted earlier they include duplicating the work we have already done in `prepend`. Our final code for this function will be much simpler. The purpose of `arrayToList` is to create a data structure like the one in his example at the beginning of the instructions, when given the list `[1, 2, 3]` as an argument. This is just going to be a group of nested objects and half our work is already done.

Here is our pseudocode:

1. Declare `arrayToList` with a single argument for the array to use.
1. Create a local variable, `list`, to hold the part of the list that is built through the following loop, initialized as null (we could also use ‘{}’ to denote an empty object). We declare this variable outside of the for loop because we will add to it with each loop.
1. Create a normal for loop to iterate through the array.
1. Populate list in each loop using our `prepend` helper function, sending the arguments (arr[i], list).
1. Return the newly created list.

```javascript
  function `arrayToList`(arr) {
    var list = null;
    for (var i = arr.length - 1; i >=0; i--) {
      list = `prepend`(arr[i], list);
    }
    return list;
  }
```

### Step Three: Building the `listToArray` Function

The function `listToArray` is going to do the reverse of `arrayToList`, it is going take a list object as the argument and convert it back to an array for the purpose of retrieving list information. I originally approached this differently than Haverbeke’s solution before I looked at it, and am going to stick with mine because for a beginner it seems more intuitive.

Here is our pseudocode:

1. Declare the function `listToArray` with one argument that is a list.
1. Declare an empty array to feed the object into.
1. Create a `while` loop that runs until list is empty (i.e., not null).
1. `.push` the input list into our new array, retrieved from `list.value`.
1. Modify the list object to hold the rest values (with `list.rest`).
1. Return the new array.

```javascript
  function `listToArray`(list) {
    var arr = [];
    while(list !== null) {
      arr.push(list.value);
      list = list.rest;
    }
    return arr;
  }
```

### Step Four: Building the `nth` Function

The final function `nth` will be our search utility. It will use a simple loop to iterate through any list and search for a value, given the object index of the value. There are better solutions for much larger sets of data, but this works best for searching small sets.

We are going to use recursion to loop through the list. Recursion can very usefully be employed to call its own function again, *but with new arguments*. It is often similar to for or while loops; it processes some data, and then calls itself again with the new data as input. When standard loops suffice they should be used because recursion can be less efficient; however recursion is much more flexible and can create more complex loops that for and while cannot.

If you don’t really “get” recursion yet (like me at first), I strongly recommend checking out [Codecademy’s lesson](https://www.codecademy.com/courses/javascript-lesson-205/0/1) on it, with 26 modules. It’s free, can be done in an hour or two, and while you won’t be a master at recursion after, you will at least understand why it exists and how it can be useful. I did it before solving the next exercise in the chapter, “Deep Comparison” (because I solved it before this one) and it made all the difference.

Here is the pseudocode:

1. Declare a function, `nth`, with two arguments, the list to search and the index to look for.
1. We should first use an `if` statement to test if the provided list even exists, and if it does not, end the function by returning undefined.
1. Recursion requires a base case that serves as the “off switch” to end it (a hazard of recursion is the browser error "Unresponsive Script" and ensuing page crash, because a recursion is not properly terminating). So we will stop the recursion if or when the index reaches 0, and return `list.value`.
1. Our last statement is the recursion call itself. It will be a return statement, calling `nth` again, but for the list argument, we’ll send `list.rest`, and for the index argument we’ll send index - 1.

```javascript
  function `nth`(list, n) {
    if (!list)
      return undefined;
    else if (n == 0)
      return list.value;
    else
      return `nth`(list.rest, n - 1);
  }
```

## Conclusion

That’s it. My full code is below. If you are reading this for help with the solution I recommend just following the pseudocode above and writing the functions from scratch until you understand everything in them. Also, compare it to Haverbeke’s solution, as I mentioned I solved a couple of the functions with approaches that differed from his and I preferred them. As you have probably already seen, there are many ways to solve almost any programming problem, some more or less efficient, some more or less human-readable, and some more or less elegant. The trade-offs are for the programmer, you, to determine.

You can put your code into a JavaScript engine (you can use the one in Eloquent JavaScript's Code Sandbox [here](http://eloquentjavascript.net/code/) if needed), and call it with the following scripts to test:

```javascript
  console.log(`arrayToList`([10, 20]));
  // Output: {value: 10, rest: {value: 20, rest: null}}
  console.log(`listToArray`(`arrayToList`([10, 20, 30])));
  // Output: [10, 20, 30]
  console.log(`prepend`(10, `prepend`(20, null)));
  // Output: {value: 10, rest: {value: 20, rest: null}}
  console.log(`nth`(`arrayToList`([10, 20, 30]), 1));
  // Output: 20
```

Happy coding!

## Full Code

```javascript
  function `prepend`(value, list){
    return {value: value, rest: list};
  }

  function `arrayToList`(arr) {
    var list = null;
    for (var i = arr.length - 1; i >=0; i--) {
      list = `prepend`(arr[i], list);
    }
    return list;
  }

  function `listToArray`(list) {
    var arr = [];
    while(list !== null) {
      arr.push(list.value);
      list = list.rest;
    }
    return arr;
  }

  function `nth`(list, n) {
    if (!list)
      return undefined;
    else if (n == 0)
      return list.value;
    else
      return `nth`(list.rest, n - 1);
  }
```