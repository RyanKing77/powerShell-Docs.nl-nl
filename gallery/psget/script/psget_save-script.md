---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: Galerie, powershell, cmdlet, psget
title: Opslaan-Script
ms.openlocfilehash: 7b692d33e3f86a89505b8d37c0da4177f3dff2c2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/12/2017
---
# <a name="save-script"></a><span data-ttu-id="655b5-103">Opslaan-Script</span><span class="sxs-lookup"><span data-stu-id="655b5-103">Save-Script</span></span>

<span data-ttu-id="655b5-104">Opslaan Script cmdlet kunt u het scriptbestand bekijken door op een opgegeven locatie op te slaan.</span><span class="sxs-lookup"><span data-stu-id="655b5-104">Save-Script cmdlet lets you to review the script file by saving it to a specified location.</span></span>

## <a name="description"></a><span data-ttu-id="655b5-105">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="655b5-105">Description</span></span>

<span data-ttu-id="655b5-106">Het opgegeven script Hiermee slaat u de cmdlet opslaan-Script.</span><span class="sxs-lookup"><span data-stu-id="655b5-106">The Save-Script cmdlet saves the specified script.</span></span>

## <a name="cmdlet-syntax"></a><span data-ttu-id="655b5-107">De syntaxis van cmdlet</span><span class="sxs-lookup"><span data-stu-id="655b5-107">Cmdlet syntax</span></span>

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## <a name="cmdlet-online-help-reference"></a><span data-ttu-id="655b5-108">Verwijzing naar het online help van cmdlet</span><span class="sxs-lookup"><span data-stu-id="655b5-108">Cmdlet online help reference</span></span>

[<span data-ttu-id="655b5-109">Opslaan-Script</span><span class="sxs-lookup"><span data-stu-id="655b5-109">Save-Script</span></span>](http://go.microsoft.com/fwlink/?LinkId=619786)

## <a name="example-commands"></a><span data-ttu-id="655b5-110">Voorbeeldopdrachten</span><span class="sxs-lookup"><span data-stu-id="655b5-110">Example commands</span></span>

### <a name="example-1-save-a-script-from-a-repository"></a><span data-ttu-id="655b5-111">Voorbeeld 1: Een script uit een bibliotheek opslaan</span><span class="sxs-lookup"><span data-stu-id="655b5-111">Example 1: Save a script from a repository</span></span>
<span data-ttu-id="655b5-112">Deze opdracht slaat u de nieuwste versie van het script Fabrikam-ClientScript vanuit GalleryINT opslagplaats naar de lokale map C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="655b5-112">This command saves the latest version of the script Fabrikam-ClientScript from GalleryINT repository to the local folder C:\ScriptSharingDemo</span></span>

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### <a name="example-2-save-a-version-of-a-script-by-piping-from-the-find-script-cmdlet"></a><span data-ttu-id="655b5-113">Voorbeeld 2: Een versie van een script opslaan door piping van de cmdlet Find-Script</span><span class="sxs-lookup"><span data-stu-id="655b5-113">Example 2: Save a version of a script by piping from the Find-Script cmdlet</span></span>

<span data-ttu-id="655b5-114">De eerste opdracht Zoeken naar versie 1.5 van Fabrikam-ClientScript vanuit de opslagplaats GalleryINT en opgeslagen in de map C:\ScriptSharingDemo</span><span class="sxs-lookup"><span data-stu-id="655b5-114">The first command finds version 1.5 of Fabrikam-ClientScript from the repository GalleryINT and saves it to the folder C:\ScriptSharingDemo</span></span>

<span data-ttu-id="655b5-115">De tweede opdracht valideert de metagegevens van de opgeslagen script.</span><span class="sxs-lookup"><span data-stu-id="655b5-115">The second command validates the saved script metadata.</span></span>

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```

