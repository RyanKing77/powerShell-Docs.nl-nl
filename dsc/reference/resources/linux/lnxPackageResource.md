---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: DSC voor Linux nxPackage-Resource
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048265"
---
# <a name="dsc-for-linux-nxpackage-resource"></a><span data-ttu-id="03f59-103">DSC voor Linux nxPackage-Resource</span><span class="sxs-lookup"><span data-stu-id="03f59-103">DSC for Linux nxPackage Resource</span></span>

<span data-ttu-id="03f59-104">De **nxPackage** resource in PowerShell Desired State Configuration (DSC) biedt een mechanisme voor het beheren van pakketten op een Linux-knooppunt.</span><span class="sxs-lookup"><span data-stu-id="03f59-104">The **nxPackage** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage packages on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="03f59-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="03f59-105">Syntax</span></span>

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="03f59-106">Eigenschappen</span><span class="sxs-lookup"><span data-stu-id="03f59-106">Properties</span></span>

|  <span data-ttu-id="03f59-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="03f59-107">Property</span></span> |  <span data-ttu-id="03f59-108">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="03f59-108">Description</span></span> |
|---|---|
| <span data-ttu-id="03f59-109">Naam</span><span class="sxs-lookup"><span data-stu-id="03f59-109">Name</span></span>| <span data-ttu-id="03f59-110">De naam van het pakket waarvan u wilt om te controleren of een specifieke status.</span><span class="sxs-lookup"><span data-stu-id="03f59-110">The name of the package for which you want to ensure a specific state.</span></span>|
| <span data-ttu-id="03f59-111">Zorg ervoor dat</span><span class="sxs-lookup"><span data-stu-id="03f59-111">Ensure</span></span>| <span data-ttu-id="03f59-112">Hiermee bepaalt u of om te controleren of het pakket bestaat.</span><span class="sxs-lookup"><span data-stu-id="03f59-112">Determines whether to check if the package exists.</span></span> <span data-ttu-id="03f59-113">Deze eigenschap instellen op 'Aanwezig' om te controleren of dat het pakket bestaat.</span><span class="sxs-lookup"><span data-stu-id="03f59-113">Set this property to "Present" to ensure the package exists.</span></span> <span data-ttu-id="03f59-114">Stel deze in op 'Ontbreekt' om te controleren of dat het pakket bestaat niet.</span><span class="sxs-lookup"><span data-stu-id="03f59-114">Set it to "Absent" to ensure the package does not exist.</span></span> <span data-ttu-id="03f59-115">De standaardwaarde is 'Aanwezig'.</span><span class="sxs-lookup"><span data-stu-id="03f59-115">The default value is "Present".</span></span>|
| <span data-ttu-id="03f59-116">PackageManager</span><span class="sxs-lookup"><span data-stu-id="03f59-116">PackageManager</span></span>| <span data-ttu-id="03f59-117">Ondersteunde waarden zijn "yum", 'apt' en 'zypper'.</span><span class="sxs-lookup"><span data-stu-id="03f59-117">Supported values are "yum", "apt", and "zypper".</span></span> <span data-ttu-id="03f59-118">Hiermee geeft u de package manager te gebruiken bij het installeren van pakketten.</span><span class="sxs-lookup"><span data-stu-id="03f59-118">Specifies the package manager to use when installing packages.</span></span> <span data-ttu-id="03f59-119">Als **FilePath** is opgegeven, wordt het opgegeven pad wordt gebruikt om het pakket te installeren.</span><span class="sxs-lookup"><span data-stu-id="03f59-119">If **FilePath** is specified, the provided path will be used to install the package.</span></span> <span data-ttu-id="03f59-120">Anders wordt het pakket installeren vanuit een vooraf geconfigureerde opslagplaats Pakketbeheer gebruikt.</span><span class="sxs-lookup"><span data-stu-id="03f59-120">Otherwise, a Package Manager will be used to install the package from a pre-configured repository.</span></span> <span data-ttu-id="03f59-121">Als geen van beide **PackageManager** noch **FilePath** zijn opgegeven, de standaard package manager voor het systeem wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="03f59-121">If neither **PackageManager** nor **FilePath** are provided, the default package manager for the system will be used.</span></span>|
| <span data-ttu-id="03f59-122">FilePath</span><span class="sxs-lookup"><span data-stu-id="03f59-122">FilePath</span></span>| <span data-ttu-id="03f59-123">Het pad waar het pakket zich bevindt</span><span class="sxs-lookup"><span data-stu-id="03f59-123">The file path where the package resides</span></span>|
| <span data-ttu-id="03f59-124">PackageGroup</span><span class="sxs-lookup"><span data-stu-id="03f59-124">PackageGroup</span></span>| <span data-ttu-id="03f59-125">Als **$true**, wordt de **naam** wordt verwacht dat de naam van de groep van een pakket voor gebruik met een **PackageManager**.</span><span class="sxs-lookup"><span data-stu-id="03f59-125">If **$true**, the **Name** is expected to be the name of a package group for use with a **PackageManager**.</span></span> <span data-ttu-id="03f59-126">**PacakgeGroup** is niet geldig bij het opgeven van een **FilePath**.</span><span class="sxs-lookup"><span data-stu-id="03f59-126">**PacakgeGroup** is not valid when providing a **FilePath**.</span></span>|
| <span data-ttu-id="03f59-127">Argumenten</span><span class="sxs-lookup"><span data-stu-id="03f59-127">Arguments</span></span>| <span data-ttu-id="03f59-128">Een tekenreeks van de argumenten die worden doorgegeven aan het pakket precies hetzelfde als de opgegeven.</span><span class="sxs-lookup"><span data-stu-id="03f59-128">A string of arguments that will be passed to the package exactly as provided.</span></span>|
| <span data-ttu-id="03f59-129">ReturnCode</span><span class="sxs-lookup"><span data-stu-id="03f59-129">ReturnCode</span></span>| <span data-ttu-id="03f59-130">De verwachte retourcode.</span><span class="sxs-lookup"><span data-stu-id="03f59-130">The expected return code.</span></span> <span data-ttu-id="03f59-131">Als de werkelijke retourcode komt niet overeen met die zijn de verwachte waarde die hier beschikbaar zijn, dat de configuratie wordt een fout geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="03f59-131">If the actual return code does not match the expected value provided here, the configuration will return an error.</span></span>|
| <span data-ttu-id="03f59-132">DependsOn</span><span class="sxs-lookup"><span data-stu-id="03f59-132">DependsOn</span></span> | <span data-ttu-id="03f59-133">Geeft aan dat de configuratie van een andere resource uitvoeren moet voordat deze resource is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="03f59-133">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="03f59-134">Bijvoorbeeld, als de **ID** van de resource is scriptblok configuratie die u wilt uitvoeren eerst **ResourceName** en het type **ResourceType**, de syntaxis voor het gebruik van dit de eigenschap is `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="03f59-134">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="03f59-135">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="03f59-135">Example</span></span>

<span data-ttu-id="03f59-136">Het volgende voorbeeld zorgt ervoor dat het pakket met de naam 'httpd' is geïnstalleerd op een Linux-computer, met behulp van de 'Yum' package manager.</span><span class="sxs-lookup"><span data-stu-id="03f59-136">The following example ensures that the package named "httpd" is installed on a Linux computer, using the “Yum” package manager.</span></span>

```
Import-DSCResource -Module nx

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```