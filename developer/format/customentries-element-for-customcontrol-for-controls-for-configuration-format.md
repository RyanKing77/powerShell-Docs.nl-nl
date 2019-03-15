---
title: CustomEntries-Element voor CustomControl voor besturingselementen voor de configuratie (-indeling) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 80fc4de2-208f-4506-9a6a-c2675bb83be4
caps.latest.revision: 11
ms.openlocfilehash: abef6c91500f665c2366f221496d4cfd6444f5c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847024"
---
# <a name="customentries-element-for-customcontrol-for-controls-for-configuration-format"></a><span data-ttu-id="54bf8-102">Het element CustomEntries voor CustomControl voor Besturingselementen voor Configuratie (opmaak)</span><span class="sxs-lookup"><span data-stu-id="54bf8-102">CustomEntries Element for CustomControl for Controls for Configuration (Format)</span></span>

<span data-ttu-id="54bf8-103">Bevat de definities van een algemene besturingselementen.</span><span class="sxs-lookup"><span data-stu-id="54bf8-103">Provides the definitions of a common control.</span></span> <span data-ttu-id="54bf8-104">Dit element wordt gebruikt bij het definiëren van een algemene besturingselement dat kan worden gebruikt door alle weergaven in de opmaak-bestand.</span><span class="sxs-lookup"><span data-stu-id="54bf8-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="54bf8-105">Configuratie-Element (indeling) besturingselementen Element van configuratie (-indeling) besturingselement Element controles voor configuratie (-indeling) CustomControl-Element voor het besturingselement voor configuratie (-indeling) CustomEntries-Element voor CustomControl voor configuratie ( -Indeling)</span><span class="sxs-lookup"><span data-stu-id="54bf8-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="54bf8-106">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="54bf8-106">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="54bf8-107">Kenmerken en elementen</span><span class="sxs-lookup"><span data-stu-id="54bf8-107">Attributes and Elements</span></span>

<span data-ttu-id="54bf8-108">De volgende secties beschrijven kenmerken, onderliggende elementen en het bovenliggende element van de `CustomEntries` element.</span><span class="sxs-lookup"><span data-stu-id="54bf8-108">The following sections describe attributes, child elements, and the parent element of the `CustomEntries` element.</span></span> <span data-ttu-id="54bf8-109">U moet een of meer onderliggende elementen.</span><span class="sxs-lookup"><span data-stu-id="54bf8-109">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="54bf8-110">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="54bf8-110">Attributes</span></span>

<span data-ttu-id="54bf8-111">Geen.</span><span class="sxs-lookup"><span data-stu-id="54bf8-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="54bf8-112">Onderliggende elementen</span><span class="sxs-lookup"><span data-stu-id="54bf8-112">Child Elements</span></span>

|<span data-ttu-id="54bf8-113">Element</span><span class="sxs-lookup"><span data-stu-id="54bf8-113">Element</span></span>|<span data-ttu-id="54bf8-114">Description</span><span class="sxs-lookup"><span data-stu-id="54bf8-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54bf8-115">CustomEntry-Element voor CustomControl voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="54bf8-115">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="54bf8-116">Bevat een definitie van de algemene besturingselementen.</span><span class="sxs-lookup"><span data-stu-id="54bf8-116">Provides a definition of the common control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="54bf8-117">Bovenliggende elementen</span><span class="sxs-lookup"><span data-stu-id="54bf8-117">Parent Elements</span></span>

|<span data-ttu-id="54bf8-118">Element</span><span class="sxs-lookup"><span data-stu-id="54bf8-118">Element</span></span>|<span data-ttu-id="54bf8-119">Description</span><span class="sxs-lookup"><span data-stu-id="54bf8-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="54bf8-120">CustomControl-Element voor controle voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="54bf8-120">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)|<span data-ttu-id="54bf8-121">Hiermee definieert u een algemene besturingselement.</span><span class="sxs-lookup"><span data-stu-id="54bf8-121">Defines a common control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="54bf8-122">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="54bf8-122">Remarks</span></span>

<span data-ttu-id="54bf8-123">In de meeste gevallen een besturingselement heeft slechts één definitie die is gedefinieerd in een enkel `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="54bf8-123">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="54bf8-124">Het is echter mogelijk om meerdere definities als u wilt de hetzelfde besturingselement gebruiken om verschillende .NET-objecten weer te geven.</span><span class="sxs-lookup"><span data-stu-id="54bf8-124">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="54bf8-125">In deze gevallen kunt u een `CustomEntry` -element voor elk object of een set van objecten.</span><span class="sxs-lookup"><span data-stu-id="54bf8-125">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="54bf8-126">Zie ook</span><span class="sxs-lookup"><span data-stu-id="54bf8-126">See Also</span></span>

[<span data-ttu-id="54bf8-127">CustomControl-Element voor controle voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="54bf8-127">CustomControl Element for Control for Configuration (Format)</span></span>](./customcontrol-element-for-control-for-controls-for-configuration-format.md)

[<span data-ttu-id="54bf8-128">CustomEntry-Element voor CustomControl voor besturingselementen voor de configuratie (-indeling)</span><span class="sxs-lookup"><span data-stu-id="54bf8-128">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)

[<span data-ttu-id="54bf8-129">Schrijven van een bestand opmaak PowerShell</span><span class="sxs-lookup"><span data-stu-id="54bf8-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)