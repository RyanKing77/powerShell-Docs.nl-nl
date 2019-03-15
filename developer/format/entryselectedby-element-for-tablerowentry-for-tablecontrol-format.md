---
title: EntrySelectedBy-Element voor TableRowEntry voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: e18564c10898c73128e0a4bc7d077e7c7ffb1c22
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851238"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="f9df2-102">Het element EntrySelectedBy voor TableRowEntry voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="f9df2-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="f9df2-103">Hiermee definieert u de .NET-typen die gebruikmaken van deze definitie van de tabelweergave of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f9df2-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="f9df2-104">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries-Element (indeling) TableRowEntry-Element (indeling) EntrySelectedBy-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="f9df2-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f9df2-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="f9df2-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f9df2-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="f9df2-106">Attributes and Elements</span></span>

<span data-ttu-id="f9df2-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="f9df2-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f9df2-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="f9df2-108">Attributes</span></span>

<span data-ttu-id="f9df2-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="f9df2-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f9df2-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f9df2-110">Child Elements</span></span>

|<span data-ttu-id="f9df2-111">Element</span><span class="sxs-lookup"><span data-stu-id="f9df2-111">Element</span></span>|<span data-ttu-id="f9df2-112">Description</span><span class="sxs-lookup"><span data-stu-id="f9df2-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f9df2-113">SelectionCondition-Element voor EntrySelectedBy voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f9df2-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="f9df2-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f9df2-114">Optional element.</span></span><br /><br /> <span data-ttu-id="f9df2-115">Hiermee definieert u de voorwaarde die moet bestaan voor deze definitie voor het weergeven van tabel moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="f9df2-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="f9df2-116">SelectionSetName-Element voor EntrySelectedBy voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f9df2-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="f9df2-117">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f9df2-117">Optional element.</span></span><br /><br /> <span data-ttu-id="f9df2-118">Hiermee geeft u een set van .NET-typen die gebruikmaken van de definitie van deze tabel weergeven.</span><span class="sxs-lookup"><span data-stu-id="f9df2-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="f9df2-119">TypeName-Element voor EntrySelectedBy voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f9df2-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="f9df2-120">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="f9df2-120">Optional element.</span></span><br /><br /> <span data-ttu-id="f9df2-121">Hiermee geeft u een .NET-type dat gebruikmaakt van de definitie van deze tabel weergeven.</span><span class="sxs-lookup"><span data-stu-id="f9df2-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f9df2-122">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="f9df2-122">Parent Elements</span></span>

|<span data-ttu-id="f9df2-123">Element</span><span class="sxs-lookup"><span data-stu-id="f9df2-123">Element</span></span>|<span data-ttu-id="f9df2-124">Description</span><span class="sxs-lookup"><span data-stu-id="f9df2-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f9df2-125">TableRowEntry-Element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f9df2-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|<span data-ttu-id="f9df2-126">De gegevens die worden weergegeven in een rij van de tabel definieert.</span><span class="sxs-lookup"><span data-stu-id="f9df2-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f9df2-127">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="f9df2-127">Remarks</span></span>

<span data-ttu-id="f9df2-128">U moet ten minste één type, selectie instellen of selectievoorwaarde voor de definitie van een tabel weergeven.</span><span class="sxs-lookup"><span data-stu-id="f9df2-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="f9df2-129">Er is geen maximale limiet voor het aantal onderliggende elementen die u kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="f9df2-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="f9df2-130">Selectie voorwaarden worden gebruikt voor het definiëren van een voorwaarde die moet aanwezig zijn voor de definitie moet worden gebruikt, zoals wanneer een object een bepaalde eigenschap heeft of die een bepaalde eigenschapwaarde of een script wordt geëvalueerd als `true`.</span><span class="sxs-lookup"><span data-stu-id="f9df2-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="f9df2-131">Zie voor meer informatie over de voorwaarden van de selectie [definiëren voorwaarden voor wanneer een item weergeven of Item wordt gebruikt](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f9df2-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f9df2-132">Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f9df2-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f9df2-133">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="f9df2-133">Example</span></span>

<span data-ttu-id="f9df2-134">Het volgende voorbeeld wordt een `TableRowEntry` element dat wordt gebruikt om weer te geven van de eigenschappen van de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span><span class="sxs-lookup"><span data-stu-id="f9df2-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="f9df2-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="f9df2-135">See Also</span></span>

[<span data-ttu-id="f9df2-136">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="f9df2-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f9df2-137">SelectionCondition-Element voor EntrySelectedBy voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f9df2-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f9df2-138">SelectionSetName-Element voor EntrySelectedBy voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f9df2-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f9df2-139">TableRowEntry-Element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f9df2-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="f9df2-140">TypeName-Element voor EntrySelectedBy voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="f9df2-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="f9df2-141">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="f9df2-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)