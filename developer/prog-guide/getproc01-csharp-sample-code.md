---
title: GetProc01 (C#) voorbeeldcode | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65094bb7-1972-44b3-b8b0-5f639860b58c
caps.latest.revision: 5
ms.openlocfilehash: 32c8214935a8c9f455426b76966d8c7fb33353d4
ms.sourcegitcommit: 69abc5ad16e5dd29ddfb1853e266a4bfd1d59d59
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57430074"
---
# <a name="getproc01-c-sample-code"></a><span data-ttu-id="43d81-102">GetProc01-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="43d81-102">GetProc01 (C#) Sample Code</span></span>

<span data-ttu-id="43d81-103">De volgende code toont de uitvoering van de GetProc01 voorbeeld-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="43d81-103">The following code shows the implementation of the GetProc01 sample cmdlet.</span></span> <span data-ttu-id="43d81-104">U ziet dat de cmdlet wordt vereenvoudigd door over te laten het eigenlijke werk van het ophalen van proces aan de [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) methode.</span><span class="sxs-lookup"><span data-stu-id="43d81-104">Notice that the cmdlet is simplified by leaving the actual work of process retrieval to the [System.Diagnostics.Process.Getprocesses\*](/dotnet/api/System.Diagnostics.Process.GetProcesses) method.</span></span>

> [!NOTE]
> <span data-ttu-id="43d81-105">U kunt downloaden de C# bronbestand (getproc01.cs) voor deze cmdlet Get-Proc is met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en .NET Framework 3.0 Runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="43d81-105">You can download the C# source file (getproc01.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="43d81-106">Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="43d81-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="43d81-107">De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="43d81-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="43d81-108">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="43d81-108">Code Sample</span></span>

[!code-csharp[GetProcessSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample01/GetProcessSample01.cs#L11-L126 "GetProcessSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="43d81-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="43d81-109">See Also</span></span>

[<span data-ttu-id="43d81-110">Windows PowerShell-programmeergids</span><span class="sxs-lookup"><span data-stu-id="43d81-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="43d81-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="43d81-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)