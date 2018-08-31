---
ms.date: 08/23/2018
keywords: PowerShell-cmdlet
title: Understanding PowerShell-pijplijnen
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: 3ee03f001668fb24ff9be1ea6ecb3817e319d0ee
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134192"
---
# <a name="understanding-pipelines"></a><span data-ttu-id="d7612-103">Inzicht in pijplijnen</span><span class="sxs-lookup"><span data-stu-id="d7612-103">Understanding pipelines</span></span>

<span data-ttu-id="d7612-104">Pijplijnen fungeert als een reeks verbonden segmenten van de pipe.</span><span class="sxs-lookup"><span data-stu-id="d7612-104">Pipelines act like a series of connected segments of pipe.</span></span> <span data-ttu-id="d7612-105">Items verplaatsen langs de pijplijn doorgegeven via elk segment.</span><span class="sxs-lookup"><span data-stu-id="d7612-105">Items moving along the pipeline pass through each segment.</span></span> <span data-ttu-id="d7612-106">Voor het maken van een pijplijn in PowerShell, u opdrachten, samen met de operator pipe verbinding maken ' | '.</span><span class="sxs-lookup"><span data-stu-id="d7612-106">To create a pipeline in PowerShell, you connect commands together with the pipe operator "|".</span></span> <span data-ttu-id="d7612-107">De uitvoer van elke opdracht wordt gebruikt als invoer voor de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="d7612-107">The output of each command is used as input to the next command.</span></span>

<span data-ttu-id="d7612-108">De notatie die wordt gebruikt voor pijplijnen is vergelijkbaar met de notatie die wordt gebruikt in andere shells.</span><span class="sxs-lookup"><span data-stu-id="d7612-108">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="d7612-109">Op het eerste gezicht deze mogelijk niet duidelijk hoe pijplijnen verschillen in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7612-109">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="d7612-110">Hoewel u tekst op het scherm ziet, geeft de PowerShell-objecten, geen tekst tussen opdrachten.</span><span class="sxs-lookup"><span data-stu-id="d7612-110">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

## <a name="the-powershell-pipeline"></a><span data-ttu-id="d7612-111">De PowerShell-pijplijn</span><span class="sxs-lookup"><span data-stu-id="d7612-111">The PowerShell pipeline</span></span>

<span data-ttu-id="d7612-112">Pijplijnen zijn weliswaar de meest waardevolle concept gebruikt in opdrachtregelinterfaces.</span><span class="sxs-lookup"><span data-stu-id="d7612-112">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="d7612-113">Wanneer u goed gebruikt, wordt pijplijnen minder moeite van het gebruik van complexe opdrachten en maken het gemakkelijker om te zien van de werkstroom voor de opdrachten.</span><span class="sxs-lookup"><span data-stu-id="d7612-113">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work for the commands.</span></span> <span data-ttu-id="d7612-114">Elke opdracht in een pijplijn (ook wel een pipeline-element genoemd) wordt de uitvoer doorgegeven aan de volgende opdracht in de pijplijn per item.</span><span class="sxs-lookup"><span data-stu-id="d7612-114">Each command in a pipeline (called a pipeline element) passes its output to the next command in the pipeline, item-by-item.</span></span> <span data-ttu-id="d7612-115">Opdrachten hebben voor het afhandelen van meer dan één item per keer niet.</span><span class="sxs-lookup"><span data-stu-id="d7612-115">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="d7612-116">Het resultaat is verlaagd resourceverbruik en de mogelijkheid om te beginnen met de uitvoer onmiddellijk aan.</span><span class="sxs-lookup"><span data-stu-id="d7612-116">The result is reduced resource consumption and the ability to begin getting the output immediately.</span></span>

<span data-ttu-id="d7612-117">Als u bijvoorbeeld de `Out-Host` cmdlet om af te dwingen van per pagina weergegeven in een uitvoer van een andere opdracht, de uitvoer er ongeveer zo uitziet net zoals de normale tekst die wordt weergegeven op het scherm, opgedeeld in pagina's:</span><span class="sxs-lookup"><span data-stu-id="d7612-117">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="d7612-118">Ook het wisselbestand minder CPU-gebruik omdat verwerking naar overgebracht de `Out-Host` cmdlet wanneer er een volledige pagina Gereed om weer te geven.</span><span class="sxs-lookup"><span data-stu-id="d7612-118">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="d7612-119">De cmdlets die worden voorafgegaan door het in de pijplijn onderbreken worden uitgevoerd totdat de volgende pagina van de uitvoer beschikbaar is.</span><span class="sxs-lookup"><span data-stu-id="d7612-119">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

<span data-ttu-id="d7612-120">Hier ziet u het verschil Windows Taakbeheer om CPU en geheugen dat wordt gebruikt door PowerShell te bewaken.</span><span class="sxs-lookup"><span data-stu-id="d7612-120">You can see the difference Windows Task Manager to monitor CPU and memory used by PowerShell.</span></span> <span data-ttu-id="d7612-121">Voer de volgende opdracht uit: `Get-ChildItem C:\\Windows -Recurse`.</span><span class="sxs-lookup"><span data-stu-id="d7612-121">Run the following command: `Get-ChildItem C:\\Windows -Recurse`.</span></span> <span data-ttu-id="d7612-122">Vergelijk de CPU- en geheugengebruik op deze opdracht: `Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging`.</span><span class="sxs-lookup"><span data-stu-id="d7612-122">Compare the CPU and memory usage to this command: `Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging`.</span></span>

## <a name="objects-in-the-pipeline"></a><span data-ttu-id="d7612-123">Objecten in de pijplijn</span><span class="sxs-lookup"><span data-stu-id="d7612-123">Objects in the pipeline</span></span>

<span data-ttu-id="d7612-124">Wanneer u een cmdlet in PowerShell uitvoert, ziet u tekstuitvoer omdat het is nodig om objecten te vertegenwoordigen als tekst in een consolevenster weergegeven.</span><span class="sxs-lookup"><span data-stu-id="d7612-124">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="d7612-125">De tekstuitvoer kan niet alle van de eigenschappen van het object uitvoer wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="d7612-125">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="d7612-126">Neem bijvoorbeeld de `Get-Location` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d7612-126">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="d7612-127">Als u `Get-Location` terwijl uw huidige locatie, de hoofdmap van station C is, ziet u de volgende uitvoer:</span><span class="sxs-lookup"><span data-stu-id="d7612-127">If you run `Get-Location` while your current location is the root of the C drive, you see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="d7612-128">De tekstuitvoer is een samenvatting van gegevens, niet een volledige weergave van het object dat wordt geretourneerd door `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="d7612-128">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="d7612-129">De kop in de uitvoer is toegevoegd door het proces dat de gegevens voor weergave op het scherm wordt opgemaakt.</span><span class="sxs-lookup"><span data-stu-id="d7612-129">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

<span data-ttu-id="d7612-130">Wanneer u de uitvoer doorsluizen naar de `Get-Member` cmdlet krijgt u informatie over het object dat wordt geretourneerd door `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="d7612-130">When you pipe the output to the `Get-Member` cmdlet you get information about the object returned by `Get-Location`.</span></span>

```powershell
PS> Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

<span data-ttu-id="d7612-131">`Get-Location` retourneert een **PathInfo** -object dat het huidige pad en andere informatie bevat.</span><span class="sxs-lookup"><span data-stu-id="d7612-131">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>