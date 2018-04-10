---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Update-ModuleManifest
ms.openlocfilehash: 45f40f753af17e82c83dbf57dea13749ba626503
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="update-modulemanifest"></a><span data-ttu-id="ceb73-103">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="ceb73-103">Update-ModuleManifest</span></span>
<span data-ttu-id="ceb73-104">Updates van een manifestbestand van de module.</span><span class="sxs-lookup"><span data-stu-id="ceb73-104">Updates a module manifest file.</span></span>

## <a name="description"></a><span data-ttu-id="ceb73-105">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ceb73-105">Description</span></span>

<span data-ttu-id="ceb73-106">Een module-manifest (.psd1)-bestand wordt bijgewerkt door de cmdlet Update-ModuleManifest.</span><span class="sxs-lookup"><span data-stu-id="ceb73-106">The Update-ModuleManifest cmdlet updates a module manifest (.psd1) file.</span></span>

### <a name="notes"></a><span data-ttu-id="ceb73-107">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ceb73-107">Notes</span></span>
    - <span data-ttu-id="ceb73-108">DscResourcesToExport wordt alleen ondersteund op de meest recente versie 5.0-PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ceb73-108">DscResourcesToExport is only supported on the latest PowerShell version 5.0.</span></span> <span data-ttu-id="ceb73-109">We niet mogelijk om te werken van het veld als u op een lagere versie van PowerShell uitvoert.</span><span class="sxs-lookup"><span data-stu-id="ceb73-109">We won’t be able to update the field if you are running on lower versions of PowerShell.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="ceb73-110">De syntaxis van cmdlet</span><span class="sxs-lookup"><span data-stu-id="ceb73-110">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Update-ModuleManifest -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="ceb73-111">Verwijzing naar het online help van cmdlet</span><span class="sxs-lookup"><span data-stu-id="ceb73-111">Cmdlet online help reference</span></span>

[<span data-ttu-id="ceb73-112">Update-ModuleManifest</span><span class="sxs-lookup"><span data-stu-id="ceb73-112">Update-ModuleManifest</span></span>](http://go.microsoft.com/fwlink/?LinkId=619311)

## <a name="example-commands"></a><span data-ttu-id="ceb73-113">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="ceb73-113">Example commands</span></span>

<span data-ttu-id="ceb73-114">Deze nieuwe cmdlet wordt gebruikt om te manifestbestand met invoer eigenschapswaarden update.</span><span class="sxs-lookup"><span data-stu-id="ceb73-114">This new cmdlet is used to help update manifest file with input property values.</span></span> <span data-ttu-id="ceb73-115">Het duurt alle parameters die nieuw ModuleManifest biedt.</span><span class="sxs-lookup"><span data-stu-id="ceb73-115">It takes all parameters that New-ModuleManifest does.</span></span>

<span data-ttu-id="ceb73-116">We merken dat veel van de module auteurs wilt opgeven '\*' in de geëxporteerde waarden zoals FunctionsToExport, CmdletsToExport, enz. Tijdens de publicatie van de module voor PowerShell Gallery, niet-opgegeven functies en opdrachten niet ingevuld correct naar de galerie.</span><span class="sxs-lookup"><span data-stu-id="ceb73-116">We notice that a lot of module authors would like to specify “\*” in exported values such as FunctionsToExport, CmdletsToExport, etc. During module publishing to PowerShell Gallery, unspecified functions and commands will not be populated properly onto the Gallery.</span></span> <span data-ttu-id="ceb73-117">Daarom raden we module auteurs update hun manifesten met de juiste waarden.</span><span class="sxs-lookup"><span data-stu-id="ceb73-117">Therefore, we suggest module authors update their manifests with proper values.</span></span>

<span data-ttu-id="ceb73-118">Als u hebt de modules die eigenschappen hebt geëxporteerd, vult Update ModuleManifest in het opgegeven manifestbestand met gegevens van geëxporteerde functies, -cmdlets, variabelen enzovoort:</span><span class="sxs-lookup"><span data-stu-id="ceb73-118">If you have modules that have exported properties, Update-ModuleManifest will fill the specified manifest file with information from exported functions, cmdlets, variables etc:</span></span>
```powershell
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'

#(Other properties removed here for Simplicity…)

# Functions to export from this module
FunctionsToExport = '*'
# Cmdlets to export from this module
CmdletsToExport = '*'
# Variables to export from this module
VariablesToExport = '*'
# Aliases to export from this module
AliasesToExport = '*'
}
```

<span data-ttu-id="ceb73-119">Na de Update-ModuleManifest:</span><span class="sxs-lookup"><span data-stu-id="ceb73-119">After Update-ModuleManifest:</span></span>
```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
Get-Content -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1"
#
# Module manifest for module 'NewManifest'
#
# Generated by: author name
#
# Generated on: 11/13/2015
#
@{
# Script module or binary module file associated with this manifest.
# RootModule = ''
# Version number of this module.
ModuleVersion = '2.5'
# ID used to uniquely identify this module
GUID = '610e5c5b-dc42-4eaa-8511-ebfb44066d5e'
# Functions to export from this module
FunctionsToExport = 'Get-FooFn Get-FooWF'
# Cmdlets to export from this module
CmdletsToExport = 'Test-PSGetTestCmdlet'
}
```

<span data-ttu-id="ceb73-120">Voor elke module er zijn ook metagegevensvelden gekoppeld.</span><span class="sxs-lookup"><span data-stu-id="ceb73-120">For each module, there are also metadata fields associated with it.</span></span> <span data-ttu-id="ceb73-121">Om metagegevens correct weergegeven op PowrShell galerie, kunt u Update ModuleManifest onder PrivateData deze velden te vullen.</span><span class="sxs-lookup"><span data-stu-id="ceb73-121">In order to display metadata properly on PowrShell Gallery, you can use Update-ModuleManifest to populate those fields under PrivateData.</span></span>

```powershell
Update-ModuleManifest -Path "C:\Temp\PSGTEST-TestPackageMetadata\2.5\PSGTEST-TestPackageMetadata.psd1" -Tags "Tag1" -LicenseUri "http://license.com" -ProjectUri "http://project.com" -IconUri "http://icon.com" -ReleaseNotes "Test module"
```

<span data-ttu-id="ceb73-122">PrivateData hashtabel van de sjabloon manifestbestand heeft de volgende eigenschappen</span><span class="sxs-lookup"><span data-stu-id="ceb73-122">PrivateData hashtable from the manifest file template has the following properties</span></span>

```powershell
# Private data to pass to the module specified in RootModule/ModuleToProcess. This may also contain a PSData hashtable with additional module metadata used by PowerShell.
PrivateData = @{
    PSData = @{
        # Tags applied to this module. These help with module discovery in online galleries.
        # Tags = @()

        # A URL to the license for this module.
        # LicenseUri = ''

        # A URL to the main website for this project.
        # ProjectUri = ''

        # A URL to an icon representing this module.
        # IconUri = ''

        # ReleaseNotes of this module
        # ReleaseNotes = ''

        # External dependent modules of this module
        # ExternalModuleDependencies = ''
    } # End of PSData hashtable
} # End of PrivateData hashtable
```