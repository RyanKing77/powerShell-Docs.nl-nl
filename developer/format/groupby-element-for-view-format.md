---
title: GroupBy-Element voor weergave (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67a2b061-2a4a-4ad1-84f9-cdbefb64aaab
caps.latest.revision: 8
ms.openlocfilehash: abb8b91626128b3deaa2db24a9fd8b34a6563410
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849278"
---
# <a name="groupby-element-for-view-format"></a><span data-ttu-id="a9d85-102">Het element GroupBy voor Weergave (opmaak)</span><span class="sxs-lookup"><span data-stu-id="a9d85-102">GroupBy Element for View (Format)</span></span>

<span data-ttu-id="a9d85-103">Hiermee definieert u hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="a9d85-103">Defines how a new group of objects is displayed.</span></span> <span data-ttu-id="a9d85-104">Dit element wordt gebruikt bij het definiëren van een tabel, lijst, breed of aangepast besturingselement weergeven.</span><span class="sxs-lookup"><span data-stu-id="a9d85-104">This element is used when defining a table, list, wide, or custom control view.</span></span>

<span data-ttu-id="a9d85-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling)</span><span class="sxs-lookup"><span data-stu-id="a9d85-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a9d85-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a9d85-106">Syntax</span></span>

```xml
<GroupBy>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
  <Label>TextToDisplay</Label>
  <CustomControl>...</CustomControl>
  <CustomControlName>NameOfControl</CustomControlName>
</GroupBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a9d85-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="a9d85-107">Attributes and Elements</span></span>

<span data-ttu-id="a9d85-108">De volgende secties beschrijven kenmerken, elementen van de onderliggende en bovenliggende elementen.</span><span class="sxs-lookup"><span data-stu-id="a9d85-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a9d85-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="a9d85-109">Attributes</span></span>

<span data-ttu-id="a9d85-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="a9d85-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a9d85-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a9d85-111">Child Elements</span></span>

|<span data-ttu-id="a9d85-112">Element</span><span class="sxs-lookup"><span data-stu-id="a9d85-112">Element</span></span>|<span data-ttu-id="a9d85-113">Description</span><span class="sxs-lookup"><span data-stu-id="a9d85-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a9d85-114">CustomControl-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="a9d85-114">CustomControl Element for GroupBy (Format)</span></span>](./customcontrol-element-for-groupby-format.md)|<span data-ttu-id="a9d85-115">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a9d85-115">Optional element.</span></span><br /><br /> <span data-ttu-id="a9d85-116">Hiermee definieert u het aangepaste besturingselement die nieuwe groepen worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="a9d85-116">Defines the custom control that display new groups.</span></span>|
|[<span data-ttu-id="a9d85-117">CustomControlName-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="a9d85-117">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)|<span data-ttu-id="a9d85-118">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a9d85-118">Optional element.</span></span><br /><br /> <span data-ttu-id="a9d85-119">Hiermee geeft u de naam van een besturingselement dat wordt gebruikt om de nieuwe groep weer te geven.</span><span class="sxs-lookup"><span data-stu-id="a9d85-119">Specifies the name of a control that is used to display the new group.</span></span>|
|[<span data-ttu-id="a9d85-120">Label-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="a9d85-120">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)|<span data-ttu-id="a9d85-121">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a9d85-121">Optional element.</span></span><br /><br /> <span data-ttu-id="a9d85-122">Hiermee geeft u een label dat wordt weergegeven wanneer een nieuwe groep is opgetreden.</span><span class="sxs-lookup"><span data-stu-id="a9d85-122">Specifies a label that is displayed when a new group is encountered.</span></span>|
|[<span data-ttu-id="a9d85-123">PropertyName-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="a9d85-123">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)|<span data-ttu-id="a9d85-124">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a9d85-124">Optional element.</span></span><br /><br /> <span data-ttu-id="a9d85-125">Hiermee geeft u de .NET-eigenschap voor de start een nieuwe groep wanneer de waarde ervan verandert.</span><span class="sxs-lookup"><span data-stu-id="a9d85-125">Specifies the .NET property the starts a new group whenever its value changes.</span></span>|
|[<span data-ttu-id="a9d85-126">ScriptBlock-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="a9d85-126">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)|<span data-ttu-id="a9d85-127">Optioneel element.</span><span class="sxs-lookup"><span data-stu-id="a9d85-127">Optional element.</span></span><br /><br /> <span data-ttu-id="a9d85-128">Hiermee geeft u het script dat een nieuwe groep wordt gestart wanneer de waarde ervan verandert.</span><span class="sxs-lookup"><span data-stu-id="a9d85-128">Specifies the script that starts a new group whenever its value changes.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a9d85-129">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="a9d85-129">Parent Elements</span></span>

|<span data-ttu-id="a9d85-130">Element</span><span class="sxs-lookup"><span data-stu-id="a9d85-130">Element</span></span>|<span data-ttu-id="a9d85-131">Description</span><span class="sxs-lookup"><span data-stu-id="a9d85-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a9d85-132">Weergave-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a9d85-132">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="a9d85-133">Hiermee definieert u een weergave met een of meer .NET-objecten.</span><span class="sxs-lookup"><span data-stu-id="a9d85-133">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a9d85-134">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a9d85-134">Remarks</span></span>

<span data-ttu-id="a9d85-135">Bij het definiëren van hoe een nieuwe groep objecten worden weergegeven, moet u de eigenschap of het script waarmee de nieuwe groep; wordt gestart u kunt niet, beide opgeven.</span><span class="sxs-lookup"><span data-stu-id="a9d85-135">When defining how a new group of objects is displayed, you must specify the property or script that will start the new group; however, you cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="a9d85-136">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a9d85-136">See Also</span></span>

[<span data-ttu-id="a9d85-137">CustomControlName-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="a9d85-137">CustomControlName Element for GroupBy (Format)</span></span>](./customcontrolname-element-for-groupby-format.md)

[<span data-ttu-id="a9d85-138">Label-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="a9d85-138">Label Element for GroupBy (Format)</span></span>](./label-element-for-groupby-format.md)

[<span data-ttu-id="a9d85-139">PropertyName-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="a9d85-139">PropertyName Element for GroupBy (Format)</span></span>](./propertyname-element-for-groupby-format.md)

[<span data-ttu-id="a9d85-140">ScriptBlock-Element voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="a9d85-140">ScriptBlock Element for GroupBy (Format)</span></span>](./scriptblock-element-for-groupby-format.md)

[<span data-ttu-id="a9d85-141">Weergave-Element (indeling)</span><span class="sxs-lookup"><span data-stu-id="a9d85-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="a9d85-142">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="a9d85-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)