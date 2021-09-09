---
title: "May the fork be with you"
excerpt_separator: "<!--more-->"
categories:
  - Blog
  - School
tags:
  - .NET
  - GitHub
  - GitHubAction
  - CI pipeline
  - YAML
  - Skolarbete
---

### Vad är en CI-pipeline?
För att förklara vad en *CI-pipeline* är behöver man först veta vad *CI* är. 
*CI* står för *Continuous integration* - direktöversatt kontinuerlig integration och betyder att man kontinuerligt pushar sin kod i mindre portioner in i ett större projekt. 
För att det ska fungera att flera utvecklare pushar in i samma projekt ställer det krav på att koden är utan konflikter och testbar. 
Det är här en CI-pipeline kommer in i bilden!

![Bild på  en CI/CD-pipeline](https://www.edureka.co/blog/content/ver.1531719070/uploads/2018/07/What-is-Devops-CI-CD-Pipeline-Edureka.png)
Bild från [DZone](https://dzone.com/articles/learn-how-to-setup-a-cicd-pipeline-from-scratch)

Den vänstra delen av bilden beskriver en CI-pipeline. Bygg- och testdelen av pipelinen triggas automatiskt när till exempel kod pushas eller en pull-request skapas. Om koden av någon anledning inte bygger eller klarar testet larmar funktionen och man kan snabbt hitta och åtgärda problemet direkt istället för att manuellt testa och försöka hitta vart något gått fel i efterhand. En CI-pipeline påminner mycket om ett [PDCA-hjul](https://en.wikipedia.org/wiki/PDCA) (Plan, Do, Check, Act) som från början kommer från fordonsindustrin där det används som ett verktyg för ständiga förbättringar. 

Ett agilt arbetssätt ställer krav på utvecklarna. Alla i teamet måste commita och pusha ofta, annars blir deras kod snabbt inaktuell och då svår att införliva i branchen man arbetar emot. 

Den högra delen av bilden visar CD-delen av pipelinen. *CD* står för *Continuous Deployment* - kontinuerlig distribution eller *Delivery* - leverans, och handlar om vad som händer med koden efter den är byggd, testad och godkänd. Dessa processer kan också automatiseras och därmed snabbas upp och göras betydligt säkrare än vid manuell hantering. 
 

### Hur vi implementerat en CI-pipeline på ett existerande projekt
Vi valde att implementera pipelinen på vårt första SpacePark-projekt. 
Det krävdes väldigt lite anpassning för att fungera med automatiseringen - det enda som behövdes var att ta bort appsettings.json från gitignore-filen. 

### Beskrivning av min YAML-fil

Beskrivande text i grönt på bilden
![Min YAML-fil](https://raw.githubusercontent.com/Baverstrand/Baverstrand.github.io/master/img/yamlexplained.JPG)


__Källor__
- [IDG.se](https://cio.idg.se/2.1782/1.730602/ci-cd-standiga-flodet)
- [Semaphore](https://semaphoreci.com/continuous-integration)
- [Info World](https://www.infoworld.com/article/3271126/what-is-cicd-continuous-integration-and-continuous-delivery-explained.html)