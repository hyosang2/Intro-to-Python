# Chapter 6: Functions

If you've studied about algebra before, you may be familiar with **functions**. They allow assessing the results for every possible inputs (parameters), making them reusable tools for repeated operations.

```
f(x) = x + 6
g(x, y) = x + 2y

f(5) = 11
f(8) = 14

g(5, 3) = 11
g(13, 17) = 47
```

Such mathematical concepts can be applied to Python, executing a consistent algorithm incorporating inputs and outputs. Functions are also known as **methods**. It is similar to the custom blocks (My Blocks) in Scratch.

## Function Structure

To use a function, one should construct it by defining what inputs it takes, how it works, and what it outputs. It is similar to the "Define" blocks in Scratch.

### Header

A header in Python is structured as below:

```python
def <function_name>(<argument>...):
```

where `function_name` is the name of the function, and `argument` are the arguments of the function. Below is an example of the header:

```python
def add_six(x):
```

An **argument** is an input variable--in any type--of the function, where its actual value is plugged in from the **parameters** of function callers. A function may have multiple arguments or no arguments.

In Python 3, arguments can be set with a certain data type like below:

```python
def add_six(x: int):
```

Such ensures consistent data type of the parameters when calling the function. It is optional; however, it is generally advised to treat the arguments as if it has consistent data type while running the function (e.g., if argument `a` is assumed as an int type, do not use `len` method).

### Return Statement

Functions have inputs in form of arguments and outputs in form of **return** statements. Once a function has information to output, it can return in the form of below:

```python
return <any>
```

Below shows an example function body with return statement:

```python
to_return = x + 6
return to_return
```

Once the computer reaches a return statement of a function, it will **immediately exit** from the function and carry out the return value. All lines inside the function body after the return statement will be ignored.

Like arguments, functions can have multiple return statements, usually one per branch of the logic tree. In each return statement, multiple values can be returned, separated by a comma:

```python
return <any>, <any>, ...
```

which will yield a **tuple** of return values.

The data type of the returned items, by convention, are called **return types**. While it's possible for a function's return type to vary depending on the parameters, it's generally recommended to maintain consistency in return types per function.

In Python 3, return types can be set with a certain data type like below:

```python
def add_six(x: int) -> int:
```

Like argument type setters, this is optional, but it is also generally advised to make functions have consistent return types.

Below is the complete Python function with the same purpose as f(x) and g(x) from the beginning of this section. It's important to note that the return value can be a variable or an operation, as long as it simplifies to the desired return type.

```python
def add_six(x):
    to_return = x + 6
    return to_return

def add_2y(x, y):
    return x + 2 * y
```

See the next subsection to learn how to call a function.

## Function Caller

At the beginning of the section, we made two algebraic functions, followed by their callers by plugging in numbers to the parameters. In this subsection, we will learn how to call functions in Python.

Function callers generally consist of below structure:

```python
<ret_var> = <func_name>(<param>...)
```

A function caller assigns a value to each parameter (`<param>`), which is then plugged into the corresponding (same position in order) argument of the function. After executing the function with the provided parameters, the return value is assigned to the return variable `<ret_var>`.

The subsequent lines can then utilize the value stored in the return variable for the subsequent operations. It's crucial to remember that, like variables, function names must be consistent to access them.

If a function returns multiple values at a time in form of a tuple, each item of the tuple can be assigned to independent variables like such:

```python
<ret_var_1>, <ret_var_2>..., <ret_var_n> = <func_name>(<param>...)
```

where `n` is the number of items in the tuple that is returned.

Below shows the callers of the previously defined example functions:

```python
def add_six(x):
    to_return = x + 6
    return to_return

def add_2y(x, y):
    return x + 2 * y

add_five_to_six = add_six(5)
print(add_five_to_six)

print(add_six(8))
print(add_2y(5, 3))
print(add_2y(13, 17))
```

**Output:**
```
11
14
11
47
```

Below shows an example function that solves quadratic equations and returns two values at a time:

```python
def solve_quadratic(a, b, c):
    discriminant = b**2 - 4*a*c
    if discriminant < 0:
        return None, None  # No real roots
    root1 = (-b + discriminant ** (1 / 2)) / (2 * a)
    root2 = (-b - discriminant ** (1 / 2)) / (2 * a)
    return root1, root2

x1, x2 = solve_quadratic(1, -3, 2)
print("Roots:", x1, x2)
```

**Output:**
```
Roots: 2.0 1.0
```

## Void Function

Functions without return statements are called **void functions**. Void functions are often used to run a series of other functions, modify variables defined outside the function, and other actions that do not need to return outputs, such as print statements.

To exit the void function in the middle of its body, return a null value (`return None`), or simply nothing (`return`). Any attempts to retrieve the "return value" of a void function will result in `None`.

```python
def introduce(name, age):
    print(f"Hello, my name is {name}.")
    if age >= 18:
        print("I can drive a car.")
        return None  # Exits from the function.
    if age >= 16:
        print("I can drive a car under supervision.")
        return       # Exits from the function.
    print("I can't drive a car.")

introduce("Andrew", 25)
return_value = introduce("Brian", 17)
print(return_value)
```

**Output:**
```
Hello, my name is Andrew.
I can drive a car.
Hello, my name is Brian.
I can drive a car under supervision.
None
```

---

## Navigation

⬅️ **[Previous: Chapter 5 - Collections](chapter-05.md)**

⬅️ **[Back to Table of Contents](table-of-contents.md)**

➡️ **[Next: Chapter 7 - Miscellaneous Topics](chapter-07.md)**