---
title: "Moby Dick has room for everything"
excerpt_separator: "<!--more-->"
categories:
  - Blog
  - School
tags:
  - .NET
  - Docker
  - School Work
---

## Containers and orchestration

### What did you install locally / GitHub?

In order to have an application running in a Docker container I need:

- [Docker Desktop](https://docs.docker.com/get-docker/)
- Some kind of CLI, I use Windows PowerShell
- An application to run :)

### How did you get the application running in the container?

We chose to use the Chris Noring [tutorial](https://softchris.github.io/pages/dotnet-dockerize.html) which only needed minor modifications to make it work. 
For example, we could skip the step creating a new project since we already cloned a previous one. 

In order to make the Dockerfile build properly, we needed to change SDK version from 2.2 (in the tutorial) too SDK 3.1.
We also changed the ENTRYPOINT .dll file name to the same as the application. 
Having this done, we could use the following commands and view the app in the web browser at localhost:80:
´docker build -t webapp .´
´run -d -p 8080:80 --name webappup webapp´

