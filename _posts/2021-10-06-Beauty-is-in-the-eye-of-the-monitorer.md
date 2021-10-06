---
title: "Beauty is in the eye of the monitorer"
excerpt_separator: "<!--more-->"
categories:
  - Blog
  - School
tags:
  - .NET
  - Azure
  - Serilog
  - Logging
  - Razor Pages
  - School Work
---
### Monitoring  
### The application  

I have, once again, recycled my [complaints app (ClApp)](https://bigclapplogged.azurewebsites.net/). It asks the user to submit a complaint and then redirects the user (if they do it right) to the history page to view all previous complaints. It's a simple app, but it has functions enough to fake some events to log. I deployed it to a workspace in Azure in order to have everything in the same place (app, insights and database).

### How ClApp interacts with other services  

![Diagram](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/211006appmap.jpg)

### ClApp code 

I have used [Serilog](https://serilog.net/) and the built in method Stopwatch for my logging. I installed a __bunch__ of NuGet packages.  

![NuGets](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/211006nugets.jpg)  

Runninig local I put the key to Application Insights in appsettings, and on Azure with the Environmental Variables to get it out of the code put on GitHub.  
Since I have a web application, I had to add code both to `Program.cs` and `Startup.cs`. The information about what to do goes straight into `Main` method in `Program.cs`, the `.UseSerilog()` in `CreateHostBuilder()` and then finally two lines in `ConfigureServices()` in `Startup.cs`.
After getting the logging into the configuration I could start logging here and there.  
Since this is not a very complicatied application with tons of users, I had to fake some errors in order to show my logging works.  
To measure the time it takes to load a page I used the built in `Stopwatch()`. I start the stopwatch it before the `<body>` of the page is loaded and stop it and log it right after the `</body>` tag. 

![StopWatch](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/211006watchcode.jpg)  

I the user tries to submit a negative number or zero as an ID number it gets logged as either a Warning or Error. This to get something to log :) 

![Error and Warning](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/211006errorcode.jpg)  

If there is something wrong with the registration of the complaint in the database it also gets logged. 

![Db Warning](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/211006dberror.jpg)  

### How logging information can prevent safety issues in my application  

Logging information is essential to keep track of the health of the application. If you have a good idea of what's normal, then you can immediately know when something is not.  
Also logging is very important regarding security, especially for web applications. 
If there is a sudden increase of error codes in the 400-series (bad request, file not found, unauthorized request and so on) it might be a sign of an attack. Mostly bad request or unauthorized indicates an injection attack of some kind is going on. 
If there are a lot of 500-errors (internal server error) something or someone could be trying to take down your application. 

### My queries  

- When a new complaint is posted. This was the first one I made, just to warm up  

![New complaint](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/211006kustocomplaint.jpg)  

- How long the different pages takes to load. If a page takes really long time, maybe there's some mistake in the code!

![Loading times](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/211006kustoload.jpg)  

- All the warnings and errors. I also made requests to keep warnings and errors apart. Going live it's better to keep them separated since an error is more severe than just a warning and they will probably trigger different actions.   

![Severity levels](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/211006kustoseverity.jpg)  

### My helpers  

- [Serilog's GitHub page](https://github.com/serilog/serilog-settings-configuration)
- [Arve's code cave](https://arvehansen.net/codecave/2020/03/01/appinsights-and-logging-with-serilog/)
- [Samples for Kusto Queries](https://docs.microsoft.com/en-us/azure/data-explorer/kusto/query/samples?pivots=azuredataexplorer)
- [Application Insights for ASPNET Core applications](https://docs.microsoft.com/en-us/azure/azure-monitor/app/asp-net-core)
- [Stackoverflow](https://stackoverflow.com/questions/11459060/razor-void-function)