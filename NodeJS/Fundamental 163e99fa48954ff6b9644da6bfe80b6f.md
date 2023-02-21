# Fundamental

Category: NodeJS
Tags: Concept, Medium

- Table of content

# 1. Fundamental

![Untitled](Fundamental%20163e99fa48954ff6b9644da6bfe80b6f/Untitled.png)

**Notes**

## Basic

- Không có `window`
- Run command `$ node` ⇒ run node in mode repl (read eval print and loop)
    - Tương đương tag `console` ở browser

## Process

- **argv**: array
    - Contain path to node

## Stream Promises API

- Convert steam to promise

**Recall**

- eval = evaluate: phỏng đoán

---

# 2. Runtime

![Untitled](Fundamental%20163e99fa48954ff6b9644da6bfe80b6f/Untitled%201.png)

**Notes**

- Node JS = Javascript engine + NodeJS’s APIs
    - fs
    - http
    - path
    - crypto: security
- NodeJS’s APIs ← NodeJS’s binding = written in C || C++
    - NodeJS’s binding ← libuv
    - libuv = asynchronous I/O
        - File
        - Request
- Event Loop Phases:
    1. Timers
        - setTimeout
        - setInterval
    2. I/O callbacks: file system
        - callback after finishing I/O action
    3. setImmediate: special kind of timers
    4. Close callbacks
        - For closing file, connection
- Each phase has own queue of callback

**Recall**

- Khi asynchronous I/O bắt event ⇒ truyền callback vào event loop

---