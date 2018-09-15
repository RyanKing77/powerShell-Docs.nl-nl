---
ms.date: 09/11/2018
contributor: JKeithB
keywords: Galerie, powershell, psgallery
title: Handmatige pakket downloaden
ms.openlocfilehash: 7d228ccea9b840e4850d03a7a2e3e1c71e11d95e
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523324"
---
# <a name="manual-package-download"></a><span data-ttu-id="67901-103">Handmatige pakket downloaden</span><span class="sxs-lookup"><span data-stu-id="67901-103">Manual Package Download</span></span>

<span data-ttu-id="67901-104">De Powershell Gallery biedt ondersteuning voor downloaden van een pakket van de website rechtstreeks, zonder gebruik van de PowerShellGet-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="67901-104">The Powershell Gallery supports downloading a package from the website directly, without using the PowerShellGet cmdlets.</span></span> <span data-ttu-id="67901-105">Het pakket worden gedownload als een NuGet-pakket (.nupkg)-bestand, dat vervolgens eenvoudig kan worden gekopieerd naar een interne opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="67901-105">The package will be downloaded as a NuGet package (.nupkg) file, which can then be easily copied to an internal repository.</span></span>

> [!NOTE]
> <span data-ttu-id="67901-106">Handmatige pakket downloaden is **niet** bedoeld als vervanging voor de cmdlet Install-Module.</span><span class="sxs-lookup"><span data-stu-id="67901-106">Manual package download is **not** intended as a replacement for the Install-Module cmdlet.</span></span>
> <span data-ttu-id="67901-107">Downloaden van het pakket wordt niet geïnstalleerd voor de module of het script.</span><span class="sxs-lookup"><span data-stu-id="67901-107">Downloading the package does not install the module or script.</span></span> <span data-ttu-id="67901-108">Afhankelijkheden zijn niet opgenomen in het NuGet-pakket gedownload.</span><span class="sxs-lookup"><span data-stu-id="67901-108">Dependencies are not included in the NuGet package downloaded.</span></span> <span data-ttu-id="67901-109">De volgende instructies zijn alleen bedoeld ter referentie opgegeven.</span><span class="sxs-lookup"><span data-stu-id="67901-109">The following instructions are provided for reference purposes only.</span></span>

## <a name="using-manual-download-to-acquire-a-package"></a><span data-ttu-id="67901-110">Gebruik van handmatig worden gedownload voor het verkrijgen van een pakket</span><span class="sxs-lookup"><span data-stu-id="67901-110">Using manual download to acquire a package</span></span>

<span data-ttu-id="67901-111">Elke pagina bevat een koppeling voor het handmatig downloaden, zoals hier wordt weergegeven:</span><span class="sxs-lookup"><span data-stu-id="67901-111">Each page has a link for Manual Download, as shown here:</span></span>

![Handmatig worden gedownload](../../Images/Manual_Item_Download.PNG)

<span data-ttu-id="67901-113">Handmatig downloaden, klikt u op **downloaden van het bestand onbewerkte nupkg**.</span><span class="sxs-lookup"><span data-stu-id="67901-113">To download manually, click on **Download the raw nupkg file**.</span></span> <span data-ttu-id="67901-114">Een kopie van het pakket gekopieerd naar de downloadmap voor uw browser met de naam van de `<name>.<version>.nupkg`.</span><span class="sxs-lookup"><span data-stu-id="67901-114">A copy of the package copied to the download folder for your browser with the name `<name>.<version>.nupkg`.</span></span>

<span data-ttu-id="67901-115">Een NuGet-pakket is een ZIP-archief met extra bestanden met informatie over de inhoud van het pakket.</span><span class="sxs-lookup"><span data-stu-id="67901-115">A NuGet package is a ZIP archive with extra files containing information about the contents of the package.</span></span> <span data-ttu-id="67901-116">Sommige browsers, zoals Internet Explorer automatisch vervangen door de `.nupkg` bestandsextensie met `.zip`.</span><span class="sxs-lookup"><span data-stu-id="67901-116">Some browsers, like Internet Explorer, automatically replace the `.nupkg` file extension with `.zip`.</span></span> <span data-ttu-id="67901-117">Wijzig om uit te breiden het pakket, de naam van de `.nupkg` van het bestand in `.zip`, indien nodig, klikt u vervolgens de inhoud uitpakken naar een lokale map.</span><span class="sxs-lookup"><span data-stu-id="67901-117">To expand the package, rename the `.nupkg` file to `.zip`, if needed, then extract the contents to a local folder.</span></span>

