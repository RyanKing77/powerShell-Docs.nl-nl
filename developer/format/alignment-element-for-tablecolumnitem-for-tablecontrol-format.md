---
title: Uitlijning-Element voor TableColumnItem voor TableControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848354"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="11a92-102">Het element Uitlijning voor TableColumnItem voor TableControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="11a92-102">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="11a92-103">Hiermee definieert u hoe de gegevens in een kolom van de rij worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="11a92-103">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="11a92-104">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) TableControl-Element (indeling) TableRowEntries-Element (indeling) TableRowEntry-Element (indeling) TableColumnItems-Element (indeling) TableColumnItem-Element (indeling) Uitlijning-Element voor TableColumnItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="11a92-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="11a92-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="11a92-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="11a92-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="11a92-106">Attributes and Elements</span></span>

<span data-ttu-id="11a92-107">De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `Alignment` element.</span><span class="sxs-lookup"><span data-stu-id="11a92-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="11a92-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="11a92-108">Attributes</span></span>

<span data-ttu-id="11a92-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="11a92-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="11a92-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="11a92-110">Child Elements</span></span>

<span data-ttu-id="11a92-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="11a92-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="11a92-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="11a92-112">Parent Elements</span></span>

|<span data-ttu-id="11a92-113">Element</span><span class="sxs-lookup"><span data-stu-id="11a92-113">Element</span></span>|<span data-ttu-id="11a92-114">Description</span><span class="sxs-lookup"><span data-stu-id="11a92-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="11a92-115">TableColumnItem-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="11a92-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="11a92-116">Een label, de breedte en de uitlijning van de gegevens voor een kolom van de tabel definieert.</span><span class="sxs-lookup"><span data-stu-id="11a92-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="11a92-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="11a92-117">Text Value</span></span>

<span data-ttu-id="11a92-118">Een van de volgende waarden opgeven.</span><span class="sxs-lookup"><span data-stu-id="11a92-118">Specify one of the following values.</span></span> <span data-ttu-id="11a92-119">(Deze waarden zijn niet hoofdlettergevoelig).</span><span class="sxs-lookup"><span data-stu-id="11a92-119">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="11a92-120">Links ploegen de gegevens die worden weergegeven in de kolom aan de linkerkant.</span><span class="sxs-lookup"><span data-stu-id="11a92-120">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="11a92-121">(Dit is de standaardwaarde als dit element is niet opgegeven.)</span><span class="sxs-lookup"><span data-stu-id="11a92-121">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="11a92-122">Juiste ploegen de gegevens die worden weergegeven in de kolom aan de rechterkant.</span><span class="sxs-lookup"><span data-stu-id="11a92-122">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="11a92-123">Center datacenters, de gegevens die worden weergegeven in de kolom.</span><span class="sxs-lookup"><span data-stu-id="11a92-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="11a92-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="11a92-124">Remarks</span></span>

<span data-ttu-id="11a92-125">Zie voor meer informatie over de onderdelen van een tabelweergave [tabelweergave](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="11a92-125">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="11a92-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="11a92-126">See Also</span></span>

[<span data-ttu-id="11a92-127">Tabelweergave</span><span class="sxs-lookup"><span data-stu-id="11a92-127">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="11a92-128">TableColumnItem-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="11a92-128">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)