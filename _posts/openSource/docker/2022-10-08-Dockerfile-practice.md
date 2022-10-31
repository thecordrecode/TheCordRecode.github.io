---
title: Docker-practice
author: kimjeahyun
date: 2022-10-08 19:00:00 +0900
categories: [openSource, Docker]
tags: [openSource, Docker]
---


# Best practices for writing Dockerfiles

This documentation covers recommended best practices and methods for buliding efficient images.

Docker builds images automatically by reading the instructions from a Dockerfile -- a text file that contains all commands, in order , needed to build a given image. A Dockerfile adheres to a specific format and set of instructions which you can find at Dockerfile reference.

A Docker image consists of read-only layers each of which represents a Dockerfile instruction.  The layers are stacked and each one is a delta of the changes from the previous layer. consider this 

```dockerfile
# syntax=docker/dockerfile:1
FROM ubuntu:18.04
COPY . /app
RUN make /app
CMD python /app/app.py
```

Each instruction creates one layer:

-   FROM create a layer from the ubuntu:18.04 Docker image.
-   COPY adds files from your Docker client's current directory
-   RUN bulids your application with make .
-   CMD specfies what command to run within the container

When you run an image and generate a container , you add a new wriable layer on top of the underlying layers. All changes made to the running container, such as writing new files, modifying existing files, and deleting files, are written to this writable container layer.

# General guidlines and recommendations

