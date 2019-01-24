---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC-Pakketresource
ms.openlocfilehash: 9285df71a303c9a53dd50d450272575a64e962e7
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048262"
---
# <a name="dsc-package-resource"></a><span data-ttu-id="01bc8-103">DSC-Pakketresource</span><span class="sxs-lookup"><span data-stu-id="01bc8-103">DSC Package Resource</span></span>

<span data-ttu-id="01bc8-104">_Van toepassing op: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="01bc8-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="01bc8-105">De **pakket** resource in Windows PowerShell Desired State Configuration (DSC) biedt een mechanisme om te installeren of verwijderen van pakketten, zoals Windows Installer en setup.exe pakketten, op een doelknooppunt.</span><span class="sxs-lookup"><span data-stu-id="01bc8-105">The **Package** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to install or uninstall packages, such as Windows Installer and setup.exe packages, on a target node.</span></span>

## <a name="syntax"></a><span data-ttu-id="01bc8-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="01bc8-106">Syntax</span></span>

```
Package [string] #ResourceName
{
    Name = [string]
    Path = [string]
    ProductId = [string]
    [ Arguments = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ ReturnCode = [UInt32[]] ]
}
```

## <a name="properties"></a><span data-ttu-id="01bc8-107">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="01bc8-107">Properties</span></span>

| <span data-ttu-id="01bc8-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="01bc8-108">Property</span></span> | <span data-ttu-id="01bc8-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="01bc8-109">Description</span></span> |
| --- | --- |
| <span data-ttu-id="01bc8-110">Naam</span><span class="sxs-lookup"><span data-stu-id="01bc8-110">Name</span></span>| <span data-ttu-id="01bc8-111">Geeft de naam van het pakket waarvan u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="01bc8-111">Indicates the name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="01bc8-112">Pad</span><span class="sxs-lookup"><span data-stu-id="01bc8-112">Path</span></span>| <span data-ttu-id="01bc8-113">Geeft het pad waar het pakket zich bevindt.</span><span class="sxs-lookup"><span data-stu-id="01bc8-113">Indicates the path where the package resides.</span></span>|
| <span data-ttu-id="01bc8-114">product-id</span><span class="sxs-lookup"><span data-stu-id="01bc8-114">ProductId</span></span>| <span data-ttu-id="01bc8-115">Geeft de product-ID die een unieke identificatie van het pakket.</span><span class="sxs-lookup"><span data-stu-id="01bc8-115">Indicates the product ID that uniquely identifies the package.</span></span>|
| <span data-ttu-id="01bc8-116">Argumenten</span><span class="sxs-lookup"><span data-stu-id="01bc8-116">Arguments</span></span>| <span data-ttu-id="01bc8-117">Geeft een lijst van een tekenreeks van de argumenten die worden doorgegeven aan het pakket precies hetzelfde als de opgegeven.</span><span class="sxs-lookup"><span data-stu-id="01bc8-117">Lists a string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="01bc8-118">Referentie</span><span class="sxs-lookup"><span data-stu-id="01bc8-118">Credential</span></span>| <span data-ttu-id="01bc8-119">Biedt toegang tot het pakket op een externe bron.</span><span class="sxs-lookup"><span data-stu-id="01bc8-119">Provides access to the package on a remote source.</span></span> <span data-ttu-id="01bc8-120">Deze eigenschap wordt niet gebruikt om het pakket te installeren.</span><span class="sxs-lookup"><span data-stu-id="01bc8-120">This property is not used to install the package.</span></span> <span data-ttu-id="01bc8-121">Het pakket is altijd geïnstalleerd op het lokale systeem.</span><span class="sxs-lookup"><span data-stu-id="01bc8-121">The package is always installed on the local system.</span></span>|
| <span data-ttu-id="01bc8-122">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="01bc8-122">Ensure</span></span>| <span data-ttu-id="01bc8-123">Geeft aan of het pakket is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="01bc8-123">Indicates if the package is installed.</span></span> <span data-ttu-id="01bc8-124">Deze eigenschap instellen op 'Afwezig"Controleer of dat het pakket niet is geïnstalleerd (of het pakket verwijderen als deze is geïnstalleerd).</span><span class="sxs-lookup"><span data-stu-id="01bc8-124">Set this property to "Absent" to ensure the package is not installed (or uninstall the package if it is installed).</span></span> <span data-ttu-id="01bc8-125">Instellen om "" (de standaardwaarde) om te controleren of dat het pakket is geïnstalleerd.</span><span class="sxs-lookup"><span data-stu-id="01bc8-125">Set it to "Present" (the default value) to ensure the package is installed.</span></span>|
| <span data-ttu-id="01bc8-126">Logboekpad</span><span class="sxs-lookup"><span data-stu-id="01bc8-126">LogPath</span></span>| <span data-ttu-id="01bc8-127">Geeft het volledige pad waar u wilt dat de provider een logboekbestand om te installeren of verwijderen van het pakket op te slaan.</span><span class="sxs-lookup"><span data-stu-id="01bc8-127">Indicates the full path where you want the provider to save a log file to install or uninstall the package.</span></span>|
| <span data-ttu-id="01bc8-128">DependsOn</span><span class="sxs-lookup"><span data-stu-id="01bc8-128">DependsOn</span></span> | <span data-ttu-id="01bc8-129">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="01bc8-129">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="01bc8-130">Bijvoorbeeld, als de ID van de resourceconfiguratie scriptblok die u wilt uitvoeren eerst is **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van deze eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="01bc8-130">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|
| <span data-ttu-id="01bc8-131">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="01bc8-131">ReturnCode</span></span>| <span data-ttu-id="01bc8-132">Geeft aan dat de verwachte retourcode.</span><span class="sxs-lookup"><span data-stu-id="01bc8-132">Indicates the expected return code.</span></span> <span data-ttu-id="01bc8-133">Als de werkelijke retourcode komt niet overeen met die zijn de verwachte waarde die hier beschikbaar zijn, dat de configuratie wordt een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="01bc8-133">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|

## <a name="example"></a><span data-ttu-id="01bc8-134">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="01bc8-134">Example</span></span>

<span data-ttu-id="01bc8-135">Het volgende voorbeeld wordt het MSI-installatieprogramma dat zich bevindt in het opgegeven pad en de opgegeven product-id heeft.</span><span class="sxs-lookup"><span data-stu-id="01bc8-135">This example runs the .msi installer that is located at the specified path and has the specified product ID.</span></span>

```powershell
Configuration PackageTest
{
    Package PackageExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Path        = "$Env:SystemDrive\TestFolder\TestProject.msi"
        Name        = "TestPackage"
        ProductId   = "ACDDCDAF-80C6-41E6-A1B9-8ABD8A05027E"
    }
}
```