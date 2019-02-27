---
title: Breedte van Element voor TableColumnHeader voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 94eb0535-8002-4f17-9a2b-4be75ec20e5c
caps.latest.revision: 18
ms.openlocfilehash: a38fcbef457e69e3ea08d25ba3a9843621036f1e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56844784"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a>Het element Breedte voor TableColumnHeader voor TableControl (opmaak)

Hiermee definieert u de breedte (in tekens) van een kolom.

Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableHeaders Element voor TableControl (indeling) TableColumnHeader Element TableHeaders voor TableControl (indeling) breedte van Element voor TableColumnHeader voor TableControl (indeling)

## <a name="syntax"></a>Syntaxis

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a>Kenmerken en elementen

De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `Width` element dat wordt gebruikt bij het definiëren van kolomkoppen.

### <a name="attributes"></a>Kenmerken

Geen.

### <a name="child-elements"></a>Onderliggende elementen

Geen.

### <a name="parent-elements"></a>Bovenliggende elementen

|Element|Description|
|-------------|-----------------|
|[TableColumnHeader-Element voor TableHeaders voor TbleControl (indeling)](./tablecolumnheader-element-format.md)|Een label, de breedte en de uitlijning van de gegevens voor een kolom van de tabel definieert.|

## <a name="text-value"></a>Tekstwaarde

Wanneer op alle mogelijke een breedte (in tekens) die groter is dan de lengte van de weergegeven waarden wilt opgeven.

## <a name="remarks"></a>Opmerkingen

Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).

## <a name="example"></a>Voorbeeld

Het volgende voorbeeld wordt een `TableColumnHeader` element waarvan u de breedte 16 tekens is.

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a>Zie ook

[Het maken van een tabelweergave](./creating-a-table-view.md)

[TableColumnHeader-Element voor TableHeader voor TableControl (indeling)](./tablecolumnheader-element-format.md)

[Schrijven van een bestand opmaak PowerShell](./writing-a-powershell-formatting-file.md)
