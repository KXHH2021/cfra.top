---
title: Asynchronous Requests in Python
date: 2023-10-4 14:22:57
categories:
  - Tips for using python
tags:
  - python
---

## Asynchronous requests in Python

Asynchronous requests are at the heart of our system. Let's think of it like this:

When a user loads our site (website or web application), the user immediately starts seeing content. But it's not quite ready yet. Therefore, we load the content asynchronously in the background as the user continues to interact with the page.

These requests do not prevent subsequent code from executing while waiting for a response. This means that other code can continue to run while the request is being processed.

This can be helpful when dealing with external resources that may take some time to respond to, such as API calls. It also makes your code more responsive because the UI can continue to update while the request is being processed.

### The Importance of Using Asynchronous Requests in Python

Asynchronous requests are a great way to improve the performance of your Python application. When a request is made, the Python interpreter can continue executing other code while processing the request.

It can significantly increase speed, especially for applications that make a lot of requests. However, here are some key points to remember when using asynchronous requests.

First, we must avoid making too many requests at the same time. If we make too many requests, the interpreter may get overwhelmed and slow down.
Second, we need to be prepared to handle errors. If the request fails, the interpreter will not be able to continue executing the code.
Overall, asynchronous requests are a great tool for improving the performance of Python applications. However, use it with care; they can help our applications run faster and smoother.

### The easiest way to write asynchronous requests in Python

Asynchronous requests can be easily issued using the asyncio module. In addition, python's asyncio library provides tools for writing asynchronous code. For example, we can use asyncio.sleep() to pause the concatenation and asyncio.wait() to wait for the concatenation to complete.

To write an asynchronous request, we need to first create a concatenation. We can do this using the asyncio.ensure_future() function. Once we have the coprogram, we can use the asyncio.sleep() function to pause it and the asyncio.wait() function to wait for it to complete.

### Handling Asynchronous Requests in Python

First of all, if we want to run asynchronous requests in Python, then you should install the aiohttp python library using the following command.

```python
pip install aiohttp

```

We can use asynchronous requests to improve the performance of Python applications. By issuing requests in parallel, we can speed up the process considerably.

There are a few different ways to handle asynchronous requests in Python. The most popular is the asyncio library. This library provides powerful tools for handling asynchronous requests.

Another popular choice is the grequests library. This library is a bit simpler to use than asyncio, but it can be just as effective.

Which option we choose will depend on our specific needs. But whichever we choose, we can see significant performance improvements with asynchronous requests.

```python
import grequests

urls = [
    'http://www.heroku.com',
    'http://tablib.org',
    'http://httpbin.org',
    'http://python-requests.org',
    'http://kennethreitz.com'
]

rs = (grequests.get(u) for u in urls)
grequests.map(rs)

```

### Python libraries for asynchronous requests

There are a number of Python libraries that we can use to make asynchronous requests. The most popular are aiohttp and asyncio.

#### The aiohttp Library for Asynchronous Requests

aiohttp is a library that enables us to make asynchronous HTTP requests. It is built on top of asyncio and provides a simple interface to make HTTP requests.

#### asyncio library for asynchronous requests

asyncio is a library that supports asynchronous programming in Python. It allows us to write asynchronous code and makes it easy to use the libraries that support asyncio.

Both aiohttp and asyncio are available on PyPI and can be installed using pip.

```python
import asyncio
import aiohttp
import json

from text_api_config import apikey

```

### Asynchronous vs. regular requests

There are two types of requests we can make to the server: asynchronous requests and regular requests. Asynchronous requests are made in the background while the user is still interacting with the page. Typical requests are made while the page is loading.

Asynchronous requests are often faster and more efficient than regular requests because they don't prevent the page from loading. However, their implementation can be more complex and not all browsers always support them.

Code Example:

```python
import requests
import time

start_time = time.time()

for number in range(1, 151):
    url = f'https://pokeapi.co/api/v2/pokemon/{number}'
    resp = requests.get(url)
    pokemon = resp.json()
    print(pokemon['name'])

print("--- %s seconds ---" % (time.time() - start_time))

```

Output：

```
bulbasaur
ivysaur
venusaur
....
dragonair
dragonite
mewtwo
--- 68.17992424964905 seconds

```

#### The asyncio Module for Python

asyncio is a module for concurrent programming in Python. It provides a framework for managing concurrent threads, tasks, and events. asyncio is used to write programs that can perform multiple tasks simultaneously.

asyncio is based on the concept of a concurrent program. A concurrent program is a function that can suspend execution and return control to the caller. It allows multiple concurrencies to run at the same time.

asyncio provides tools for managing concurrent processes, including event loops, task schedulers, and concurrent data structures.

asyncio is an efficient way to write concurrent programs. It is easy to use and can scale to large programs. asyncio is an excellent choice for programs that need to perform multiple tasks simultaneously.

Code Example:

```python
import asyncio
import aiohttp
import json
from text_api_config import apikey

async def gather_with_concurrency(n, *tasks):
    semaphore = asyncio.Semaphore(n)
    async def sem_task(task):
        async with semaphore:
            return await task
   
    return await asyncio.gather(*(sem_task(task) for task in tasks))

```

#### The aiohttp Module in Python

The aiohttp module is Python's asynchronous HTTP client/server. It is built on asyncio and provides a simple API for handling HTTP.

The aiohttp module makes it easy to use HTTP in Python. It provides a simple API that makes it easy to send and receive HTTP requests and responses.

The aiohttp module also provides a way to run an asynchronous HTTP server.

```python
import asyncio
import aiohttp
import json
from text_api_config import apikey

async def main():
    conn = aiohttp.TCPConnector(limit=None, ttl_dns_cache=300)
    session = aiohttp.ClientSession(connector=conn)
    urls = [summarize_url, ner_url, mcp_url]
    conc_req = 3

```

### Asynchronous Requests in Python

Code example:

```python
import queue
def task1(name, s_queue):
    if s_queue.empty():
        print(f'Task {name} has nothing to do')
    else:
        while not s_queue.empty():
            cnt = s_queue.get()
            total = 0
            for x in range(cnt):
                print(f'Task {name} is working now.')
                total += 1
            print(f'Task {name} is working with a total of: {total}')
def s_async():
    s_queue = queue.Queue()
    for work in [2, 5, 10, 15, 20]:
        s_queue.put(work)
    tasks = [
        (task1, 'Async1', s_queue),
        (task1, 'Async2', s_queue),
        (task1, 'Async3', s_queue)
    ]
    for t, n, q in tasks:
        t(n, q)
if __name__ == '__main__':
    s_async()

```

Output：

```python
Task Async1 is running now.
Task Async1 is running with a total of: 2
Task Async1 is running now
...
Task Async1 is running now.
Task Async1 is running with a total of: 5
Task Async1 is running now
...
Task Async1 is running now.
Task Async1 is running with a total of: 10
Task Async1 is running now
...
Task Async1 is running now.
Task Async1 is running with a total of: 15
Task Async1 is running now
...
Task Async1 is running now.
Task Async1 is running with a total of: 20
Task Async3 has nothing to do

```

