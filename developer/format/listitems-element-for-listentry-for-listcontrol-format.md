---
title: ListItems-Element voor ListEntry voor ListControl (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848620"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="982ee-102">Het element ListItems voor ListEntry voor ListControl (opmaak)</span><span class="sxs-lookup"><span data-stu-id="982ee-102">ListItems Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="982ee-103">Definieert de eigenschappen en -scripts waarvan de waarden worden weergegeven in de rijen van de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="982ee-103">Defines the properties and scripts whose values are displayed in the rows of the list view.</span></span>

<span data-ttu-id="982ee-104">Configuratie Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) ListControl Element (indeling) ListEntries Element voor lijst besturingselement (indeling) ListEntry-Element voor ListControl (indeling) ListItems Element voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="982ee-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for List Control (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="982ee-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="982ee-105">Syntax</span></span>

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="982ee-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="982ee-106">Attributes and Elements</span></span>

<span data-ttu-id="982ee-107">De volgende secties worden de kenmerken, de onderliggende elementen en het bovenliggende element van de `ListItems` element.</span><span class="sxs-lookup"><span data-stu-id="982ee-107">The following sections describe the attributes, child elements, and parent element of the `ListItems` element.</span></span> <span data-ttu-id="982ee-108">Er is geen limiet voor het aantal onderliggende elementen die kunnen worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="982ee-108">There is no limit to the number of child elements that can be specified.</span></span> <span data-ttu-id="982ee-109">De volgorde van de onderliggende elementen bepaalt de volgorde die waarden worden weergegeven in de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="982ee-109">The order of the child elements defines the order that values are displayed in the list view.</span></span>

### <a name="attributes"></a><span data-ttu-id="982ee-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="982ee-110">Attributes</span></span>

<span data-ttu-id="982ee-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="982ee-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="982ee-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="982ee-112">Child Elements</span></span>

|<span data-ttu-id="982ee-113">Element</span><span class="sxs-lookup"><span data-stu-id="982ee-113">Element</span></span>|<span data-ttu-id="982ee-114">Description</span><span class="sxs-lookup"><span data-stu-id="982ee-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="982ee-115">Lijstitem-Element voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="982ee-115">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="982ee-116">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="982ee-116">Required element.</span></span><br /><br /> <span data-ttu-id="982ee-117">Hiermee definieert de eigenschap of het script waarvan de waarde wordt weergegeven in de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="982ee-117">Defines the property or script whose value is displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="982ee-118">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="982ee-118">Parent Elements</span></span>

|<span data-ttu-id="982ee-119">Element</span><span class="sxs-lookup"><span data-stu-id="982ee-119">Element</span></span>|<span data-ttu-id="982ee-120">Description</span><span class="sxs-lookup"><span data-stu-id="982ee-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="982ee-121">ListEntry-Element voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="982ee-121">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="982ee-122">Bevat een definitie van de lijstweergave.</span><span class="sxs-lookup"><span data-stu-id="982ee-122">Provides a definition of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="982ee-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="982ee-123">Remarks</span></span>

<span data-ttu-id="982ee-124">Zie voor meer informatie over dit type weergave [het maken van een lijstweergave](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="982ee-124">For more information about this type of view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="982ee-125">Voorbeeld</span><span class="sxs-lookup"><span data-stu-id="982ee-125">Example</span></span>

<span data-ttu-id="982ee-126">In dit voorbeeld ziet u de XML-elementen die drie rijen van de lijstweergave definiëren.</span><span class="sxs-lookup"><span data-stu-id="982ee-126">This example shows the XML elements that define three rows of the list view.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="982ee-127">Zie ook</span><span class="sxs-lookup"><span data-stu-id="982ee-127">See Also</span></span>

[<span data-ttu-id="982ee-128">ListEntry-Element voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="982ee-128">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="982ee-129">Lijstitem-Element voor ListControl (indeling)</span><span class="sxs-lookup"><span data-stu-id="982ee-129">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="982ee-130">Het maken van een lijst weergeven</span><span class="sxs-lookup"><span data-stu-id="982ee-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="982ee-131">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="982ee-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)