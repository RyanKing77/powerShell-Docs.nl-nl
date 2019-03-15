---
title: SelectionCondition-Element voor EntrySelectedBy voor CustomControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848788"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="c22f3-102">Het element SelectionCondition voor EntrySelectedBy voor CustomControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="c22f3-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="c22f3-103">Hiermee definieert u een voorwaarde die moet aanwezig zijn voor de besturingselementdefinitie van een moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c22f3-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="c22f3-104">Dit element wordt gebruikt bij het definiëren van een aangepast besturingselement-weergave.</span><span class="sxs-lookup"><span data-stu-id="c22f3-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="c22f3-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) CustomControl Element voor weergave (indeling) CustomEntries-Element voor CustomControl voor weergave (indeling) CustomEntry Element voor CustomEntries voor CustomControl voor weergave ( -Indeling) CustomItem Element voor CustomEntry voor CustomControl voor weergave (indeling) EntrySelectedBy Element voor CustomEntry voor CustomControl voor weergave (indeling) SelectionCondition Element voor EntrySelectedBy voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c22f3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c22f3-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="c22f3-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c22f3-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="c22f3-107">Attributes and Elements</span></span>

<span data-ttu-id="c22f3-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="c22f3-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c22f3-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="c22f3-109">Attributes</span></span>

<span data-ttu-id="c22f3-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="c22f3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c22f3-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c22f3-111">Child Elements</span></span>

|<span data-ttu-id="c22f3-112">Element</span><span class="sxs-lookup"><span data-stu-id="c22f3-112">Element</span></span>|<span data-ttu-id="c22f3-113">Description</span><span class="sxs-lookup"><span data-stu-id="c22f3-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c22f3-114">PropertyName-Element voor SelectionCondition voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c22f3-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="c22f3-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c22f3-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c22f3-116">Hiermee geeft u een .NET-eigenschap die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="c22f3-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="c22f3-117">ScriptBlock-Element voor SelectionCondition voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c22f3-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="c22f3-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c22f3-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c22f3-119">Hiermee geeft u het script dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="c22f3-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="c22f3-120">SelectionSetName-Element voor SelectionCondition voor aangepaste besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c22f3-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="c22f3-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c22f3-121">Optional element.</span></span><br /><br /> <span data-ttu-id="c22f3-122">Hiermee geeft u de set van .NET-typen die de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="c22f3-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="c22f3-123">TypeName-Element voor SelectionCondition voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c22f3-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="c22f3-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="c22f3-124">Optional element.</span></span><br /><br /> <span data-ttu-id="c22f3-125">Hiermee geeft u een .NET-type dat de voorwaarde wordt geactiveerd.</span><span class="sxs-lookup"><span data-stu-id="c22f3-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c22f3-126">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="c22f3-126">Parent Elements</span></span>

|<span data-ttu-id="c22f3-127">Element</span><span class="sxs-lookup"><span data-stu-id="c22f3-127">Element</span></span>|<span data-ttu-id="c22f3-128">Description</span><span class="sxs-lookup"><span data-stu-id="c22f3-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c22f3-129">EntrySelectedBy-Element voor CustomEntry voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c22f3-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="c22f3-130">Hiermee definieert u de .NET-typen die gebruikmaken van de besturingselementdefinitie van dit of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="c22f3-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c22f3-131">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c22f3-131">Remarks</span></span>

<span data-ttu-id="c22f3-132">Wanneer u een selectievoorwaarde definieert, wordt de volgende vereisten gelden:</span><span class="sxs-lookup"><span data-stu-id="c22f3-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="c22f3-133">De selectievoorwaarde moet de naam van een minimaal één eigenschap of een scriptblok opgeven, maar u kunt niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="c22f3-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="c22f3-134">De selectievoorwaarde een willekeurig aantal .NET-typen kunt opgeven of de selectie wordt ingesteld, maar niet beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="c22f3-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="c22f3-135">Zie voor meer informatie over het gebruik van de voorwaarden van de selectie [definiëren voorwaarden voor wanneer gegevens worden weergegeven](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c22f3-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c22f3-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="c22f3-136">See Also</span></span>

[<span data-ttu-id="c22f3-137">PropertyName-Element voor SelectionCondition voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c22f3-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c22f3-138">ScriptBlock-Element voor SelectionCondition voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c22f3-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c22f3-139">SelectionSetName-Element voor SelectionCondition voor aangepaste besturingselementen voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c22f3-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c22f3-140">TypeName-Element voor SelectionCondition voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c22f3-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c22f3-141">EntrySelectedBy-Element voor CustomEntry voor CustomControl voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="c22f3-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="c22f3-142">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="c22f3-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)