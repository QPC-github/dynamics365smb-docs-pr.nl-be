---
title: Taken plannen voor automatische uitvoering
description: Leer hoe u taakwachtrijposten gebruikt om rapporten en codeunits uit te voeren.
author: brentholtorf
ms.author: bholtorf
ms.reviewer: jswymer
ms.topic: conceptual
ms.date: 03/20/2023
ms.custom: bap-template
ms.search.form: '672, 673, 674, 671'
---
# <a name="use-job-queues-to-schedule-tasks" />Gebruik van taakwachtrijen om taken te plannen

Gebruik de pagina **Taakwachtrijposten** om specifieke rapporten en codeunits te plannen en uit te voeren. U kunt taken éénmalig of herhaaldelijk uitvoeren. U kunt bijvoorbeeld het rapport **Verkoper * Verkoopstatistieken** wekelijks uitvoeren om verkopen per verkoper elke week bij te houden of u kunt de codeunit **Goedkeuringsaanvragen delegeren** dagelijks uitvoeren om te voorkomen dat documenten zich opstapelen.

Op de pagina Taakwachtrijposten worden alle bestaande posten weergegeven. Als u een nieuwe taakwachtrijpost toevoegt die volgens planning wordt uitgevoerd, moet u wat informatie verstrekken. Voorbeeld:

* Het type object dat moet worden uitgevoerd, zoals een rapport of codeunit. U moet toestemming hebben om het specifieke rapport of de codeunit uit te voeren.
* De naam en object-id van het object.
* Parameters om het gedrag van het taakwachtrij-item te specificeren. Zo kunt u een parameter toevoegen om alleen geboekte verkooporders te verzenden.
* Wanneer en hoe vaak het taakwachtrij-item wordt uitgevoerd.

> [!IMPORTANT]  
> Als aan u de machtigingenset SUPER is toegewezen die wordt geleverd met [!INCLUDE[prod_short](includes/prod_short.md)], bent u gemachtigd alle in uw licentie opgenomen objecten uit te voeren. Als u de rol Gedelegeerd beheerder hebt, kunt u taakwachtrijposten maken en plannen, maar alleen beheerders en gelicentieerde gebruikers kunnen ze uitvoeren. Gebruikers met de apparaatlicentie kunnen geen taakwachtrijposten maken of uitvoeren.

Nadat taakwachtrijen zijn ingesteld en werken, kan de status als volgt veranderen in elke doorlopende periode:

* **Afwachten**  
* **Gereed**  
* **In verwerking**  
* **Fout**  
* **Gereedgemeld**  

Nadat een taak is voltooid, wordt deze verwijderd uit de lijst met taakwachtrij-items, tenzij het een terugkerende taak is. Voor terugkerende taken wordt het veld **Vroegste begintijd** aangepast, zodat het de volgende keer weergeeft dat de taak wordt uitgevoerd.  

## <a name="monitor-status-or-errors-in-the-job-queue" />Status of fouten in de taakwachtrij bewaken

Gegevens die de taakwachtrij genereert, worden opgeslagen, zodat u fouten kunt oplossen.  

Voor elk item in de wachtrij kunt u de status bekijken en wijzigen. Wanneer u een taakwachtrij-item maakt, wordt de status ingesteld op **Afwachten**. U kunt de status bijvoorbeeld instellen op **Klaar** en weer op **Afwachten**. Als u dat niet doet, wordt statusinformatie automatisch bijgewerkt.

De volgende tabel beschrijft de waarden van het veld **Status**.

| Status | Omschrijving |
|--|--|
| Gereed | Het taakwachtrij-item is klaar om te worden uitgevoerd. |
| In verwerking | Het taakwachtrij-item wordt verwerkt. Dit veld wordt bijgewerkt terwijl de taakwachtrij wordt uitgevoerd. |
| Afwachten | De standaardstatus van het taakwachtrij-item wanneer het wordt gemaakt. Kies de actie **Status instellen op Gereed** om de status te wijzigen in **Gereed**. Kies de actie **Instellen op afwachten** om de status terug te zetten naar **Afwachten**. |
| Fout | Er is iets fout gegaan. Kies **Fout weergeven** om het foutbericht weer te geven. |
| Voltooid | Het taakwachtrij-item is voltooid. |

