---
image: card-file.jpg
title: "Python: Understanding Objects and Types"
---

Python is an *object-oriented-programming* (OOP) language. An *object* in computer programming essentially refers to a package of information--or *data*, that is active in the computer's memory (has a location and address, just like an apartment in a city) and that some program is aware of. A Python program sees everything that it knows of (variables that have been assigned, functions or methods that have been called, lists or dictionaries that have been defined) as either objects or the relations between them. You can almost see objects as physical things from the fact that if they are instantiated, they are occupying cells of space in the computer's RAM. All Python objects have three basic properties (which can be added to in making the object more functional): an identity (its address), a type and a value.

![Photo by NASA on Unsplash]({{ site.baseurl }}/assets/images/nasa-43569-unsplash.jpg) 

#### An Object's Identity
An object's *identity*, or `id()`, is essentially its numeric address in memory (RAM). That is, where it can be found and accessed when it is needed.

```python
>>> x = 10
>>> id(x)
1526820608
```

#### Object Types
An object's *type* describes what category the information in that object falls into; this defines what operations can be performed on it. If the object is text its type is `str` (pronounced like 'stir'). If it is a decimal fraction it is a `float`. If it is a whole number it is an `int`. `True` and `False` are called *conditionals* and are type `bool`.

Python also provides object types that are containers for other objects like the ones we just covered. Three common container types in Python include *lists*, *dictionaries* and *tuples*. Lists, or `list`, are groups of zero or more distinct pieces of data such as the names of all of the elements, or all of the meta information about a music album. Dictionaries, or `dict` are *key: value* pairs such as the names of all of the elements as keys with their atomic numbers as values, or that music album's meta-information including labels as keys for each piece of data like **Title** or **Year**. Tuples (pronounced 'toople' or 'tupple', whichever pleases you), or `tuple` are similar to lists in that they hold groups of discrete data, however they cannot be modified after they are create (they are great for data that shouldn't be changed) and are faster to search.

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
