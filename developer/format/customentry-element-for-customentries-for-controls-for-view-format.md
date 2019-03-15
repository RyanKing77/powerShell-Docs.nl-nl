---
title: CustomEntry-Element voor CustomEntries voor besturingselementen voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c6739205-2bc9-4507-b2af-d19d548c2057
caps.latest.revision: 6
ms.openlocfilehash: b92b99d88992cf13dbf7bfbe88aad603615f3138
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848753"
---
# <a name="customentry-element-for-customentries-for-controls-for-view-format"></a><span data-ttu-id="ea845-102">Het element CustomEntry voor CustomEntries voor Besturingselementen voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="ea845-102">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

<span data-ttu-id="ea845-103">Bevat een definitie van het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="ea845-103">Provides a definition of the control.</span></span> <span data-ttu-id="ea845-104">Dit element wordt gebruikt bij het definiëren van besturingselementen die kunnen worden gebruikt door een weergave.</span><span class="sxs-lookup"><span data-stu-id="ea845-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="ea845-105">Configuratie-Element (indeling) ViewDefinitions-Element (indeling) weergave-Element (indeling) besturingselementen Element (indeling) controle-Element voor besturingselementen voor weergave (indeling) CustomControl Element voor de controle voor besturingselementen voor weergave (indeling) CustomEntries Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ea845-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ea845-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="ea845-106">Syntax</span></span>

```xml
<CustomEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <CustomItem>...</CustomItem>
</CustomEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ea845-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="ea845-107">Attributes and Elements</span></span>

<span data-ttu-id="ea845-108">De volgende secties beschrijven kenmerken, onderliggende elementen en de bovenliggende elementen van de `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="ea845-108">The following sections describe attributes, child elements, and the parent elements of the `CustomEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ea845-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="ea845-109">Attributes</span></span>

<span data-ttu-id="ea845-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="ea845-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ea845-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ea845-111">Child Elements</span></span>

|<span data-ttu-id="ea845-112">Element</span><span class="sxs-lookup"><span data-stu-id="ea845-112">Element</span></span>|<span data-ttu-id="ea845-113">Description</span><span class="sxs-lookup"><span data-stu-id="ea845-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ea845-114">EntrySelectedBy-Element voor CustomEntry voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ea845-114">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="ea845-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="ea845-115">Optional element.</span></span><br /><br /> <span data-ttu-id="ea845-116">Hiermee definieert u de .NET-typen die gebruikmaken van de besturingselementdefinitie van dit of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="ea845-116">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="ea845-117">CustomItem-Element voor CustomEntry voor besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ea845-117">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>](./customitem-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="ea845-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="ea845-118">Required element.</span></span><br /><br /> <span data-ttu-id="ea845-119">Hiermee definieert u hoe de gegevens in het besturingselement wordt weergegeven.</span><span class="sxs-lookup"><span data-stu-id="ea845-119">Defines how the control displays the data.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ea845-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="ea845-120">Parent Elements</span></span>

|<span data-ttu-id="ea845-121">Element</span><span class="sxs-lookup"><span data-stu-id="ea845-121">Element</span></span>|<span data-ttu-id="ea845-122">Description</span><span class="sxs-lookup"><span data-stu-id="ea845-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ea845-123">CustomEntries-Element voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ea845-123">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="ea845-124">Bevat de definities voor het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="ea845-124">Provides the definitions for the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ea845-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="ea845-125">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="ea845-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ea845-126">See Also</span></span>

[<span data-ttu-id="ea845-127">CustomEntries-Element voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="ea845-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="ea845-128">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea845-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)