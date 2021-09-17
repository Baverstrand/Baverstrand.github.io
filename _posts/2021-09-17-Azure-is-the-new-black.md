---
title: "Azure is the new black"
excerpt_separator: "<!--more-->"
categories:
  - Blog
  - School
tags:
  - .NET
  - Serverless
  - Azure
  - YAML
  - CI/CD
  - GitHub
  - School Work
---
## Serverless applications

### What is Serverless and Function As A Service (FaaS)?
Serverless is where the server capacity is in the cloud, where the cloud provider takes care of the hardware stuff. This means you use capacity on demand as a service instead of having to maintain capacity you rarely use (Private clouds) or having to identify the need for and manage scaling yourself as you do with IaaS. This means you only use (and pay for) capacity you actually use. 

Faas means you deploy small pieces of code (functions) to the cloud and your cloud provider more or less takes it from there. The function gets triggered from some kind of event (a button gets pressed, a timer or some kind of call for example) and executes its function. Then it goes idle again. This means the function only uses resources when called upon. Also every event triggers its own "copy" of the function which means there is no risk of overloading it. 
Not being dependent on a specific place or service can cut the downtime to almost zero. 

upp-tid endast
automatisk upp- och nedskalning
polyglott - 
highly available, ingen downtime

### Describe your calculator
Beskriv din/eran kalkylator.
Koden?
Hur har du/ni fått den att köra i Azure functions? Screenshots, scrips, pipelines
Hur har du testat appliktionen?

### Which are the security issues with your application?
Vilka säkerhets hot finns där till en applikation om din (beskriv minst en)? Och har du gjort något för att säkra dig emot dissa? (hint: OWASP top 10 - Interpretation for Serverless)



## Containers and orchestration

### What did you install locally / GitHub?

In order to have an application running in a Docker container I need:

- [Docker Desktop](https://docs.docker.com/get-docker/)
- Some kind of CLI, I use Windows PowerShell
- An application to run :)

For the third task we used the [Build and Push Docker Images](https://github.com/marketplace/actions/build-and-push-docker-images) Action template. 
