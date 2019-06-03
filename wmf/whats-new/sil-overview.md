---
ms.date: 06/12/2017
keywords: wmf,powershell,installeren
title: Registratie van software-inventaris (SIL)
ms.openlocfilehash: b12cfc4ae1e505bbc4d47596bed9352ce53a98f2
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856166"
---
# <a name="software-inventory-logging-sil"></a><span data-ttu-id="3518a-103">Registratie van software-inventaris (SIL)</span><span class="sxs-lookup"><span data-stu-id="3518a-103">Software Inventory Logging (SIL)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3518a-104">Bij het installeren van WMF 5.x op een Windows Server 2012 R2-Server waarop SIL al wordt uitgevoerd, is het nodig om uit te voeren van de cmdlet Start-SilLogging eenmaal na de installatie van WMF, zoals het installatieproces foutievelijk met de functie logboekregistratie van Software-inventaris stopt.</span><span class="sxs-lookup"><span data-stu-id="3518a-104">When installing WMF 5.x on a Windows Server 2012 R2 Server that is already running SIL, it is necessary to run the Start-SilLogging cmdlet once after the WMF install, as the installation process will errantly stop the Software Inventory Logging feature.</span></span>

<span data-ttu-id="3518a-105">Logboekregistratie van software-inventaris reduceert de operationele kosten van het verkrijgen van nauwkeurige informatie over de Microsoft-software die lokaal worden geïnstalleerd op een server, maar vooral voor grote aantallen servers in een IT-omgeving (ervan uitgaande dat de software is geïnstalleerd en uitgevoerd met de IT-omgeving).</span><span class="sxs-lookup"><span data-stu-id="3518a-105">Software Inventory Logging helps reduce the operational costs of getting accurate information about the Microsoft software installed locally on a server, but especially across many servers in an IT environment (assuming the software is installed and running across the IT environment).</span></span> <span data-ttu-id="3518a-106">Voorwaarde die is ingesteld, kunt u doorsturen van deze gegevens naar een aggregatieserver en verzamelen van de logboekgegevens op één plek met behulp van een uniform, automatisch proces.</span><span class="sxs-lookup"><span data-stu-id="3518a-106">Provided one is set up, you can forward this data to an aggregation server, and collect the log data in one place by using a uniform, automatic process.</span></span>

<span data-ttu-id="3518a-107">Terwijl u ook software-inventarisatiegegevens vastleggen kunt rechtstreeks een query uitgevoerd op elke computer, kunt logboekregistratie van Software-inventaris, met behulp van een architectuur doorsturen (via het netwerk) is gestart door elke server strijden tegen server discovery uitdagingen die gangbaar zijn voor een groot zijn software-inventarisatie en asset beheerscenario's.</span><span class="sxs-lookup"><span data-stu-id="3518a-107">While you can also log software inventory data by querying each computer directly, Software Inventory Logging, by employing a forwarding (over the network) architecture initiated by each server, can overcome server discovery challenges that are typical for many software inventory and asset management scenarios.</span></span> <span data-ttu-id="3518a-108">Logboekregistratie van software-inventaris maakt gebruik van SSL het beveiligen van gegevens die naar een aggregatieserver wordt doorgestuurd via HTTPS.</span><span class="sxs-lookup"><span data-stu-id="3518a-108">Software Inventory Logging uses SSL to secure data that is forwarded over HTTPS to an aggregation server.</span></span> <span data-ttu-id="3518a-109">Opslaan van gegevens op één plek, maakt de gegevens gemakkelijker te analyseren, bewerken en delen wanneer nodig.</span><span class="sxs-lookup"><span data-stu-id="3518a-109">Storing the data in one place makes the data easier to analyze, manipulate, and share when necessary.</span></span>

<span data-ttu-id="3518a-110">Geen van deze gegevens is naar Microsoft als onderdeel van de functionaliteit verzonden.</span><span class="sxs-lookup"><span data-stu-id="3518a-110">None of this data is sent to Microsoft as part of the feature functionality.</span></span> <span data-ttu-id="3518a-111">Gegevens en functionaliteit van Logboekregistratie voor software-inventaris zijn alleen bedoeld voor gebruik door de gelicentieerde eigenaar en beheerders van de serversoftware.</span><span class="sxs-lookup"><span data-stu-id="3518a-111">Software Inventory Logging data and functionality is meant for the sole use of the server software’s licensed owner and administrators.</span></span>

<span data-ttu-id="3518a-112">Zie voor meer informatie en documentatie over cmdlets van logboekregistratie van Software-inventaris, [beheren Sil in Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="3518a-112">For more information and documentation about Software Inventory Logging cmdlets, see [Manage Software Inventory Logging in Windows Server 2012 R2](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn383584(v=ws.11)).</span></span>