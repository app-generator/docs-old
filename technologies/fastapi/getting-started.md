---
description: A comprehensive introduction to FastAPI
---

# Getting Started

[FastAPI](https://fastapi.tiangolo.com/) is an open-source high-performance, easy to learn web framework, at the same time fast to code, and production-ready.

* [FastAPI](https://fastapi.tiangolo.com/) - official website
* [FastAPI](https://github.com/tiangolo/fastapi) - source code (published on Github)
* [Learn FastAPI by coding](https://github.com/app-generator/fastapi-learn-by-coding) - sample project&#x20;



As posted on the official website, FastAPI key features are listed below:

* **Very high performance** - thanks to [Starlette](https://www.starlette.io/) and [Pydantic](https://pydantic-docs.helpmanual.io/)
* **Fast-to-code** and intuitive&#x20;
* **Robust** - provides interactive documentation `out-of-the-box`
* **Standards-based** - fully compatible with `OpenAPI` and `JSON Schema`



### Simple FastAPI Project

FastAPI requires Python 3.6 (or above) to execute successfully. For most of the Unix environments, Python3 might be already installed. To check the version, open a terminal and type:

```bash
$ python3 --version
```

If the version is 3.6 or above we can move forward and create a virtual environment for our first project powered by FastAPI.&#x20;

> Create/activate a Virtual Environment (Unix systems)

```bash
$ virtualenv env
$ source env/bin/activate
```

> Create/activate a Virtual Environment for Windows Systems

```bash
$ # virtualenv env
$ # .\env\Scripts\activate
```

> Install FastAPI&#x20;

```bash
$ pip install fastapi
$ pip install uvicorn
```

> Create `main.py`

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
async def root():
    return {"message": "Hello FastAPI"}
```

Save the file and start the project using `uvicorn`

```bash
$ uvicorn main:app --reload
$ 
$ The project is LIVE - https://localhost:8000 
```

At this point we should be able to visit the API in the browser:

* API Root: `http://localhost:8000`
* OpenAPI Specs: `http://localhost:8000/docs`
* Redoc:  `http://localhost:8000/redoc`

![FastAPI - Simple API Project](../../.gitbook/assets/fastapi-hello-world.jpg)



### FastAPI Resources

* [The future of FastAPI and Pyndantic](https://tiangolo.medium.com/the-future-of-fastapi-and-pydantic-is-bright-2d1785a603a9)
* [You should start using FastAPI](https://towardsdatascience.com/you-should-start-using-fastapi-now-7efb280fec02)
* [Rise of Pydantic Stack](https://python.plainenglish.io/an-introduction-to-the-pydantic-stack-9e490d606c8d) &#x20;
