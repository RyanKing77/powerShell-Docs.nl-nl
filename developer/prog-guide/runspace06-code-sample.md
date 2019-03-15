---
title: Codevoorbeeld RunSpace06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d71f86d5-eb62-4b16-aa95-5fd3f314ffd3
caps.latest.revision: 6
ms.openlocfilehash: d0330f082262b68486a582ed95c7a520be1e184c
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57429530"
---
# <a name="runspace06-code-sample"></a><span data-ttu-id="b2fac-102">Runspace06-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="b2fac-102">RunSpace06 Code Sample</span></span>

<span data-ttu-id="b2fac-103">Hier volgt de broncode voor het voorbeeld Runspace06 die zijn beschreven [configureren van een Runspace met behulp van een Windows PowerShell-Snap-in](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span><span class="sxs-lookup"><span data-stu-id="b2fac-103">Here is the source code for the Runspace06 sample described in [Configuring a Runspace Using a Windows PowerShell Snap-in](http://msdn.microsoft.com/en-us/a7289ee8-9732-49ee-91c7-d533e9538b83).</span></span> <span data-ttu-id="b2fac-104">Deze voorbeeldtoepassing maakt een runspace op basis van een Windows PowerShell-module, dit vervolgens gebruikt wordt om uit te voeren van een pijplijn met één opdracht.</span><span class="sxs-lookup"><span data-stu-id="b2fac-104">This sample application creates a runspace based on a Windows PowerShell snap-in, which is then used to run a pipeline with a single command.</span></span> <span data-ttu-id="b2fac-105">U doet dit door de toepassing de configuratiegegevens runspace maakt, maakt u een runspace maakt een pijplijn met één opdracht en voert de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="b2fac-105">To do this, the application creates the runspace configuration information, creates a runspace, creates a pipeline with a single command, and then executes the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="b2fac-106">U kunt downloaden de C# bronbestand (runspace06.cs) met behulp van Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3.0 Runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="b2fac-106">You can download the C# source file (runspace06.cs) by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="b2fac-107">Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="b2fac-107">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="b2fac-108">De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="b2fac-108">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b2fac-109">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="b2fac-109">Code Sample</span></span>

[!code-csharp[Runspace06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/Runspace06/Runspace06.cs#L11-L85 "Runspace06.cs")]

## <a name="see-also"></a><span data-ttu-id="b2fac-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="b2fac-110">See Also</span></span>

[<span data-ttu-id="b2fac-111">Windows PowerShell-programmeergids</span><span class="sxs-lookup"><span data-stu-id="b2fac-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="b2fac-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b2fac-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)