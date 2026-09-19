
# Python Data Structures

Python provides several built-in data structures for storing and organizing data.

The four fundamental data structures are:

1. List
2. Tuple
3. Set
4. Dictionary

Each one is useful for a different purpose.

---

# 1. Quick Comparison

| Data Structure | Syntax         | Ordered | Mutable | Allows Duplicates   |
| -------------- | -------------- | ------- | ------- | ------------------- |
| List           | `[]`           | Yes     | Yes     | Yes                 |
| Tuple          | `()`           | Yes     | No      | Yes                 |
| Set            | `{}`           | No      | Yes     | No                  |
| Dictionary     | `{key: value}` | Yes     | Yes     | Keys must be unique |

### Important Terms

**Ordered** means the elements maintain a predictable position.

**Mutable** means the data structure can be changed after it is created.

**Duplicate** means the same value can appear more than once.

---

# 2. List

A **list** stores multiple values in a single variable.

Lists use square brackets:

```python
fruits = ["apple", "banana", "orange"]
```

Think of it as:

```text
Index:      0         1          2
         "apple"  "banana"   "orange"
```

Python indexing starts at `0`.

---

## Accessing List Elements

```python
fruits = ["apple", "banana", "orange"]

print(fruits[0])
print(fruits[1])
```

Output:

```text
apple
banana
```

---

## Negative Indexing

Negative indexes count from the end.

```python
fruits = ["apple", "banana", "orange"]

print(fruits[-1])
```

Output:

```text
orange
```

Indexes can be visualized as:

```text
             apple      banana      orange

Positive:      0           1           2
Negative:     -3          -2          -1
```

---

## Changing a List Element

Lists are mutable.

```python
fruits = ["apple", "banana", "orange"]

fruits[1] = "mango"

print(fruits)
```

Output:

```text
['apple', 'mango', 'orange']
```

---

## Adding Elements

### `append()`

Adds an item to the end.

```python
fruits = ["apple", "banana"]

fruits.append("orange")

print(fruits)
```

Output:

```text
['apple', 'banana', 'orange']
```

### `insert()`

Adds an item at a specific position.

```python
fruits = ["apple", "orange"]

fruits.insert(1, "banana")

print(fruits)
```

Output:

```text
['apple', 'banana', 'orange']
```

---

## Removing Elements

### `remove()`

Removes an item by value.

```python
fruits = ["apple", "banana", "orange"]

fruits.remove("banana")

print(fruits)
```

### `pop()`

Removes an item by index.

```python
fruits = ["apple", "banana", "orange"]

removed = fruits.pop(1)

print(removed)
print(fruits)
```

Output:

```text
banana
['apple', 'orange']
```

Using `pop()` without an index removes the last element:

```python
fruits.pop()
```

---

## List Length

Use `len()`:

```python
fruits = ["apple", "banana", "orange"]

print(len(fruits))
```

Output:

```text
3
```

---

## Checking Whether an Item Exists

Use `in`:

```python
fruits = ["apple", "banana", "orange"]

if "banana" in fruits:
    print("Banana found!")
```

Output:

```text
Banana found!
```

---

## Looping Through a List

```python
fruits = ["apple", "banana", "orange"]

for fruit in fruits:
    print(fruit)
```

Output:

```text
apple
banana
orange
```

---

## List Slicing

Slicing extracts part of a list.

```python
numbers = [10, 20, 30, 40, 50]

print(numbers[1:4])
```

Output:

```text
[20, 30, 40]
```

Syntax:

```text
list[start:stop]
```

The `start` index is included.

The `stop` index is not included.

---

## Common List Methods

```python
items.append(value)
items.insert(index, value)
items.remove(value)
items.pop()
items.sort()
items.reverse()
items.clear()
```

Useful built-in functions and operators:

```python
len(items)
value in items
```

---

# 3. Tuple

A **tuple** is similar to a list, but it cannot normally be changed after creation.

Tuples use parentheses:

```python
coordinates = (10, 20)
```

---

## Accessing Tuple Elements

Tuples use indexes just like lists.

```python
coordinates = (10, 20)

print(coordinates[0])
```

Output:

```text
10
```

---

## Tuples Are Immutable

This works with a list:

```python
numbers = [10, 20]

numbers[0] = 50
```

But this does not work with a tuple:

```python
coordinates = (10, 20)

coordinates[0] = 50
```

Python will produce an error because tuples are **immutable**.

---

## When Should You Use a Tuple?

Use a tuple when the values should remain fixed.

Examples include:

```python
coordinates = (37.5, -122.0)

rgb_color = (255, 128, 0)

dimensions = (1920, 1080)
```

The idea is:

```text
List  → data may change

Tuple → data should remain fixed
```

---

## Tuple Unpacking