<span data-ttu-id="67901-118">Een NuGet-pakket-bestand bevat de volgende NuGet-specifieke elementen die geen deel uitmaken van de oorspronkelijke verpakte code:</span><span class="sxs-lookup"><span data-stu-id="67901-118">A NuGet package file includes the following NuGet-specific elements that aren't part of the original packaged code:</span></span>

- <span data-ttu-id="67901-119">Een map met de naam `_rels` -bevat een `.rels` bestand de afhankelijkheden bevat</span><span class="sxs-lookup"><span data-stu-id="67901-119">A folder named `_rels` - contains a `.rels` file that lists the dependencies</span></span>
- <span data-ttu-id="67901-120">Een map met de naam `package` -bevat de NuGet-specifieke gegevens</span><span class="sxs-lookup"><span data-stu-id="67901-120">A folder named `package` - contains the NuGet-specific data</span></span>
- <span data-ttu-id="67901-121">Een bestand met de naam `[Content_Types].xml` -beschrijving van de werking van extensies als PowerShellGet met NuGet</span><span class="sxs-lookup"><span data-stu-id="67901-121">A file named `[Content_Types].xml` - describes how extensions like PowerShellGet work with NuGet</span></span>
- <span data-ttu-id="67901-122">Een bestand met de naam `<name>.nuspec` -het grootste deel van de metagegevens bevat</span><span class="sxs-lookup"><span data-stu-id="67901-122">A file named `<name>.nuspec` - contains the bulk of the metadata</span></span>

## <a name="installing-powershell-modules-from-a-nuget-package"></a><span data-ttu-id="67901-123">PowerShell-Modules installeren vanaf een NuGet-pakket</span><span class="sxs-lookup"><span data-stu-id="67901-123">Installing PowerShell Modules from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="67901-124">Deze instructies **niet** krijgt u hetzelfde resultaat als het uitvoeren `Install-Module`.</span><span class="sxs-lookup"><span data-stu-id="67901-124">These instructions **DO NOT** give the same result as running `Install-Module`.</span></span> <span data-ttu-id="67901-125">Deze instructies te voldoen aan de minimale vereisten voldoet.</span><span class="sxs-lookup"><span data-stu-id="67901-125">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="67901-126">Ze zijn niet bedoeld als vervanging voor `Install-Module`.</span><span class="sxs-lookup"><span data-stu-id="67901-126">They are not intended to be a replacement for `Install-Module`.</span></span> <span data-ttu-id="67901-127">Sommige stappen die worden uitgevoerd door `Install-Module` zijn niet opgenomen.</span><span class="sxs-lookup"><span data-stu-id="67901-127">Some steps performed by `Install-Module` are not included.</span></span>

<span data-ttu-id="67901-128">De beste aanpak is het verwijderen van de NuGet-specifieke elementen uit de map.</span><span class="sxs-lookup"><span data-stu-id="67901-128">The easiest approach is to remove the NuGet-specific elements from the folder.</span></span> <span data-ttu-id="67901-129">Hierdoor blijft de PowerShell-code die zijn gemaakt door de auteur van het pakket.</span><span class="sxs-lookup"><span data-stu-id="67901-129">This leaves the PowerShell code created by the package author.</span></span> <span data-ttu-id="67901-130">De stappen zijn:</span><span class="sxs-lookup"><span data-stu-id="67901-130">The steps are:</span></span>

