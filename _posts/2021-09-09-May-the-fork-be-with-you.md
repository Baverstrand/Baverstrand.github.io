---
title: "May the fork be with you"
excerpt_separator: "<!--more-->"
categories:
  - Blog
  - School
tags:
  - .NET
  - GitHub
  - GitHubAction
  - CI pipeline
  - YAML
  - Skolarbete
---

### What is a CI-pipeline?

To explain what a *CI-pipeline* is you need to know what *CI* is. 
*CI* stands for *Continuous integration* and means you continuously push your code in smaller portions into a bigger project. 
To make it work with several developers pushing to the same project the code being pushed has to be without conflict and testable. 
This is where a CI-pipeline comes in the picture!

![Image of a CI/CD-pipeline](https://www.edureka.co/blog/content/ver.1531719070/uploads/2018/07/What-is-Devops-CI-CD-Pipeline-Edureka.png)

Picture from [DZone](https://dzone.com/articles/learn-how-to-setup-a-cicd-pipeline-from-scratch)

The left part of the picture describes a CI-pipeline. The build- and test part is triggered when, for example, code is pushed or a pull-request is created. If the code for some reason doesn't build or the tests aren't passed the function tells you and you can quickly find and fix the issue immediately instead of manually testing and trying to find where something went wrong afterwards. A CI-pipeline strongly reminds of a [PDCA-wheel](https://en.wikipedia.org/wiki/PDCA) (Plan, Do, Check, Act) which origins from automotive industry where it's used as a tool for continuous improvements. 

An agile approach places demands on the developers. Everyone in the team has to commit and push often, or else their code will quickly fall behind and become inaccurate. This makes it difficult to merge into the branch you are working against.  

The right part of the picture describes the CD-part of the pipeline. *CD* stands for *Continuous Deployment* or *Delivery* and is about what happens with the code after passing the CI-part. These processes can also be automated which means the process is both faster and more secure than manual processing. 

### How we implemented a CI-pipeline on an existing project

We chose to implement the pipeline on our first SpacePark-project. 
Since we forked the project we only needed minor adjustments were needed to make it work with the automation.  We only had to remove appsettings.json from the .gitignore.file. When working in group each person had their own local copy of the appsettings file since we had different paths to our databases, but without it, GitHub won't build the project.  

In the Actions menu we chose "New Workflow" at the start page for SpacePark in GitHub. Since we didn't want our pipeline to do something really advanced, we chose the .NET template to modify. 
The assignment says the action should be triggered on every commit, but this is not to be done (if you for example work in VS Code you can make several commits before actually pushing without GitHub knowing about it) a push is the trigger instead. We took away the "pull request" from the trigger list and also "main" from push condition since we wanted to trigger the action on push to *all* branches. 

On jobs I changed to Windows instead of Ubuntu. I tried out both, but left Windows. 

On Restore, Build and Test we had to add the path to SpacePark.sln for the file to find what was to be built and tested. 

At the very end, I added an echo-thing just to be funny

### Description of my YAML-file

Descriptive text (in Swedish) in the picture

![My YAML-file](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/yamlexplained.JPG)


__Resources__
- [IDG.se](https://cio.idg.se/2.1782/1.730602/ci-cd-standiga-flodet)
- [Semaphore](https://semaphoreci.com/continuous-integration)
- [Info World](https://www.infoworld.com/article/3271126/what-is-cicd-continuous-integration-and-continuous-delivery-explained.html)