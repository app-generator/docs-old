---
description: Crawl Website in Python
---

# Crawl Website in Python

This page explains how to use Python and extract (title) information from a LIVE website. The code provided is fairly simple and to use it we need to be comfortable using a terminal and have basic programming knowledge. Resources and libraries used:

* A terminal window
* `Python3` installed and accessible via the terminal window
* `PIP`, the official Python package manager
* `requests` - a popular and simple HTTP library
* `Beautiful Soup` - a library used to parse HTML and extract information with ease
* 10minutes to understand and type the commands&#x20;



### Let's start writing code.

**Check Python is installed**

Python is installed by default in MacOS and Linux systems and should be downloaded and installed in all Windows versions. Once is properly installed, we can start the Python console by typing `python` in the terminal.

```bash
$ python
Python 3.8.4 (tags/v3.8.4:dfa645a, Jul 13 2020, 16:46:45) [MSC v.1924 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

**Install libraries**

* [Request](https://requests.readthedocs.io/en/master/) - simple HTTP library for Python, built for human beings.
* [Beautiful Soup](https://www.crummy.com/software/BeautifulSoup/bs4/doc/) - Python library for pulling data out of HTML and XML files.

```bash
$ pip install requests
$ pip install BeautifulSoup4
```

**Write code in Python Console**

The first step is to import the libraries used in our code:

```python
>>> import requests                        # import the library
>>> from bs4 import BeautifulSoup as bs    # import the library
```

Once the libraries are imported we can use all helpers exposed. The following code snippet defines a variable that holds the website address and download the page using `requests` library.

```python
>>> site = 'https://google.com'            # define the website we want to process
>>> page = requests.get( site )            # download the page
```

At this point, the `page` should be injected and used via `BeautifulSoup4`.

```python
>>> soup = bs(page.content, 'html.parser') # Parse the downloaded page with BeautifulSoup
>>> soup.title                             # Print the title   
<title>Google</title>
```

This simple tutorial should provoke curious minds to search other Python `hot topics` and try to code more useful things. We will provide a short-list with suggestions:

* List all images of a web page
* List the inner links (to other pages, the same domain)
* List the outer links (external websites)



#### Links & Resources

* [Python](https://www.python.org/) - the official website
* [Python Cheatsheet](https://www.pythoncheatsheet.org/) - this site should make you curious
* Join [AppSeed](https://appseed.us) - For support and `production-ready` starters&#x20;
