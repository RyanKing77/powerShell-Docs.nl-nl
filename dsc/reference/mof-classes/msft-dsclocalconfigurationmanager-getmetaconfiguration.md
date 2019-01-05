---
ms.date: 06/12/2017
keywords: DSC, powershell, configuratie en installatie
title: De GetMetaConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048321"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d29d6-103">De GetMetaConfiguration-methode van de klasse MSFT_DSCLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="d29d6-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d29d6-104">De lokale Configuration Manager-instellingen die worden gebruikt voor het beheren van de configuratie van Agent worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d29d6-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="d29d6-105">Syntaxis</span><span class="sxs-lookup"><span data-stu-id="d29d6-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="d29d6-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="d29d6-106">Parameters</span></span>

<span data-ttu-id="d29d6-107">*MetaConfiguration* \[uit\] bij resultaat, bevat een ingesloten exemplaar van de **MSFT_DSCMetaConfiguration** klasse waarin de instellingen worden gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="d29d6-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="d29d6-108">Retourwaarde</span><span class="sxs-lookup"><span data-stu-id="d29d6-108">Return value</span></span>

<span data-ttu-id="d29d6-109">Retourneert nul op succes; Anders retourneert een foutcode.</span><span class="sxs-lookup"><span data-stu-id="d29d6-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d29d6-110">Opmerkingen</span><span class="sxs-lookup"><span data-stu-id="d29d6-110">Remarks</span></span>

<span data-ttu-id="d29d6-111">Dit is een statische methode.</span><span class="sxs-lookup"><span data-stu-id="d29d6-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d29d6-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d29d6-112">Requirements</span></span>

<span data-ttu-id="d29d6-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d29d6-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d29d6-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d29d6-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d29d6-115">Zie ook</span><span class="sxs-lookup"><span data-stu-id="d29d6-115">See also</span></span>

[<span data-ttu-id="d29d6-116">**MSFT_DSCLocalConfigurationManager**</span><span class="sxs-lookup"><span data-stu-id="d29d6-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)