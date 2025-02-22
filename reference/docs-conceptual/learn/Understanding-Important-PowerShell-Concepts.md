---
ms.date: 08/23/2018
keywords: PowerShell-cmdlet
title: Informatie over belangrijke PowerShell-concepten
ms.openlocfilehash: 8f9af370db46ea47dbccbabb7cc90fc27b8f2765
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030980"
---
# <a name="understanding-important-powershell-concepts"></a>Informatie over belangrijke PowerShell-concepten

Het ontwerp van de PowerShell kan worden geïntegreerd met de concepten van veel verschillende omgevingen. Aantal van de concepten bekend zijn voor mensen met ervaring in de houders of programmeeromgevingen worden. Maar weet weinig mensen over al deze. Kijken naar enkele van deze concepten biedt een handig overzicht van de shell.

## <a name="output-is-object-based"></a>Uitvoer is gebaseerd op objecten

PowerShell-cmdlets zijn in tegenstelling tot traditionele opdrachtregelinterfaces ontworpen om op te lossen met objecten.
Een object is gestructureerde gegevens dat is meer dan alleen de reeks tekens op het scherm wordt weergegeven. Opdrachtuitvoer altijd bevat extra informatie die u gebruiken kunt als u deze nodig hebt.

Als u hulpprogramma's voor tekst-de verwerking hebt gebruikt voor het verwerken van gegevens in het verleden, zult u merken dat ze zich anders gedragen bij gebruik in PowerShell. In de meeste gevallen hoeft u geen tekst-de verwerking hulpprogramma's om specifieke informatie te extraheren. U rechtstreeks toegang tot gedeelten van de gegevens met behulp van standaard-object PowerShell-syntaxis.

## <a name="the-command-family-is-extensible"></a>De opdracht serie worden uitgebreid

Interfaces, zoals **cmd.exe** niet bieden een manier waarop u kunt rechtstreeks uitbreiden van de ingebouwde opdrachtenset. U kunt externe opdrachtregelprogramma's die worden uitgevoerd in maken **cmd.exe**. Maar deze hulpprogramma's voor externe services, zoals Help-integratie niet hebt. **cmd.exe** niet automatisch zeker weet dat deze externe hulpprogramma's geldige opdrachten zijn.

De systeemeigen in PowerShell-opdrachten worden aangeduid als *cmdlets* (uitgesproken als opdracht kunt). U kunt uw eigen modules cmdlets maken en functies met gecompileerde code of scripts. Modules kunnen cmdlets en providers toevoegen aan de shell. PowerShell biedt ook ondersteuning voor scripts die vergelijkbaar met UNIX-shell-scripts zijn en **cmd.exe** batch-bestanden.

## <a name="powershell-handles-console-input-and-display"></a>PowerShell wordt gebruikt voor console-invoer en weergave

Wanneer u een opdracht hebt getypt, verwerkt PowerShell altijd de opdrachtregel invoer rechtstreeks. De uitvoer die u op het scherm ziet ook de opmaak van PowerShell. Dit verschil is van belang omdat deze het werk dat nodig van elke cmdlet vermindert. Het zorgt ervoor dat u altijd dingen dezelfde manier als met een cmdlet doen kunt. Cmdlet ontwikkelaars hoeft te schrijven van code voor het parseren van de argumenten voor de opdrachtregel of de uitvoer.

Traditionele opdrachtregelprogramma's hebben hun eigen schema's voor het aanvragen en Help-informatie weergeven. Bepaalde opdrachtregelprogramma's gebruiken **/?** voor het activeren van de Help-informatie weergeven; anderen gebruiken **-?** , **/H**, of zelfs **//** . Sommige wordt Help weergegeven in het venster van een GUI, in plaats van in de console weer te geven. Als u de verkeerde parameter gebruikt, kan het hulpprogramma voor wat u hebt getypt en beginnen met het uitvoeren van een taak automatisch negeren.
Omdat PowerShell automatisch parseert en de opdrachtregel, verwerkt de **-?** parameter betekent altijd 'Toon Help voor deze opdracht'.

> [!NOTE]
> Als u een grafische toepassing in PowerShell uitvoert, wordt het venster voor de toepassing wordt geopend.
> PowerShell is opgetreden alleen bij verwerking van de opdrachtregel invoer u levering of de uitvoer van de toepassing die wordt geretourneerd naar het consolevenster. Dit heeft geen invloed op hoe de toepassing intern werkt.

## <a name="powershell-uses-some-c-syntax"></a>PowerShell maakt gebruik van sommige C# syntaxis

PowerShell is gebouwd op het .NET Framework. Deze deelt sommige functies van de syntaxis en trefwoorden met de C# programmeertaal. Leren werken met PowerShell kunt u veel gemakkelijker om te leren C#. Als u al bekend met bent C#, deze overeenkomsten leren werken met PowerShell gemakkelijker kunnen maken.