> [!Tip]  
> Taakwachtrij-items worden niet meer uitgevoerd wanneer er een fout is. Dit kan bijvoorbeeld een probleem zijn wanneer een item verbinding maakt met een externe service, zoals een bankfeed. Als de service tijdelijk niet beschikbaar is en het item in de taakwachtrij geen verbinding kan maken, geeft het item een fout weer en stopt het met werken. U moet het taakwachtrij-item handmatig opnieuw starten. De velden **Maximaal aantal pogingen** en **Vertraging bij opnieuw uitvoeren (sec.)** kunnen u echter helpen deze situatie te voorkomen. Met het veld **Maximaal aantal pogingen** kunt u specificeren hoe vaak het invoeren van het taakwachtrij-item kan mislukken voordat het stopt met proberen te worden uitgevoerd. Met het veld **Vertraging bij opnieuw uitvoeren (sec.)** kunt u de hoeveelheid tijd, in seconden, tussen pogingen specificeren. De combinatie van deze twee velden kan ervoor zorgen dat het taakwachtrij-item actief blijft totdat de externe service beschikbaar komt.

### <a name="to-view-status-for-any-job" />De status voor een taak weergeven

1. Kies het ![Lampje dat de functie Vertel me opent.](media/ui-search/search_small.png "Vertel me wat u wilt doen"), voer **Taakwachtrijposten** in en kies vervolgens de gerelateerde koppeling.
2. Selecteer op de pagina **Taakwachtrijposten** een taakwachtrijpost en kies vervolgens de actie **Logboekvermeldingen**.  

> [!TIP]
> Voor grondige analyse op basis van telemetrie kunt u Application Insights in Microsoft Azure gebruiken om de status van taakwachtrijposten te controleren. Ga voor meer informatie over telemetrie naar [Telemetrie bewaken en analyseren](/dynamics365/business-central/dev-itpro/administration/telemetry-overview) en [Traceringstelemetrie van levenscyclus van taakwachtrij analyseren](/dynamics365/business-central/dev-itpro/administration/telemetry-job-queue-lifecycle-trace).

## <a name="view-scheduled-tasks" />Geplande taken weergeven

De pagina **Geplande taken** in [!INCLUDE [prod_short](includes/prod_short.md)] laat zien welke taken klaar zijn om te worden uitgevoerd in de taakwachtrij. De pagina toont ook informatie over het bedrijf waarvoor elke taak is ingesteld om te worden uitgevoerd. Alleen taken die zijn gemarkeerd als behorend tot de huidige omgeving kunnen echter worden uitgevoerd.  

Alle geplande taken stoppen bijvoorbeeld als het bedrijf zich in een omgeving bevindt die een kopie is van een andere omgeving. Gebruik de pagina **Geplande taken** om taken in te stellen als gereed om te worden uitgevoerd in de taakwachtrij.  

> [!NOTE]
> Interne beheerders en gelicentieerde gebruikers kunnen taken plannen om te worden uitgevoerd. Gedelegeerde beheerders kunnen taken instellen en plannen om uit te voeren, maar alleen gebruikers met een licentie kunnen ze uitvoeren.

## <a name="the-my-job-queue-part" />Het onderdeel Mijn taakwachtrij

In het onderdeel **Mijn taakwachtrij** in uw rolcentrum worden de taakwachtrij-items weergegeven die u hebt gestart, maar die niet zijn voltooid. Standaard wordt het onderdeel niet weergegeven, maar u kunt het toevoegen aan uw rolcentrum. Ga voor meer informatie over personalisatie naar [Uw werkruimte personaliseren](ui-personalization-user.md).  

Het onderdeel toont de volgende informatie:

* Welke documenten met uw id in het veld **Toegewezen gebruikers-id** worden verwerkt of in de wachtrij staan, inclusief documenten die op de achtergrond worden geboekt. 
* Of er een fout is opgetreden bij het boeken van een document of in de taakwachtrij. 

Met het onderdeel Mijn taakwachtrij kunt u een documentboeking ook annuleren.

### <a name="to-view-an-error-from-the-my-job-queue-part" />Een fout in het gedeelte Mijn taakwachtrij weergeven

1. Kies in een post met de status **Fout** de actie **Fout weergeven**.
2. Bekijk de foutmelding en los het probleem op.

## <a name="examples-of-what-you-can-schedule-using-job-queue-entries" />Voorbeelden van wat kan worden gepland met behulp van taakwachtrijposten

### <a name="schedule-reports" />Rapporten plannen

U kunt een rapport plannen voor uitvoering op een bepaalde datum en tijd. Geplande rapporten en batchtaken worden in de verwerkingswachtrij ingevoerd en verwerkt op het geplande tijdstip, net zoals andere taken. U kiest de optie **Schema** nadat u de actie **Verzenden naar** hebt gekozen en voert vervolgens informatie in zoals de printer, de tijd en datum en de herhaling.  

