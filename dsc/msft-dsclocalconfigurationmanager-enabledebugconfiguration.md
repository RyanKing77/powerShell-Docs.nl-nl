---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie, setup
title: De EnableDebugConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9e2a978f9d16abaed959be022229db4da5fd65bd
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="eb0c2-103">De EnableDebugConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="eb0c2-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="eb0c2-104">Hiermee schakelt u foutopsporing van DSC-resource.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="eb0c2-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="eb0c2-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="eb0c2-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="eb0c2-106">Parameters</span></span>
----------

<span data-ttu-id="eb0c2-107">*BreakAll* \[in\] een onderbrekingspunt instellen op elke regel in het resource-script.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="eb0c2-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="eb0c2-108">Return value</span></span>
------------

<span data-ttu-id="eb0c2-109">Retourneert nul geslaagd; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="eb0c2-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="eb0c2-110">Remarks</span></span>

<span data-ttu-id="eb0c2-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="eb0c2-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="eb0c2-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="eb0c2-112">Requirements</span></span>
------------
><span data-ttu-id="eb0c2-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="eb0c2-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="eb0c2-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="eb0c2-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="eb0c2-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="eb0c2-115">See also</span></span>


[<span data-ttu-id="eb0c2-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="eb0c2-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)