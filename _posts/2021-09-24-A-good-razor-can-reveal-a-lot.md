---
title: "A good razor can reveal a lot"
excerpt_separator: "<!--more-->"
categories:
  - Blog
  - School
tags:
  - .NET
  - Azure
  - Razor Pages
  - MongoDb
  - Docker
  - Visual Studio
  - Visual Studio Code
  - School Work
---

## Web applications in the cloud

### About the application

The application does exactly the same as the function from [our last assignment](https://baverstrand.github.io/blog/school/Throw-something-in-and-see-what-comes-out/), you can post new and view old complaints, but with a simple frontend. 
On the [start page](https://bigclappdocker.azurewebsites.net) you can submit a new complaint, and when you go to the history tab you view all previously submitted complaints. 

This is the code for submitting a new claim. The `_appsettings.RootUrl` is an Environmental Variable - it differs between running app locally and deployed to the cloud in some way! I've added it as an Application Setting in Azure. 

HTML

![SubmitHTML](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210924indexhtml.jpg)

Code

![SubmitCode](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210924indexcode.jpg)

Result

![SubmitPage](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210924indexpage.jpg)

Application setting

![ApiSettings](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210924apisetting.jpg)

I started with the ASP.NET Core Web App template to get the basic file structure. Most of the code structure is the same as in our Ludo 2 project where we also used Razor pages. I started out with getting my MongoDB connected with good help from [Microsoft](https://docs.microsoft.com/en-us/aspnet/core/tutorials/first-mongo-app?view=aspnetcore-2.2&tabs=visual-studio) and this tutorial at [DEV](https://dev.to/zoltanhalasz/mongodb-crud-with-asp-net-core-razor-pages-simple-tutorial-gbe). At first I had some certificate issues - my app was built properly but complained about a certificate. Both the error message and [Microsoft](https://docs.microsoft.com/en-us/aspnet/core/security/enforcing-ssl?view=aspnetcore-5.0&tabs=visual-studio#trust-the-aspnet-core-https-development-certificate-on-windows-and-macos) said to delete certificates and make a new one and restart VS. That did NOT work. Finally I found a [blogpost](https://itnext.io/installed-asp-net-16702767e7b3) to help me out. 

### How I got it to run everywhere

I have mostly relied on the provided tutorials in the assignment text. To publish the application straight to Azure App Services I used the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice) extenstion and simply followed it step by step. 

When I first created the application in Visual Studio I added support for Docker immediately, and VS made the Dockerfile for me. Experience told me there was going to be trouble, and I was just right. Auto-generated Dockerfile tends to cause some trouble when the `.sln` file is placed one level up from the Dockerfile. The changes I made are commented out in the picture.

![Dockerfile](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210924dockerfile.jpg)

After getting the Dockerfile to build properly, I just followed the [Hildenco Software tutorial](https://blog.hildenco.com/2020/10/pushing-docker-images-to-azure.html) almost step by step to push my Dockerfile to Azure Container Registry.
The [Visual Studio Code](https://code.visualstudio.com/docs/containers/app-service) took me almost all the way to running my application in App Service via Docker image. Colon is not a valid punctuation mark when deploying via Dockerfile, but someone at [Stackoverflow](https://stackoverflow.com/questions/51480085/configuring-appsettings-with-asp-net-core-on-azure-web-app-for-containers-whith) figured it out!

The deployments has not been the difficult thing this time, it has clearly been "everything else" around it. The MongoDB tutorials for example put their connection string in appsettings which is fine when you run the application locally, but when I pushed to GitHub and Azure I needed to figure out something else. My solution was to make it an Environmental Variable just like I later did with the base URL. I also had to add a few lines in `Program.cs`. 

![Environmental](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210924environmental.jpg)

### Cost calculation

Just like the other day, I'm in the dark trying to figure out what is a lot and what is not, but here is another try on calculation comparasion!

Lowest, cheapest alternative on everything

![Low cost](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210924costlow.jpg)

Premium where available, multiple region, a lot of data and service for dummies

![High cost](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210924costhigh.jpg)

Upfront cost stays at zero. I might have gone through the roof with the container registry, but still it's obvious that it's not the app service that costs the big $$$