Python allows tuple values to be assigned to separate variables.

```python
coordinates = (10, 20)

x, y = coordinates

print(x)
print(y)
```

Output:

```text
10
20
```

This is called **unpacking**.

---

# 4. Set

A **set** stores unique values.

Example:

```python
skills = {"Python", "SQL", "Git"}
```

Sets use curly braces.

---

## Sets Do Not Keep Duplicate Values

```python
skills = {"Python", "SQL", "Python", "Git"}

print(skills)
```

The set contains only one `"Python"`.

Conceptually:

```text
Input:

Python
SQL
Python
Git

Set:

Python
SQL
Git
```

This makes sets useful for removing duplicates.

---

## Creating a Set

```python
languages = {"Python", "Java", "C++"}
```

Be careful with an empty set.

This:

```python
data = {}
```

creates an empty **dictionary**, not an empty set.

To create an empty set:

```python
data = set()
```

---

## Adding an Element

Use `add()`:

```python
skills = {"Python", "SQL"}

skills.add("Git")

print(skills)
```

---

## Removing an Element

```python
skills = {"Python", "SQL", "Git"}

skills.remove("SQL")
```

---

## Checking Membership

```python
skills = {"Python", "SQL", "Git"}

if "Python" in skills:
    print("Python found!")
```

---

## Set Operations

Sets are especially useful when comparing collections.

Example:

```python
backend = {"Python", "SQL", "Git"}
data = {"Python", "SQL", "Pandas"}
```

### Intersection

Values that exist in both sets:

```python
print(backend & data)
```

Conceptually:

```text
Python
SQL
```

### Union

All unique values from both:

```python
print(backend | data)
```

Conceptually:

```text
Python
SQL
Git
Pandas
```

### Difference

Values in one set but not the other:

```python
print(backend - data)
```

Conceptually:

```text
Git
```

---

## When Should You Use a Set?

Sets are useful when:

* You only want unique values.
* You want to remove duplicates.
* You want fast membership checks.
* You want to compare groups of values.

---

# 5. Dictionary

A **dictionary** stores information as **key-value pairs**.

Example:

```python
user = {
    "name": "Alan",
    "age": 25,
    "language": "Python"
}
```

Think of it as:

```text
Key          Value

name    →    Alan
age     →    25
language →   Python
```

Unlike a list, you normally access values using a **key** rather than a numerical index.

---

## Accessing Dictionary Values

```python
user = {
    "name": "Alan",
    "age": 25
}

print(user["name"])
```

Output:

```text
Alan
```

---

## Changing a Value

Dictionaries are mutable.

```python
user = {
    "name": "Alan",
    "age": 25
}

user["age"] = 26

print(user)
```

---

## Adding a New Key-Value Pair

```python
user = {
    "name": "Alan"
}

user["language"] = "Python"

print(user)
```

Conceptually:

```text
Before:

name → Alan

After:

name     → Alan
language → Python
```

---

## Removing an Item

```python
user = {
    "name": "Alan",
    "age": 25
}

user.pop("age")
```

---

## Using `get()`

You can access dictionary values using:

```python
user.get("name")
```

Example:

```python
user = {
    "name": "Alan"
}

print(user.get("name"))
```

Output:

```text
Alan
```

`get()` is useful because it can avoid an error when a key does not exist.

```python
print(user.get("city"))
```

Output:

```text
None
```

You can also provide a default value:

```python
print(user.get("city", "Unknown"))
```

Output:

```text
Unknown
```

---

# 6. Looping Through a Dictionary

## Loop Through Keys

```python
user = {
    "name": "Alan",
    "age": 25
}

for key in user:
    print(key)
```

Output:

```text
name
age
```

---

## Loop Through Values

```python
for value in user.values():
    print(value)
```

---

## Loop Through Keys and Values

```python
for key, value in user.items():
    print(key, value)
```

Output:

```text
name Alan
age 25
```

---

# 7. Why Dictionaries Are Important for APIs

Dictionaries are extremely important when working with APIs.

An API may return JSON like:

```json
{
    "name": "John",
    "age": 30,
    "city": "New York"
}
```

Python can convert that JSON into a dictionary:

```python
data = {
    "name": "John",
    "age": 30,
    "city": "New York"
}
```

Then you can access:

```python
print(data["name"])
```

Output:

```text
John
```

This is why understanding dictionaries is especially important before learning APIs deeply.

---

# 8. Nested Data Structures

Python data structures can contain other data structures.

For example, a list can contain dictionaries:

```python
users = [
    {
        "name": "John",
        "age": 30
    },
    {
        "name": "Sarah",
        "age": 25
    }
]
```

To access the first user's name:

```python
print(users[0]["name"])
```

Output:

```text
John
```

