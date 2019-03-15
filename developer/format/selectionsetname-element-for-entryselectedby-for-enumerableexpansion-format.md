---
title: SelectionSetName-Element voor EntrySelectedBy voor EnumerableExpansion (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 936d09f2-2c48-49e8-ab2d-0c8729199a2e
caps.latest.revision: 8
ms.openlocfilehash: 8ba8931ea5e34f610878351396cad42023393ad6
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851532"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="db052-102">Het element SelectionSetName voor EntrySelectedBy voor EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="db052-102">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="db052-103">Hiermee geeft u de set met .NET-typen die door deze definitie zijn uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="db052-103">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="db052-104">Configuratie van Element (indeling) DefaultSettings-Element (indeling) EnumerableExpansions-Element (indeling) EnumerableExpansion-Element (indeling) EntrySelectedBy Element voor EnumerableExpansion (indeling) SelectionSetName-Element voor EntrySelectedBy voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="db052-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="db052-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="db052-105">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="db052-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="db052-106">Attributes and Elements</span></span>

<span data-ttu-id="db052-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="db052-107">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="db052-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="db052-108">Attributes</span></span>

<span data-ttu-id="db052-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="db052-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="db052-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="db052-110">Child Elements</span></span>

<span data-ttu-id="db052-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="db052-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="db052-112">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="db052-112">Parent Elements</span></span>

|<span data-ttu-id="db052-113">Element</span><span class="sxs-lookup"><span data-stu-id="db052-113">Element</span></span>|<span data-ttu-id="db052-114">Description</span><span class="sxs-lookup"><span data-stu-id="db052-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db052-115">EntrySelectedBy-Element voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="db052-115">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="db052-116">Hiermee definieert u de .NET-verzameling objecten die door deze definitie zijn uitgebreid.</span><span class="sxs-lookup"><span data-stu-id="db052-116">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="db052-117">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="db052-117">Text Value</span></span>

<span data-ttu-id="db052-118">Geef de naam van de selectie is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="db052-118">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="db052-119">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="db052-119">Remarks</span></span>

<span data-ttu-id="db052-120">Elke definitie moet opgeven voor een of meer namen, een selectie instellen of een selectievoorwaarde.</span><span class="sxs-lookup"><span data-stu-id="db052-120">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="db052-121">Selectiesets worden meestal gebruikt wanneer u wilt definiëren van een groep objecten die worden gebruikt in meerdere weergaven.</span><span class="sxs-lookup"><span data-stu-id="db052-121">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="db052-122">Bijvoorbeeld, als u wilt weergeven als een tabel en een lijst weergeven voor dezelfde set objecten maken.</span><span class="sxs-lookup"><span data-stu-id="db052-122">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="db052-123">Zie voor meer informatie over het definiëren van selectiesets [definiëren ingesteld van objecten voor een weergave](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="db052-123">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="db052-124">Zie ook</span><span class="sxs-lookup"><span data-stu-id="db052-124">See Also</span></span>

[<span data-ttu-id="db052-125">Selectiesets definiëren</span><span class="sxs-lookup"><span data-stu-id="db052-125">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="db052-126">EntrySelectedBy-Element voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="db052-126">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="db052-127">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="db052-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)