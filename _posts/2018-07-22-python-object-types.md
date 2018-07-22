---
image: card-file.jpg
title: "Python: Understanding Objects and Types"
---

Python is an *object-oriented-programming* (OOP) language. An *object* in computer programming essentially refers to a package of information--or *data*, that is active in the computer's memory (has a location and address, just like an apartment in a city) and that some program is aware of. A Python program sees everything that it knows of (variables that have been assigned, functions or methods that have been called, lists or dictionaries that have been defined) as either objects or the relations between them. You can almost see objects as physical things from the fact that if they are instantiated (i.e., the program knows about them), they are occupying cells of space in the computer's RAM. All Python objects have three basic properties (which can be added to in making the object more functional): an identity (its address), a type and a value.

![Photo by NASA on Unsplash]({{ site.baseurl }}/assets/images/nasa-43569-unsplash.jpg) 

#### An Object's Identity
An object's *identity*, or `id()`, is essentially its numeric address in memory (RAM). That is, where it can be found and accessed when it is needed.

```python
>>> x = 10
>>> id(x)
1526820608
```

The physical memory cell addressed (numbered) at 1526820608 is the the beginning cell in memory the computer will go to to access the information for the variable `x`. 

#### Object Types
An object's *type* describes what category the information in that object falls into; this defines what operations can be performed on it. If the object contains text its type is `str` (pronounced like 'stir'). If it is a decimal fraction it is a `float`. If it is a whole number it is an `int`. `True` and `False` are called *conditionals* and are type `bool`.

Python also provides object types that are *containers* for other objects like the ones we just covered (strings, numbers, etc.). Three commonly used container types in Python include *lists*, *dictionaries* and *tuples*. Lists, or type `list`, are groups of zero or more distinct pieces of data such as the names of all of the elements, or all of the meta information about a music album. Dictionaries, or type `dict` are *key: value* pairs such as the names of all of the elements as keys with their atomic numbers as values, or that music album's meta-information including labels as keys for each piece of data like **Title** or **Year**. Tuples (pronounced 'toople' or 'tupple', whichever pleases you), or type `tuple` are similar to lists in that they hold groups of discrete data, however they cannot be modified after they are created (they are great for data that shouldn't be changed because it can't be) and are also faster to search through large datasets due to less overhead than modifiable lists.

In order to use computer resources efficiently containers don't actually hold the information you place in them, they hold lists of ids that point to the memory locations of the container's members. So the act of changing the content of a container that can be modified such as a list just changes the pointer in the list to the new content.

```python
# Create a variable and assign it a value
>>> x = 10

# Check its type
>>> type(x)
<class 'int'>

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

#### Object Values

The actual data, say the number 10, is the *value* of the object, for example our variable `x` above. 

As I mentioned briefly when I discussed tuples, the data held in some types of objects can be changed, but not all. Once a string of text is assigned to a variable, the text cannot be modified. The variable can be assigned a new value (essential over-writing the original), which will point to a new memory location, but the letters inside the original memory location cannot be modified (say from `cat` to `bat`). Tuples are the same, as are the basic data types we covered earlier, `int`, `float`, and `bool`. 

The data contained in lists and dictionaries *can* be modified. This makes them very handy for information that is dynamic and needs to change from time to time. Strings and tuples are said to be *immutable* and lists are said to be *mutable*. 

#### Conclusion

Objects in object-oriented programming are really just memory addresses that hold information a program is using. Objects are grouped into types that define what can and cannot be done to them. Basic data type in Python (their names vary in different languages) include `str`, `int`, `float`, and `bool`. Three container object types in Python include `list`, `dict` and `tuple`. List and dictionary container types are mutable; string, number, conditional and tuple types are immutable and cannot be modified (they can be recreated with the same name but different values however).

For more information browse over these excellent sources:
- [The Python Data Model: Objects, Values and Types](https://docs.python.org/dev/reference/datamodel.html)
- [Python Data Types](https://docs.python.org/3/library/datatypes.html)
- [Python Built-in Types](https://docs.python.org/3/library/stdtypes.html#hashing-of-numeric-types)