---
title: Hoe bij te werken Help Works | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 5b6ae54ee6c843996c875189b6ee553be5e4f614
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794379"
---
# <a name="how-updatable-help-works"></a><span data-ttu-id="695ec-102">De werking van Help die kan worden bijgewerkt</span><span class="sxs-lookup"><span data-stu-id="695ec-102">How Updatable Help Works</span></span>

<span data-ttu-id="695ec-103">In dit onderwerp wordt uitgelegd hoe bij te werken Help processen de HelpInfo XML-bestand en de CAB-bestanden voor elke module en installeert de help voor gebruikers bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="695ec-103">This topic explains how Updatable Help processes the HelpInfo XML file and CAB files for each module, and installs updated help for users.</span></span>

## <a name="the-update-help-process"></a><span data-ttu-id="695ec-104">Het proces voor Update-Help</span><span class="sxs-lookup"><span data-stu-id="695ec-104">The Update-Help Process</span></span>

<span data-ttu-id="695ec-105">De volgende lijst beschrijft de acties van de [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet wanneer een gebruiker een opdracht voor het bijwerken van de help-bestanden voor een module in een bepaalde gebruikersinterfacecultuur uitvoert.</span><span class="sxs-lookup"><span data-stu-id="695ec-105">The following list describes the actions of the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet when a user runs a command to update the help files for a module in a particular UI culture.</span></span>

1. <span data-ttu-id="695ec-106">`Update-Help` Met deze eigenschap wordt het externe HelpInfo XML-bestand van de locatie die is opgegeven door de waarde van de **HelpInfoURI** sleutel in de module-manifest en valideert u het bestand op basis van het schema.</span><span class="sxs-lookup"><span data-stu-id="695ec-106">`Update-Help` gets the remote HelpInfo XML file from the location specified by the value of the **HelpInfoURI** key in the module manifest and validates the file against the schema.</span></span> <span data-ttu-id="695ec-107">(Als u het schema, Zie [HelpInfo XML-Schema](./helpinfo-xml-schema.md).) Vervolgens `Update-Help` zoekt naar een lokale HelpInfo XML-bestand voor de module in de modulemap op de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="695ec-107">(To view the schema, see [HelpInfo XML Schema](./helpinfo-xml-schema.md).) Then `Update-Help` looks for a local HelpInfo XML file for the module in the module directory on the user's computer.</span></span>

2. <span data-ttu-id="695ec-108">`Update-Help` vergelijkt het versienummer van de help-bestanden voor de opgegeven cultuur van de gebruikersinterface in de lokale en externe HelpInfo XML-bestanden voor de module.</span><span class="sxs-lookup"><span data-stu-id="695ec-108">`Update-Help` compares the version number of the help files for the specified UI culture in the remote and local HelpInfo XML files for the module.</span></span> <span data-ttu-id="695ec-109">Als het versienummer van het externe bestand is groter dan het versienummer van het lokale bestand, of als er geen lokale HelpInfo XML-bestand voor de module `Update-Help` bereidt het downloaden van nieuwe help-bestanden.</span><span class="sxs-lookup"><span data-stu-id="695ec-109">If the version number on the remote file is greater than version number on the local file, or if the there is no local HelpInfo XML file for the module, `Update-Help` prepares to download new help files.</span></span>

3. <span data-ttu-id="695ec-110">`Update-Help` het CAB-bestand voor de module selecteert in de locatie die is opgegeven door de **HelpContentUri** -element in het externe HelpInfo XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="695ec-110">`Update-Help` selects the CAB file for the module from the location specified by the **HelpContentUri** element in the remote HelpInfo XML file.</span></span> <span data-ttu-id="695ec-111">Deze modulenaam van de, module GUID en gebruikersinterfacecultuur gebruikt om te identificeren van het CAB-bestand.</span><span class="sxs-lookup"><span data-stu-id="695ec-111">It uses the module name, module GUID, and UI culture to identify the CAB file.</span></span>

4. <span data-ttu-id="695ec-112">`Update-Help` het CAB-bestand wordt gedownload, Hiermee wordt het, valideert de inhoudsbestanden van Help-informatie en de help-inhoud bestanden opgeslagen in de taalspecifieke submap van de modulemap op de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="695ec-112">`Update-Help` downloads the CAB file, unpacks it, validates the help content files, and saves the help content files in the language-specific subdirectory of the module directory on the user's computer.</span></span>

5. <span data-ttu-id="695ec-113">`Update-Help` Hiermee maakt u een lokaal HelpInfo XML-bestand door de externe HelpInfo XML-bestand te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="695ec-113">`Update-Help` creates a local HelpInfo XML file by copying the remote HelpInfo XML file.</span></span> <span data-ttu-id="695ec-114">Wordt het lokale HelpInfo XML-bestand hebt bewerkt, waarbij er elementen alleen voor de CAB-bestand dat deze is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="695ec-114">It edits the local HelpInfo XML file so that it includes elements only for the CAB file that it installed.</span></span> <span data-ttu-id="695ec-115">Vervolgens slaat het lokale HelpInfo XML-bestand in de modulemap en is de update.</span><span class="sxs-lookup"><span data-stu-id="695ec-115">Then it saves the local HelpInfo XML file in the module directory and concludes the update.</span></span>

## <a name="the-save-help-process"></a><span data-ttu-id="695ec-116">Het proces Help opslaan</span><span class="sxs-lookup"><span data-stu-id="695ec-116">The Save-Help Process</span></span>

<span data-ttu-id="695ec-117">De volgende lijst beschrijft de acties van de [Help opslaan](/powershell/module/Microsoft.PowerShell.Core/Save-Help) en [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets wanneer een gebruiker wordt uitgevoerd voor opdrachten voor het bijwerken van de help-bestanden in een bestandsshare en deze bestanden vervolgens gebruiken om bij te werken van de help-bestanden op de de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="695ec-117">The following list describes the actions of the [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) and [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlets when a user runs commands to update the help files in a file share, and then use those files to update the help files on the user's computer.</span></span>

<span data-ttu-id="695ec-118">De `Save-Help` cmdlet worden de volgende acties uitgevoerd in reactie op een opdracht voor het opslaan van de help-bestanden voor een module in een bestandsshare die is opgegeven door de **doelpad** parameter.</span><span class="sxs-lookup"><span data-stu-id="695ec-118">The `Save-Help` cmdlet performs the following actions in response to a command to save the help files for a module in a file share that is specified by the **DestinationPath** parameter.</span></span>

1. <span data-ttu-id="695ec-119">`Save-Help` Met deze eigenschap wordt het externe HelpInfo XML-bestand van de locatie die is opgegeven door de waarde van de **HelpInfoURI** sleutel in de module-manifest en valideert u het bestand op basis van het schema.</span><span class="sxs-lookup"><span data-stu-id="695ec-119">`Save-Help` gets  the remote HelpInfo XML file from the location specified by the value of the **HelpInfoURI** key in the module manifest and validates the file against the schema.</span></span> <span data-ttu-id="695ec-120">(Als u het schema, Zie [HelpInfo XML-Schema](./helpinfo-xml-schema.md).) Vervolgens `Save-Help` zoekt naar een lokale HelpInfo XML-bestand in de map die is opgegeven door de **doelpad** parameter in de `Save-Help` opdracht.</span><span class="sxs-lookup"><span data-stu-id="695ec-120">(To view the schema, see [HelpInfo XML Schema](./helpinfo-xml-schema.md).) Then `Save-Help` looks for a local HelpInfo XML file in the directory that is specified by the **DestinationPath** parameter in the `Save-Help` command.</span></span>

2. <span data-ttu-id="695ec-121">`Save-Help` vergelijkt het versienummer van de help-bestanden voor de opgegeven cultuur van de gebruikersinterface in de lokale en externe HelpInfo XML-bestanden voor de module.</span><span class="sxs-lookup"><span data-stu-id="695ec-121">`Save-Help` compares the version number of the help files for the specified UI culture in the remote and local HelpInfo XML files for the module.</span></span> <span data-ttu-id="695ec-122">Als het versienummer van het externe bestand is groter dan het versienummer van het lokale bestand, of als er geen lokale HelpInfo XML-bestand voor de module in de **doelpad** directory `Save-Help` bereidt het downloaden van nieuwe help-bestanden.</span><span class="sxs-lookup"><span data-stu-id="695ec-122">If the version number on the remote file is greater than version number on the local file, or if the there is no local HelpInfo XML file for the module in the **DestinationPath** directory, `Save-Help` prepares to download new help files.</span></span>

3. <span data-ttu-id="695ec-123">`Save-Help` het CAB-bestand voor de module selecteert in de locatie die is opgegeven door de **HelpContentUri** -element in het externe HelpInfo XML-bestand.</span><span class="sxs-lookup"><span data-stu-id="695ec-123">`Save-Help` selects the CAB file for the module from the location specified by the **HelpContentUri** element in the remote HelpInfo XML file.</span></span> <span data-ttu-id="695ec-124">Deze modulenaam van de, module GUID en gebruikersinterfacecultuur gebruikt om te identificeren van het CAB-bestand.</span><span class="sxs-lookup"><span data-stu-id="695ec-124">It uses the module name, module GUID, and UI culture to identify the CAB file.</span></span>

4. <span data-ttu-id="695ec-125">`Save-Help` het CAB-bestand wordt gedownload en opgeslagen in de **doelpad** directory.</span><span class="sxs-lookup"><span data-stu-id="695ec-125">`Save-Help` downloads the CAB file and saves it in the **DestinationPath** directory.</span></span> <span data-ttu-id="695ec-126">(Er wordt geen eventuele submappen taalspecifieke gemaakt.)</span><span class="sxs-lookup"><span data-stu-id="695ec-126">(It does not create any language-specific subdirectories.)</span></span>

5. <span data-ttu-id="695ec-127">`Save-Help` Hiermee maakt u een lokaal HelpInfo XML-bestand door de externe HelpInfo XML-bestand te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="695ec-127">`Save-Help` creates a local HelpInfo XML file by copying the remote HelpInfo XML file.</span></span> <span data-ttu-id="695ec-128">Wordt het lokale HelpInfo XML-bestand hebt bewerkt, waarbij er elementen alleen voor het CAB-bestand die zijn opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="695ec-128">It edits the local HelpInfo XML file so that it includes elements only for the CAB file that it saved.</span></span> <span data-ttu-id="695ec-129">Vervolgens wordt het lokale HelpInfo XML-bestand in de **doelpad** directory en de update is afgelopen.</span><span class="sxs-lookup"><span data-stu-id="695ec-129">Then it saves the local HelpInfo XML file in the  **DestinationPath** directory and concludes the update.</span></span>

   <span data-ttu-id="695ec-130">De `Update-Help` cmdlet worden de volgende acties uitgevoerd in reactie op een opdracht voor het bijwerken van de help-bestanden op de computer van een gebruiker uit de bestanden in een bestandsshare die is opgegeven door de **bronpad** parameter.</span><span class="sxs-lookup"><span data-stu-id="695ec-130">The `Update-Help` cmdlet performs the following actions in response to a command to update the help files on a user's computer from the files in a file share that is specified by the **SourcePath** parameter.</span></span>

1. <span data-ttu-id="695ec-131">`Update-Help` Met deze eigenschap wordt het externe HelpInfo XML-bestand van de **bronpad** directory.</span><span class="sxs-lookup"><span data-stu-id="695ec-131">`Update-Help` gets the remote HelpInfo XML file from the **SourcePath** directory.</span></span> <span data-ttu-id="695ec-132">Vervolgens wordt gezocht naar een lokale HelpInfo XML-bestand in de modulemap op de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="695ec-132">Then it looks for a local HelpInfo XML file in the module directory on the user's computer.</span></span>

2. <span data-ttu-id="695ec-133">`Update-Help` vergelijkt het versienummer van de help-bestanden voor de opgegeven cultuur van de gebruikersinterface in de lokale en externe HelpInfo XML-bestanden voor de module.</span><span class="sxs-lookup"><span data-stu-id="695ec-133">`Update-Help` compares the version number of the help files for the specified UI culture in the remote and local HelpInfo XML files for the module.</span></span> <span data-ttu-id="695ec-134">Als het versienummer van het externe bestand is groter dan het versienummer van het lokale bestand, of als er geen lokale HelpInfo XML-bestand, `Update-Help` wordt voorbereid voor het installeren van nieuwe help-bestanden.</span><span class="sxs-lookup"><span data-stu-id="695ec-134">If the version number on the remote file is greater than version number on the local file, or if the there is no local HelpInfo XML file, `Update-Help` prepares to install new help files.</span></span>

3. <span data-ttu-id="695ec-135">`Update-Help` Hiermee selecteert u het CAB-bestand voor de module op basis van **bronpad** directory.</span><span class="sxs-lookup"><span data-stu-id="695ec-135">`Update-Help` selects the CAB file for the module from **SourcePath** directory.</span></span> <span data-ttu-id="695ec-136">Deze modulenaam van de, module GUID en gebruikersinterfacecultuur gebruikt om te identificeren van het CAB-bestand.</span><span class="sxs-lookup"><span data-stu-id="695ec-136">It uses the module name, module GUID, and UI culture to identify the CAB file.</span></span>

4. <span data-ttu-id="695ec-137">`Update-Help` Hiermee wordt het CAB-bestand, valideert de inhoudsbestanden van Help-informatie en de help-inhoud bestanden opgeslagen in de taalspecifieke submap van de modulemap op de computer van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="695ec-137">`Update-Help` unpacks the CAB file, validates the help content files, and saves the help content files in the language-specific subdirectory of the module directory on the user's computer.</span></span>

5. <span data-ttu-id="695ec-138">`Update-Help` Hiermee maakt u een lokaal HelpInfo XML-bestand door de externe HelpInfo XML-bestand te kopiëren.</span><span class="sxs-lookup"><span data-stu-id="695ec-138">`Update-Help` creates a local HelpInfo XML file by copying the remote HelpInfo XML file.</span></span> <span data-ttu-id="695ec-139">Wordt het lokale HelpInfo XML-bestand hebt bewerkt, waarbij er elementen alleen voor de CAB-bestand dat deze is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="695ec-139">It edits the local HelpInfo XML file so that it includes elements only for the CAB file that it installed.</span></span> <span data-ttu-id="695ec-140">Vervolgens slaat het lokale HelpInfo XML-bestand in de modulemap en is de update.</span><span class="sxs-lookup"><span data-stu-id="695ec-140">Then it saves the local HelpInfo XML file in the module directory and concludes the update.</span></span>