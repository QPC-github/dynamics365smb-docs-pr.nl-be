---
title: artikelposten openen
description: Informatie lezen waarom het voorraadniveau nul is hoewel er open artikelposten bestaan.
author: edupont04
ms.service: dynamics365-financials
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 
ms.date: 11/23/2017
ms.author: edupont
ms.translationtype: HT
ms.sourcegitcommit: b34f276a764f0e828fbc1f015429df9852242a4c
ms.openlocfilehash: 5ca7f39425ebbfa741b464f7421d798ee2d88bbd
ms.contentlocale: nl-be
ms.lasthandoff: 03/22/2018

---
# <a name="design-details-known-item-application-issue"></a>Ontwerpdetails: bekend probleem met artikelvereffening
Dit artikel bespreekt een probleem waarbij het voorraadniveau nul is, hoewel er openstaande artikelposten bestaan [!INCLUDE[d365fin](includes/d365fin_md.md)].  

Het artikel begint met een overzicht van typerende symptomen van het probleem, gevolgd door de basis van artikelvereffening om de beschreven redenen van dit probleem te ondersteunen. Aan het eind van het artikel is een oplossing voor dergelijke openstaande artikelposten.  

## <a name="symptoms-of-the-issue"></a>Symptomen van het probleem  
 Veelvoorkomende symptomen van het probleem met nulvoorraad hoewel er openstaande artikelposten bestaan zijn de volgende:  

-   Het volgende bericht als u een voorraadperiode probeert af te sluiten: "De voorraadperiode kan niet worden afgesloten omdat er negatieve voorraad is voor een of meer artikelen".  

-   Een situatie met een artikelpost waarin zowel een uitgaande artikelpost als de gerelateerde inkomende artikelpost openstaan.  

     Zie het volgende voorbeeld van een situatie met een artikelpost.  

     |Postnr.|Boekingsdatum|Boekingssoort|Documenttype|Documentnr.|Artikelnr.|Vestiging|Aantal|Tot. werk. kosten|Geboekt aantal|Resterend aantal|Openen|  
     |---------|------------|----------|-------------|------------|--------|-------------|--------|------------------------|-----------------|------------------|----|  
     |333|28-01-2018|Verkoop|Verkoopverzending|102043|TEST|BLAUW|-1|-10|-1|-1|Ja|  
     |334|28-01-2018|Verkoop|Verkoopverzending|102043|TEST|BLAUW|1|10|1|1|Ja|  

<!--![Why is inventory zero 1](media/helene/TechArticleInventoryZero1.png "Whyisinventoryzero\_1")-->

## <a name="basics-of-item-application"></a>Grondbeginselen van artikelvereffening  
 Een artikelvereffeningspost wordt gemaakt voor elke voorraadtransactie om de kostenontvanger te koppelen aan de kostenbron, zodat de kosten op basis van de waarderingsmethode kunnen worden doorgestuurd. Zie [Ontwerpdetails: artikelvereffening](design-details-item-application.md) voor meer informatie.  

-   Voor een inkomende artikelpost wordt de artikelvereffeningspost gemaakt als de artikelpost wordt gemaakt.  

-   Voor een uitgaande artikelpost wordt de artikelvereffeningspost gemaakt als de artikelpost wordt geboekt, ALS er een open inkomende artikelpost met beschikbaar aantal is waarmee kan worden vereffend. Als er geen open inkomende artikelpost is waarmee kan worden vereffend, blijft de uitgaande artikelpost open tot een inkomende artikelpost wordt geboekt waarmee kan worden vereffend.  

 Er zijn twee soorten artikelvereffening:  

-   Aantalvereffening  

-   Vereffeningskosten  

### <a name="quantity-application"></a>Aantalvereffening  
 Aantalvereffeningen worden gemaakt voor alle voorraadtransacties en worden automatisch gemaakt of in speciale processen handmatig. Wanneer ze handmatig worden gemaakt, wordt naar aantalvereffeningen verwezen als vaste vereffening.  

 Het volgende diagram toont hoe aantalvereffeningen worden gemaakt.  

