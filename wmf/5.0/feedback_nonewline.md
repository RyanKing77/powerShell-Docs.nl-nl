---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: e01f6ceea361f5a9b3de645346d0652986b6267d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685912"
---
# <a name="nonewline-parameter"></a><span data-ttu-id="9c648-102">Parameter NoNewLine</span><span class="sxs-lookup"><span data-stu-id="9c648-102">NoNewLine parameter</span></span>
<span data-ttu-id="9c648-103">**Out-File**, **toevoegen-inhoud**, en **Set-inhoud** hebben nu een nieuwe **– NoNewline** switch die gewoon een nieuwe regel na de uitvoer wordt weggelaten.</span><span class="sxs-lookup"><span data-stu-id="9c648-103">**Out-File**, **Add-Content**, and **Set-Content** now have a new **–NoNewline** switch which simply omits a new line after the output.</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
<span data-ttu-id="9c648-104">Zonder **– NoNewline** opgegeven, wordt elk fragment zou worden op een afzonderlijke regel:</span><span class="sxs-lookup"><span data-stu-id="9c648-104">Without **–NoNewline** specified, each fragment would be on a separate line:</span></span>
```powershell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```
