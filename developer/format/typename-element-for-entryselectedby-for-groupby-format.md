---
title: TypeName-Element voor EntrySelectedBy voor GroupBy (indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b8b6739b-770c-432a-95ab-551c7507c51f
caps.latest.revision: 6
ms.openlocfilehash: 3b5ce60d3a0d76988af48f49445a5478a415d498
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850776"
---
# <a name="typename-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="7575b-102">Het element TypeName voor EntrySelectedBy voor GroupBy (opmaak)</span><span class="sxs-lookup"><span data-stu-id="7575b-102">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="7575b-103">Hiermee geeft u een .NET-type dat gebruikmaakt van deze definitie van het aangepaste besturingselement.</span><span class="sxs-lookup"><span data-stu-id="7575b-103">Specifies a .NET type that uses this definition of the custom control.</span></span> <span data-ttu-id="7575b-104">Dit element wordt gebruikt bij het definiëren van hoe een nieuwe groep objecten worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="7575b-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="7575b-105">Configuratie van Element (indeling) ViewDefinitions-Element (indeling) weergave Element (indeling) GroupBy Element voor weergave (indeling) CustomControl Element voor GroupBy (indeling) CustomEntries Element voor CustomControl voor GroupBy (indeling) CustomEntry Element voor CustomControl voor GroupBy (indeling) EntrySelectedBy Element voor CustomEntry voor GroupBy (indeling) TypeName Element voor EntrySelectedBy voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7575b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7575b-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="7575b-106">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7575b-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="7575b-107">Attributes and Elements</span></span>

<span data-ttu-id="7575b-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="7575b-108">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7575b-109">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="7575b-109">Attributes</span></span>

<span data-ttu-id="7575b-110">Geen.</span><span class="sxs-lookup"><span data-stu-id="7575b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7575b-111">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7575b-111">Child Elements</span></span>

<span data-ttu-id="7575b-112">Geen.</span><span class="sxs-lookup"><span data-stu-id="7575b-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7575b-113">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="7575b-113">Parent Elements</span></span>

|<span data-ttu-id="7575b-114">Element</span><span class="sxs-lookup"><span data-stu-id="7575b-114">Element</span></span>|<span data-ttu-id="7575b-115">Description</span><span class="sxs-lookup"><span data-stu-id="7575b-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7575b-116">EntrySelectedBy-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7575b-116">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="7575b-117">Hiermee definieert u de .NET-typen die gebruikmaken van de besturingselementdefinitie van dit of de voorwaarde die moet bestaan voor deze definitie moet worden gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7575b-117">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7575b-118">Tekstwaarde</span><span class="sxs-lookup"><span data-stu-id="7575b-118">Text Value</span></span>

<span data-ttu-id="7575b-119">Geef de volledig gekwalificeerde naam van het .NET-type, bijvoorbeeld `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="7575b-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="7575b-120">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="7575b-120">Remarks</span></span>

<span data-ttu-id="7575b-121">De besturingselementdefinitie van elk moet ten minste één naam, selectie instellen of selectievoorwaarde gedefinieerd hebben.</span><span class="sxs-lookup"><span data-stu-id="7575b-121">Each control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="7575b-122">Zie voor meer informatie over de onderdelen van de weergave van een aangepast besturingselement [het maken van aangepaste besturingselementen](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="7575b-122">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7575b-123">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7575b-123">See Also</span></span>

[<span data-ttu-id="7575b-124">Het maken van aangepaste besturingselementen</span><span class="sxs-lookup"><span data-stu-id="7575b-124">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="7575b-125">EntrySelectedBy-Element voor CustomEntry voor GroupBy (indeling)</span><span class="sxs-lookup"><span data-stu-id="7575b-125">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="7575b-126">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="7575b-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
