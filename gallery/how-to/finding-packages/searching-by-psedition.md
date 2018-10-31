---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galerie, powershell, cmdlet, psgallery
title: Pakketten met compatibele PowerShell-edities
ms.openlocfilehash: e16cfb0ee30e344c9399bec2985baafc5a252fd7
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004042"
---
# <a name="packages-with-compatible-powershell-editions"></a><span data-ttu-id="2a7dd-103">Pakketten met compatibele PowerShell-edities</span><span class="sxs-lookup"><span data-stu-id="2a7dd-103">Packages with compatible PowerShell Editions</span></span>

<span data-ttu-id="2a7dd-104">Vanaf versie 5.1 is PowerShell beschikbaar in verschillende edities die staan voor verschillende functies en platformcompatibiliteit.</span><span class="sxs-lookup"><span data-stu-id="2a7dd-104">Starting with version 5.1, PowerShell is available in different editions which denote varying feature sets and platform compatibility.</span></span>

- <span data-ttu-id="2a7dd-105">**Desktop-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een volledige footprint zoals Server Core en Windows Desktop.</span><span class="sxs-lookup"><span data-stu-id="2a7dd-105">**Desktop Edition:** Built on .NET Framework and provides compatibility with scripts and modules targeting versions of PowerShell running on full footprint editions of Windows such as Server Core and Windows Desktop.</span></span>
- <span data-ttu-id="2a7dd-106">**Core-editie:** deze editie is gebaseerd op .NET Framework en biedt compatibiliteit met scripts en modules die zijn gericht op versies van PowerShell die worden uitgevoerd op edities van Windows met een verminderde footprint zoals Nano Server en Windows IoT.</span><span class="sxs-lookup"><span data-stu-id="2a7dd-106">**Core Edition:** Built on .NET Core and provides compatibility with scripts and modules targeting versions of PowerShell running on reduced footprint editions of Windows such as Nano Server and Windows IoT.</span></span>

## <a name="powershell-gallery-extracts-supported-pseditions-metadata-and-allows-you-to-filters-the-packages-compatible-for-specific-powershell-editions"></a><span data-ttu-id="2a7dd-107">PowerShell Gallery ondersteunde PSEditions metagegevens worden uitgepakt en kunt u filters de pakketten compatibel voor bepaalde PowerShell-edities</span><span class="sxs-lookup"><span data-stu-id="2a7dd-107">PowerShell Gallery extracts supported PSEditions metadata and allows you to filters the packages compatible for specific PowerShell Editions</span></span>

<span data-ttu-id="2a7dd-108">Als een pakket met compatibele PSEditions opgegeven, worden deze weergegeven als onderdeel van de PowerShell-edities op de pagina van het pakket weergeven en in de pakketten resultaten.</span><span class="sxs-lookup"><span data-stu-id="2a7dd-108">If a package has compatible PSEditions specified, they will be listed as part of 'PowerShell Editions' in the package display page and also in packages results.</span></span>

![Pagina voor item weergeven met PSEditions](../../Images/manual_package_download.png)

## <a name="search-for-packages-in-the-gallery-ui-which-works-on-powershellcore"></a><span data-ttu-id="2a7dd-110">Zoeken naar pakketten in de galerie gebruikersinterface die op PowerShellCore werkt</span><span class="sxs-lookup"><span data-stu-id="2a7dd-110">Search for packages in the gallery UI which works on PowerShellCore</span></span>

<span data-ttu-id="2a7dd-111">Codes gebruiken: Tags en "PSEdition_Desktop": "PSEdition_Core" met filters in de pakketten op PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="2a7dd-111">Use Tags:"PSEdition_Desktop" and Tags:"PSEdition_Core" to filters the packages on PowerShell Gallery.</span></span>

### <a name="use-tagspseditioncore-to-search-items-compatible-with-powershell-core-edition"></a><span data-ttu-id="2a7dd-112">Codes gebruiken: "PSEdition_Core" om te zoeken naar items die compatibel is met PowerShell Core-editie.</span><span class="sxs-lookup"><span data-stu-id="2a7dd-112">Use Tags:"PSEdition_Core" to search items compatible with PowerShell Core Edition.</span></span>

![Zoekresultaten voor items die compatibel is met Core PSEdition](../../Images/SearchResultsWithPSEditions.PNG)

### <a name="use-tagspseditiondesktop-to-search-items-compatible-with-powershell-desktop-edition"></a><span data-ttu-id="2a7dd-114">Codes gebruiken: "PSEdition_Desktop" om te zoeken naar items die compatibel is met de PowerShell-Desktop-editie.</span><span class="sxs-lookup"><span data-stu-id="2a7dd-114">Use Tags:"PSEdition_Desktop" to search items compatible with PowerShell Desktop Edition.</span></span>

![Zoekresultaten voor items die compatibel is met Desktop PSEdition](../../Images/SearchResultsWithPSEdition-Desktop.PNG)

## <a name="more-details-on-authoring-and-finding-the-packages-with-compatible-powershell-editions"></a><span data-ttu-id="2a7dd-116">Meer informatie over het ontwerpen en zoeken van de pakketten met compatibele PowerShell-edities</span><span class="sxs-lookup"><span data-stu-id="2a7dd-116">More details on authoring and finding the packages with compatible PowerShell Editions</span></span>

- [<span data-ttu-id="2a7dd-117">Modules met PSEditions</span><span class="sxs-lookup"><span data-stu-id="2a7dd-117">Modules with PSEditions</span></span>](../../concepts/module-psedition-support.md)
- [<span data-ttu-id="2a7dd-118">Scripts met PSEditions</span><span class="sxs-lookup"><span data-stu-id="2a7dd-118">Scripts with PSEditions</span></span>](../../concepts/script-psedition-support.md)