![Waarom is voorraad nul 2](media/helene/TechArticleInventoryZero2.png "Whyisinventoryzero\_2")

 Hierboven is artikelpost 1 (Inkoop) zowel de leverancier van het artikel als de kostenbron voor de vereffende artikelpost, artikelpost 2 (Verkoop).  

> [!NOTE]  
>  Als de uitgaande artikelpost op gemiddelde kostprijs wordt gewaardeerd, is de vereffende inkomende artikelpost niet de unieke kostenbron. Het speelt slechts een rol in de berekening van de gemiddelde kosten van de periode.  

### <a name="cost-application"></a>Vereffeningskosten  
Kostenvereffeningen worden alleen gemaakt voor inkomende transacties waarbij het veld **Vereffenen met artikelpost** wordt gevuld om een vaste vereffening te bieden. Dit gebeurt vaak met betrekking tot een verkoopcreditnota of een scenario waarin een verzending wordt teruggedraaid. De kostenvereffening zorgt dat het artikel weer in voorraad komt met dezelfde kosten als waarmee het is verzonden.  

Het volgende diagram toont hoe kostenvereffeningen worden uitgevoerd.  

|Postnr.|Boekingsdatum|Boekingssoort|Documenttype|Documentnr.|Artikelnr.|Vestiging|Aantal|Tot. werk. kosten|Geboekt aantal|Resterend aantal|Openen|  
|---------|------------|----------|-------------|------------|--------|-------------|--------|------------------------|-----------------|------------------|----|  
|333|28-01-2018|Verkoop|Verkoopverzending|102043|TEST|BLAUW|-1|-10|-1|-1|Ja|  
|334|28-01-2018|Verkoop|Verkoopverzending|102043|TEST|BLAUW|1|10|1|1|Ja|  
<!--![Why is inventory zero 3](media/helene/TechArticleInventoryZero3.png "Whyisinventoryzero\_3")-->

 Hierboven is inkomende artikelpost 3 (Verkoopretour) een kostenontvanger voor de oorspronkelijke uitgaande artikelpost 2 (Verkoop).  

## <a name="illustration-of-a-basic-cost-flow"></a>Illustratie van een basiskostenstroom  
 Stel een complete kostenstroom waarin een artikel wordt ontvangen, verzonden en gefactureerd met exacte kostentegenboeking, en opnieuw wordt verzonden.  

 Het volgende diagram illustreert de kostenstroom.  

![Waarom is voorraad nul 4](media/helene/TechArticleInventoryZero4.png "Whyisinventoryzero\_4")

 Hierboven worden de kosten doorgestuurd naar artikelpost 2 (Verkoop), vervolgens naar artikelpost 3 (Verkoopretour) en uiteindelijk naar artikelpost 4 (Verkoop 2).  

## <a name="reasons-for-the-issue"></a>Redenen voor het probleem  
 Het probleem met nulvoorraad hoewel er openstaande artikelposten bestaan kan worden veroorzaakt door de volgende scenario's:  

-   Scenario 1: Een verzending en een factuur worden geboekt hoewel het artikel niet beschikbaar is. Het boeken wordt vervolgens exact tegengeboekt met een verkoopcreditnota.  

-   Scenario 2: Een verzending wordt geboekt hoewel het artikel niet beschikbaar is. De boeking wordt vervolgens ongedaan gemaakt met de functie Verzending ongedaan maken.  

 Het volgende diagram illustreert hoe artikelvereffeningen in beide scenario's worden uitgevoerd.  

![Waarom is voorraad nul 6](media/helene/TechArticleInventoryZero6.png "Whyisinventoryzero\_6")  

 Er wordt een kostenvereffening gemaakt (vertegenwoordigd door de blauwe pijlen) om te zorgen dat artikelpost 2 (Verkoopretour) dezelfde kosten toegewezen krijgt als de artikelpost die ermee wordt tegengeboekt, artikelpost 1 (Verkoop 1). Echter, een aantalvereffening (vertegenwoordigd door de rode pijlen) wordt niet uitgevoerd.  

 Artikelpost 2 (Verkoopretour) kan niet zowel een kostenontvanger van de oorspronkelijke artikelpost zijn als tegelijkertijd een leverancier van artikelen en de kostenbron ervan. Daarom blijft oorspronkelijke artikelpost 1 (Verkoop 1) open totdat een geldige bron verschijnt.  

