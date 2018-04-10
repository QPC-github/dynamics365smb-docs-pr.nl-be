---
title: 'Procedure: een offerte maken voor een op-order-assembleren-verkoop | Microsoft Docs'
description: U kunt assemblagebeheer gebruiken om een assemblageartikel op verzoek van een klant aan te passen tijdens het verkoopproces.
services: project-madeira
documentationcenter: 
author: SorenGP
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 
ms.date: 08/15/2017
ms.author: sgroespe
ms.translationtype: HT
ms.sourcegitcommit: d7fb34e1c9428a64c71ff47be8bcff174649c00d
ms.openlocfilehash: 402745a9c90d1b82779e436f4a6533d2aed1b344
ms.contentlocale: nl-be
ms.lasthandoff: 03/22/2018

---
# <a name="quote-an-assemble-to-order-sale"></a>Een offerte maken voor een assembleren voor order-verkoop
U kunt assemblagebeheer gebruiken om een assemblageartikel op verzoek van een klant aan te passen tijdens het verkoopproces. Zie voor meer informatie [Op order geassembleerde artikelen verkopen](assembly-how-to-sell-items-assembled-to-order.md).  

Als u een ander soort artikel verkoopt, kunt u ook een verkoopofferte maken voor een aangepast assemblageartikel voordat u deze omzet in een verkooporder. Dit proces omvat verschillende extra stappen wanneer u het vergelijkt met het maken van een normale verkoopofferte, en gebruikt assemblageoffertes, een variatie van een gekoppelde assemblageorder.

> [!NOTE]  
>  Zoals alle soorten van offertes worden de aantallen op assemblageoffertes niet gebruikt in beschikbaarheid, plannen of reserveringen.  

## <a name="to-create-a-sales-quote-for-an-assemble-to-order-item"></a>Een verkoopofferte voor een op-order-assembleren-artikel maken  
1.  Klik op het pictogram ![Zoeken naar pagina of rapport](media/ui-search/search_small.png "pictogram Zoeken naar pagina of rapport"), voer **Verkoopofferte** in en klik vervolgens op de gerelateerde koppeling.  
2.  Maak een nieuwe verkoopofferteregel met één regel voor een assemblageartikel. Zie voor meer informatie [Aanbiedingen doen](sales-how-make-offers.md).  
3.  Voer de volledige aantal het in veld **Aantal voor op order assembleren** in.

    > [!NOTE]  
    >  U moet geen offerte maken voor een gedeeltelijke hoeveelheid. Daarom moet u dezelfde hoeveelheid invoeren die u hebt ingevoerd in het veld **Hoeveelheid** op de verkoopofferteregel.  

4.  Kies op het sneltabblad **Regels** de optie **Regel** en vervolgens **Op order assembleren** en **Op orderregels assembleren**. Of kies het veld **Aant. op order assembleren** op de regel.  
5.  Bekijk of wijzig de assemblageorderregels volgens de offerte die de klant heeft aangevraagd in het venster **Op orderregels assembleren**. Als u meer informatie wilt, kiest u de actie **Document weergeven** om het volledige offerteraamcontract te openen. U kunt de inhoud van de meeste velden niet wijzigen en u kunt niet boeken.  
6.  Wanneer u de assemblageorderregels hebt bijgewerkt volgens de offerte sluit u het venster **Op orderregels assembleren** om terug te keren naar het venster **Verkoopofferte**.  
7.  Als de klant de offerte heeft geaccepteerd, maakt u een verkooporder voor het genoteerde assemblageartikel. Zie voor meer informatie [Aanbiedingen doen](sales-how-make-offers.md). De gekoppelde assemblageofferte en eventuele aanpassingen zijn gekoppeld aan die nieuwe verkooporder, als voorbereiding op de assemblage van het artikel of de artikelen die verkocht worden.  

## <a name="see-also"></a>Zie ook  
[Assemblagebeheer](assembly-assemble-items.md)  
[Werken met stuklijsten](inventory-how-work-BOMs.md)  
[Voorraad](inventory-manage-inventory.md)  
[Ontwerpdetails: Magazijnbeheer](design-details-warehouse-management.md)  
[Werken met [!INCLUDE[d365fin](includes/d365fin_md.md)]](ui-work-product.md)
