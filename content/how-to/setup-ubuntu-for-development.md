---
description: Setup Ubuntu for Developers
---

# Setup Ubuntu for coding

Ubuntu is a complete Linux operating system, freely available with both community and professional support. Ubuntu is suitable for both desktop and server use. The current Ubuntu release supports many architectures: Intel x86 (IBM-compatible PC), AMD64 (x86-64), ARMv7, ARMv8.

Ubuntu includes thousands of pieces of software, starting with the Linux kernel version 4.15 and GNOME 3.28, and covering every standard desktop application from word processing and spreadsheet applications to internet access applications, web server software, email software, programming languages and tools and of course several games. For more information please access the official website: [Ubuntu.com](https://ubuntu.com/)

###

### Install basic development tools

The `Build Essential` package group provides the GNU Compiler Collection (GCC), GNU Debugger (GDB), and other related development tools.

```bash
$ # install Development Tools bundle
$ sudo apt install build-essential
```

###

### Install [Git](https://git-scm.com/)

[Git](https://git-scm.com/) is the most popular version control system on Linux. It is easy to use, amazingly fast, it’s very efficient with large projects, and it has an incredible branching system for non-linear development.

```bash
$ sudo apt install install git
```

### Install Python3

Ubuntu comes with both Python 2.7 and Python 3.5 by default. You can install Python 3.6 along with them via a `third-party PPA` by doing the following steps:

```bash
$ sudo add-apt-repository ppa:jonathonf/python-3.6
```

> And Python3 libraries for development

```bash
$ sudo apt-get update
$ sudo apt-get install python3.6
```

### Installing [Node.js](https://nodejs.org/)

Node.js is an open-source, cross-platform, JavaScript runtime environment that executes JavaScript code outside of a browser.

```bash
$ sudo apt-get install install nodejs
$
$ # check the version
$ node --version
```

### Installing [Yarn](https://yarnpkg.com/)

The yarn is an advanced package management software for Node.js applications. It is a fast, secure, and reliable alternative that any other Nodejs package manager.

```bash
$ sudo npm install yarn -g
$
$ # check the version
$ yarn -v
```
