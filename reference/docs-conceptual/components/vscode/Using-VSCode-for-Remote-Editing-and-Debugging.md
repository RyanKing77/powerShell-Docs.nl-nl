---
title: Met behulp van Visual Studio Code voor het externe bewerken en foutopsporing
description: Met behulp van Visual Studio Code voor het externe bewerken en foutopsporing
ms.date: 08/06/2018
ms.openlocfilehash: bab1a629a7e9dafd5957cf93025abb18b8a4f326
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655509"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a><span data-ttu-id="6fbb2-103">Met behulp van Visual Studio Code voor het externe bewerken en foutopsporing</span><span class="sxs-lookup"><span data-stu-id="6fbb2-103">Using Visual Studio Code for remote editing and debugging</span></span>

<span data-ttu-id="6fbb2-104">Bedoeld voor degenen die bekend zijn met de ISE zijn misschien herinnert u zich dat u kunt uitvoeren `psedit file.ps1` rechtstreeks vanuit de geïntegreerde console bestanden - lokale of externe - te openen in de ISE.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-104">For those of you that were familiar with the ISE, you may recall that you could run `psedit file.ps1` from the integrated console to open files - local or remote - right in the ISE.</span></span>

<span data-ttu-id="6fbb2-105">Deze functie is ook beschikbaar in de PowerShell-extensie voor VSCode als het blijkt.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-105">As it turns out, this feature is also available in the PowerShell extension for VSCode.</span></span> <span data-ttu-id="6fbb2-106">Deze handleiding wordt beschreven hoe om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-106">This guide will show you how to do it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6fbb2-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="6fbb2-107">Prerequisites</span></span>

<span data-ttu-id="6fbb2-108">Deze handleiding wordt ervan uitgegaan dat u hebt:</span><span class="sxs-lookup"><span data-stu-id="6fbb2-108">This guide assumes that you have:</span></span>

- <span data-ttu-id="6fbb2-109">een externe bron (bijvoorbeeld: een virtuele machine, een container) dat u toegang tot hebt</span><span class="sxs-lookup"><span data-stu-id="6fbb2-109">a remote resource (ex: a VM, a container) that you have access to</span></span>
- <span data-ttu-id="6fbb2-110">PowerShell die worden uitgevoerd op deze en de hostcomputer</span><span class="sxs-lookup"><span data-stu-id="6fbb2-110">PowerShell running on it and the host machine</span></span>
- <span data-ttu-id="6fbb2-111">VSCode en de PowerShell-extensie voor VSCode</span><span class="sxs-lookup"><span data-stu-id="6fbb2-111">VSCode and the PowerShell extension for VSCode</span></span>

<span data-ttu-id="6fbb2-112">Deze functie werkt op Windows PowerShell en PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-112">This feature works on Windows PowerShell and PowerShell Core.</span></span>

<span data-ttu-id="6fbb2-113">Deze functie werkt ook bij het verbinden met een externe computer via WinRM, PowerShell Direct of SSH.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-113">This feature also works when connecting to a remote machine via WinRM, PowerShell Direct, or SSH.</span></span> <span data-ttu-id="6fbb2-114">Als u wilt gebruiken van SSH, maar met behulp van Windows, bekijk dan de [Win32-versie van SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span><span class="sxs-lookup"><span data-stu-id="6fbb2-114">If you want to use SSH, but are using Windows, check out the [Win32 version of SSH](https://github.com/PowerShell/Win32-OpenSSH)!</span></span>

## <a name="lets-go"></a><span data-ttu-id="6fbb2-115">We gaan</span><span class="sxs-lookup"><span data-stu-id="6fbb2-115">Let's go</span></span>

<span data-ttu-id="6fbb2-116">In deze sectie behandelen ik externe bewerken en foutopsporing van mijn MacBook Pro op een Ubuntu-VM in Azure wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-116">In this section, I'll walk through remote editing and debugging from my MacBook Pro, to an Ubuntu VM running in Azure.</span></span> <span data-ttu-id="6fbb2-117">Ik kan niet worden met behulp van Windows, maar **het proces is identiek**.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-117">I might not be using Windows, but **the process is identical**.</span></span>

