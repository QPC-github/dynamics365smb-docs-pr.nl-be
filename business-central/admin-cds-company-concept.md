---
title: Toewijzing van bedrijf en bedrijfsunit | Microsoft Docs
description: Bedrijven zijn zowel juridische als zakelijke constructies en worden gebruikt om bedrijfsgegevens te beveiligen en te visualiseren.
author: bholtorf
ms.service: dynamics365-business-central
ms.topic: article
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: CDS, Common Data Service, integration, sync
ms.date: 01/17/2020
ms.author: bholtorf
ms.openlocfilehash: 795656cd5b4ad8d40c48a2edf327cffb56ad6906
ms.sourcegitcommit: 7d54d8abe52e0546378cf760f5082f46e8441b90
ms.translationtype: HT
ms.contentlocale: nl-BE
ms.lasthandoff: 04/30/2020
ms.locfileid: "3324066"
---
# <a name="data-ownership-models"></a>Modellen voor gegevenseigendom
[!INCLUDE[d365fin](includes/cds_long_md.md)] vereist dat u een eigenaar opgeeft voor de gegevens die u opslaat. Zie voor meer informatie [Entiteiteigendom](https://docs.microsoft.com/powerapps/maker/common-data-service/types-of-entities#entity-ownership) in de Power Apps-documentatie. Wanneer u integratie instelt tussen [!INCLUDE[d365fin](includes/cds_long_md.md)] en [!INCLUDE[d365fin](includes/d365fin_md.md)] , moet u een van de twee eigendomsmodellen kiezen voor records die worden gesynchroniseerd:

* Team 
* Persoon (gebruiker)

Acties die op deze records kunnen worden uitgevoerd, kunnen op gebruikersniveau worden beheerd. Zie voor meer informatie [Gebruikers- en teamentiteiten](https://docs.microsoft.com/powerapps/developer/common-data-service/user-team-entities). We raden het teameigendomsmodel aan, omdat het beheer van eigendom voor meerdere mensen gemakkelijker maakt.

## <a name="team-ownership"></a>Teameigendom
In [!INCLUDE[d365fin](includes/d365fin_md.md)] is een bedrijf een juridische en zakelijke entiteit die manieren biedt om bedrijfsgegevens te beveiligen en te visualiseren. Gebruikers werken altijd in de context van een bedrijf. [!INCLUDE[d365fin](includes/cds_long_md.md)] komt hier het dichtst bij in de buurt met de entiteit bedrijfsunit, die geen juridische of zakelijke implicaties heeft.

Omdat bedrijfsunits juridische en zakelijke implicaties missen, kunt u geen één-op-één (1: 1) toewijzing afdwingen om gegevens tussen een bedrijf en een bedrijfsunit te synchroniseren, hetzij eenrichting, hetzij bidirectioneel. Om synchronisatie mogelijk te maken wanneer u synchronisatie voor een bedrijf inschakelt [!INCLUDE[d365fin](includes/d365fin_md.md)], gebeurt het volgende in [!INCLUDE[d365fin](includes/cds_long_md.md)]:

* We creëren een bedrijfsentiteit die gelijk is aan de bedrijfsentiteit in [!INCLUDE[d365fin](includes/d365fin_md.md)]. De naam van het bedrijf krijgt het achtervoegsel "BC-bedrijfs-ID". Bijvoorbeeld Cronus International Ltd. (93555b1a-af3e-ea11-bb35-000d3a492db1).
* We creëren een standaardbedrijfseenheid met dezelfde naam als het bedrijf. Bijvoorbeeld Cronus International Ltd. (93555b1a-af3e-ea11-bb35-000d3a492db1).
* We creëren een apart eigenaarsteam met dezelfde naam als het bedrijf en associëren het met de bedrijfsunit. De naam van het team krijgt het prefix "BCI -". Bijvoorbeeld BCI - Cronus International Ltd. (93555b1a-af3e-ea11-bb35-000d3a492db1).
* Records die zijn gemaakt en gesynchroniseerd met [!INCLUDE[d365fin](includes/cds_long_md.md)], worden toegewezen aan het team "BCI-eigenaar" dat is gekoppeld aan de bedrijfsunit.

> [!NOTE]
> Als u een bedrijf een andere naam geeft in [!INCLUDE[d365fin](includes/d365fin_md.md)], worden de namen van het bedrijf, de bedrijfsunit en het team die we automatisch maken in [!INCLUDE[d365fin](includes/cds_long_md.md)], niet bijgewerkt. Omdat alleen de bedrijfs-id wordt gebruikt voor integratie, heeft dit geen invloed op synchronisatie. Als u wilt dat de namen overeenkomen, moet u het bedrijf, de bedrijfsunit en het team bijwerken [!INCLUDE[d365fin](includes/cds_long_md.md)].

De volgende afbeelding toont een voorbeeld van deze gegevensconfiguratie in [!INCLUDE[d365fin](includes/cds_long_md.md)].

![De hoofdbedrijfsunit staat bovenaan, de teams staan in het midden en de bedrijven staan onderaan.](media/cds_bu_team_company.png)

In deze configuratie zijn records die gerelateerd zijn aan het Cronus US-bedrijf eigendom van een team dat is gekoppeld aan de Cronus US <ID> bedrijfseenheid in [!INCLUDE[d365fin](includes/cds_long_md.md)]. Gebruikers die toegang hebben tot die bedrijfseenheid via een beveiligingsrol die is ingesteld op zichtbaarheid op bedrijfsunitniveau in [!INCLUDE[d365fin](includes/cds_long_md.md)] kunnen nu die records zien. In het volgende voorbeeld ziet u hoe u teams kunt gebruiken om toegang te verlenen tot die records.

* De rol van Verkoopmanager wordt toegewezen aan leden van het team Cronus US Sales.
* Gebruikers met de rol van Verkoopmanager hebben toegang tot accountrecords voor leden van dezelfde bedrijfseenheid.
* Het team Cronus US Sales is gekoppeld aan de eerder genoemde bedrijfsunit Cronus US. Leden van het team Cronus US Sales kunnen elk account zien dat eigendom is van de Cronus US <ID>-gebruiker, die afkomstig zal zijn van de bedrijfsentiteit Cronus US in [!INCLUDE[d365fin](includes/d365fin_md.md)].

De 1: 1-toewijzing tussen bedrijfsunit, bedrijf en team is echter slechts een startpunt, zoals weergegeven in de volgende afbeelding.

![De beveiligingsrol bepaalt de zichtbaarheid van gegevens.](media/cds_bu_team_company_2.png)

In dit voorbeeld wordt een nieuwe hoofdbedrijfsunit EUR (Europa) gecreëerd in [!INCLUDE[d365fin](includes/cds_long_md.md)] als bovenliggend element voor zowel Cronus DE (Duitsland) als Cronus ES (Spanje). De bedrijfsunit EUR is niet gerelateerd aan synchronisatie. Deze kan leden van het team EUR Sales echter toegang geven tot accountgegevens in zowel Cronus DE als Cronus ES door de zichtbaarheid van gegevens in te stellen op **Bovenliggende/onderliggende BU** in de bijbehorende beveiligingsrol in [!INCLUDE[d365fin](includes/cds_long_md.md)].

Synchronisatie bepaalt welk team records moet bezitten. Dit wordt bepaald door het veld **Standaardeigenaarsteam** in het BCI - <ID>-record. Wanneer een BCI - <ID>-record is ingeschakeld voor synchronisatie, maken we automatisch de bijbehorende bedrijfseenheid en het eigenaarsteam (als het nog niet bestaat) en wordt het veld **Standaardeigenaarsteam** ingesteld. Als synchronisatie is ingeschakeld voor een entiteit, kunnen beheerders het eigenaarsteam wijzigen, maar er moet altijd een team worden toegewezen.

> [!NOTE]
> Records worden alleen-lezen nadat een bedrijf is toegevoegd en opgeslagen, dus zorg ervoor dat u het juiste bedrijf kiest.

## <a name="choosing-a-different-business-unit"></a>Een andere bedrijfsunit kiezen
U kunt de selectie van de bedrijfsunit wijzigen als u het eigendomsmodel Teams gebruikt. Als u het eigendomsmodel Persoon gebruikt, wordt altijd de standaardbedrijfsunit geselecteerd. 

Als u bijvoorbeeld een andere bedrijfsunit kiest, een die u eerder in [!INCLUDE[d365fin](includes/cds_long_md.md)] hebt gemaakt, behoudt deze de oorspronkelijke naam. Dat wil zeggen, de naam krijgt niet als achtervoegsel de bedrijfs-ID. We stellen een team samen dat de naamgevingsconventie gebruikt.

Bij het wijzigen van een bedrijfsunit kunt u alleen de bedrijfsunits kiezen die één niveau lager liggen dan de hoofdbedrijfsunit.

## <a name="person-ownership"></a>Persoonseigendom
Als u het eigendomsmodel Persoon kiest, moet u elke verkoper specificeren die eigenaar zal zijn van nieuwe records. De bedrijfsunit en het team worden gemaakt zoals beschreven in de sectie [Teameigendom](admin-cds-company-concept.md#team-ownership).

De standaardbedrijfsunit wordt gebruikt wanneer het eigendomsmodel Persoon wordt gekozen en u kunt geen andere bedrijfsunit kiezen. Het team dat is gekoppeld aan de standaardbedrijfsunit is eigenaar van records voor gemeenschappelijke entiteiten, zoals de productentiteit, die niet zijn gerelateerd aan specifieke verkopers.

## <a name="see-also"></a>Zie ook
[Informatie over [!INCLUDE[d365fin](includes/cds_long_md.md)]](admin-common-data-service.md)