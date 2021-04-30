---
description: Short introduction to Pipenv
---

# What is [Pipenv](https://pipenv-fork.readthedocs.io/en/latest/)
---

**Pipenv** is a dependency manager for Python projects similar with Npm/Yarn for Node that provides more features than his older brother `pip`.
Pipenv aims to help users manage environments, dependencies, and imported packages on the command line. 
While `pip` alone is often sufficient for personal use, Pipenv is recommended for collaborative projects as it’s a higher-level tool that simplifies dependency management for common use cases.

<br />

**How to use Pipenv**

```bash
$ pip install pipenv
```

<br />

Once `pipenv` is installed we can star using it in our projects. To install `Django` for instance, we must type:

```bash
$ pipenv install django
```

This command will create automatically a virtual environment and install django package.

<br />

**Start a shell**

```bash
$ pipenv shell
```

<br />

**Run a Python script**

```bash
$ pipenv run python hello.py
```

<br />

To use an exiting `requirements.txt` with `pipenv`:

```bash
pipenv install requirements.txt
```

This will create a Pipfile and install the specified requirements. Consider your project upgraded!

<br />

### Pipenv Resources

- [Pipenv](https://pipenv-fork.readthedocs.io/en/latest/) - Python Dev Workflow for Humans
- [Why Python devs should use Pipenv](https://opensource.com/article/18/2/why-python-devs-should-use-pipenv)
- [Pipenv](https://docs.pipenv.org/basics/) - Basic Usage
