---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC ProcessSet-Resource
ms.openlocfilehash: 91a2d5b562864addcb8e11062916d291448bbf57
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048176"
---
# <a name="dsc-windowsprocess-resource"></a><span data-ttu-id="fb0e8-103">DSC WindowsProcess-Resource</span><span class="sxs-lookup"><span data-stu-id="fb0e8-103">DSC WindowsProcess Resource</span></span>

<span data-ttu-id="fb0e8-104">_Van toepassing op: Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="fb0e8-104">_Applies To: Windows PowerShell 5.0_</span></span>

<span data-ttu-id="fb0e8-105">De **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het configureren van processen op een doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-105">The **ProcessSet** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to configure processes on a target node.</span></span> <span data-ttu-id="fb0e8-106">Deze resource is een [samengestelde resource](../../../resources/authoringResourceComposite.md) die roept de [WindowsProcess-resource](windowsProcessResource.md) voor elke groep die is opgegeven in de `GroupName` parameter.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-106">This resource is a [composite resource](../../../resources/authoringResourceComposite.md) that calls the [WindowsProcess resource](windowsProcessResource.md) for each group specified in the `GroupName` parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="fb0e8-107">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="fb0e8-107">Syntax</span></span>

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="fb0e8-108">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="fb0e8-108">Properties</span></span>

| <span data-ttu-id="fb0e8-109">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="fb0e8-109">Property</span></span> | <span data-ttu-id="fb0e8-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fb0e8-110">Description</span></span> |
| --- | --- |
| <span data-ttu-id="fb0e8-111">Argumenten</span><span class="sxs-lookup"><span data-stu-id="fb0e8-111">Arguments</span></span>| <span data-ttu-id="fb0e8-112">Een tekenreeks met argumenten worden doorgegeven aan de proces-is.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-112">A string that contains arguments to pass to the process as-is.</span></span> <span data-ttu-id="fb0e8-113">Als u meerdere argumenten doorgeven wilt, plaatst u ze allemaal op deze tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-113">If you need to pass several arguments, put them all in this string.</span></span>|
| <span data-ttu-id="fb0e8-114">Pad</span><span class="sxs-lookup"><span data-stu-id="fb0e8-114">Path</span></span>| <span data-ttu-id="fb0e8-115">De paden naar het proces uitvoerbare bestanden.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-115">The paths to the process executables.</span></span> <span data-ttu-id="fb0e8-116">Als dit zijn de namen van de uitvoerbare bestanden (geen volledig gekwalificeerde paden), de DSC-resource wordt zoeken in de omgeving **pad** variabele (`$env:Path`) om de bestanden te zoeken.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-116">If these are the names of the executable files (not fully qualified paths), the DSC resource will search the environment **Path** variable (`$env:Path`) to find the files.</span></span> <span data-ttu-id="fb0e8-117">Als de waarden van deze eigenschap volledig gekwalificeerde paden zijn, DSC niet gebruiken de **pad** omgevingsvariabele om de bestanden te zoeken en genereert een fout als een van de paden niet bestaan.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-117">If the values of this property are fully qualified paths, DSC will not use the **Path** environment variable to find the files, and will throw an error if any of the paths do not exist.</span></span> <span data-ttu-id="fb0e8-118">Relatieve paden zijn niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-118">Relative paths are not allowed.</span></span>|
| <span data-ttu-id="fb0e8-119">Referentie</span><span class="sxs-lookup"><span data-stu-id="fb0e8-119">Credential</span></span>| <span data-ttu-id="fb0e8-120">Geeft aan dat de referenties voor het starten van het proces.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-120">Indicates the credentials for starting the process.</span></span>|
| <span data-ttu-id="fb0e8-121">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="fb0e8-121">Ensure</span></span>| <span data-ttu-id="fb0e8-122">Hiermee geeft u op of de processen bestaat.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-122">Specifies whether the processes exists.</span></span> <span data-ttu-id="fb0e8-123">Deze eigenschap instellen op 'Aanwezig' om ervoor te zorgen dat het proces bestaat.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-123">Set this property to "Present" to ensure that the process exists.</span></span> <span data-ttu-id="fb0e8-124">Anders wordt deze ingesteld op 'Ontbreekt'.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-124">Otherwise, set it to "Absent".</span></span> <span data-ttu-id="fb0e8-125">De standaardwaarde is 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-125">The default is "Present".</span></span>|
| <span data-ttu-id="fb0e8-126">StandardErrorPath</span><span class="sxs-lookup"><span data-stu-id="fb0e8-126">StandardErrorPath</span></span>| <span data-ttu-id="fb0e8-127">Het pad waarnaar de processen standaardfout schrijven.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-127">The path to which the processes write standard error.</span></span> <span data-ttu-id="fb0e8-128">Er een bestaand bestand wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-128">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="fb0e8-129">StandardInputPath</span><span class="sxs-lookup"><span data-stu-id="fb0e8-129">StandardInputPath</span></span>| <span data-ttu-id="fb0e8-130">De stroom van waaruit het proces standaard invoer ontvangt.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-130">The stream from which the process receives standard input.</span></span>|
| <span data-ttu-id="fb0e8-131">StandardOutputPath</span><span class="sxs-lookup"><span data-stu-id="fb0e8-131">StandardOutputPath</span></span>| <span data-ttu-id="fb0e8-132">Het pad van het bestand waarnaar de processen standaarduitvoer schrijven.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-132">The path of the file to which the processes write standard output.</span></span> <span data-ttu-id="fb0e8-133">Er een bestaand bestand wordt overschreven.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-133">Any existing file there will be overwritten.</span></span>|
| <span data-ttu-id="fb0e8-134">WorkingDirectory</span><span class="sxs-lookup"><span data-stu-id="fb0e8-134">WorkingDirectory</span></span>| <span data-ttu-id="fb0e8-135">De locatie die wordt gebruikt als de huidige werkmap voor de processen.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-135">The location used as the current working directory for the processes.</span></span>|
| <span data-ttu-id="fb0e8-136">DependsOn</span><span class="sxs-lookup"><span data-stu-id="fb0e8-136">DependsOn</span></span> | <span data-ttu-id="fb0e8-137">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="fb0e8-137">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="fb0e8-138">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **_ResourceType**, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"` .</span><span class="sxs-lookup"><span data-stu-id="fb0e8-138">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **_ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"` .</span></span>|