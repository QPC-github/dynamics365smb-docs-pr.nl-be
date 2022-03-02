---
author: edupont04
ms.service: dynamics365-business-central
ms.topic: include
ms.date: 04/01/2021
ms.author: edupont
ms.openlocfilehash: e75327e1c87af593d8e3f7e4f95e74349fb3a63c
ms.sourcegitcommit: 2c972dfc94d27245eaa99efcf638d030dedafb22
ms.translationtype: HT
ms.contentlocale: nl-BE
ms.lasthandoff: 02/09/2022
ms.locfileid: "8104395"
---
De volgende tabel beschrijft enkele van de belangrijkste rapporten in debiteurenrapportage.

| Rapport | Object-id | Omschrijving |
|--|--|--|
| **Vervallen vorderingen** | 120 | Toont het uitstaande bedrag bij klanten, uitgesplitst in tijdsintervallen voor de achterstallige tijd. Het rapport geeft ook het deel van het saldo van de klant weer dat niet verschuldigd is en kan voor elke klant worden weergegeven met of zonder documentdetails. Dit rapport is het hoofdrapport voor het reconciliëren van het klantengrootboek met het grootboek. Ervan uitgaande dat u directe boekingen niet hebt toegestaan op de rekeningen die worden gebruikt in de debiteurenrekening van de klantenboekingsgroepen, is dit rapport een specificatie van de bedragen die u in het grootboek vindt. |
| **Rekeningoverzicht van klant** | 1316 | Genereert een klantafschrift voor een opgegeven tijdsinterval. Het wordt meestal naar de klanten gestuurd om hen een overzicht te geven van openstaande bedragen en ook als herinnering om achterstallige bedragen te betalen. U kunt ervoor kiezen om de achterstallige bedragen in een aparte rubriek te tonen. U kunt een vervaldatuminterval opnemen dat lijkt op het interval dat wordt gebruikt in het rapport **Vervallen vorderingen**. Voor het vervaldatuminterval stelt u meestal *30D* in, wat betekent dat er intervallen van 30 dagen zijn, zoals 30, 60, 90 en 90+ dagen te laat, vanaf de einddatum, of *1M+CM*, wat de huidige maand in een afzonderlijk interval is en vervolgens maandelijkse intervallen voor de voorgaande maanden. **Opmerking**: in de klantenlijst heeft dit rapport ook een aparte actie **Geplande overzichten**. Deze optie filtert niet op de klant die u hebt geselecteerd. Het is hetzelfde rapport, maar wordt gebruikt wanneer u een overzicht naar alle/meer klanten wilt sturen. |
| **Klant: saldo tot datum** | 121 | Toont de openstaande klantposten tot de einddatum. Dit rapport toont vergelijkbare inhoud als het klantenoverzicht, maar zonder indicatie of de post te laat is. **Opmerking**: het datumfilter wordt toegepast op de gedetailleerde klantenposten. Dit betekent dat als u betalingen heeft die later zijn dan de einddatum die zijn toegepast op facturen binnen het datumbereik, de facturen in het rapport zullen verschijnen omdat ze niet zijn afgesloten op de einddatum. |
| **Klant - Proefbalans** | 129 | Toont de mutaties voor klanten voor de periode die is opgegeven in het datumfilter, evenals de mutatie van jaar tot heden voor het fiscale jaar dat overeenkomt met de geselecteerde periode. Het rapport is gegroepeerd op klantboekingsgroepen en geeft een ander beeld van het klantenboek dan het rapport **Vervallen vorderingen**. **Opmerking**: als u geen boekhoudperiode hebt ingesteld, weet het systeem niet welk fiscaal jaar moet worden gebruikt en toont het ofwel het jaar tot nu toe vanaf het meest recente gedefinieerde fiscale jaar of selecteert u gewoon de periode, die al dan niet vanaf het begin van een jaar loopt.|
| **Klant: Proefbalans Detail** | 104 | Toont alle klantenposten binnen het gespecificeerde datumfilter. Dit rapport wordt over het algemeen gebruikt om te controleren of alle posten voor een specifieke klant zijn verantwoord, of om andere interne controles op klantboeken te controleren. |
| **Klant: betalingsontvangst** | 211 | Creëert een betalingsbewijs voor elke klantenpost van het type **Betaling**. Als de betaling op facturen is toegepast, worden de facturen gespecificeerd; anders wordt het betalingsbedrag alleen als niet toegepast vermeld. Dit rapport wordt gebruikt om naar klanten te sturen die documentatie willen voor de ontvangst van de betaling.|
| **Klant- en leveranciersrekeningen reconciliëren** | 33 |Toont de grootboekposten die voortvloeien uit het boeken van klant- en leveranciersposten, opgesplitst per grootboekrekening en boekingsgroepen. Dit rapport wordt gebruikt voor het reconciliëren van de saldi op klant- en leveranciersgrootboeken met grootboeksaldi. |
| **Klant - Open po&sten (Vast)**| 109 |Dit is een verouderde versie van een rapport over vervallen vorderingen. We raden u aan om in plaats hiervan het rapport **Vervallen vorderingen** te gebruiken. |
| **Verkoopstatistiek** |112  |[!INCLUDE [reports-sales-statistics](reports-sales-statistics.md)]<br>Dit rapport kan ook worden gebruikt in debiteuren, omdat het gemakkelijker is om geboekte betalingen, kortingen en verkopen voor een bepaalde klant snel op te zoeken.|
|**Klantenoverzicht**|101| Bevat allerlei basisgegevens over klanten, zoals de klantboekingsgroepen, kortingsgroepen, toeslag- en betalingsgegevens, verkopers, standaardvaluta's en kredietlimieten van de klanten in uw lokale valuta (LV), alsmede het huidige saldo van elke klant (in LV). Met het rapport kunt u bijvoorbeeld de gegevens in de tabel Klant beheren.|