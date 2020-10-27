---
title: Bedrijven toevoegen aan uw bedrijfshub
description: Leer hoe u bedrijven uit andere Business Central-omgevingen aan uw bedrijfshub toevoegt, zodat u werk in verschillende omgevingen kunt beheren.
author: edupont04
ms.service: dynamics365-business-central
ms.topic: article
ms.search.keywords: accountant, accounting, company hub
ms.date: 10/01/2020
ms.author: edupont
ms.openlocfilehash: 773731ecc860e7d1ea0d13bbf9e6896a746544be
ms.sourcegitcommit: ddbb5cede750df1baba4b3eab8fbed6744b5b9d6
ms.translationtype: HT
ms.contentlocale: nl-BE
ms.lasthandoff: 10/01/2020
ms.locfileid: "3927806"
---
# <a name="add-companies-to-your-company-hub"></a>Bedrijven toevoegen aan uw bedrijfshub

Met de bedrijfshub hebt u toegang tot uw werk vanuit meerdere bedrijven vanuit meerdere [!INCLUDE [prodshort](includes/prodshort.md)]-omgevingen. U kunt handmatig omgevingen en bedrijven toevoegen als uw bedrijven niet automatisch in de bedrijfshub verschijnen.  

Op de landingspagina van de bedrijfshub vindt u het menu **Instellingen** , van waaruit u de pagina **Omgevingskoppelingen** kunt openen. Kies gewoon **Nieuw** en vul vervolgens de velden in. [!INCLUDE [tooltip-inline-tip_md](includes/tooltip-inline-tip_md.md)]  

## <a name="environment-links"></a>Omgevingskoppelingen

Een omgevingskoppeling is een kaart waar u de [!INCLUDE [prodshort](includes/prodshort.md)]-omgeving opgeeft die een of meer bedrijven host waarin u werkt. De gegevens op de kaart voor elke omgeving worden door u opgegeven en u kunt deze desgewenst wijzigen. Het veld **Omgevingskoppeling** is echter erg belangrijk. Daarmee krijg u toegang tot elk bedrijf in [!INCLUDE [prodshort](includes/prodshort.md)]. Gebruik de actie **De verbinding testen** op het lint om te testen dat u de juiste koppeling hebt ingevoerd. De koppeling die u moet invoeren verwijst naar de omgeving die het bedrijf host dat u toevoegt, en moet de Azure Active Directory-id (Azure AD) of de domeinnaam van de organisatie bevatten. Als zij het domein bijvoorbeeld hebben opgegeven als MyBusiness.com, is de koppeling naar hun [!INCLUDE [prodshort](includes/prodshort.md)] ```https://businesscentral.dynamics.com/mybusiness.com?redirectedfromsignup=1```. Anders ziet het er ongeveer zo uit: ```https://businesscentral.dynamics.com/1a23b456-789c-0123-45de-678910fg12h/production?redirectedfromsignup=1```  

De koppeling wordt gebruikt wanneer u het bedrijf kiest in de bedrijfshub.  

:::image type="content" source="media/company-hub-company-list-actions.png" alt-text="Acties voor een bedrijf dat wordt vermeld in de bedrijfshub":::

> [!TIP]
> Als u werkt in de gratis proefversie van [!INCLUDE [prodshort](includes/prodshort.md)], is het eenvoudig om de bedrijven aan uw tenant toe te voegen. U kunt de omgevingskoppeling vinden door de Azure Active Directory-id te kopiëren vanuit de sectie **Problemen oplossen** van de pagina Help en ondersteuning. De omgevingsnaam is waarschijnlijk de standaardwaarde, PRODUCTIE. Voeg deze informatie toe aan het veld **Omgevingskoppeling** , zoals ```https://businesscentral.dynamics.com/1a23b456-789c-0123-45de-678910fg12h/production?redirectedfromsignup=1``` en kies vervolgens **De verbinding testen** . Het evaluatiebedrijf wordt aan de lijst toegevoegd.
>
> Als u bent overgestapt op het bedrijf van de proefversie van 30 dagen, Mijn bedrijf, kunt u dat aan de lijst toevoegen door te kiezen voor de actie **Opnieuw laden/Alle bedrijven opnieuw laden** in de lijst.

## <a name="load-companies"></a>Bedrijven laden

Wanneer u uw omgevingen hebt toegevoegd, verschijnen uw bedrijven automatisch. Als u echter weet dat er een nieuw bedrijf aan een omgeving is toegevoegd, kunt u de actie **Alle bedrijven opnieuw laden** kiezen om de lijst te vernieuwen. Gebruik dezelfde actie om gegevens van al uw bedrijven te vernieuwen.  

> [!TIP]
> Om de gegevens in de bedrijfshub te vernieuwen moet u toegang hebben tot de gegevens in de bedrijven waar de gegevens vandaan komen.

## <a name="see-also"></a>Zie ook

[Werk beheren tussen meerdere bedrijven in de bedrijfshub](company-hub.md)  
[Bronnen voor Help en ondersteuning](product-help-and-support.md)  