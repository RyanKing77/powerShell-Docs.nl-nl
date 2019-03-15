---
title: TableColumnItem-Element voor TableColumnItems voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 5d80bdd736ad540f01c5ebc1f3d31dc9bd628ba5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851301"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="ffefe-102">Het element TableColumnItem voor TableColumnItems voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ffefe-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="ffefe-103">Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="ffefe-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="ffefe-104">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries Element voor TableControl (indeling) TableRowEntry-Element voor TableRowEntries voor TableControl (indeling) TableColumnItems-Element voor TableControlEntry voor TableControl (indeling) TableColumnItem Element voor TableColumnItems voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="ffefe-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ffefe-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ffefe-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <SciptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ffefe-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ffefe-106">Attributes and Elements</span></span>

<span data-ttu-id="ffefe-107">De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `TableColumnItem` element.</span><span class="sxs-lookup"><span data-stu-id="ffefe-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ffefe-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ffefe-108">Attributes</span></span>

<span data-ttu-id="ffefe-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="ffefe-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ffefe-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ffefe-110">Child Elements</span></span>

|<span data-ttu-id="ffefe-111">Element</span><span class="sxs-lookup"><span data-stu-id="ffefe-111">Element</span></span>|<span data-ttu-id="ffefe-112">Description</span><span class="sxs-lookup"><span data-stu-id="ffefe-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ffefe-113">Uitlijning-Element voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="ffefe-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="ffefe-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="ffefe-114">Optional element.</span></span><br /><br /> <span data-ttu-id="ffefe-115">Hiermee definieert u hoe de gegevens in een kolom van de rij worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="ffefe-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="ffefe-116">FormatString-Element voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="ffefe-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="ffefe-117">Hiermee geeft u een indeling-patroon dat wordt gebruikt om de opmaak van de gegevens in de kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="ffefe-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="ffefe-118">PropertyName-Element voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="ffefe-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="ffefe-119">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="ffefe-119">Optional element.</span></span><br /><br /> <span data-ttu-id="ffefe-120">Hiermee geeft u de naam van de eigenschap waarvan de waarde wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="ffefe-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="ffefe-121">ScriptBlock-Element voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="ffefe-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="ffefe-122">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="ffefe-122">Optional element.</span></span><br /><br /> <span data-ttu-id="ffefe-123">Hiermee geeft u het script waarvan de waarde wordt weergegeven in de kolom van een rij.</span><span class="sxs-lookup"><span data-stu-id="ffefe-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ffefe-124">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ffefe-124">Parent Elements</span></span>

|<span data-ttu-id="ffefe-125">Element</span><span class="sxs-lookup"><span data-stu-id="ffefe-125">Element</span></span>|<span data-ttu-id="ffefe-126">Description</span><span class="sxs-lookup"><span data-stu-id="ffefe-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ffefe-127">TableColumnItems-Element voor TableControlEntry voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="ffefe-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="ffefe-128">Definieert de eigenschappen of scripts waarvan de waarden worden weergegeven in de rij.</span><span class="sxs-lookup"><span data-stu-id="ffefe-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ffefe-129">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ffefe-129">Remarks</span></span>

<span data-ttu-id="ffefe-130">U kunt een eigenschap van een object of een script opgeven in elke kolom van de rij.</span><span class="sxs-lookup"><span data-stu-id="ffefe-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="ffefe-131">Als er geen onderliggende elementen zijn opgegeven, wordt het item is een tijdelijke aanduiding en worden geen gegevens weergegeven.</span><span class="sxs-lookup"><span data-stu-id="ffefe-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="ffefe-132">Zie voor meer informatie over de onderdelen van een tabelweergave [het maken van een tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="ffefe-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ffefe-133">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ffefe-133">Example</span></span>

<span data-ttu-id="ffefe-134">In dit voorbeeld ziet u een `TableColumnItem` element waarin de waarde van de `Status` eigenschap van de [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span><span class="sxs-lookup"><span data-stu-id="ffefe-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="ffefe-135">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ffefe-135">See Also</span></span>

[<span data-ttu-id="ffefe-136">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="ffefe-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ffefe-137">Uitlijning-Element voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="ffefe-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="ffefe-138">TableColumnItems-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="ffefe-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="ffefe-139">FormatString-Element voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="ffefe-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="ffefe-140">PropertyName-Element voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="ffefe-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="ffefe-141">ScriptBlock-Element voor TableColumnItem voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="ffefe-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="ffefe-142">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="ffefe-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)