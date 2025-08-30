---
layout: default
title: Chapter 5 - Collections
---

# Chapter 5: Collections

In Python, a series of data can be organized in a **collection**. There are four commonly-used collections: strings, lists, tuples, and dictionaries.

## Strings

Recall from chapter 2 that strings are sequences of characters enclosed in quotation marks. While we initially introduced strings as a basic data type alongside integers and floats, strings are actually **non-primitive** data types that belong to the family of collections.

Unlike primitive data types (integers, floats, Booleans) that store a single value, strings are **collections of characters**. Each character in a string occupies a specific position (index), making strings **ordered sequences**. This collection nature allows strings to share many behaviors with other collections like lists—they can be indexed, sliced, traversed, and measured for length using the same methods.

For example, the string `"Hello"` is actually a collection containing five characters: `'H'`, `'e'`, `'l'`, `'l'`, and `'o'`, each accessible by their index position (0, 1, 2, 3, 4 respectively).

### String Concatenation

Strings can be **concatenated** using the `+` operator. A combination of strings and string variables can also be concatenated. However, data of other types, such as integers or floats, must be converted to strings before concatenation using the `str(<any>)` function. Like numerical addition, `+=` can be used if the same variable is used to store concatenation done on the *right* side of a string.

```python
my_string = "Hello " + "world!"
print(my_string)

my_string2 = my_string + " How are you doing?"
print(my_string2)

my_string2 += " I'm doing fine!"
print(my_string2)

my_age = 15
my_string3 = my_string2 + " I am " + str(my_age) + " years old!"
print(my_string3)
```

**Output:**
```
Hello world!
Hello world! How are you doing?
Hello world! How are you doing? I'm doing fine!
Hello world! How are you doing? I'm doing fine! I am 15 years old!
```

**Python 3.6 and above** support **f-strings** to simplify string concatenations of both constants and variables. An `f` is attached before the opening quotation mark to initiate an f-string. Unlike the previous method, non-string variables do not require conversion to a string. F-strings are perceived as a string type.

```python
my_age = 15
my_string = f"I am {my_age} years old!"
print(my_string)
print(type(my_string))
```

**Output:**
```
I am 15 years old!
<class 'str'>
```

### String Traversal

Strings can be traversed by characters using a for loop, similar to how we'll see lists can be traversed by elements.

```python
my_string = "Hello"
for letter in my_string:
    print(letter)
```

**Output:**
```
H
e
l
l
o
```

Like we'll see with lists, `enumerate` can be used to obtain both index and character of a string per cycle.

### Substrings

Like other collections, one can obtain a character from a string using its corresponding index. This indexing behavior mirrors what we'll see with list elements.

A **substring** is a string consisting of some characters from another string, comparable to how sublists contain some items of other lists.

Substrings can be obtained using indexing at a character level, using the same slicing syntax we'll see for lists.

```python
my_string = "Hello world!"
print(my_string[7])
print(my_string[:5])
print(my_string[6:11])
```

**Output:**
```
o
Hello
world
```

### String Built-in Functions

There are several built-in functions for strings. Below are commonly used string functions:

- **`len(<string>)`** returns the **length** of a string (number of characters).

```python
my_string = "Hello"
print(len(my_string))
```

**Output:**
```
5
```

- **`<string>.upper()`** converts all characters to uppercase.

```python
my_string = "Hello World"
print(my_string.upper())
```

**Output:**
```
HELLO WORLD
```

- **`<string>.lower()`** converts all characters to lowercase.

```python
my_string = "Hello World"
print(my_string.lower())
```

**Output:**
```
hello world
```

- **`<substring> in <string>`** checks whether the string contains a specific substring.

```python
my_string = "Hello World"
if "World" in my_string:
    print("Found 'World' in the string!")
```

**Output:**
```
Found 'World' in the string!
```

## Lists

A **list** is an array consisting of data **in a specific order**. Like strings, an **element** of a list can be retrieved by using **index**, a number that represents the *position* of the element in the list's order. As with strings, indices are **0-based**; the first element has index 0, the second has 1, and so on.

Using indices, elements of the lists can be retrieved or replaced using **get and set methods**. See below example to see how they're done:

```python
my_list = [1, 2, 3]

# Get method
print(my_list[0])  # Access the first element
print(my_list[1])  # Access the second element
print(my_list[-1]) # Access the LAST element
print(my_list[-2]) # Access the SECOND LAST element

# Set method
my_list[1] = 4
print(my_list)
```

**Output:**
```
1
2
3
2
[1, 4, 3]
```

A list may contain items of different data types, including lists.

```python
my_list = [1, 2.4, "Coding", [2, 5]]
```

### List Traversal

Like strings, lists are iterables, so one can use for-loops to traverse through a list.

```python
my_list = [1, 2, 3]
for elem in my_list:
    print(elem)
```

**Output:**
```
1
2
3
```

If you need access to each element's index per cycle, you can use `enumerate` just like with strings:

```python
my_list = ["a", "b", "c"]
for i, elem in enumerate(my_list):
    print(i, elem)
```

