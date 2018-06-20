---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 2d6a25908de746e296bef91e05c3d4e250aa77c9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189802"
---
# <a name="nonewline-parameter"></a><span data-ttu-id="acf4c-102">De parameter NoNewLine</span><span class="sxs-lookup"><span data-stu-id="acf4c-102">NoNewLine parameter</span></span>
<span data-ttu-id="acf4c-103">**Out-File**, **toevoegen inhoud**, en **Set inhoud** hebt nu een nieuwe **– NoNewline** switch die gewoon een nieuwe regel na de uitvoer wordt weggelaten.</span><span class="sxs-lookup"><span data-stu-id="acf4c-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="acf4c-104">Zonder **– NoNewline** opgegeven, elke fragment zou zijn op een afzonderlijke regel:</span><span class="sxs-lookup"><span data-stu-id="acf4c-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```
