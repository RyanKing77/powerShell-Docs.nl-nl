---
title: CustomEntries-Element voor CustomControl voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cb412831-94f7-4054-b19e-32c1b14c66dd
caps.latest.revision: 11
ms.openlocfilehash: 827baacd22ef258dd9b0c8a383a23fce7d975f7f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066512"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="1507f-102">Het element CustomEntries voor CustomControl voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="1507f-102">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="1507f-103">Bevat de definities van de weergave van het aangepaste besturingselement.</span><span class="sxs-lookup"><span data-stu-id="1507f-103">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="1507f-104">De weergave van het aangepaste besturingselement moet een of meer netwerkdefinities opgeven.</span><span class="sxs-lookup"><span data-stu-id="1507f-104">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="1507f-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element (indeling) CustomEntries Element voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="1507f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1507f-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="1507f-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1507f-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="1507f-107">Attributes and Elements</span></span>

<span data-ttu-id="1507f-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomControlEntries` element.</span><span class="sxs-lookup"><span data-stu-id="1507f-108">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="1507f-109">U moet een of meer onderliggende elementen.</span><span class="sxs-lookup"><span data-stu-id="1507f-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="1507f-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1507f-110">Attributes</span></span>

<span data-ttu-id="1507f-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="1507f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1507f-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1507f-112">Child Elements</span></span>

|<span data-ttu-id="1507f-113">Element</span><span class="sxs-lookup"><span data-stu-id="1507f-113">Element</span></span>|<span data-ttu-id="1507f-114">Description</span><span class="sxs-lookup"><span data-stu-id="1507f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1507f-115">CustomEntry-Element voor CustomEntries voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="1507f-115">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="1507f-116">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="1507f-116">Required element.</span></span><br /><br /> <span data-ttu-id="1507f-117">Bevat een definitie van de weergave van het aangepaste besturingselement.</span><span class="sxs-lookup"><span data-stu-id="1507f-117">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1507f-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="1507f-118">Parent Elements</span></span>

|<span data-ttu-id="1507f-119">Element</span><span class="sxs-lookup"><span data-stu-id="1507f-119">Element</span></span>|<span data-ttu-id="1507f-120">Description</span><span class="sxs-lookup"><span data-stu-id="1507f-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1507f-121">CustomControl-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="1507f-121">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="1507f-122">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="1507f-122">Required element.</span></span><br /><br /> <span data-ttu-id="1507f-123">Hiermee definieert u een aangepast besturingselement-indeling voor de weergave.</span><span class="sxs-lookup"><span data-stu-id="1507f-123">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1507f-124">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="1507f-124">Remarks</span></span>

<span data-ttu-id="1507f-125">In de meeste gevallen een besturingselement heeft slechts één definitie die is gedefinieerd in een enkel `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="1507f-125">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="1507f-126">Het is echter mogelijk om meerdere definities als u wilt de hetzelfde besturingselement gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="1507f-126">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="1507f-127">In deze gevallen kunt u een `CustomEntry` -element voor elk object of een set van objecten.</span><span class="sxs-lookup"><span data-stu-id="1507f-127">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="1507f-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="1507f-128">See Also</span></span>

[<span data-ttu-id="1507f-129">CustomControl-Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="1507f-129">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="1507f-130">CustomEntry-Element voor CustomEntries voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="1507f-130">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="1507f-131">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="1507f-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