## <a name="identifying-the-issue"></a>Het probleem identificeren  
 Als u wilt weten of de open artikelposten worden gemaakt, doet u het volgende voor het respectievelijke scenario:  

 Voor scenario 1 identificeert u het probleem als volgt:  

-   Voer in het venster **Geboekte verkoopcreditnota** of **Geboekte retourontvangst** een opzoekactie uit vanuit het veld **Vereffenen met artikelpost** om te zien of het veld wordt ingevuld, en in dat geval met welke artikelpost de retourontvangst wordt kostenvereffend.  

 Voor scenario 2 identificeert u het probleem op een van de volgende manieren:  

-   Zoek een openstaande uitgaande artikelpost en een inkomende artikelpost met hetzelfde nummer in het veld **Documentnr.** en met Ja in het veld **Storno**. Zie het volgende voorbeeld van een dergelijke situatie met een artikelpost.  

|Postnr.|Boekingsdatum|Boekingssoort|Documenttype|Documentnr.|Artikelnr.|Vestiging|Aantal|Tot. werk. kosten|Geboekt aantal|Resterend aantal|Openen|Storno|  
|---------|------------|----------|-------------|------------|--------|-------------|--------|------------------------|-----------------|------------------|----|---------|
|333|28-01-2018|Verkoop|Verkoopverzending|102043|TEST|BLAUW|-1|-10|-1|-1|Ja|Nr.|  
|334|28-01-2018|Verkoop|Verkoopverzending|102043|TEST|BLAUW|1|10|1|1|Ja|**Ja**|  
<!--![Why is inventory zero 7](media/helene/TechArticleInventoryZero7.png "Whyisinventoryzero\_7")-->

-   Voer in het venster **Geboekte verkoopverzending** een opzoekactie uit vanuit het veld **Vereffenen met artikelpost** om te zien of het veld gevuld is en in dat geval met welke artikelpost de retourontvangst wordt kostenvereffend.  

> [!NOTE]  
>  Kostenvereffeningen kunnen niet worden geïdentificeerd in het venster **Vereffende artikelposten** omdat dat venster alleen aantalvereffeningen weergeeft.  

 Voor beide scenario's identificeert u de betrokken kostenvereffening als volgt:  

1.  Open de tabel **Artikelvereffeningspost**.  

2.  Filter op het veld **Artikelpostnr.** met het nummer van de Verkoopretourartikelpost.  

3.  Analyseer de artikelvereffeningspost en let op het volgende:  

     Als het veld **Uitgaand art.-postnr.** voor een inkomende artikelpost (positief aantal) wordt ingevuld, dan is de inkomende artikelpost de kostenontvanger van de uitgaande artikelpost.  

     Zie het volgende voorbeeld van een situatie met een artikelvereffeningspost.  

     |Postnr.|Artikelpostnr.|Inkomend art.-postnr.|Uitgaand art.-postnr.|Aantal|Boekingsdatum|Vereffeningskosten|  
     |---------|---------------------|----------------------|-----------------------|--------|------------|----------------|  
     |299|334|334|333|1|28-01-2018|Ja|  
<!--![Why is inventory zero 8](media/helene/TechArticleInventoryZero8.png "Whyisinventoryzero\_8")  -->

 Hierboven wordt inkomende artikelpost 334 kostenvereffend met uitgaande artikelpost 333.  

## <a name="workaround-for-the-issue"></a>Oplossing voor het probleem  
 Boek in het venster **Artikeldagboek** de volgende regels voor het betreffende artikel:  

-   Een positieve correctie om de openstaande uitgaande artikelpost te sluiten.  

-   Een negatieve correctie met hetzelfde aantal.  

     Deze aanpassing brengt de positieve voorraadmutatie in evenwicht die wordt veroorzaakt door de positieve correctie en wordt de open inkomende artikelpost gesloten.  

 Het resultaat is dat de voorraad nul is en alle artikelposten worden afgesloten.  

## <a name="see-also"></a>Zie ook  
[Ontwerpdetails: Artikelvereffening](design-details-item-application.md)   
[Ontwerpdetails: Voorraadwaardering](design-details-inventory-costing.md)  
