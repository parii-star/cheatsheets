# Python Cheat Sheet

> **Goal:** Learn Python syntax and core concepts clearly enough to write simple scripts and programs, even as a beginner.

Python is a high-level, interpreted programming language used for web development, data analysis, automation, scripting, and machine learning.

## How To Read This Sheet

| Pattern | Meaning |
|---|---|
| `[variable]` | replace with a real variable name, such as `name` |
| `[value]` | replace with an actual value, such as `"Hello"` or `42` |
| `[condition]` | replace with a boolean expression, such as `x > 0` |
| `[list]` | replace with a list, such as `[1, 2, 3]` |
| `[dict]` | replace with a dictionary, such as `{"a": 1}` |

Example:

```python
print([value])
```

If the value is a string, run:

```python
print("Hello")
```

## Table Of Contents

| Section | What You Learn |
|---|---|
| [Basic Syntax](#basic-syntax) | comments, variables, and printing |
| [Data Types](#data-types) | integers, strings, lists, dictionaries |
| [String Operations](#string-operations) | manipulate and format text |
| [Lists](#lists) | work with ordered collections |
| [Dictionaries](#dictionaries) | work with key-value pairs |
| [Control Flow](#control-flow) | conditional statements |
| [Loops](#loops) | repeat code with for and while |
| [Functions](#functions) | create reusable code blocks |
| [File I/O](#file-io) | read and write files |
| [Exception Handling](#exception-handling) | handle errors gracefully |
| [Imports](#imports) | use modules and libraries |
| [Built-in Functions](#built-in-functions) | use Python's built-in functions |
| [Object-Oriented Programming](#object-oriented-programming) | work with classes and objects |
| [Common Libraries](#common-libraries) | use popular Python modules |
| [Tips And Tricks](#tips-and-tricks) | useful Python patterns |

## Basic Syntax

Getting started with Python.

**Syntax:**

```python
command [value]
```

| Command | Clear Description |
|---|---|
| `# This is a comment` | single-line comment in code |
| `""" Multi-line comment """` | string used as multi-line comment |
| `print("Hello")` | output text to console |
| `name = "Ada"` | create and assign a variable |
| `a, b = 1, 2` | assign multiple variables at once |
| `"Hello" + " World"` | join strings together using plus sign |

## Data Types

Common Python data types.

**Syntax:**

```python
variable_name = [value]
```

| Command | Clear Description |
|---|---|
| `x = 42` | integer: whole numbers without decimals |
| `x = 3.14` | float: numbers with decimal points |
| `x = "hello"` | string: text enclosed in quotes |
| `x = True` | boolean: True or False value |
| `x = [1, 2, 3]` | list: ordered collection that can be changed |
| `x = (1, 2, 3)` | tuple: ordered collection that cannot be changed |
| `x = {"a": 1, "b": 2}` | dictionary: key-value pairs |
| `x = {1, 2, 3}` | set: unordered collection of unique items |

## String Operations

Manipulating and formatting text.

**Syntax:**

```python
string_variable.method([parameter])
```

| Command | Clear Description |
|---|---|
| `len("hello")` | get the number of characters in a string |
| `"hello"[0]` | access a single character at position 0 |
| `"hello"[1:4]` | get a substring from position 1 to 3 |
| `"hello".upper()` | convert all letters to uppercase |
| `"hello".lower()` | convert all letters to lowercase |
| `"hello".replace("l", "L")` | replace characters in a string |
| `"a,b,c".split(",")` | break a string into a list by separator |
| `",".join(["a", "b"])` | combine list items into a single string |
| `" hello ".strip()` | remove whitespace from start and end |
| `f"Hello {name}"` | insert variables into string using f-string |

## Lists

Working with ordered collections.

**Syntax:**

```python
list_variable.method([parameter])
```

| Command | Clear Description |
|---|---|
| `lst = [1, 2, 3]` | create a list with elements |
| `lst[0]` | access the first element |
| `lst[1:3]` | get elements from index 1 to 2 |
| `lst.append(4)` | add a single element to the end |
| `lst.insert(0, 0)` | insert an element at a specific position |
| `lst.remove(2)` | remove the first occurrence of a value |
| `lst.pop()` | remove and return the last element |
| `len(lst)` | get the number of elements in list |
| `lst.sort()` | arrange elements in ascending order |
| `lst.reverse()` | reverse the order of elements |

## Dictionaries

Working with key-value pairs.

**Syntax:**

```python
dictionary_variable[key] = value
```

| Command | Clear Description |
|---|---|
| `d = {"a": 1, "b": 2}` | create a dictionary with key-value pairs |
| `d["a"]` | get value using its key |
| `d["c"] = 3` | add or update a key-value pair |
| `del d["a"]` | remove a key-value pair completely |
| `d.keys()` | get all keys in the dictionary |
| `d.values()` | get all values in the dictionary |
| `d.items()` | get all key-value pairs as tuples |
| `"a" in d` | check if a key exists in dictionary |
| `d.get("x", 0)` | get value or return default if key missing |

## Control Flow

Conditional statements for branching logic.

**Syntax:**

```python
if [condition]:
    # code to run if true
```

| Command | Clear Description |
|---|---|
| `if x > 0: print("positive")` | run code block only if condition is true |
| `if x > 0: ... else: ...` | run one block if true, another if false |
| `if x > 0: ... elif x < 0: ... else: ...` | check multiple conditions in order |
| `x == 5`, `x != 5`, `x > 5`, `x <= 5` | common comparison operators |
| `x > 0 and y > 0` | combine conditions using logical operators |
| `"yes" if x > 0 else "no"` | conditional expression in one line |

## Loops

Repeating code.

**Syntax:**

```python
for item in [list]:
    # code to repeat
```

| Command | Clear Description |
|---|---|
| `for i in range(5): print(i)` | iterate from 0 to 4 using range |
| `for item in lst: print(item)` | iterate through each item in list |
| `while x > 0: x -= 1` | repeat code while condition is true |
| `break` | exit loop immediately |
| `continue` | skip current iteration and go to next |
| `for i, item in enumerate(lst)` | iterate with both index and value |
| `range(5)`, `range(1, 5)`, `range(0, 10, 2)` | generate numeric sequences |

## Functions

Defining and using reusable code blocks.

**Syntax:**

```python
def function_name([parameter]):
    return [value]
```

| Command | Clear Description |
|---|---|
| `def greet(name): return f"Hello {name}"` | define a function that returns a value |
| `greet("Ada")` | call a function with arguments |
| `def greet(name="Friend"): ...` | set a default value for a parameter |
| `def get_pair(): return 1, 2` | return multiple values as a tuple |
| `def func(*args): ...` | accept any number of positional arguments |
| `def func(**kwargs): ...` | accept any number of keyword arguments |
| `lambda x: x * 2` | create an anonymous function in one line |
| `def func(): """Doc text"""` | add documentation string to function |

## File I/O

Reading and writing files.

**Syntax:**

```python
f = open([filename], [mode])
```

| Command | Clear Description |
|---|---|
| `f = open("file.txt", "r")` | open file for reading |
| `f = open("file.txt", "w")` | open file for writing (overwrites) |
| `f = open("file.txt", "a")` | open file for appending (adds to end) |
| `f.read()` | read entire file as a single string |
| `f.readlines()` | read file as list of lines |
| `f.write("text")` | write text to file |
| `f.close()` | close file and free resources |
| `with open("file.txt") as f: ...` | automatically close file after use |

## Exception Handling

Dealing with errors gracefully.

**Syntax:**

```python
try:
    # code that might fail
except [ErrorType]:
    # code to run if error occurs
```

| Command | Clear Description |
|---|---|
| `try: ... except ValueError: ...` | catch specific type of error |
| `try: ... except (ValueError, TypeError): ...` | catch multiple error types |
| `try: ... except: ... else: ...` | run else block only if no error occurred |
| `try: ... finally: ...` | always execute finally block |
| `raise ValueError("message")` | manually throw an error |

## Imports

Using modules and libraries.

**Syntax:**

```python
import [module]
```

| Command | Clear Description |
|---|---|
| `import os` | import entire module |
| `from os import path` | import specific function from module |
| `import numpy as np` | import module with a shorter alias |
| `from module import *` | import everything (not recommended) |

## Built-in Functions

Common Python functions ready to use.

**Syntax:**

```python
function_name([argument])
```

| Command | Clear Description |
|---|---|
| `type(x)` | get data type of a variable |
| `len(lst)` | get length of any collection |
| `range(5)` | create sequence of numbers |
| `sum([1, 2, 3])` | add all elements together |
| `min(lst)`, `max(lst)` | find smallest or largest value |
| `sorted(lst)` | return a new sorted copy |
| `list(reversed(lst))` | return a new reversed copy |
| `map(lambda x: x*2, lst)` | apply function to each item |
| `filter(lambda x: x > 0, lst)` | keep only items matching condition |
| `enumerate(lst)` | get index and value pairs |
| `zip(lst1, lst2)` | combine multiple lists together |
| `all(lst)`, `any(lst)` | check if all or any items are true |

## Object-Oriented Programming

Basics of classes and objects.

**Syntax:**

```python
class ClassName:
    def method(self):
        pass
```

| Command | Clear Description |
|---|---|
| `class Dog: ...` | define a new class |
| `def __init__(self, name): ...` | constructor that initializes an object |
| `def bark(self): ...` | define a method inside a class |
| `dog = Dog("Rex")` | create a new object from a class |
| `dog.name` | access object property or attribute |
| `self.name = name` | set value on current object |
| `class Puppy(Dog): ...` | inherit from a parent class |

## Common Libraries

Frequently used Python modules.

**Syntax:**

```python
import [library]
[library].[function]()
```

| Command | Clear Description |
|---|---|
| `os.path.exists("file.txt")` | check if file exists using os module |
| `sys.exit()`, `sys.argv` | system functions and command-line arguments |
| `json.loads(text)`, `json.dumps(obj)` | convert between JSON and Python |
| `re.search(r"\d+", text)` | find patterns in text with regex |
| `math.sqrt(16)` | mathematical functions like square root |
| `datetime.now()` | get current date and time |
| `random.randint(1, 10)` | generate random numbers |
| `requests.get(url)` | make HTTP requests |
| `subprocess.run(["ls"])` | run external commands from Python |

## Tips And Tricks

Useful Python patterns and shortcuts.

**Syntax:**

```python
pattern_example
```

| Command | Clear Description |
|---|---|
| `[x*2 for x in range(5)]` | create list concisely using comprehension |
| `{x: x*2 for x in range(5)}` | create dictionary concisely |
| `a, b, c = [1, 2, 3]` | assign multiple variables from list |
| `a, b = b, a` | swap variables without temp variable |
| `if lst:` | empty list is False, non-empty is True |
| `x = x or 0` | use 0 if x is falsy |
| `if "a" in lst:` | check if item is in collection |
| `"hello".upper().replace("L", "!")` | chain method calls together |# Python Cheat Sheet

> **Goal:** Quick reference for Python basics, common commands, and practical DevOps use.

## Python At A Glance

| Topic | Quick Answer |
|---|---|
| What is Python? | A simple, readable programming language |
| Main use | Automation, scripts, data, web apps, DevOps |
| Why use it? | Easy syntax, large ecosystem, fast to write |
| Main strength | Flexibility |

## Core Ideas

| Term | Meaning |
|---|---|
| Interpreted language | Code is run by the Python interpreter |
| `import` | Bring in a module |
| `def` | Define a function |
| `if __name__ == "__main__":` | Run code only when file is executed directly |
| `None` | Empty or no value |
| `try/except` | Handle errors |

## Common Commands

| Command | What It Does |
|---|---|
| `python3 --version` | Show installed Python version |
| `python3 [file]` | Run a Python script |
| `python3 -c "code"` | Run a short command |
| `python3 -i [file]` | Run a script and stay interactive |
| `python3 -m pip install [package]` | Install a package |

## Caddy (Simple HTTPS Reverse Proxy)

Caddy is a small web server that automatically manages HTTPS (TLS) and makes it trivial to reverse-proxy Python web apps.

- Install (Debian/Ubuntu): `sudo apt install caddy` (or follow the official installer for your platform).
- Start and enable: `sudo systemctl enable --now caddy` and check `sudo systemctl status caddy`.

Simple Caddyfile to reverse-proxy a local app (save as `/etc/caddy/Caddyfile`):

```
example.com {
    reverse_proxy 127.0.0.1:8000
}
```

Quick notes for DevOps:

- Automatic HTTPS: Caddy obtains and renews TLS certs for you.
- Easy for staging and small production services; use it as a lightweight ingress or reverse proxy in front of Python app servers.
- Good for local testing: `caddy run --config /etc/caddy/Caddyfile`.
| `python3 -m pip uninstall [package]` | Remove a package |
| `python3 -m pip list` | Show installed packages |
| `python3 -m pip freeze` | Output installed packages |
| `python3 -m venv .venv` | Create a virtual environment |
| `python3 -m unittest` | Run unittest tests |
| `pytest` | Run pytest tests |
| `python3 -m pdb [file]` | Start debugger |

## Quick Flow

```text
Code -> Python interpreter -> Run
```

```bash
python3 --version
python3 app.py
python3 -m pip install requests
```

## Virtual Environment

```bash
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install requests
deactivate
```

## File Handling

```python
with open("notes.txt", "r") as file_handle:
    content = file_handle.read()
```

| Pattern | Meaning |
|---|---|
| `open(file, "r")` | Read a file |
| `open(file, "w")` | Write a file |
| `f.read()` | Read all content |
| `f.readline()` | Read one line |
| `f.readlines()` | Read all lines |

## Useful Snippets

```python
def greet(name):
    return f"Hello, {name}"


if __name__ == "__main__":
    print(greet("world"))
```

| Pattern | Meaning |
|---|---|
| `for item in items:` | Loop through items |
| `print(value)` | Show a value |
| `len(x)` | Get length |
| `dict[key]` | Read from a dictionary |
| `list.append(x)` | Add to a list |

## DevOps Use

Use Python for:

- Automation scripts
- API calls
- Log parsing
- Cloud tasks
- CI/CD helpers
- Small operational tools

## Good To Remember

| Concept | Quick Meaning |
|---|---|
| `pip` | Package installer |
| `venv` | Isolated environment |
| `unittest` | Built-in test module |
| `pytest` | Popular third-party test tool |
| `pdb` | Debugger |

## Short Summary

Python is best when you want code that is easy to write, easy to read, and useful for automation and DevOps. # Python Cheat Sheet
 
 > **Goal:** Learn the most common Python commands and workflows clearly enough to use them as a beginner.
 
-This cheat sheet is for Python 3 on Linux, macOS, and Windows with small command changes where needed.
+This cheat sheet is a beginner-friendly reference for Python 3 on Linux, macOS, and Windows with small command changes where needed.
+
+The commands and snippets are chosen for simple day-to-day use.
