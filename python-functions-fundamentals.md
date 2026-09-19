
# Python Functions Fundamentals

This note covers the core concepts of functions in Python, including function types, imports, parameters, return values, scope, `*args`, `**kwargs`, type hints, and more.

## 1. What is a Function?

A function is a reusable block of code that performs a specific task.

You can think of it like:

```text
Input -> Function -> Output
```

Basic example:

```python
def say_hello():
    print("Hello!")

say_hello()
```

Output:

```text
Hello!
```

---

## 2. Function with Parameters

A parameter allows a function to receive information.

```python
def greet(name):
    print("Hello", name)

greet("Alan")
greet("John")
```

Output:

```text
Hello Alan
Hello John
```

Here:

* `name` is a parameter.
* `"Alan"` and `"John"` are arguments.

---

## 3. Function with `return`

The `return` statement sends a value back to the caller.

```python
def add(a, b):
    return a + b

result = add(10, 20)

print(result)
```

Output:

```text
30
```

A shorter version:

```python
def add(a, b):
    return a + b
```

---

## 4. `print()` vs `return`

`print()` displays a value:

```python
def add(a, b):
    print(a + b)
```

`return` gives the value back so it can be reused:

```python
def add(a, b):
    return a + b

result = add(10, 20)
result = result * 2

print(result)
```

Output:

```text
60
```

Use `return` when the result needs to be used later.

---

# Major Types of Functions in Python

## 5. Built-in Functions

Python provides many functions automatically.

Examples:

```python
print("Hello")
len("Python")
type(10)
int("25")
max(10, 20, 30)
```

Common built-in functions include:

```python
print()
len()
type()
input()
range()
sum()
min()
max()
int()
str()
float()
```

---

## 6. User-Defined Functions

These are functions you create using `def`.

```python
def greet():
    print("Hello!")

greet()
```

With parameters:

```python
def greet(name):
    print("Hello", name)

greet("Alan")
```

With a return value:

```python
def multiply(a, b):
    return a * b

result = multiply(5, 4)
print(result)
```

---

## 7. Lambda Functions

Lambda functions are small anonymous functions.

Normal function:

```python
def square(x):
    return x * x
```

Lambda equivalent:

```python
square = lambda x: x * x

print(square(5))
```

Output:

```text
25
```

Lambda functions are useful for short operations, but normal `def` functions are usually easier to read.

---

## 8. Methods

A method is a function that belongs to an object.

String method:

```python
name = "alan"

print(name.upper())
```

List method:

```python
numbers = [10, 20]

numbers.append(30)

print(numbers)
```

Examples:

```python
str.upper()
str.lower()
list.append()
list.remove()
dict.get()
```

---

# Importing Functions

## 9. Using `import`

You can import an entire module:

```python
import math

result = math.sqrt(25)

print(result)
```

Output:

```text
5.0
```

When you import the full module, use:

```python
module.function()
```

For example:

```python
math.sqrt(25)
math.ceil(4.2)
math.floor(4.8)
```

---

## 10. Using `from ... import`

You can import a specific function:

```python
from math import sqrt

result = sqrt(25)

print(result)
```

Output:

```text
5.0
```

You no longer need to write:

```python
math.sqrt(25)
```

You can write:

```python
sqrt(25)
```

---

## 11. Import Multiple Functions

```python
from math import sqrt, ceil, floor

print(sqrt(25))
print(ceil(4.2))
print(floor(4.8))
```

Output:

```text
5.0
5
4
```

---

## 12. Import with `as`

You can give a module another name:

```python
import math as m

print(m.sqrt(25))
```

This is common with libraries such as NumPy:

```python
import numpy as np
```

Then:

```python
np.array([1, 2, 3])
```

---

## 13. `import math` vs `from math import sqrt`

Using:

```python
import math
```

requires:

```python
math.sqrt(25)
```

Using:

```python
from math import sqrt
```

allows:

```python
sqrt(25)
```

There is usually no meaningful performance difference.

Both load the `math` module if it has not already been loaded.

The main difference is readability and namespace management.

Prefer:

```python
import math
```

when using many functions from the module.

Prefer:

```python
from math import sqrt
```

when only using a small number of functions.

Avoid:

```python
from math import *
```

because it imports many names into your namespace and may create conflicts.

---

# Function Parameters and Arguments

## 14. Multiple Parameters

```python
def add(a, b):
    return a + b

print(add(10, 20))
```

Here:

```text
a, b      -> parameters
10, 20    -> arguments
```

---

## 15. Returning Multiple Values

A function can return multiple values:

```python
def calculate(a, b):
    total = a + b
    product = a * b

    return total, product

x, y = calculate(5, 3)

print(x)
print(y)
```

Output:

```text
8
15
```

---

## 16. Default Parameters

Parameters can have default values:

```python
def greet(name, message="Hello"):
    print(message, name)

greet("Alan")
greet("Alan", "Good morning")
```

Output:

```text
Hello Alan
Good morning Alan
```

---

## 17. Positional Arguments

Arguments can be passed based on position:

