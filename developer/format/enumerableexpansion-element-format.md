---
title: EnumerableExpansion-Element (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 93d27173-9ae4-46e5-bb78-90525915cd70
caps.latest.revision: 9
ms.openlocfilehash: bc1e58c00ca8419f9204076f0a46050281e704db
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847395"
---
# <a name="enumerableexpansion-element-format"></a><span data-ttu-id="302cc-102">Het element EnumerableExpansion (opmaak)</span><span class="sxs-lookup"><span data-stu-id="302cc-102">EnumerableExpansion Element (Format)</span></span>

<span data-ttu-id="302cc-103">Hiermee definieert u hoe specifieke .NET-verzameling objecten worden uitgevouwen wanneer ze worden weergegeven in een weergave.</span><span class="sxs-lookup"><span data-stu-id="302cc-103">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>

<span data-ttu-id="302cc-104">Configuratie-Element (indeling) DefaultSettings-Element (indeling) EnumerableExpansions-Element (indeling) EnumerableExpansion Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="302cc-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="302cc-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="302cc-105">Syntax</span></span>

```xml
<EnumerableExpansion>
  <EntrySelectedBy>...</EntrySelectedBy>
  <Expand>EnumOnly, CoreOnly, Both</Expand>
</EnumerableExpansion>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="302cc-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="302cc-106">Attributes and Elements</span></span>

<span data-ttu-id="302cc-107">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `EnumerableExpansion` element.</span><span class="sxs-lookup"><span data-stu-id="302cc-107">The following sections describe attributes, child elements, and the parent element of the `EnumerableExpansion` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="302cc-108">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="302cc-108">Attributes</span></span>

<span data-ttu-id="302cc-109">Geen.</span><span class="sxs-lookup"><span data-stu-id="302cc-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="302cc-110">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="302cc-110">Child Elements</span></span>

|<span data-ttu-id="302cc-111">Element</span><span class="sxs-lookup"><span data-stu-id="302cc-111">Element</span></span>|<span data-ttu-id="302cc-112">Description</span><span class="sxs-lookup"><span data-stu-id="302cc-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="302cc-113">EntrySelectedBy-Element voor EnumerableExpansion (indeling)</span><span class="sxs-lookup"><span data-stu-id="302cc-113">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="302cc-114">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="302cc-114">Optional element.</span></span><br /><br /> <span data-ttu-id="302cc-115">Hiermee definieert u welke .NET verzameling objecten worden uitgebreid door deze definitie.</span><span class="sxs-lookup"><span data-stu-id="302cc-115">Defines which .NET collection objects are expanded by this definition.</span></span>|
|[<span data-ttu-id="302cc-116">Vouw Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="302cc-116">Expand Element (Format)</span></span>](./expand-element-format.md)|<span data-ttu-id="302cc-117">Hiermee geeft u op hoe het verzamelingsobject voor deze definitie is uitgevouwen.</span><span class="sxs-lookup"><span data-stu-id="302cc-117">Specifies how the collection object is expanded for this definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="302cc-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="302cc-118">Parent Elements</span></span>

|<span data-ttu-id="302cc-119">Element</span><span class="sxs-lookup"><span data-stu-id="302cc-119">Element</span></span>|<span data-ttu-id="302cc-120">Description</span><span class="sxs-lookup"><span data-stu-id="302cc-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="302cc-121">EnumerableExpansions-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="302cc-121">EnumerableExpansions Element (Format)</span></span>](./enumerableexpansions-element-format.md)|<span data-ttu-id="302cc-122">Hiermee definieert u de verschillende manieren die .NET-verzameling objecten worden uitgevouwen wanneer ze worden weergegeven in een weergave.</span><span class="sxs-lookup"><span data-stu-id="302cc-122">Defines the different ways that .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="302cc-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="302cc-123">Remarks</span></span>

<span data-ttu-id="302cc-124">Dit element wordt gebruikt om te definiëren hoe de verzameling en de objecten in de verzameling worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="302cc-124">This element is used to define how collection objects and the objects in the collection are displayed.</span></span> <span data-ttu-id="302cc-125">In dit geval een verzamelingsobject verwijst naar objecten die ondersteuning biedt voor de **System.Collections.ICollection** interface.</span><span class="sxs-lookup"><span data-stu-id="302cc-125">In this case, a collection object refers to any object that supports the  **System.Collections.ICollection** interface.</span></span>

<span data-ttu-id="302cc-126">Het standaardgedrag is om alleen de eigenschappen van de objecten in de verzameling weer te geven.</span><span class="sxs-lookup"><span data-stu-id="302cc-126">The default behavior is to display only the properties of the objects in the collection.</span></span>

## <a name="see-also"></a><span data-ttu-id="302cc-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="302cc-127">See Also</span></span>

[<span data-ttu-id="302cc-128">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="302cc-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
