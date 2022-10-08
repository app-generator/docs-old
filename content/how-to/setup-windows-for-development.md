---
description: Setup Windows for Developers
---

# Setup Windows for coding

Microsoft Windows, commonly referred to as Windows, is a group of several proprietary graphical operating system families, all of which are developed and marketed by Microsoft. Each family caters to a certain sector of the computing industry. Active Microsoft Windows families include Windows NT and Windows IoT; these may encompass subfamilies, e.g. Windows Server or Windows Embedded Compact (Windows CE). Defunct Microsoft Windows families include Windows 9x, Windows Mobile and Windows Phone.

###

### Install basic development tools

This guide is written for Windows 10 version but can be used as a starting point for older versions of Windows.



### [Visual Studio Code](https://code.visualstudio.com/)

Visual Studio Code is a lightweight but powerful source code editor that runs on your desktop and is available for Windows, MacOS and Linux. It comes with built-in support for JavaScript, TypeScript and Node.js and has a rich ecosystem of extensions for other languages (such as C++, C#, Java, Python, PHP, Go) and runtimes (such as .NET and Unity).&#x20;

* [Visual Studio Code](https://code.visualstudio.com/) - the official page
* [Visual Studio Code](https://code.visualstudio.com/docs) - documentation

###

### Install [Python](https://www.python.org)

It is highly unlikely that your Windows system shipped with Python already installed. Fortunately, installing does not involve much more than downloading the Python installer from the python.org website and running it. Let’s take a look at how to install Python3 on Windows:

* Access the [download page](https://www.python.org/downloads/windows/)
* Click on the installer that matches your operating system version 32b or 64b
* Run the installer and mark the option that includes Python executable to your PATH variable (image credit: RealPython )

![Install Python - The Visual Installer Screen.](https://files.realpython.com/media/win-install-dialog.40e3ded144b0.png)

If the installation goes well, test the Python execution from the terminal:

```bash
$ python --version
Python 3.7.2
```

###

### Install [Git](https://git-scm.com/downloads)

To install Git on Windows you will need to download the installer from the [Git](https://git-scm.com/downloads) website:

* Download the installer
* Execute the installer, using the default options
* Test the installation by typing `git` &#x20;

```bash
$ git
usage: git [--version] [--help] [-C <path>] [-c name=value]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]
```

For more information about Git please access:

* [How to Install Git on Linux, Mac or Windows](https://www.linode.com/docs/development/version-control/how-to-install-git-on-linux-mac-and-windows/)
* [Getting Started with Git](https://www.linode.com/docs/development/version-control/how-to-configure-git/)

###

### Install [Node.js](https://nodejs.org/en/)

Node.js is a run-time environment that includes everything you need to execute a program written in JavaScript. It’s used for running scripts on the server to render content before it is delivered to a web browser. NPM stands for Node Package Manager, which is an application and repository for developing and sharing JavaScript code.

**Download the installer**

In a web browser, navigate to [https://nodejs.org/en/download/](https://nodejs.org/en/download/). Click the Windows Installer button to download the latest default version. At the time this article was written, version 10.16.0-x64 was the latest version. The Node.js installer includes the NPM package manager.

![NodeJs - Donwload Page.](<../../.gitbook/assets/programming-kit-nodejs (1).jpg>)

Execute the installer, and choosing the default options should be enough to have a successfull installation:

```bash
$ node -v
$ npm -v
```

