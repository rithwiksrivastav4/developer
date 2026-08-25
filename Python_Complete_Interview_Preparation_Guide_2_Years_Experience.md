# Python Complete Interview Preparation Guide (2 Years Experience)

# 1. Python Introduction

Python is a high-level, interpreted, object-oriented programming
language used for:

-   Web development
-   Automation
-   Data processing
-   APIs
-   AI/ML
-   Scripting

## Python Features

-   Simple syntax
-   Dynamic typing
-   Large standard library
-   Object-oriented programming
-   Cross-platform support
-   Large community

------------------------------------------------------------------------

# 2. Python Installation and Environment

Check version:

``` bash
python --version
```

Create virtual environment:

``` bash
python -m venv venv
```

Activate:

Windows:

``` bash
venv\Scripts\activate
```

Linux/Mac:

``` bash
source venv/bin/activate
```

Install packages:

``` bash
pip install package_name
```

List packages:

``` bash
pip list
```

------------------------------------------------------------------------

# 3. Python Variables

Python does not require datatype declaration.

Example:

``` python
name = "John"
age = 25
salary = 50000
```

------------------------------------------------------------------------

# 4. Python Data Types

## Numbers

``` python
age = 25
price = 99.99
```

## String

``` python
name = "Python"
```

## Boolean

``` python
is_active = True
```

## List

``` python
numbers = [1,2,3]
```

## Tuple

``` python
values = (1,2,3)
```

## Set

``` python
items = {1,2,3}
```

## Dictionary

``` python
user = {
"name":"John",
"age":25
}
```

------------------------------------------------------------------------

# 5. Operators

Arithmetic:

``` python
+
-
*
/
%
```

Comparison:

``` python
==
!=
>
<
```

Logical:

``` python
and
or
not
```

------------------------------------------------------------------------

# 6. Conditional Statements

``` python
age = 18

if age >= 18:
    print("Adult")
else:
    print("Minor")
```

------------------------------------------------------------------------

# 7. Loops

## For Loop

``` python
for i in range(5):
    print(i)
```

## While Loop

``` python
count = 0

while count < 5:
    print(count)
    count += 1
```

------------------------------------------------------------------------

# 8. Functions

Basic function:

``` python
def add(a,b):
    return a+b

print(add(10,20))
```

Arguments:

``` python
def user(name, age):
    print(name, age)
```

------------------------------------------------------------------------

# 9. \*args and \*\*kwargs

## args

Multiple positional arguments:

``` python
def total(*numbers):
    return sum(numbers)
```

## kwargs

Multiple keyword arguments:

``` python
def user(**data):
    print(data)
```

------------------------------------------------------------------------

# 10. Lambda Functions

Anonymous functions.

Example:

``` python
square = lambda x:x*x

print(square(5))
```

------------------------------------------------------------------------

# 11. List Comprehension

Normal:

``` python
numbers=[]

for i in range(5):
    numbers.append(i)
```

Comprehension:

``` python
numbers=[i for i in range(5)]
```

------------------------------------------------------------------------

# 12. Exception Handling

Example:

``` python
try:
    result = 10/0

except Exception as e:
    print(e)

finally:
    print("Completed")
```

Keywords:

-   try
-   except
-   else
-   finally
-   raise

------------------------------------------------------------------------

# 13. File Handling

Write:

``` python
file=open("test.txt","w")

file.write("Hello")

file.close()
```

Read:

``` python
file=open("test.txt","r")

data=file.read()

print(data)
```

Better:

``` python
with open("test.txt") as file:
    data=file.read()
```

------------------------------------------------------------------------

# 14. Modules and Packages

Import module:

``` python
import math

print(math.sqrt(25))
```

Create module:

``` python
# calculator.py

def add(a,b):
    return a+b
```

------------------------------------------------------------------------

# 15. Object Oriented Programming

## Class

``` python
class Employee:

    company="ABC"
```

## Object

``` python
emp = Employee()
```

------------------------------------------------------------------------

# 16. Constructor

``` python
class Employee:

    def __init__(self,name):
        self.name=name


emp=Employee("John")
```

------------------------------------------------------------------------

# 17. Inheritance

``` python
class Animal:

    def sound(self):
        print("Sound")


class Dog(Animal):

    pass
```

------------------------------------------------------------------------

# 18. Encapsulation

Protecting data inside class.

``` python
class Account:

    def __init__(self):
        self.__balance=1000
```

------------------------------------------------------------------------

# 19. Polymorphism

Same method with different behavior.

``` python
class Dog:

    def sound(self):
        print("Bark")


class Cat:

    def sound(self):
        print("Meow")
```

