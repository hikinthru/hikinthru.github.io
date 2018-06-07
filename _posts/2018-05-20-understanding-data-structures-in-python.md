---
image: card-file.jpg
title: Understanding Python Data Structures, Containers and Collections
---
  
When I first began programming in Python I was sometimes confused by the way different authors and online sources referred to the various ways of holding, manipulating and processing sets of data. Three terms that kept coming up were **data structures**, **containers** and **collections**, and I was not completely sure they were always referring to the same things, even in technical documents. 

I did a bit of research and this article came out of that. This does not address the functionality of specific container types in Python here such as `list`, `deque`, `tuple`, etc., it simply clarifies the methods of organization of groups of data and the associated terminology.

![Image alt]({{ site.baseurl }}/assets/images/card-file.jpg) 

---

#### Contents

- [Terms](#terms)
- [Attributes of *All* Containers](#attributes-of-all-containers)
- [Built-in Container Types](#built-in-container-types)
- [NOT Containers](#not-containers)
- [The `collections` Module](#the-collections-module)
- [Built-in vs. Imported Object Types and Functions](#built-in-vs-imported-object-types-and-functions)

### Terms

At base, all three of these terms in Python refer to ways of placing data into sets that can be operated on. Three examples of types of data grouping in Python include dictionaries (`my_dict = {"uno":"one", "dos":"two"}`), lists (`my_list = [3, 4, "five"]`) and tuples (`my_tuple = (6, 7, "zed")`). 

I came to realize that the term **data structure** is used informally (even in official Python Documentation) to refer to *both or either* of `container` and `collections`. I then learned that regarding these, in one way containers are a type of collection and in another collections are types of containers.

This sounds confusing, but it is because all containers (generally) fall in to one of two groups in Python. One group is called **builtins** and the others are **imported**. If you are not sure about the difference between the idea of 'builtin' vs. 'imported' see [this](#built-in-vs-imported-object-types-and-functions) explanation below.

All containers are a type of collection in the technical sense that to determine if an object, for example `my_list` is a container, you ask Python, `isinstance(object, collections.Container)`. Which implies that by definition all containers are a Python sub-class of the class `collections`.

But you can also import the Python module `collections` to add additional container types to the *built-in containers* (e.g., `list`, `dict`, `tuple`, etc. that do not need to be imported). These additional types (e.g., `deque`, `Counter`, `defaultdict`) are often directly referred to as collections, even though they are really just containers with modified or additional functions.

### Attributes of *All* Containers

The following three rules apply to ALL objects that can be considered Python containers:

* Objects which have a `__contains__` method defined
* `isinstance(object, collections.Container)` returns `True`
* Can be searched or iterated with the `in` operator

See also:  
[PyDocs 3.6.5 - Built-in Types](https://docs.python.org/3/library/stdtypes.html)  
[PyDocs 3.6.5 - Data Structures](https://docs.python.org/3/tutorial/datastructures.html)

### Built-in Container Types

According to [PyDocs 3.6.5 on Container datatypes](https://docs.python.org/3.6/library/collections.html), Python’s general purpose built-in containers are: `dict`, `list`, `set`, and `tuple`. Four additional built-in container types mentioned in [PyDocs 3.6.5 - Built-in Types](https://docs.python.org/3/library/stdtypes.html) include `str`, `range`, `frozenset` and `bytearray`.

* *Basic sequence* type containers
  - Lists
  - Tuples
  - Ranges
* *Text sequence* type containers
  - Strings
* *Binary sequence* type containers
  - Bytearrays
* *Set* type containers
  - Sets
  - Frozensets (immutable)
* *Map* type containers
  - Dictionaries

### NOT Containers

This is a list of built-in object types which are **not** containers:
`isinstance(object, collections.Container` returns `False`:

* Int objects
* Float objects
* Long objects
* Boolean objects
* Module objects
* File objects
* Buffer objects
* The None object

### The `collections` Module

The Python module `collections` can be imported (like `math`) to add additional collection/container types available. The types in Python 3.5.6 are listed here.

| **Type** | **Description** |
|--|--|
| namedtuple( | factory function for creating tuple subclasses with named fields
| deque | list-like container with fast appends and pops on either end
| ChainMap | dict-like class for creating a single view of multiple mappings
| Counter | dict subclass for counting hashable objects
| OrderedDict* | dict subclass that remembers the order entries were added
| defaultdict | dict subclass that calls a factory function to supply missing values
| UserDict | wrapper around dictionary objects for easier dict subclassing
| UserList | wrapper around list objects for easier list subclassing
| UserString | wrapper around string objects for easier string subclassing

### Built-in vs. Imported Object Types and Functions

When the Python interpreter begins running it loads a lot of functionality into the running computer's memory (RAM). But to keep from being a memory hog it must pick and choose (or rather its developers already have) what functionality will be loaded by default. We essentially get a 'base model' when we start Python. Everything in this base model is considered 'builtin.'

The options deemed important enough in common use to include on a base load of Python is not however all that the local version of Python contains for achieving a developer's goals. Many programs may need to use the functionality of Python's pi class (a class is a list of functionality for a command, such as `pi`), but not all programs. A developer who would like to use the Python class of `pi` in their program (without having to compute and program in its value themselves every time they need it) would import the Python module named `math`. The `math` module includes classes and functions to find cosines, tangents, arithmetic ceilings or floors, factorials, pi, etc.

If they are needed, Python modules such as `math` and `collections` can be added with the `import` command during the writing of the program, and every time the program runs these modules are added on to the code that the developer wrote.
