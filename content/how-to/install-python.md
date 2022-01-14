---
description: Getting Started with Python
---

# Install Pyhton

To get started working with Python 3, you’ll need to have access to the Python interpreter (the console, and related tools and libraries). We can accomplish this in several ways:

* Download the installer from the official [download](https://www.python.org/downloads/) page.
* Use a package manager like `yum`, `apt` on Linux systems
* Homebrew for MacOS users.
* Build Python from sources, a method used by super geeks.



### Install Python on Windows

To install Python on our windows workstation, a few simple steps should be followed:

* Navigate to the official [download](https://www.python.org/downloads/) page, using a web browser
* Select the installer that matches the OS (32b or 64b)
* Execute the installer (using the default options, should be enough in most of the cases)
* Test the installation by typing `python -v` in a terminal



### Install Python on Linux

There is a very good chance your Linux distribution has Python installed already, but it probably won’t be the latest version, and it may be Python 2 instead of Python3. To check the installed versions, just type:

```bash
$ python --version
$ python3 --version
```

###

### Install on CentOS

To install, you should first update your system with the yum package manager:

```bash
$ sudo yum install python36u
$ sudo yum install python36u-pip
```

####

#### Links

* [Python 3 Installation & Setup Guide](https://realpython.com/installing-python/) - article published on RealPython
* [How to install Python](https://realpython.com/installing-python/) - a complete guide for many OS: Fedora, MacOS, Ubuntu
