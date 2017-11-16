---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Register PSRepository
ms.openlocfilehash: badac5dc1157bbfa79058630c5c2f260d2151bd8
ms.sourcegitcommit: 3720ce4efb6735694cfb53a1b793d949af5d1bc5
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/29/2017
---
# <a name="register-psrepository"></a><span data-ttu-id="35fb1-103">Register PSRepository</span><span class="sxs-lookup"><span data-stu-id="35fb1-103">Register-PSRepository</span></span>

<span data-ttu-id="35fb1-104">Hiermee haalt u de geregistreerde opslagplaatsen op een computer.</span><span class="sxs-lookup"><span data-stu-id="35fb1-104">Gets the registered repositories on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="35fb1-105">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="35fb1-105">Description</span></span>

<span data-ttu-id="35fb1-106">De cmdlet Register-PSRepository registreert de onlineopslagplaats voor PowerShell-modules.</span><span class="sxs-lookup"><span data-stu-id="35fb1-106">The Register-PSRepository cmdlet registers the online repository for PowerShell modules.</span></span> <span data-ttu-id="35fb1-107">Nadat een opslagplaats is geregistreerd, u ernaar kunt verwijzen vanuit de Find-Module installeren-Module en de cmdlets Publish-Module.</span><span class="sxs-lookup"><span data-stu-id="35fb1-107">After a repository is registered, you can reference it from the Find-Module, Install-Module, and Publish-Module cmdlets.</span></span> <span data-ttu-id="35fb1-108">De geregistreerde opslagplaats, wordt de standaard-opslagplaats in zoek-Module en installatie-Module.</span><span class="sxs-lookup"><span data-stu-id="35fb1-108">The registered repository becomes the default repository in Find-Module and Install-Module.</span></span> 

<span data-ttu-id="35fb1-109">Geregistreerde opslagplaatsen zijn specifiek voor een gebruiker.</span><span class="sxs-lookup"><span data-stu-id="35fb1-109">Registered repositories are user-specific.</span></span> <span data-ttu-id="35fb1-110">Ze zijn niet geregistreerd in een context van het gehele systeem.</span><span class="sxs-lookup"><span data-stu-id="35fb1-110">They are not registered in a system-wide context.</span></span>


## <a name="cmdlet-syntax"></a><span data-ttu-id="35fb1-111">De syntaxis van cmdlet</span><span class="sxs-lookup"><span data-stu-id="35fb1-111">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Register-PSRepository -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="35fb1-112">Verwijzing naar het online help van cmdlet</span><span class="sxs-lookup"><span data-stu-id="35fb1-112">Cmdlet online help reference</span></span>

