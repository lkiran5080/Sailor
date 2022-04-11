# Sailor - Secure Online Compiler

> This code is submitted to Vmware Campus Hackathon

## High-level System Architecture

![](./project/architecture.png)

## Built With

- Flask (Python based Web Framework)
- Gunicorn (Python WSGI HTTP Server for UNIX)
- Nginx (Web Proxy)

### Storage

- PostgreSQL (Relational Database for publishing results)
- SQLAlchemy (Object Relational Mapper)
- Alembic (Database Migration Tool)
- Redis (In-memory NoSQL Database used for caching)

### Sandboxed Remote Code Execution

- RabbitMQ (Message Broker)
- Celery (Python based Asynchronous Task Queue)
- Docker (For Sandboxing)

### Monitoring, Logging & Management

- Supervisord (Process Monitoring)
- Flower (Celery Monitoring)
- pgAdmin (Postgres management)
- RabbitMQ Management Pod

### Endpoint Security

- Bcrypt (Secure password hashing algorithm and module)

## Security Model

### Secure Code Execution

**Multiple Layers of Security**

- Running code submitted by users in a remote Docker container
  - Sandboxing Container
    - Limiting Pod Resources
    - Restricting Network I/O
    - Execution Environment Level restrictions 

> Worst case scenario : 
>
> Execution Environment Crashes => Drop the Task => Flag malicious actor/Repeated abuser => Fresh Pod Restarts
>
> Rest of the system keeps running

- Task level
  - Limiting the number of process task can spawn
  - Limiting no. of files
  - Limiting file size it can write
  - Limiting CPU usage
  - Liming memory address space

### Endpoint Security

- Taking care of OWASP Top 10
  - Using `CSRF` Tokens
  - Using `httpOnly` cookies only
  - Security Headers
  - etc...

## Sailor Screenshots

![](./project/sailor01.png)

### Authentication

![](./project/login.png)

![](./project/registeration.png)

### Editor Interface

![](./project/editor0.png)

![](./project/editor.png)

### Terminal Output Streams

![](./project/output.png)

![](./project/stderr.png)

### Design Peek-a-boo

![](./project/sailor02.png)

## How to run?

:exclamation: The project relies on Docker & Docker Compose!

```
$ docker-compose up -d --scale worker=5
```

Now you can go to http://localhost:5000

## Demo

https://drive.google.com/drive/folders/1A6wwHqFHAZsnKSbA7Op2tet0y3nKRAVo?usp=sharing

## Team

Team Name : Thundering Bits

Lakshay, National Institute of Technology Kurukshetra  
https://github.com/lkiran5080  
lakshay5080@gmail.com

Sahil, National Institute of Technology Kurukshetra  
https://github.com/SahilKumar7  
sahil.kumar5729@gmail.com
