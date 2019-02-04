---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: 5b31fe833fb0f9d0f3f2733e777e4608a697d583
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685632"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a><span data-ttu-id="df52c-102">Side-By-Side-Module-ondersteuning voor versiebeheer voor DSC-Resources</span><span class="sxs-lookup"><span data-stu-id="df52c-102">Side-By-Side Module Versioning Support for DSC Resources</span></span>

<span data-ttu-id="df52c-103">Modules met DSC-resources kunnen worden geïnstalleerd side-by-side en DSC-configuraties kunt een specifieke versie van de resource die is geïnstalleerd op het systeem.</span><span class="sxs-lookup"><span data-stu-id="df52c-103">Modules containing DSC resources can be installed side-by-side, and DSC configurations can use a specific version of the resource that is installed on the system.</span></span>

<span data-ttu-id="df52c-104">Zie voor meer informatie, [resources met meerdere versies gebruiken](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span><span class="sxs-lookup"><span data-stu-id="df52c-104">For more information, see [Using resources with multiple versions](https://msdn.microsoft.com/powershell/dsc/sxsresource).</span></span>

## <a name="known-issues"></a><span data-ttu-id="df52c-105">Bekende problemen</span><span class="sxs-lookup"><span data-stu-id="df52c-105">Known issues</span></span>

<span data-ttu-id="df52c-106">In deze release volgen de volgende bekende problemen van side-by-side-installatie:</span><span class="sxs-lookup"><span data-stu-id="df52c-106">In this release, the following are known issues of side-by-side installation:</span></span>

-   <span data-ttu-id="df52c-107">Met behulp van twee verschillende versies van de DSC-resource binnen dezelfde configuratie wordt niet ondersteund.</span><span class="sxs-lookup"><span data-stu-id="df52c-107">Using two different versions of the DSC resource within the same configuration is not supported.</span></span>
