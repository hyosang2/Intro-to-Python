---
layout: default
title: Chapter 2 - Classes
---

# Chapter 2: Classes

To start using OOP, developers dive into **classes**. A class is a "blueprint" that is used to create objects.

Recall functions from the Intro to Python guide. To utilize a function, we first *define* it with a header that consists of a name and arguments, a body of algorithm, and a series of return-statements. Then, we call the function to actually use it.

Now, the procedure of definition and utilization is seen at a much larger scope, where a class falls under the definition step.

A class, like functions, starts with a header:

```python
class <ClassName>:
```

where `<ClassName>` is the name of the class. Unlike names of variables or functions, by common practice, we capitalize each word in the name and do *not* use `_` to represent the space.

In general, a class consists of *class variables, instance variables, an __init__ method, and instance methods*.

## Class and Instance Variables

Remember our animal simulator from Chapter 1. Each pet has different traits that can be organized into categories. For example, all pets have names, ages, and favorite foods. By organizing these traits, we can easily manage each pet in our program.

**Instance variables** are unique to each object created from a class. Since a class doesn't represent a single object, instance variables can also depend on the parameters provided when creating an object. For instance, an instance variable named `favorite_food` can be defined. Then, when creating objects for pets, each pet's actual favorite food can be initialized with a specific value.

**Class variables** are similar to instance variables, except that all objects created from the class share the same value. It is also known as **static variables** in other languages.

One way to distinguish between instance and class variables is to observe the presence of the `self` tag in front of the variable name, assuming that the variable is within the scope of a class. If the `self` syntax is included in a variable or function, it means that such will be **unique to each object**.

## The `__init__()` Method

An `__init__()` method, also known as the **constructor**, is a function that is run when an affiliated object is *initialized*. In general, `__init__()` methods take optional arguments for the object creation and assign them into the corresponding instance variables. For some cases, such arguments are taken in as a dependent for actions taken when creating an object. A class should have exactly one `__init__()` method.

The format to define an `__init__()` method is the following:

```python
def __init__(self, <arguments>):
```

where `<arguments>` are replaced with the actual arguments.

The `self` argument, like the `self` tag for instance variables, implies unique execution of the `__init__()` method for each object creation. When taking object creation parameters, the first parameter matches the *second* argument of the `__init__()` method, ignoring the `self` argument.

Now, let's create a `Pet` class that will be used to create our virtual pets as objects.

```python
class Pet:
    # Like if-statements, while- or for-loops, the class header that ends with a ":" is followed with the body which are indented.
    
    pet_count = 0
    
    def __init__(self, name, age, animal_type, favorite_food):
        self.name = name
        self.age = age
        self.animal_type = animal_type
        self.favorite_food = favorite_food

        print(f"{self.name} is a {self.age} year old {self.animal_type} who loves {self.favorite_food}!")

        Pet.pet_count += 1

# Since the code below is at the same indentation level as the class header, it is now outside the scope of the class.
buddy = Pet("Buddy", 3, "dog", "chicken")
print(f"Total pets: {Pet.pet_count}")
print(f"Pet name: {buddy.name}, Age: {buddy.age} years old")
```

**Output:**
```
Buddy is a 3 year old dog who loves chicken!
Total pets: 1
Pet name: Buddy, Age: 3 years old
```

Here, the `Pet` class is created, and the `__init__()` method does the following:

1. It accepts `name`, `age`, `animal_type`, and `favorite_food` as parameters and sets each into instance variables.

2. Next, a print statement prints what kind of new pet is created.

3. Outside `__init__()` method, a class variable `pet_count` is initialized to 0, and the `__init__()` method updates the `pet_count` for each creation of `Pet` object.

To avoid misrepresentations, class variables are defined outside the scope of `__init__()` method, whereas instance variables are defined inside.

Creating an object of `Pet` class named `buddy` at line 17 executes the `__init__()` method. Then, lines 18 and 19 print the class and instance variables of `buddy`, respectively. Notice that, being outside the scope of the class, the class variables have the tag that is the name of the **class**, and instance variables have the tag of the **object** name.

## Instance Methods

**Instance methods** are functions that are unique to each object created from a class, just like instance variables. In general, such uniqueness depend on the instance variables of the same object.

In our pet simulator example, while instance variables represent the **characteristics** of each pet, instance methods will represent the **behaviors** of each pet.

The function header of an instance method is defined as following:

```python
def <fn_name>(self, <arguments>...):
```

where `<fn_name>` represents the function name, and `<arguments>...` denotes the sequence of arguments. Like instance variables and the `__init__()` method, the `self` tag indicates that these methods are exclusive to each object and is disregarded when comparing parameters from function calls.

Let's look at an example of instance method. Assume that the same variables and the `__init__()` method from last example were used.

```python
import random   # See Intro to Python guide

class Pet:
    # Class and instance variables and __init__() method placed here

    def play(self):
        if self.age < 5:
            print(f"{self.name} is playing happily!")
        else:
            print(f"{self.name} is taking a nap.")
    
    def eat(self, food):
        if food == self.favorite_food:
            print(f"{self.name} loves eating {food}!")
        else:
            print(f"{self.name} doesn't really like {food}.")

buddy = Pet("Buddy", 3, "dog", "chicken")
buddy.play()
buddy.eat("chicken")
buddy.eat("broccoli")
```

**Output:**
```
Buddy is a 3 year old dog who loves chicken!
Buddy is playing happily!
Buddy loves eating chicken!
Buddy doesn't really like broccoli.
```

Here, we have two instance methods: `play` which doesn't take any arguments, and `eat` which takes a `food` argument. The `play` method checks the pet's age, while the `eat` method compares the given food with the pet's favorite food. These methods demonstrate how instance variables are used within instance methods to create unique behaviors for each object.

## Access Tags Summary

| **Scope** | **Member Type** | **Access Tag** | **Example** |
|-----------|-----------------|----------------|-------------|
| Inside class (outside methods) | Class variable | Class name | `MyClass.var` |
| Inside class (outside methods) | Instance variable | Invalid | N/A |
| Inside class (outside methods) | Instance method | Invalid | N/A |
| Inside instance method (including __init__ method) | Class variable | Class name | `MyClass.var` |
| Inside instance method (including __init__ method) | Instance variable | `self` | `self.var` |
| Inside instance method (including __init__ method) | Instance method | `self` | `self.method()` |
| Outside class | Class variable | Class name | `MyClass.var` |
| Outside class | Instance variable | Instance name | `obj.var` |
| Outside class | Instance method | Instance name | `obj.method()` |

*Assume `MyClass` is the name of the class, and `obj` is the name of the object created from `MyClass`.*

---

## Navigation

⬅️ **[Previous: Chapter 1 - OOP Introduction](chapter-01.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 3 - Objects](chapter-03.md)**