Ga voor meer informatie over planning naar [Een rapport plannen voor uitvoering](ui-work-report.md#ScheduleReport)

### <a name="schedule-synchronization-between-includeprodshortincludesprodshortmd-and-includeprodshortincludescdslongmdmd" />Synchronisatie plannen tussen [!INCLUDE[prod_short](includes/prod_short.md)] en [!INCLUDE[prod_short](includes/cds_long_md.md)]

Als u [!INCLUDE[prod_short](includes/prod_short.md)] hebt geïntegreerd met [!INCLUDE[prod_short](includes/cds_long_md.md)], kunt u met de taakwachtrij plannen wanneer u gegevens wilt synchroniseren. Afhankelijk van de richting en regels die u hebt gedefinieerd, kan het taakwachtrij-item records maken in de ene app om met records in de andere overeen te komen. Een goed voorbeeld is dat wanneer u een contact registreert in [!INCLUDE[crm_md](includes/crm_md.md)], het taakwachtrij-item dat contact voor u kan instellen in [!INCLUDE[prod_short](includes/prod_short.md)]. Zie [Een synchronisatie plannen tussen Business Central en Dynamics 365 Sales](admin-scheduled-synchronization-using-the-synchronization-job-queue-entries.md) voor meer informatie over planning.

### <a name="schedule-when-to-post-sales-and-purchase-orders" />Het boeken van verkoop- en inkooporders plannen

U kunt taakwachtrij-items gebruiken om bedrijfsprocessen te plannen die op de achtergrond worden uitgevoerd. Achtergrondtaken zijn bijvoorbeeld nuttig wanneer meerdere gebruikers tegelijkertijd verkooporders boeken, maar er slechts één order tegelijk kan worden verwerkt. Ga voor meer informatie over boeken op de achtergrond naar [Boeking op de achtergrond instellen met taakwachtrijen](ui-batch-posting.md#to-set-up-background-posting-with-job-queues).

## <a name="handle-job-queue-entry-issues" />Problemen met taakwachtrijposten afhandelen

Als een taakwachtrijpost een fout vertoont, is uw eerste optie om het probleem op te lossen het opnieuw starten van de taakwachtrijpost. U kunt de status van de taakwachtrijpost instellen op **Afwachten** en dan naar **Gereed**, of start het gewoon opnieuw.

Als opnieuw starten niet helpt, ligt het probleem mogelijk in de code. U vindt de eigenaar (ook wel de *uitgever*) van de code in de AL-stacktracering in het taakwachtrijlogboek. Neem contact op met uw Microsoft-partner als de fout afkomstig is van een app/extensie. Als de fout afkomstig is van een Microsoft-toepassing, open dan een ondersteuningsverzoek bij Microsoft.

Als u contact opneemt met uw Microsoft-partner of Microsoft voor ondersteuning, geef dan de volgende informatie door:

* De id van de taakwachtrijpost waar de fout optrad
* Het tijdstempel van wanneer de fout optrad
* Uw tijdzone

> [!TIP]
> Afhankelijk van of uw [!INCLUDE [prod_short](includes/prod_short.md)] ouder of later is dan versie 22.1, verzamelt u de informatie op de volgende manieren:
>
> * Geef voor eerdere versies een schermafbeelding van de pagina **Logposten taakwachtrij**.
> * Voor latere versies gebruikt u de actie **Details kopiëren** op de pagina Logposten taakwachtrij om de informatie te kopiëren (taakwachtrij-id, tijdstempel en uw tijdzone).

## <a name="monitor-the-job-queue-with-telemetry" />De taakwachtrij bewaken met telemetrie

Beheerders kunnen [Azure Application Insights](/azure/azure-monitor/app/app-insights-overview) gebruiken om telemetrie te verzamelen en te analyseren die u kunt gebruiken om problemen te identificeren. Ga voor meer informatie over telemetrie naar [Telemetrie bewaken en analyseren](/dynamics365/business-central/dev-itpro/administration/telemetry-overview) en [Traceringstelemetrie van levenscyclus van taakwachtrij analyseren](/dynamics365/business-central/dev-itpro/administration/telemetry-job-queue-lifecycle-trace).

Met telemetrie kunnen beheerders waarschuwingen instellen voor problemen met de taakwachtrij die een sms, e-mail of een bericht in Teams verzenden als er iets niet klopt. Ga voor meer informatie over deze waarschuwingen naar [Waarschuwing over telemetrie](/dynamics365/business-central/dev-itpro/administration/telemetry-alert).

## <a name="see-also" />Zie ook

[Beheer](admin-setup-and-administration.md)  
[Business Central instellen](setup.md)  
[Basisinstellingen wijzigen](ui-change-basic-settings.md)  
[Traceringstelemetrie van levenscyclus van taakwachtrij analyseren](/dynamics365/business-central/dev-itpro/administration/telemetry-job-queue-lifecycle-trace)  
[Waarschuwing over telemetrie](/dynamics365/business-central/dev-itpro/administration/telemetry-alert)

[!INCLUDE[footer-include](includes/footer-banner.md)]
