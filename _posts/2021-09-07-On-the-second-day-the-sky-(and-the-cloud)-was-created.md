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

A third kind of cloud is the *Hybrid cloud* where you combine a private and a public cloud. 
En tredje sorts moln är ett *Hybridmoln* där man kan kombinera ett privat moln med ett offentligt. Som exempel kan man lagra känslig data i en databas i ett privat moln företaget själva äger och administrerar och sedan använda mjukvaran som administrerar datan i ett offentligt moln. 


### Vilka fördelar och nackdelar har molnet?

Fördelar:
- Man behöver inte vara fysiskt kopplad emot hårdvaran utan kan komma åt saker från lite varsomhelst även om man äger sitt eget moln
- Om man använder IaaS står man inte för kostnaden för hårdvara och uppgradering själv
- Inga uppstartskostnader för inköp av hårdvara eller licenser för t.ex operativsystem eller databaser utan man betalar per tidsenhet man använder tjänsten. 
- Man behöver som företag inte anställa dyr personal med spetskompetens eller köpa dyra konsulttimmar för underhåll
- Man kan utöka eller minska kapacitet blixtsnabbt
- Data och funktioner kan göras permanent tillgängliga - om det blir strömavbrott i en serverhall någonstans finns det fler platser som tar över helt sömlöst

Nackdelar:
- Det man vinner i frihet förloras i kontroll!
- Man har begränsad kontroll över vem som egentligen kontrollerar (och vad som händer med) ens egen data
- Det är inte självklart att man geografiskt kan kontrollera sin data
- Man blir låst vid tjänsteleverantörens utbud och tvingas anpassa sig till det
- Det kan vara svårt att förutsäga kostnader, om dataanvändningen plötsligt ökar kan prislappen växa fort. Detta kan bero på både ökad trafik till din data eller att något fel i koden plötsligt kräver mycket mer kapacitet
- Man kan göras beroende av tredjepartslösningar utan att veta om det eller kunna kontrollera detta själv om till exempel tjänsteleverantören i sin tur köper tjänster av någon annan. 


### Slutsats kring prisjämförelse

När vi började leta priser att jämföra hos de olika molnleverantörerna insåg vi snabbt att man nog behöver vara _mycket_ insatt för att överhuvudtaget förstå vad de olika alternativen innebär. Många som tillhandahåller molntjänster är företag som i sin tur levererar tjänster från Azure och AWS, och jag kan tänka mig att man som köpare är beredd att belata någon för att specificera sitt eget behov. När vi klickade runt litegrann blev det väldigt tydligt att det snabbt kan kosta väldigt mycket pengar i onödan om man inte vet exakt vad man behöver och vilja tjänster man har nytta av. 

Det blev också tydligt att bra service kostar otroligt mycket pengar. Ett 24/7-avtal kan kosta över 1000 USD/månad bara för en enkel liten server enligt specen i uppgiften. Och då kostar själva molnlagringen kanske 70 USD/månad. 

Vi gjorde en enkel uppställning i Excel för att få en överblick. Även om inte alla alternativ är likvärdiga och att vi kanske gjort lite konstiga val på en del ställen blev det snabbt tydligt att priserna för själva lagringen sjönk drastiskt när man valde att binda upp sig över längre tid. 

![Klipp från jämförelsen](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/cloudprices.JPG)

Vad som förvånade mig är att det inte var speciellt mycket dyrare att ha molntjänsterna hos en mindre leverantör lokalt än hos någon av "jättarna".