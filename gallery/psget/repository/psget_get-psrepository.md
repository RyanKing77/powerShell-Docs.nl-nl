---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Get-PSRepository
ms.openlocfilehash: 97279a8ed0087c835fb924991484959cd7237016
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="get-psrepository"></a><span data-ttu-id="c0580-103">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="c0580-103">Get-PSRepository</span></span>

<span data-ttu-id="c0580-104">Hiermee haalt u de geregistreerde opslagplaatsen op een computer.</span><span class="sxs-lookup"><span data-stu-id="c0580-104">Gets the registered repositories on a computer.</span></span>

## <a name="description"></a><span data-ttu-id="c0580-105">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c0580-105">Description</span></span>

<span data-ttu-id="c0580-106">De cmdlet Get-PSRepository haalt een PowerShell-module-opslagplaatsen die zijn geregistreerd voor de huidige gebruiker op een computer.</span><span class="sxs-lookup"><span data-stu-id="c0580-106">The Get-PSRepository cmdlet gets PowerShell module repositories that are registered for the current user on a computer.</span></span>

<span data-ttu-id="c0580-107">Voor elke geregistreerde opslagplaats retourneert Get-PSRepository een PSRepository-object dat kan eventueel worden doorgesluisd naar Unregister-PSRepository voor de registratie van een geregistreerde opslagplaats.</span><span class="sxs-lookup"><span data-stu-id="c0580-107">For each registered repository, Get-PSRepository returns a PSRepository object which can optionally be piped to Unregister-PSRepository for unregistering a registered repository.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="c0580-108">De syntaxis van cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0580-108">Cmdlet syntax</span></span>
```powershell
Get-Command -Name Get-PSRepository -Module PowerShellGet -Syntax
```

## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="c0580-109">Verwijzing naar het online help van cmdlet</span><span class="sxs-lookup"><span data-stu-id="c0580-109">Cmdlet online help reference</span></span>

[<span data-ttu-id="c0580-110">Get-PSRepository</span><span class="sxs-lookup"><span data-stu-id="c0580-110">Get-PSRepository</span></span>](http://go.microsoft.com/fwlink/?LinkID=517127)

## <a name="example-commands"></a><span data-ttu-id="c0580-111">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="c0580-111">Example commands</span></span>

```powershell

# Properties of Get-PSRepository returned object
Get-PSRepository PSGallery | Format-List * -Force

Name                      : PSGallery
SourceLocation            : https://www.powershellgallery.com/api/v2/
Trusted                   : False
Registered                : True
InstallationPolicy        : Untrusted
PackageManagementProvider : NuGet
PublishLocation           : https://www.powershellgallery.com/api/v2/package/
ScriptSourceLocation      : https://www.powershellgallery.com/api/v2/items/psscript/
ScriptPublishLocation     : https://www.powershellgallery.com/api/v2/package/
ProviderOptions           : {}

# Get all registered repositories
Get-PSRepository

# Get a specific registered repository
Get-PSRepository PSGallery

Name                      InstallationPolicy   SourceLocation
----                      ------------------   --------------
PSGallery                 Untrusted            https://www.powershellgallery.com/api/v2/

# Get registered repository with wildcards
Get-PSRepository *Gallery*

```