---
title: AccessDBProviderSample06 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 46dc0657-110f-4367-8bb6-a95dca2c5016
caps.latest.revision: 8
ms.openlocfilehash: f020f023f9a379ff8a610edb7d5dcfe207170394
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080982"
---
# <a name="accessdbprovidersample06"></a>AccessDBProviderSample06

In dit voorbeeld laat zien hoe u inhoud methoden ter ondersteuning van aanroepen naar overschrijven de `Clear-Content`, `Get-Content`, en `Set-Content` cmdlets. Deze methoden moeten worden uitgevoerd wanneer de gebruiker nodig heeft voor het beheren van de inhoud van de items in het gegevensarchief. De providerklasse in dit voorbeeld is afgeleid van de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasse en implementeert de [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.

## <a name="demonstrates"></a>Ziet u

> [!IMPORTANT]
> Uw providerklasse wordt waarschijnlijk zijn afgeleid van een van de volgende klassen en mogelijk andere provider-interfaces te implementeren:
>
> -   [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class. Zie [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) class. Zie [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.
>
> Voor meer informatie over het kiezen van welke providerklasse afgeleid op basis van de functies van resourceproviders, raadpleeg dan [het ontwerpen van uw Windows PowerShell-Provider](./provider-types.md).

In dit voorbeeld ziet u het volgende:

- Declareren de `CmdletProvider` kenmerk.

- Het definiëren van een klasse in de provider die is afgeleid van de [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) klasse en die verklaart de [ System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider) interface.

- Overschrijven de [System.Management.Automation.Provider.Icontentcmdletprovider.Clearcontent*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.ClearContent) methode voor het wijzigen van het gedrag van de `Clear-Content` cmdlet, zodat de gebruiker de inhoud uit een item te verwijderen. (In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `Clear-Content` cmdlet.)

- Overschrijven de [System.Management.Automation.Provider.Icontentcmdletprovider.Getcontentreader*](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider.GetContentReader) methode voor het wijzigen van het gedrag van de `Get-Content` cmdlet, zodat de gebruiker ophalen van de inhoud van een item. (In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `Get-Content` cmdlet.).

- Overschrijven de [Microsoft.PowerShell.Commands.Filesystemprovider.Getcontentwriter*](/dotnet/api/Microsoft.PowerShell.Commands.FileSystemProvider.GetContentWriter) methode voor het wijzigen van het gedrag van de `Set-Content` cmdlet, zodat de gebruiker de inhoud van een item bijwerken. (In dit voorbeeld wordt niet weergegeven voor het toevoegen van dynamische parameters aan de `Set-Content` cmdlet.)

## <a name="example"></a>Voorbeeld

Dit voorbeeld laat zien hoe u het overschrijven van de methoden die nodig zijn om te wissen, ophalen en de inhoud van items in een Microsoft Access-gegevens instellen.

[!code-csharp[AccessDBProviderSample06.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample06/AccessDBProviderSample06.cs#L11-L2399 "AccessDBProviderSample06.cs")]

## <a name="see-also"></a>Zie ook

[System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Het ontwerpen van uw Windows PowerShell-Provider](./provider-types.md)