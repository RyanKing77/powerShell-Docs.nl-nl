---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC-Archiefresource
ms.openlocfilehash: d5ccd242d000a0907c6768f30923764be6bf20a3
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048283"
---
# <a name="dsc-archive-resource"></a><span data-ttu-id="7c7fe-103">DSC-Archiefresource</span><span class="sxs-lookup"><span data-stu-id="7c7fe-103">DSC Archive Resource</span></span>

> <span data-ttu-id="7c7fe-104">Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="7c7fe-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="7c7fe-105">De archief-resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme uit te pakken archiefbestanden (.zip) op een specifiek pad.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-105">The Archive resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to unpack archive (.zip) files at a specific path.</span></span>

## <a name="syntax"></a><span data-ttu-id="7c7fe-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7c7fe-106">Syntax</span></span>
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="7c7fe-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="7c7fe-107">Properties</span></span>

|  <span data-ttu-id="7c7fe-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="7c7fe-108">Property</span></span>  |  <span data-ttu-id="7c7fe-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7c7fe-109">Description</span></span>   |
|---|---|
| <span data-ttu-id="7c7fe-110">Bestemming</span><span class="sxs-lookup"><span data-stu-id="7c7fe-110">Destination</span></span>| <span data-ttu-id="7c7fe-111">Hiermee geeft u de locatie waar u om te controleren of de dat inhoud van het archief worden geëxtraheerd.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-111">Specifies the location where you want to ensure the archive contents are extracted.</span></span>|
| <span data-ttu-id="7c7fe-112">Pad</span><span class="sxs-lookup"><span data-stu-id="7c7fe-112">Path</span></span>| <span data-ttu-id="7c7fe-113">Hiermee geeft u het bronpad van het bestand.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-113">Specifies the source path of the archive file.</span></span>|
| <span data-ttu-id="7c7fe-114">__Controlesom__</span><span class="sxs-lookup"><span data-stu-id="7c7fe-114">__Checksum__</span></span>| <span data-ttu-id="7c7fe-115">Definieert het type te gebruiken bij het bepalen of twee bestanden hetzelfde zijn.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-115">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="7c7fe-116">Als __controlesom__ niet is opgegeven, alleen de naam van bestand of map wordt gebruikt voor de vergelijking.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-116">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="7c7fe-117">Geldige waarden zijn: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate none (standaard).</span><span class="sxs-lookup"><span data-stu-id="7c7fe-117">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, none (default).</span></span> <span data-ttu-id="7c7fe-118">Als u opgeeft __controlesom__ zonder __valideren__, mislukt de configuratie van de.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-118">If you specify __Checksum__ without __Validate__, the configuration will fail.</span></span>|
| <span data-ttu-id="7c7fe-119">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="7c7fe-119">Ensure</span></span>| <span data-ttu-id="7c7fe-120">Hiermee bepaalt u of om te controleren of de inhoud van het archief bestaat op de __bestemming__.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-120">Determines whether to check if the content of the archive exists at the __Destination__.</span></span> <span data-ttu-id="7c7fe-121">Deze eigenschap instellen op __aanwezig__ om te controleren of de inhoud bestaat.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-121">Set this property to __Present__ to ensure the contents exist.</span></span> <span data-ttu-id="7c7fe-122">Stel deze in op __afwezig__ om te controleren of ze bestaan niet.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-122">Set it to __Absent__ to ensure they do not exist.</span></span> <span data-ttu-id="7c7fe-123">De standaardwaarde is __aanwezig__.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-123">The default value is __Present__.</span></span>|
| <span data-ttu-id="7c7fe-124">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7c7fe-124">DependsOn</span></span> | <span data-ttu-id="7c7fe-125">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-125">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7c7fe-126">Bijvoorbeeld, als de ID van de resource-configuratie-scriptblok die u wilt uitvoeren eerst ResourceName en het bijbehorende type is is __ResourceType__, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-126">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="7c7fe-127">Valideren</span><span class="sxs-lookup"><span data-stu-id="7c7fe-127">Validate</span></span>| <span data-ttu-id="7c7fe-128">De controlesom-eigenschap wordt gebruikt om te bepalen of het archief overeenkomt met de handtekening.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-128">Uses the Checksum property to determine if the archive matches the signature.</span></span> <span data-ttu-id="7c7fe-129">Als u controlesom zonder te valideren opgeeft, mislukt de configuratie.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-129">If you specify Checksum without Validate, the configuration will fail.</span></span> <span data-ttu-id="7c7fe-130">Als u valideren zonder controlesom opgeeft, wordt er een SHA-256-controlesom standaard gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-130">If you specify Validate without Checksum, a SHA-256 checksum is used by default.</span></span>|
| <span data-ttu-id="7c7fe-131">Force</span><span class="sxs-lookup"><span data-stu-id="7c7fe-131">Force</span></span>| <span data-ttu-id="7c7fe-132">Bepaalde bestandsbewerkingen (zoals een bestand te overschrijven of verwijderen van een directory die is niet leeg), een fout leidt.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="7c7fe-133">Met behulp van de Force-eigenschap heeft voorrang op dergelijke fouten.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-133">Using the Force property overrides such errors.</span></span> <span data-ttu-id="7c7fe-134">De standaardwaarde is False.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-134">The default value is False.</span></span>|

## <a name="example"></a><span data-ttu-id="7c7fe-135">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="7c7fe-135">Example</span></span>

<span data-ttu-id="7c7fe-136">Het volgende voorbeeld ziet hoe u kunt de archiefresource gebruiken om ervoor te zorgen dat de inhoud van een bestand met de naam Test.zip bestaan en op een bepaalde bestemming worden geëxtraheerd.</span><span class="sxs-lookup"><span data-stu-id="7c7fe-136">The following example shows how to use the Archive resource to ensure that the contents of an archive file called Test.zip exist and are extracted at a given destination.</span></span>

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```