
## 1. What is Python?
- Python is a high-level, interpreted programming language known for simplicity and readability.

## 2. Is Python compiled or interpreted?
- Python is interpreted, but it first compiles code into bytecode before execution.

## 3. What are Python’s key features?
- Easy to learn
- Interpreted
- Object-oriented
- Large standard library
- Dynamically typed
-
## 4. What is PEP 8?
- PEP 8 is the style guide for writing clean and readable Python code.

## 5. What are variables in Python?
- Variables are used to store data values and don’t require explicit data types.

## 6. What are Python data types?
- Common types: int, float, str, list, tuple, set, dict.

## 7. What is type casting?
- Converting one data type into another, e.g., int("10").

## 8. What is indentation in Python?
- Indentation defines code blocks and is mandatory in Python.

## 9. What is a comment in Python?
- Comments explain code and start with #.

## 10. What is None in Python?
- None represents the absence of a value.

## 11. What are conditional statements?
- if, elif, and else control decision-making.

## 12. What are loops in Python?
- for and while loops repeat code execution.

## 13. What is the difference between break and continue?
- break stops the loop
- continue skips the current iteration

## 14. What is a pass statement?
- pass is a placeholder that does nothing.

## 15. What is a range function?
- range() generates a sequence of numbers.

## 16. What is a function?

- A function is a reusable block of code that performs a task.

## 17. What is the difference between parameters and arguments?

- Parameters: variables in function definition
- Arguments: actual values passed

## 18. What is a lambda function?

- A small anonymous function written in one line.

## 19. What is recursion?
- A function calling itself.

## 20. What is *args and **kwargs?

- *args handles multiple positional arguments

- **kwargs handles keyword arguments

## 21. What is a list?

- A mutable, ordered collection of elements.

## 22. What is a tuple?

- An immutable, ordered collection.

## 23. What is a set?

- An unordered collection of unique elements.

## 24. What is a dictionary?

- A key-value pair data structure.

## 25. Difference between list and tuple?

- Lists are mutable; tuples are immutable.

## 26. What is OOP?

- Object-Oriented Programming organizes code using objects and classes.

## 27. What is a class?

- A blueprint for creating objects.

## 28. What is an object?

- An instance of a class.

## 29. What is inheritance? and types of inheritance

- One class acquiring properties of another.
## types of inheritance
- Single
- Multiple
- Multilevel
- Hierarchical
- Hybrid
## 30. What is polymorphism?

- Same function name with different behavior.


## 31. Explain Python garbage collection.

- Garbage collection in Python is automatic memory management that removes unused objects using reference counting and cyclic garbage collection.

## 32. What is an exception?

- An error that occurs during execution.

## 33. How do you handle exceptions?

- Using try, except, else, and finally.

## 34. What is finally?

- Block that always executes, even if an error occurs.

## 35. What is the difference between error and exception?

- Errors stop execution; exceptions can be handled.

## 36. What is a module?

- A Python file containing reusable code.

## 37. How do you import a module?

- Using import module_name.

## 38. What is a package?

- A collection of Python modules.

## 39. How do you read a file in Python?

- Using open() and read methods.

## 40. What is the use of with statement?

- Automatically closes files after use.

## 41. What is list comprehension?

- A concise way to create lists.

## 42. What is a generator?

- A function that returns values one at a time using yield.

## 43. What is slicing?

- Extracting parts of sequences using indexes.

## 44. What is __init__?

- A constructor method that initializes objects.

## 45. What is virtual environment?

- An isolated Python environment for dependencies.

## 46. What is pip?

- Python’s package installer.

## 47. What is multithreading?

- Running multiple threads concurrently.

## 48. What is GIL?

- Global Interpreter Lock ensures one thread executes Python bytecode at a time.

## 49. What is Python used for?

- Web development, automation, data science, AI, DevOps.

## 50. Why is Python popular?

- Because it is simple, powerful, and versatile.


## 51 How is Python used in DevOps?
## Answer
- Python is used for CI/CD automation, infrastructure management, monitoring, scripting, and cloud automation.

## 51 What Python libraries are commonly used in DevOps?
## Answer
- os, sys – system operations
- subprocess – run shell commands
- boto3 – AWS automation
- requests – API calls

## 52 How do you run a shell command in Python?
- Use the subprocess module to execute shell commands.

## 53. How do you read environment variables in Python?
- Using os.environ or os.getenv().

## 54. How do you automate server tasks using Python?
## Answer
- Use the os module for file operations, environment variables, and directory management.
- Use the subprocess module to run system commands like starting or stopping services.
- Use the shutil module for file copying, moving, and cleanup tasks.
- Use the schedule or cron (via subprocess) for task scheduling.
- Use the logging module to track script execution and errors.

## 55 . What is virtualenv and why is it used?
- It creates an isolated Python environment to avoid dependency conflicts.

## 56. How do you handle configuration files in Python?

- Using YAML, JSON, or INI files with libraries like yaml or json.

## 57 How do you make API calls in Python?
- Using the requests library.


## 42. How to handle API calls?

Using requests library:

import requests
requests.get(url).json()

## 58. What is idempotency and why is it important?
- Running a script multiple times should give the same result.

## 59. How do you log in Python?

- Using the built-in logging module.

## 60. How do you handle exceptions in automation scripts?

- Using try-except blocks to prevent pipeline failures.

## 61. How do you secure secrets in Python scripts?
- Using environment variables or secret managers.

## 62. How do you check script exit status in Python?
- Using return codes from subprocess.


## 63 What is a decorator?

A function that modifies another function.

Example:

def login_required(func):
    def wrapper():
        print("Checking login")
        func()
    return wrapper

## 64. What are magic methods?

Special methods like:
```
__init__

__str__

__len__

__add__
```
## 65. What is an abstract class?

Class containing abstract methods using abc module.

## 66. What is encapsulation?

Hiding implementation details.
_protected, __private


## 67. What is multithreading?

Run multiple threads concurrently.

But GIL prevents true parallel CPU execution.

## 68. What is asyncio?

Used for asynchronous, non-blocking code.

## 69. What is pickling?

Serializing objects.

pickle.dump(obj, file)

## 70. Fibonacci program
def fib(n):
    a,b = 0,1
    for i in range(n):
        a,b = b,a+b
    return a

## 71. How to handle API calls?

Using requests library:

import requests
requests.get(url).json()

## 72. How to connect Python with SQL?

Using pymysql, psycopg2, sqlite3.

## 73. How do you improve Python performance?

Use NumPy

Use caching

Use generators

Use multiprocessing

## 74. How to write a REST API in Python?

Using FastAPI or Flask

## 75. What is venv?

Isolated environment for dependencies.






