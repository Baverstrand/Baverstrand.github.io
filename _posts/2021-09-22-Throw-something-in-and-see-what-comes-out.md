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

Vad skulle det kosta att driva detta? Tänk gärna två scenarier: Nästan ingen använadere och jätte jätte mycket användere
Använd Azure Calculator till att ta fram kostnad



## Databases in the cloud

### My function and how it works 

I made a Http-triggered function where you can post and see complaints. You can *POST* a new complaint, and you can *GET* all complaints from the database.
In order to make it easy for myself i used an if-statement to separate *post* and *get*.  

![The if-statement](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210922if.jpg)

#### Post

On *post*, you submit Customer ID, Customer Name and your Problem Description like this and get a message back:

![Post in Postman](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210922postresult.jpg)

If you post invalid data, you will get a Bad Request status and a message about that:

![Post bad in Postman](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210922postbadresult.jpg)

The code basically consists of a try/catch where the request body gets converted into a json Issue (see picture of Issue class) and stored in the database. If the conversion is unsuccessful the catch returns a Bad Request.

![Post code](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210922post.jpg)

`public string _id` is set upon writing to database, and as you can see in the database structure picture further down becomes a, for the db, unique id. 

![Issue class](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210922issue.jpg)

#### Get

On *get* a call with an empty filter is made to the db, which returns all posts in it. The issues in the result is converted into anonymous objects in order to remove sensitive identification data. 

![Get code](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210922get.jpg)

And the return looks like this:

![Get result](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210922getresult.jpg)

### My database and how it works

I made the database with the Azure Database extension for VS Code.
This assignment seemed to be a good opportunity to learn a bit about MongoDB since everything is in json format, and with a little help from a friend I got it up and running quite smoothly! I structured it like this, and here you can also see what I mentioned above about the unique id:

![Db structure](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922db.jpg)

To reach the db from my function and make it easy to work with there were a few steps to be made. First, finding the connection string to be able to make an instance of the database client. Then I also declared the database and everything in it to use later on. 

![Db connection](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922dbconnect.jpg)

### Orchestration

To keep track of the components in this assignment, I put everything in the same (new) Resource group in Azure. 

The function is created the same way as [the calculator I made the other day](https://baverstrand.github.io/blog/school/Azure-is-the-new-black/). New function in Visual Studio -> save in new repo on GitHub. New Function App in Azure -> get the function from GitHub via Deployment Center which created a GitHub Actions file. All I had to do with the action file was to set the dotnet version and remove the .sln file. I ran into some trouble upon building since there was a conflict when I had both a .csproj and a .sln file in the same directory. I spent some time trying to find the right combination of paths, but I gave up and just removed the .sln file. 

As I mentioned earlier I used the Azure Database extension to create the database. The [Build a .NET Core App...](https://docs.microsoft.com/en-us/learn/modules/build-cosmos-db-app-with-vscode/) tutorial was also really helpful. Once it was created I went to the portal, and from the database Settings/Connectionstring/PrimaryConnectionstring I copied the connection string and pasted it into local.settings.json in the "values" section. I did this to be able to do test runs locally instead of making new deploys all the time. 

With the function running locally, I can use [Postman](https://www.postman.com/) for testing. 

To test run the function from Azure I had to add the connection string as an Application Setting in Azure. 

![Connection string](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922connectionstring.jpg)

### Thoughts about changing schemas and new migrations

Since this is a MongoDb database, migrations is not really an issue. That's one of the good things about MongoDb.
If there are properties in my db which are not in my *Issue* class, I need to ignore those using code. I will need to keep track on what is where in order of my db not to crash!

### Cost calculation

The cost calculation is a bit tricky since I have NO idea of how much is a lot and not, but a fantasy comparation at least shows that the up fron cost is low even if the traffic is high :)

Low traffic cost
![Low cost](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922lowcost.jpg)

Fantasy high cost
![High cost](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922highcost.jpg)
