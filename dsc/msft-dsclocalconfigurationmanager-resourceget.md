---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, configuratie, setup
title: De ResourceGet-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3fd7ae54eb3ae782156dc4619ee0b6905dfb1212
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/09/2018
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="a3747-103">De ResourceGet-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="a3747-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="a3747-104">Rechtstreeks roept de **ophalen** methode van een DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="a3747-104">Directly calls the **Get** method of a DSC resource.</span></span>

<a name="syntax"></a><span data-ttu-id="a3747-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="a3747-105">Syntax</span></span>
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a><span data-ttu-id="a3747-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="a3747-106">Parameters</span></span>
----------

<span data-ttu-id="a3747-107">*ResourceType* \[in\] de naam van de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="a3747-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="a3747-108">*Modulenaam* \[in\] de naam van de module met de bron aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="a3747-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="a3747-109">*resourceProperty* \[in\] specificeert de naam van de resource-eigenschap en de waarde in een hashtabel als sleutel en waarde, respectievelijk.</span><span class="sxs-lookup"><span data-stu-id="a3747-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="a3747-110">Gebruik de [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet voor het detecteren van de resource-eigenschappen en hun typen.</span><span class="sxs-lookup"><span data-stu-id="a3747-110">Use the [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="a3747-111">*configuraties* \[uit\] op return bevat een ingesloten exemplaar van de configuraties.</span><span class="sxs-lookup"><span data-stu-id="a3747-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="a3747-112">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="a3747-112">Return value</span></span>
------------

<span data-ttu-id="a3747-113">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="a3747-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a3747-114">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="a3747-114">Remarks</span></span>

<span data-ttu-id="a3747-115">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="a3747-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a3747-116">Vereisten</span><span class="sxs-lookup"><span data-stu-id="a3747-116">Requirements</span></span>
------------
><span data-ttu-id="a3747-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a3747-117">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="a3747-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a3747-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="a3747-119">Zie ook</span><span class="sxs-lookup"><span data-stu-id="a3747-119">See also</span></span>


[<span data-ttu-id="a3747-120">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="a3747-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)