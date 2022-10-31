---
title: Docker
author: kimjeahyun
date: 2022-10-08 19:00:00 +0900
categories: [openSource, Docker]
tags: [openSource, Docker]
---


This Article contains step-by-step instructions on how to get started with Docker. In this tutorial, You'll learn how to: 

-   Build and run an image as a container 
-   share images using Docker hub
-   Deploy Docker applications using multiple containers with database 
-   Run applications using Docker Compose 

In addition , You'll also learn about the best practices for building images, including instructures on how to scan your images for security vulnerailities

If you are looking for information on how to containerize an application using your favorite language

we also recommend the video workshop from Dockercon 2022, Watch the video below or use the links to open the video at a particular section


# Start the tutorial


```bash

docker run -d -p 80:80 docker/getting-started

```

-   -d Run the container in detached mode
-   -p 80:80 Map port 80 of the host to port 80 in the container. To access the tutorial, open a web brower and navigate to http://localhost:80. If you already have a service listening on port 80 on your host machine, you can specify another port
-   docker/getting-started Specify the image to use 

# The Docker Dashboard

Before going too far, we want to highlight the Docker Dashboard, 
which gives you a quick view of the containers running on your machine. The Docker Dashboard is available for Windows , Mac and linus It gives you quick access to container logs, lets you get a shell inside the container, and lets you easily manage container lifecycles

To access the dashboard , follow the instructions in the Docker Desktop manual


# What is a conatainer? 

Now that you have run a container , What is a container? Simply put , a container is a sandboxed process on your machine that is isolated from all other processes on the host machine. That isolation leverages kernel namespaces and cgroups, features that have been in Linux for a long time.
Docker has worked to make these capabilities approachable and easy to use. To summarize a container:

-   is a runnable instance of an image. You can create , start , stop , move, or delete a container using the DockerAPI or CLI
-   Can be run on local machines, virtual machines or deployed to the cloud.
-   is portable(can be run on any OS)
-   is isolated from other containers and runs its own software, binaries and configurations 

# What is a container image?

when running a container , it uses an isolated filesystem This custom firesystem is provided by a container image. Since the image containers the container's filesystem, it must contain everything needed to run an application - all dependencies, configurations, scripts , binaries, etc, The image also contains other configuration for the container, such as enviroment variables, a default command to run and other metadata.

# Start an app container 

Now that we have an image, let's run the application. To do so, we will use the docker run command (remember that from earlier?)

1. Start your container using the dockor run command and spcify the name of the image we just created:

```bash
docker run -dp 3000:3000 getting-started
```

! Remember the -d and -p flags? we are running the new container in detached mode and creating a mapping between the host's port 3000 to the container's port 3000 without the port mapping we wouldn't be able to access the application.

2. After a few second, open your web brower to http://localhost:3000/ You shuld wee our app.

3. Go ahead and add an item or two and see that it works as you expect. You can mark items as complete and remove items. Your frontend is successfully storing items in the backend. Pretty quick and easy, huh?

At this point, you should have a running todo list manager with a few items, all built by you. Now, let’s make a few changes and learn about managing our containers.

If you take a quick look at the Docker Dashboard, you should see your two containers running now (this tutorial and your freshly launched app container).

















