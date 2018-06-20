---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 9a9bdac652512640209c20e3deb20d7abc0142c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219528"
---
# <a name="register-a-powershell-repository"></a><span data-ttu-id="4420f-102">Een PowerShell-opslagplaats registreren</span><span class="sxs-lookup"><span data-stu-id="4420f-102">Register a PowerShell Repository</span></span>
<span data-ttu-id="4420f-103">U kunt PowerShellGet interne opslagplaatsen kunnen configureren.</span><span class="sxs-lookup"><span data-stu-id="4420f-103">You can configure PowerShellGet to operate against internal repositories.</span></span> <span data-ttu-id="4420f-104">Dit wordt gedaan met behulp van de volgende toevoegingen:</span><span class="sxs-lookup"><span data-stu-id="4420f-104">This is done by using the following additions:</span></span>
- <span data-ttu-id="4420f-105">Register-PSRepository: Registreert een opslagplaats voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="4420f-105">Register-PSRepository: Registers a repository for the current user.</span></span>
- <span data-ttu-id="4420f-106">Registratie-PSRepository: Hiermee verwijdert u een geregistreerde opslagplaats voor de huidige gebruiker.</span><span class="sxs-lookup"><span data-stu-id="4420f-106">Unregister-PSRepository: Removes a registered repository for the current user.</span></span>
- <span data-ttu-id="4420f-107">Set-PSRepository: Waarden voor een geregistreerde-opslagplaats instellen.</span><span class="sxs-lookup"><span data-stu-id="4420f-107">Set-PSRepository: Set values for a registered repository.</span></span>
- <span data-ttu-id="4420f-108">Get-PSRepository: Alle geregistreerde opslagplaatsen voor de huidige gebruiker niet ophalen.</span><span class="sxs-lookup"><span data-stu-id="4420f-108">Get-PSRepository: Get all registered repositories for the current user.</span></span>

<span data-ttu-id="4420f-109">Nadat een opslagplaats is geregistreerd, kunt u zoeken-Module en installatie-Module om hiermee te werken.</span><span class="sxs-lookup"><span data-stu-id="4420f-109">After a repository is registered, you can use Find-Module and Install-Module to work with it.</span></span>

```powershell
\#Register a default repository
Register-PSRepository –Name DemoRepo –SourceLocation “https://www.myget.org/F/powershellgetdemo/api/v2” –PublishLocation “<https://www.myget.org/F/powershellgetdemo/api/v2>/package” –InstallationPolicy –Trusted

\#Get all of the registered repositories
Get-PSRepository
Name SourceLocation
---- --------------
PSGallery https://msconfiggallery.cloudapp...
DemoRepo https://www.myget.org/F/powershe...

\#Search only the new repository for modules
Find-Module -Repository DemoRepo
Repository Version Name
---------- ------- ----
DemoRepo 1.0.1 xActiveDirectory
DemoRepo 1.1.1 SomeModule

\#By default, PowerShellGet operates against all registered repositories when none is specified. In this example, the “SomeModule” module is installed from the DemoRepo.
Install-Module SomeModule

\#Removing a repository
Unregister-PSRepository DemoRepo
```
