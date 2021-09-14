---
title: "Moby Dick has room for everything"
excerpt_separator: "<!--more-->"
categories:
  - Blog
  - School
tags:
  - .NET
  - Docker
  - YAML
  - CI/CD
  - Workflow
  - School Work
---

## Containers and orchestration

### What did you install locally / GitHub?

In order to have an application running in a Docker container I need:

- [Docker Desktop](https://docs.docker.com/get-docker/)
- Some kind of CLI, I use Windows PowerShell
- An application to run :)

For the third task we used the [Build and Push Docker Images](https://github.com/marketplace/actions/build-and-push-docker-images) Action template. 

### How did you get the application running in the container?

We chose to use the [Chris Noring tutorial](https://softchris.github.io/pages/dotnet-dockerize.html) which only needed minor modifications to make it work. 
For example, we could skip the step creating a new project since we already cloned a previous one. 

In order to make the Dockerfile build properly, we needed to change SDK version from 2.2 (in the tutorial) too SDK 3.1.
We also changed the ENTRYPOINT .dll file name to the same as the application. The .dockerignore file was left as is.  
Having this done, we could use the following commands and view the app in the web browser at localhost:80:

`docker build -t webapp .`

`run -d -p 80:80 --name webappup webapp`

### Describe you Dockerfile

The Dockerfile is basically a copy from the [Chris Noring tutorial](https://softchris.github.io/pages/dotnet-dockerize.html). We changed the SDK (Software Developer Kit) version to 3.1 to make it work properly. Also the name of the .dll- file was changed. Explanations in green text in the picture. 

![Dockerfile](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210914dockerfile.JPG)

### Describe your GitHub Pipeline

We started out with the pipelinefile described in the [Fork Post](https://baverstrand.github.io/blog/school/May-the-fork-be-with-you/), but soon we realized we could delete most of it and just use the example from the instructions and combine with a slightly adjusted template from [Build and Push Docker Images](https://github.com/marketplace/actions/build-and-push-docker-images). First I added stuff and modified until I got it working, and then I took away stuff until I found (what I think is) minimum needed. What is left now is:

- Actions get triggered on *pushes to master branch*
- The only job step is docker related:
  1. Login to GitHub Container Registry using *login action*
  2. Build and push using *build push action* tagging the webpack with *latest* and the run number of the push

### There are two *tags*, try to explain why

The run number tag is to keep track of the order, it's like an extension of the name to make things clear. 
I made an experiment and took away the *latest* tag and quickly realized why I need it. 

The first image shows what happened when I took the tag away. The succeeding push was, of course, not tagged with *latest*, and when using the command `docker pull ghcr.io/baverstrand/webapp` it turns out the default tag to look for is *latest* (second image). In this particular case it means I would pull run #37 instead of #38... 

![Tags](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210914tags.JPG)

![Latest](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210914latest.JPG)

### How did you manage secrets?

When logging in to Github Container Registry I used `{ { github.actor } }` to set the username and `{ { secrets.GITHUB_TOKEN } }` instead of the password. GitHub automatically creates GITHUB_TOKEN for the repository when you enable GitHub Actions. 
In the tags I used `{ { github.actor } }` to avoid showing my username in plain text. 