---
title: AccessDBProviderSample01 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 853b7e5d-76c1-490e-8269-0ef31ba2ff13
caps.latest.revision: 10
ms.openlocfilehash: dc1ae92af8a57d6197b595db8e098256ac444b78
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081118"
---
# <a name="accessdbprovidersample01"></a><span data-ttu-id="05ef6-102">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="05ef6-102">AccessDBProviderSample01</span></span>

<span data-ttu-id="05ef6-103">In dit voorbeeld laat zien hoe u een providerklasse die is afgeleid rechtstreeks van declareert de [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klasse.</span><span class="sxs-lookup"><span data-stu-id="05ef6-103">This sample shows how to declare a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span> <span data-ttu-id="05ef6-104">Het is hier opgenomen voor de volledigheid.</span><span class="sxs-lookup"><span data-stu-id="05ef6-104">It is included here only for completeness.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="05ef6-105">Ziet u</span><span class="sxs-lookup"><span data-stu-id="05ef6-105">Demonstrates</span></span>

> [!IMPORTANT]
> <span data-ttu-id="05ef6-106">Uw providerklasse wordt waarschijnlijk zijn afgeleid van een van de volgende klassen en mogelijk andere provider-interfaces te implementeren:</span><span class="sxs-lookup"><span data-stu-id="05ef6-106">Your provider class will most likely derive from one of the following classes and possibly implement other provider interfaces:</span></span>
>
> -   <span data-ttu-id="05ef6-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="05ef6-107">[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span> <span data-ttu-id="05ef6-108">Zie [AccessDBProviderSample03](./accessdbprovidersample03.md).</span><span class="sxs-lookup"><span data-stu-id="05ef6-108">See [AccessDBProviderSample03](./accessdbprovidersample03.md).</span></span>
> -   <span data-ttu-id="05ef6-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="05ef6-109">[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class.</span></span> <span data-ttu-id="05ef6-110">Zie [AccessDBProviderSample04](./accessdbprovidersample04.md).</span><span class="sxs-lookup"><span data-stu-id="05ef6-110">See [AccessDBProviderSample04](./accessdbprovidersample04.md).</span></span>
> -   <span data-ttu-id="05ef6-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span><span class="sxs-lookup"><span data-stu-id="05ef6-111">[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span> <span data-ttu-id="05ef6-112">Zie [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="05ef6-112">See [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>
>
> <span data-ttu-id="05ef6-113">Voor meer informatie over het kiezen van welke providerklasse afgeleid op basis van de functies van resourceproviders, raadpleeg dan [het ontwerpen van uw Windows PowerShell-Provider](./provider-types.md).</span><span class="sxs-lookup"><span data-stu-id="05ef6-113">For more information about choosing which provider class to derive from based on provider features, see [Designing Your Windows PowerShell Provider](./provider-types.md).</span></span>

<span data-ttu-id="05ef6-114">In dit voorbeeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="05ef6-114">This sample demonstrates the following:</span></span>

- <span data-ttu-id="05ef6-115">Declareren de `CmdletProvider` kenmerk.</span><span class="sxs-lookup"><span data-stu-id="05ef6-115">Declaring the `CmdletProvider` attribute.</span></span>

- <span data-ttu-id="05ef6-116">Het definiëren van een klasse in de provider die is afgeleid rechtstreeks vanuit de [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) klasse.</span><span class="sxs-lookup"><span data-stu-id="05ef6-116">Defining a provider class that derives directly from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) class.</span></span>

## <a name="example"></a><span data-ttu-id="05ef6-117">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="05ef6-117">Example</span></span>

<span data-ttu-id="05ef6-118">Dit voorbeeld laat zien hoe u een providerklasse definieert en hoe u declareert de `CmdletProvider` kenmerk.</span><span class="sxs-lookup"><span data-stu-id="05ef6-118">This sample shows how to define a provider class and how to declare the `CmdletProvider` attribute.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  /// <summary>
  /// This sample shows how to declare a provider class and how to
  /// declare the CmdletProvider attribute.
  /// </summary>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : CmdletProvider
  {
    // Add provider logic here.
  }
}
```

## <a name="see-also"></a><span data-ttu-id="05ef6-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="05ef6-119">See Also</span></span>

[<span data-ttu-id="05ef6-120">System.Management.Automation.Provider.Itemcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="05ef6-120">System.Management.Automation.Provider.Itemcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[<span data-ttu-id="05ef6-121">System.Management.Automation.Provider.Containercmdletprovider</span><span class="sxs-lookup"><span data-stu-id="05ef6-121">System.Management.Automation.Provider.Containercmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[<span data-ttu-id="05ef6-122">System.Management.Automation.Provider.Navigationcmdletprovider</span><span class="sxs-lookup"><span data-stu-id="05ef6-122">System.Management.Automation.Provider.Navigationcmdletprovider</span></span>](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[<span data-ttu-id="05ef6-123">Het ontwerpen van uw Windows PowerShell-Provider</span><span class="sxs-lookup"><span data-stu-id="05ef6-123">Designing Your Windows PowerShell Provider</span></span>](./provider-types.md)