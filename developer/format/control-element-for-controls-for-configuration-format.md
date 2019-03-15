---
title: Element beheren voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bddf7ffa-04d3-4354-90b9-5e714e096260
caps.latest.revision: 13
ms.openlocfilehash: 26fe417c9ca60dda22bdc23d9d339d40135a0c9b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848830"
---
# <a name="control-element-for-controls-for-configuration-format"></a><span data-ttu-id="42dc9-102">Het element Besturingselement voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="42dc9-102">Control Element for Controls for Configuration (Format)</span></span>

<span data-ttu-id="42dc9-103">Hiermee definieert u een algemene besturingselement dat kan worden gebruikt door alle weergaven van de opmaak bestands- en de naam die wordt gebruikt om te verwijzen naar het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="42dc9-103">Defines a common control that can be used by all the views of the formatting file and the name that is used to reference the control.</span></span>

<span data-ttu-id="42dc9-104">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="42dc9-104">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="42dc9-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="42dc9-105">Syntax</span></span>

```xml
<Control>
  <Name>NameOfControl</Name>
  <CustomControl>...</CustomControl>
</Control>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="42dc9-106">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="42dc9-106">Attributes and Elements</span></span>

<span data-ttu-id="42dc9-107">De volgende secties worden de kenmerken, onderliggende elementen en het bovenliggende element voor de `Control` element.</span><span class="sxs-lookup"><span data-stu-id="42dc9-107">The following sections describe the attributes, child elements, and the parent element for the `Control` element.</span></span> <span data-ttu-id="42dc9-108">U moet slechts één van elk onderliggend element opgeven.</span><span class="sxs-lookup"><span data-stu-id="42dc9-108">You must specify only one of each child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="42dc9-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="42dc9-109">Attributes</span></span>

<span data-ttu-id="42dc9-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="42dc9-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="42dc9-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="42dc9-111">Child Elements</span></span>

|<span data-ttu-id="42dc9-112">Element</span><span class="sxs-lookup"><span data-stu-id="42dc9-112">Element</span></span>|<span data-ttu-id="42dc9-113">Description</span><span class="sxs-lookup"><span data-stu-id="42dc9-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42dc9-114">CustomControl-Element voor het besturingselement voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="42dc9-114">CustomControl Element for Control for Controls for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="42dc9-115">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="42dc9-115">Required element.</span></span><br /><br /> <span data-ttu-id="42dc9-116">Hiermee definieert u het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="42dc9-116">Defines the control.</span></span>|
|[<span data-ttu-id="42dc9-117">Naamelement voor controle voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="42dc9-117">Name Element for Control for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="42dc9-118">Vereist element.</span><span class="sxs-lookup"><span data-stu-id="42dc9-118">Required element.</span></span><br /><br /> <span data-ttu-id="42dc9-119">Hiermee geeft u de naam die wordt gebruikt om te verwijzen naar het besturingselement.</span><span class="sxs-lookup"><span data-stu-id="42dc9-119">Specifies the name used to reference the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="42dc9-120">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="42dc9-120">Parent Elements</span></span>

|<span data-ttu-id="42dc9-121">Element</span><span class="sxs-lookup"><span data-stu-id="42dc9-121">Element</span></span>|<span data-ttu-id="42dc9-122">Description</span><span class="sxs-lookup"><span data-stu-id="42dc9-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="42dc9-123">Besturingselementen Element van de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="42dc9-123">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)|<span data-ttu-id="42dc9-124">Hiermee definieert u de algemene besturingselementen die kunnen worden gebruikt door alle weergaven van de opmaak bestand of andere besturingselementen.</span><span class="sxs-lookup"><span data-stu-id="42dc9-124">Defines the common controls that can be used by all views of the formatting file or by other controls.</span></span>|

## <a name="remarks"></a><span data-ttu-id="42dc9-125">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="42dc9-125">Remarks</span></span>

<span data-ttu-id="42dc9-126">De naam van dit besturingselement kan naar worden verwezen in de volgende elementen:</span><span class="sxs-lookup"><span data-stu-id="42dc9-126">The name given to this control can be referenced in the following elements:</span></span>

- [<span data-ttu-id="42dc9-127">ExpressionBinding-Element voor CustomItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="42dc9-127">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

- [<span data-ttu-id="42dc9-128">GroupBy-Element voor View(Format)</span><span class="sxs-lookup"><span data-stu-id="42dc9-128">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

## <a name="see-also"></a><span data-ttu-id="42dc9-129">Zie ook</span><span class="sxs-lookup"><span data-stu-id="42dc9-129">See Also</span></span>

[<span data-ttu-id="42dc9-130">Besturingselementen Element van de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="42dc9-130">Controls Element of Configuration (Format)</span></span>](./controls-element-for-configuration-format.md)

[<span data-ttu-id="42dc9-131">CustomControl-element voor controle voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="42dc9-131">CustomControl element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="42dc9-132">ExpressionBinding-Element voor CustomItem (indeling)</span><span class="sxs-lookup"><span data-stu-id="42dc9-132">ExpressionBinding Element for CustomItem (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="42dc9-133">GroupBy-Element voor View(Format)</span><span class="sxs-lookup"><span data-stu-id="42dc9-133">GroupBy Element for View(Format)</span></span>](./groupby-element-for-view-format.md)

[<span data-ttu-id="42dc9-134">Naamelement voor controle van besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="42dc9-134">Name Element for Control for Controls for Configuration (Format)</span></span>](./name-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="42dc9-135">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="42dc9-135">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)