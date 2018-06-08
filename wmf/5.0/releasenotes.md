---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
ms.openlocfilehash: a6366e18b4b6478bfab89475bc6975e6491da9f7
ms.sourcegitcommit: 01d6985ed190a222e9da1da41596f524f607a5bc
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34482859"
---
# <a name="windows-management-framework-wmf-50-rtm-release-notes-overview"></a><span data-ttu-id="c7208-102">Overzicht van Windows Management Framework (WMF) 5.0 RTM Release-opmerkingen</span><span class="sxs-lookup"><span data-stu-id="c7208-102">Windows Management Framework (WMF) 5.0 RTM Release Notes Overview</span></span>

<span data-ttu-id="c7208-103">**WMF 5.0 is superceeded door WMF 5.1. Gebruikers met WMF 5.0 upgrade naar WMF 5.1 ondersteuning krijgen. Volg de [installatie intructions van WMF 5.1](../5.1/install-configure.md)**</span><span class="sxs-lookup"><span data-stu-id="c7208-103">**WMF 5.0 is superceeded by WMF 5.1. Users with WMF 5.0 must upgrade to WMF 5.1 to receive support. Please follow the [installation intructions of WMF 5.1](../5.1/install-configure.md)**</span></span>

<span data-ttu-id="c7208-104">Windows Management Framework (WMF) 5.0 biedt RTM functionaliteit die is bijgewerkt van WMF 4.0.</span><span class="sxs-lookup"><span data-stu-id="c7208-104">Windows Management Framework (WMF) 5.0 RTM brings functionality that has been updated from WMF 4.0.</span></span> <span data-ttu-id="c7208-105">WMF 5.0 RTM is beschikbaar voor installatie alleen op **Windows Server 2012 R2**, **Windows Server 2012**, **Windows Server 2008 R2**, **Windows 8.1**, en **Windows 7 SP1** en bijgewerkte versies of introductie van de volgende functies bevat:</span><span class="sxs-lookup"><span data-stu-id="c7208-105">WMF 5.0 RTM is available for installation only on **Windows Server 2012 R2**, **Windows Server 2012**, **Windows Server 2008 R2**, **Windows 8.1**, and **Windows 7 SP1** and contains updated versions or introduction of the following features:</span></span>

- <span data-ttu-id="c7208-106">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7208-106">Windows PowerShell</span></span>
- <span data-ttu-id="c7208-107">Just Enough Administration (JEA)</span><span class="sxs-lookup"><span data-stu-id="c7208-107">Just Enough Administration (JEA)</span></span>
- <span data-ttu-id="c7208-108">Windows PowerShell Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="c7208-108">Windows PowerShell Desired State Configuration (DSC)</span></span>
- <span data-ttu-id="c7208-109">Windows PowerShell ISE (Integrated Scripting Environment)</span><span class="sxs-lookup"><span data-stu-id="c7208-109">Windows PowerShell Integrated Scripting Environment (ISE)</span></span>
- <span data-ttu-id="c7208-110">Windows PowerShell-webservices (Management OData IIS-extensie)</span><span class="sxs-lookup"><span data-stu-id="c7208-110">Windows PowerShell Web Services (Management OData IIS Extension)</span></span>
- <span data-ttu-id="c7208-111">Windows Remote Management (WinRM)</span><span class="sxs-lookup"><span data-stu-id="c7208-111">Windows Remote Management (WinRM)</span></span>
- <span data-ttu-id="c7208-112">Windows Management Instrumentation (WMI)</span><span class="sxs-lookup"><span data-stu-id="c7208-112">Windows Management Instrumentation (WMI)</span></span>

<span data-ttu-id="c7208-113">WMF 5.0 RTM vervangt de [WMF 5.0 productie Preview](http://blogs.msdn.com/b/powershell/archive/2015/08/31/windows-management-framework-5-0-production-preview-is-now-available.aspx).</span><span class="sxs-lookup"><span data-stu-id="c7208-113">WMF 5.0 RTM replaces the [WMF 5.0 Production Preview](http://blogs.msdn.com/b/powershell/archive/2015/08/31/windows-management-framework-5-0-production-preview-is-now-available.aspx).</span></span> <span data-ttu-id="c7208-114">U kunt WMF 5.0 RTM installeren zonder WMF 5.0 productie Preview verwijderen, maar moet u alle andere oudere versies van WMF 5.0 previews verwijderen voordat u installeert de WMF 5.0 RTM.</span><span class="sxs-lookup"><span data-stu-id="c7208-114">You can install WMF 5.0 RTM without uninstalling WMF 5.0 Production Preview, but you must uninstall all other older releases of WMF 5.0 previews before installing the WMF 5.0 RTM.</span></span>

<span data-ttu-id="c7208-115">*Opmerking:* als u Windows 10 uitvoert, kunt u dezelfde set functionaliteit die beschikbaar zijn in WMF 5.0 RTM krijgen door bij te werken naar de November update van Windows 10 (versie 1511).</span><span class="sxs-lookup"><span data-stu-id="c7208-115">*Note:* If you are running Windows 10, you can get the same set of functionality available in WMF 5.0 RTM by updating to the November update of Windows 10 (Version 1511).</span></span> <span data-ttu-id="c7208-116">Als u uw Windows 10-systeem niet al hebt bijgewerkt, selecteert u de knop Start en selecteer Instellingen > bijwerken en beveiliging > Windows Update > controleren op updates.</span><span class="sxs-lookup"><span data-stu-id="c7208-116">If you have not already updated your Windows 10 system, select the Start button, then select Settings > Update & security > Windows Update > Check for updates.</span></span>