**Output:**
```
0 a
1 b
2 c
```

In the above code, `i` stores the index of the element in each iteration. For example, when `elem = "a"`, then `i = 0`.

### Sublists

A sublist can be retrieved by using a range of indices, using the same slicing syntax we saw for substrings.

```python
my_list = ["a", "b", "c", "d", "e"]
print(my_list[1: 4])  
print(my_list[4: 1: -1]) 
print(my_list[1: 4: 2])   
```

**Output:**
```
['b', 'c', 'd']
['e', 'd', 'c']
['b', 'd']
```

An empty start or end index will automatically include all elements from beginning or to end, respectively.

```python
print(my_list[:3])
print(my_list[2:])
print(my_list[::-1])
```

**Output:**
```
['a', 'b', 'c']
['c', 'd', 'e']
['e', 'd', 'c', 'b', 'a']
```

### 2D and nD Lists

A 1D list may not be suitable for representing grids or tables. Instead, a 2D list can be constructed by leveraging the property of lists that allows them to contain other lists as elements. See how indexing and traversing (using nested for-loops) are done below:

```python
my_list = [["a", "b", "c"],
           ["d", "e", "f"],
           ["g", "h", "i"]]

print(my_list[0][0])
print(my_list[1][-1])
print()

for i, row in enumerate(my_list):
    for j, elem in enumerate(row):
        print(i, j, elem)
```

**Output:**
```
a
f

0 0 a
0 1 b
0 2 c
1 0 d
1 1 e
1 2 f
2 0 g
2 1 h
2 2 i
```

By incorporating additional lists within the inner lists, lists with dimensions of three or higher can be constructed.

### List Built-in Functions

There are several built-in functions for lists. Below are commonly used list functions:

- **`len(<list>)`** returns the **length** of a list. A length is the number of elements in the list.

```python
my_list = ["a", "b", "c", "d"]
print(len(my_list))
```

**Output:**
```
4
```

- **`<list>.append(<any>)`** adds an element at the end of the list.

```python
my_list = ["a", "b", "c", "d"]
my_list.append("e")
print(my_list)
```

**Output:**
```
['a', 'b', 'c', 'd', 'e']
```

- **`<list>.insert(<int>, <any>)`** adds an element at the position of given index in the list. The subsequent parts of the list are pushed backward.

```python
my_list = ["a", "c", "d"]
my_list.insert(1, "b")
print(my_list)
```

**Output:**
```
['a', 'b', 'c', 'd']
```

- **`<list>.pop(<int>=-1)`** removes the element at given index of the list and returns it. If no index is given, it removes the element at *last* index.

```python
my_list = ["a", "b", "c", "d"]
my_list.pop(0)
print(my_list)
my_list.pop()
print(my_list)
```

**Output:**
```
['b', 'c', 'd']
['b', 'c']
```

- **`<any> in <list>`** checks whether the list has at least one element of a certain value.

```python
my_list = ["a", "b", "c", "d"]
if "b" in my_list:  # True
    print("my_list has a \"b\".")
if "e" in my_list:  # False
    print("my_list has an \"e\".")
```

**Output:**
```
my_list has a "b".
```

Note that there are many more built-in functions, so it's strongly recommended to search for the function not listed in this guide based on your specific needs.

## Tuples

Lists are **mutable**; in other words, the size (length) of lists can be changed after initialized using functions such as `append()`.

A **tuple**, while similar to lists, is an **immutable** collection. Once initialized, their length and elements cannot be changed. However, reassigning a tuple to a variable allows for replacing the entire tuple.

```python
my_tuple = (0, 0)
print(my_tuple)
print(my_tuple[0])
my_tuple = (0, 1)
print(my_tuple)
my_tuple[0] = 1     # Throws error!
print(my_tuple)
```

**Output:**
```
(0, 0)
0
(0, 1)
TypeError: 'tuple' object does not support item assignment
```

Tuples can be substituted with lists in most use cases, which allows for more flexible actions. However, using tuples can help reduce memory usage.

## Dictionaries

Lists have their elements **ordered** via their index system. On the other hand, a **dictionary**--a.k.a. *hashmap* or *map*--is an **unordered** collection where each of its elements consist of **key-value pairs**. Imagine that a list's indices are the "keys" to access or modify its elements. Similarly, accessing or modifying a value of a dictionary can be done by using the corresponding key. Just like the indices of all elements in a list are unique, **every key in a dictionary should also be unique**. Below shows the structure of dictionaries:

```python
{keyA: valueA, keyB: valueB}
```

where each key and value is separated by `:`.

```python
my_list = ["a", "c", "e"]
print(my_list[1])  # 1 is the "key" to access the element "c".

my_dict = {"Andrew": 8, "Brian": 5, "Charlie": 10}
print(my_dict["Brian"])  # "Brian" is the key of the dictionary to access the corresponding value 5.

my_dict["Brian"] = 9
print(my_dict["Brian"])
```

**Output:**
```
c
5
9
```

The keys of a dictionary can consist of any *immutable* data types (including tuples) and the mix of the types. The values of a dictionary can consist of any data types.