### <a name="local-file-editing-with-open-editorfile"></a><span data-ttu-id="6fbb2-118">Lokaal bestand bewerken met Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="6fbb2-118">Local file editing with Open-EditorFile</span></span>

<span data-ttu-id="6fbb2-119">Met de PowerShell-extensie voor VSCode gestart en de geïntegreerde PowerShell-Console hebt geopend, kunnen we typen `Open-EditorFile foo.ps1` of `psedit foo.ps1` lokale foo.ps1 bestand rechts in de editor te openen.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-119">With the PowerShell extension for VSCode started and the PowerShell Integrated Console opened, we can type `Open-EditorFile foo.ps1` or `psedit foo.ps1` to open the local foo.ps1 file right in the editor.</span></span>

![Open-EditorFile foo.ps1 werkt lokaal](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> <span data-ttu-id="6fbb2-121">foo.ps1 moet al bestaan.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-121">foo.ps1 must already exist.</span></span>

<span data-ttu-id="6fbb2-122">Van daaruit kunnen we:</span><span class="sxs-lookup"><span data-stu-id="6fbb2-122">From there, we can:</span></span>

<span data-ttu-id="6fbb2-123">onderbrekingspunten toevoegen aan de extra ![onderbrekingspunten rugmarge toevoegen](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span><span class="sxs-lookup"><span data-stu-id="6fbb2-123">add breakpoints to the gutter ![adding breakpoint to gutter](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)</span></span>

<span data-ttu-id="6fbb2-124">en druk op F5 om op te sporen in het PowerShell-script.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-124">and hit F5 to debug the PowerShell script.</span></span>
<span data-ttu-id="6fbb2-125">![het lokale PowerShell-script-foutopsporing](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span><span class="sxs-lookup"><span data-stu-id="6fbb2-125">![debugging the PowerShell local script](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)</span></span>

<span data-ttu-id="6fbb2-126">Tijdens het opsporen van fouten, kunt u communiceren met de console voor foutopsporing, bekijk de variabelen in het bereik aan de linkerkant en alle andere standard hulpmiddelen voor foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-126">While debugging, you can interact with the debug console, check out the variables in the scope on the left, and all the other standard debugging tools.</span></span>

### <a name="remote-file-editing-with-open-editorfile"></a><span data-ttu-id="6fbb2-127">Extern bestand bewerken met Open-EditorFile</span><span class="sxs-lookup"><span data-stu-id="6fbb2-127">Remote file editing with Open-EditorFile</span></span>

<span data-ttu-id="6fbb2-128">Nu gaan we krijgen tot externe bestand bewerken en het opsporen van fouten.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-128">Now let's get into remote file editing and debugging.</span></span> <span data-ttu-id="6fbb2-129">De stappen zijn vrijwel hetzelfde, wordt er slechts één wat die we moeten eerst doen - opgeven van onze PowerShell-sessie met de externe server.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-129">The steps are nearly the same, there's just one thing we need to do first - enter our PowerShell session to the remote server.</span></span>

<span data-ttu-id="6fbb2-130">Er is een cmdlet voor om dit te doen.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-130">There's a cmdlet for to do so.</span></span> <span data-ttu-id="6fbb2-131">Dit heet `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-131">It's called `Enter-PSSession`.</span></span>

<span data-ttu-id="6fbb2-132">De watered omlaag uitleg van de cmdlet is:</span><span class="sxs-lookup"><span data-stu-id="6fbb2-132">The watered down explanation of the cmdlet is:</span></span>

- <span data-ttu-id="6fbb2-133">`Enter-PSSession -ComputerName foo` Hiermee wordt een sessie via WinRM gestart</span><span class="sxs-lookup"><span data-stu-id="6fbb2-133">`Enter-PSSession -ComputerName foo` starts a session via WinRM</span></span>
- <span data-ttu-id="6fbb2-134">`Enter-PSSession -ContainerId foo` en `Enter-PSSession -VmId foo` een sessie via PowerShell Direct starten</span><span class="sxs-lookup"><span data-stu-id="6fbb2-134">`Enter-PSSession -ContainerId foo` and `Enter-PSSession -VmId foo` start a session via PowerShell Direct</span></span>
- <span data-ttu-id="6fbb2-135">`Enter-PSSession -HostName foo` Hiermee wordt een sessie via SSH gestart</span><span class="sxs-lookup"><span data-stu-id="6fbb2-135">`Enter-PSSession -HostName foo` starts a session via SSH</span></span>

<span data-ttu-id="6fbb2-136">Voor meer informatie over `Enter-PSSession`, bekijk de documenten [hier](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="6fbb2-136">For more info on `Enter-PSSession`, check out the docs [here](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).</span></span>

<span data-ttu-id="6fbb2-137">Ik moet gebruikmaken van SSH voor externe toegang omdat ik in Mac OS een Ubuntu-VM in Azure.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-137">I'll be using SSH for remoting since I'm going from macOS to an Ubuntu VM in Azure.</span></span>

<span data-ttu-id="6fbb2-138">Eerst in de geïntegreerde Console, gaan we onze Enter-PSSession uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-138">First, in the Integrated Console, let's run our Enter-PSSession.</span></span> <span data-ttu-id="6fbb2-139">Weet u zeker dat u in de sessie bent omdat `[something]` worden weergegeven aan de linkerkant van de opdrachtprompt.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-139">You'll know that you're in the session because `[something]` will show up to the left of your prompt.</span></span>

![De aanroep naar de Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

<span data-ttu-id="6fbb2-141">Van daaruit doen we de exacte stappen als wanneer we bezig was met het bewerken van een lokale script.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-141">From there, we can do the exact steps as if we were editing a local script.</span></span>

1. <span data-ttu-id="6fbb2-142">Voer `Open-EditorFile test.ps1` of `psedit test.ps1` openen van de externe `test.ps1` bestand ![Open-EditorFile het bestand test.ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span><span class="sxs-lookup"><span data-stu-id="6fbb2-142">Run `Open-EditorFile test.ps1` or `psedit test.ps1` to open the remote `test.ps1` file ![Open-EditorFile the test.ps1 file](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)</span></span>
2. <span data-ttu-id="6fbb2-143">Het bestand/set-onderbrekingspunten bewerken</span><span class="sxs-lookup"><span data-stu-id="6fbb2-143">Edit the file/set breakpoints</span></span> ![bewerken en onderbrekingspunten instellen](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. <span data-ttu-id="6fbb2-145">Foutopsporing (F5) het externe bestand starten</span><span class="sxs-lookup"><span data-stu-id="6fbb2-145">Start debugging (F5) the remote file</span></span>

![foutopsporing van het externe bestand](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

<span data-ttu-id="6fbb2-147">Dat is alles eenvoudig werkt dat.!</span><span class="sxs-lookup"><span data-stu-id="6fbb2-147">That's all there's to it!</span></span> <span data-ttu-id="6fbb2-148">We hopen dat deze handleiding wissen van vragen over externe foutopsporing en het bewerken van PowerShell in VSCode geholpen.</span><span class="sxs-lookup"><span data-stu-id="6fbb2-148">We hope that this guide helped clear up any questions about remote debugging and editing PowerShell in VSCode.</span></span>

<span data-ttu-id="6fbb2-149">Als u problemen hebt, kunt u problemen melden [op de GitHub-opslagplaats](http://github.com/powershell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="6fbb2-149">If you have any problems, feel free to open issues [on the GitHub repo](http://github.com/powershell/vscode-powershell).</span></span>