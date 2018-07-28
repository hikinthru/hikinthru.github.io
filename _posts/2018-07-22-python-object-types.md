---
image: nasa-43569-unsplash.jpg
title: "Python: Understanding Objects and Types"
---

Python is an *object-oriented programming* (OOP) language. An *object* in computer programming refers to a package of information--or *data*, that is active in the computer's memory (has a location and address, just like an apartment in a city) and that some program is aware of. Like the letter blocks we played with as children, objects are a way of efficiently and flexibly organizing the data and information that a program uses to do what it is designed to do. A running Python program sees everything that it currently knows (variables that have been assigned, functions or methods that have been called, lists or dictionaries that have been defined) as either objects or the relationships between them. You can almost think of objects as physical things from the fact that if they have been instantiated (i.e., the program knows about them), they are physically occupying cells of space in the computer's RAM (memory). 

Python objects can be created with properties and attributes to accomplish anything Python is capable of, but once it is running (it is instantiated) all objects have three basic things:  an **identity** (the exact location where it can be found in the computer's memory in order to be used); a **type** (what family of objects it belongs to); and a **value** (the useful information or instructions that it holds).

![Satellite view of the city lights of New York City at night - Photo by NASA on Unsplash]({{ site.baseurl }}/assets/images/nasa-43569-unsplash.jpg) 

#### Contents: <!-- omit in toc -->

- [An Object's Identity](#an-objects-identity)
- [Object Types](#object-types)
- [Object Values](#object-values)
  - [Conclusion](#conclusion)

### An Object's Identity
An object's *identity*, or `id()`, is its numeric address in memory (RAM). That is, where it can be found and retrieved from when it is needed.

```python
>>> x = 10
>>> id(x)
1417309952
>>> id(10)
1417309952
```

The physical memory cell addressed (numbered) at 1417309952 is the the beginning cell in memory the computer will go to to use the information for the variable `x`.

An interesting note is that some values, such as lower numbers (e.g., '10'), are so commonly used that Python automatically loads them into memory (gives them addresses and ids) when it first opens. As long as your Python interpreter (Idle, Spyder, etc.) is running, the number 10 will have the same memory address. If you change the value of `x`, say to `8`, `x` will simply now point to the location your interpreter has placed the whole number 8 in memory (the number 8s `id()` for the duration of the interpreter's session). So the `id()` of `x` will change, but until you restart your interpreter, the `id()` of `10` will not.

### Object Types
An object's *type* describes what category the information in that object falls into; this defines what operations can be performed on it. If the object is a piece of text its type is `str` (pronounced like 'stir'). If it is a decimal number it is a `float`. If it is a whole number or its whole number negative it is an `int`. `True` and `False` are called *conditionals* and are type `bool`. 

You will also see the term *class* used and in today's Python 'class' and 'type' are generally interchangeable. In discussions on the Web you will likely find the term 'class' used more abstractly about Python object categories and 'type' used to refer more often to concrete objects.

Python also provides types that are *containers* for other objects like the ones we just covered (strings, numbers, etc.). Three commonly used container types in Python include *lists*, *dictionaries* and *tuples*. 

Lists, or Python type `list`, are groups of zero or more distinct pieces of data such as the names of common organic elements, or all of the meta information about a music album. Lists are created by declaring an arbitrary name, called a *variable* for the values, and then entering the values inside *brackets* (the square cornered parentheses).

```python
>>> my_elements = ['Hydrogen', 'Carbon', 'Nitrogen', 'Oxygen', 'Fluorine', 'Phosphorus', 'Sulfur', 'Chlorine', 'Bromine', 'Iodine', 'Astatine']
>>> print(my_elements)
['Hydrogen', 'Carbon', 'Nitrogen', 'Oxygen', 'Fluorine', 'Phosphorus', 'Sulfur', 'Chlorine', 'Bromine', 'Iodine', 'Astatine']
```

Dictionaries, or type `dict` are *key: value* pairs such as the names of all of the elements as keys with their atomic numbers as values, or that music album's meta-information including labels as keys for each piece of data like **Title** or **Year**. 

Tuples (pronounced 'toople' or 'tupple', whichever pleases you), or type `tuple` are similar to lists in that they hold groups of discrete data, however a tuple's contents cannot be modified after it is created, tuples are *immutable* objects. Their immutability makes them great for data that shouldn't be changed, because it can't be, and faster to search through large datasets due to less overhead than *mutable* lists. 

Mutable data types like lists must include the mechanics to "be" manipulated (functions must exist to append, remove, replace, sort, reverse, etc., the list's values), and this additional but inherent functionality increases its overhead, and makes mutable types such as lists slower to search with large amounts of data.

Different container types have strengths and weaknesses that are trade offs depending on what the programmer is trying to accomplish.

```python
# Create a variable and assign it a value
>>> x = 10

# Check its type
>>> type(x)
<class `int`> 

# Create some more variables
>>> y = 20
>>> z = 30

# Create a list containing our variables, which contain our values
>>> my_list = [x, y, z]
>>> type(my_list)
<class 'list'>
>>> print(my_list)
[10, 20, 30]

# my_list is a Python object with a physical memory address
>>> id(my_list)
2008429200776

# We can also perform operations on my_list
>>> sum(my_list)
60
```

For a great overview of all of Python's types take a look at this Python doc on [The standard type hierarchy](https://docs.python.org/2.0/ref/types.html) at Python.org. It is an older document but an excellent full outline.

### Object Values

The actual data, say the number 10, is the *value* of the object, for example our variable `x` above. 

As I mentioned briefly when I discussed tuples, the data held in some types of objects can be changed, but not all. Once a string of text is assigned to a variable, the text cannot be modified. The variable can be assigned a new value (essential over-writing the original), which will point to a new memory location, but the letters inside the original memory location cannot be modified (say from `cat` to `bat`). Tuples are the same, as are the basic data types we covered earlier, `int`, `float`, and `bool`. 

The data contained in lists and dictionaries *can* be modified. This makes them very handy for information that is dynamic and needs to change from time to time. Strings and tuples are said to be *immutable* and lists are said to be *mutable*. 

In order to use computer resources efficiently containers don't actually hold the values you place in them, they hold lists of ids that point to the memory locations of the container's discrete members, for example the number 10 in a list of numbers. So the act of changing the content of a container that can be modified such as a list just changes the pointer in the list to the new value's id (address) in memory.

```python
# Create a variable and assign it a value
>>> x = 10

# Check its type
>>> type(x)
<class `int`>

# Create some more variables
>>> y = 20
>>> z = 30

# Create a list containing our variables
>>> my_list = [x, y, z]
>>> print(my_list)
[10, 20, 30]

# my_list is a Python object with a physical memory address
>>> id(my_list)
2008429200776

# my_list's space in memory does not contain copies of the variables that it
# holds, it contains pointers to the variables' own locations in memory. We
# can see that 'x' is still in the same place it was in our previous example.
>>> id(x)
1526820608

# We can also perform operations on my_list
>>> sum(my_list)
60
```

#### Conclusion

An *object* in object-oriented programming is really just a package of code at a memory location that holds information and instructions a program is using. Objects are grouped into *types* that define the ways they can be used. Basic data type in Python (their names vary in different languages) include `str`, `int`, `float`, and `bool`. Three container object types in Python include `list`, `dict` and `tuple`. List and dictionary container types are mutable; string, number, conditional and tuple types are immutable and cannot be modified (they can however be recreated with the same name but different values and ids).

For more information browse over these excellent sources:
- [The Python Data Model: Objects, Values and Types](https://docs.python.org/dev/reference/datamodel.html)
- [Python Data Types](https://docs.python.org/3/library/datatypes.html)
- [Python Built-in Types](https://docs.python.org/3/library/stdtypes.html#hashing-of-numeric-types)