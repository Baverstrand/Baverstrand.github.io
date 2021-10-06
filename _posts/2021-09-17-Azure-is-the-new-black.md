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

Serverless is where the server capacity is in the cloud, where the cloud provider takes care of the hardware stuff. This means you use capacity on demand as a service instead of having to maintain capacity you rarely use (Private clouds) or having to identify the need for and manage scaling yourself as you do with IaaS. This means you only use (and pay for) capacity when invoked. 

FaaS means you deploy small pieces of code (functions) to the cloud and your cloud provider more or less takes it from there. The function gets triggered from some kind of event (a button gets pressed, a timer or some kind of call for example) and executes its function. Then it goes idle again. This means the function only uses resources (and money) when called upon. Also every event triggers its own instance of the function which means there is no risk of overloading the function itself since several instances of the function can run simultaneously.However, if the function uses third-party applications, like a database for example, there is still the same risk of overloading that. 
Not being dependent on a specific place or service can cut the down time to close to zero. 

### Describe your calculator

The calculator is a HTTP-triggered Azure Function of the simplest kind. I installed Azure in VS Code, used a template for a HTTP-triggered function and took it from there. Since the point of the exercise is more about trying to keep a descent level of security rather than analyzing indata, I did not separate the BadRequest-messages.  

- Only works with GET-requests
- I declared two strings, "first" and "second" from the HttpRequest.Query
- Performs a TryParse to doubles on the strings
- If the TryParses succeed, the result is returned with a code 200
- If the TryParses are unsuccessful, a message is returned with a code 400

To make my function run in Azure I created storage and a Function App from the Azure page with a little help from the steps in the sample script on this [Microsoft Docs](https://docs.microsoft.com/en-us/azure/azure-functions/scripts/functions-cli-create-function-app-github-continuous)  page. Then I made a CI/CD pipeline with GitHub Actions with the "Deploy Node.js to Azure Web App" template, modified it to match my code and deployed it from there. Again with a little help from [Microsoft Docs](https://docs.microsoft.com/en-us/azure/azure-functions/functions-how-to-github-actions?tabs=dotnet). 

![YAML file](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210917yaml.JPG)

When I got green lights from the Actions tab in GitHub I went back to Azure to test my function. 
From the Dashboard in Azure you can find the Code + Test page. Fill in your parameters and check out the result!

![Find the test](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210917findtest.JPG)

![Enjoy the output](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210917output.JPG)

### Which are the security issues with your application?  

One issue with an application that receives input data is *injection* - an attach through the request data. 
To avoid this I validate the input; I don't use it as is. If it is anything but numbers my functions returns *BadRequest*.

Another issue might be *exposure of sensitive data*. When setting up the CI/CD workflow file I used secrets and environmental settings and tokens provided by both GitHub and Azure, being careful not to expose any usernames, passwords or other keys. 

![Secrets in YAML](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210917secret.JPG)