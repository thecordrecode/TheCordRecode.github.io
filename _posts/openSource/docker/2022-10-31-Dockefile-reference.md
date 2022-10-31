---
title: Docker
author: kimjeahyun
date: 2022-10-31 19:00:00 +0900
categories: [openSource, Docker]
tags: [openSource, Docker]
---

# Dockerfile reference 

Docker can build images automatically by reading the instructures from a Dockerfile . A Dockerfile is a text document that contains all the commands a user could call on the command line to assemble an image.  Using docker build users can create an automated build that executes serveral command-line instructures in succession.

This page describes the commands you can use in a Dockerfile When you are done reading this page, refer to the Dockerfile Best Practices for a tip-oriented guide.

# Usage 

The docker build command bulids an image from a Dockerfile and a context. The build's context is the set of files as a specified location PATH or URL. THE PATH is a directory on your local fileSystem The URL is a Git repository location.

The build context is processed recursively. So , a PATH includes any subdirectories and the URL includes the repository and its submodules. This example shows a build command that uses the current directory (.) as build context:

The build is run by the Docker Daeomon, not by the CLI. The first thing a build process does is send the entire context to the daemon. In most cases, it's best to start with an empty directory as context and keep your Dockerfile in that directory. Add only the files needed for buliding the Dockerfile.

To use a file in the build context, the Dockerfile refers to the file specified in an instruction, for example a COPY instruction To increse the build's performance, exclude files and directories by adding a .dockerignore file to the context directory. For information about how to create a .dockerignore file see the documentation on this page.

Traditionally , the Dockerfile is called Dockerfile and located in the root of the context You use the -f flag with docker build to point to a Dockerfile anywhere in your file system.

```bash
docker build -f /path/to/a/Dockerfile .
```

you can specify a repository and tag at which to save the new image if the build succeeds:

```bash
docker build -t shykes/myapp .
```


To tag the image into multiple repositorys after the build , add multiple -t parameters when you run the build command.

```bash
docker build -t shykes/myapp:1.0.2 -t shykes/myapp:latest .
```

Before the Docker daemon runs the instructure in the Dockerfile , it performs a preliminary validation of the Dockerfile and returns an error if the syntax is incorrect:

```
docker build -t text/myapp
```

The Docker daemon runs the instructions in the Dockerfile one-by-one , committing the result of each instruction to a new image if necessary, before finally outputting the ID of your new image. The Docker daemon will automatically clean up the context you sent.

Note that each instruction is run independently, and causes a new image to be created -so RUN cd/tmp will not have any effect on the next instructures.

whenever possible , Docker user a build-cache to accelerate the docker build process significantly. This is indicated by the CACHED message in the console output ( For more information , see the Dockerfile best pratices guide)\\
















