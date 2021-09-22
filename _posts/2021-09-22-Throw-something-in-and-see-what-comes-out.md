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
  - MongoDb
  - CI/CD
  - GitHub
  - GitHub Actions
  - School Work
---


Beskriv kort applikationen, vad gör den?
Beskriv koden
Beskriv databasen
Hur har du/ni fått den att köra i Azure functions? Screenshots, scrips, pipelines
Hur har du tänkt runt uppdatring av databsen ifall scheman ändras? Migrations?
Vad skulle det kosta att driva detta? Tänk gärna två scenarier: Nästan ingen använadere och jätte jätte mycket användere
Använd Azure Calculator till att ta fram kostnad



## Databases in the cloud

### Description of my function and how it works 

I made a Http-triggered function where you can post and see complaints. You can *POST* a new complaint, and you can *GET* all complaints from the database. 

#### Post

On *post*, you submit Customer ID, Customer Name and your Problem Description like this and get a message back:

![Post in Postman](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922postresult.JPG)

If you post invalid data, you will get a Bad Request status and a message about that:

![Post bad in Postman](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922postbadresult.JPG)

The code basically consists of a try/catch where the request body gets converted into json Issue (see picture of Issue class) and stored in the database.
`public string _id` is set upon writing to database, and as you can see in the database structure picture further down becomes a, for the db, unique id. 

![Issue class](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922issue.JPG)

I made the database with the Azure Database extension for VS Code, and it's structured like this:

![Db structure](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922db.JPG)






You need to make your post in the right format, or the function will return Bad Request

To make my function run in Azure I created storage and a Function App from the Azure page with a little help from the steps in the sample script on this [Microsoft Docs](https://docs.microsoft.com/en-us/azure/azure-functions/scripts/functions-cli-create-function-app-github-continuous)  page. Then I made a CI/CD pipeline with GitHub Actions with the "Deploy Node.js to Azure Web App" template, modified it to match my code and deployed it from there. Again with a little help from [Microsoft Docs](https://docs.microsoft.com/en-us/azure/azure-functions/functions-how-to-github-actions?tabs=dotnet). 

![YAML file](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210917yaml.JPG)

When I got green lights from the Actions tab in GitHub I went back to Azure to test my function. 
From the Dashboard in Azure you can find the Code + Test page. Fill in your parameters and check out the result!

![Find the test](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210917findtest.JPG)

![Enjoy the output](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210917output.JPG)

### Which are the security issues with your application?
Vilka säkerhets hot finns där till en applikation om din (beskriv minst en)? Och har du gjort något för att säkra dig emot dissa? (hint: OWASP top 10 - Interpretation for Serverless)

One issue with an application that receives input data is *injection* - an attach through the request data. 
To avoid this I validate the input; I don't use it as is. If it is anything but numbers my functions returns *BadRequest*.

Another issue might be *exposure of sensitive data*. When setting up the CI/CD workflow file I used secrets and environmental settings and tokens provided by both GitHub and Azure, being careful not to expose any usernames, passwords or other keys. 

![Secrets in YAML](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210917secret.JPG)