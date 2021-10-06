---
title: "Shared files are twice the files"
excerpt_separator: "<!--more-->"
categories:
  - Blog
  - School
tags:
  - .NET
  - Azure
  - Blob
  - Razor Pages
  - School Work
---
## Files and files

### My application(s)

I made two in one. My goal has been a web app made with Razor Pages from start, but I realized I need to take this one step at a time.
So I started with creating a blob storage in Azure. Then I used a template in Visual Studio and just commented away the  `CreateHostBuilder(args).Build().Run();` from `Program.cs`. With some help from [Pat](https://www.youtube.com/channel/UCWIgdMSJn8X9IwylP-7Ad8w/videos) I quickly got files uploaded to the blob, and then I spent some time to figure out how to bring them back down again. My result was a pretty simple console application with everything executed from `Program.cs` which prints out the Uri for the files in my blob storage. 

![Upload](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/211001upload.jpg)

![Download](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/211001download.jpg)

Then I commented away all this and got back to making my web app. Since this is an application just running on local host I could keep the connection string in `appsettings.json` without using Environmental Variables and such.

The web app calls Azure for a list of info on the files in a specific blob container, then I add the Uri to the container and present them in a foreach loop with the concatenated link as the image source. Tadaa!

![Frontend](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/211001frontend.jpg)

The data flows something like this:

![Data flow](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/211001flow.jpg)

### Cost estimate

I made a cost estimate over 3 months for blob storage. To calculate the amount of operations I assumed 100MB is about 20 high resolution files. The cost for views will be the big cost riser, since *all* pictures are viewes three times a day. 

![Cost calculation](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/211001cost.jpg)

### How secure can I feel using Azure blob storage?

All data saved within Azure is encrypted and accessed only via keys or login. All traffic to or from Azure is sent via https, and therefore encrypted. You can also rotate the keys used for access to further upgrade the security. 
