## 1. What is Python?

A high-level, interpreted, dynamically-typed programming language.

## 2. What are Python’s key features?

Interpreted

Object-oriented

Dynamically typed

Extensive libraries

Easy syntax

3. What is PEP 8?

## A style guide for writing clean, readable Python code.

## 4. What is the difference between list and tuple?
List	Tuple
Mutable	Immutable
Slower	Faster
Uses []	Uses ()
## 5. What is a dictionary?

A key-value pair data structure:
{"name": "Hanumanth", "age": 26}

## 6. What is slicing?

Extracting a portion of list/string:

data = [1,2,3,4]
data[1:3]  # [2,3]

## 7. What is the difference between == and is?

== compares values

is compares memory address (identity)

## 8. What are Python data types?

int

float

bool

str

list

tuple

dict

set

## 9. Explain function vs lambda.

Functions:

def add(a,b): return a+b


Lambda:

lambda a,b: a+b

## 10. What is a decorator?

A function that modifies another function.

Example:

def login_required(func):
    def wrapper():
        print("Checking login")
        func()
    return wrapper

## 11. What are args and kwargs?

Used to pass variable arguments.

def test(*args, **kwargs):
    print(args, kwargs)

## 12. What is list comprehension?

Short form of creating lists.

squares = [x*x for x in range(10)]

## 13. What is a generator?

A function that yields values one by one — memory efficient.

def gen():
    yield 1
    yield 2

## 14. What is the difference between deep copy and shallow copy?

Shallow copy → Only top-level copy
Deep copy → Full clone of all nested objects

## 15. What is monkey patching?

Changing behavior of code at runtime.

## 16. What is GIL?

Global Interpreter Lock — only one thread executes Python bytecode at a time.

## 17. How to handle exceptions?
try:
    x = 10/0
except ZeroDivisionError:
    print("Error")

## 18. Difference between class and object?

Class → blueprint
Object → instance of class

## 19. Types of inheritance?

Single

Multiple

Multilevel

Hierarchical

Hybrid

## 20. What are class variables vs instance variables?

Class variables: shared

Instance variables: object-specific

## 21. What is method overloading?

Python does not support true overloading; can be mimicked using default arguments.

## 22. What is method overriding?

Child class redefining parent method.

## 23. What are magic methods?

Special methods like:

__init__

__str__

__len__

__add__

## 24. What is an abstract class?

Class containing abstract methods using abc module.

## 25. What is encapsulation?

Hiding implementation details.
_protected, __private


## 26. What is multithreading?

Run multiple threads concurrently.

But GIL prevents true parallel CPU execution.

## 27. Multiprocessing vs Multithreading?
Multithreading	Multiprocessing
Shared memory	Separate memory
Affected by GIL	No GIL
Good for I/O	Good for CPU tasks
## 28. What is asyncio?

Used for asynchronous, non-blocking code.

## 29. What is a context manager?

Used with with block.

with open("file.txt") as f:
    data = f.read()

## 30. How does Python memory management work?

Reference counting

Garbage collector

Private heap

## 31. Explain Python garbage collection.

Automatic removal of unused objects using reference counting and cyclic GC.

## 32. What is pickling?

Serializing objects.

pickle.dump(obj, file)


## 33. Reverse a string
s[::-1]

## 34. Find the largest number in a list
max(lst)

## 35. Remove duplicates
list(set(lst))

## 36. Fibonacci program
def fib(n):
    a,b = 0,1
    for i in range(n):
        a,b = b,a+b
    return a

## 37. Check palindrome
s == s[::-1]

## 38. Count occurrences of each element
from collections import Counter
Counter(lst)

## 39. Read file and count lines
len(open("file.txt").readlines())

## 40. Swap two numbers
a, b = b, a

## 41. How to read a large file efficiently?

Use generator:

for line in open("bigfile.txt"):
    print(line)

## 42. How to handle API calls?

Using requests library:

import requests
requests.get(url).json()

## 43. How to connect Python with SQL?

Using pymysql, psycopg2, sqlite3.

## 44. How do you improve Python performance?

Use NumPy

Use caching

Use generators

Use multiprocessing

## 45. How to write a REST API in Python?

Using FastAPI or Flask

## 46. What is venv?

Isolated environment for dependencies.

## 47. How to package Python code?

Using:

setup.py

requirements.txt

pyproject.toml


## 48. Pandas vs NumPy?
Pandas	NumPy
DataFrames	Arrays
Labelled	Indexed
Slow	Fast

## 49. Explain broadcasting.

Automatic expansion of arrays in NumPy operations.

## 50. What is vectorization?

Replacing loops with NumPy operations for speed.