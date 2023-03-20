---
title: Docker Sample application
author: kimjeahyun
date: 2022-10-08 19:00:00 +0900
categories: [openSource, Docker]
tags: [openSource, Docker]
---

# Sample application 

For the rest of this tutorial, we will be working with a simple todo list manager that is running in Node.js. If you’re not familiar with Node.js, don’t worry. No real JavaScript experience is needed.

At this point, your development team is quite small and you’re simply building an app to prove out your MVP (minimum viable product). You want to show how it works and what it’s capable of doing without needing to think about how it will work for a large team, multiple developers, etc.

# Get the app

Before we can run the application, we need to get the application source code onto our machine. For real projects, you will typically clone the repo. But, for this tutorial, we have created a ZIP file containing the application.

Download the App contents from the getting-started repository. You can either pull the entire project or download it as a zip and extract the app folder out to get started with.

Once extracted, use your favorite code editor to open the project. If you’re in need of an editor, you can use Visual Studio Code. You should see the package.json and two subdirectories (src and spec).


# Build the app's container image

in order to build the application , we need to use a Dockerfile. a Dockerfile is simply a text-based script of instructions that is used to create a container Image, If you'have created Dockerfiles before , you might see a few flaws in the Dockerfile below. But, don't worry. we'll go over them.

1.Create a file named Dockerfile in the same folder as the file package.json with the following contents.

~~~
# syntax=docker/dockerfile:1
FROM node:12-alpine
RUN apk add --no-cache python2 g++ make
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]
EXPOSE 3000
~~~

Please check that the file Dockerfile has no file extention like .txt 
Some editors may append this file extention automatically and this would result in an error in the next step.

2.If you haven't aleady done so, open a terminal and go to the app directory with the Dockerfile. Now bulid the container image using the docker build command.

```bash
docker bulid -t getting-started.
```

This command used the Dockerfile to build a new container image. you might have noticed that a lot of 'layers' were downloaded This is because we instructed the builder that we wanted to start from the node:12-alpine image. But since we didn't have that on our machine, that image needed to be downloaded.

After the image was downloaded , we copied in our application and used yarn to install or application's dependencies. The CMD directive specifies the default command to run when starting a container from this image.

Finally, the -t flag tags our image. Think of this simply as a human-readable name for the final image. since we named the image getting-started , we can refer to that image when we run a container.

The .at the end of the docker build command tells Docker that is should look for the Dockerfile in the current dicrectory.