```python
def student(name, age):
    print(name, age)

student("Alan", 25)
```

Python understands:

```text
name = "Alan"
age = 25
```

---

## 18. Keyword Arguments

You can explicitly specify parameter names:

```python
def student(name, age):
    print(name, age)

student(age=25, name="Alan")
```

This can make function calls easier to understand.

---

# Variable Scope

## 19. Local Variables

Variables created inside a function are usually local.

```python
def test():
    message = "Hello"
    print(message)

test()
```

This will fail:

```python
def test():
    message = "Hello"

test()

print(message)
```

Because `message` only exists inside the function.

---

## 20. Global Variables

A variable created outside a function can usually be accessed inside it.

```python
name = "Alan"

def greet():
    print(name)

greet()
```

Output:

```text
Alan
```

In general, avoid modifying global variables unnecessarily. Passing values through parameters and returning results is usually cleaner.

---

# Flexible Function Arguments

## 21. `*args`

`*args` lets a function receive any number of positional arguments.

```python
def show_numbers(*numbers):
    print(numbers)

show_numbers(10, 20, 30, 40)
```

Output:

```text
(10, 20, 30, 40)
```

Inside the function, `numbers` is a tuple.

Example:

```python
def add(*numbers):
    return sum(numbers)

print(add(10, 20))
print(add(10, 20, 30, 40))
```

Output:

```text
30
100
```

---

## 22. `**kwargs`

`**kwargs` lets a function receive any number of keyword arguments.

```python
def show_info(**info):
    print(info)

show_info(
    name="Alan",
    age=25,
    city="Sunnyvale"
)
```

Inside the function, `info` is a dictionary.

It looks like:

```python
{
    "name": "Alan",
    "age": 25,
    "city": "Sunnyvale"
}
```

You can access values like this:

```python
def show_info(**info):
    print(info["name"])
    print(info["age"])

show_info(name="Alan", age=25)
```

---

# Functions Working Together

## 23. Calling One Function from Another

Functions can work together.

```python
def add(a, b):
    return a + b

def double(number):
    return number * 2

result = add(10, 5)
result = double(result)

print(result)
```

Output:

```text
30
```

This is one of the most important ideas in programming: breaking a large problem into smaller reusable functions.

---

# Type Hints

## 24. Basic Type Hints

Type hints describe the expected types of parameters and return values.

```python
def add(a: int, b: int) -> int:
    return a + b
```

Meaning:

```text
a: int    -> a should be an integer
b: int    -> b should be an integer
-> int    -> the function should return an integer
```

Another example:

```python
def greet(name: str) -> str:
    return "Hello " + name
```

Type hints make larger programs easier to understand and maintain.

They are hints rather than strict runtime enforcement by Python itself.

---

# Important Function Concepts to Learn Later

Once the fundamentals are comfortable, learn these topics:

```text
Functions
|
+-- Parameters and arguments
+-- return
+-- Default arguments
+-- Positional arguments
+-- Keyword arguments
+-- Local and global scope
+-- *args
+-- **kwargs
+-- Type hints
+-- Lambda functions
|
+-- Later:
    +-- Recursion
    +-- Higher-order functions
    +-- Closures
    +-- Decorators
    +-- Generators
    +-- Async functions
```

---

# Recommended Learning Order

A good progression is:

```text
def
 |
parameters
 |
arguments
 |
return
 |
default parameters
 |
positional arguments
 |
keyword arguments
 |
local and global scope
 |
*args
 |
**kwargs
 |
type hints
 |
lambda
 |
decorators and generators
```

The most important topics to master first are:

1. Defining functions with `def`
2. Parameters and arguments
3. Returning values with `return`
4. Local variable scope
5. Calling functions from other functions

---

# Practice Exercises

## Exercise 1

Create a function that adds two numbers.

```python
def add(a, b):
    # your code
```

Expected:

```python
print(add(5, 10))
```

Output:

```text
15
```

---

## Exercise 2

Create a function that determines whether a number is even.

Example:

```python
is_even(10)
```

Should return:

```python
True
```

And:

```python
is_even(7)
```

Should return:

```python
False
```

---

## Exercise 3

Create a function that accepts a name and age.

```python
person_info("Alan", 25)
```

Expected output:

```text
Alan is 25 years old.
```

---

## Exercise 4

Create a function that accepts any number of numbers and returns their total.

Hint:

```python
def total(*numbers):
    ...
```

Example:

```python
print(total(10, 20, 30))
```

Expected:

```text
60
```

---

## Exercise 5

Create a function using keyword arguments:

```python
def profile(**info):
    ...
```

Call it like:

```python
profile(
    name="Alan",
    language="Python",
    level="Beginner"
)
```

---

# Final Takeaway

A Python function is essentially:

```python
def function_name(parameters):
    # do something
    return result
```

The central idea is:

```text
input -> processing -> output
```

For example:

```python
def calculate_price(price, quantity):
    total = price * quantity
    return total
```

Then:

```python
amount = calculate_price(10, 5)

print(amount)
```

Output:

```text
50
```

