---
title: Automatische overdracht en gecombineerde posten | Microsoft Docs
description: In kostprijsboekhouding kunt u grootboekposten overbrengen naar een kostensoort door middel van een gecombineerde boeking. U kunt opgeven of een kostensoort gecombineerde posten ontvangt in het veld **Posten combineren** in de definitie van het kostensoort. De volgende tabel beschrijft de verschillende opties.
services: project-madeira
documentationcenter: 
author: SorenGP
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 
ms.date: 07/01/2017
ms.author: sgroespe
ms.translationtype: HT
ms.sourcegitcommit: d7fb34e1c9428a64c71ff47be8bcff174649c00d
ms.openlocfilehash: 4f1bcf009b397438bb302a16a23be2f4638cefc4
ms.contentlocale: nl-be
ms.lasthandoff: 03/22/2018

---
# <a name="automatic-transfer-and-combined-entries"></a>Automatische overdracht en gecombineerde posten
In kostprijsboekhouding kunt u grootboekposten overbrengen naar een kostensoort door middel van een gecombineerde boeking. U kunt opgeven of een kostensoort gecombineerde posten ontvangt in het veld **Posten combineren** in de definitie van het kostensoort. De volgende tabel beschrijft de verschillende opties.  

|Posten combineren|Omschrijving|  
|---------------------|-----------------|  
|Geen|Elke grootboekpost wordt afzonderlijk overgebracht naar het bijbehorende kostensoort.|  
|Dag|Grootboekposten met dezelfde boekingsdatum worden als één post overgeboekt naar de bijbehorende kostensoort.|  
|Maand|Alle grootboekposten in dezelfde kalendermaand worden als één post overgeboekt naar de bijbehorende kostensoort.|  

> [!IMPORTANT]  
>  Als u het selectievakje **Automatisch overdragen van GB** in het venster **Instelling kostprijsboekhouding** hebt ingeschakeld, wordt de kostprijsboekhouding automatisch bijgewerkt in [!INCLUDE[d365fin](includes/d365fin_md.md)] na elke boeking in het grootboek. Gecombineerde posten zijn niet mogelijk.  

## <a name="see-also"></a>Zie ook  
 [Grootboekposten overbrengen naar kostenposten](finance-how-to-transfer-general-ledger-entries-to-cost-entries.md)   
 [Criteria voor het overbrengen van grootboekposten naar kostenposten.](finance-criteria-for-transferring-general-ledger-entries-to-cost-entries.md)   
 [Resultaten van de overboeking](finance-results-of-the-transfer.md)   
 [Kostenposten overbrengen en boeken](finance-transfer-and-post-cost-entries.md)  
 [Werken met [!INCLUDE[d365fin](includes/d365fin_md.md)]](ui-work-product.md)
