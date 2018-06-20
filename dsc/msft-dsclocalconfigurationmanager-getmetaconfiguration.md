---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De GetMetaConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: ebf2b65f152c622ccf42e12545b0048a0b96d963
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219773"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8917b-103">De GetMetaConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="8917b-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8917b-104">Hiermee haalt u de lokale Configuration Manager-instellingen die worden gebruikt voor het beheren van de configuratie-Agent.</span><span class="sxs-lookup"><span data-stu-id="8917b-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="8917b-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="8917b-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="8917b-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="8917b-106">Parameters</span></span>
----------

<span data-ttu-id="8917b-107">*Metaconfiguratie* \[uit\] op return bevat een ingesloten exemplaar van de **MSFT_DSCMetaConfiguration** klasse die de instellingen definieert.</span><span class="sxs-lookup"><span data-stu-id="8917b-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="8917b-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="8917b-108">Return value</span></span>
------------

<span data-ttu-id="8917b-109">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="8917b-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8917b-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="8917b-110">Remarks</span></span>

<span data-ttu-id="8917b-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="8917b-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8917b-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="8917b-112">Requirements</span></span>
------------
><span data-ttu-id="8917b-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8917b-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="8917b-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8917b-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="8917b-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="8917b-115">See also</span></span>


[<span data-ttu-id="8917b-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="8917b-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)