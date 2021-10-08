---
title: "On the second day the sky (and the cloud) was created"
excerpt_separator: "<!--more-->"
categories:
  - Blog
  - School
tags:
  - .NET
  - Cloud applications
  - The cloud
  - SchoolWork
---
There are people who believe the sky was created on the second day. 
Today is my second day of my second year on the road becoming a .NET-developer.
Today everything will be about the sky. Or at least the clouds in the sky and what's in them (and what's not!). 

### What is the cloud?

The simple way to explain the cloud: Computer power delivered online. 

Depending on what kind of service you purchase, the cloud can provide everything from hardware (for example storage) to a complete application (for example Office 365). The cloud can be divided into three categories:

- *IaaS* - Infrastructure as a Service: Servers, storage space and network services
- *Paas* - Platform as a Service: IaaS + O/S and often database services
- *SaaS* - Software as a Service: PaaS + software

Example: I have developed an app i need to keep somewhere. I buy *Paas* from Azure to store and run my app from them. Then I sell licenses with log in to my friends so they can use my app online. They buy *SaaS* from me! 

There are also several different kinds of clouds depending on what needs I have as a buyer and what reach I want to have. 

*Private clouds* are usually only made available to the owner of the cloud or for a specific group of users. You can either own, house and support the cloud yourselves or use IaaS (infrastructure as a service) or PaaS (platform as a service) to buy all or parts of the hard- and software capacity as a service. Private clouds often means higher cost to start with since the company needs to finance purchase and service of hard- and software and security. Even if they use IaaS or PaaS the cost might be higher because of the need to limit the access. 

With a *Public cloud* the buyer / user only pays for the capacity they actually use. A public cloud easily scales up both horizontally (more units are used in the cloud) and vertically (more computing power in the same amount of units) since the user doesn't actually have to purchase and configure the new hardware. 

A third kind of cloud is the *Hybrid cloud* where you combine a private and a public cloud. For example, you can store sensitive data in a databas in a private cloud which your company own and administrate, and use the software which administrates the data from a public cloud. 


### Which are the pros and cons with the cloud?

Pros:
- You don't need to be physically connected to hardware; you can access your data from anywhere even if you use your private cloud.
- If you use IaaS you don't need to purchase any hardware or upgrades yourself.
- No startup costs for purchasing hardware or licenses (for example O/S or Db) - you pay per time unit you use the service. 
- As a company you don't need to hire staff with expert competence or buy expensive consultant hours for maintenance. 
- Increase or decrease of capacity is fast. 
- Data and resources can be made permanently available - if the power is out in a server area somewhere there are others in other places to take over seamless. 

Cons:
- What you gain in freedom you will lose in control!
- Control over who actually have control over (and what happens with) your data is lost. 
- You cannot be sure to georaphically control your data. 
- You are locked to your service provider's range of service and you have to adapt to it. 
- It might be difficult to predict costs. If the use of data suddenly increases your price tag might increase rapidly. This can depend on increased traffic to your data, or maybe an error in your code which creates some undfortunate and costly loop. 
- Your service provider might in an indirect way make you dependent on third-party solutions without you knowing about it or being able to control it by using other providers themselves. 


### Conclusion comparing prizes

When we started looking for prices to compare from the different cloud providers we quickly realized you need to be _very_ skilled to understand the meaning of the different alternatives. A lot of those who provide cloud services also delivers services from Azure and AWS, and I'm convinced that as a buyer you are willing to pay someone to help specify your needs. Clicking around a bit it became obvious that a lot of money can be spent unnecessarily if you don't know exactly what you are doing. 

We also found good service to be incredibly expensive. A 24/7 service contract can cost more than 1000USD per month for a small, simple server like the one in the assignment spec. And in that case, the cloud storage itself only costs 70USD per month. 

A simple Excel table made it easy to get an overview. Even if all the alternatives are not exactly the same, and maybe we did some strange choices in some places, it's clear the prices for storage is drastically reduced when signing a deal for a longer time. 

![Snip from comparation](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/cloudprices.JPG)

What really surprised me is that keeping your cloud services at a smaller, local provider is not a lot more expensive than at one of the "giants". 