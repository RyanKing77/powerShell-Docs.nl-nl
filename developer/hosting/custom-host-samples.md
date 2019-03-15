---
title: Voorbeelden van aangepaste Host | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55aee25b-bbcb-4d41-a4c0-fb8e30c4cdc1
caps.latest.revision: 11
ms.openlocfilehash: 1e58b74cf1c37c70ebfb0f4970cfbf8a8263ec5c
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794141"
---
# <a name="custom-host-samples"></a><span data-ttu-id="f4fa9-102">Voorbeelden van aangepaste hosts</span><span class="sxs-lookup"><span data-stu-id="f4fa9-102">Custom Host Samples</span></span>

<span data-ttu-id="f4fa9-103">In deze sectie bevat voorbeelden van code voor het schrijven van een aangepaste host.</span><span class="sxs-lookup"><span data-stu-id="f4fa9-103">This section includes sample code for writing a custom host.</span></span> <span data-ttu-id="f4fa9-104">Microsoft Visual Studio kunt u een consoletoepassing maken en kopieer vervolgens de code van de onderwerpen in deze sectie in uw hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="f4fa9-104">You can use Microsoft Visual Studio to create a console application and then copy the code from the topics in this section into your host application.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f4fa9-105">In deze sectie</span><span class="sxs-lookup"><span data-stu-id="f4fa9-105">In This Section</span></span>

 <span data-ttu-id="f4fa9-106">[Voorbeeld van Host01](./host01-sample.md) dit voorbeeld laat zien hoe u een hosttoepassing die gebruikmaakt van een eenvoudige aangepaste host implementeert.</span><span class="sxs-lookup"><span data-stu-id="f4fa9-106">[Host01 Sample](./host01-sample.md) This sample shows how to implement a host application that uses a basic custom host.</span></span>

 <span data-ttu-id="f4fa9-107">[Voorbeeld van Host02](./host02-sample.md) dit voorbeeld laat zien hoe u een hosttoepassing die gebruikmaakt van de Windows PowerShell-runtime, samen met de implementatie van een aangepaste host schrijft.</span><span class="sxs-lookup"><span data-stu-id="f4fa9-107">[Host02 Sample](./host02-sample.md) This sample shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span> <span data-ttu-id="f4fa9-108">De hosttoepassing wordt de cultuur van de host ingesteld op Duits, wordt uitgevoerd de [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet en wordt weergegeven op de resultaten op als u ze ziet met behulp van pwrsh.exe en vervolgens af te drukken om de huidige datum en tijd in het Duits.</span><span class="sxs-lookup"><span data-stu-id="f4fa9-108">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them using pwrsh.exe, and then prints out the current data and time in German.</span></span>

 <span data-ttu-id="f4fa9-109">[Voorbeeld van Host03](./host03-sample.md) in dit voorbeeld laat zien hoe u een interactieve console-gebaseerde hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, Hiermee voert u de opdrachten en vervolgens de resultaten worden weergegeven in de console.</span><span class="sxs-lookup"><span data-stu-id="f4fa9-109">[Host03 Sample](./host03-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

 <span data-ttu-id="f4fa9-110">[Voorbeeld van Host04](./host04-sample.md) in dit voorbeeld laat zien hoe u een interactieve console-gebaseerde hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, Hiermee voert u de opdrachten en vervolgens de resultaten worden weergegeven in de console.</span><span class="sxs-lookup"><span data-stu-id="f4fa9-110">[Host04 Sample](./host04-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="f4fa9-111">Weergave prompts die toestaan dat de gebruiker om op te geven meerdere mogelijkheden biedt ook ondersteuning voor deze hosttoepassing.</span><span class="sxs-lookup"><span data-stu-id="f4fa9-111">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

 <span data-ttu-id="f4fa9-112">[Voorbeeld van Host05](./host05-sample.md) in dit voorbeeld laat zien hoe u een interactieve console-gebaseerde hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, Hiermee voert u de opdrachten en vervolgens de resultaten worden weergegeven in de console.</span><span class="sxs-lookup"><span data-stu-id="f4fa9-112">[Host05 Sample](./host05-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="f4fa9-113">Deze hosttoepassing biedt ook ondersteuning voor aanroepen naar externe computers met behulp van de [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) en [afsluiten PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span><span class="sxs-lookup"><span data-stu-id="f4fa9-113">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets</span></span>

 <span data-ttu-id="f4fa9-114">[Voorbeeld van Host06](./host06-sample.md) in dit voorbeeld laat zien hoe u een interactieve console-gebaseerde hosttoepassing bouwt die opdrachten leest vanaf de opdrachtregel, Hiermee voert u de opdrachten en vervolgens de resultaten worden weergegeven in de console.</span><span class="sxs-lookup"><span data-stu-id="f4fa9-114">[Host06 Sample](./host06-sample.md) This sample shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span> <span data-ttu-id="f4fa9-115">Dit voorbeeld wordt bovendien de Tokenizer-API's gebruikt om op te geven van de kleur van de tekst die is ingevoerd door de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="f4fa9-115">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="see-also"></a><span data-ttu-id="f4fa9-116">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f4fa9-116">See Also</span></span>