------------------------------------------------------------------------

# 20. Decorators

Functions that modify another function.

Example:

``` python
def logger(func):

    def wrapper():
        print("Before")
        func()
        print("After")

    return wrapper
```

------------------------------------------------------------------------

# 21. Iterators

Iterator allows sequential access.

Example:

``` python
numbers=[1,2,3]

iterator=iter(numbers)

print(next(iterator))
```

------------------------------------------------------------------------

# 22. Generators

Generators produce values one by one.

Example:

``` python
def numbers():

    yield 1
    yield 2
    yield 3
```

Advantages:

-   Memory efficient
-   Lazy execution

------------------------------------------------------------------------

# 23. Context Manager

Used with with statement.

Example:

``` python
with open("file.txt") as f:
    data=f.read()
```

------------------------------------------------------------------------

# 24. Regular Expressions

Example:

``` python
import re

pattern=r"\d+"

result=re.findall(pattern,"Age 25")
```

------------------------------------------------------------------------

# 25. JSON Handling

Convert dictionary to JSON:

``` python
import json

data={"name":"John"}

json_data=json.dumps(data)
```

JSON to dictionary:

``` python
data=json.loads(json_data)
```

------------------------------------------------------------------------

# 26. Multithreading

Used for I/O operations.

Example:

``` python
import threading

def task():
    print("Running")

thread=threading.Thread(target=task)

thread.start()
```

------------------------------------------------------------------------

# 27. Multiprocessing

Used for CPU intensive tasks.

``` python
from multiprocessing import Process

def task():
    print("Process")

p=Process(target=task)

p.start()
```

------------------------------------------------------------------------

# 28. Async Programming

Example:

``` python
import asyncio

async def hello():

    print("Hello")


asyncio.run(hello())
```

------------------------------------------------------------------------

# 29. Database Connection

Using SQLite:

``` python
import sqlite3

connection=sqlite3.connect("database.db")
```

------------------------------------------------------------------------

# 30. Python Memory Management

Python uses:

-   Reference counting
-   Garbage collection
-   Private heap

Garbage collector:

``` python
import gc

gc.collect()
```

------------------------------------------------------------------------

# Python Interview Questions

## Q1. Difference between list and tuple?

List: - Mutable - More memory

Tuple: - Immutable - Faster

------------------------------------------------------------------------

## Q2. Difference between shallow copy and deep copy?

Shallow: - Copies references

Deep: - Creates independent copy

------------------------------------------------------------------------

## Q3. Difference between is and ==?

==: - Checks value

is: - Checks memory location

------------------------------------------------------------------------

## Q4. What are decorators?

Decorators modify the behavior of existing functions without changing
code.

------------------------------------------------------------------------

## Q5. Difference between iterator and generator?

Iterator: - Uses iter() and next()

Generator: - Uses yield - Memory efficient

------------------------------------------------------------------------

## Q6. How does Python manage memory?

Using:

-   Private heap
-   Reference counting
-   Garbage collector

------------------------------------------------------------------------

## Q7. Difference between threading and multiprocessing?

Threading: - I/O tasks

Multiprocessing: - CPU tasks

------------------------------------------------------------------------

## Q8. What is GIL?

Global Interpreter Lock allows only one thread to execute Python
bytecode at a time.

------------------------------------------------------------------------

## Q9. Difference between deep copy and shallow copy?

Shallow copy copies references.

Deep copy creates complete independent objects.

------------------------------------------------------------------------

## Q10. What are Python virtual environments?

They isolate project dependencies.

------------------------------------------------------------------------

# Python Scenario Based Questions

## Scenario 1: API is slow

Check:

-   Database calls
-   External API calls
-   Memory usage
-   Logging

Solutions:

-   Caching
-   Async calls
-   Query optimization

------------------------------------------------------------------------

## Scenario 2: Application memory increasing

Check:

-   Memory leaks
-   Large objects
-   Garbage collection

------------------------------------------------------------------------

## Scenario 3: Production error handling

Implement:

-   Logging
-   Exception handling
-   Monitoring
-   Alerts

------------------------------------------------------------------------

# Python Command Cheat Sheet

``` bash
python file.py

pip install package

pip freeze

python -m venv venv

pytest

python manage.py
```

------------------------------------------------------------------------

# 2 Years Experience Python Developer Checklist

Must know:

-   Python syntax
-   OOP
-   Functions
-   Decorators
-   Generators
-   Exception handling
-   File handling
-   Modules
-   Virtual environments
-   Threading
-   Multiprocessing
-   Async programming
-   Database handling
-   Debugging
-   Production scenarios
