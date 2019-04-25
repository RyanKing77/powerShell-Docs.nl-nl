---
title: Codevoorbeeld AccessDbProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35540d2a-c18f-4179-b869-1a3dc5a8c1bd
caps.latest.revision: 6
ms.openlocfilehash: 01b95e18794501c2aff13d1e51b7400ae6fb8730
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081985"
---
# <a name="accessdbprovidersample01-code-sample"></a><span data-ttu-id="50be0-102">AccessDbProviderSample01-codevoorbeeld</span><span class="sxs-lookup"><span data-stu-id="50be0-102">AccessDbProviderSample01 Code Sample</span></span>

<span data-ttu-id="50be0-103">De volgende code toont de uitvoering van de Windows PowerShell-provider wordt beschreven in [het maken van een eenvoudige Windows PowerShell-Provider](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="50be0-103">The following code shows the implementation of the Windows PowerShell provider described in [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="50be0-104">Deze implementatie biedt methoden voor het starten en stoppen van de provider en hoewel geen een manier toegang tot een gegevensarchief biedt of als u wilt ophalen of instellen van de gegevens in het gegevensarchief, biedt de essentiële functionaliteit die is vereist voor alle providers.</span><span class="sxs-lookup"><span data-stu-id="50be0-104">This implementation provides methods for starting and stopping the provider, and although it does not provide a means to access a data store or to get or set the data in the data store, it does provide the basic functionality that is required by all providers.</span></span>

> [!NOTE]
> <span data-ttu-id="50be0-105">U kunt downloaden de C# bronbestand (AccessDBSampleProvider01.cs) voor deze provider met behulp van Windows Software Development Kit voor Windows Vista en Microsoft .NET Framework 3.0 Runtime-onderdelen.</span><span class="sxs-lookup"><span data-stu-id="50be0-105">You can download the C# source file (AccessDBSampleProvider01.cs) for this provider by using the Windows Software Development Kit for Windows Vista and Microsoft .NET Framework 3.0 Runtime Components.</span></span> <span data-ttu-id="50be0-106">Zie voor instructies voor het downloaden [hoe u Windows PowerShell installeren en Download de Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span><span class="sxs-lookup"><span data-stu-id="50be0-106">For download instructions, see [How to Install Windows PowerShell and Download the Windows PowerShell SDK](/powershell/developer/installing-the-windows-powershell-sdk).</span></span>
>
> <span data-ttu-id="50be0-107">De bronbestanden van de gedownloade zijn beschikbaar in de  **\<voorbeelden van PowerShell >** directory.</span><span class="sxs-lookup"><span data-stu-id="50be0-107">The downloaded source files are available in the **\<PowerShell Samples>** directory.</span></span>
>
> <span data-ttu-id="50be0-108">Zie voor meer informatie over andere Windows PowerShell-provider-implementaties, [het ontwerpen van uw Windows PowerShell-Provider](./designing-your-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="50be0-108">For more information about other Windows PowerShell provider implementations, see [Designing Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="50be0-109">Voorbeeld van code</span><span class="sxs-lookup"><span data-stu-id="50be0-109">Code Sample</span></span>

[!code-csharp[AccessDBProviderSample01.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample01/AccessDBProviderSample01.cs#L11-L30 "AccessDBProviderSample01.cs")]

## <a name="see-also"></a><span data-ttu-id="50be0-110">Zie ook</span><span class="sxs-lookup"><span data-stu-id="50be0-110">See Also</span></span>

[<span data-ttu-id="50be0-111">Windows PowerShell-programmeergids</span><span class="sxs-lookup"><span data-stu-id="50be0-111">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="50be0-112">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="50be0-112">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)