1. <span data-ttu-id="67901-131">Pak de inhoud van het NuGet-pakket naar een lokale map.</span><span class="sxs-lookup"><span data-stu-id="67901-131">Extract the contents of the NuGet package to a local folder.</span></span>
2. <span data-ttu-id="67901-132">NuGet-specifieke elementen verwijderen uit de map.</span><span class="sxs-lookup"><span data-stu-id="67901-132">Delete the NuGet-specific elements from the folder.</span></span>
3. <span data-ttu-id="67901-133">Wijzig de naam van de map.</span><span class="sxs-lookup"><span data-stu-id="67901-133">Rename the folder.</span></span> <span data-ttu-id="67901-134">De standaardnaam van de map is meestal `<name>.<version>`.</span><span class="sxs-lookup"><span data-stu-id="67901-134">The default folder name is usually `<name>.<version>`.</span></span> <span data-ttu-id="67901-135">De versie kan bevatten "-prerelease ' als de module is gemarkeerd als een prerelease-versie.</span><span class="sxs-lookup"><span data-stu-id="67901-135">The version can include "-prerelease" if the module is tagged as a prerelease version.</span></span> <span data-ttu-id="67901-136">Wijzig de naam van de map tot alleen de modulenaam.</span><span class="sxs-lookup"><span data-stu-id="67901-136">Rename the folder to just the module name.</span></span> <span data-ttu-id="67901-137">Bijvoorbeeld, wordt 'azurerm.storage.5.0.4-preview' 'azurerm.storage'.</span><span class="sxs-lookup"><span data-stu-id="67901-137">For example, "azurerm.storage.5.0.4-preview" becomes "azurerm.storage".</span></span>
4. <span data-ttu-id="67901-138">Kopieer de map naar uw PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="67901-138">Copy the folder to your PSModulePath.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="67901-139">Bevat geen eventuele afhankelijkheden vereist door de module voor het handmatig worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="67901-139">The manual download does not include any dependencies required by the module.</span></span> <span data-ttu-id="67901-140">Als het pakket afhankelijkheden heeft, moeten ze worden geïnstalleerd op het systeem voor deze module correct te laten werken.</span><span class="sxs-lookup"><span data-stu-id="67901-140">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="67901-141">De PowerShell-galerie bevat alle afhankelijkheden die zijn vereist voor het pakket.</span><span class="sxs-lookup"><span data-stu-id="67901-141">The PowerShell Gallery shows all dependencies required by the package.</span></span>

## <a name="installing-powershell-scripts-from-a-nuget-package"></a><span data-ttu-id="67901-142">PowerShell-Scripts van een NuGet-pakket installeren</span><span class="sxs-lookup"><span data-stu-id="67901-142">Installing PowerShell Scripts from a NuGet package</span></span>

> [!NOTE]
> <span data-ttu-id="67901-143">Deze instructies **niet** krijgt u hetzelfde resultaat als het uitvoeren `Install-Script`.</span><span class="sxs-lookup"><span data-stu-id="67901-143">These instructions **DO NOT** give the same result as running `Install-Script`.</span></span> <span data-ttu-id="67901-144">Deze instructies te voldoen aan de minimale vereisten voldoet.</span><span class="sxs-lookup"><span data-stu-id="67901-144">These instructions fulfill the minimum requirements.</span></span> <span data-ttu-id="67901-145">Ze zijn niet bedoeld als vervanging voor `Install-Script`.</span><span class="sxs-lookup"><span data-stu-id="67901-145">They are not intended to be a replacement for `Install-Script`.</span></span>

<span data-ttu-id="67901-146">De eenvoudigste methode is rechtstreeks en gebruik het script vervolgens uitpakken het NuGet-pakket.</span><span class="sxs-lookup"><span data-stu-id="67901-146">The easiest approach is to extract the NuGet package, then use the script directly.</span></span> <span data-ttu-id="67901-147">De stappen zijn:</span><span class="sxs-lookup"><span data-stu-id="67901-147">The steps are:</span></span>

1. <span data-ttu-id="67901-148">Pak de inhoud van het NuGet-pakket.</span><span class="sxs-lookup"><span data-stu-id="67901-148">Extract the contents of the NuGet package.</span></span>
2. <span data-ttu-id="67901-149">De `.PS1` bestand in de map rechtstreeks vanaf deze locatie kan worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="67901-149">The `.PS1` file in the folder can be used directly from this location.</span></span>
3. <span data-ttu-id="67901-150">U kunt de NuGet-specifieke elementen in de map verwijderen.</span><span class="sxs-lookup"><span data-stu-id="67901-150">You may delete the NuGet-specific elements in the folder.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="67901-151">Bevat geen eventuele afhankelijkheden vereist door de module voor het handmatig worden gedownload.</span><span class="sxs-lookup"><span data-stu-id="67901-151">The manual download does not include any dependencies required by the module.</span></span> <span data-ttu-id="67901-152">Als het pakket afhankelijkheden heeft, moeten ze worden geïnstalleerd op het systeem voor deze module correct te laten werken.</span><span class="sxs-lookup"><span data-stu-id="67901-152">If the package has dependencies, they must be installed on the system for this module to work correctly.</span></span> <span data-ttu-id="67901-153">De PowerShell-galerie bevat alle afhankelijkheden die zijn vereist voor het pakket.</span><span class="sxs-lookup"><span data-stu-id="67901-153">The PowerShell Gallery shows all dependencies required by the package.</span></span>