---
title: "På den andra dagen skapades himlen (och molnet)"
excerpt_separator: "<!--more-->"
categories:
  - Blog
  - School
tags:
  - .NET
  - Molnapplikationer
  - Molnet
  - Skolarbete
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

När vi började leta priser att jämföra hos de olika molnleverantörerna insåg vi snabbt att man nog behöver vara _mycket_ insatt för att överhuvudtaget förstå vad de olika alternativen innebär. Många som tillhandahåller molntjänster är företag som i sin tur levererar tjänster från Azure och AWS, och jag kan tänka mig att man som köpare är beredd att belata någon för att specificera sitt eget behov. När vi klickade runt litegrann blev det väldigt tydligt att det snabbt kan kosta väldigt mycket pengar i onödan om man inte vet exakt vad man behöver och vilja tjänster man har nytta av. 

Det blev också tydligt att bra service kostar otroligt mycket pengar. Ett 24/7-avtal kan kosta över 1000 USD/månad bara för en enkel liten server enligt specen i uppgiften. Och då kostar själva molnlagringen kanske 70 USD/månad. 

Vi gjorde en enkel uppställning i Excel för att få en överblick. Även om inte alla alternativ är likvärdiga och att vi kanske gjort lite konstiga val på en del ställen blev det snabbt tydligt att priserna för själva lagringen sjönk drastiskt när man valde att binda upp sig över längre tid. 

![Klipp från jämförelsen](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/cloudprices.JPG)

Vad som förvånade mig är att det inte var speciellt mycket dyrare att ha molntjänsterna hos en mindre leverantör lokalt än hos någon av "jättarna".