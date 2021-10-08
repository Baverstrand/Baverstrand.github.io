---
title: "Scaling can be fishy business"
excerpt_separator: "<!--more-->"
categories:
  - Blog
  - School
tags:
  - .NET
  - Azure Function
  - Loader.io
  - Logging
  - SchoolWork
---
### Scaling  
### Vertical vs. Horizontal

You could compare scaling with hiring new staff. It all depends on your business and on your needs. If you work with assembling really advanced and expensive wristwatches you need top notch, highly qualified people to make good money. If you, on the other hand, work with assembling alarm clocks where the assembly staff connects a display with a small chip and put it all in a plastic shell with three screws, number of workers is the key to the money.  
Scaling up vertically is like rising your competence level. You add computing power to your existing hardware. This is the alternative if you need to handle complicated or very big requests but not neccessarily large numbers of requests.  
Scaling out horizontally on the other hand is adding more of the same. If you handle high numbers of smaller requests you might want a lot of smaller units doing their job quickly instead of one, big mastermind. 

### How is the cost affected when scaling vertically vs. horizontally?
#### For an app service  

Comparing cost when scaling up vs out is a bit difficult since scaling up is not as easy as mergeing two servers next to eachother to double the computing power. There is a huge amount of choices to be made in terms of processors, RAM, storage and such. This chart is for Basic tier where I've compared 1 core (1,75 GB RAM) and 4 cores(7 GB RAM) instances.

![App Service cost compare](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/211008horiapp.jpg)

Keeping within the same tier you basically have a linear cost increase and pay per core and RAM. 25 instances of 4 cores cost just as much as 100 instances of 1 core, and 250 instances will cost 10 times as much as 25.

#### For virtual machines

Comparing VMs shows just about the same. I am not familiar with the different options, but I have tried to find comparable ones. 

![App Service cost compare](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/211008horivm.jpg)

Here you can also see the cost increases are linear between the total amount of cores. You do not get a discount for amount of instances here either, 100 instances cost 10 times as much as 10!

### Which Azure Apps Services are scalable? How?

Azure App Services is scalable up and down both within its tier (cores, RAM and storage per instance) from Basic tier and up, and changing tier.  
Scaling out is only possible from the Basic tier and up - from three instances using Basic to 100 with the Isolated tier. 

### Resources

- [Opsani](https://opsani.com/blog/scale-up-vs-scale-out-whats-the-difference/)
- [Azure pricing calculator](https://azure.microsoft.com/en-us/pricing/calculator/)
- [App Service pricing](https://azure.microsoft.com/en-us/pricing/details/app-service/windows/)
- [App Service limits](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/azure-subscription-service-limits#app-service-limits)
- [Canva](https://www.canva.com/)