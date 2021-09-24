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
  - School Work
---


Hur har du/ni fått den att köra i Azure App Service? Screenshots, scrips, pipelines
Vad skulle det kosta att driva detta? Tänk gärna två scenarier: Nästan ingen använadere och jätte jätte mycket användere
Använd Azure Calculator till att ta fram kostnad


## Web applications in the cloud

### About the application

The application does exactly the same as the function from [our last assignment](https://baverstrand.github.io/blog/school/Throw-something-in-and-see-what-comes-out/), you can post new and view old complaints, but with a simple frontend. 
On the start page you can submit a new complaint, and when you go to the history tab you view all previously submitted complaints. 

This is the code for submitting a new claim. The `_appsettings.RootUrl` is an Environmental Variable - it differs between running app locally and deployed to the cloud in some way! I've added it as an Application Setting in Azure. 
![SubmitHTML](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210924indexhtml.jpg)
![SubmitCode](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210924indexcode.jpg)
![SubmitPage](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210924indexpage.jpg)
![ApiSettings](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210924apisetting.jpg)

I started with the ASP.NET Core Web App template to get the basic file structure. Most of the code structure is the same as in our Ludo 2 project where we also used Razor pages. I started out with getting my MongoDB connected with good help from [Microsoft](https://docs.microsoft.com/en-us/aspnet/core/tutorials/first-mongo-app?view=aspnetcore-2.2&tabs=visual-studio) and this tutorial at [DEV](https://dev.to/zoltanhalasz/mongodb-crud-with-asp-net-core-razor-pages-simple-tutorial-gbe). At first I had some certificate issues - my app was built properly but complained about a certificate. Both the error message and [Microsoft](https://docs.microsoft.com/en-us/aspnet/core/security/enforcing-ssl?view=aspnetcore-5.0&tabs=visual-studio#trust-the-aspnet-core-https-development-certificate-on-windows-and-macos) said to delete certificates and make a new one and restart VS. That did NOT work. Finally I found a [blogpost](https://itnext.io/installed-asp-net-16702767e7b3) to help me out. 

### How I got it to run everywhere

I have mostly relied on the provided tutorials in the assignment text. To publish the application straight to Azure App Services I used the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-azureappservice) extenstion and simply followed it step by step. 

When I first created the application in Visual Studio I added support for Docker immediately, and VS made the Dockerfile for me. Experience told me there was going to be trouble, and I was just right. Auto-generated Dockerfile tends to cause some trouble when the `.sln` file is placed one level up from the Dockerfile. The changes I made are commented out in the picture.

![Dockerfile](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210924dockerfile.jpg)

After getting the Dockerfile to build properly, I just followed the [Hildenco Software tutorial](https://blog.hildenco.com/2020/10/pushing-docker-images-to-azure.html) almost step by step to push my Dockerfile to Azure Container Registry.
The [Visual Studio Code](https://code.visualstudio.com/docs/containers/app-service) took me all the way to running my application in App Service via Docker image. 

The deployments has not been the difficult thing this time, it has clearly been "everything else" around it. The MongoDB tutorials for example put their connection string in appsettings which is fine when you run the application locally, but when I pushed to GitHub and Azure I needed to figure out something else. My solution was to make it an Environmental Variable just like I later did with the base URL. I also had to add a few lines in `Program.cs`

![Environmental](https://raw.githubusercontent.com/baverstrand/Baverstrand.github.io/master/img/210924environmental.jpg)





#### Razor pages
#### MongoDb & Razor pages
- 
- 

#### Making https work
- 
- 

#### Image to Azure
[Pushing Docker images to ACR](https://blog.hildenco.com/2020/10/pushing-docker-images-to-azure.html)
[Deploy image to App Service](https://code.visualstudio.com/docs/containers/app-service)


### Cost calculation

The cost calculation is a bit tricky since I have NO idea of how much is a lot and not, but a fantasy comparation at least shows that the up fron cost is low even if the traffic is high :)

Low traffic cost
![Low cost](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922lowcost.jpg)

Fantasy high cost
![High cost](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210922highcost.jpg)
