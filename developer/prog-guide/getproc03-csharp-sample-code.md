---
title: GetProc03 (C#) voorbeeldcode | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ebc0d538-69ac-43d5-837d-b6f47344fc6a
caps.latest.revision: 5
ms.openlocfilehash: 116a116a5ba5b81a77b4432a81f001cc999fe46d
ms.sourcegitcommit: f60fa420bdc81db174e6168d3aeb11371e483162
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67301360"
---
# <a name="getproc03-c-sample-code"></a><span data-ttu-id="edf4a-102">GetProc03-codevoorbeeld (C#)</span><span class="sxs-lookup"><span data-stu-id="edf4a-102">GetProc03 (C#) Sample Code</span></span>

<span data-ttu-id="edf4a-103">De volgende code toont de implementatie van een `Get-Process` cmdlet kan accepteren pipelined invoer.</span><span class="sxs-lookup"><span data-stu-id="edf4a-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="edf4a-104">Deze implementatie definieert een `Name` parameter die de invoer van de pijplijn, accepteert procesinformatie opgehaald uit de lokale computer op basis van de opgegeven namen en gebruikt vervolgens de [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_)methode als de uitvoer-mechanisme voor het verzenden van objecten aan de pijplijn.</span><span class="sxs-lookup"><span data-stu-id="edf4a-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="edf4a-105">U kunt downloaden de C# bronbestand (getprov03.cs) voor deze cmdlet Get-Proc is met behulp van de Microsoft Windows Software Development Kit voor Windows Vista en .NET Framework 3.0 Runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="edf4a-105">You can download the C# source file (getprov03.cs) for this Get-Proc cmdlet using the Microsoft Windows Software Development Kit for Windows Vista and .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="edf4a-106">Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="edf4a-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="edf4a-107">De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="edf4a-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>

## <a name="code-sample"></a><span data-ttu-id="edf4a-108">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="edf4a-108">Code Sample</span></span>

[!code-csharp[GetProcessSample03.cs](../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample03/GetProcessSample03.cs#L11-L78 "GetProcessSample03.cs")]

## <a name="see-also"></a><span data-ttu-id="edf4a-109">Zie ook</span><span class="sxs-lookup"><span data-stu-id="edf4a-109">See Also</span></span>

[<span data-ttu-id="edf4a-110">Windows PowerShell-programmeergids</span><span class="sxs-lookup"><span data-stu-id="edf4a-110">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="edf4a-111">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="edf4a-111">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
