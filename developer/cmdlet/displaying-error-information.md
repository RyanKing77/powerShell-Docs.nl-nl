---
title: Weergeven van informatie over de fout | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 76fcc0c1-9795-45d3-a564-40f822b657b5
caps.latest.revision: 8
ms.openlocfilehash: 4bc8666ee9053eb368402c8644558f4fe2dcc9ee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848403"
---
# <a name="displaying-error-information"></a><span data-ttu-id="f999d-102">Foutgegevens weergeven</span><span class="sxs-lookup"><span data-stu-id="f999d-102">Displaying Error Information</span></span>

<span data-ttu-id="f999d-103">In dit onderwerp worden de manieren waarop gebruikers informatie over de fout kunnen weergeven.</span><span class="sxs-lookup"><span data-stu-id="f999d-103">This topic discusses the ways in which users can display error information.</span></span>

<span data-ttu-id="f999d-104">Wanneer de cmdlet een fout optreedt, de presentatie van gegevens van de fout ziet, standaard eruit als in de volgende foutuitvoer.</span><span class="sxs-lookup"><span data-stu-id="f999d-104">When your cmdlet encounters an error, the presentation of the error information will, by default, resemble the following error output.</span></span>

```powershell
$ stop-service lanmanworkstation
You do not have sufficient permissions to stop the service Workstation.
```

<span data-ttu-id="f999d-105">Echter gebruikers fouten kunnen weergeven op categorie door in te stellen de `$ErrorView` variabele `"CategoryView"`.</span><span class="sxs-lookup"><span data-stu-id="f999d-105">However, users can view errors by category by setting the `$ErrorView` variable to `"CategoryView"`.</span></span> <span data-ttu-id="f999d-106">Categorieweergave bevat specifieke gegevens uit de foutrecord in plaats van een vrije tekst beschrijving van de fout.</span><span class="sxs-lookup"><span data-stu-id="f999d-106">Category view displays specific information from the error record rather than a free-text description of the error.</span></span> <span data-ttu-id="f999d-107">In deze weergave is handig als u hebt een lange lijst met fouten om te scannen.</span><span class="sxs-lookup"><span data-stu-id="f999d-107">This view can be useful if you have a long list of errors to scan.</span></span> <span data-ttu-id="f999d-108">In de Categorieweergave, wordt als volgt het vorige foutbericht weergegeven.</span><span class="sxs-lookup"><span data-stu-id="f999d-108">In category view, the previous error message is displayed as follows.</span></span>

```powershell
$ $ErrorView = "CategoryView"
$ stop-service lanmanworkstation
CloseError: (System.ServiceProcess.ServiceController:ServiceController) [stop-service], ServiceCommandException
```

<span data-ttu-id="f999d-109">Zie voor meer informatie over foutcategorieën [Windows PowerShell-foutrecords](./windows-powershell-error-records.md).</span><span class="sxs-lookup"><span data-stu-id="f999d-109">For more information about error categories, see [Windows PowerShell Error Records](./windows-powershell-error-records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f999d-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f999d-110">See Also</span></span>

[<span data-ttu-id="f999d-111">Windows PowerShell-foutrecords</span><span class="sxs-lookup"><span data-stu-id="f999d-111">Windows PowerShell Error Records</span></span>](./windows-powershell-error-records.md)

[<span data-ttu-id="f999d-112">Schrijven van een Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="f999d-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)