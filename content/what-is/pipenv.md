---
description: Short introduction to Pipenv
---

# What IS Pipenv

**Pipenv** is a dependency manager for Python projects similar to Npm/Yarn for Node that provides more features than his older brother `pip`. Pipenv aims to help users manage environments, dependencies, and imported packages on the command line. While PIP alone is often sufficient for personal use, Pipenv is recommended for collaborative projects as it’s a higher-level tool that simplifies dependency management for common use cases.

**How to use Pipenv**

```bash
$ pip install pipenv
```

Once `pipenv` is installed we can start using it in our projects. To install `Django` for instance, we must type:

```bash
$ pipenv install django
```

This command will create automatically a virtual environment and install Django package.

**Start a shell**

```bash
$ pipenv shell
```

**Run a Python script**

```bash
$ pipenv run python hello.py
```

To use an exiting `requirements.txt` with `pipenv`:

```bash
pipenv install requirements.txt
```

This will create a Pipfile and install the specified requirements. Consider your project upgraded!



#### Resources

* [Pipenv](https://pipenv-fork.readthedocs.io/en/latest/) - Python Dev Workflow for Humans
* [Why Python devs should use Pipenv](https://opensource.com/article/18/2/why-python-devs-should-use-pipenv)
* [Pipenv](https://docs.pipenv.org/basics/) - Basic Usage
