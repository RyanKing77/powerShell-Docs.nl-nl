---
title: TypeName-Element voor EntrySelectedBy voor WideEntry (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81a91c74-6229-4b64-aa2b-9123e8b7e9e5
caps.latest.revision: 11
ms.openlocfilehash: be35f6e9e2ad0b2d9a21a91c053aa0f70cafaf9c
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083923"
---
# <a name="typename-element-for-entryselectedby-for-wideentry-format"></a>Het element TypeName voor EntrySelectedBy voor WideEntry (opmaak)

Hiermee geeft u een .NET-type voor de definitie. De definitie wordt gebruikt wanneer dit object wordt weergegeven.

Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) WideControl-Element (indeling) WideEntries-Element (indeling) WideEntry-Element (indeling) EntrySelectedBy Element voor WideEntry (indeling) TypeName-Element voor WideEntry ( -Indeling)

## <a name="syntax"></a>Syntaxis

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element van de `TypeName` element.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[EntrySelectedBy-Element voor WideEntry (indeling)](./entryselectedby-element-for-wideentry-format.md)|Hiermee definieert u de .NET-typen die gebruikmaken van deze vermelding breed of de voorwaarde die moet aanwezig zijn voor dit item moet worden gebruikt.|

## <a name="text-value"></a>Tekstwaarde

Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.

## <a name="remarks"></a>Opmerkingen

Elk item wide moet opgeven voor een of meer .NET-typen, een selectie instellen of de selectievoorwaarde moet bestaan voor de definitie moet worden gebruikt.

Zie voor meer informatie over andere onderdelen van een brede weergave [het maken van een brede weergave](./creating-a-wide-view.md).

## <a name="see-also"></a>Zie ook

[Het maken van een brede weergave](./creating-a-wide-view.md)

[EntrySelectedBy-Element voor WideEntry (indeling)](./entryselectedby-element-for-wideentry-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
