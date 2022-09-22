---
description: Getting Started with Python
---

# Getting Started with Python

This page explains how to get started with Python and execute simple code using this programming language - Resources:

* [Python](https://www.python.org/) - the official website
* [Applications for Python](https://www.python.org/about/apps/) - blog artcile&#x20;
* [What can I do with Python](https://www.freecodecamp.org/news/what-can-you-do-with-python-the-3-main-applications-518db9a68a78/) - blog article&#x20;

### **What is Python**

Python is an `interpreted` high-level and general-purpose programming language. Interpreted means that the instructions are executed one-by-one at runtime. This pattern is different from compiled languages like C++, where the code is initially compiled and later executed in the operating system.

**Reasons to use it**

_Portability_ - Python runs everywhere: Mac, Linux, Windows. In other words, if we code a program on Windows, we can get the same effects on Linux or Mac. This is quite a thing because all Python libraries are compatible across all supported operating systems.

_Productivity_ - Python programs are smaller and you can build the same thing writing less code. This aspect comes from the language syntax and also from the huge ecosystem that provides libraries for (almost) anything.

_Ecosystem_ - Python has a huge ecosystem with many libraries that covers large areas as: Web Development, Data Science or Visualization. To read more about this topic, please access a comprehensive article published by Freecodecamp: [What can I do with Python](https://www.freecodecamp.org/news/what-can-you-do-with-python-the-3-main-applications-518db9a68a78/)

**Getting Started**

The first thing we need to take care is the Python version. Python comes in two versions:

* [Python2](https://www.python.org/download/releases/2.7/) - the legacy version that reached the _end-of-life_ at 01.Jan.2020
* [Python3](https://www.python.org/download/releases/3.0/) - actively supported and the recommended version for all new Python projects

Curious minds can read more about Python2 EOL (end-of-life) here - [Sunsetting Python 2](https://www.python.org/doc/sunset-python-2/).

**Install Python**

Before installing Python, it might be a good idea to check if is not already installed. Python is shipped in MacOS and Linux-based systems (no default installation in Windows). The fastest way is to open a terminal and type "python --version". On my M$ Windows shows:

```bash
$ python --version
Python 3.8.4
```

Anything that leads to an error, probably requires an install. To do this, just go to the official website and follow the set-up suggested for your operating system: [Windows](https://www.python.org/downloads/windows/), [Linux](https://www.python.org/downloads/source/), [MacOS](https://www.python.org/downloads/mac-osx/).

**Execute code in Python**

Once we have the Python interpreter properly installed we can start playing with the code. The most simple way is to open a terminal, type "python" and start coding something simple.

```python
$ python
Python 3.8.4 on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> 2+2
4
```

We've used Python to add two numbers. Let's print a message to the console:

```python
$ python
Python 3.8.4 on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
>>> print('Hello from Python')
Hello from Python
>>> var1 = 'Hello'
>>> var2 = ' from Python'
>>>
>>> print ( var1 + var2 )
Hello from Python
```

The sample code print the string "Hello from Python" in two ways:

* using the plain string "Hello from Python"
* concatenate two variables: var1 and var2

In both cases, we are using the built-in method "print()" to print the texts to the terminal.

**Create a file in Python**

```python
$ python
Python 3.8.4 on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
>>> f = open('my_file.txt', 'w+')
>>> f.write('some text ...')
13
>>> f.close()
```

This code snippet will create a new file in the current working directory and add the new text and close the file.&#x20;
