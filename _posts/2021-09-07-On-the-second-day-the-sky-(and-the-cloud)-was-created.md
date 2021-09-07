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

Det finns de som tror att himlen skapades på den andra dagen. 
Idag är min andra dag på mitt andra år på vägen mot att bli .NET-utvecklare. 
Den här dagen kommer allt att handla om himlen. Eller iallafall molnen på himlen och vad som finns (och inte finns) i dem. 

### Vad är molnet?

Molnet är, enkelt förklarat, datorkraft som levereras online. 

Beroende lite på vilken molntjänst man har kan molnet leverera allt ifrån hårdvara (till exempel lagring) till en hel tjänst online (till exempel Office 365). Molntjänsterna delas in i tre kategorier;

- *IaaS* - Infrastructure as a Service: Servrar, lagringsutrymme och nätverksfunktioner
- *Paas* - Platform as a Service: IaaS + operativsystem och ofta databashantering
- *SaaS* - Software as a Service: PaaS + mjukvara

Exempel: Jag har utvecklat en app jag behöver ha någonstans. Då köper jag *PaaS* hos Azure för att jag ska få ha min applikation hos dem. Sedan säljer jag licenser med inloggning till mina vänner för att de ska kunna använda min app online. De köper då *SaaS* av mig!

Det finns också flera olika sorters moln beroende på vad man som köpare har för behov och vem man vill nå. 
*Privata moln* är ofta bara tillgängliga för ägaren av molnet eller för en specifik grupp användare. Man kan antingen äga, husera och administrera molnet själv eller använda sig av IaaS (infrastruktur som tjänst) eller PaaS (plattform som tjänst) för att då istället köpa hela eller delar av hårdvarukapaciteten och mjukvaruhanteringen som en tjänst. Privata moln innebär ofta högre uppstartskostnader och företagen får själva stå för inköp och underhåll av såväl hård- som mjukvara och säkerhet. Även om man köper IaaS eller PaaS kan kostnaderna bli högre i och med att man behöver avgränsa tillgången. 

Med *Offentliga moln* betalar köpare/användare bara för kapaciteten de faktiskt utnyttjar. Ett offentligt moln är enkelt att skala upp både horisontellt (fler enheter används i molnet) och vertikalt (högre beräkningskraft i det antal enheter som redan finns) eftersom den som nyttjar molnet inte behöver gå till affären och köpa en fysisk enhet och installera och konfigurera den. 

En tredje sorts moln är ett *Hybridmoln* där man kan kombinera ett privat moln med ett offentligt. Som exempel kan man lagra känslig data i en databas i ett privat moln företaget själva ägen och administrerar och använda mjukvaran som administrerar datan i ett offentligt moln. 


### Vilka fördelar och nackdelar har molnet?

Fördelar:
- Man behöver inte vara fysiskt kopplat emot hårdvaran utan kan komma åt saker från lite varsomhelst även om man äger sitt eget moln
- Om man använder IaaS betalar man inte för mer prestanda än man använder
- Inga uppstartskostnader för inköp av hårdvara eller licenser för t.ex operativsystem eller databaser utan man betalar per tidsenhet man använder tjänsten. 
- Man behöver som företag inte anställa dyr personal med spetskompetens eller köpa dyra konsulttimmar för underhåll
- Man kan utöka eller minska kapacitet blixtsnabbt
- Data och funktioner kan göras permanent tillgängliga - om det blir strömavbrott i en serverhall någonstans finns det fler platser som tar över helt sömlöst
- Det är enkelt att distribuera t.ex en programuppdatering till hela organisationen - det görs i molnet och når alla samtidigt

Nackdelar:
Det man vinner i frihet förloras i kontroll!
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