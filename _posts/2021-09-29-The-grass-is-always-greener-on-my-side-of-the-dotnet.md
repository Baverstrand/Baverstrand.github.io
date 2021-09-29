---
title: "The grass is always greener on my side of the .NET"
excerpt_separator: "<!--more-->"
categories:
  - Blog
  - School
tags:
  - .NET
  - Azure
  - PaaS
  - Private cloud
  - Argumentative
  - School Work
---

## Why Azure is the best thing since sliced bread

### Dear CTO

It has come to my knowledge you are the head of taking our department into the future. 
I have also come to understand you are highly reluctant to make use of all the possibilities with the cloud. 

Please allow me a few minutes of your time and I will do my best to paint you a clear picture of how I think we can make the most of our business!

#### Today

At the moment our application runs on (to be honest) old hardware with outdated software in the basement. And due to the security restrictions regarding some of the data it's difficult to have and effective way of working. I know it's usually a bad idea to fix something that isn't broken, but what will happen when things actually starts to break down? Or if we want to expand our business abroad? Or if our office suffers from a power out? 
To modernize both hard- and software as well as making this system redundant in a safe way will cost a *lot* of money. Even if we do not take the full step over to the cloud in this round, I have a suggestion that when we do, will cost our business less money upfront, be instantly scalable, completely redundant and just as safe as keeping our servers in house. 

#### The future

Let me introduce you to [Azure](https://azure.microsoft.com/). They provide all the service we would need to stay updated, be able to quickly expand both in terms of customer base and geographically and keep our systems redundant but still maintain full security regarding our protected data in the future. 
For now, since our business is not ready to take the big step just yet, I have a smaller change to begin with. As we have agreed, an enterprise bus is the way to go for us, I would like to suggest Azure's service *Azure Service Bus* for this. My simple drawing below illustrates how we, in a completely safe way, can communicate with our Service Bus without exposing any restricted data. 

![Layout](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/210929layout.jpg)

Since I you are one of my most dedicated followers I know you have read [my very first post in this blog](https://baverstrand.github.io/blog/school/On-the-second-day-the-sky-(and-the-cloud)-was-created/#what-is-the-cloud) about the Cloud - what kinds of clouds there are and what services to be found in them. Therefore I'm sure you are familiar with both private clouds and PaaS (which I will mention further on). 

My suggestion is that we, for now, keep both our application and our restricted data as is in our private cloud and use the Service Bus remote. Since the Service Bus handles pretty small amounts of data, and we can choose storage location for it ourselves, the distanse will not be an issue. There are three pillars in this solution: *Azure Virtual Network (VNet)*, *Private Link* and *Private Endpoint* (PE in my drawing). Let me explain in short:

- *VNet* is almost the same as our own private network - but online. The  big bonuses with VNet is that it's scalable, has a high availability and is isolated. You can choose who has access to what. VNet also gives us the option to use more of Azure's PaaS services. 
- *Private Link* is the link that makes it possible to securely access the Service Bus over the private endpoint. Data travels over Microsoft network, and our service will never be available to or visible on public internet. 
- *Private Endpoint* is the private interface (kind of the door with a big lock on it) to the service using Private Link for access. 

#### Even further into the future

A Virtual Private Cloud (VPC) is a private cloud put into a public cloud, but with limited access. We will maintain the control and management of security, but we will be able to use PaaS and all its benefits. With a VPC we could put both our application and our data in the cloud which would give us a lot less vulnerable application in terms of up-time and redundancy. A solution like this would also significantly lower our hardware costs. 

<!-- 
Ni jobbar i ett företag som har en intern applikation som ni gärna vill modernisera, denna interna applikation använder tillgång till interna server och resurser, och jobbar med klassificerade data som inte får öppet skickas via nätat, och därför är det i följa din CTO inte möjligt att använda en PaaS moln-lösning.

Ett viktigt punkt i modernisering är att implementera en enterprise bus, och ni vill gärna använda er av Azure Service Bus, men tyvär säger eran CTO säger “nej”, på grund av data inte får skickas öppet.

Skriv (i eran blogg) ett argument till eran CTO som förklara och övertyga hen om att ni med hjälp av ett Azure Private Link kan använda Azure Service Bus i eran interna applikation. Förklara begrepp som Virtual Private Cloud i eran förklaring.

Om ni lyckas att övertyga eran CTO till att tillåta att ni använder Azure Service Bus, kommer ni i framtiden att kunna använda andra Azure PaaS tjänster (vilket gör livet som utvecklare mycket bättre) :-)


App Service
CosmosDB
[What is Azure Virtual Network?](https://docs.microsoft.com/en-us/azure/virtual-network/virtual-networks-overview)
[What is Azure Private Link?](https://docs.microsoft.com/en-us/azure/private-link/private-link-overview)
[Azure Private Link availability](https://docs.microsoft.com/en-us/azure/private-link/availability)
[What is Azure Private Link service?](https://docs.microsoft.com/en-us/azure/private-link/private-link-service-overview)
[What is Azure Private Endpoint?](https://docs.microsoft.com/en-us/azure/private-link/private-endpoint-overview)
 -->
