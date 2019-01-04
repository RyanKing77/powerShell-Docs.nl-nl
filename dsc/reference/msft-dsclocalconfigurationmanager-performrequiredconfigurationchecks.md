---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De PerformRequiredConfigurationChecks-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b92eefb7fbea6d96afa31f6b802ba10fe20d4103
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/14/2018
ms.locfileid: "53403891"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="76ff4-103">De PerformRequiredConfigurationChecks-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="76ff4-103">PerformRequiredConfigurationChecks method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="76ff4-104">Een consistentiecontrole starten met behulp van de Taakplanner.</span><span class="sxs-lookup"><span data-stu-id="76ff4-104">Starts a consistency check by using the Task Scheduler.</span></span>

## <a name="syntax"></a><span data-ttu-id="76ff4-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="76ff4-105">Syntax</span></span>

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a><span data-ttu-id="76ff4-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="76ff4-106">Parameters</span></span>

<span data-ttu-id="76ff4-107">*Vlaggen* \[in\] een bitmasker waarmee het type van een consistentiecontrole uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="76ff4-107">*Flags* \[in\] A bitmask that specifies the type of consistency check to run.</span></span> <span data-ttu-id="76ff4-108">De volgende waarden geldig zijn en kunnen worden gecombineerd met behulp van een bitwise **of** bewerking:</span><span class="sxs-lookup"><span data-stu-id="76ff4-108">The following values are valid, and can be combined by using a bitwise **OR** operation:</span></span>

|<span data-ttu-id="76ff4-109">Value</span><span class="sxs-lookup"><span data-stu-id="76ff4-109">Value</span></span> |<span data-ttu-id="76ff4-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="76ff4-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="76ff4-111">**1**</span><span class="sxs-lookup"><span data-stu-id="76ff4-111">**1**</span></span> | <span data-ttu-id="76ff4-112">Een normale consistentiecontrole uit.</span><span class="sxs-lookup"><span data-stu-id="76ff4-112">A normal consistency check.</span></span> |
|<span data-ttu-id="76ff4-113">**2**</span><span class="sxs-lookup"><span data-stu-id="76ff4-113">**2**</span></span> | <span data-ttu-id="76ff4-114">Een voortzetting van een consistentiecontrole uit na het opnieuw opstarten.</span><span class="sxs-lookup"><span data-stu-id="76ff4-114">A continuation of a consistency check after a reboot.</span></span> <span data-ttu-id="76ff4-115">Deze waarde moet niet worden gecombineerd met andere waarden.</span><span class="sxs-lookup"><span data-stu-id="76ff4-115">This value should not be combined with other values.</span></span> |
|<span data-ttu-id="76ff4-116">**4**</span><span class="sxs-lookup"><span data-stu-id="76ff4-116">**4**</span></span> | <span data-ttu-id="76ff4-117">De configuratie moet worden opgehaald uit de pull-server die is opgegeven in de metaconfiguration voor het knooppunt.</span><span class="sxs-lookup"><span data-stu-id="76ff4-117">The configuration should be pulled from the pull server specified in the metaconfiguration for the node.</span></span> <span data-ttu-id="76ff4-118">Deze waarde moet altijd worden gecombineerd met **1**, voor een waarde van **5**.</span><span class="sxs-lookup"><span data-stu-id="76ff4-118">This value should always be combined with **1**, for a value of **5**.</span></span> |
|<span data-ttu-id="76ff4-119">**8**</span><span class="sxs-lookup"><span data-stu-id="76ff4-119">**8**</span></span> | <span data-ttu-id="76ff4-120">De status verzenden naar de rapportserver.</span><span class="sxs-lookup"><span data-stu-id="76ff4-120">Send status to the report server.</span></span> |

## <a name="return-value"></a><span data-ttu-id="76ff4-121">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="76ff4-121">Return value</span></span>

<span data-ttu-id="76ff4-122">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="76ff4-122">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="76ff4-123">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="76ff4-123">Remarks</span></span>

<span data-ttu-id="76ff4-124">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="76ff4-124">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="76ff4-125">Vereisten</span><span class="sxs-lookup"><span data-stu-id="76ff4-125">Requirements</span></span>

<span data-ttu-id="76ff4-126">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="76ff4-126">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="76ff4-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="76ff4-127">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="76ff4-128">Zie ook</span><span class="sxs-lookup"><span data-stu-id="76ff4-128">See also</span></span>

[<span data-ttu-id="76ff4-129">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="76ff4-129">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)