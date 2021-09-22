---
title: "Throw something in and see what comes out"
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

### My function and how it works 

I made a Http-triggered function where you can post and see complaints. You can *POST* a new complaint, and you can *GET* all complaints from the database.
In order to make it easy for myself i used an if-statement to separate *post* and *get*.  

![The if-statement](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922if.jpg)

#### Post

On *post*, you submit Customer ID, Customer Name and your Problem Description like this and get a message back:

![Post in Postman](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922postresult.jpg)

If you post invalid data, you will get a Bad Request status and a message about that:

![Post bad in Postman](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922postbadresult.jpg)

The code basically consists of a try/catch where the request body gets converted into a json Issue (see picture of Issue class) and stored in the database. If the conversion is unsuccessful the catch returns a Bad Request.

![Post code](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922post.jpg)

`public string _id` is set upon writing to database, and as you can see in the database structure picture further down becomes a, for the db, unique id. 

![Issue class](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922issue.jpg)

#### Get

On *get* a call with an empty filter is made to the db, which returns all posts in it. The issues in the result is converted into anonymous objects in order to remove sensitive identification data. 

![Get code](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922get.jpg)

And the return looks like this:

![Get result](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922getresult.jpg)

### My database and how it works

I made the database with the Azure Database extension for VS Code.
This assignment seemed to be a good opportunity to learn a bit about MongoDB since everything is in json format, and with a little help from a friend I got it up and running quite smoothly! I structured it like this, and here you can also see what I mentioned above about the unique id:

![Db structure](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922db.jpg)

To reach the db from my function and make it easy to work with there were a few steps to be made. First, finding the connection string to be able to make an instance of the database client. Then I also declared the database and everything in it to use later on. 

![Db connection](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922dbconnect.jpg)

### Orchestration









You need to make your post in the right format, or the function will return Bad Request

To make my function run in Azure I created storage and a Function App from the Azure page with a little help from the steps in the sample script on this [Microsoft Docs](https://docs.microsoft.com/en-us/azure/azure-functions/scripts/functions-cli-create-function-app-github-continuous)  page. Then I made a CI/CD pipeline with GitHub Actions with the "Deploy Node.js to Azure Web App" template, modified it to match my code and deployed it from there. Again with a little help from [Microsoft Docs](https://docs.microsoft.com/en-us/azure/azure-functions/functions-how-to-github-actions?tabs=dotnet). 

![YAML file](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210917yaml.JPG)

When I got green lights from the Actions tab in GitHub I went back to Azure to test my function. 
From the Dashboard in Azure you can find the Code + Test page. Fill in your parameters and check out the result!

