---
title: TableColumnHeader-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: 15f47c97ac5d55cb76e153af86672b3ffaf176c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848627"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="7f8fc-102">Het element TableColumnHeader (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7f8fc-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="7f8fc-103">Het label, de breedte van de kolom en de uitlijning van het label voor een kolom van de tabel definieert.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="7f8fc-104">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableHeaders Element voor TableControl (indeling) TableColumnHeader-Element voor TableHeaders voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="7f8fc-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7f8fc-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7f8fc-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7f8fc-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7f8fc-106">Attributes and Elements</span></span>

<span data-ttu-id="7f8fc-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `TableColumnHeader` element.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7f8fc-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7f8fc-108">Attributes</span></span>

<span data-ttu-id="7f8fc-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7f8fc-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7f8fc-110">Child Elements</span></span>

|<span data-ttu-id="7f8fc-111">Element</span><span class="sxs-lookup"><span data-stu-id="7f8fc-111">Element</span></span>|<span data-ttu-id="7f8fc-112">Description</span><span class="sxs-lookup"><span data-stu-id="7f8fc-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7f8fc-113">Label-Element voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="7f8fc-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="7f8fc-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-114">Optional element.</span></span><br /><br /> <span data-ttu-id="7f8fc-115">Hiermee definieert u het label dat wordt weergegeven aan de bovenkant van de kolom.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="7f8fc-116">Als u geen naam opgeeft, wordt de naam van de eigenschap waarvan de waarde wordt weergegeven in de rijen gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="7f8fc-117">Breedte van Element voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="7f8fc-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="7f8fc-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-118">Required element.</span></span><br /><br /> <span data-ttu-id="7f8fc-119">Geeft de breedte (in tekens) van de kolom.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="7f8fc-120">Uitlijning-Element voor TableColumbnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="7f8fc-120">Alignment Element for TableColumbnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="7f8fc-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-121">Optional element.</span></span><br /><br /> <span data-ttu-id="7f8fc-122">Hiermee geeft u op hoe het label van de kolom wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="7f8fc-123">Als er geen uitlijning is opgegeven, wordt het label links uitgelijnd.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7f8fc-124">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7f8fc-124">Parent Elements</span></span>

|<span data-ttu-id="7f8fc-125">Element</span><span class="sxs-lookup"><span data-stu-id="7f8fc-125">Element</span></span>|<span data-ttu-id="7f8fc-126">Description</span><span class="sxs-lookup"><span data-stu-id="7f8fc-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7f8fc-127">TableHeaders-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="7f8fc-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="7f8fc-128">Hiermee definieert u de kolommen van een tabelweergave.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7f8fc-129">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7f8fc-129">Remarks</span></span>

<span data-ttu-id="7f8fc-130">Hiermee geeft u een koptekst voor elke kolom van de tabel.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="7f8fc-131">De kolommen worden weergegeven in de volgorde waarin de `TableColumnHeader` elementen worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="7f8fc-132">Een tabel moet hetzelfde aantal `TableColumnHeader` elementen als `TableRowEntry` elementen.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="7f8fc-133">De kolomkop wordt gedefinieerd hoe de tekst boven aan de tabel wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="7f8fc-134">De rij-vermeldingen definiëren welke gegevens worden weergegeven in de rijen van de tabel.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="7f8fc-135">Zie voor meer informatie over de onderdelen van een tabelweergave [tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="7f8fc-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7f8fc-136">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="7f8fc-136">Example</span></span>

<span data-ttu-id="7f8fc-137">Het volgende voorbeeld ziet u twee `TableColumnHeader` elementen.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="7f8fc-138">Het eerste element definieert een kolom waarvan de label 'Kolom 1' is, een breedte van 16 tekens heeft en waarvan de label aan de linkerkant is uitgelijnd.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="7f8fc-139">Het tweede element definieert een kolom waarvan de label "Kolom 2" is, een breedte van 10 tekens heeft en waarvan de label in de kolom wordt gecentreerd.</span><span class="sxs-lookup"><span data-stu-id="7f8fc-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
    <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="7f8fc-140">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7f8fc-140">See Also</span></span>

[<span data-ttu-id="7f8fc-141">Uitlijning-Element voor TableColumnHeader voor TableContrl (indeling)</span><span class="sxs-lookup"><span data-stu-id="7f8fc-141">Alignment Element for TableColumnHeader for TableContrl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="7f8fc-142">Het maken van een tabelweergave</span><span class="sxs-lookup"><span data-stu-id="7f8fc-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7f8fc-143">Label-Element voor TableColumnHeader voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="7f8fc-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="7f8fc-144">TableHeaders-Element voor TableControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="7f8fc-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="7f8fc-145">Breedte voor TableColumnHeader voor TableControl-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="7f8fc-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="7f8fc-146">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="7f8fc-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)