[<span data-ttu-id="35fb1-113">Register PSRepository</span><span class="sxs-lookup"><span data-stu-id="35fb1-113">Register-PSRepository</span></span>](http://go.microsoft.com/fwlink/?LinkID=517129)

## <a name="example-commands"></a><span data-ttu-id="35fb1-114">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="35fb1-114">Example commands</span></span>

### <a name="register-a-powershell-repository"></a><span data-ttu-id="35fb1-115">Registreren van een PowerShell-opslagplaats</span><span class="sxs-lookup"><span data-stu-id="35fb1-115">Register a PowerShell Repository</span></span>
<span data-ttu-id="35fb1-116">U kunt PowerShellGet werken tegen interne opslagplaatsen configureren.</span><span class="sxs-lookup"><span data-stu-id="35fb1-116">You can configure PowerShellGet to work against internal repositories.</span></span> <span data-ttu-id="35fb1-117">Nadat een opslagplaats is geregistreerd, kunt u zoeken-Module en installatie-Module om hiermee te werken.</span><span class="sxs-lookup"><span data-stu-id="35fb1-117">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

```powershell
# Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation "https://www.myget.org/F/powershellgetdemo/api/v2" –InstallationPolicy Trusted

# Get all of the registered repositories
Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
PSGallery                 Untrusted            https://www.powershellgallery.com/api/v2/
DemoRepo                  Trusted              https://www.myget.org/F/powershellgetdemo/api/v2


# Search only the new repository for modules
Find-Module -Repository DemoRepo

Version    Name                                Repository           Description
-------    ----                                ----------           -----------
2.12.0.0   xActiveDirectory                    DemoRepo             The xActiveDirectory module is originally part of the Windows PowerShell Desired State Configuration (DSC) Resource Kit. This version has been modified for use in Azure. This module contains the xADD...
1.1.1      SomeModule                          DemoRepo             Module description.

# By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

# Removing a repository
Unregister-PSRepository DemoRepo
```


### <a name="register-psrepository-and-set-psrepository-cmdlets-with-script-sharing-support"></a><span data-ttu-id="35fb1-118">Register PSRepository en Set-PSRepository cmdlets met script-ondersteuning voor delen</span><span class="sxs-lookup"><span data-stu-id="35fb1-118">Register-PSRepository and Set-PSRepository cmdlets with script sharing support</span></span>

<span data-ttu-id="35fb1-119">De cmdlet Register-PSRepository gebruiken om toe te voegen de **ScriptSourceLocation** en **ScriptPublishLocation** naar de PSRepository.</span><span class="sxs-lookup"><span data-stu-id="35fb1-119">Use Register-PSRepository cmdlet to add the **ScriptSourceLocation** and **ScriptPublishLocation** to the PSRepository.</span></span>

```powershell

# Register an GalleryINT repository with Scripts and Modules support

Register-PSRepository -Name GalleryINT `
                      -SourceLocation https://customgallery.cloudapp.net `
                      -InstallationPolicy Trusted `
                      -Verbose

NuGet provider is required to continue
PowerShellGet requires NuGet provider version '2.8.5.201' or newer to interact with NuGet-based repositories. The NuGet provider must be available in 'C:\Program
Files\PackageManagement\ProviderAssemblies' or 'C:\Users\manikb\AppData\Local\PackageManagement\ProviderAssemblies'. You can also install the NuGet provider by running
'Install-PackageProvider -Name NuGet -MinimumVersion 2.8.5.201 -Force'. Do you want PowerShellGet to install and import the NuGet provider now?
[Y] Yes [N] No [S] Suspend [?] Help (default is "Y"): Y
VERBOSE: Installing NuGet provider.
VERBOSE: The specified assembly 'C:\Program Files\PackageManagement\ProviderAssemblies\nuget-anycpu.exe' is installed at top level directory. However it is recommended that the assemblies
should be installed under its ProviderName\Version folder.
VERBOSE: Installing the package 'https://oneget.org/nuget-2.8.5.201.package.swidtag'.
VERBOSE: Installed the package 'nuget' to 'C:\Program Files\PackageManagement\ProviderAssemblies\nuget\2.8.5.201\Microsoft.PackageManagement.NuGetProvider.dll'.
VERBOSE: The provider 'NuGet' has already been imported. Trying to import it again.
VERBOSE: Importing package provider 'NuGet'.
VERBOSE: Performing the operation "Register Module Repository" on target "Module Repository 'GalleryINT' (https://customgallery.cloudapp.net/) in provider 'PowerShellGet'".
VERBOSE: User did not specify the PackageManagement provider name, trying with the provider name 'NuGet'.
VERBOSE: Successfully registered the repository 'GalleryINT' with source location 'https://customgallery.cloudapp.net/api/v2/'.
VERBOSE: Repository details, Name = 'GalleryINT', Location = 'https://customgallery.cloudapp.net/api/v2/'; IsTrusted = 'True'; IsRegistered = 'True'.

# Get the registered repository details
Get-PSRepository -Name GalleryINT

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
GalleryINT                 Trusted              https://customgallery.cloudapp.net/api/v2/


Get-PSRepository -Name GalleryINT | Format-List * -Force

Name : GalleryINT
SourceLocation : https://customgallery.cloudapp.net/api/v2/
Trusted : True
Registered : True
InstallationPolicy : Trusted
PackageManagementProvider : NuGet
PublishLocation : https://customgallery.cloudapp.net/api/v2/package/
ScriptSourceLocation : https://customgallery.cloudapp.net/api/v2/items/psscript/
ScriptPublishLocation : https://customgallery.cloudapp.net/api/v2/package/
ProviderOptions : {}

```

