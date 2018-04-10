---
title: Betalingsbestanden afdrukken
description: Als u een testrapport hebt afgedrukt en alle fouten hebt gecorrigeerd, kunt u betalingsdagboekregels naar een betalingsbestand afdrukken.
services: project-madeira
documentationcenter: 
author: SorenGP
ms.service: dynamics365-financials
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: 
ms.date: 07/01/2017
ms.author: sgroespe
ms.translationtype: HT
ms.sourcegitcommit: b34f276a764f0e828fbc1f015429df9852242a4c
ms.openlocfilehash: a7305fe72c7bbc35b8e164f12e3fe341b489d80c
ms.contentlocale: nl-be
ms.lasthandoff: 03/22/2018

---
# <a name="print-payment-files"></a>Betalingsbestanden afdrukken
Als u een testrapport hebt afgedrukt en alle fouten hebt gecorrigeerd, kunt u betalingsdagboekregels naar een betalingsbestand afdrukken.  

Een betalingsbestand bevat binnenlandse, internationale of SEPA-betalingen (in euro's of in een andere valuta). Het bestand kan per schijf of via een modem of Isabel (Interbanks Standards Association Belgium) worden verzonden. U kunt slechts één bestand per boekingsdatum en valutacode maken. Wanneer u de betalingen naar een bestand exporteert, wordt er een bijbehorende notitie afgedrukt die ook naar de bank kan worden verzonden.  

In het betalingsdagboek wordt het veld **Status** op de geëxporteerde regels ingesteld op **Geboekt**.  

## <a name="to-print-a-payment-file"></a>Een betalingsbestand afdrukken  

1.  Klik op het pictogram ![Zoeken naar pagina of rapport](../../media/ui-search/search_small.png "pictogram Zoeken naar pagina of rapport"), voer **Betalingsdagboek** in en klik vervolgens op de gerelateerde koppeling.  
2.  Vul op het sneltabblad **Opties** de velden in zoals in de volgende tabel wordt beschreven.  

    |Veld|Description|  
    |---------------------------------|---------------------------------------|  
    |**Batchnaam**|Geef de batchnaam van het betalingsdagboek op.|  
    |**Bankrekening**|Geef de bankrekening van het betalingsdagboek op.|  
    |**Exportprotocol**|Geef de exportprotocolcode van de betalingsdagboekregel op. Exportprotocollen bepalen welk betalingsbestand in het betalingsdagboek wordt gegenereerd.<br /><br /> U kunt een combinatie van exportindelingen in één batch hebben, bijvoorbeeld binnenlandse, internationale en SEPA-betalingen. Wanneer u de betalingsregels naar een bestand exporteert, kunt u echter slechts één exportindeling, of exportprotocol, gebruiken. **Opmerking:** door het exportprotocol op te geven, geeft u ook het validatietype op dat wordt uitgevoerd in het betalingsdagboek.|  

3.  Kies de actie **Betalingsregels controleren**.

    Het venster **Logboeken voor controlefouten exporteren** bevat eventuele fouten die kunnen bestaan. Als er fouten zijn, moet u deze oplossen voordat u verder kunt gaan.

4. Als er geen fouten zijn, kiest u de actie **Betalingsregels exporteren**.  

    Vervolgens wordt het rapport geopend dat u in het veld **Testrapport-id** in **Betalingsdagboeksjablonen** hebt opgegeven.  

5.  Klik op **Afdrukken**.  

## <a name="see-also"></a>Zie ook  
 [Elektronisch bankieren voor België](belgian-electronic-banking.md)   
 [Belgische elektronische betalingen](belgian-electronic-payments.md)   
 [Elektronisch bankieren instellen](how-to-set-up-electronic-banking.md)   
 [IBLC-BLWI-transactiecodes instellen](how-to-set-up-iblc-blwi-transaction-codes.md)   
 [Leveranciers voor automatische betalingsvoorstellen instellen](how-to-set-up-vendors-for-automatic-payment-suggestions.md)   
 [Betalingsvoorstellen genereren](how-to-generate-payment-suggestions.md)   
 [Betalingsdagboeksjablonen en -batches maken](how-to-create-payment-journal-templates-and-batches.md)   
 [Elektronische betalingen testen](how-to-test-electronic-payments.md)   
 [Regels voor elektronische betalingen beheren](how-to-manage-electronic-payment-lines.md)