Think of it as:

```text
users
  │
  ├── index 0
  │      ├── name → John
  │      └── age  → 30
  │
  └── index 1
         ├── name → Sarah
         └── age  → 25
```

This structure is extremely common in API responses.

---

# 9. List vs Tuple vs Set vs Dictionary

## Use a List When

You need an ordered collection that can change.

```python
shopping_cart = ["milk", "bread", "eggs"]
```

---

## Use a Tuple When

You need an ordered collection that should remain fixed.

```python
screen_size = (1920, 1080)
```

---

## Use a Set When

You need unique values.

```python
skills = {"Python", "SQL", "Git"}
```

---

## Use a Dictionary When

You need to describe something using key-value pairs.

```python
student = {
    "name": "John",
    "grade": 95
}
```

---

# 10. Easy Way to Remember Them

```text
LIST
[]
Ordered collection
Can change
Duplicates allowed

Example:
["Python", "SQL", "Git"]


TUPLE
()
Ordered collection
Cannot normally change
Duplicates allowed

Example:
(10, 20)


SET
{}
Unique collection
Can change
No duplicates

Example:
{"Python", "SQL", "Git"}


DICTIONARY
{key: value}
Key-value collection
Can change
Keys are unique

Example:
{"name": "Alan", "age": 25}
```

---

# 11. Real-World Examples

### List

A shopping cart:

```python
cart = ["laptop", "mouse", "keyboard"]
```

### Tuple

Coordinates:

```python
location = (37.5, -122.0)
```

### Set

Unique programming skills:

```python
skills = {"Python", "SQL", "Git"}
```

### Dictionary

Information about a person:

```python
person = {
    "name": "John",
    "age": 30,
    "city": "Chicago"
}
```

---

# 12. Combining Data Structures

Real Python applications often combine structures.

For example:

```python
students = [
    {
        "name": "John",
        "skills": ["Python", "SQL"]
    },
    {
        "name": "Sarah",
        "skills": ["Java", "Git"]
    }
]
```

Here we have:

```text
List
 ↓
Dictionaries
 ↓
Lists
```

To access `"Python"`:

```python
print(students[0]["skills"][0])
```

Output:

```text
Python
```

Breaking it down:

```text
students[0]
```

gets the first student.

```text
students[0]["skills"]
```

gets that student's skills list.

```text
students[0]["skills"][0]
```

gets the first skill.

---

# 13. Mutable vs Immutable

One of the most important concepts in Python data structures is mutability.

## Mutable

Can be changed after creation:

```text
List
Set
Dictionary
```

Example:

```python
numbers = [1, 2, 3]

numbers.append(4)
```

The original list changed.

---

## Immutable

Cannot normally be changed after creation:

```text
Tuple
```

Example:

```python
coordinates = (10, 20)
```

You cannot do:

```python
coordinates[0] = 50
```

---

# 14. Index vs Key

Lists and tuples normally use **indexes**:

```python
languages = ["Python", "Java"]

print(languages[0])
```

Dictionaries use **keys**:

```python
language = {
    "name": "Python"
}

print(language["name"])
```

Remember:

```text
List / Tuple
       ↓
     Index
       ↓
       [0]


Dictionary
       ↓
      Key
       ↓
    ["name"]
```

---

# 15. Summary

The four major Python data structures are:

```text
                   Python Data Structures
                           │
          ┌────────────────┼─────────────────┐
          │                │                 │
        List             Tuple              Set
         []                ()                {}
          │                │                 │
       Ordered          Ordered           Unique
       Mutable         Immutable          Mutable
          │
          │
      Dictionary
       {key: value}
          │
       Key-value
        Mutable
```

The most important structures for beginners to understand deeply are:

```text
1. List
2. Dictionary
3. Tuple
4. Set
```

Lists and dictionaries are especially important because they appear constantly in real Python applications and API responses.

---

# 16. Quick Reference

```python
# List
languages = ["Python", "Java", "C++"]

# Tuple
coordinates = (10, 20)

# Set
skills = {"Python", "SQL", "Git"}

# Dictionary
user = {
    "name": "Alan",
    "language": "Python"
}
```

Remember:

```text
[]          → List

()          → Tuple

{1, 2, 3}   → Set

{"a": 1}    → Dictionary
```

---

# Recommended Learning Order

Study these individually rather than trying to memorize everything at once:

```text
1. Lists
   ↓
2. Dictionaries
   ↓
3. Tuples
   ↓
4. Sets
   ↓
5. Nested data structures
   ↓
6. List comprehensions
   ↓
7. Working with JSON/API data
```

The goal is not to memorize every method.

The goal is to understand:

* How data is stored
* How data is accessed
* How data is changed
* How to loop through data
* Which data structure fits a particular problem