```python
my_dict = {"David": 9, 
           8: ["Hello", "Hi"], 
           (1, 2): 2.4
}  # This is a valid dictionary.

print(my_dict[(1, 2)])
```

**Output:**
```
2.4
```

While dictionaries are **unordered collections**, they can be iterated using for loops, saving either key, value, or key-value pair (in form of tuple) as an iterable per cycle:

```python
my_dict = {"Andrew": 8, "Brian": 5, "Charlie": 10}

# Key as the iterable
for key in my_dict:  # 'my_dict' may be replaced with 'my_dict.keys()'
    print(key)

# Value as the iterable
for value in my_dict.values():
    print(value)

# Key-Value pair (tuple) as the iterable
for item in my_dict.items():
    print(item)
```

**Output:**
```
Andrew
Brian
Charlie
8
5
10
('Andrew', 8)
('Brian', 5)
('Charlie', 10)
```

While `keys()`, `values()`, and `items()` return iterables, they are **not** lists. However, they can be converted to lists via `list()`.

```python
my_dict = {"Andrew": 8, "Brian": 5, "Charlie": 10}

keys = my_dict.keys()
print(type(keys), keys)

key_list = list(keys)
print(type(key_list), key_list)
```

**Output:**
```
<class 'dict_keys'> dict_keys(['Andrew', 'Brian', 'Charlie'])
<class 'list'> ['Andrew', 'Brian', 'Charlie']
```

### Dictionary Built-in Functions

`len`, `pop`, and `in` functions used for strings and lists can be applied for dictionaries. Note that the `pop` function takes the *key* of a pair to remove an item from the dictionary (unlike lists, not including the key argument will result in error, but it is possible to set a "default" value to return if key is not found), while the `in` function asserts whether a *key* exists in the dictionary.

Sometimes, one cannot expect that a certain key exists and want to handle cases of getting a value without throwing errors. In such cases, use `get(<key>, <default_value=None>)`, which will work in the similar fashion as the traditional get method using `[<key>]`, except when the requested key does not exist, it will return `None` or the default value, if specified.

```python
my_dict = {"Andrew": 8, "Brian": 5, "Charlie": 10}

print(len(my_dict))

print(my_dict.pop("Brian"))
print(my_dict)

print(my_dict.pop("Daniel", -1))  # Since "Daniel" is not a key in my_dict, the "default" value -1 is returned.

print("Charlie" in my_dict, "Brian" in my_dict)

print(my_dict.get("Daniel"))
print(my_dict.get("Daniel", 0))
```

**Output:**
```
3
5
{'Andrew': 8, 'Charlie': 10}
-1
True False
None
0
```

Since dictionaries are unordered, `append` or `insert` functions cannot be used. Instead, the set method with an unintroduced key can be used to add new key-value pair.

```python
my_dict = {"Andrew": 8, "Brian": 5, "Charlie": 10}

my_dict["Daniel"] = 12
print(my_dict)
```

**Output:**
```
{'Andrew': 8, 'Brian': 5, 'Charlie': 10, 'Daniel': 12}
```

## Sets

A **set**, a.k.a. *hashset*, contain elements that are distinct from each other. Therefore, using a set is preferred if all elements have to be unique when adding elements to it. Like dictionary keys, tuples and other immutable data can be stored in sets.

```python
my_set = set()
print(type(my_set))

my_set2 = {1, 2, 3, 4, 1}
print(type(my_set2), my_set2)  # Prints the type and itself.
```

**Output:**
```
<class 'set'>
<class 'set'> {1, 2, 3, 4}
```

Since sets are **unordered**, and each item does not have unique keys, accessing a single item in a set is not possible. However, one can iterate through a set via a for-loop (consistent order of iterations is not guaranteed) and confirm whether a specific value is contained inside a set.

```python
my_set = {1, 2, 3, 4, 1}
print(my_set)

for num in my_set:
    print(num)

print(2 in my_set)
print(5 in my_set)
```

**Output:**
```
{1, 2, 3, 4}
1
2
3
4
True
False
```

### Set Built-in Functions

`add()` and `remove()` will add a value to a set or remove from it, respectively. Remember that sets keep all its elements unique, so adding an existing value will do nothing to it (but won't throw an error). Note that attempting to remove a value that does not exist in a set will throw an error.

```python
my_set = {1, 2, 3, 4}
print(my_set)

my_set.add(5)
print(my_set)

my_set.add(3)
print(my_set)

my_set.remove(3)
print(my_set)
```

**Output:**
```
{1, 2, 3, 4}
{1, 2, 3, 4, 5}
{1, 2, 3, 4, 5}
{1, 2, 4, 5}
```

Like mathematical sets, there are built-in set methods that do operations such as creating a union or intersection of two sets, or checking if one set is a superset or subset of another set. Search them up for more details about them!

---

## Navigation

⬅️ **[Previous: Chapter 4 - Loops](chapter-04)**

⬅️ **[Back to Table of Contents](table-of-contents)**

➡️ **[Next: Chapter 6 - Functions](chapter-06)**